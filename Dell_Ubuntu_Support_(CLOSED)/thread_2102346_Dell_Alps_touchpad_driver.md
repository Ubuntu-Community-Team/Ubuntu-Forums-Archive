---
title: "Dell Alps touchpad driver"
date: 2013-01-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aboud on 2013-01-07
I have struggled a lot before  I found a solution for my Dell inpiron touchpad driver. 

I have downloaded pieces of the driver from different sources and compiled them before I had work driver.

In the attached tar file I have included a simple install script that will compile and backup and install new touchpad driver (psmouse.ko).

---

### Post by anohigisavay on 2013-02-14
Woa this really helped a lot! Thank you!

---

### Post by kalyanvarma on 2013-02-17
This has been very helpful thanks a lot!

---

### Post by Jayjewels93 on 2013-02-18
Sorry, I'm still somewhat new to Ubuntu. How do I install this touchpad driver on my system? step-by-step would be great, as I said, I'm still getting the hang of this. Thanks in advance!

---

### Post by sixel on 2013-02-19
I'm with Jayjewels93 don't know how to run the install script

---

### Post by zAo on 2013-02-26
Can someone give me a hint?
```
/usr/src/psmouse-alps-dst-0.4/dkms.conf must have PACKAGE_VERSION set to alps-dst-0.4

------------------------------
Deleting module version: alps-dst-0.4
completely from the DKMS tree.
------------------------------
Done.
/usr/src/psmouse-alps-dst-0.4/dkms.conf must have PACKAGE_VERSION set to alps-dst-0.4
This places the psmouse.ko dlkm in /lib/modules/3.8.0-7-generic/updates/dkms

Creating symlink /var/lib/dkms/psmouse/alps-dst-0.4/source ->
                 /usr/src/psmouse-alps-dst-0.4

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.8.0-7-generic -C /lib/modules/3.8.0-7-generic/build M=/var/lib/dkms/psmouse/alps-dst-0.4/build/src psmouse.ko....(bad exit status: 2)
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.8.0-7-generic (i686)
Consult /var/lib/dkms/psmouse/alps-dst-0.4/build/make.log for more information.
Build failed
DKMS make.log for psmouse-alps-dst-0.4 for kernel 3.8.0-7-generic (i686)
Tue Feb 26 21:17:10 CET 2013
make: Entering directory `/usr/src/linux-headers-3.8.0-7-generic'
  CC [M]  /var/lib/dkms/psmouse/alps-dst-0.4/build/src/psmouse-base.o
/var/lib/dkms/psmouse/alps-dst-0.4/build/src/psmouse-base.c: In function ‘__check_smartscroll’:
/var/lib/dkms/psmouse/alps-dst-0.4/build/src/psmouse-base.c:64:1: warning: return from incompatible pointer type [enabled by default]
  CC [M]  /var/lib/dkms/psmouse/alps-dst-0.4/build/src/synaptics.o
/var/lib/dkms/psmouse/alps-dst-0.4/build/src/synaptics.c: In function ‘set_input_params’:
/var/lib/dkms/psmouse/alps-dst-0.4/build/src/synaptics.c:1153:3: error: too few arguments to function ‘input_mt_init_slots’
In file included from /var/lib/dkms/psmouse/alps-dst-0.4/build/src/synaptics.c:29:0:
include/linux/input/mt.h:78:5: note: declared here
/var/lib/dkms/psmouse/alps-dst-0.4/build/src/synaptics.c:1165:3: error: too few arguments to function ‘input_mt_init_slots’
In file included from /var/lib/dkms/psmouse/alps-dst-0.4/build/src/synaptics.c:29:0:
include/linux/input/mt.h:78:5: note: declared here
make[1]: *** [/var/lib/dkms/psmouse/alps-dst-0.4/build/src/synaptics.o] Error 1
make: *** [psmouse.ko] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-7-generic'

