---
title: "Re: User-controlled dialup/hangup with modems"
date: 2005-05-01
forum: Desktop Environments
---

### Post by haakon on 2005-05-01
I kind of mis-posted this to [http://www.ubuntuforums.org/showthread.php?t=11639](http://www.ubuntuforums.org/showthread.php?t=11639), so I'm trying again here. Background: I've set my computer-illiterate father up with Ubuntu. He's been using it since January. He's using a modem, and I was pointed to the excellent Modem Lights applets for non-root controlled dialup/hangup.

Now I've upgraded him to 5.04. In the new GNOME, the Modem Lights applet seems to be gone -- I cannot find it in the dialog to add stuff to the panel from. There's a different applet called Modem something, but that's really awkward to use, requires root access to dial up, and forgets options you enter into it so it doesn't actually work at all.

So my question: is Modem Lights gone from GNOME 2.10/Ubuntu 5.04? Or could there be a package I'm missing? (I installed ubuntu-desktop with all deps) Does anyone else have Modem Lights in the list of applets they can add?

Thanks for any help,
Haakon.

EDIT: Ok, I should have read more before posting. I now see that Modem Lights is gone and replaced by the inferior Modem Monitor, requiring root password (and, in my attempts, not working at all because it forgets properties as soon as I enter them and press Ok). Looks like I will have to get creative and learn my father some new tricks.

EDIT2: Sorry to be a little gloomy, but my father passed away suddenly late last year, long before his time. He had never used a computer before I built one for him and set up Ubuntu, and thanks to the friendly help of people on this forum and on #ubuntu, he was able to get a lot of joy out of his computer -- and I out of teaching him about it. So thank you again.

---

### Post by Ptero-4 on 2005-05-01
[QUOTE=haakon]I kind of mis-posted this to [http://www.ubuntuforums.org/showthread.php?t=11639](http://www.ubuntuforums.org/showthread.php?t=11639), so I'm trying again here. Background: I've set my computer-illiterate father up with Ubuntu. He's been using it since January. He's using a modem, and I was pointed to the excellent Modem Lights applets for non-root controlled dialup/hangup.

Now I've upgraded him to 5.04. In the new GNOME, the Modem Lights applet seems to be gone -- I cannot find it in the dialog to add stuff to the panel from. There's a different applet called Modem something, but that's really awkward to use, requires root access to dial up, and forgets options you enter into it so it doesn't actually work at all.

So my question: is Modem Lights gone from GNOME 2.10/Ubuntu 5.04? Or could there be a package I'm missing? (I installed ubuntu-desktop with all deps) Does anyone else have Modem Lights in the list of applets they can add?

Thanks for any help,
Haakon.

EDIT: Ok, I should have read more before posting. I now see that Modem Lights is gone and replaced by the inferior Modem Monitor, requiring root password (and, in my attempts, not working at all because it forgets properties as soon as I enter them and press Ok). Looks like I will have to get creative and learn my father some new tricks.[/QUOTE]
 You can install kdebase+kdebase-dev, then install kmodemlights (KDE equivalent of the gnome 2.8 modem lights applet) from [www.kde-apps.org](www.kde-apps.org) and finally set the kde panel (kicker) to run at startup so that he have modem lights in his box. (Or just install KDE).

---

### Post by haakon on 2005-05-03
I ended up fixing this like so: add a custom launcher to the panel, which on start runs this script:

```
#!/bin/sh
# Simple connect / disconnect script for ppp
# written by Jeffry Johnston, 2004
TITLE="Dial-up Connection"
ICON=/usr/share/icons/hicolor/48x48/apps/modem.png
ps ax | grep [/]pppd > /dev/null
if [ $? == 0 ] ; then
   zenity --question --text="Disconnect?" --title="$TITLE" --window-icon=$ICON
   if [ $? == 0 ] ; then
       poff
   fi
else
   zenity --question --text="Connect?" --title="$TITLE" --window-icon=$ICON
   if [ $? == 0 ] ; then
       pon
   fi
fi
```

I found this script at [https://bugzilla.ubuntu.com/show_bug.cgi?id=8890](https://bugzilla.ubuntu.com/show_bug.cgi?id=8890) . So the only thing lost is the counter for time spent online, but that's not critical.

After reading some around here, I added the user to the tty group just to be sure there would be no root password requirement, but to be honest, I have no idea if that's necessary or not.

---

### Post by puddleglum on 2005-05-26
Where did you place this script?

Also, did you ever find out if the removal of Modem Lights is a Gnome or Ubuntu
thing?  I'm pretty dependent on Modem Lights for information on my connection state, upload/download activity, etc.  Modem Monitor is not an acceptable substitute.  If it's only missing in Ubuntu, I'll jump to another Linux.  If it's Gnome 2.10 then I guess I have to hammer on them.

---

### Post by haakon on 2006-03-01
You can place the script anywhere you like, just make it executable. I placed it in /usr/local/bin, which I think is a good place.

The Modem Lights removal is a GNOME thing. I don't know if newer versions has a better solution, but they should better get one, because I agree Modem Monitor is a terrible replacement.

---

