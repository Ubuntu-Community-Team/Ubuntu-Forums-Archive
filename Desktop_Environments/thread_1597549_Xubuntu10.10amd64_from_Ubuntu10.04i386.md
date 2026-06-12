---
title: "Xubuntu10.10amd64 from Ubuntu10.04i386"
date: 2010-10-15
forum: Desktop Environments
---

### Post by Mike_tn on 2010-10-15
Hi :) This is kind of a fun post but I'm also interested in thoughts. 
There is a Question after the paragraph break, feel free to skip this intro and go there. Please allow me to ramble...my other forum visits wanted OS fixes. This is my first say-hello-to-Ubuntu-community post because I finally got it running the way I like! double YAY! I thank all the posters on the forums because I get a lot of help here and other Linux forums, and usually don't post on the thread at all.  As a new Linux user of a few months, I just got Ubuntu 10.04 i386 running well on a Dell laptop (CPU-64bit-i3core) after much basic Linux digging/learning. In fairly short time I struggled with all of this: My initial Wubi install bootup system was destroyed by the GRUB2 update, fixed that by starting over and going to a full partition install with dual booting W7 and Ubuntu with EasyBCD free software to set up the boot sequence. Then used EasyBCD again to fix the boot problem after the GRUB2 update I knew was coming.  Learned how to implement fixes for the proprietary broadcom b43 wireless driver to get online since internet is a must for Linux. Then got my laser mouse speed how I like it because the GUI fell short and common commands like *xset m...* didn't work, instead used the *xinput* terminal command and dropped a script for it into the startup applications. Played with bunches of Live Distros because I hadn't done much of that, I had installed Ubuntu without much Linux help or experience. My main draw to the internet was flickr and photography so I learned some GIMP and found the best RAW photo software (UFRaw). My plug on that >Ubuntu should keep GIMP in the LiveCD! And UFRaw too like Debian-Live does.  So here I am. Seems you never want to stop making it better.

Was wondering if I should just enjoy my new 32-bit Ubuntu Lucid, it's lovely, or possibly keep making my life nuts by switching to Xubuntu 10.10 64-bit for: speed (faster desktop, 64bit, make use of 4GB RAM), or because I have the CPU for it even if I maybe don't need it HA, and maybe just because 10.10 is the flavor of the month. How hard is it? Would you upgrade the existing Ubuntu10.04i386, or do a fresh install, or install Xubuntu to the empty partition of the same size sitting right next to it (which I have), or don't bother because what you have is fine and the speed is not that big of deal unless you need it for gaming or your job or something like that? Maybe I ought to rest and actually use it for something...my flickr friends think I dropped of the edge of the globe. Peace

---

### Post by 3Miro on 2010-10-15
I like Gnome (which comes with Ubuntu), however, I prefer XFCE (which comes with Xubuntu). XFCE is lighter on memory, its native components are snappier (like the file manager and panel applets), the default windows manager (xfwm4) has a few very nice features on top of everything that the default Gnome manger (metacity) has to offer. Furthermore, compiz (which is the program for visual effects) works fine on both (although it requires extra steps to setup in XFCE). XFCE and Gnome also share the same underlying framework, based on GTK, which means that the Ubuntu repository apps that are optimized for Gnome will run just fine (with Kubuntu and KDE for example, you will get an occasional incompatibility). On the other hand, XFCE does come at a small price. Some things are harder to setup (like shortcut launchers on the top menu) and there is a small number of other features that may be hard to setup.

If you want to check XFCE out, you can go to Ubuntu software center and install xubuntu-desktop. Then you can select between Gnome and XFCE when you login. Xubuntu 10.04 is good to check things out, however, I do recommend 10.10 as they have fixed a few annoying bugs (Ubuntu 10.04 vs 10.10 is pretty much the same in my view, Xubuntu 10.10 is a big improvement over Xubuntu 10.04). You can go from 10.04 32-bit to 10.10 32-bit with an upgrade.

32-bit vs 64-bit has been beaten to death on the forums, checkout the recurring discussions section. Basically, the speed boost is usually small and it becomes significant only for specific apps (like video encoding). 64-bit apps also use a bit more RAM. Furthermore, 64 also has occasional problems with some printer drivers and such.

I use 64-bit only for my desktop, however, my laptop seems to work a bit better with 32-bit (probably because it has a crappy CPU).

The only way to go from 32-bit to 64-bit is to do a clean install on your system.

