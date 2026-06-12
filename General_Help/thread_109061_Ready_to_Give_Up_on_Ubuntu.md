---
title: "Ready to Give Up on Ubuntu"
date: 2005-12-27
forum: General Help
---

### Post by fontosaurus on 2005-12-27
I've had it.  I am so ready to quit on Ubuntu, it's not even funny.  I have the good ol' 915GM chipset that causes so many headaches it's not funny.

I have tried every trick in the book.  Even the 915resolution app, which reports back as seeing a mode for 1280x800 (24 bit).

Every time I boot up the machine, it comes up in 1024x768, and I have to go through and do the dpkg-reconfigure xserver-xorg so that I can run in my actual resolution.

This is unacceptable.  I have tried everything I can possibly think of to get this resolved, and pored over every listing for 915GM that I can come up with in these forums and in the wiki.  And no luck.

I'm starting to think two things:

1. I should have just bought a Powerbook and run Mac OS X.
2. I'm going to put away my shiny new laptop and wait for Ubuntu 6.04 to come up.

Neither of these is a pleasant thought, but right now, I'm so annoyed that I can barely see straight. :mad:

---

### Post by weltall on 2005-12-27
have you tried editing your xorg.conf manually?

```
sudo gedit /etc/X11/xorg.conf
```

and manually inserting your desired resolution in the 24-bit capable resolution area?  (dont forget to save).

---

### Post by briancurtin on 2005-12-27
try another distro. ubuntu is not for everyone, and everyone is not for ubuntu. if you cant get it to work, try something else.

people overlook that freedom of choice way too many times.

---

### Post by fontosaurus on 2005-12-27
[QUOTE=weltall]have you tried editing your xorg.conf manually?

```
sudo gedit /etc/X11/xorg.conf
```

and manually inserting your desired resolution in the 24-bit capable resolution area?  (dont forget to save).[/QUOTE]

Yes.  And it didn't help.  As I said, I've tried everything I can find in here.  Unless someone else has some magical idea, I got nuthin'.

---

### Post by fontosaurus on 2005-12-27
[QUOTE=briancurtin]try another distro. ubuntu is not for everyone, and everyone is not for ubuntu. if you cant get it to work, try something else.

people overlook that freedom of choice way too many times.[/QUOTE]

Other than the resolution issue, I'm already pretty entrenched on this system.  Switching distros would be too much of a headache.

And if it's got issues in Ubuntu, I'm willing to bet that that issue exists just about everywhere else.  (It seems to be something with X not recognizing the 915GM chipset.)

---

### Post by exkalibur on 2005-12-27
Did you try the Intel driver ? Go to Intel website, then to the support section for your 915 GM chipset and read the info about Linux issues....This might help.

Regards

---

### Post by thingy on 2005-12-27
Hi

I haven't searched the forums for any of your other posts so I don't know what you've tried so far...apart from the details you've mentioned in this thread.

I did a very quick google for that chipset and linux and came across this:

[http://www.bram.be/travelmate_4651lci.html](http://www.bram.be/travelmate_4651lci.html)

It seems this person did get Ubuntu working with that graphics card and so you should be able too as well, if you follow his method. I can see that your chipset is what is at fault here and not Ubuntu. For example:

"The 915GM can only support a limited amount of resolutions. These resolutions are pre-programmed in the BIOS. Some laptops have a special BIOS section where you can select these resolutions. The Acer travelmate 4651lci hasn't. Luckily you can overwrite the BIOS settings with a utility: 855resolution. The utility only overwrite the settings in the RAM memory so you can't do anything wrong with the BIOS itself. Note that there is also a program called 915resolution. This one should also work but 855resolution (despite it's name) also supports the 915 chip."

If you want someone to help you in real time, visit the ubuntu/kubuntu irc channel on irc.freenode.net and ask someone to help you setup xorg to work properly with your graphics card. Give as much detail as possible, using the pastebin service if needed and usually a clued up person who doesn't actually have your hardware, will still be able to talk you through how to get it working.

Let me know if the url pasted above proved useful or not. Did you already come across it and/or carry out similar actions?

regards,

JC

---

