---
title: "Font Problems"
date: 2005-04-12
forum: Desktop Environments
---

### Post by pinecone on 2005-04-12
My courier font is not displaying (I installed true type fonts).  So I've got two questions for you guys.
1)  If I just remove the font will fonts that are supposed to show up as courier just appear as something else?
2)  How could I do this?

I know next to nothing about fonts and how they work in linux to be honest, so if this is a real stupid question I'm sorry.  Thanks in advance yall :)

---

### Post by Papaskunk on 2005-04-12
I could be wrong on this, but I think you have to restart Gnome for it to recognize the font. I think Gnome is a little buggy with fonts, personally. As far as uninstalling fonts, if you go to the Font control panel, click on the 'details' button (I think it says that, I'm at work right now) you can go to the Font folder. Just delete what fonts you want to. However, if nothing shows up as Courier, Gnome may not have detected it yet, so it might not show up in the folder (you'd have to restart). This is similar to the Windows font system of manually copying and deleting files.

So yes, it will simply display another monospace font (probably 'monospace') instead of Courier.

KDE's font management system is vastly superior to Gnome's, so even if you stay in Gnome all the time, it might be worth it to install KDE for that reason alone (that's what I've done). It will still work from within Gnome, and you won't have to restart. KDE's Font Control Panel Applet looks and behaves very much like a commercial font management program you might be used to if you have a Mac, such as Font Reserve or Suitcase, where you can dynamically activate and deactivate fonts without having to deal with folders, albeit there are no categories.

Good luck!

---

### Post by pinecone on 2005-04-12
[QUOTE=Papaskunk]I could be wrong on this, but I think you have to restart Gnome for it to recognize the font. I think Gnome is a little buggy with fonts, personally. As far as uninstalling fonts, if you go to the Font control panel, click on the 'details' button (I think it says that, I'm at work right now) you can go to the Font folder. Just delete what fonts you want to. However, if nothing shows up as Courier, Gnome may not have detected it yet, so it might not show up in the folder (you'd have to restart). This is similar to the Windows font system of manually copying and deleting files.

So yes, it will simply display another monospace font (probably 'monospace') instead of Courier.

KDE's font management system is vastly superior to Gnome's, so even if you stay in Gnome all the time, it might be worth it to install KDE for that reason alone (that's what I've done). It will still work from within Gnome, and you won't have to restart. KDE's Font Control Panel Applet looks and behaves very much like a commercial font management program you might be used to if you have a Mac, such as Font Reserve or Suitcase, where you can dynamically activate and deactivate fonts without having to deal with folders, albeit there are no categories.

Good luck![/QUOTE]
well the computer has been restarted many times.  I've been living with this problem for a couple weeks now.

---

### Post by Papaskunk on 2005-04-13
Well, I've had the same problem, but I fixed it by going into KDE. I'm sure this is not an ideal fix though (just a workaround), especially if you do not want to install KDE. However, since I like KDE's font management so much better, I just use it anyway...

Anyone have the real fix for Gnome's font issues? :|

---

### Post by Nano on 2005-04-13
If you put it in the proper place it would be enough by executing:
```

fc-cache

```

---

### Post by pinecone on 2005-04-14
[QUOTE=Papaskunk]Well, I've had the same problem, but I fixed it by going into KDE. I'm sure this is not an ideal fix though (just a workaround), especially if you do not want to install KDE. However, since I like KDE's font management so much better, I just use it anyway...

Anyone have the real fix for Gnome's font issues? :|[/QUOTE]
I really like gnome though, I guess I could move to KDE as a last resort, but I'd really rather not.

---

### Post by Alexander Kirillov on 2005-04-15
[QUOTE=pinecone]My courier font is not displaying (I installed true type fonts).  So I've got two questions for you guys.
1)  If I just remove the font will fonts that are supposed to show up as courier just appear as something else?
2)  How could I do this?

I know next to nothing about fonts and how they work in linux to be honest, so if this is a real stupid question I'm sorry.  Thanks in advance yall :)[/QUOTE]
 Two questions:
 - how - and where exactly - have you installed the Courier font? THe default location is /usr/share/fonts; is it there?

 - does it show in font selector (try, e.g., desktop Preferences->Fonts)

---

### Post by pinecone on 2005-04-15
[QUOTE=Alexander Kirillov]Two questions:
 - how - and where exactly - have you installed the Courier font? THe default location is /usr/share/fonts; is it there?

 - does it show in font selector (try, e.g., desktop Preferences->Fonts)[/QUOTE]
 It is in /usr/share/fonts and it does show in the font selector, but when you click it to see what it looks like you get nothing but blank spaces.

---

### Post by Alexander Kirillov on 2005-04-22
[QUOTE=pinecone]It is in /usr/share/fonts and it does show in the font selector, but when you click it to see what it looks like you get nothing but blank spaces.[/QUOTE]
 My guess is, it maybe one of:
 - permission problem - what are permissions on the file? 
 -corrupted file. If this is the case, you have to remove it (with sudo rm /usr/share/fonts/<filename>) - then GNOME (and KDE) will automatically chose a different monospace font to display instead of courier.

---

### Post by Hamilcar on 2005-05-25
I solved this problem by deleting files "cou*.fon" in "usr/share/fonts/truetype/Fonts/" and executing fc-cache. The file "Courier" in gnome-fonts-viewer disappeared. In Konqueror, pages HTML with "Courier font" display now normally.

---

