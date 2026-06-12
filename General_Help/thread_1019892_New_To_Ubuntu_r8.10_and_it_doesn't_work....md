---
title: "New To Ubuntu r8.10 and it doesn't work..."
date: 2008-12-23
forum: General Help
---

### Post by Braziltraveller on 2008-12-23
Hi to all,

I just installed the r8.10 Ubuntu on my laptop. The installation went alright (I think). When I boot the system it eventually comes up with the logon screen but this keeps on flickering (don't know if that is a exact english word).

The last installation it didn't ask me to give any username or password, but know it is asking for it while flickering.

I guess I'm missing something and therefore your help is very much appreciated.

Cheers,

Johan

---

### Post by XFaisalX on 2008-12-23
Okay, I may not be an expert at Linux (I'm a bit nub in it), but I know more than an average human of my age about computers and programs.
So could you give me some specs of your computer please?

---

### Post by Braziltraveller on 2008-12-23
Thanks,

Just a Laptop, an Acer1350...

[ftp://ftp.acer-euro.com/notebook/aspire_1350/manual/1350-uk.pdf](ftp://ftp.acer-euro.com/notebook/aspire_1350/manual/1350-uk.pdf)

The installation seems to go well, but the actual booting up and getting to the UI doesn't go so well.

Cheers

---

### Post by XFaisalX on 2008-12-23
Hmmm, since you have Linux, you have Grub.
Sometimes there is a bug for some odd reason. (Programs, AV's etc.)
So what I would suggest to try, is boot up with the linux disc in it, and hit Rescue, and select the Grub file to reinstall.
Just go through it all and hopefully it will work out.
If you tried this reply and I will respond as soon as possible =D

---

### Post by Braziltraveller on 2008-12-23
I have redone the whole installation procedure without any problems...

It is "stuck" @ [ubuntu@ubuntu:~$]

I was hoping it would go directly to the Gnome/KDE/graphical interface...

---

### Post by wilson47 on 2008-12-23
Does CTRL + ALT + F7 do anything? If not maybe try and run the command: ```
sudo /etc/init.d/gdm start

```. That should start X-Windows and all that jazz.

Is "ubuntu" also really your username? Did you not change that?

---

### Post by wilson47 on 2008-12-23
Sorry for asking such a stupid question, but you did install the desktop version, right?

---

### Post by Braziltraveller on 2008-12-23
Oke...I reinstalled Ubuntu from a CD, after it is finished it just gives me a prompt. I tried the previous post suggestions but without succes...

If I reboot the system it seems to have lost all information, it doesn't boot into Ubuntu.

Okay....another intallation and now I'll write done what happens:

[start pc]
-choose language, -> English
-Install Ubuntu
[it starts installing, ubuntu logo with orange time indicator]
it is promptimg....de cd stops spinning

I get a loading sign and:

{ubuntu@ubuntu:~$]

know what?

---

### Post by wilson47 on 2008-12-23
1. Does your computer have enough memory for the installation? I tried installing a newer version of Ubuntu on an older computer and ran into simmilar issues due to a lack of RAM. 
2. Have you checked the CD for errors?
3. If it could be a hardware problem, you could try installing an older version of Ubuntu. Do you get anywhere on the live trial? It sounds like you are just using the text installer.

---

### Post by Braziltraveller on 2008-12-23
Could be...just 512mb internal memory. Shouldn't be such a big deal right.

But I will try to find a older version of Ubuntu and try to install that. If that doesn't work I'll logon again.

Cheers

---

### Post by Braziltraveller on 2008-12-23
..text version??

[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&mirror=http://ftp.snt.utwente.nl/pub/linux/ubuntu-releases/&arch=i386](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&mirror=http://ftp.snt.utwente.nl/pub/linux/ubuntu-releases/&arch=i386)

It is supposed to be the desktop version...

Cheers

---

### Post by spcwingo on 2008-12-23
If the live CD worked for you try to boot the live CD back up and mount your HDD.  Open a terminal and type:

```
gksu gedit
```

That will open gedit as root.  Use gedit to open /boot/grub/menu.lst.  Put xforcevesa in the kernel line.  It should now look something like this:

```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=19a7e596-c01b-45df-960e-4ecc77ba50df ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

You won't have all the pretty compiz effects, but it should at least work.  I hope this helps...let me know how it turns out.

---

### Post by Braziltraveller on 2008-12-24
Hi,

Okay a new day so I started again from scratch. I deleted all partitions from the harddrive. So no operating system on my harddrive.

I burned a new image 8.04 on a CD and launched this one. First I tried to run Ubuntu from the CD without installing. It seems to do a lot but it doesn't result in the actual GUI.

Again, I tried to do the actuall installation but in the end it keeps prompting like I posted it in previous post. When I switch off the Laptop and reboot it without CD no operating system has been installed.

What am I doing wrong here...this should be easy right?

Cheers

---

### Post by imtheguido on 2008-12-24
I am unsure of 8.04 as I never used it and just started with 8.10 when it came out, but it gave me the option of running a check on my Memory to make sure it all worked alright? Does it give you this option before installing? If it does I would recommend it. You may have some bad memory in the laptop.

---

### Post by Braziltraveller on 2008-12-24
Yup, I'm running the memory test right now, man that's some big memory test. So far so good, no errors...

---

### Post by Braziltraveller on 2008-12-24
PC is still buisy with the MemoryTest. The fact that the installations hasn't succeeded so far can there be a relation with the integrated VIA KM400 videocard? I've been browsing some sites and see that this card has given a lot of issues for Linux users...

It does however support OpenGL.

Cheers

---

### Post by Petecoi on 2008-12-24
My father has the same laptop and the same problem.

I'm new to Linux but have instlled itsuccessfully on a pc. The differences in the install process for the aspire 1350 laptop are that after setting a language no option for partitioning the drive appears. Instead the Ubunt bar comes on showing progress but drops into a code page after about 5 minutes. Installing on the aptop takes much much longer.

Using a different CD makes no difference and repairing the install creates chaos. The screen flashes, distorts and has two green bars at the top and bottom.

However, the laptop seems to start with a windows like boot page. Does this laptop have a windows pre-boot type programme that prevents anything else loading?

Pete

---

### Post by russo.mic on 2008-12-24
Assuming that you've installed the proper version of the OS, i.e. not the server version or something, This sounds like a problem with your video card.  What graphics card do you have in this thing?

---

### Post by Braziltraveller on 2008-12-25
Hi,

Well the harddrive was whiped clean before installing. The MBR was also re-newed. So it "doensn't" contain any traces of previous OS.

The Video card is a VIA KM400 64MB, it is notourious - yes I know. But I have also already found refference to driver for this card on the Ubuntu-forum/communitee.

Cheers

---

### Post by Braziltraveller on 2008-12-26
> **imtheguido said:**
> I am unsure of 8.04 as I never used it and just started with 8.10 when it came out, but it gave me the option of running a check on my Memory to make sure it all worked alright? Does it give you this option before installing? If it does I would recommend it. You may have some bad memory in the laptop.

I'm stopping the memory test, it has done already 80tests and has been running for over 54hr...

---

### Post by Braziltraveller on 2008-12-29
I fixed the installation,it is working properly now. The problem was in the end the monitor.

>  Re: Installing 8.04 onto Acer Aspire 1350 - not running desktop
Hi Gmorales!

1. Insert LiveCD and boot (as you have problem with your screen, you will get only a command line - I assume you are in the console after booting the live CD)

2. type "sudo vim /etc/X11/xorg.conf", hit enter (vim editor opens)

3. find the section "monitor" in the file using the up/down keys
4. press 'I' (this will start the editor's insertion mode)
5. add these two lines inside the section (try to type patiently, vim editor is not too user friendly for newbies):

HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0

6. press Esc (quit edit mode that you started by pressing I)
7. type ":wq!" (you will see :wq! in the bottom of the screen) and press Enter (commands Write+Quit with no prompt were executed, you are back to command line, you have edited the xorg.conf file)

8. type "startx" on the command line
-> Xserver is started

Thank you "nigelm187", this post helped me a lot (my Acer is happily running on 8.10 now)...

[http://ubuntuforums.org/showthread.php?t=852101&highlight=Acer+Aspire+1350]("http://ubuntuforums.org/showthread.php?t=852101&highlight=Acer+Aspire+1350")

Cheers

---