```

---

### Post by macsym on 2013-02-26
Hello Aboud,

I have a Dell Vostro 3360 running Ubuntu 64 bits. I could use my touchpad to move the mouse but the multitouch (especially for 2-finger scrolling) wasn't working so I installed *dkms add psmouse/alps-dst-0.4* with a custom *alps.c* I found on a forum (can't remember where). Everything was fine until this morning (I guess the computer autoupdated itself and this driver doesn't work anymore) . My mouse was completely blocked so I used an external USB mouse to purge dkms psmouse/alps-dst-0.4. I was able to move the mouse via the touchpad again but 2-finger scrolling wasn't working so I decided to download and run your script.

My problem is my mouse is now completely blocked again and I don't know how to remove your files (I didn't find any uninstallation script).

Could you please explain me how I can completely remove your solution? At least I'll be able to move my mouse again.

Thank you for any help.

PS: look what *xinput* and *dkms remove* returns:

max@max-Vostro-3360:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_E4HD               id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]
max@max-Vostro-3360:~$ sudo dkms remove psmouse/alps-dst-0.4 --all
[sudo] password for max: 
Error! There are no instances of module: psmouse
alps-dst-0.4 located in the DKMS tree.
max@max-Vostro-3360:~$

---

### Post by rodrigob on 2013-03-12
Thanks a lot, just saved my day !

rodrigob.

---

### Post by thomaspot on 2013-03-28
Aboud.. You made my day. ThanX :D

---

### Post by stash1071 on 2013-04-12
I ran into a problem trying to install the driver as well, and then my touchpad was completely disabled.  Unfortunately, I didn't save the error, but if you look at the install script it thankfully makes a copy of psmouse.ko before trying to install the new one.  The copy should be in the directory from where you ran the install script as psmouse.ko.org.  I copied it back to /lib/modules/`uname -r`/kernel/drivers/input/mouse/psmouse.ko and restarted and touchpad and mouse work again.

---

### Post by Nathanericscott on 2013-04-19
Been Struggling for the past 2-3 hours trying to fix on dell E6400 with Ubuntu 10.04Lts,, Finally got it working 100%.  Needs to be a better way though

---

### Post by batmanone on 2013-04-29
Thanks a lot! Seems to work on my Dell Inspiron 17R special edition running Ubuntu 12.04 64bit.  It at least can now detect my touchpad as a touchpad instead of a generic mouse.
For people asking for directions on installing the script, here's what I did.
1.  Download the gz file to a convenient directory.
2.  Open a Terminal.
3.  cd into the directory where you downloaded the file.
4.  Run "tar -xvf DellAplsDriver.tar.gz" (with no quotes) to extract the contents of the file.
5.  cd into the new DellAplsDriver/ directory.
6.  Run "sudo ./install" (no quotes) to run the install script.
After doing these steps, running "xinput list" for me shows a new "AlpsPS/2 ALPS GlidePoint" entry.

---

### Post by axept on 2013-05-02
Just wondering, I have a Fujitsu laptop with (I think) Alps touchpad. This is listed as "PS/2 Generic Mouse". I want it to work as it should or at least with 2-finger scroll. I run Ubuntu 12.10 64Bit. Will this work on my laptop?

---

### Post by axept on 2013-05-09
No one?? :P

---

### Post by skilia on 2013-05-15
> **batmanone said:**
> Thanks a lot! Seems to work on my Dell Inspiron 17R special edition running Ubuntu 12.04 64bit. It at least can now detect my touchpad as a touchpad instead of a generic mouse.
For people asking for directions on installing the script, here's what I did.
1. Download the gz file to a convenient directory.
2. Open a Terminal.
3. cd into the directory where you downloaded the file.
4. Run "tar -xvf DellAplsDriver.tar.gz" (with no quotes) to extract the contents of the file.
5. cd into the new DellAplsDriver/ directory.
6. Run "sudo ./install" (no quotes) to run the install script.
After doing these steps, running "xinput list" for me shows a new "AlpsPS/2 ALPS GlidePoint" entry.


I have the same issue with touchpad driver on Dell Vostro 3360. I have downloaded gz archive and have done all these steps, but I get an errors:
```
make: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/ilia/Downloads/DellAplsDriver/synaptics.o
/home/ilia/Downloads/DellAplsDriver/synaptics.c: In function «set_input_params»:
/home/ilia/Downloads/DellAplsDriver/synaptics.c:1153:3: error: too few arguments to function «input_mt_init_slots»
In file included from /home/ilia/Downloads/DellAplsDriver/synaptics.c:29:0:
include/linux/input/mt.h:78:5: note: declared here
/home/ilia/Downloads/DellAplsDriver/synaptics.c:1165:3: error: too few arguments to function«input_mt_init_slots»
In file included from /home/ilia/Downloads/DellAplsDriver/synaptics.c:29:0:
include/linux/input/mt.h:78:5: note: declared here
make[1]: *** [/home/ilia/Downloads/DellAplsDriver/synaptics.o] Error 1
make: *** [psmouse.ko] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
ERROR: could not insert 'psmouse': Exec format error
```
and after that touchpad is not working at all, here my xinput list:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_E4HD               id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]



```

---

### Post by Sanket Kumar Singh on 2013-05-16
Well anyone who is struggling with touchpad, not working after applying the patch try following:
First try to follow what @stash1071 has suggested in previous page.
If that not works than simply live boot via same distribution and copy the directory /lib/modules/`uname -r`/kernel/drivers/input/mouse and replace the very same directory in your installed OS with this one. Things will start working fine again...... :)

---

