---
title: "Disable blank screen if no activity"
date: 2009-02-19
forum: General Help
---

### Post by Nicador on 2009-02-19
Hello guys.
I have Ubuntu Server 8.10 Intrepid running on my box. I want my monitor to actually stay on, if, or I don't use the keyboard.
Using the forum's search engine and Google I managed to find different solutions but non worked.
I changed the BIOS setting for the blank screen after no activity to **never**.

```

root@blt:/etc/X11# xset dpms 0 0 0
xset:  unable to open display ""

```

```
root@blt:/etc/X11# ls
app-defaults  Xresources  Xsession.d        Xwrapper.config
xkb           Xsession    Xsession.options
root@blt:/etc/X11#
```

```

root@blt:/etc/X11# cat /etc/console-tools/config |grep BLANK
BLANK_TIME=0
# blanking method (VESA DPMS mode to use after BLANK_TIME, before powerdown):
BLANK_DPMS=off
# minutes _after_ blanking.  (POWERDOWN_TIME + BLANK_TIME after the last input)
root@blt:/etc/X11#

```

```

root@blt:/etc/X11# cat /etc/console-tools/config |grep POWERDOWN_TIME
# Powerdown time.  The console will go to DPMS Off mode POWERDOWN_TIME
# minutes _after_ blanking.  (POWERDOWN_TIME + BLANK_TIME after the last input)
POWERDOWN_TIME=0
root@blt:/etc/X11#

```

Please help. 
Thank you in advance!
Adrian

---

### Post by Nicador on 2009-02-19
Bump :(

---

### Post by Nicador on 2009-02-19
Solved!

```
setterm -blank 0
```

And I edited: /etc/init.d/console-screen.kbd.sh in the same way I did with /etc/console-tools/config.

---

### Post by Nicador on 2009-02-19
Seamns it's not working :|

Any ideeas anybody ?

---

### Post by Racecar56 on 2009-02-19
I thought you just solved it....
?

---

### Post by Nicador on 2009-02-19
Seemns not. Any ideea?

---

### Post by Nicador on 2009-02-19
Bump

---

### Post by Nicador on 2009-02-20
Bump

---

### Post by Nicador on 2009-02-20
I managed to make it work without your help.

Read here and learn ;) so that next time, a noob like me comes, you will be able to help him.
[http://pastebin.com/f2f9c3ec2](http://pastebin.com/f2f9c3ec2)

---

### Post by jespdj on 2009-02-20
Aren't you doing things much more difficult than necessary?

Look at **System > Preferences > Screensaver**. Switch off the screensaver.

Also look at **System > Preferences > Power Management**. Set it so that the display is never put to sleep.

*edit* Oh, I just relized that you're using Ubuntu Server and that you probably don't have the GNOME desktop installed.

---

### Post by Nicador on 2009-02-21
Probably not :)

---

### Post by kaligus on 2009-02-27
Mine has not been blanking until yesterday when turning off the screensaver and power management AND the previous changes to rc.local have quit working.

I remember my original solution being the rc.local because the GUI solutions did not work.

I did have to put the awesomeness back into rc.local today and other than some updates yesterday I do not remember installing anything else for several days.

So there could be something else running about half baked.

---

### Post by nikoz on 2009-04-18
into the Monitor section of /etc/X11/xorg.conf add (if not present)

        Option          "DPMS"

and then, put this in the ServerLayout section:

        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"

if you have multiple layouts add a &#8220;SeverFlags&#8221; Section 

Section "ServerFlags"
        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"
EndSection

---

