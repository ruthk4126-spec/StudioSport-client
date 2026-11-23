# StudioSport — Client

לקוח הדפים של מערכת ניהול שיעורי הסטודיו. HTML/CSS/JavaScript ללא build,
ומדבר עם שרת ה-API (הריפו הנפרד `StudioSport-server`) דרך HTTP.

## מבנה

```
index.html            דף הבית
login.html            התחברות / הרשמה
classes.html          שיעורים קרובים + הרשמה
my-classes.html       השיעורים שלי, ביטול הרשמה, משוב
subscribe.html        בחירת מנוי
admin.html            ניהול בקשות מנוי (Admin)
admin-classes.html    ניהול שיעורים (Admin)
css/style.css         עיצוב
js/config.js          כתובת השרת — הקובץ היחיד שמשנים בהתאם לסביבה
js/api.js             שכבת קריאות ל-API, ניהול טוקן, הודעות
```

## חיבור לשרת

כל הדפים טוענים קודם `js/config.js` ואחריו `js/api.js`. את הכתובת מגדירים במקום אחד:

```js
// js/config.js
window.STUDIO_CONFIG = {
  API_BASE: "http://localhost:5170/api"     // בפיתוח
  // API_BASE: "https://<service>.onrender.com/api"  // בפרודקשן
};
```

השרת חייב להתיר את הדומיין של הלקוח ב-CORS (`Program.cs` → `ClientApp`).

## הרצה מקומית

השרת רץ על `http://localhost:5170` (נראה `README` של ריפו השרת), ואז:

```powershell
cd <תיקיית-הריפו-הזה>
python -m http.server 5500
```

הלקוח נפתח ב-`http://localhost:5500`.

## פריסה ב-Render

Static Site:

- **Build Command:** (ריק)
- **Publish Directory:** `.` (שורש הריפו)
- אחרי הפריסה — עדכנו `js/config.js` בכתובת השירות של השרת, וטענו מחדש.

## משתמשי דמו (מגיעים מה-Seed של השרת)

| Username | Password | Role |
|---|---|---|
| admin | Admin123! | Admin |
| ruthi | Member123! | Member |
