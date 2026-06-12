---
title: "Complete Newbie - Installation Problem"
date: 2005-09-11
forum: Desktop Environments
---

### Post by wncoutdoors on 2005-09-11
Hi all,

I'm brand-new to Linux, attempting to explore the benefits promised by this alternative to Windows for the very first time. So please forgive my ignorance!

I have sucessfully downloaded the ISO & burned a CD for Hoary 5.04 (i386 platform), and I installed a 2nd hard drive in my system to install it on.  I am running this on a new eMachines computer with an AMD Athlon 64 processor, 1gb of ram, whatever the default hardware is in there and a 20gb second Seagate drive as a slave to keep Linux completely seperate.  I had one problem during installation - having to do with ACPI. The installation would not continue - an error message stated "Perhaps changing your ACPI settings would help". Not sure what ACPI is, but I know it has something to do with USB. Disabling ACPI in the BIOS allowed me to proceed with the installation, which then seemed to go just fine.

So I ran the installation sucessfully, but after installing all the packages it attempted to load into KDE. I got the nice, blue Ubuntu logo along with a mouse cursor, which moves for a few seconds but then freezes entirely. That's where I'm stuck. I am able to boot to a command line by choosing "Recovery Mode" from ?grub, I think it is - the boot manager? but I can't do much from there (yet). Typing "exit" causes it to try to load KDE again, and I can get to that point by a hard reboot,  but again it will freeze.

So I'm kind of stuck - any help would be greatly appreciated. I'll be glad to provide any additional info needed - not sure what experts here would need to make suggestions. Thanks!

Sorry...I should have searched the forums before posting. Found someone with the exact same problem:
[http://ubuntuforums.org/showthread.php?t=64400](http://ubuntuforums.org/showthread.php?t=64400)

Any info you could contribute there would be great...

---

### Post by Takis on 2005-09-11
Welcome to the forums and the Linux community at large!

Firstly as a quick correction: ACPI is an acronym for Advanced Configuration and Power Interface - so it's actually to do with power control, not USB. It's the interface on a motherboard that allows you to do software-based shutdowns and reboots, without having to hit the big button on your computer.
[http://www.google.com.au/search?q=define%3A+acpi](http://www.google.com.au/search?q=define%3A+acpi)

Also that thread you searched seems to be getting a little out of hand, so let's see what we can do in this one.
[QUOTE=invalid]try using the noapic boot option[/QUOTE]
Have you tried this? You'll need to edit the GRUB options when your system boots. If this is total gobbledygook, say so and I'll give step-by-step instructions.

---

### Post by wncoutdoors on 2005-09-11
Yeah, that thread is a little crazy, but for more info - Bob described the problem I'm having exactly. Same machine, same error messages, everything. That's right - now I do remember from my old Computer Upgrade and Maintenance classes - ACPI is power configuration. Not sure why I related that to USB. Thanks for the Google link, could've done that myself, duh. Ok, so the message says "different ACPI or APIC" settings may help, and turning off ACPI in my BIOS did work, but broke Windows.

I know what GRUB is, i.e. the thing that lets you choose which OS to start, but ... options, I have no idea. So I've got Ubuntu installed, but no luck booting to the desktop. How would I set that option?

Thanks for the reply!

---

### Post by Takis on 2005-09-12
It should be by default the first option listed in GRUB. Something along the lines of:```

Ubuntu, kernel 2.6.10-5-k7
```

---

### Post by mlomker on 2005-09-12
His problem doesn't sound exactly the same to me.  His is hanging while loading firewire drivers and yours is hanging later on.  You could always (as a test) go into the BIOS and shut everything off that isn't totally necessary...USB, firewire, power management, the works.

Usually these sort of problems are the result of the BIOS on the system board doing something unusual.  Have you verified that you are running the latest BIOS from Emachines?  You might even try a BIOS from a different vendor that sells the same system board.

I wonder if your problem isn't the video card driver...have you ever booted up on a Knoppix CD?  Perhaps you could download one and see if the result is different.

The file for the video driver is /etc/X11/xorg.conf.  If you search on that you'll find some info.  I think you should try changing the driver to VESA from whatever it is....as a test.

---

### Post by wncoutdoors on 2005-09-12
You're right - it is hanging later on (when the desktop is loading). But I WAS having the exact same problem, to the T, when I first started out. That is, until I disabled ACPI in the BIOS. THEN, it started hanging when loading the desktop. I tried the noacpi option - didn't change a thing.

However, it may be a moot point. I tried what I could, but someone suggested I try the Xandros Open Circulation distro instead...hate to say it, but it installed/worked perfectly on the first try. Now, I need to start a new thread - "why should I use Ubuntu instead of Xandros" [http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=347484#](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=347484#)
Razz

Well, I'm not done trying different distros...so I may be back. Thanks!

---

### Post by mlomker on 2005-09-13
[QUOTE=wncoutdoors]Now, I need to start a new thread - "why should I use Ubuntu instead of Xandros" [/QUOTE]

No reason, really, if you like KDE.  I ran Linspire but switched to Kubuntu because I couldn't make it work well with my new laptop.  I think most linux people avoid Linspire and Xandros because they aren't free.

---

