# Connect the form to Google Sheets (5 minutes)

1. Create a new Google Sheet. In row 1 type: name, phone, email, location, role, business, level, interest, registeredAt
2. Extensions > Apps Script. Delete the default code and paste:

```
function doPost(e){
  var s=SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var d=JSON.parse(e.postData.contents);
  s.appendRow([d.name,d.phone,d.email,d.location,d.role,d.business,d.level,d.interest,d.registeredAt]);
  return ContentService.createTextOutput("ok");
}
```
3. Deploy > New deployment > type "Web app". Execute as: Me. Who has access: Anyone. Deploy and copy the Web app URL.
4. In index.html find `const CONFIG` and paste the URL into SHEET_URL.
5. Also fill WHATSAPP_GROUP (your class group invite link) and WHATSAPP_NUMBER (e.g. 2348012345678).
6. Test with a fake registration and confirm the row appears in the sheet.
