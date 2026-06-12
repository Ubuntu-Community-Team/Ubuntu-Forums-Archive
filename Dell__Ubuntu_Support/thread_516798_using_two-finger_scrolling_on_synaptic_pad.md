---
title: "using two-finger scrolling on synaptic pad"
date: 2007-08-03
forum: Dell  Ubuntu Support
---

### Post by kmcq on 2007-08-03
hey everyone, recently i got a new macbook and several older dell laptops, ive really enjoyed the ability to scroll using two fingers on the track pad and ive wondered if there is a way to use this technology while running Ubuntu Feisty 7.04 on dell laptops... i did some research and came across some work by Stefan Kombrink but i have not tried using his patches or other software since they are over 2 years old...  has anyone been able to get this working since then? (note: synclient -l is not returning a var called "TwoFingerScroll" which according to one website was added in v0.14.5, and im running 0.14.6)

---

### Post by erimar77 on 2007-08-04
My Dell D610 kinda has that built into the right side of the trackpad.  It's just one finger though.

---

### Post by kmcq on 2007-08-04
no, i know what that is, thats what all the synaptic pads do by default and i dont want that

---

### Post by apswartz on 2007-08-04
While that would be great (I love the touchpad on my MacBookPro) hardware usually can't be forced to do something it wasn't designed to do.

---

### Post by switchcode on 2007-08-13
synaptics touchpads can detect 2 or 3 finger taps and scrolls..
[http://ubuntuforums.org/showthread.php?t=82850&highlight=osx+touchpad]("http://ubuntuforums.org/showthread.php?t=82850&highlight=osx+touchpad")
is this the thread you were referring to Kmcq?
My worry is the same; I want to enable 2 finger scrolling and 3 finger middle button, but fear for the age of these solutions =/

---

### Post by kgr132 on 2007-08-13
The thread you linked is pretty old. It states "Just for the record: You don't need the patch anymore since it's included in Synaptics from 0.14.5 on." I'm running a recent install of Feisty and **synclient -V** shows that I have driver version 0.14.6 straight from the install.

When I run **synclient -l** in a terminal, I see these two settings available with my driver version: VertTwoFingerScroll and HorizTwoFingerScroll.

I'm not sure about the two finger scrolling since I haven't tried it myself, but I've found I have more control over my Synaptics Touchpad with Linux than I do with Windows (Assuming you're not afraid to edit the settings directly):

The Touchpad setting are found in:
/etc/X11/xorg.conf
(use **sudo gedit** ... to edit the file)

Check this web site for some more details, and a sampling of some of the possibilities:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

Also you can refer to **man synaptics** for detailed explanations of the advanced features of the touchpad that are available using the dedicated driver.


Good luck.
-K-

---

### Post by doofus on 2007-08-13
I have a 2 year old Inspiron 9300 that I wiped  and install Fedora on when I got it.  I've since moved to Ubuntu (Feisty) and most things work from installation.  I don't have any bluetooth devices and I don't use the touchpad so I can't advise on those.  The recent release of [modem drivers]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400%2FE1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745")   helped, so much easier than "the hard way" (tm).

Wireless & wired lan work (intel wireless) work.
Sound works.
Nvidia :icon_frown: proprietary driver for 3d & gaming, yeah gaming :)

I have to say I am really enjoying Ubuntu on my Dell.

---

### Post by switchcode on 2007-08-14
Yeah; I should have posted last night as soon as I got this thing working.
  First thing I did was to add
 ```

          "VertTwoFingerScroll"   "1"
          "HorizTwoFingerScroll"  "1"
```

to my /etc/X11/xorg.conf in nano, hit CTRL+ALT+BACKSPACE.... And I killed by X; I had a message  saying that there was an error in my X config and that ubuntu would load just as soon as i had fixed it...
  So I rebooted in recovery mode, did
```
sudo nano /etc/X11/xorg.conf
```
and soon realised my mistake; I had omitted the word "Option" from the beginning of the both lines I had added to xorg.conf.. They should have looked like this;
 ```
       Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"

```
  All is good now; I have two finger scrolling on my Compaq PresarioC300 lappy, along with Beryl running the sexiest Emerald theme imaginable =D Happy days.

