---
title: "why i can't see file in folder ? how bring it back?"
date: 2009-06-23
forum: Desktop Environments
---

### Post by tonjaa on 2009-06-23
what'r wrong ?  i install fedora11 and i try to rename some file - desktop-login.ogg in folder stereo
that first time i can't change all file because at properties  file  at permission it tell - " you are not the owner ,so you could not change these permission" 
and i try to use command in terminal for change rename . someone tell me use command [COLOR=DarkOrange]
su[/COLOR]
[COLOR=SandyBrown][COLOR=DarkOrange]chmod 744  folder or file location[/COLOR][/COLOR]
i try to use su  but when i type chmod 744 and file name at first time i don't know what happen i don't 
understand it's correct or not. but i try to use command 
rename.  [COLOR=DarkOrange] mv sound-login.ogg sound-009.ogg
[COLOR=Black]i can rename but now it have problem i can't see all file .ogg in folder stereo and when i boot to login
not have sound to login and all no sound from folder when i click at folder /usr/share/sounds/freedesktop/stereo   in folder stereo i can't see file it empty. 
 but when i use command [COLOR=DarkOrange]su [COLOR=Black]for look in terminal and directory of stereo folder i can see all file.  
that i not understand why i can't see file in icon folder and why i can see in su command in terminal?
and how i can bring all file back to folder -stereo and use it same time? 
who know please tell me.:confused:
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by squaregoldfish on 2009-06-23
In order to see the contents of a directory, you have to set the execute bit. So, you should use:

```
chmod 755 <folderName>
```

Whether or not you can see the files doesn't affect what you can do with them, which is why you can still rename the file even though you can't see it!

Hope this helps,
Steve.

---

### Post by tonjaa on 2009-06-23
[COLOR=SeaGreen]yessss.[/COLOR] it work i can see all file and i can use sound again.
thank you so much Steve. 
[COLOR=DarkOrange]for human beings[/COLOR]
TON '

---

