---
title: "Webcam worries !"
date: 2009-03-05
forum: General Help
---

### Post by steelbloo on 2009-03-05
Hi Everybody !

How difficult can it be to install a webcam ?? If anyone can help me that would be great, but please be gentle, as the new LINUX lingo is very new to me!!
So much so, I realise I have been posting in the wrong part of the forum for help previously!  :(

Ok, here goes:
Running a old PC with ubuntu 8.10 via ethernet.(now wireless! mastered that one!!)

Skype2 is running fine.
When I click to test webcam the screen is just a load of fuzz.
Does this mean ubuntu knows the webcam is there, but not installed correctly? or have I just got it all wrong?

The webcam is a Phillips SPC 300NC

Thanking you in advance for any help
Vicky

---

### Post by mb_webguy on 2009-03-05
That webcam is [supported by the gspca module]("http://ftp.gnu.org/tmp/linux-libre-fsf2_2.6.28/linux-2.6.28/Documentation/video4linux/gspca.txt"), which should be included in Ubuntu.  It could be, however, that this module isn't being loaded.

Open the terminal and type the following:```
lsmod | grep gspca
```If that doesn't produce any output, the module isn't being loaded.  If this is the case, type the following command to load the module.```
sudo modprobe gspca
```

---

### Post by RichardCain on 2009-03-10
I've recently loaded Ubuntu Hardy onto my Compaq Presario V3700 laptop.  Due to Windows folding up completely, I had to format my hard disc in the process.  The in-built webcam does not show up at all.  I've installed Camorama Webcam Viewer from the Synaptic, but it comes up with the error:

"Could not connect to video device (/dev/video0)
Please check connection.

Any ideas?

---

### Post by lolwhites on 2009-03-13
I'm having the same problem with my 150 Spacecam, even though it's worked before in Ubuntu. It doesn't work at all with Camorama, and while Cheese sees it, the image is very dark.

I tried mb_webguy's solution but I just got the message *FATAL: Module gspca not found.* Installing gspca-source from Synaptic doesn't seem to help either.

---

### Post by steelbloo on 2009-03-14
> **mb_webguy said:**
> That webcam is [supported by the gspca module]("http://ftp.gnu.org/tmp/linux-libre-fsf2_2.6.28/linux-2.6.28/Documentation/video4linux/gspca.txt"), which should be included in Ubuntu.  It could be, however, that this module isn't being loaded.

Open the terminal and type the following:```
lsmod | grep gspca
```If that doesn't produce any output, the module isn't being loaded.  If this is the case, type the following command to load the module.```
sudo modprobe gspca
```

Hi WebGuy !
Many thanks for your help with this one.
I really need some hand holding, I have looked through 'system' and can't find 'terminal' to type in your suggested codes.
Sorry...  you must think I'm really dum!!  (ok don't answer that one!!  LOL)

Would you mind (if you have the time) listing where I need to find the page, in order to type in the codes?

Many thanks
Vicky

---

### Post by |{urse on 2009-03-14
have you tried amsn (another msn chat clone)? It autodetects most webcams.

---

### Post by lolwhites on 2009-03-14
AMSN detects my cam but it's still really dark and the brightness/colour/contrast controls don't work. Same with Skype. Empathy and Ekiga can't see it at all.

Funny thing is it worked fine until the last kernel upgrade.

---

### Post by ProNux on 2009-03-14
> **steelbloo said:**
> Hi WebGuy !
Many thanks for your help with this one.
I really need some hand holding, I have looked through 'system' and can't find 'terminal' to type in your suggested codes.
Sorry...  you must think I'm really dum!!  (ok don't answer that one!!  LOL)

Would you mind (if you have the time) listing where I need to find the page, in order to type in the codes?

Many thanks
Vicky

Terminal can be found on "Applications-Accessories-Terminal"
It will open up like a dos-prompt.  Just type the codes suggested by WebGuy and post the result here...

---

### Post by sigurnjak on 2009-03-15
Being a noob here myself  ,just copy and paste commands so you do not type them wrong . It works better for me .

---

### Post by lolwhites on 2009-03-15
By running gstreamer-properties, I find that my webcam is visible when Video for Linux 2 (v4l2) is set as the plugin, but not when it's v4l.

I've also discovered that Ekiga allows me to set v4l2 as the input, which solves the webcam issue there. I can get Skype to see it by typing *LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype* into a terminal, but Camorama doesn't give me the option as it simply won't open unless it can see the cam.

---

### Post by rmartinus on 2009-05-05
I had problems with my /dev/video0 as well.
When I had my logitech webcam plugged in to my laptop's USB, I did "dmesg | tail -15" and this is what I've got:
> 
[ 6860.838423]  CIFS VFS: ignoring corrupt resume name
[ 7161.409656] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 7161.865052] usb 7-2: new full speed USB device using uhci_hcd and address 2
[ 7162.156726] usb 7-2: configuration #1 chosen from 1 choice
[ 7162.245665] Linux video capture interface: v2.00
[ 7162.272942] pwc: Philips webcam module version 10.0.13 loaded.
[ 7162.272950] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[ 7162.272955] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[ 7162.272960] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[ 7162.273022] pwc: Logitech QuickCam Orbit/Sphere USB webcam detected.
[ 7162.273129] pwc: Registered as /dev/video0.
[ 7163.542816] pwc: Failed to set video mode QSIF@10 fps; return code = -110
[ 7164.543104] pwc: Failed to set video mode QSIF@10 fps; return code = -110
[ 7164.705363] usbcore: registered new interface driver snd-usb-audio
[ 7164.705356] usbcore: registered new interface driver Philips webcam
.... so I thought, great! All I needed to do was install "camorama" from Synaptic.
I had problem accessing /dev/video0, but if I run it as root ("sudo camorama"), it worked!
The problem was because /dev/video0 does not allow any read/write access to the world, 
so I ran these commands to fix the problem:
> 
rm@rm-laptop:~/Pictures$ ls -ltra /dev/vid*
crw-rw---- 1 root video 81, 0 2009-05-05 21:27 /dev/video0
rm@rm-laptop:~/Pictures$ sudo chmod o+rw /dev/video
chmod: cannot access `/dev/video': No such file or directory
rm@rm-laptop:~/Pictures$ sudo chmod o+rw /dev/video0
rm@rm-laptop:~/Pictures$ ls -ltra /dev/vid*
crw-rw-rw- 1 root video 81, 0 2009-05-05 21:27 /dev/video0


---

