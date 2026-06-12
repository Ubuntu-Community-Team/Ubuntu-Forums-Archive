---
title: "metacity/gnome twinview placement problem"
date: 2005-10-19
forum: Desktop Environments
---

### Post by tufkal on 2005-10-19
I have googled my head off on this and found lots of discussion about it, but very few soltutions.  I have my xorg.conf file setup with twinview, 1280x1024 on my LCD and 640x480 off to the side on my TV (svideo out).  Here is the device/screen sections.

```
Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
        Option "TwinView"
        Option "MetaModes" "1280x1024,640x480;1280x1024,NULL"
        Option "TwinViewOrientation" "RightOf"
        Option "ConnectedMonitor" "CRT,TV"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Monitor         "VA712b"
        DefaultDepth    24
        Option "TVStandard" "NTSC-M"
        SubSection "Display"
                Depth           24
                Modes           "1920x1024" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```

It works nicely, with my 1920x1024 I can slide Totem over to my TV, fullscreen it, and watch videos while I work.  I have done this in KDE for many years, and in other distros.  I just recently moved to Ubuntu for my main development PC.  

The problem is if I have a window open on my main screen (the LCD) and then i try to open another one, it opens it on the 640x480 TV screen.  According to what I read, it is due to metacity trying to make use of all xinerama screens as per it's natural behavior.  That is fine, as long as I can change it. 

In KDE, i could choose what xinerama screen (0 or 1) that new windows would appear on, no exceptions, everytime (not following some algorithm if free space < 200 pixels use other screen etc).  I can find no such option in gnome or the metacity configs I have located so far.

I can't possibly be the only ubuntu user using a twinview/xinerama setup who has this new window placement problem.  Any takers? :D

note:I am enjoying rediscovering gnome since the last time I tried it (pre gnome 2.0) so telling me to use kubuntu will get you a boot to the head ;)

---

### Post by tsvetan on 2005-10-19
Hi,
I have this problem with metacity too.
Just open a new window (gnome-terminal or smth. else) on your second screen and maximize it. Then all other new windows will appear on the first screen.
This workaround doesn't fully solves the problem, but helps... at least for me.

Best Regards.

---

### Post by tufkal on 2005-10-19
Yeah I have been using that workaround, but it is becoming a pain because if you have maximized windows on both, metacity starts making decisions for you again. :(

---

### Post by RawMustard on 2005-10-19
Metacity needs to die and its maker needs to suffer the bite of a thousand mosquito's.  It is the worst window manager I've have ever used.
It's so bad it makes you want to stick a fork in your eyes so you can't use a computer anymore.

When you have to open a window and strategically place it, so you can get the next window somewhere in the vicinity of your liking; tells you metacity was no where to be found when they were handing out usability features ](*,)

But it doesn't stop there, try doing a properties on a file on your main screen, only to have the property window open 300000000000000 pixels away, over the other side on your other screen ](*,) --  And just when you thought it was safe to look at your screen again, it will put something else no where you'd expect it, in fact, it will without doubt - put it somewhere where it knows is going to make you scream and reach for that fork!  I am totally convinced it was designed by mongrel's incorporated (TM) just to annoy people ](*,)

DIE METACITY, DIE!!!!!

---

### Post by el3ktro on 2006-01-26
So is there no solution yet? I'm pulling the hair out of my head for this. All I want is an EASY way to watch my videos on the TV. Yes, I can do something like DISPLAY=":0.1" xine ... or so, but that's not really a good solution that also my girlfriend could use. It sounds nice to be able to open Totem on the LCD and drag it over to the desktop, but if this strange problem persists, it's unusable again. I'm yet waiting for a video player which just has a simple "Play on TV" button. That shouldn't be so hard!!

Tom

P.S.: Could your post your complete xorg.conf with Twinview? Whats the difference between Xinerama and Twinview? Which is better?

---

### Post by ookami on 2006-03-31
I finally installed Ubuntu (Dapper) on my desktop computer yesterday after running Breezy om my laptop for some time. However the problem of Metacitys crappy placement routines is already driving me completly nuts!  I had all but forgotten that I installed this: [http://www.itee.uq.edu.au/~agn/ag_fedora/extras/](http://www.itee.uq.edu.au/~agn/ag_fedora/extras/) on my previous Fedora install. It worked perfectly so provided we can get a hold of that "one-line patch" wouldn't it be possible to make a similar modified .deb using apt-build or something?

---

### Post by TLE on 2006-08-15
I think I found a solution. Please read [this thread]("http://www.ubuntuforums.org/showthread.php?p=1381463#post1381463"), inparticular the last post

---

### Post by TLE on 2006-08-24
I have posted the solution in this HOWTO [http://ubuntuforums.org/showthread.php?t=242502](http://ubuntuforums.org/showthread.php?t=242502)

---

