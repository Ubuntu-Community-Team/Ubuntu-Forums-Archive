---
title: "Problem with KDE 4.1?"
date: 2009-03-26
forum: Desktop Environments
---

### Post by zolek78 on 2009-03-26
I've got kubuntu 8.10 installed on my laptop (vaio VGN - SZ53B). Recently, i have encountered a problem on kde.

Today, i opened my laptop as usual. The starting up process was normal until I got to the log in part. So, i logged in but instead of the normal desktop ive got something which was completely black. I waited for a while for it  to process, hopefully it would open but nothing happened. Then, I realised that it did open something but all i could see is black and glowing white color which look like the shape of the opening applications. There was no color, no buttons, no texts that i could see. I only saw the cursor clearly and nothing else.
I doubted this is a problem with the theme or may be it was because the update last night which i dont really remember what package it was.
I dont know how to fix this since i cant see anything. All i can acess to is the console. I dont know if anyone ever had this problem before but please help me to solve this or just tell me how i can restore the harddrive because there are extremely important data in there.

---

### Post by zolek78 on 2009-03-26
Anyone helps? Ive had this since yesterday and nothing improve ever since. I tried recovery mode but it makes no difference. I tried to open kubuntu from the install cd, it didnt work as well. I really dont know what to try now. Someone helps plz

---

### Post by imolafem on 2009-03-26
Are you logging in with the Default Profile?  Make sure you choose KDE4 when you are at the screen typing your user name and password.

---

### Post by zolek78 on 2009-03-26
I tried that one also but still, nothing works. It seems like a graphic problem. Things are still there but there is no color or image

---

### Post by zolek78 on 2009-03-27
I doubt that this problem happened after i updated some packages but i dony remember what they were.

---

### Post by imolafem on 2009-03-27
I'm not really strong in linux, but I remember I had that problem once after I updated my drivers.  I had to start X Server in default mode which used the default VGA driver and default screen resolution. I went in through the command prompt and edited the X configuration file to do this, then restarted the computer.

---

### Post by Monsieur Gonzalez on 2009-03-27
Can you log in with the failsafe option in the login manager? If you can, then that must be something KDE related. If you cannot, then it's probably the graphic server. 

1- If you can enter failsafe mode, copy the output of less /var/log/Xorg.0.log

2- If you cannot log in, then go to a terminal (press Alt+F1, that's a terminal login, text-only mode, and you can go back to the graphic session pressing Alt+F7) and copy the output of less /var/log/Xorg.0.log.

---

