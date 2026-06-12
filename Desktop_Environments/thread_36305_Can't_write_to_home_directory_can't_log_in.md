---
title: "Can't write to home directory can't log in"
date: 2005-05-22
forum: Desktop Environments
---

### Post by Vin_L on 2005-05-22
I think while trying to install My Neatgear wireless card I may have ended up with some files owned by root in y home directory. Now when I try to log in I get an error to the effect that it cannot write to the home directory. It will not let me log in even under the failsafe console.

I am a noob please teach me how to fix this?

Thanks

Vin

---

### Post by kvidell on 2005-05-22
[QUOTE=Vin_L]I think while trying to install My Neatgear wireless card I may have ended up with some files owned by root in y home directory. Now when I try to log in I get an error to the effect that it cannot write to the home directory. It will not let me log in even under the failsafe console.

I am a noob please teach me how to fix this?

Thanks

Vin[/QUOTE]
 Try putting the Ubuntu CD and instead of going to the installer, go to the Recovery type root console thinger and chown everything back to your user (You'll have to do it by numeric UID/GID though, just as a heads up... the recovery window wont have your passwords file with uid->uname stuff.)

Hope that helps,
- Kev

---

### Post by Vin_L on 2005-05-22
Thanks Kev, I'll give that a try although I am not sure about numeric UID/GID. I am thinking it may be obviouse when I go in.

---

### Post by kvidell on 2005-05-22
[QUOTE=Vin_L]Thanks Kev, I'll give that a try although I am not sure about numeric UID/GID. I am thinking it may be obviouse when I go in.[/QUOTE]
 cat /etc/passwd | grep yourusername

You can look at them from your recovery console, mount your harddrive to something and you'll have to mount your home direcs too.
The passwd/group files will be visible but not useful.
So just grab your uid and gid from that file and you should be set.

---

### Post by Vin_L on 2005-05-23
That did it!
I learned all about chown tonight!

Thanks again Kev

---

