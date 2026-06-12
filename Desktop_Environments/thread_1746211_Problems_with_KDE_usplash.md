---
title: "Problems with KDE usplash"
date: 2011-05-01
forum: Desktop Environments
---

### Post by RenThaL on 2011-05-01
Hello, I'm new on linux. 
I installed kubuntu yesterdeay, and to day I changed the login-pass screen (usplash I guess), to one  that looks like a debian icon on the center. well... rebot, and before I get to that usplash, I get the "Theme not usable with authentication method 'Username + password (classic)' alert.

Then, in the screen, I can't write anything... just take the enter, delete, and esc (oh, and I cand copy paste by mouse)

So that's for now. I hope you take piece of your time with this

Thanks!!, and sorry for my english

---

### Post by RenThaL on 2011-05-01
Anyone?

---

### Post by t2kburl on 2011-05-01
I believe usplash is the grub wallpaper. you are at the kdm login screen. If you can, login in text mode then type 

startx

which should get you back in to KDE where you can change your login screen settings back.

---

### Post by RenThaL on 2011-05-01
> **t2kburl said:**
> I believe usplash is the grub wallpaper. you are at the kdm login screen. If you can, login in text mode then type 

startx

which should get you back in to KDE where you can change your login screen settings back.

Hey t2kburl, thanks for the answer.


Here is what I get when typing startx 
> Fatal server error:
Server is already active for display 0
            If this server is no longer runnint, remove /tmp/.X0-lock
            and start again.

Please consult the The X.Org Foundation support
               at [http://wiki.x.org](http://wiki.x.org)
for help.

ddxSigGiveUp: Closing log
Invalid MIT-MAGIC-COOKIE-1 keyxinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

Grettings

---

### Post by t2kburl on 2011-05-02
I'm not sure what the next step is, but I'm sure someone here knows.
Good luck!

---

### Post by RenThaL on 2011-05-02
Haha that's ok man
thanks for answering... I'll wait

---

### Post by bergfly on 2011-05-03
You can try doing what the error message says and remove the lock. You will need to do this as root.

so try

sudo rm -rf /tmp/.X0-lock

and then try startx again

---

### Post by RenThaL on 2011-05-03
Well I did it:

sudo rm -rf /temp/.X0-lock
startx 

and it gives:

"_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:

Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
  for help
Please also check the log file at "/var/log/Xorg.o.log" for additional information 

  ddxSigGiveUp: Closing log 
(here It takes like 5 seg)
Invalid MIT-MAGIC-COOKIE-1 keyxinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error"


I hope it helps
Thanks

---

