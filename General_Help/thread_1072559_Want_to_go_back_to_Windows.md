---
title: "Want to go back to Windows"
date: 2009-02-17
forum: General Help
---

### Post by toobad22 on 2009-02-17
Help me stop this endless circle jerk. 
Installed ubuntu, now I do not want it and want to go back to Windows. All my programs that I need will not work with it.

It has taking over my BIOS and will not let me get off this 4 day nightmare.
Have tried to reinstall windows, but will not let me. 
Tried ultimatebootcd and nuked the hard drive with Darik's Boot And Nuke. Still will not take the windows disc. It just hangs at
Verifying DMI Pool Data ................
Boot from CD : _

I have set the BIOS to boot from CD

I have pulled the drive out and put it in a windows machine and it does not find it.

How can I format this drive to windows NTFS system.

Please - Please help me!
Thanks

---

### Post by Thelasko on 2009-02-17
Sounds like your hard drive is busted.

---

### Post by HermanAB on 2009-02-17
Windows is too dumb to understand Linux partitions.

You need to boot with a Linux live CD and delete the first little bit of the hard disk in order to erase the partition table.  After that, Windows will be able to use the disk again:

# dmesg
see what the drive number is

# dd if=/dev/zero of=/dev/sdx bs=1K count=10
where sdx is the device name of the HDD, probably sda if it is the only HDD.

Anyhoo, the solution to your original problem is to install VMware or Virtualbox and make a WindowsXP virtual machine for your one or two applications that require Windows.

Cheers,

Herman

---

### Post by Martje_001 on 2009-02-17
Hmm.. seems that your cd-drive or cd is kaput. Have you tried cleaning your disc?

And btw, Ubuntu cannot 'take over' your BIOS.

If you manage to get your machine booted from cd (Vista / XP) you can just delete your partitions and install Windows on it.

---

### Post by stchman on 2009-02-17
> **toobad22 said:**
> Help me stop this endless circle jerk. 
Installed ubuntu, now I do not want it and want to go back to Windows. All my programs that I need will not work with it.

It has taking over my BIOS and will not let me get off this 4 day nightmare.
Have tried to reinstall windows, but will not let me. 
Tried ultimatebootcd and nuked the hard drive with Darik's Boot And Nuke. Still will not take the windows disc. It just hangs at
Verifying DMI Pool Data ................
Boot from CD : _

I have set the BIOS to boot from CD

I have pulled the drive out and put it in a windows machine and it does not find it.

How can I format this drive to windows NTFS system.

Please - Please help me!
Thanks

Sounds like the CD drive or the disc.  Let me guess Ubuntu broke your CD ROM.

Ubuntu does not cause the BIOS to do things.

---

### Post by Slim Odds on 2009-02-17
> **stchman said:**
> Sounds like the CD drive or the disc.  Let me guess Ubuntu broke your CD ROM.

Ubuntu does not cause the BIOS to do things.

Amen and amen.....

I am **extremely** tired of the "Ubuntu did a bad thing" posts.

It's just software. It's not magic voodoo juju.

---

### Post by toobad22 on 2009-02-17
Thanks for the help. A friend of mine figured it out. It was a bad battery. 
You know I have read over 100 or so posts of people having the same trouble of getting rid of ubuntu and every one had a different answer on how to do it.

So, can you see why I blamed the software? Sorry about that!

---

### Post by Joneerickson on 2009-02-17
?Are your sure that you searched for the Linux Substitute for Your Needed Programs?
?Are you sure that WINE will not open your "Needed Programs"?

The only Needed program I can't find a Substitute for, is Quickbooks [can't believe linux people  haven't made a port of it yet] and WINE opens that.

---

### Post by Slim Odds on 2009-02-17
> **Joneerickson said:**
> The only Needed program I can't find a Substitute for, is Quickbooks [can't believe linux people  haven't made a port of it yet] and WINE opens that.

What doesn't GnuCash have?

---

### Post by perlluver on 2009-02-17
Let's be nice fellows, sometimes you just need Windows.  Original Poster hope you got it worked out.

---

### Post by FXEF on 2009-02-17
> **perlluver said:**
> Let's be nice fellows, sometimes you just need Windows.  Original Poster hope you got it worked out.

Sometimes you just **[SIZE="4"]THINK[/SIZE]** you need Windows.

---

### Post by perlluver on 2009-02-17
Some people just prefer Windows, no reason to stop them.  If you try that will make them hate the Linux community.  Why not, let them go ahead and use what works for them?  If Linux works for us that is fantastic.  If it doesn't work for him, he is entitled to run Windows or whatever else he chooses.

---

### Post by Kain000 on 2009-02-18
> **perlluver said:**
> Some people just prefer Windows, no reason to stop them.  If you try that will make them hate the Linux community.  Why not, let them go ahead and use what works for them?  If Linux works for us that is fantastic.  If it doesn't work for him, he is entitled to run Windows or whatever else he chooses.

I have to say it.....

allegory of the cave anyone?.... 

lol jk True sometimes you do not have a nice opensource choice for mission critical things and are forced to re-visit the slums of MR. Gates/Baulmer, 

example:  I have been using the opensource KTech Lab for nearly all my electronics classes, circuit diagram and sim, BUT alas it has but a generic diode and and I was forced at long last to VM xp back to life and use multisim.

---

### Post by AcidHawk on 2009-02-18
> **FXEF said:**
> Sometimes you just **[SIZE="4"]THINK[/SIZE]** you need Windows.

There are 2 things at the moment that I can't do without widows for.  
[LIST]
[*]Visio - There just isn't a viable linux alternative
[*]Windows Services - I support the development of software of which many runs as windows services
[/LIST]
However for both of these I use Vbox with an XP virtual machine.

I definitely believe that as long as there are people that use Windows on their machines, and I want to make a living, I will need at least a windows virtual machine to emulate their experience.

---

### Post by rbmorse on 2009-02-18
> **Slim Odds said:**
> What doesn't GnuCash have?
End of fiscal year close out, for one thing. 

I use GnuCash, but find the whole reports area sort of substandard compared to Quickbooks. If you ask about it you get a polite "learn Scheme (or is it Guile?) and write it yourself" answer.

---

