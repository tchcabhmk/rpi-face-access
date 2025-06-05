# 🔐 Raspberry Pi Face Access System

מערכת פתיחת שער/דלת לפי זיהוי פנים על Raspberry Pi.  
כוללת צילום מראש של מורשים, עיבוד במחשב עם GPU, ושימוש קל ב־Raspberry Pi עם ספריית `face_recognition`.

---

## 💡 מה המערכת עושה?

1. מזהה פנים שמופיעות במצלמה בזמן אמת.
2. בודקת אם הפנים תואמות לאחד המורשים.
3. אם כן — פותחת את המנעול/שער באמצעות GPIO.

---

## 📁 מבנה הפרויקט

rpi-face-access/
├── authorized_faces/ # תמונות של כל האנשים המורשים (ממויינות לפי תיקיות)
├── create_encodings.py # סקריפט שמייצר known_encodings.pickle
├── known_encodings.pickle # קובץ הקידודים (מועבר ל-RPi)
├── main.py # הקוד הראשי שרץ על ה-Raspberry Pi
├── requirements.txt # ספריות הדרושות (RPi)
├── README.md # קובץ זה


---

## 🛠 שלבי התקנה

### 💻 שלב 1 – על מחשב רגיל (עם GPU)

1. שים תמונות של המורשים בתיקייה `authorized_faces/`, לכל אדם תיקייה נפרדת.
2. הרץ:
   
   python create_encodings.py
יווצר הקובץ known_encodings.pickle.

🍓 שלב 2 – על ה־Raspberry Pi
התקן ספריות (מומלץ לעשות venv):


pip install -r requirements.txt
חבר מצלמה USB או CSI.

הרץ:


python main.py



📦 requirements.txt (RPi)


face_recognition
opencv-python
gpiozero
pickle-mixin
\


📷 דוגמה להרצה
python main.py


אם זוהתה פנים מוכרת: תודפס הודעה וייפתח המנעול.

✍️ קרדיטים
הפרויקט פותח על ידי אביב גרינברג במסגרת פרויקט אישי לשילוב בין AI, חומרה וזיהוי פנים.


