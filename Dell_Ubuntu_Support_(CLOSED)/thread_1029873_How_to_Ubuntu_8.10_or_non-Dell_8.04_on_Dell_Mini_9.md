---
title: "How to: Ubuntu 8.10 or non-Dell 8.04 on Dell Mini 9"
date: 2009-01-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vegetarianshrimp on 2009-01-03
[SIZE=3]If you are tired of having a Dell version of Ubuntu on your Mini 9, or if you can't upgrade to 8.10 like I couldn't (even after changing to Normal Releases on Software Sources), then this is what you do:[/SIZE]

**PLEASE READ ALL INSTRUCTIONS CAREFULLY BEFORE DOING _ANYTHING_**
[B]
Note:[/B]  with Ubuntu 8.10 on my Mini 9, I have not been able to get the microphone to work yet.

Make sure all important files, like Openoffice.org files, are copied onto a USB drive, or emailed to yourself, or whatever way works best for you to back them up BEFORE you do this.

Insert your** [COLOR=Blue]_[USB flash drive]("http://en.wikipedia.org/wiki/USB_flash_drive")_[/COLOR]** (1GB should be enough, although less may work too, I just haven't tested it with less)

Go to [COLOR=Blue]_**[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)**_[/COLOR]

Click on **Download (for Linux)**

**Save** to **Desktop**

Applications>Accesories>[B]Terminal

[/B]Copy and paste each of these lines separately into the terminal (Edit>Copy and Edit>Paste on the menu bars) and press enter after each
```
cd Desktop
chmod u+x unetbootin-linux-304
sudo ./unetbootin-linux-304
```enter your password, press enter again

Before UNetbootin opens, there might be messages saying that you need to install certain packages (e.g. p7zip-full) Use the **Synaptic Package Manager** to install these. If you don't know how [COLOR=Blue]_[click here]("https://help.ubuntu.com/community/SynapticHowto")_[/COLOR]. Once you've installed those packages, run the last command (sudo ./unetbootin-linux-304) again in the terminal.

**Do NOT close the Terminal AT ANY TIME, for doing this will also close UNetbootin.**

In the UNetbootin window, there will be a drop-down menu "==Select Distribution=="
Select **Ubuntu**

There will also be one called "==Select Version=="
Select **8.10_Live** for 8.10 Intrepid Ibex, or **8.04_Live **for a non-Dell version of 8.04 Hardy Heron

In the bottom left corner of the window, there will be another drop down menu. It will either say "Hard Disk" or "USB Drive". You want it to say **USB Drive**

Click **OK**

Wait for everything to finish. While you are waiting, **DO NOT CLOSE THE TERMINAL. UNETBOOTIN WINDOW, OR TAKE OUT YOUR USB DRIVE**

When it's done, make sure your important files are on something else besides your computer, because afterwards they [B]WILL BE ERASED.

Reboot [/B]your Mini

When you see the **Dell Logo**, **press 0** (zero) on your keyboard

When the next screen comes up, press the **down arrow key** and then **enter**.

Wait for Ubuntu to load.

On the **Desktop**, double click **Install**

Go through the installation process. At some point, it will ask you about **Partitions**. If you have followed the instructions correctly and backed up important files, you can go ahead and select the **whole disk **option. 

You're done!
If you installed 8.10, make sure to go to [[COLOR=Blue]_this website_[/COLOR]]("https://help.ubuntu.com/community/DellMini9/Intrepid") to fix sound, etc.
[SIZE=3]
Thanks to [/SIZE][SIZE=3][COLOR=Blue]_[logos34]("http://ubuntuforums.org/member.php?u=127804") _[/COLOR][/SIZE][SIZE=3]for [/SIZE][SIZE=3][COLOR=Blue]_[helping me get started]("http://ubuntuforums.org/showthread.php?t=1027616")_. [COLOR=black]If it wasn't for him/her, I would be stuck with a horribly messed up OS, and you wouldn't be reading this How-to.[/COLOR][/COLOR][/SIZE]

---

### Post by armandh on 2009-01-04
a usb cd-dvd drive works too.
bought a case, had a drive
I much prefer 8.10

---

### Post by vegetarianshrimp on 2009-01-04
I didn't buy an external CD drive with my Mini 9, because it was an extra $80 I didn't want to spend, so I had to use UNetbootin

---

### Post by ArKay on 2009-01-04
You can also look here :
[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

It's an easy to follow guide and has more hints (installing remix, fixing other problems, etc)

Not that this forum doesn't work - but it's devoted solely to solving Ubuntu/mini 9 problems.

---

### Post by vegetarianshrimp on 2009-01-04
Actually, you need another computer for that.  This is for people who only have access to a Mini 9.

---

### Post by anjilslaire on 2009-01-05
You can also simply install usb-creator to create a bootable usb ISO to install 8.10, then refer to the guide at 
[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

for full details for sound, tweaks, etc.

---

### Post by dragonmojo on 2009-01-16
"Note: with Ubuntu 8.10 on my Mini 9, I have not been able to get the microphone to work yet. Same goes for the battery."

Hi Veg,
I can't seem to find any info on the internet that resolves the microphone issue, and am wondering if you have been successful. I went from Dell Mini OS to 8.10 and it appears so much nicer (I am a Linux/Ubuntu noob). My Mini9's mic still doesn't seem to work.

Thx,
Alan

---

### Post by vegetarianshrimp on 2009-01-16
No, I haven't figured out how to make it work.

[Edit]

Even after doing this: [https://help.ubuntu.com/community/DellMini9/Intrepid](https://help.ubuntu.com/community/DellMini9/Intrepid)

I did get the battery working though. It was the battery's problem not Ubuntu's

---

