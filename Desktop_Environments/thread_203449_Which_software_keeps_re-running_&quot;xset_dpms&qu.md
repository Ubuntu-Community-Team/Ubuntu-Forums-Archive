---
title: "Which software keeps re-running &quot;xset dpms&quot;?"
date: 2006-06-25
forum: Desktop Environments
---

### Post by HippoMan on 2006-06-25
I'm running KDE under Dapper, and I'm another person who's struggling with unwanted screen blanking, despite everything that I have tried.

In summary, I turn off all DPMS-related parameters, both in **/etc/X11/xorg.conf** and via the** xset** command, but after a while,  these parameters get mysteriously turned on again, and my screen starts blanking.  I can't figure out what software might be resetting these parameters.

Here are all the things I've done, and my proof that these parameters are indeed being reset:

I have the following commands in an executable called **.kde/Autostart/00-start** under the home directory of the user ID that's running KDE and which I log into:
```

/usr/bin/xset s noblank
/usr/bin/xset dpms 0 0 0 -dpms
{
  xset q
  date
} >>/tmp/xset.out 2>&1

``` The reason for the code whose output is being redirected to **/tmp/xset.out** is to confirm that the **xset** commands are indeed being  invoked and are properly functioning. And they are, as is shown by the following info which appears among this output every time I log in:
```

Screen Saver:
  prefer blanking:  no    allow exposures:  yes
  timeout:  0    cycle:  600
... etc. ...
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled
``` Also, I have the following lines in **/etc/X11/xorg.conf**:
```

Section "Monitor"
        Identifier      "Dell Inspiron 9300 Screen"
        HorizSync       28-96
        VertRefresh     43-60
        ##Option                "DPMS"
EndSection
``` ... and these:
```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "OffTime"       "0"
        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
EndSection
``` (I've also tried this with "off" in the **Option** lines instead of "0", with no difference in behavior)

Despite all of this, after an hour or so after logging on, if I manually invoke **xset q**, the DPMS-related values have changed to the following:
```

DPMS (Energy Star):
  Standby: 3600    Suspend: 3600    Off: 7200
  DPMS is Enabled
  Monitor is On
``` So ... what program or subsystem could be resetting these DPMS parameters?  And more to the point, how can I stop this from occurring?

Thanks in advance.

---

### Post by dmartinsca on 2006-06-25
I haven't used KDE in a while, but doesn't the screensaver program it uses have settings for screen blanking?

---

### Post by HippoMan on 2006-06-25
Well, I forgot to mention that I have **kscreensaver** disabled.

---

### Post by vigleik on 2006-06-25
[QUOTE=HippoMan]Well, I forgot to mention that I have **kscreensaver** disabled.[/QUOTE]

Did you turn off the *gnome* screensaver? Try 
$gnome-power-preferences &
and see if there's something there. I've had trouble avoiding screensavers too, but I think I finally managed, after 
1. turning off the kde screensaver
2. turning off the gnome screensaver
3. turning off powersave with gnome-power-preferences
4. editing my xorg.conf file, commenting out the DPMS option.

In my opinion that's way too many steps for such a simple thing. When things like this are on as default, they should be easy to turn off. The same goes for autorun, but I digress.

Vigleik

---

### Post by HippoMan on 2006-06-28
Thank you very much, vigleik.

Yes, unfortunately, I've done all the the things you have mentioned.

But I'm hopeful that eventually, I'll figure this out.

---

### Post by HippoMan on 2006-07-04
... and I have now figured it out.  I've been running **xscreensaver** instead of **kscreensaver**, and it has a **Display Power Management** configuration section.  Once I disabled all of that stuff, my problem went away.

Yes, I know that this is pretty obvious, and I should have thought of it earlier.

But all's well that ends well.

Thanks to all of you for your suggestions and help.

---