At any rate, I always try to recomend for people to backup their stuff before making major changes.

---

### Post by Mike_tn on 2010-10-16
> **3Miro said:**
> I like Gnome (which comes with Ubuntu), however, I prefer XFCE (which comes with Xubuntu). XFCE is lighter on memory, its native components are snappier (like the file manager and panel applets), ...

If you want to check XFCE out, you can go to Ubuntu software center and install xubuntu-desktop. Then you can select between Gnome and XFCE when you login...Xubuntu 10.10 is a big improvement over Xubuntu 10.04). You can go from 10.04 32-bit to 10.10 32-bit with an upgrade...

32-bit vs 64-bit has been beaten to death on the forums, checkout the recurring discussions section. Basically, the speed boost is usually small and it becomes significant only for specific apps (like video encoding)...The only way to go from 32-bit to 64-bit is to do a clean install on your system...

At any rate, I always try to recomend for people to backup their stuff before making major changes.


3Miro thanks for the considered reply.  I'm going to try your suggestion and wait on the 64bit mainly because it's simpler than a new installation. My CPU is fine for anything but I originally went with 32 because people on forums said 64 was problematic and as a newbie I wanted to minimize my problems. I bet the i686 in 10.10 with the Xfce desktop will be happy snappy!  No doubt that it could be, I tried Debian-live 6.0SqueezeAlpha2 with its i686 and it flys in Gnome but again, am not going there either, a full install is not what I feel like at the moment. Plus I only worked out the online access in a handful of distros, Debian is not one of them. Appreciate the reminder to backup the system.  Will do. I continuously backup my data and any downloads. But I'll run Clonezilla too. I like to use Acronis TrueImageHome to backup but the 2010 version I have does not support ext4 filesystems, 2011 does. Clonezilla looked like it worked making the image, though I never restored with it. Will do it again and then upgrade to Xub and 10.10. Gimma a few days and I'll pop back in to report the drama, will it be :cry: or :-D ?

---

### Post by Mike_tn on 2010-10-16
don't know how to delete this

---

### Post by Mike_tn on 2010-10-24
> **3Miro said:**
> 
Xubuntu 10.04 is good to check things out, however, I do recommend 10.10 as they have fixed a few annoying bugs (Ubuntu 10.04 vs 10.10 is pretty much the same in my view, Xubuntu 10.10 is a big improvement over Xubuntu 10.04). You can go from 10.04 32-bit to 10.10 32-bit with an upgrade.

32-bit vs 64-bit has been beaten to death on the forums, checkout the recurring discussions section. Basically, the speed boost is usually small and it becomes significant only for specific apps (like video encoding). 64-bit apps also use a bit more RAM. Furthermore, 64 also has occasional problems with some printer drivers and such.
3 Miro
I discovered the Startup Disk Creator, never knew!  So instead of any hard drive install I made a persistent install on an 8GB flash drive with Xubuntu 10.10. I went for 64bit after running it live and printing with it.  Runs great. Put in a startup app for my mouse speed to be tweaked. Got the internet going with difficult b43 broadcom wireless even.  Enjoying it. Thanks for the encouragements! Mike

---

### Post by Mike_tn on 2010-11-04
Just a quick reply update.  
Installed the Xub10.10 64bit over Ubuntu 10.04 32 bit Lucid...and then back to Ubuntu again but 10.10 64 bit Maverick.
Main straw that broke the camel's back for the 1st switch: The Ubuntu Gnome standard version Main Menu items seemed to keep breaking on me when I made any normal changes in the GUI.  Nautilus wouldn't boot, fixed that, then Compiz wouldn't boot, fixed that, then main folder icons disconnected, fixed it but by then I decided the simplicity of Xubuntu though not too simple had an advantage.  Only thing I didn't like was no automatic partition mounting for each partition of the HDD that Xubuntu was installed on.  So learned about fstab file and fixed it with that.
BUT then noticed you can't even write to a USB. I was appalled.  Some other Xubuntu issues were the GUIs were ultra simplistic. Like if you set up a startup application you can't look at it or edit it later, you can only delete it.  The GUIs in general are too simplified, hardly any options.  I guess they don't break easily but there is not much there too break.  Sooo I went back to Ubuntu but upgraded to Maverick 64 bit.  It's nice.  I'll just stay away from rearranging the main menu and no messing with compiz.

No more posts now since this seems to be a thread turning blog. Have a nice day and thanks.

---

