---
title: "Removing Global Menu application specific"
date: 2022-11-01
forum: Desktop Environments
---

### Post by jamo1234 on 2022-11-01
G'day, I did a fresh install of Unity 22.10 and love it, my wife can't come to grips with Evolution Mail Global Menu, so can anyone please help my remove Global menu application specific,

Regards Joe.

---

### Post by TheFu on 2022-11-02
```
sudo apt purge {package name}
```
That should do it.

---

### Post by jamo1234 on 2022-11-02
G'day and thanks for your reply but correct me if I'm wrong wont your instruction remove the entire application, I just want to remove Global menu in Evolution Mail.

I have followed lots of suggestions but none work, I have Unity 22.10 installed, 

Regards Joe
PS. sorry about the duplicate post, put it down as a seniors momebt.

---

### Post by Frogs Hair on 2022-11-02
You might have a look in the dconf-editor if installed. I don't have Ubuntu Unity installed , so can't check.

---

### Post by jamo1234 on 2022-11-02
Hey thanks mate, it was not installed, I have installed it, now what ?

Joe.

---

### Post by Frogs Hair on 2022-11-02
Try navigating to the application via org>gnome>desktop or there is also a search function. When you locate evolution there _may be_ an option to set the global menu integration to false thus disabling it. Without installing the operating system I can't be sure.

---

### Post by TheFu on 2022-11-02
Well, you said remove it. I assumed you wanted the program gone.

You can look for .desktop files that are NOT in any user's HOME directory.  Rename that file and it should remove it from any menu.  There is a per-user location for .desktop files, but those are DE specific and I haven't used a DE in about a decade, so you'll need to figure out where that is.  It will be under the User's HOME, somewhere, but I don't know where.  So, you'd probably want to copy the .desktop that was in the system areas /etc/ or /lib/ would be my top guesses to the user-specific location under your HOME.

---

### Post by jamo1234 on 2022-11-02
Sorry bout the confusion 
, I think Dconf Editor is my best bet, I can open dconf but don't want to stuff it up so will search for examples , thanks everyone for your input,

Regards Joe..

---

### Post by jamo1234 on 2022-11-02
OK I can edit dconf editor by flicking the switch from Default and entering evolution between the square brackets but how to save it, I'm stuffed if I can see a way, oh well life wasn't meant to be easy, any help would be appreciated

regards Joe

---

