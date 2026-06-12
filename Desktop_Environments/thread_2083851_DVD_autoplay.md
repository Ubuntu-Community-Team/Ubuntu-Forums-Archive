---
title: "DVD autoplay"
date: 2012-11-13
forum: Desktop Environments
---

### Post by TREESofRIGHTEOUSNESS on 2012-11-13
Hi I was posting this because I think that there has to be a way to enable Autoplay (for DVDs) in Lxde.  I have searched the Forums and found something, but there was no resolution.  I searched askubuntu, and the Lxde forums, and the internet on a few different search engines.... to no avail.

I think that there has to be a way to edit some config file somewhere to make the popup window use the vlc CLI options to auto play.  It would be nice to have a GUI like in Xfce4 where you can set up stuff.  Actually a centralized GUI for settings is a great idea, but I am no programmer, yet...

So a big preemptive THANKS to all who can help!

---

### Post by joke444 on 2012-11-13
It`s my experience with LXDE distros that none will autoplay except for Mint LXDE, and actually that only opens the window of your designated dvd player, the movie will not start playing automatically.   What I did to get around this is install Thunar which is the XFCE file manager which has the capability to autoplay any dvd    You also have to install thunar-volman which might be in the xfce-goodies package.  Not absolutely sure.  Then you have to configure autoplay with thunar.   This may not be what you want to do but it`s the best I can come up with.  LXDE after all is no frills.  Best of luck

---

### Post by TREESofRIGHTEOUSNESS on 2012-11-14
Yeah I really dislike the current tabless version of Thunar, so I don't want to use it as default volume management.  Autoplay isn't much of a frill I'd think, and besides Lxde is lightweight, not no frills.  I have xcompmgr enabled in Lxde... that is more of a frill than automounting and opening a video player for a DVD.  There has to be some config file or something that can be edited somewhere to add a line of code to make it work.

---

### Post by krackersk on 2012-11-15
You could maybe use a udev rule?

Not sure how to do it though

---

### Post by TREESofRIGHTEOUSNESS on 2012-11-15
> **krackersk said:**
> You could maybe use a udev rule?

Not sure how to do it though

Ok, that sounds more like it.  I wonder where one would look to find good udev documentation.  It seems like some setting should be changed for the default Lubuntu setup.  DVD drives are very common now, and on some very old hardware, As the newer hardware ages, people will be requiring this feature more, I think.

---

### Post by Dusenberg on 2012-11-15
Hi TREESofRIGHTEOUSNESS, 
I'm also looking for autostart of vlc in lubuntu when dvd inserted but have failed to find one.  Thought the udev route sounded good. Here's a link to some documentation I found. There's a section on 'Running external programs upon certain events' which seems to be what's needed.
[http://www.reactivated.net/writing_udev_rules.html]()
Haven't had time to try it yet.

---

### Post by TREESofRIGHTEOUSNESS on 2012-11-15
[http://www.reactivated.net/writing_udev_rules.html#example-cdrom](http://www.reactivated.net/writing_udev_rules.html#example-cdrom)
looks promising indeed
I really don't know much of anything, so I'll have to read way more into this whole issue.  I am glad to find there are people interested in solving this issue.  As laptops age it will be increasingly important to have a working DVD solution for the older hardware.  Xubuntu is nice, but still to heavy for my old laptop, it worked about as well as XP did.  Lubuntu is almost as fast as my newer computer.
Thanks for looking into this!!

---

### Post by Dusenberg on 2012-11-16
The following terminal command starts vlc and plays whatever is in the dvd drive.  The dvd drive is sr0 on my machine.
```
/usr/bin/vlc --fullscreen dvd:///dev/sr0
```

In theory that could be put in a shell script that would be executed from a udev rule using RUN.
 
I'm far from an expert here, but thinking about it more I'm not sure if udev will do the trick. From what I've read, it appears udev rules trigger when a device is created, like when a usb drive is plugged in. What we are looking for is to trigger vlc to start when a playable dvd has been put in to an existing drive - not a cd or a data disk. That sounds like a file manager-type event, which fits with the solution joke444 used. I may be wrong about udev of course.  

When I get more time I'll try with udev.

---

### Post by TREESofRIGHTEOUSNESS on 2012-11-16
That is exciting!!  If this works, I wonder if we can contact the Lubuntu people to put it in as default?  Just a thought....

---

### Post by TREESofRIGHTEOUSNESS on 2012-11-21
Yeah after searching more and more, and looking through the udev  stuff... I think udev could work, but the main thing is the volume  management issue.  PcmanFM does volume management (better than ever before) but  there are no visible options to configure what option is default for a given  program.  I guess joke444 has the "best" solution for now.... Though
 ```
 sudo apt-get install thunar-volman
``` pulls in xfce4-panel and a bunch of other  stuff...  I suppose nautilus will work too (and probably usurp my desktop  background).  

So, at this point it seems that I can workaround pcmanfm by learning how to make a udev rule with something like this:

```
KERNEL=="sr0", RUN+="/usr/bin/vlc --fullscreen dvd:///dev/sr0"
```or  I can install Xfce4's file manager....  still there seems to be another  way somewhere....  What is the config of the volume management for  pcmanfm?  can I edit that?  anyone know?

---

### Post by TREESofRIGHTEOUSNESS on 2013-01-01
Well it looks like udisk-glue might do the job.  I am not quite sure how to use it though...  halevt might also work as well.  There may even be more that might work.  Any ideas?

---

