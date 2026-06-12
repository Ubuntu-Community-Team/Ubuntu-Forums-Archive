---
title: "Ubuntu Freezing During Installation"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Chobo-Mog on 2006-06-03
Hey.  I've been having trouble installing Ubuntu on my desktop.

Whenever I try and install Ubuntu (either Dapper Drake or Hoary Hedgehog), or run a Live CD, it will always boot and lead me through most of the installation process without a problem.  It says that its setting up what seems like an endless list of components, and also says [OK] beside each.  However, after that the screen seems to refresh, and then just freezes on a blank, black screen.

It might be a compatibility issue with my hardware, since I had the exact same problem when I tried a friend's old Hoary Hedgehog CD last week, but it could be something completely different.

My PC's parts are:  

- Pentium 3 866mHz
- 384mb pc-100 ram
- 40gb master hard drive
- 250gb slave hard drive
- An LG® DVD+/-RW master optical drive
- DVD-ROM slave optical drive
- Audigy 2 ZS sound card
- ATI Radeon 7500 64mb video card, PCI Version
- Motherboard (Intel 810e chipset) with onboard 3Com 10/100 NIC and an unused onboard 4mb video card
- Aztech 56k/Fax modem
- An unused, but still installed, Creative PCI sound card

***  When I asked about this in the IRC channel, it was suggested that I try installing Ubuntu without the unused sound card and 56k modem since I didn't need them, and since they may be causing problems.  Unfortunately, I tried removing those two components and the problem still continued.  ='(

If anyone knows what might be causing this problem, or a possible way to fix it, I would greatly appreciate some help.  

Thank You ^___^

---

### Post by taurus on 2006-06-04
What kind of monitor do you have?  The problem could be your video card!  After the screen goes blank, hold down <Ctrl><Atl>F1 to get to a terminal, console.  Edit your /etc/X11/xorg.conf and use "vesa"  driver for your video card.  Otherwise, try installing it in text mode (the alternate version of Dapper) and configure X later or install the server version and then install X (Gnome) when it's done...

---

### Post by Chobo-Mog on 2006-06-07
I'm using a Dell e771p 17-inch CRT monitor, and its connected to my Radeon 7500 64mb PCI card.  The video card in my motherboard is unused.

I tried installing Dapper Drake again and encountered the same problem, unfortunately.  I tried pressing ctrl+alt+F1 like you said, but nothing happened.  It seemed that the installation was actually frozen since nothing I pressed on the keyboard was able to make the computer respond.  I really hope that there is some way to get Ubuntu working on my system.  

In case it might help, I took note of the last thing which was set up by the installer, just so you know exactly where it froze.  The last line displayed said, &#8220;Starting GNOME display manager&#8221;,  and then [OK] popped up beside it.  Once that finished, the screen seemed to refresh, as it had done a couple of times before, and I ended up on the black screen I mentioned in the first post.  The only thing which appears on that screen is a DOS-like cursor, in the top left corner, but it is not flashing like it normally would when waiting for something.

---

### Post by cdeszaq on 2006-06-14
I too am having this same problem on a Dell OptiPlex GX110 machine, 750MHz(or so) proc, 512MB Ram, unknown videocard...

If there have been any solutions found, please post them!

Also, when booting the Dapper Live CD to "Safe Graphics Mode," the X server fails and an odd command line interface comes up, but each line is offset from the line above it resulting in a nearly un-readable command line interface.

---

### Post by Chobo-Mog on 2006-06-15
I didn't think my PC model number would have made a difference with all the other specs there, but I'm actually using a Dell Optiplex GX110 as well.  With any luck we can get this fixed.

---

### Post by just4one on 2006-07-12
If your using a dell Optiplex GX110. then remove the pci video card and ues the on board card. reboot with the install cd and you should have no problems.

---

### Post by Chobo-Mog on 2006-07-12
If I remove my PCI video card, so only the onboard will be in use, will I be able to install the PCI video card again once Ubuntu is working?  Also, since I'm planning on dual booting with my already installed WinXP, how would it react if I suddenly removed my PCI video card?  I would have no problem with temporarily removing the card, for the Ubuntu installation, as long as I will eventually be able to use it again.

Thanks for the help.

---

