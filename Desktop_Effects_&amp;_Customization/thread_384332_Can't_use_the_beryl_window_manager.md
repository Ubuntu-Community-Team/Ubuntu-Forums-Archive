---
title: "Can't use the beryl window manager"
date: 2007-03-14
forum: Desktop Effects &amp; Customization
---

### Post by zoozabar on 2007-03-14
ok I finally got beryl to install without dumping Ubuntu, this has been a long process. now that I have neryl installed I can not use the winidow manager it just defaults to gnome. Maybe I am to new at this and maybe I just don't know how to use beryl,I have recently dumped xp and running pure Ubuntu, any help with this would be appreciated

---

### Post by divague on 2007-03-14
> I can not use the winidow manager it just defaults to gnome

By this you mean that you can't use the effects?

If so, then try running this in a terminal

$beryl-manager

---

### Post by zoozabar on 2007-03-14
andy@andy-laptop:~$ $beryl-manager
bash: -manager: command not found


when I try the command without the $ then it just opens up the same menu I see when I right click on the beryl icon

any ideas whats wrong if anything?

---

### Post by divague on 2007-03-14
Try running:

$beryl

and see if there are errors.

Also did you installed it with glx or aiglx?

If you installed with glx i suppose you created a glx session, if you didn't logged in using that session, log out and select glx in the session menu the log in again.

---

### Post by zoozabar on 2007-03-14
andy@andy-laptop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : failed

Root window size (1400/1050) is bigger then maximum texture size (1024x1024)

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  4 (X_GLXDestroyContext)
  Serial number of failed request:  38
  Current serial number in output stream:  40


I will log myself out and select GLX and see if that works, thanks for the quick response!

---

### Post by zoozabar on 2007-03-14
ok how do I get GLX?

---

### Post by divague on 2007-03-14
which guide did you followed to install beryl?

---

### Post by zoozabar on 2007-03-14
[http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7)

---

### Post by zoozabar on 2007-03-14
When I am at my log in screen all I have for session options are...

Last Session
Default session
Gnome
Failsafe Gnome
Failsafe Terminal

what do I need to do?

---

### Post by zoozabar on 2007-03-14
do I need to specify "FGLRX" in /etc/default/linux-restricted-modules-common?

---

### Post by zoozabar on 2007-03-14
Thanks for your help I can't believe how much of a bone head I am , once I adjusted my resolution down to 0124x768 all is well. thanks again for putting up with me.:guitar:

---

