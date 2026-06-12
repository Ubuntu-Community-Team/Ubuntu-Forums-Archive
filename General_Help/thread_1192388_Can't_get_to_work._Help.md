---
title: "Can't get to work. Help?"
date: 2009-06-20
forum: General Help
---

### Post by Slane583 on 2009-06-20
Hello, I'm new to this forum as I just signed up. I saw Ubuntu in another location on the web and was curious with wanting to try it out. I'm used to Windows and since I haven't used Windows 95 or 98 like I did as a kid I kind of lost the know how with the commands to run stuff. Unlike the new stuff which is "easier" to use.

Okay, now. I dl'ed the 64bit version since I run an older Athlon 64. It burnt no problem to a disk and the disk starts up as it should. But when I try to do the demo it doesn't boot the cd on reboot.

I did this on another hd I have with XP on it as not to ruin my main drive. I also installed it to try it out and when I reboot it gives the choice between Ubuntu and XP like it should. But when I try to use Ubuntu it just has the little blinking white "loading" line on the top left of the screen and that's all I get, it doesn't load or do anything.

I was wondering, maybe because it's the 64bit version and my os is 32bit that it might not be working? Or maybe it's my motherboard because it wasn't on the list of motherboards "compatible" with Ubuntu?

I have no clue since I'm not a software "nerd" (no offence) and I'd really, really, REALLLY like to give it a try. Please help.

---

### Post by coffeecat on 2009-06-20
Hi. Welcome to the forum. We need to clarify a few things.

> **Slane583 said:**
> Okay, now. I dl'ed the 64bit version since I run an older Athlon 64. It burnt no problem to a disk and the disk starts up as it should. But when I try to do the demo it doesn't boot the cd on reboot.

Not quite sure what you mean here. Normally, when you boot from the CD you get a menu. If you choose the first, it boots into the Ubuntu desktop running live from the CD. You can then either just try it out, or install to the HD. You don't do a reboot for a demo. Or were you using the 'alternate' CD?

> **Slane583 said:**
> I did this on another hd I have with XP on it as not to ruin my main drive. I also installed it to try it out and when I reboot it gives the choice between Ubuntu and XP like it should.

Do you mean you managed to get the live desktop this time, and installed to the HD? Or were you using the alternate CD this time as well? Because...

> **Slane583 said:**
> But when I try to use Ubuntu it just has the little blinking white "loading" line on the top left of the screen and that's all I get, it doesn't load or do anything.

... if the CD runs live OK, it almost always runs OK from the HD. If you clarify what you mean here, we can take this further.

> **Slane583 said:**
> I was wondering, maybe because it's the 64bit version and my os is 32bit that it might not be working? Or maybe it's my motherboard because it wasn't on the list of motherboards "compatible" with Ubuntu?

The 32-bit version of Ubuntu will run fine with a 64-bit machine. It's possible you may be unlucky with your motherboard, but the compatible list is hardly comprehensive. Post details of your motherboard - it'll be useful to see which chipset it's using.

**Edit:** one other thing. You clearly managed to get a couple of bootable CDs, but there's a couple of things you need to know about. Did you check the md5sum of the downloaded ISO? Did you burn at a slow speed? Useful details here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Slane583 on 2009-06-21
Ok. Sorry for sounding confusing.

What I'm saying is. I dl'ed the iso file from the main page. It burnt on to the cd with no problems. I used the verify feature to make sure it was burnt properly.

Now. When I put the cd into the drive it boots and then shows this little window "menu" with three buttons. I think one is a learn more button, the middle is an install inside Windows I believe and the button at the top of the list says demo/full installation.

When I click on the demo/full installation button. It then pops up another little menu that says "Reboot required: To start the Live CD you need to reboot your machine leaving your cd in the tray. If your machine cannot boot from cd the last option should."

It gives the option to reboot now or reboot manually. When I do what it says it doesn't even do anything on reboot.

What I did was use the "help me to boot from cd" option under both of the two reboot options.

When I did this. It booted, brought me to what looked like an installation screen, did its task which didn't seem very long unlike a Windows install.

When it was "complete" it rebooted on its own and then brought me to the list that gives the choice to run Windows or Ubuntu. I tried running Ubuntu, it shows the little white line saying it's booting, and that's all it does. It doesn't go any further.



So what am I doing wrong?


As for the confussion of my version. What I meant to say is, my system does support 64bit, but my current os is 32bit. But I dl'ed the 64bit version of Ubuntu. Would it cause a clashing problem?

