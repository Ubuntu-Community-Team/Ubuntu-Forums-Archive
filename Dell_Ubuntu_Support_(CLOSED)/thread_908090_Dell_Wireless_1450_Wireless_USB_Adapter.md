---
title: "Dell Wireless 1450 Wireless USB Adapter"
date: 2008-09-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by C4D on 2008-09-02
Yes, I have been self reliant and already have done research upon this subject.  I have a Dell Wireless 1450 Wireless USB Adapter (Model:D1450U REV A01) that I'm trying to get working with Ubuntu 8.04 LTS Desktop Edition.

The guides I've read have already taught me some but I'm stuck on one part: It says that the driver is invalid when I try to install it.  I've extracted as desired and have gotten the correct .inf file.  I have even recalled the already extracted DELLNIC.inf file in experimentation from the other hard drive running my Windows XP Professional SP 3 (where it currently will work if booted through windows).

Does any one have any ideas on what's possibly going wrong?  Are there steps missing or is it simply not compatible?  According to threads I've read from 2006 and 2007, it did once work.  

P.S.
First time Linux User.

---

### Post by C4D on 2008-09-02
Nevermind, I figured it out!

If anyone has been having the same problem and would like a resolution, private message me.

---

### Post by C4D on 2008-09-16
Alright, a couple of you have messaged me for help and so far I've brought success.  Here's what you do for any one else who would like to know:

[INDENT][/INDENT]If you do in fact have the same adapter as I do then the driver below will work 110% guaranteed.

[http://www.sendspace.com/file/25ybis](http://www.sendspace.com/file/25ybis)

1)Download the folder with drivers in it from the above link

2)Move the folder on your Linux machine to /home/user/bin (or, wherever you'd like to store it)

If you already have ndiswrapper installed then skip the following steps (3-5):(download the following)
3)Ndiswrapper-common[http://packages.ubuntu.com/hardy/misc/ndiswrapper-common]("http://packages.ubuntu.com/feisty/misc/ndiswrapper-common")

4)Ndiswrapper-Utils-1.9[http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9]("http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9")

5)Ndisgtk[http://packages.ubuntu.com/hardy/net/ndisgtk]("http://packages.ubuntu.com/hardy/net/ndisgtk")
---

6)With those files downloaded, throw all of them into the same folder: Open Terminal and enter into the folder through terminal. Type these commands to install each:
sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils-1.9_*.deb
sudo dpkg -i --force-depends ndisgtk_*.deb

7)Since you have installed these extra applications, you have to blacklist a open source file that came included with Ubuntu. Type this:
gksudo gedit /etc/modprobe.d/blacklist

Once that opens, add this:
blacklist bcm43xx
Save and close it out.

8)Go to System >> Administration >> Windows Wireless Drivers and press the Install New Driver button. Direct it to 2K folder you downloaded and select dellnic.inf file and you're done.

