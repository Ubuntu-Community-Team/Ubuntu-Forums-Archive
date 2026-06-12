---
title: "Nvidia driver problems"
date: 2009-05-16
forum: General Help
---

### Post by zeldarocks on 2009-05-16
I recently dual booted XP with Ubuntu, to get to the chase, I tried to install the nvidia drivers, I reboot and I get a black screen, this same thing happened when trying to update the drivers on XP.

Here's my graphics card: nVIDIA GeForce 6100 GPU

I really hope I can get this resolved ASAP, I don't want to have to resort to a low resolution when I have the potential to use 1280*1024.

---

### Post by zeex on 2009-05-16
> **zeldarocks said:**
> I recently dual booted XP with Ubuntu, to get to the chase, I tried to install the nvidia drivers, I reboot and I get a black screen, this same thing happened when trying to update the drivers on XP.

Here's my graphics card: nVIDIA GeForce 6100 GPU

I really hope I can get this resolved ASAP, I don't want to have to resort to a low resolution when I have the potential to use 1280*1024.

hi, 

[Take a look]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/") this might help. worked for me.

Good luck :)

---

### Post by zeldarocks on 2009-05-16
I got as far as the 5th step, but when I killed the GDM and attempted to run NVIDIA-Linux-x86-180.44.pkg1.run it said that it couldn't open the file, when the file was clearly in my desktop...

 EDIT: 

Also something weird happened, the guide said that after initially killing the Xserver, that I would get a very low resolution (800 x 600) but I got a fairly higher resolution than before ( 1024 x 768 )

---

### Post by fillintheblanks on 2009-05-16
after you stop the GDM make sure you type **cd /home/your username/Desktop**

thats Desktop with a capital D. assuming the installer is on your desktop

then type **sudo sh NV** and press tab button on your keyboard it should automatically fill out

---

### Post by zeldarocks on 2009-05-16
apparently I installed the wrong driver or something, it went black again on startup.

---

### Post by zeldarocks on 2009-05-16
can saomebody help me get the correct drivers? asnd guide me through uninstalling the wrong ones?

---