---

### Post by HokeyFry on 2007-12-12
Alright, yes, now I have two fingered scrolling!!!


One quick question though... when I lift my fingers from scrolling it likes to scroll down until pressure is applied to the touchpad. The only remedy to this so far i have found is to lift one finger, then the other. Since I do not want to think about how my fingers come off of the touchpad, is there something I can pass in xorg.conf to say "When there is no pressure, stop scrolling"?

---

### Post by alterKrieg on 2007-12-17
Awesome!  Works like a charm on my pavillion dv9500 with Gutsy.

UPDATE: Well, the vertical scroll works fine. I can't figure out why, but the horizontal scroll likes to jump through the page history in Firefox, so I disabled the horizontal and am enjoying the vertical two-fingered scrolling.

---

### Post by MikeRussell on 2007-12-19
No Dice on my Inspiron 1420 running 7.10 :(

---

### Post by varchar255 on 2007-12-30
Doesn't work on my Dell Inspiron 6000 either. "synclient -l" returns a line that says "VertTwoFingerScroll  = 1", so I assume it's just unsupported hardware :(

---

### Post by lusepuster on 2008-03-30
#10
That is due to a 'feature' in Firefox. You can disable this feature by following this guide: [http://www.semicomplete.com/blog/web/firefox-scrolling-fix.html](http://www.semicomplete.com/blog/web/firefox-scrolling-fix.html)

---

### Post by adult swim on 2008-03-30
this is cool, i have been wondering about this for a while and have never seen it around.  i realize this thread is old but i have a question, is there a way to allow a tolerance to picking up your fingers?  if on is before the other, then i scroll to the top or bottom automatically.  if there isnt a solution i guess i can just get my fingers more in snyc!

---

### Post by zergamat on 2008-05-04
adult swim
Have you found a solution to the scroling to the top or bottom problem ?!?
It's very annoying, making two finger scrolling usless. 

thx

---

### Post by Niels Olson on 2008-05-04
Didn't work on my Dell Latitude D820. It's an Alps glidepoint though, so maybe that's the issue. These guys with an Alps also ran into problems. [http://ubuntuforums.org/showthread.php?t=582707](http://ubuntuforums.org/showthread.php?t=582707)

you can check your hardware with this:

```
$ less /proc/bus/input/devices
```

and scroll down to the mice.

---

### Post by AdamsJourney on 2008-06-12
Didn't work on my Dell Inspiron 1720.  I confirmed from another post on another site that this is due to the ALPS  GlidePoint Touchpad not recognizing multitouch inputs.

I confirmed this by first running 
```
synclient -m 15
``` This gives you a read out of what your touchpad is receiving input wise. (the number 15 is just the amount of seconds of input this test will output) The column under the f represents the number of fingers the device is reading.  On my touchpad, no matter how many fingers I stuffed into the touchpad square,  the column under f never showed anything other than a 0 or a 1 :(

So if you run ```
cat /proc/bus/input/devices
``` and you see ALPS in the mouse section, you are stuck with side scrolling :mad:  If anyone knows how to get around this I'm all ears.

---

### Post by madonion87 on 2008-06-18
Yea I really want to get this feature to work too =(

(I have the same problem where it will just jump to the top/bot of the page)

---

### Post by Qalthos on 2008-07-11
To enable two finger scrolling on an Alps pad, you need to use EmulateTwoFingerMinZ.  The value is the amount of pressure on the pad before it decides you are using two fingers.  For example this in my xorg.conf gives me two fingered scrolling on my Dell 1420n:

```
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
        Option          "EmulateTwoFingerMinZ"  "120"
```

The initial minz value reccomended to me was 90, but that made Firefox freeze every 5 seconds or so, so I figured upping th number might help and it did.  Depending on how much pressure you use on your pad, the number may need to be adjusted accordingly.

Hopefully this will help a few of you out.

---

