---
title: "945GM Intel Desktop Effects - Jaunty"
date: 2009-04-23
forum: General Help
---

### Post by bonfire89 on 2009-04-23
So, once again, Ubuntu has neglected my decently modern card.

I have been running Jaunty for all of 5 minutes

any tips on getting the desktop effects to work with the 945GM intel chipset.


here is my lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

Thanks a bunch. 
looks great otherwise

---

### Post by Sam Lars on 2009-04-24
If you run
```
compiz --replace
```
in a terminal, what does it tell you?

---

### Post by RD1 on 2009-04-24
Same chipset here and desktop effects are working fine. 

I know that doesn't help you but, the support is there. Ubuntu has not neglected your card.

---

### Post by jamessnell on 2009-04-24
Indeed, I've seen a few posts on the subject.. There's a "fix" out there for some common Intel Graphics related issues people are experiencing in 9.04 right now..

---

### Post by paradigm2 on 2009-04-24
> **bonfire89 said:**
> So, once again, Ubuntu has neglected my decently modern card.

I have been running Jaunty for all of 5 minutes

any tips on getting the desktop effects to work with the 945GM intel chipset.


here is my lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

Thanks a bunch. 
looks great otherwise

I don't have experience fixing this issue so canot personally help much, my apologies, but check these threads for experiences with the same card in Jaunty while it was in beta testing:

[http://ubuntuforums.org/showthread.php?t=1114093&highlight=945GM](http://ubuntuforums.org/showthread.php?t=1114093&highlight=945GM)

[http://ubuntuforums.org/showthread.php?t=1103916&highlight=945GM](http://ubuntuforums.org/showthread.php?t=1103916&highlight=945GM)

Some people might have been able to get it working with various workarounds and updates?

---

### Post by bonfire89 on 2009-04-25
> **Sam Lars said:**
> If you run
```
compiz --replace
```
in a terminal, what does it tell you?

```
$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1360x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
```



> **RD1 said:**
> Same chipset here and desktop effects are working fine. 

I know that doesn't help you but, the support is there. Ubuntu has not neglected your card.

How strange :/


> **paradigm2 said:**
> I don't have experience fixing this issue so canot personally help much, my apologies, but check these threads for experiences with the same card in Jaunty while it was in beta testing:

[http://ubuntuforums.org/showthread.php?t=1114093&highlight=945GM](http://ubuntuforums.org/showthread.php?t=1114093&highlight=945GM)

[http://ubuntuforums.org/showthread.php?t=1103916&highlight=945GM](http://ubuntuforums.org/showthread.php?t=1103916&highlight=945GM)

Some people might have been able to get it working with various workarounds and updates?

Thanks for the links, I'll check em out and get back if things change.



Thanks guys.

---

### Post by bonfire89 on 2009-04-25
Alright some improvement because of those links.

I set up X/Uxa and I have done a few reboots and suspended and came back up and seems to be a bit better now.

Here is the link for others who may need it [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

Also, what I think helped the most is that my virtual area in the /etc/X11/xorg.conf file was set for dual head purposes even though I am only using the external monitor (since I know Ubuntu wont allow otherwise)

But, I was able to run the desktop effects after changing the resolution, and it's running pretty much like intrepid now. Not awesome, but fine for most of my needs. I don't game, or even need the crazy desktop effects. I just want to watch youtube (partly adobes fault) and be able to see thumbnails when I Alt-tab which I can do now.

I just hate to see what happens if I attach my laptop to my tv when friends are over for youtube watching.



anyways. Enough ramble.
Thanks for the links. I wouldn't have gotten this far without them. Unfortunately I have only advanced from garbage to satisfactory. I should be able to to run dual head. but I can live with that. Good for now.

---

### Post by caro on 2009-04-25
I have the Intel 945 video card and could watch video just fine, but my compiz effects and screen saver were slow and jerky.  I reverted the Xorg intel driver back to the version in Intrepid and everything is fine now.  You may want to check it out.  

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

---

### Post by bonfire89 on 2009-04-26
good to know, I wasn't aware of that even being an option.

Right now it's running as good as intrepid so I don't think I will use the option, but, it could come in handy for someone else, so, thanks for posting.

Correct me if I'm wrong, but I wouldn't consider it fixed until it's running like it could in vista.

This is just making me want to buy a desktop for at home instead of using my school laptop. These graphic issues are getting old and tiresome. But. I do love Ubuntu and this wont cause me to even think about switching. Just for the record.

---

### Post by Stupendoussteve on 2009-04-26
Select the BSOD screensaver, don't touch your computer. It will eventually appear to run just like Vista.

---

### Post by jonboy99 on 2009-05-02
Caro, where did you get the gpg key from?  I can't find the relevant one anywhere, it doesn't seem to be on the page you linked to.

cheers
Jon

Edit - ignore that, finally found - shame they couldn't have just linked to the relevant PPA page, but then I am a newbie.

[https://launchpad.net/~siretart/+archive/ppa](https://launchpad.net/~siretart/+archive/ppa)


> **caro said:**
> I have the Intel 945 video card and could watch video just fine, but my compiz effects and screen saver were slow and jerky.  I reverted the Xorg intel driver back to the version in Intrepid and everything is fine now.  You may want to check it out.  

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

---

### Post by almikul on 2009-05-06
For those of you who are 'fine' now, try to run high-definition YouTube videos in full screen. Or try to run glxgears -info and compare it to Intrepid. You will see that reverting back to ver. 2.4 only fixes Compiz effects.

---

### Post by bonfire89 on 2009-05-06
yeah, although I have a nicer alt-tab experience, often I can barely play flash video.

It really sucks.

---

### Post by jonboy99 on 2009-05-06
Yep, full screen flash rubbish here too.  It needs sorting.

---

