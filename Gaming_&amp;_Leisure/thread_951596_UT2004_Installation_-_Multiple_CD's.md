---
title: "UT2004 Installation - Multiple CD's"
date: 2008-10-18
forum: Gaming &amp; Leisure
---

### Post by Scorpio11 on 2008-10-18
Hi

I have recent installed Ubuntu 8.04 my PC. I have never used Ubuntu (or linux for that matter).

I am wanting to install UT2004 (the CD version). Now there are 5 discs to install. I have followed the instructions for loading the installation screen via the terminal and all is well until i get to the point where i have to insert disc 2. It simply refuses to eject and i have to terminate the installation. I even tried copying the CD's onto my desktop, nothing.

Is there a way i can install games with multiple discs and be allowed to eject the cd so i can put in the next one?

Scorpio

---

### Post by lavinog on 2008-12-20
I have the DVD version. On the DVD there are folders for each cd:
```

0x0409.ini   CD5           instmsiw.exe
AutoRun.inf  CD6           linux-installer.sh
CD1          CD7           Setup.exe
CD2          Data1.cab     Setup.ini
CD3          ecesetup.exe  UT2004 Editor's Choice Edition Mod Installer.msi
CD4          instmsia.exe

```
you could probibily copy each cd to a folder on your hd and install from there.

You also might be able to remaster your cds onto a DVD for future use.
I might do that with mine to add my ini files and all of the patches.

---

### Post by PoHandle on 2008-12-20
I was having a similar problem.  What I was able to do was make ISOs of each CD, then mount/umount each ISO as needed for the installation process.

To make ISOs backups of your cds:

**1)** Insert your CD into your CD/DVD-ROM.

**2a)** You can use Brasero (Applications>Sound & Video>Brasero Disk Burning) to copy the disk to an image.  Just open Brasero, click on **Disk Copy** and then under the "Select Drive to Write to" section, select **File image** from the dropdown menu, then click Copy.

**2b)** Alternatively, you can use the terminal (Applications>Accessories>Terminal) to make ISO files from a command line interface.  In terminal, type the command:
```
mkisofs -J -l -o ut2004-cd**xxx**.iso /media/*<your ut2004 CD mount point>*
```
Where the xxx is, replace with the CD number (eg: 001)

**3)** Unmount/eject the CD and repeat steps 1 and 2 for each CD in your set.

**4)** Once all ISOs are created, mount the first ISO (eg ut2004-cd001.iso) with:
```
sudo mount -o loop *ut2004-cd001.iso* /media/ut2004
```
and run the installation script with
```
sudo sh /media/ut2004/linux-installer.sh
```

**5)** When the installer prompts you to insert the next CD, unmount the first ISO with
```
sudo umount /media/ut2004
```
and mount the next ISO with
```
sudo mount -o loop *ut2004-cd002.iso* /media/ut2004
```
and click OK to continue the installation.

**6)** Repeat step 5 for the rest of the CDs (ISOs).

**7)** When the installer finishes, unmount the final ISO and you should be good to go.  Run the game with
```
ut2004
``` in terminal

I wrote these steps from memory, so I'm sure I made a mistake somewhere.  Please point them out so I can correct them.  Also, I used a Nautilus script to mount/unmount the ISO files, so I don't know if the commands are 100% correct.  I'm pretty sure that linux-installer.sh has execute permissions by default, but if not, just copy the file to your home folder, chmod it, and run it from there.

I hope this helps.

---

### Post by epitaph on 2008-12-20
Copy the linux-installer.sh to your desktop and run it.

```
sudo sh ~/Desktop/linux-installer.sh
```

---

### Post by GSZX1337 on 2008-12-20
When you click on the installer file, are you choosing "run in terminal"? If you are, DO NOT DO THAT! I did that and couldn't get my discs to be unmounted. Just select "run".

---

### Post by PoHandle on 2008-12-22
I ran the installer from the terminal and it worked just fine for me.  The prompts in the installer should properly halt the installation to allow you to unmount your disk.  You can just open a new tab in the terminal to *sudo umount* it.

---

### Post by Brebs on 2008-12-23
> **Scorpio11 said:**
> refuses to eject
This is presumably because you've made the CD "busy" by "cd"ing into a directory on the CD (e.g. /media/cdrom or whatever the mount point is). So, be careful what the current directory is, because Linux is nowhere near user-friendly enough to warn anyone about this.

If the installer script/executable is on the CD, then run it with one of e.g.:

bash /media/cdrom/runthis.sh
/media/cdrom/runthis.run

To eject the CD, an easy way is with the "eject" command.

---

### Post by lumpy211 on 2009-03-27
Since the OP hasn't marked this as solved, I figured I'd offer up how I solved this issue today on Arch Linux (although the general steps should be the same on any Linux distribution).

I tried creating images of each of the CDs but that did not work. What did work, however was copying every file from every CD to a folder on my hard drive (called UT2004). After every file was on my hard drive, I had the same file layout as lavinog did. It needs to be mounted to either /media/cdrom or /mnt/cdrom, so I had to create an ISO image, so in a terminal type:

```
mkisofs -J -o UT2004.iso UT2004
```

Then, mount it to /media/cdrom with

```
mount -o loop UT2004.iso /media/cdrom
```

It works best if you copy the install file to your home folder, so type

```
cp /meda/cdrom/linux-installer.sh ~
```

and finally, run the installer by invoking

```
sh ~/linux-installer.sh
```.

After that, it worked great for me :) When you're done, be sure to clean up by deleting UT2004.iso (or burning it on a dual-layer DVD if you want) and the folder UT2004 (otherwise, that's 10 GB of wasted space!)

---

