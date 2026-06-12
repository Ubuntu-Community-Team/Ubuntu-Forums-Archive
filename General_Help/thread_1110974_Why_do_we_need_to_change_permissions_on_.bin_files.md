---
title: "Why do we need to change permissions on .bin files"
date: 2009-03-30
forum: General Help
---

### Post by ade234uk on 2009-03-30
Can you please explain why we need to change permissions on .bin files?
Had to do this when I downloaded google-earth as well.

sudo chmod +x filename.binAdbeRdr9.1.0-1_i486linux_enu.bin

---

### Post by heindsight on 2009-03-30
Because you can't execute any file unless you have permission to do so.

---

### Post by binbash on 2009-03-30
you have to make the files executable if you are gonna run it.That command gives executable permissions to that file

---

### Post by anaconda on 2009-03-30
In windows the system assumes that any .exe file is executable. But in linux we can mark ANY file as executable. And only executable files can be "executed" ;)


PS.
"sudo chmod +x filename.binAdbeRdr9.1.0-1_i486linux_enu.bin"

I didn't know that that would work..
I tought that it was
chmod a+x filename   (a=all)
chmod u+x filename   (u=user)  OR
chmod g+x filename   (g=group)

thanks for the info.

---

### Post by ade234uk on 2009-03-30
Thank you for the explanation. Basically the .bin is a binary file. Of course when I installed it, I ended up installing as root, so I could not run it to begin with so chmod777 on the thing.

However I would be interested in finding out what the proper procedure is to install this? I can then update my site and hopefully other users can get help.

Learn something new with Ubuntu everyday.

---

