---
title: "Bad Graphics driver removal without graphics interface"
date: 2009-06-07
forum: General Help
---

### Post by Dolf123 on 2009-06-07
Hi,
 
I downloaded a new ATI driver from the package manager, and it completely screwed up my display. I cannot do anything with clicking.
 
How do I fix this? I booted up in shell but how can I find out to remove what? I read somewhere that modprobe are the drivers. I am new to the command shell, I thought I could get by with clicking in this modern Ubuntu 9.
 
Or is there any "system restore" command somewhere? Like windows ?
 
Thanks,
 
Dolf

---

### Post by kpkeerthi on 2009-06-07
There is no system restore in Ubuntu. Thats why you should learn to backup your system so you can be on track in a snap.

To restore a working X, boot into Recovery mode (from GRUB menu). At the command prompt, enter
```
sudo nano /etc/X11/xorg.conf
```

Search for a line that reads (under Device section)
```

Driver "ati"

```
and change it to 
```

Driver "vesa"

```

Save and Exit. At the prompt, type **reboot** and boot into normal mode.

---

### Post by Dolf123 on 2009-06-07
Hi,
 
The file doesn't contain a "driver "ati"" .
 
It is build up like this:
 
Section "Device"
Identifier "Configured Video Device"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
EndSection
Section "Screen"
Identifier "Default Screen"
EndSection
 
 
Should I just add Driver vesa?

---

### Post by kpkeerthi on 2009-06-07
Just add it so the X will be forced to load vesa. vesa is a generic driver with 2D-only capabilities, but hey it gets you back to your Desktop and then you could possibly work on fixing the bad ATi.

```

Section "Device"
Identifier "Configured Video Device"
[COLOR="Red"]Driver "vesa"[/COLOR]
EndSection

```

---

### Post by Dolf123 on 2009-06-07
Thanks for your help, but it is still not working.. I added it and it doesn't change anything.

---

### Post by kpkeerthi on 2009-06-07
Do you have xserver-xorg-video-vesa installed? You can check with:
```
dpkg -l | grep xserver-xorg-video-vesa 
```

You can install it with
```
sudo apt-get install xserver-xorg-video-vesa
```

---

### Post by Dolf123 on 2009-06-07
"dpkg -l | grep xserver-xorg-video-vesa"
 
Tells me:
 
ii xserver-xorg-video-vesa 1:2.0.0-1ubuntu6
X.Org X server -- VESA display driver
 
 
So I did the apt-get just to be sure, am now rebooting to see if it helped.
 
Edit: It didnt help

---

### Post by Dolf123 on 2009-06-07
I inserted the Ubuntu CD, now I can browse my linux files ... would it be safe to just override some files ( i dont know which ones ) that have to do with drivers from CD to installed version?
 
Like, if I would copy the X11 folder from the CD to my installed version, would it help?
 
Or should I just backup and bail out?
 
Edit: How can I uninstall packages from the installed ubuntu? That would help because everything cocked up when I installed "ATI binary X.Org driver" from the Add/Remove menu

---

### Post by Mehashi on 2009-06-09
Hello! I am having the same problems as the original poster. 

Foolishly (I should have learnt my lesson from 7.10!) I thought I would try to install the Ati driver from the add/remove repositories. My display is basically blank, but with some random noise to the top and bottom of the screen.

I have tried the same fixes as described above with the same results, except my display now shows the noise and two distorted and random coloured ubuntu logos as well. Unfortunately I cannot load the system, I have tried name and password but it makes no noticable change to my noise or the black background.

I remember the first step mentioned here fixed my problems in 7.10 but has not helped this time. I also have the option to use my live cd, but I am not sure what I should do once it is loaded. It does not let me access my account on booting the live cd but I can mount that drive from a guest session so that is something!

Sorry guys despite using ubuntu for a while now I am still really a "Noobie" as it doesnt really break enough for me to have learnt much! Any help would be really appreciated! [COLOR=Magenta]^_^b[/COLOR]

---

### Post by Odemia on 2009-06-09
I had this issue with kubuntu 9.04 x86_64.  The fglrx driver is all messed up.

For me the first K/Ubuntu splash screen worked fine but then everything was as described by Mehashi when the login manager should have loaded.

If your install started going wrong after installing the "fglrx" package you can try doing what I did to get rid of it:
1) Restart and get to the Grub menu (You may need to press "Esc" during the boot to get the grub menu to show).
2) Selected the "(recovery mode)" option from the grub menu.
In my case it was "Kubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)", this brings up a list of options.
3) Scrolled down and selected root terminal.
This will log you in as root.  No window manager just command line.
4) In the root terminal enter "apt-get remove fglrx" and enter, then "apt-get autoremove" and enter.  Then "exit" followed by enter.
This removes the fglrx package and all dependencies and exits the root terminal.
5) Then selected continue boot.

There is also an option in the recover mode to reconfiguring X, running it will clean up any changes you have made to /etc/X11/xorg.conf.  Or you could try running "dpkg-reconfigure xserver-xorg" in the root terminal.

Hope that helps.

PS When are the ubuntu forums getting tab completion?  I can't get past "/et" without hitting tab!

---

### Post by Mehashi on 2009-06-10
Thank you for your help, I have a fully working system again, with all my previous desktop effects just as they were!

For anyone else having these troubles the step I had missed was to boot into recovery mode >> root or netroot, then:
```
sudo apt-get remove xorg-driver-fglrx
```To remove the driver then
```
apt-get autoremove
```To clear up unneccessary files.

After these steps, which I had missed you can go ahead and reconfigure the xorg.conf file. With any luck you will be back to a working system again!

Thanks for the help guys, and good luck to anyone else! 
[COLOR=Magenta]^_^b[/COLOR]

---

### Post by Odemia on 2009-06-11
Glad to hear you got it working again.

---

