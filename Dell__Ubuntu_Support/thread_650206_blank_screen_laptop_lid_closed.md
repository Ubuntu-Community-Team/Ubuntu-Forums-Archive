---
title: "blank screen laptop lid closed"
date: 2007-12-26
forum: Dell  Ubuntu Support
---

### Post by htaj on 2007-12-26
hi everyone.

im running a dell inspiron 640m, i just recently switched to ubuntu and loving it. however, im deciding to switch back to vista if i cant solve this problem im having.

i went to power management and chose blank screen when i close laptop lid. however, whenever i close my lid, the monitor doesnt blank out, the backlight is still on.

any help would be greatly appreciated.

---

### Post by dnvikram on 2007-12-26
Try this and let Me know if its working:

contrl + alt+ L (It will lock the screen)

Now,close the lid.Did it blank out or still the same?

Are you sure the power management options when running on battery and AC power are set to blank screen specifically?

---

### Post by htaj on 2007-12-26
hi.

im 100% sure the settings are on blank screen on both A/C and power.
 
i did the lock screen, and my monitor turned black but backlight is still on. when i closed the lid, it shutoff for about 1 sec then the monitor is back on again. When i opened the lid now, its asking me for my password to unlock.

---

### Post by dnvikram on 2007-12-26
Could you kindly post a screenshot of the power management setting?Its strange though,that it shuts off of 1sec and then comes back on.And is it Fiesty or Gutsy you are using?

---

### Post by htaj on 2007-12-26
im using gusty.

[http://img169.imageshack.us/my.php?image=screenshotuz1.png](http://img169.imageshack.us/my.php?image=screenshotuz1.png)

---

### Post by dnvikram on 2007-12-26
My office firewall is blocking the imageshack site.So couldnt view the screenshot.

---

### Post by htaj on 2007-12-26
[http://www.flickr.com/photos/jath611/2137808256/](http://www.flickr.com/photos/jath611/2137808256/)

---

### Post by dnvikram on 2007-12-26
I appreciate your patience in providing Me the alternate links to access image.Unfortunately,My office firewall is blocking almost similar site.I am really sorry.If I am not wrong,one can paste the image in the posts or attach it.I really want to help you in this issue.If you are bugged ,then My apologies.I will check once I reach home and let you know.

---

### Post by htaj on 2007-12-26
oh im sorry, i didnt notice there was an attachment feature in this forum.

i really appreciate your help. 

[http://ubuntuforums.org/attachment.php?attachmentid=54248&stc=1&d=1198654896](http://ubuntuforums.org/attachment.php?attachmentid=54248&stc=1&d=1198654896)

---

### Post by dnvikram on 2007-12-26
The settings are exactly similar to what I have on my inspiron1420N running gutsy final and its working perfectly.As a workaround,did you try setting a blank screensaver and then closing the lid.Does it still keep running or stays blank?

---

### Post by htaj on 2007-12-26
ive already tried running a blank screen saver but still the same result. =(

---

### Post by dnvikram on 2007-12-26
Now thats really annoying.Have to wait and see if someone has come across the same problem who has a fix or workaround for it.Will check meanwhile for a workaround and keep you posted.

---

### Post by hardskinone on 2007-12-28
I have a 640m and I think I have same issue. When I close the lid the backlight switch off for just a second then it lights on again.

In Feisty this feature worked well, this looks like a regression in Gutsy. There is a way to log lid's events?

---

### Post by hardskinone on 2008-01-06
As steted in bug #30802 commeting line 9 in /etc/acpi/lid.sh solve the issue but there still a 'flash' (screen off/on/off) after lid closed.

Hope helps.

---

### Post by lshlyapnikov on 2008-01-14
BTW I am running Ubuntu 7.10 on Dell Inspiron E1505. And I have the same behavior. When the laptop lid angle is about 10-20 degree the screen turns off... but if I close the lid completely the display turns on again. If I keep the lid not closed completely (10-20 degree) the screen is staying off all the time.

Commented line 9 in /etc/acpi/lid.sh. Have this flashing off/on/off.

Maybe the fact that display goes off when it is not closed completely can help to solve the flashing problem.

Thanks for the help,
Leonid

---

### Post by tophue on 2008-02-10
I have the same machine and the same problem. In feisty i could shut the lid and the screen would go blank and it would lock it for me. I can't get it to do that now. If anyone has a fix for this please explain how to do it.

---

### Post by zzHanks on 2008-02-16
Is this problem still unresolved?

I'm running Gusty on Dell Latitude D505, it seems to affect every Dell running on Ubuntu.

---

### Post by adult swim on 2008-02-17
> **hardskinone said:**
> As steted in bug #30802 commeting line 9 in /etc/acpi/lid.sh solve the issue but there still a 'flash' (screen off/on/off) after lid closed.

Hope helps.
this worked on my inspiron E1705

---

### Post by tophue on 2008-02-24
> **hardskinone said:**
> As steted in bug #30802 commeting line 9 in /etc/acpi/lid.sh solve the issue but there still a 'flash' (screen off/on/off) after lid closed.

Hope helps.

This seems to help people but could someone explain what I am actually supposed to do to line 9? I am looking at it but have no clue what I am supposed to change or edit to make it work

---

### Post by adult swim on 2008-02-25
in terminal type 
```
sudo gedit /etc/acpi/lid.sh
```
then put a the number sign, #, in front of the ninth line
it will look like this
```
#!/bin/bash

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

#if [ `CheckPolicy` == 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
```

---

