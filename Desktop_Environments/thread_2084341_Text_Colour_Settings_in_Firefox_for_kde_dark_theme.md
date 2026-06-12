---
title: "Text Colour Settings in Firefox for kde dark themes make text unreadable"
date: 2012-11-15
forum: Desktop Environments
---

### Post by Thanduel on 2012-11-15
Hi

I have a rather annoying issue where often the colour of the text in a text box in my browser is as light as the colour of the background of the text box.  So for example when I google search the text is light grey and the textbox has a white background. 

I have played with a number of the colour settings for the browser and the theme but I haven't been able to sort it out.  Any help to sort this out would be greatly appreciated.

---

### Post by vasa1 on 2012-11-15
Close (exit) all instances of Firefox.
Go to your profile folder. It is here: /home/your_name/.mozilla/firefox/randomstring.default
Look for a subfolder called **chrome**. If it doesn't exist, create it.
If **chrome** does exist, look for a file called **userContent.css**. Otherwise, create an empty file with this name in **chrome**.
Now open it with a text editor and paste in this code (adjusted to your taste):```
INPUT {color: black !important; background: #aaaaaa !important }
```
Save the file (as plain text) and close the editor.
Restart Firefox. You should now have black text on a gray background.

Notes: 
chrome and userContent.css are case-sensitive and should be spelled correctly.
The settings here will take precedence over those in the OS theme.

---

### Post by Thanduel on 2012-11-15
Thank you for your response, your suggestion solves the issue in a number of cases like search bars however the issue persists on websites like facebook.  Are there any further things I can do?

---

### Post by vasa1 on 2012-11-15
> **Thanduel said:**
> Thank you for your response, your suggestion solves the issue in a number of cases like search bars **however the issue persists** on websites like facebook.  Are there any further things I can do?
I don't connect to Facebook. If there are other sites not requiring a sign-in, do mention the specific links and perhaps include small images of the troublesome areas.

---

### Post by vasa1 on 2012-11-15
Change this code ```
INPUT {color: black !important; background: #aaaaaa !important }
```
to this:
```
INPUT, TEXTAREA {color: black !important; background: #aaaaaa !important }
```

---

### Post by Thanduel on 2012-11-16
Thank you very much that works!

---

