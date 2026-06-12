---
title: "X going crazy! and no nvidia"
date: 2005-01-06
forum: Desktop Environments
---

### Post by eldados on 2005-01-06
Hi there,
I took u64 off my machine in favoure of a 386 (running 2.6.9-686) at last all is working my gdesklets and all is the way I want except for 2 problems:
1. there is no way i can get the nvidia working, (did on u64) following the Howto and changing my xorg.conf to "nvidia" and disabeling "GlCore" and "dri" but the x won't start, than I'm getting a screen from the install setting up my clock and apt-get! than I'm dropped into a root command line. I have to revert back to the "nv" driver and restart the computer to log in aa a user... very strange...

2. which is worse at the moment. I did an apt-get to install xine-ui and a few other xine packages, in the middle of the install the screen went crazy with giberish I had to ctrl+alt+backspace i got a new desktop and saying it backed up my old one! and at the moment i can only log in at 640x480!!! nothing has changed in the xorg.conf.
I really need a system that works :(
any ideas???

---

### Post by jbh on 2005-01-06
I have a Geforce 6800GT, and run hoary 64. Use a 32bit chroot to run any 32 applications. here's my nvidia settings:

removed all my screwed up drivers, then did this:

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable


edit xorg:
sudo vi /etc/X11/xorg.conf

Section "Device"
	Identifier	"NVIDIA Corporation GeForce 6800GT"
	Driver 		"nvidia"
	Option 		"RenderAccel" "true"
	Option 		"AllowGLXWithComposite" "True"
	Option 		"NoLogo" "1"
	Option 		"NvAGP" "3"
	BusID 		"PCI:1:0:0"
EndSection

then, x started ok, however i had no glxgears. so I did the following:

sudo ln -s /usr/X11R6/lib/modules/extensions/libglx.{so,a}



everything works now.

---

### Post by eldados on 2005-01-06
thanks mate, I'll try it when I get home after work (if she'll let me... :))
how hard was it setting a chroot for 32? I never did it b 4, where is the best place to look for? I might get U64 back on with chroot 32 for my other apps...

---

### Post by jbh on 2005-01-06
[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Building_a_clean_32bit_chroot_with_debbootstrap)

some things i changed in there was I didn't add this line to fstab, and didn't mount my CD-rom anywhere in the chroot:
```
/media/cdrom    /var/chroot/media/cdrom none    bind            0       0 
```
The part "Then mount (mkdir) each folder." means u mkdir the directory, then mount each one ie: 'mount /var/chroot/proc'



I didn't install any nvidia drivers in the chroot either, so avoid this:
```
sudo apt-get install nvidia-glx linux-restricted-modules-k7 linux-image-k7
```
I find my nvidia glxgears work fine running in the 64bit mode. 
I also skipped the install point2play/cedega stuff, i'll try that later whenever I want to try out linux gaming.





also this part:
```
sudo chmod 777 /usr/local/bin/do_dchroot
```
I had to change that line to "sudo chmod 777 /usr/local/bin/do_chroot" (took out the extra d)



now i just type 'dchroot -d' and it drops me into a 32bit shell where I apt-installed firefox, java, and the flash firefox plugin. i also ported win32 codecs there and other multimedia goodies.  then inside Gnome, I edited my firefox command line to read "dchroot -d firefox" so it runs it in 32bit mode. there has to be an easier way for all the above, but i'm a noob. plus the only way i could get gdesklets working was to upgrade to hoary, which was pretty much painless.

---

### Post by eldados on 2005-01-06
Beautiful mate!
thanks so much for taking the time to answer, this is cool, will put my U64 back on tonight...

---

### Post by jbh on 2005-01-06
it took me numerous tries, such as screwing around with locales. ubuntu forum search is your friend there. see if you can get Option "NvAGP" "1" to work, i can't get any agp doing with that option, so i just use NvAGP 3 to load 'agpgart' until i can figure a way out how to use nvidia's agp

---

### Post by eldados on 2005-01-07
Report:
All is going good again :D  nvidia is working and x looks cool again... thanks again for your help.
I will try AGP 3 later and will let you know, which program is best to test that with? runing glxgears I get the following error:
"Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual." 
so I guess a bit more work... :)

---

