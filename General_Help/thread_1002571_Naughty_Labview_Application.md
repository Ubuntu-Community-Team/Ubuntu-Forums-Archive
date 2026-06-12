---
title: "Naughty Labview Application"
date: 2008-12-05
forum: General Help
---

### Post by Zim Zelen on 2008-12-05
Hello Everyone,

I just made the great leap forward to Ubuntu, and it's going pretty well - with the help from the community.

However i'm stuck on this one : i'm trying to install a Labview application (my colleague made it) - i don't need labview itself but just the application. I tried to do it with wine, but the installer rapidly complains and says :

[I]
Error: this installer needs access to "My Documents". However, this location "C:\windows\profiles\crash-san\My documents\ is not available. Ensure that this directory exists and is available and run the installer again.[/I]

in Wine My documents is set to be /home/crash-san/Documents/ . Also the folder that the error mentions does exist (with an arrow on top though??). I really have no idea what to try.

I'm running on an old dell inspiron 1150 laptop...

Thanks!

Zim

---

### Post by Grolsche on 2008-12-05
i'm not up on linux and wine as yet, but the arrow you speak about means its a shortcut. So technically the file doesn't exist in in that location. It actually exists in the .wine folder but wine has just placed a shortcut and named it My Documents to make it easier for you to find.

Hope this helps you to solve the problem. I'm not sure if you can get the java app to point there instead or not?

---

### Post by Zim Zelen on 2008-12-07
Yep, i figured that out eventually, tried creating a My Documents folder in the right location,but i still get the same error message when i install...

I could get the developer of the app to try and change it, but he's unfamiliar with Linux and rather busy, so i'd do that as a last resort!

---

### Post by sankarapandian.s on 2009-01-06
Hello Zim Zelen,

You told ur frnd made labVIEW application, Can u help me how to install LabVIEW in Ubuntu ??? 

I want to install labVIEW.

Thanks.
sankar.s

---