The following steps are to ensure it has been installed and are in proper working order.
9)In Terminal, type ndiswrapper -l(That's a L). This command will displayed installed drivers... and it should confirm that it is.
If it has installed correctly then type:
sudo depmod -a
sudo modprobe ndiswrapper

In order to make this start every start up, you have to edit a module... type this in Terminal:
gksudo gedit /etc/modules
Add ndiswrapper to the bottom of the document, save and close it out.

You are done! It should work flawlessly now.  Let me know if you have anymore questions.  I switched from Ubuntu to OpenSuse 11 (Gnome) 1 day after using Ubuntu (and was able to figure out my driver problem).  Opensuse 11 is a better OS in my opinion and takes about 3 steps to get this driver working right... but suit yourself!

- Richard

---

### Post by daml on 2010-04-23
You Rock! :guitar:    Thanks man!\\:D/

---

### Post by CJN on 2010-04-30
I realize this is a really old post I'm resurrecting but it addresses my problem exactly....

I followed the instructions very closely with the following changes...

I switched out hardy for lucid
I used the driver cd that came with the device to get the driver (because it wasn't exactly the same one: the model and rev were both off by a couple digits at the end)

and now the computer still doesn't recognize any wireless capability... 

should the things I changed make any difference?

Edit: more info:

the Windows wireless drivers list includes a dellnic which I assume is the right one, and the output of terminal from the commands above is:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will  be ignored in a future release.
dellnic : driver installed
device (413C:8104) present (alternate driver: p54usb)
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will  be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it  will  be ignored in a future release.

---

### Post by CJN on 2010-05-01
Bump, I really would appreciate any help I can get here.

More Info:

I read elsewhere that to fix the warnings all I had to do was add .conf to the files... So I did for the ndiswrapper file, and I checked the Blacklist.conf file and it contained the content from the above instructions so I deleted the blacklist I had created... still not working though.

The output from the [COLOR=Red]ndiswrapper -l && sudo depmod -a && sudo modprobe ndiswrapper[/COLOR] command is the following:

dellnic : driver installed
device (413C:8104) present (alternate driver: p54usb)

the following command: [COLOR=Red]tail /var/log/messages[/COLOR] returns:
May 1 11:42:01 camden-desktop kernel: [ 12.464320] [drm] noveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 2)
May 1 11:42:01 camden-desktop kernel: [ 12.464326] [drm] noveau  0000:01:00.0: Output DVI-I-2 is running on CRTC 0 using output c
May 1 11:42:01 camden-desktop kernel: [ 12.470563] Console: switching to color frame buffer device 160x64
May 1 11:42:01 camden-desktop kernel: [ 12.489276] ppdev: user-space parallel port driver
May 1 11:42:01 camden-desktop kernel: [ 12.590026] usb 1-7: reset high speed USB device using ehci_hcd and address 4
May 1 11:42:02 camden-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver dellnic
May 1 11:42:02 camden-desktop kernel: [ 12.801583] usbcore: registered new interface driver ndiswrapper
May 1 11:42:02 camden-desktop kernel: [ 13.452579] [drm] noveau  0000:01:00.0: Allocating FIFO number 1
May 1 11:42:02 camden-desktop kernel: [ 13.455782] [drm] noveau  0000:01:00.0: noveau_channel_alloc: initialised FIFO 1
May 1 11:42:11 camden-desktop pulseaudio[1205]: ratelimit.c: 37 events suppressed

I added the following command to the list of things I've tried:

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf

Nothing changed.

---

### Post by CJN on 2010-05-02
Bump, still not working.

---

### Post by CJN on 2010-05-05
Bump.

---

### Post by CJN on 2010-05-06
Bump.

---

### Post by lleachii on 2010-05-18
This was my instalation procedure for a [COLOR="Red"]Dell Computer Corp. Wireless 1450 Dual-band (802.11a/b/g) USB2.0 Adapter:
[/COLOR] on Lucid (please note, a different file must be downloaded depending on kernel version, this accurate for for 2.6.29 kernels and above).

Note, I'm an old Windows kid...so hopefully the CLI commands are accurate (I actually used an GUI web browser to downloaded from the web and used ```
kdesudo dolphin
``` to copy, rename and paste the file). Since this is an extra step for the GUI-prefered, I will note kdesudo [gksudo in gnome] to open a GUI program with root access. I hope this makes this easy for the CLI and GUI crowds.

After visiting the list at [http://wireless.kernel.org/en/users/Drivers/p54/devices]("http://wireless.kernel.org/en/users/Drivers/p54/devices"), I downloaded the USB 2nd generation (ISL3887) isl3887usb firmware  noted at [http://wireless.kernel.org/en/users/Drivers/p54]("http://wireless.kernel.org/en/users/Drivers/p54") (**verify your kernel version and ckeck this site for correct file and file name to use**) and installed the file:

```
wget http://daemonizer.de/prism54/prism54-fw/fw-usb/2.13.24.0.lm87.arm
```

```
sudo cp 2.13.24.0.lm87.arm /lib/firmware/isl3887usb
```

I then installed the Ubuntu package that carries compat-wireless, it is called linux-backport-modules and it has more backported modules than just your wireless subsystem. It's updated whenever major updates are pushed out into the wireless-testing git tree.

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

My Dell TrueMobile 1400 USB worked upon rebooting, given that Linux RARELY needs to be rebooted (I was raised on Windows, so I knew rebooting worked also), I understand these commands also give the same effect:

```
modprobe -r p54usb | modprobe -r p54common
```

then

```
modprobe p54usb | modprobe p54common
```


```
iwconfig 
```

It should list your adapter.

Some people experience slow browsing, it is probably the result of the Wireless Card operating at 1Mbps connection, to fix see:

[http://ubuntuforums.org/showthread.php?t=816541]("http://ubuntuforums.org/showthread.php?t=816541")
[http://ubuntuforums.org/showthread.php?t=1416505]("http://ubuntuforums.org/showthread.php?t=1416505")

---

### Post by CJN on 2010-05-30
I got my setup working by using an airport express and Ethernet cable. Seems to be the only solution that works.

---

### Post by Marc van der Wijst on 2010-11-07
> **C4D said:**
> Alright, a couple of you have messaged me for help and so far I've brought success.  Here's what you do for any one else who would like to know:
If you do in fact have the same adapter as I do then the driver below will work 110% guaranteed.

[http://www.sendspace.com/file/25ybis](http://www.sendspace.com/file/25ybis)

1)Download the folder with drivers in it from the above link

2)Move the folder on your Linux machine to /home/user/bin (or, wherever you'd like to store it)

(...)

You are done! It should work flawlessly now.  Let me know if you have anymore questions.  I switched from Ubuntu to OpenSuse 11 (Gnome) 1 day after using Ubuntu (and was able to figure out my driver problem).  Opensuse 11 is a better OS in my opinion and takes about 3 steps to get this driver working right... but suit yourself!

- Richard

Went from Ubuntu 9.10 to Linux Mint 9 (fork of Ubuntu 10.4). In 9.10 I could install my Dell 1450 Wireless USB adapter by activating the "Broadcom STA wireless driver" in "Hardware Drivers". In 10.4 this is not possible any more.
As workaround I installed this 2K Windows driver. Goto "Control Center" and select "Windows Wireless Drivers" (under "System"). Click "Install New Driver" and locate ./2K/DELLNIC.inf.

So many thanks for the link! You rock!
:guitar:

I found on another site that you can install "Windows Wireless Drivers". It's called ndisgtk. This is a quote that I found. Have fun with it! :P
> 
This tutorial shows how to install your Windows system wireless network-card driver in Ubunu using ndisgtk.
 ***Step1:*** Install ndisgtk.
 [INDENT]Go to **System->Administration->Synaptic Package Manager**,search **ndisgtk**,then mark and install ndisgtk.(three packages *ndiswrapper-common,ndiswrapper-utils,ndisgtk* will be installed)
[/INDENT] this can be used to install Windows network card drivers in ubuntu system.
**Step2:**
 [INDENT]After installed ndisgtk,open **Windows Wireless Drivers** from **System->Administration** menu.Then just click **Install New Drivers** and select your Windows card driver file to install.
[/INDENT]  Finally,the installed network card driver will list in the left box.You can click the network manager icon at right-top of your screen and find wireless network.



---

### Post by ubto66 on 2012-11-27
to cjn

Did you get the wireless card to run?
I ask, because I ran the card on ubuntu 10.04 and now on ubuntu 12.04,
if its the same card.
Can tell you how.

---

### Post by wildmanne39 on 2012-11-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

