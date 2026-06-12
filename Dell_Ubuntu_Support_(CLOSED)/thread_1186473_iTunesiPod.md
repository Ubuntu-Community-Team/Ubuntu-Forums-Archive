---
title: "iTunes/iPod?"
date: 2009-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CanadianBac0n77 on 2009-06-13
Hello, I am new here!

I was searching around and i was wondering if iTunes worked on Ubuntu? if Not what will be compatible with my iPod touch?

Thanks in advance!

---

### Post by JIMIneitor on 2009-06-13
This is a guide Ubuntu made, and that I used to make a script 

[http://www.ipodtouchfans.com/forums/showthread.php?t=199292](http://www.ipodtouchfans.com/forums/showthread.php?t=199292)

oh, and itunes will work on ubuntu under wine, but you wont be able to sync anything, unless you own an ipod, not an ipod touch nor iphone.

that is the only thing that ties me to windows
and its baaad to use windows!

Hi Five! First Post

---

### Post by hayden92 on 2009-06-13
Itunes has quite a shaky experience under wine, so I wouldn't highly recommend it.

You can use the default program "Rhythmbox" to sync your Ipod and things like that, but quite a few people prefer "Amarok"

Amarok won't be installed by default but if you want to try it out open up the terminal (Applications->Accessories->Terminal) and type:
```
sudo apt-get install amarok
```
It will ask for your password so type it, and when it is finished, you will find Amarok (Applicaitons->Sound and Video->Amarok)

I hope this is what you were looking for!

Hayden

---

### Post by CanadianBac0n77 on 2009-06-13
Thank You so much this was exactly what i was looking for!

Any chance Apple is going to make an iTunes for linux?

---

### Post by JIMIneitor on 2009-06-14
> **CanadianBac0n77 said:**
> Thank You so much this was exactly what i was looking for!

Any chance Apple is going to make an iTunes for linux?


who helped you?  :(

And i Dont see Apple doing anything for Linux anytime soon :(

---

### Post by CanadianBac0n77 on 2009-06-14
You both helped out!

Thanks!

---

### Post by anchorschmidt on 2009-06-14
You might want to try rhythmbox. It comes pre-installed. Go to Applications > Sound and Video

---

### Post by CanadianBac0n77 on 2009-06-14
i tried that but it was skipping (CD) alot...? I Just installed Ubuntu Yesterday so im fairly new to all this but im loving it! The only thing thats keeping me tied to my Vista Desktop Is iTunes and a few games/Programming things...

---EDIT---
since it was skipping i dont know if it was The Application it's self or the CD or even the CD-Drive... O-Well

---

### Post by JIMIneitor on 2009-06-14
dont worry, a few months ago i was still sticked to windows because of my itouch, but now i can sync it using the virtual machine and use linux mint for everything else

that will happen to you eventually   :)

---

### Post by enlli on 2009-06-14
I have an iPhone and need to use iTunes. I also had problems with TomTom Home. 
Solution was to run Vista in Sun Virtualbox which has proved a lot better than remaining dual boot

---

### Post by JIMIneitor on 2009-06-14
> **enlli said:**
> I have an iPhone and need to use iTunes. I also had problems with TomTom Home. 
Solution was to run Vista in Sun Virtualbox which has proved a lot better than remaining dual boot

i told you! 
thats the solution!

i dont even know why apple doesnt release itunes for linux, i mean, mac os is UNIX based too! 
its like they hate their OS brother and support their main competitor

---

### Post by JIMIneitor on 2009-06-14
sorry for the double post, but i have a good thing for you!

since you just installed ubuntu two days ago, you cant have many things there right?

so id rather use linux mint, since it is more windows like, and its based on ubuntu, so your experience will be almost the same

it has support out of the box for many restricted software that ubuntu doesnt have, and it has quite an elegant desktop!

[www.linuxmint.com](www.linuxmint.com)

---

### Post by CanadianBac0n77 on 2009-06-14
I think i just might try to install Sun's Virtual Box and start from there...

---

### Post by Jekshadow on 2009-06-15
Run Windows XP/Vista/7 in Sun VBox. Works great for me.

---

### Post by CanadianBac0n77 on 2009-06-15
Do you have a guide for Sun's Virtual Box? I just for some reason can't get it to work:(:)

---

### Post by themrfreeze on 2009-06-15
> **JIMIneitor said:**
> 
i dont even know why apple doesnt release itunes for linux, i mean, mac os is UNIX based too! 
its like they hate their OS brother and support their main competitor

Apple doesn't have a Linux version of iTunes because the iPod/iTunes combo sells a lot of Macintoshes.  It would be foolish of them to throw away the only MAJOR reason why a noob would spend 3x as much for a Mac instead of a Linux machine.

I'm a Mac -> Linux convert and I have an iPod, and I've found that Rhythmbox works well enough.  It's not as easy as iTunes (it doesn't autosync, and I don't think it'll accept Rhythmbox playlists), but at least the music gets on the iPod.

---

### Post by JIMIneitor on 2009-06-16
heres the guide you requested and that i have had already provided you:

```
 1.

      Add the Virtualbox repository and key as detailed on this page. Select the repository matching your distribution and add to /etc/apt/sources.list file. For example, the Intrepid Ibex line is:

      deb http://download.virtualbox.org/virtualbox/debian intrepid non-free

(You should change the "Intrepid" line with whichever Ubuntu Version you're using, and if you're not in Ubuntu, take a look at the VIrtualBox site) 

      Now add the key for this repository.

      wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add - 

      Now update your apt cache:

      sudo apt-get update

   2.

      Remove the package virtualbox-ose:

      sudo apt-get autoremove virtualbox-ose 

      Now install the latest Virtualbox, at the time of writing this is version 2.2.

      sudo apt-get install virtualbox-2.2 

   3.

      Add your username to the vboxusers group. Don't forget to substitute your username:

      sudo gpasswd -a YourUserName vboxusers 

(Replace "YourUserName" with yours, obviously)

   4.     We new entry in the file '/etc/fstab' to correct USB permissions. To do this, first you need to know what the group id (GID) is for the group vboxusers. Run this command:

      sed '/vboxusers/!d;s/vboxusers:x:\(.*\):.*/\1/' /etc/group

      The output should be a number. Now edit /etc/fstab and add the following line, but make sure you set the devgid= number to the output of the previous command.

      none /proc/bus/usb usbfs devgid=123,devmode=664 0 0 

   5.

      You can now start up Virtualbox, located under System &#8594; Sun Virtualbox . Create a new machine; the wizard will guide you, the details are outside of the scope for this howto. Within the settings for the machine, ensure both "Enable USB Controller" and "Enable USB 2.0 (EHCI) Controller" are ticked. You can also add a filter to make the iPhone/iTouch automatically pass thru here, otherwise you will have to manually select and enable it when plugged in.
   6. Install Windows and iTunes in the VM. Windows XP and iTunes 8 is known to work. The Virtualbox guest addons are also recommended for performance and integration, but are not explicitly required. Again, the details of this are outside of scope, but are straightforward. 

7. Boot the VM, plug in iPhone (and select it to be passed thru via the VM menu if you didn't add a filter before) and confirm iTunes detects it. All systems go for iLaunch!

Note: I (JIMIneitor) tested this ny myself, and tested everything, evend restoring, and I can say that everything works excellent but restoring, you can sync, back-up, install apps, remove apps, everything, but you won't restore it using VirtualBox.

Troubleshoot

   1.

      iTunes error 0xe8000035: Windows sees the iPhone correctly, and attempts to download pictures, but iTunes doesn't connect correctly. One cause of this is MAX_USBFS_BUFFER_SIZE being too small in /drivers/usb/core/devio.c. The author had this problem in Hardy Heron. Here is how to recompile "only" this module for Hardy (thanks to remainder comment 2008-09-21 04:22:26):

      cd /usr/src
      sudo apt-get build-dep linux-source-2.6.24
      sudo apt-get install linux-source-2.6.24 build-essential
      tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2
      cd linux-source-2.6.24/drivers/usb/core
      sudo perl -pi.bak -e 's/16384/131072/' devio.c
      make -C /lib/modules/`uname -r`/build/ M=`pwd` modules
      strip --strip-debug usbcore.ko
      sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
      sudo depmod -ae
      sudo update-initramfs -u
      sudo reboot

      You could instead modify /drivers/usb/core/devio.c and recompile the whole kernel if you wanted to. Note that this error can also occur for lots of other reasons, including bad cables, 3rd party docks etc. Ask Google about this error for lots of other possibilities.
   2. The VM seems to lock up at boot if an iPhone is plugged in at boot time. Try booting without the iPhone plugged in!
```


Or the script i made to make the whole process easier, just make sure to read it all to follow the directions:
[script](cid-0946f1a5078fb715.skydrive.live.com/self.aspx/virtualbox/VirtualBox.sh")

---

### Post by barlas on 2009-06-21
Is there any way to restore/update to newer firmware, using VirtualBox (or any other way in linux)?

---

### Post by loveandequality on 2009-06-21
I got my touch 2g working you need to jailbreak first tho but i made a guide so if you want check out my stuff plus mines sync by USB no SSH.:popcorn: VERY SIMPLE.

---

### Post by loveandequality on 2009-06-21
> **barlas said:**
> Is there any way to restore/update to newer firmware, using VirtualBox (or any other way in linux)?
Vbox is the only way & get the one that supports USB and while updating you need to check the USB as it will not continue because the ipodtouch chnges from dfu mode to apple recovery mode to ipod.

---

### Post by CanadianBac0n77 on 2009-11-20
> **loveandequality said:**
> I got my touch 2g working you need to jailbreak first tho but i made a guide so if you want check out my stuff plus mines sync by USB no SSH.:popcorn: VERY SIMPLE.
 
i know this post is.... DeAd, but hopefully i could get that guide? i just wanna be able to view/play my songs on my ipod touch (2G jailbroken). is there some software for that?

---

