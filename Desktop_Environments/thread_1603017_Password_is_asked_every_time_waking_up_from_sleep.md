---
title: "Password is asked every time waking up from sleep"
date: 2010-10-22
forum: Desktop Environments
---

### Post by adit on 2010-10-22
I am using ubuntu 10.10.  When the computer wakes up from sleep it asks for password.  I don't want password to be asked.

---

### Post by mikewhatever on 2010-10-22
So how else do you want it to log you in?

---

### Post by vader95 on 2010-10-22
I think he means that he doesn't want the screen to lock, just go black

---

### Post by adit on 2010-10-22
> he means that he doesn't want the screen to lock, just go black
Exactly.

---

### Post by Grenage on 2010-10-22
Preferences/Screensaver

Untick 'Lock screen when screen-saver is active'.  Does that work?

---

### Post by mosaic2s on 2010-10-22
Go to system>preferences>screensaver.
Uncheck - lock screen when screen saver activates.

---

### Post by adit on 2010-10-22
> Untick 'Lock screen when screen-saver is active'
Done.
Now password is not asked to wake up screen (only screen).
However when I suspend the computer and wake it up it asks for password.

---

### Post by Grenage on 2010-10-22
If you need a to log into the machine when it first starts, I imagine you'd have to have one after suspend.

---

### Post by adit on 2010-10-22
I have enabled automatic log in.  I don't want password for waking up from sleep also.

---

### Post by kerry_s on 2010-10-22
gconf-editor, apps-> gnome-power-manager-> lock

---

### Post by Grenage on 2010-10-22
gconf-editor in a terminal.
Tick /apps/gnome-power-manager/lock/use_screensaver_settings

Any joy?

---

### Post by adit on 2010-10-22
Thank you very much kerry_s and Grenage.
I unchecked /apps/gnome-power-manager/lock/suspend key.
Now the computer doesn't ask for any password during wakeup.

---

### Post by Teotihuacan on 2010-11-01
Hello,

I wanted to do the same (remove the password when returning from sleep-mode). So I unchecked the items in the GConf-Editor as said in this thread, but it doesn't work everywhere:
[LIST]
[*]When choose the sleep mode in the shutdown dialog (the one I get when I push the power button for example), it works. I don't have to enter my password then.
[*]When I choose the sleep mode in the logout drop-down menu (the one on the top right corner of the screen), it doesn't work (I have to enter my password again)
[/LIST]
I would like to remove this password everywhere. Do you have any idea how I can do that?

Thanks in advance.

---

### Post by rhy7s on 2010-11-02
> **Teotihuacan said:**
> Hello,

I wanted to do the same (remove the password when returning from sleep-mode). So I unchecked the items in the GConf-Editor as said in this thread, but it doesn't work everywhere:
[LIST]
[*]When choose the sleep mode in the shutdown dialog (the one I get when I push the power button for example), it works. I don't have to enter my password then.
[*]When I choose the sleep mode in the logout drop-down menu (the one on the top right corner of the screen), it doesn't work (I have to enter my password again)
[/LIST]
I would like to remove this password everywhere. Do you have any idea how I can do that?

Thanks in advance.

It behaves the same for me in that it still asks for a password when choosing to sleep from the logout drop-down menu. I haven't yet tried sleeping from the shutdown dialog, sleep button on keyboard or automated sleep though.

Edit: not ideal, but [http://ubuntuforums.org/showpost.php?p=9756347&postcount=11]("http://ubuntuforums.org/showpost.php?p=9756347&postcount=11") works in all cases for me.

---

### Post by Teotihuacan on 2010-11-06
Thanks a lot. It worked.

---

