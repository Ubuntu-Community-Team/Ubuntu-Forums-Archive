---
title: "Notification ballons on Karmic Koala"
date: 2009-11-01
forum: Desktop Environments
---

### Post by ricpat51 on 2009-11-01
hi everyone,
I'd like to know how to configure the Notification ballons that appears on the desktop when some event occurs cuz it's been showing up near to the middle of the screen rather than close to the up right corner where it used to be shown. The curious thing is that it occurs only to some events like when changing songs in rhythmbox. I'll post a picture for visualization.

[IMG]http://lh4.ggpht.com/_Szv5NPXunkc/Su0YDdyZCJI/AAAAAAAAAH0/GjA44_xSWZk/Captura_de_tela.png[/IMG]

I'd like it was placed in the up right corner. There's a way to configure that? Thanks in advance for any help.
I apologize for my English as well.

regards

---

### Post by shafin on 2009-11-01
This is placed there by design, and I dont think there is a way you can change the position. Notifications are meant to take your attention, and user interface experts figured out its more in the face in its current position, hence the position change.

---

### Post by bakhy on 2009-11-01
Is this change related to the fact that Empathy and Pidgin no longer display notifications when someone goes online or offline? (Yes, I configured both to do that.)

Btw, I think it's ugly, having some notifications pop up in the usual place, and some away from the top.

Edit - Sorry, but they seem to work fine with Pidgin. It's just Empathy...

---

### Post by ricpat51 on 2009-11-01
thanks guys for your help.
well it's kind of weird I think even more when in previous versions, like jaunty for example, it didn't happen. In jaunty all the osd notifications where placed in the top right corner. It looks like a bug for me.:(

regards

---

### Post by chickencaesar on 2009-11-01
There's a fix for this.

Notifications are handled by the package notify-osd. What we have to do is replace the default version with one from Julien Lavergne's PPA.

First of all add the following two repos to your sources list: 
[FONT=monospace]
[/FONT]deb [http://ppa.launchpad.net/gilir/updates/ubuntu](http://ppa.launchpad.net/gilir/updates/ubuntu) karmic main [FONT=monospace]
[/FONT]deb-src [http://ppa.launchpad.net/gilir/updates/ubuntu](http://ppa.launchpad.net/gilir/updates/ubuntu) karmic main

Then add the signing key:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0EF28BC1
 
and reload the package info:

sudo apt-get update

Then you can find notify-osd in Synaptic and install the new package. Once you've done that all the notifications will go back to the top right-hand corner where they belong.

(H/T [http://www.webupd8.org/2009/10/things-to-fix-tweak-after-installing.html](http://www.webupd8.org/2009/10/things-to-fix-tweak-after-installing.html))

---

### Post by ForestTraveler on 2009-11-03
I thought this might be a bug as well. It looks very strange. I'm not sure if it actually catches my eye more, but I know that it annoys me when I do notice it.

---

### Post by meanderthalz on 2009-11-10
Would you know where I could look for help fixing my balloons. I applied the PPA so they now appear in the correct location, however they only appear as lines and blocks of purple or green.

[IMG]http://farm3.static.flickr.com/2741/4093756245_6127a0ee85.jpg[/IMG]

---

### Post by yocec on 2009-11-12
Same bug, only green ballon with strip

Any idea ?

---

### Post by ayampanggang on 2009-11-12
I was just googling for this very issue. I think while it might be good if there's an setting that allows it to be changed, personally I'm already used to the old, bigger notification, which doesn't appear a bit to the middle vertically like this.

---

### Post by meanderthalz on 2009-11-17
I found this:

> 
           After living with this problem for a long time and a few hours of playing around I found a fix. I created an xorg.conf file and added one line to the Device section changing to EXA instead of XAA, leaving all defaults the same. Here's the important part:
 Section "Device"
        Option     "AccelMethod"                "EXA"
        [...]
EndSection
 Why does this work? For some cards like some models of Mobility Radeon the developers decided to change the default from EXA to XAA for performance reasons. Most other ATI cards default to EXA, but some default to XAA. Even if you think you know what it should default to, double check it. Changing the AccelMethod fixed my problems.

        


at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001)

I don't know how to update conf files manually so I'll have to wait until I reboot to see if it fixes the notification balloons and Gnome-Do, but some users at [http://https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001]("http://https//bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001") said it  worked.[URL="http://https//bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001"]
[/URL]

---

### Post by meanderthalz on 2009-11-18
The Fix from the launchpad site worked. Notifications from Rhythmbox and Gnome-Do now appear correctly. However, I do notice that Xorg has a permanent place at the top when I run top in the terminal. I don't know if this is normal, but my system seems to be running fine so I'm not going to worry about it. Now, if only I could get my wireless card to access WPA protected networks . . .

---

### Post by Jota37 on 2009-11-22
Opa!

"user interface experts"?? I hope the so-called "experts" in question were not paid for this work, because these Notify OSD modifications are an abomination, seriously. It worked very fine on Jaunty. Since I installed Karmic, it has been terrible, and really irritating. My install must be broken, because nobody could have thought this abortion was a good idea.

"Best" thing: it can't be configured by the user. What is this, Mac OS X? No offense, but are the intended users mentally challenged, I wonder? Not even some hidden way to change the thing, like in gconf-editor or the like, so as not to traumatize hoi polloi? C'mon.

Now, the position of the notifications itself is weird enough; on a netbook's small screen it interferes a lot with the content. But I could live with that, that's not the worst.

The worst is that the damn OSD is "not clickable", so there is no way to dismiss it. There's more: when the mouse pointer is placed on top of it, the OSD disappears, and reappears when the pointer is moved away. The notification stays on screen for a long time (it seems like 5 seconds at least, probably more), at least for the network manager applet and for Rhythmbox, so I assume the behavior is the same for all apps. 

(Edit: I just timed one of the notifications from Rhythmbox and it took about 10 SECONDS for it to disappear. Beautiful.)

Please, tell me this is a problem of my install of UNR 9.10 and not the intended behavior of Notify OSD. Please. I think I'm not upgrading my computer at work from 9.04 until this notification system grows back a brain.

Edit: I just timed one of the notifications from Rhythmbox and it took about 10 SECONDS for it to disappear. Beautiful.

---

### Post by Strongman332 on 2009-12-29
try this it works

[http://www.ubuntugeek.com/how-to-restore-notifications-position-in-ubuntu-9-10-as-they-did-in-ubuntu-9-04.html](http://www.ubuntugeek.com/how-to-restore-notifications-position-in-ubuntu-9-10-as-they-did-in-ubuntu-9-04.html)

---

### Post by jellyfisharepretty on 2010-01-10
I agree with Jota37.  I was looking for a way to change the duration of the notification.  It seems it stays on way too long, and it's placement interferes with UI buttons I commonly use.  The most irritating behavior is that hovering the mouse over it seems to reset the timer for the notification to close.  That's especially annoying when you want to go click something that's under the box!  Now you'll have to wait 5 more seconds...

I wish there was an "x" at top right of the box for closing it (middle mouse could do the same).  Right-click could allow you to configure stuff like placement and duration... Wouldn't that be somewhat consistent with how most applications behave ?

I do like the idea and the look of the OSD notifications though.  It's just that the usability doesn't seem to be allright at this point.

---