### Post by parthsane on 2013-05-18
> **batmanone said:**
> Thanks a lot! Seems to work on my Dell Inspiron 17R special edition running Ubuntu 12.04 64bit.  It at least can now detect my touchpad as a touchpad instead of a generic mouse.
For people asking for directions on installing the script, here's what I did.
1.  Download the gz file to a convenient directory.
2.  Open a Terminal.
3.  cd into the directory where you downloaded the file.
4.  Run "tar -xvf DellAplsDriver.tar.gz" (with no quotes) to extract the contents of the file.
5.  cd into the new DellAplsDriver/ directory.
6.  Run "sudo ./install" (no quotes) to run the install script.
After doing these steps, running "xinput list" for me shows a new "AlpsPS/2 ALPS GlidePoint" entry.

Hi, I have a Dell Inspiron 14R Special Edition and running Ubuntu 13.04 64 bit, I tried running the the install script, but I get an error. Could you help me with it? After running the script, the touchpad stops working

Here's the log

parth@parth-Inspiron-7420:~/Downloads/DellAplsDriver$ sudo ./install
[sudo] password for parth: 
make: Entering directory `/usr/src/linux-headers-3.8.0-21-generic'
  CC [M]  /home/parth/Downloads/DellAplsDriver/synaptics.o
/home/parth/Downloads/DellAplsDriver/synaptics.c: In function &#8216;set_input_params&#8217;:
/home/parth/Downloads/DellAplsDriver/synaptics.c:1153:3: error: too few arguments to function &#8216;input_mt_init_slots&#8217;
In file included from /home/parth/Downloads/DellAplsDriver/synaptics.c:29:0:
include/linux/input/mt.h:78:5: note: declared here
/home/parth/Downloads/DellAplsDriver/synaptics.c:1165:3: error: too few arguments to function &#8216;input_mt_init_slots&#8217;
In file included from /home/parth/Downloads/DellAplsDriver/synaptics.c:29:0:
include/linux/input/mt.h:78:5: note: declared here
make[1]: *** [/home/parth/Downloads/DellAplsDriver/synaptics.o] Error 1
make: *** [psmouse.ko] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-21-generic'
ERROR: could not insert 'psmouse': Exec format error

parth@parth-Inspiron-7420:~/Downloads/DellAplsDriver$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wireless Optical Mouse                      id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Integrated Webcam                           id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]

---

### Post by Sanket Kumar Singh on 2013-05-18
> **parthsane said:**
> Hi, I have a Dell Inspiron 14R Special Edition and running Ubuntu 13.04 64 bit, I tried running the the install script, but I get an error. Could you help me with it? After running the script, the touchpad stops working


Well even I ran into the very same problem few days before. Even though the script makes a backup copy of file psmouse.ko as psmouse.ko.org, but replacing that does not worked for me. So I simply burned the very same distro in pd and booted through it.

1. All you need to do is to first make a live boot.
2. Get inside **/lib/modules/`uname -r`/kernel/drivers/input** and copy directory **mouse** and save it somewhere safe.
3. Now reboot and get back inside you orginal installed distro and replace the **mouse** directory inside **/lib/modules/`uname -r`/kernel/drivers/input** with the copied one.
4. Reboot your system again and things will start working well.
5. Remember one need root priveleges to perform above actions.

That's all....

---

### Post by hencoappel on 2013-05-23
For those still struggling, this [link]("https://www.linuxwind.org/html/dell-touchpad-driver-for-ubuntu-13-04.html") helped me on Debian, using the 3.8-2-amd64 kernel. I was getting a similar error to parthsane and skilia.

---

### Post by kaustuv1993 on 2013-06-23
Hey, I also have a Dell Inspiron 14R Special Edition... And I downloaded the DellAplsDriver.tar.gz folder.... I've extracted it, but running install in terminal doesn't work... and the step by step instructions provided by batmanone and Sanket K. Singh don't seem the be working for me.

---

### Post by BillaSong on 2013-07-12
> **hencoappel said:**
> For those still struggling, this [link]("https://www.linuxwind.org/html/dell-touchpad-driver-for-ubuntu-13-04.html") helped me on Debian, using the 3.8-2-amd64 kernel. I was getting a similar error to parthsane and skilia.

I have Dell inspiron 7720 SE R17 and i had same problems as parthsane and skilia. But the [link]("https://www.linuxwind.org/html/dell-touchpad-driver-for-ubuntu-13-04.html") hencoappel posted is great. Now my touchpad works as touchpad =) Ty hencoappel \\:D/
Oh yes and i have Ubuntu 13.04 64-bit =)

---

### Post by Tim_Hellner on 2013-09-03
Hi Aboud,

I have been stuggling for months to find a solution to my own problem with running Mint 14 (which is Ubuntu-based) on a newly-acquired Sony Vaio laptop.  I deliberately purchased a powerful, fully-loaded laptop which came with Windows 7--intending to set up a multiboot environment.  The touchpad was detected, yet I was baffled when I found that my cursor would behave wildly whenever I attempted to type.  "System Settings" in Mint 14 was no help at all.  It turns out that the ALPS touchpad was being interpreted as a PS2 mouse, just as you describe.

I downloaded your file, and I took a chance and ran your script.  Now, the touchpad is listed among my devices, and it works flawlessly!

My hat is off to you, Sir.  I went down several blind alleys before finding your elegant approach.

Many thanks,

Tim Hellner

---

### Post by Neo_Mofoka on 2013-09-30
That little tarball worked like a charm. Thank you Aboud =D

---

### Post by Syamantak_Naskar on 2013-10-02
I tried this on my Dell Inspiron 7720 and it is working perfectly. The Arch Linux forum has a solution.

The procedure:

 
[LIST]
[*]download latest alps source code from [here]("http://www.dahetral.com/public-download") (in case the page goes in 404 i have a stashed copy [here]("http://dl.dropbox.com/u/19100957/linuxStuff/alpsTouchpad/psmouse-alps-dst-0.4.tbz"))
[*]unpack it and substitute the “alps.c” with [this one]("http://pastebin.com/raw.php?i=m404GW1G") ([stashed version here]("http://dl.dropbox.com/u/19100957/linuxStuff/alpsTouchpad/alps.c"))
[*]copy the psmouse-alps-dst-0.x folder to your /usr/src directory
[*](as root) dkms add psmouse/alps-dst-0.x
[*](as root) dkms autoinstall
[*](as root) rmmod psmouse && modprobe psmouse
[/LIST]
 

 (Thanks to user “post-factum” for the solution and [nwoki]("http://nwoki.wordpress.com/2012/10/02/multitouch-fix-for-alps-touchpad/"))

---

### Post by mikesmithv on 2013-10-06
Here are the simplified instructions for the most recent Ubuntu versions.  This has been tested on 13.04 and 13.10 and it works great.

Download the driver (to the Downloads folder presumabley):
[https://www.linuxwind.org/download/psmouse-alps-1.3-alt.tbz](https://www.linuxwind.org/download/psmouse-alps-1.3-alt.tbz)

```
cd Downloads
tar xvf psmouse-alps-1.3-alt.tbz
sudo cp -afr usr/src/psmouse-alps-1.3/ /usr/src/
sudo dkms add psmouse/alps-1.3