My motherboard is an ASUS A8S-X. I don't remember the chip set but my built in eithernet is an Intel chip. I think my bios is American Mega Trends. But I also don't know that off my head either.

---

### Post by Big_astur on 2009-06-21
Having Xp 32 and installing Ubuntu 64 is not a problem, i had it before moving completely to Ubuntu.

I never had your problems but maybe cause i just change in the BIOS booting order to boot first from the DVD/CD so it loads from there. Then you get the options coffeecat says: test ubuntu, install it, ...

---

### Post by coffeecat on 2009-06-21
> **Slane583 said:**
> Ok. Sorry for sounding confusing.

No problem. You're new to Linux which is a totally different animal from Windows (Hooray! :wink: ) - you have a right to be a bit bewildered. Even more bewildering is that there are two completely different ways of installing Ubuntu. I assumed (my bad) that you were attempting the regular way, but your post tells me otherwise....

> **Slane583 said:**
> What I'm saying is. I dl'ed the iso file from the main page. It burnt on to the cd with no problems. I used the verify feature to make sure it was burnt properly.

Now. When I put the cd into the drive it boots and then shows this little window "menu" with three buttons. I think one is a learn more button, the middle is an install inside Windows I believe and the button at the top of the list says demo/full installation.

When I click on the demo/full installation button. It then pops up another little menu that says "Reboot required: To start the Live CD you need to reboot your machine leaving your cd in the tray. If your machine cannot boot from cd the last option should."

You're describing wubi. Does [this page]("https://help.ubuntu.com/community/Wubi") look familiar? Wubi is a way of installing Ubuntu in the Windows C: partition. If you boot into Windows and look in My Computer, you'll find a C:\ubuntu folder - this is where Ubuntu is installed.

> **Slane583 said:**
> When it was "complete" it rebooted on its own and then brought me to the list that gives the choice to run Windows or Ubuntu. I tried running Ubuntu, it shows the little white line saying it's booting, and that's all it does. It doesn't go any further.

So what am I doing wrong?

Clearly, there's a problem with wubi - you're not doing anything wrong. Apart from a brief tryout with wubi, I have no real experience of it so I'm not sure what's wrong, but we'll come back to this.

> **Slane583 said:**
> As for the confussion of my version. What I meant to say is, my system does support 64bit, but my current os is 32bit. But I dl'ed the 64bit version of Ubuntu. Would it cause a clashing problem?

An interesting question. To be honest, I don't know. I'll see if I can find an answer.

Anyway - it sounds as though you have the regular live CD there. I guess you ran it from within Windows because that's how you get to the first screen in the above link. If it is a regular live CD, try this. Your computer must be set up to boot from the CD/DVD drive first - you may have to go into the BIOS and change the settings. Boot up from the live CD and you will see [the first and second screenshots]("https://help.ubuntu.com/community/GraphicalInstall") - the second screenshot there is the menu I was referring to. Instead of selecting "install Ubuntu" as that link says, select "Try Ubuntu without any changes to your computer" and it will boot up into the live desktop, running from the CD. Don't worry - it won't do anything to your hard drive, not unless you start the installer.  You can try the desktop out but it will be excruciatingly slow - be assured that when you do get it running from the hard drive it will be much zippier. On the desktop you'll see the install icon. Don't go there just yet. With the install application, you can install Ubuntu into its own partition(s) on the hard drive and set up a dual-boot menu, but this might involve shrinking the Windows partition, depending on your hard drive layout. Ubuntu installed this way is a much better option than with wubi, but it does involve changes to the partition layout.

That gives you a taste of Ubuntu, but back to wubi. I'll try to answer the 32/64-bit question - or someone else might be able to. If this is the problem then at worst you'll simply need to uninstall wubi-ised Ubuntu and install the 32-bit wubi Ubuntu. But have a think about whether you might prefer to install Ubuntu to its own partition from the live CD.

**Edit:** I've just re-read your post and it may be that you installed from the CD in the regular way after all - the first button in wubi gives you the chance to install from the CD in the regular way. An answer to one simple question will tell us whether you've got a regular or wubi-ised Ubuntu, and then we can go from there.

> **Slane583 said:**
> When it was "complete" it rebooted on its own and then brought me to the list that gives the choice to run Windows or Ubuntu.

This "list" - the boot menu. Does it have a line at the top saying, "Windows Boot Manager", or three lines at the bottom saying, "Use the (up) and (down) keys to select which entry ..... or 'c' for a command-line"? The first means you have wubi, the second is the grub menu and means you have a regular install.

---

