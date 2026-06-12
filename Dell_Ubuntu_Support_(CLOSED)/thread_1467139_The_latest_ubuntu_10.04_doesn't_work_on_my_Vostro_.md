---
title: "The latest ubuntu 10.04 doesn't work on my Vostro 1500"
date: 2010-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by warking on 2010-04-30
First, My laptop's specs:
CPU: T8100
RAM: 4G
HD: Toshiba 250G
Graphics: Nvidia 8600M GT 256M
Screen: 1440*900


I have been trying ubuntu 10.04 since its alpha stage. There's always a problem for me trying the live cd or even install it on my harddisk. The problem is really severe. My screen did not display anything I could recognize. it displays like this:
[http://photo.lujun.info/main.php?g2_itemId=5554&g2_imageViewsIndex=1]("http://photo.lujun.info/main.php?g2_itemId=5554&g2_imageViewsIndex=1")

purple background with two vertical lines and soon the background fades into gray.

There is a Windows 7 ultimate x64 system on this laptop and that works perfect. So I think my hardware is OK. And Ubuntu system has been working on this machine perfectly since ubuntu 7.10, I kept it updated always. 7.10, 8.04, 8.10, 9.04 and 9.10, everyone of these distributions is OK. why does it go wrong on 10.04?

If anyone with this dell series having the same problem and got it solved, please gimme some clue on the solution. Thank you.

---

### Post by warking on 2010-05-01
Nobody knows?

---

### Post by sadaruwan12 on 2010-05-01
I think it might be due to this issue,

[Click me to read]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Incompatibility%20with%20nVidia%20upstream%20driver%20installer")

I think you might have to wait a little while till this problem get sorted out.

---

### Post by warking on 2010-05-01
Incompatibility with nVidia upstream driver installer

Ubuntu 10.04 LTS includes improved integration for nVidia binary driver packages. Unfortunately, this comes at the expense of compatibility with the installer provided upstream on the nVidia website. Users who wish to use the nVidia binary video drivers with 10.04 LTS should install them using the Ubuntu packages, as made available under System -> Administration -> Hardware Drivers.

Is my problem this one? I didn't have a chance to install any drivers. Actually I didn't have the chance to do anything in 10.04. Boot and nonsense screen displayed. :(

---

### Post by philaurent on 2010-05-02
Same problem here!
I have a vostro 1500 too. (nvidia 8600gt)
I tried different tipps I got from the internet.. but no chance to install 10.04. (I tried a clean fresh install with the x86 Desktop Version, same disk works on other pcs)
I hope there will be a solution soon.

---

### Post by philaurent on 2010-05-02
Ok, now I'm running 10.04 from a fresh install.

I hooked up a second screen on my dell vostro and with that I had no problem(maybe you need to switch between the screens with the key FN+F8). After the ubuntu installation I installed the nvidia driver (the recommended one from system->system management-> hardware-drivers). Reboot.. voila

I know, it's not the best way.. but it's easy and without "tweeking things".

---

### Post by calandryll on 2010-05-02
Interesting.  My 1500 is working perfectly fine, I can't remember what my graphics card is, I know it is a nVidia M but not sure.  Only I would like to get working is fan control.  Dellfand is working but I keep getting random spikes of high temp.  I would also like to have it just run at low speed the entire time.

---

### Post by CK0y0TE on 2010-05-05
My vostro 1500 is working fine too after release upgarde from 9.04.
-CPU on demand works,no loud fans, so it is fine without "dellfand"
- nvidia chip 8600GT Mobile is at lowest performance level "0" and I havent figured out to force it to "1" or "2". Powermizer seems locked in driver gui. (Eye candy is performing like syrup blown uphill at level 0)

---

### Post by blakaxe on 2010-05-28
I have the exact same issue.

Dell Vostro : 1500
NVIDIA graphics

---

### Post by blakaxe on 2010-05-28
Did you figure out a solution? I have the same issue.

---

### Post by theduke88 on 2010-07-02
I was able to get this working in a two pronged approach:

On the initial install, you need to hit F6 and select nomodeset as the extra option (on the boot-up menu where you first select your language and then select the "install ubuntu" option, you are adding this option before you hit enter, from the F6 menu).  This will allow you to boot into the GUI.  

Once the install is done, it will reboot with the same problem.  From here, what you need to do is select the recovery option inside of grub and edit the line that has all the options (ro quiet splash etc).  You need to place the nomodeset option in amongst those other options (keep seperated by a space) and boot up (once you add the nomodeset parameter, hit ctrl-x to boot that kernel with your parmaters).  Once the system gets to the recovery menu (which you can read now) tell it that you want to drop to a shell with network.

Once you are on a shell with network, it seems as though a simple "sudo apt-get update; sudo apt-get upgrade" does the trick, although to be sure I just installed the nvidia binary driver "sudo apt-get install nvidia-current".

This was the only combination of tries that was successful for me, after a bunch of attempts.  Hopefully this is a help to other Vostro 1500 or Nvidia 8600M users who were struggling to get an initial install.:P

Edit:  The technical problem is the nuveau driver that is now used.. it sets the modeline incorrectly, and by default.  There are other kernel-flag workarounds to disable this modeline setting but this is the seemingly best way to do it with only the vanilla installer disk. FWIW this was all done on an i386 copy as the Vostro is capped on RAM and 64b doesn't matter for me on the portable.

---

### Post by AsgerJorn on 2010-08-16
I'm lost at section two of your post. Perhaps you can explain it better/more noob friendly?

Same issue here, but with Kubuntu.
[http://ubuntuforums.org/showthread.php?p=9726655#post9726655](http://ubuntuforums.org/showthread.php?p=9726655#post9726655)
Tried: Live CD, Desktop CD, Netbook CD nothing worked.
Dell Vostro 1500
Nvidida Geforce 8600M GT 512mb

---