cd /var/lib/dkms/psmouse
sudo dkms autoinstall
```

Restart Ubuntu (not just log out and back in)

After restarting you will now see the touchpad settings in "Mouse & Touchpad" under System Settings.  I have a Dell 17R but I assume this works for the 14R and most of the other Dells in this thread.

---

### Post by ppls12 on 2013-10-11
@mikesmithv, I followed your instructions on a Dell 17R SE with Ubuntu 13.04 and got this result:

```
admin@PC:/var/lib/dkms/psmouse$ sudo dkms autoinstall

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.8.0-31-generic -C /lib/modules/3.8.0-31-generic/build M=/var/lib/dkms/psmouse/alps-dst-0.4/build/src psmouse.ko.....(bad exit status: 2)
ERROR (dkms apport): binary package for psmouse: alps-dst-0.4 not found
Error! Bad return status for module build on kernel: 3.8.0-31-generic (x86_64)
Consult /var/lib/dkms/psmouse/alps-dst-0.4/build/make.log for more information.
```

Do you know any help?

---

### Post by mikesmithv on 2013-10-15
Maybe you need to remove your old dkms module first:

```
cd /var/lib/dkms/psmouse/
rm -rf alps-dst-0.4
```

This was the first step in [these instructions]("https://www.linuxwind.org/html/dell-touchpad-driver-for-ubuntu-13-04.html") which was the basis of mine.  If that works for you let me know and I'll add that.

---

### Post by ahotik on 2014-02-18
wow! That helped a lot and was so easy to install! Thanks a lot!
I can then confirm it worked on my Dell Latitude e6530 with Ubuntu 12.04, Kernel Linux 3.4.0-030400-generic.

---

### Post by kevin-hanning on 2014-03-04
worked on Inspiron 5323 like a champ. Now if we could get something for the bloody hotkeys/function keys!

---

### Post by mfletcher on 2014-03-09
Hi,

Do these instructions apply to the Dell XPS 13 9333 also? I tried running the instructions and while I did not see any errors, I still dont have multitouch enabled.

Mark

---

### Post by Vernica_RD on 2014-05-02
This also worked on my Dell Inspiron 17R SE, with Ubuntu 12.04 LTS. Thank you so much!!

---