### Post by Crafty Kisses on 2009-05-17
Hey there! This appears to be the right driver for your card: [http://www.nvidia.com/object/linux_display_ia32_180.51.html](http://www.nvidia.com/object/linux_display_ia32_180.51.html). You can remove the current drivers you have installed by running:
```
sudo sh NVIDIA* --uninstall
```
Once you have the proper driver downloaded don't forget to run:
```
chmod +x NVIDIA-Linux.run
sudo ./NVIDIA-Linux.run
```
Try that and you should be on your way.

---

### Post by zeldarocks on 2009-05-17
the only thing is that I don't know whether these will work, the ones I tried seemed to be the right ones, but an older version...

Also, if the display remains black, how will I do anything at all? can I still get to command prompt by going ctrl-alt-F1?

---

### Post by zeldarocks on 2009-05-17
I just tried the uninstal command at prompt, and it said something along the lines of: "can't open Nvidia"

---

### Post by zeldarocks on 2009-05-17
Please, i really want to resolve all this, i've been more or less non stop since 7:00, it's now 12:00

---

### Post by zeldarocks on 2009-05-17
bump

---

### Post by zeldarocks on 2009-05-17
Bump!!!! Help me!!!

---

### Post by zeex on 2009-05-17
> **zeldarocks said:**
> Bump!!!! Help me!!!

Hi, 

try this.

Download the driver and keep it in your home directory (/home/*<user>*/). Make sure gcc, linux-source is installed. Now Ctrl+Alt+F1 and kill GDM

Uninstalling installed driver.

```
$ sudo nvidia-uninstall
```

Installing driver (File should be in your home directory)

```
$ sudo sh NVIDIA-Linux-x86-180.44.pkg1.run
```

Follow the instructions, DO NOT download kernel from nivida site instead choose to compile. At the end of installation it asks for updating xorg.conf, make sure you say Yes *(by default NO is highlighted)*

Start GDM

```
$ sudo /etc/init.d/gdm start
```

This should work :|
[I][U]
:: you haven't mentioned your OS type. Is it 32 or 64 bit because the driver in that guide is for 32 bit OS.[/U][/I]

---

### Post by jonnygd on 2009-05-17
I had the same problem when I installed NVIDIA Drivers. For some reason when you install NVIDIA drivers it does not write anything in the xorg.conf file. To fix it first make a backup of the xorg.conf file just in case things go wrong, type

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```Then find the BusID of the graphics card by typing

```
lspci
```find the graphics card and take note of the BusID which should look something like 01:00.1
Then to edit the xorg.conf type

```
sudo nano /etc/X11/xorg.conf
```At the bottom of the file type something that looks like the following

```
Section  "Device"
            Identifier         "Device0"
            VendorName         "NVIDIA Corporation"
            BoardName          "GeForce 6100"
            BusID              "PCI:1:0:0" *or whatever the BusID was*
            Driver             "nvidia"
EndSection
```Press CTRL - X
Press Y to save
Type sudo reboot, then it should work

---

### Post by zeldarocks on 2009-05-17
I cannot uninstall the drivers, it either tells me that it can't run NVIDIA, or that the command is invalid.... I'm at wits end with all this...

---

### Post by zeldarocks on 2009-05-17
Arghhg!!!! Help

---

### Post by zeldarocks on 2009-05-17
please I'm deperate!!!!!

---

### Post by zeldarocks on 2009-05-17
I'm really reconsidering giving up on the whole ubuntu thing, windows is being stupid and now ubuntu is as well.

---

### Post by zeldarocks on 2009-05-17
unless I get a response and resolution ti my problem, I'm out of here, not kidding... I have tried since yeterday at 7:00 pm to get all this working, I'm about to just throw in the towel...

---

### Post by zeldarocks on 2009-05-17
I'm really getting ticked, there are plenty of qualified pople in the form at the moment who would be able to give a solution to my problme, but none of them are even giving my thread a galncing look.

---

### Post by fillintheblanks on 2009-05-17
you should have no problem installing the NVIDIA driver on a fresh ubuntu install. in fact, after having installed ubuntu 9.04 for the first time the very first thing I did was to install the latest NVIDIA driver. this is what I did:


step 1 goto [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and download the appropriate driver for you card. you can save it to desktop

step 2 press CTRL+ALT+F1

step 3 enter your login and password

step 4 stop the GDM by typing **sudo /etc/init.d/gdm stop**

step 5 goto where you saved the installer by typing **cd /home/your username/Desktop**

step 6 type **sudo sh NV** press TAB it will fill out the filename for you. press enter

step 7 say N to download and Y to compile. say Y to everything else. this will install the driver

step 8 you should be back at the prompt now, type **sudo /etc/init.d/gdm restart**

step 9 your done.


considering you took the wrong steps or followed the wrong guides maybe you should think about starting from square 1 again. sometimes its not your fault you want to do the right things and it doesnt work out. just think of it as a learning process thats all. if you follow these steps you will have the latest driver (in mycase 180.51) running no problem

---

### Post by zeldarocks on 2009-05-17
one thing, the driver you mentioned is for windows, can you give me the page for the Ubuntu one?
Also, I need to download the source and compiler for the kernel right?

---

### Post by zeldarocks on 2009-05-17
I just reinstalled ubuntu using wubi, I have just downloaded thw kernel source and gcc compiler, now I just need the lniux drivers for my card:

 Nvidia Geforce 6100 GPU.

---

### Post by zeldarocks on 2009-05-17
bump

---

### Post by fillintheblanks on 2009-05-17
> **zeldarocks said:**
> one thing, the driver you mentioned is for windows, can you give me the page for the Ubuntu one?
Also, I need to download the source and compiler for the kernel right?

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

you need to download the linux driver.

I installed the NVIDIA graphics driver on a fresh 9.04 ubuntu without downloading any source or compiler beforehand, just steps 1 to 9 like I wrote it works

---

### Post by zeldarocks on 2009-05-17
oh, I justa attmepted to install the drivers, after having downloaded the compiler and source, guess what?... It failed

What's up?

Also, how did you get the prompt ro compile if you didn't downlaod the source or compiler?

---

### Post by grappler on 2009-05-17
What worked for me (I have an NVIDIA card but not the same one) was to install envyng. 

```
sudo apt-get install envyng-gtk
```

It will want to install envyng-core too. 

Then run envyng and follow the prompts.

---

### Post by zeldarocks on 2009-05-17
It didn't work, the only thing I haven't tried yet is using envyNG, but that may yield the same result...

---

### Post by grappler on 2009-05-17
I am not sure what you are saying didn't work. Looking over the conversation, it seems to me that the last thing that was suggested (by me) was to install envyNG. Did you try that and if so what happened?

---

### Post by zeldarocks on 2009-05-17
I've yet to try using EnvyNG, standby

---

### Post by zeldarocks on 2009-05-17
What exactly will EnvyNG do? will it be any different than any of the previous driver installation methods outlined?

---

### Post by grappler on 2009-05-17
It automates the process. Checks your card, downloads the appropriate driver, installs it, and I think updates xorg.conf. Check out:

[HTML]http://www.albertomilone.com/envyngfaq[/HTML]

---

### Post by zeldarocks on 2009-05-17
it didn't work, black screen on startup. oh well, any more ideas?

---

### Post by zeldarocks on 2009-05-17
bump, any more ideas on what might work, all else has failed...

---

### Post by zeldarocks on 2009-05-18
bumpity bump bump...

---

### Post by gossiplady on 2009-05-18
I do not .too!

---

### Post by zeldarocks on 2009-05-18
what else can I do?

---

### Post by edwardTheGreat on 2009-05-18
Have you looked here [http://wiki.ubuntulinux.org/BinaryDriverHowto]("http://wiki.ubuntulinux.org/BinaryDriverHowto")
or
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by zeldarocks on 2009-05-18
I've already tried using the restricted driver installe, it failed as well... Am I at a complete loss?

---

### Post by edwardTheGreat on 2009-05-18
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Troubleshooting]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Troubleshooting")

Looking through here there is a section that describes:

> after enabling the nvidia drivers via the Resricted Drivers Manager, X will no longer start, a possible workaround may be to remove and reinsert the nvidia kernel module by ```
rmmod nvidia && modprobe nvidia
```. 

Have a look here and see if any of these commands help.

---

### Post by zeex on 2009-05-18
> **zeldarocks said:**
> bumpity bump bump...

Hi, 

In one of your post you mentioned you installed ubuntu using **Wubi**. I don't trust Wubi it's just for a test drive of ubuntu not for a complete system. 

Try uninstalling Ubuntu from Wubi and use a Live disk and separate partition for root and swap for installing ubuntu. Install 8.10 or 8.04 and Use the [guide]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/") i referred to you in my earlier post. 

Keep in mind people who respond usually assume that you 've a standard installation on a standard desktop/Laptop system. You 've a standard system but you missed standard installation

Don't curse ubuntu. if you'll do a proper install and configure it right, trust me you won't go back to windows. Now say good bye to Wubi and Make a real Linux installation.

---

### Post by zeldarocks on 2009-05-18
you think maybe Wubi was to blame for my constant problems all around?

 Edit: Ignore this post, my mistake... double posted by accident...

---

### Post by zeldarocks on 2009-05-18
you think maybe Wubi was to blame for my constant problems with the drivers and various installation methods?

---

### Post by Arup on 2009-05-18
Try running Live CD and see if you get the same issues, if not, then its WUBI at fault.

---

### Post by zeldarocks on 2009-05-18
how could I install drivers oof of a live CD if the OS is not installed yet?

---

### Post by zeex on 2009-05-18
> **zeldarocks said:**
> you think maybe Wubi was to blame for my constant problems with the drivers and various installation methods?

Hi, 

yes i do think that Wubi is responsible. Please do fresh ubuntu installation. You seems new to ubuntu so don't try 9.04 try 8.04 or 8.10. My suggestion is 8.04 because 8.10 have couple of bugs that you 'll encounter right after a fresh install.

Un-install ubuntu from Wubi and install from a live CD. I hope you understand the basics installation process. It's different from windows that i can tell you. Most new users don't understand swap concept. 

Here is little info. 

Installation process is very simple , just 5-7 steps. The most important step is partitioning and it's dangerous cuz you could lose data if you mess this up. 
1) Go to windows and make a empty drive say 10GB.
2) Boot from live CD
3) Make swap space out of that 10 GB
4) Mount swap to swap and rest to /
5) rest is easy :)

I know that you won't have any problem installing nvidia drivers after fresh install because we all 've been there.

::* you might find a video in youtube for step by step installation of ubuntu*

---

### Post by jbruced on 2009-05-18
I know zeex is trying to help, but I'd use the latest version(jaunty).

If you're going to do a partition install, 
uninstall wubi from windows
backup important windows files(just in case, always a good idea)
defrag windows (important to do this) 
boot live cd
open terminal
type: sudo gparted
resize the end of your windows partion(slide it to the left to give you the room you need)
apply changes in gparted
(you should see a block of unallocated space)
close gparted
double click install icon
choose the "use free space" install
finish
reboot
click the hardware icon on panel when it shows up
choose the correct driver and WAIT(took me a long time before it loaded for me)
restart computer
goto system>administration>synaptic 
 search for nvidia-settings
 check box for install
 apply
close synaptic
open terminal
type sudo nvidia-settings
(this should offer to make a xorg.config for you if nvidia drivers aren't in use)
reboot
come back here and let us know if it works!

GL
Bruce

---

### Post by planetlarg2 on 2009-05-18
I fixed a blackscreen problem with 
        
        Option "UseDisplayDevice" "DFP-0"

I posted it here - [http://ubuntuforums.org/showthread.php?t=1149825](http://ubuntuforums.org/showthread.php?t=1149825)

---

### Post by zeldarocks on 2009-05-18
I'm scared of partitioning ubuntu, what if the drivers fail again, what if I want to delete ubuntu and retain all hardrive space for windows?

---

### Post by zeldarocks on 2009-05-18
also, would I run gparted on live cd or what?

---

### Post by zeldarocks on 2009-05-18
bump.

---

### Post by jbruced on 2009-05-19
> **zeldarocks said:**
> I'm scared of partitioning ubuntu, what if the drivers fail again, what if I want to delete ubuntu and retain all hardrive space for windows?

Very valid points, but no need to worry with gparted.

With the liveCD you can always delete your Ubuntu and swap partitions, and get your Windows partition back to where it was by resizing it with gparted.

Keep in mind this, if you end up deleting Ubuntu, you'll need to 

boot from your Windows install disk
choose repair a partition
drop to prompt and type
fixmbr
reboot

That being said, I believe you'll have fun fooling around and tweaking Ubuntu, and learn to love it.

You can make a small Ubuntu partion to start, and resize as you use it more.

---

### Post by zeldarocks on 2009-05-19
I don't have an installation disk in the event of an emergency...

---

### Post by jbruced on 2009-05-19
I understand.

Although you most likely will have no problems at all, maybe it isn't worth the risk for you.

I'm not sure of your comfort level with boot records, grub, partitions etc., but there's actually a way to copy your mbr(master boot record) using the dd command from the LiveCD, and that can be used to restore your system to the way it was also. (Though this is a scary proposition for the uninitiated)

If you ever do get a Windows install disk, come back to the forums and there'll be many people here waiting to help you take the next step.

---

