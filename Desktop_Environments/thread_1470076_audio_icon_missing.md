---
title: "audio icon missing"
date: 2010-05-02
forum: Desktop Environments
---

### Post by ubunlilluz on 2010-05-02
hi,
i don't know what i did but the icon where i can adjust the audio volume is missing from the right side of upper bar.
Is there nobody so kind out there able to fix this problem?
thanks

---

### Post by nitstorm on 2010-05-02
ubuntuforums.orgubuntuforums.org/newreply.php
If you can see the network manager icon but not the volume icon i don't know what the problem is, but if you can't see it then you are probably missing a notification area on your taskbar thing. right-click on the panel, choose Add to panel and choose the Notification Area and add. Your missing icons should show up hopefully.

---

### Post by ubunlilluz on 2010-05-02
yes i can see the network manager icon but not the audio icon and if i try to right click on that side of upper bar it dosn't work the "add on panel" but only the remove

---

### Post by ghostborg on 2010-05-02
Right click on a blank area of the upper panel and you should see a menu that has Add To Panel. Then scroll down the list to Indicator Applet.
When I right click on my volume indicator and then about it says Indicator Applet 0.3.6. Afterward you can move it by unchecking Lock to panel if checked and then select move from the right click menu of the applet.

---

### Post by ubunlilluz on 2010-05-02
i'm sorry but if i do right click and then Add to Panel in the list there's no audio volume applet. In older version i remenber there was it, but now no.

---

### Post by nitstorm on 2010-05-03
ubuntuforums.orgubuntuforums.org/showthread.php
[http://ubuntuforums.org/showpost.php?p=9223950&postcount=3](http://ubuntuforums.org/showpost.php?p=9223950&postcount=3)

---

### Post by Chromagnum on 2010-05-03
Try this:
```
$ killall -1 gnome-panel
```
It should restart gnome-panel including failed app.

If that doesn't work, then try this:
1. Press Ctrl + Alt + F1, it should bring you to the text based terminal.

2. Login with your username and password

3. Run this command from your terminal:
```
$ rm -rf .gnome .gnome2 .gconf .gconfd
```

4. Press Ctrl + Alt + F7

I should warn you, perform that command will set your desktop to default configuration — the wallpaper, theme, etc, back to default.

---

### Post by ubunlilluz on 2010-05-03
> **Chromagnum said:**
> Try this:
```
$ killall -1 gnome-panel
```
It should restart gnome-panel including failed app.

If that doesn't work, then try this:
1. Press Ctrl + Alt + F1, it should bring you to the text based terminal.

2. Login with your username and password

3. Run this command from your terminal:
```
$ rm -rf .gnome .gnome2 .gconf .gconfd
```

4. Press Ctrl + Alt + F7

I should warn you, perform that command will set your desktop to default configuration — the wallpaper, theme, etc, back to default.

the second way works. thanks !

---

### Post by foureyesboy on 2010-05-15
same for here.  the second method works.

but the question is why are they gone?
first it was the envelope icon, then the speaker icon, one by one they're gone from the notification area (likely after an update).  kinda weird.

---

### Post by arturic on 2010-07-17
I had this issue too, adding the indicator applet solved it.

I don't know what caused this, but I think it was this:

I was playing with my configuration, among other things I was trying to change the login screen background and tried this command in a terminal that worked, but threw some errors in the terminal. Also using **gdm2setup** left me with 2 "blue circle with a guy" icons of Assistive Tech. in the tray.

The suspect code is:
```
gksu -u gdm dbus-launch gnome-appearance-properties

``` 
from this thread: [How do you change the boot splash screen image for 10.04 Lucid Lynx?]("http://ubuntuforums.org/showthread.php?t=1446949") (comment #10)

I also did some other config. stuff before rebooting so I can't be sure...
Cheers!

EDIT: Here is a similar thread: [Lucid missing volume control symbol?]("http://ubuntuforums.org/showthread.php?p=9601800")

---

### Post by Tootler on 2010-11-19
I had the same problem and restoring the indicator applet solved it.

I couldn't see any use for the envelope I removed it. I didn't want any of the facilities it linked to as I never use them and I don't use evolution for email, so it was of no use to me.

There doesn't seem any logical reason why the volume control should be tied to the other facilities linked to the envelope but I have had to put the envelope back so I can use the volume control.

I see it also has access to Rhythmbox as well. I would like to be able to remove that as I don't particularly like Rhythmbox.


However, I don't see why the

---

