---
title: "erasing grub"
date: 2009-03-14
forum: General Help
---

### Post by deathscith on 2009-03-14
alright, so a while ago, i installed ubuntu on a secondary harddrive, i got it working after a while, and my vista and ubuntu co-existed without hassle, my grub worked fine, tho i am going to a lan tomorrow and i'll spare you the details, but i needed extra room for games and such so i cleared up the secondary drive with ubuntu in vista, it all worked fine, but i figured my mbr would be out of whack, so i rebooted and lo and behold, grub error 17, i then went into my linux and ran the command that had let me get into my windows before when i was fixing it

```
sudo apt-get install syslinux

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```

rebooted and bam, grub error 17, that didnt happen before, now im questioning what to do, is there a way to do this from my live ubuntu, or do i need my windows disk, im running windows home, but i have a windows ultimate, will this matter?

---

### Post by nelskurian on 2009-03-14
For PCs with SATA disks, the windows XP install disk can not fix the boot problem. You need use Windows Vista install DVD to fix the Grub problem.

How to use Windows Vista install DVD to fix the boot problem?

1. Put the Windows Vista installation disc in the disc drive, and then start the computer (set to boot from CD in BIOS).
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair (Vista in this case), and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Once in the command prompt, type exactly Bootrec.exe /FixMbr and then press ENTER. You will see "operation completed successfully."
8. Reboot and set BIOS to boot from the HDD again.

GRUB will be overwritten in step 7 and your old bootloader (windows xp, windows vista) will once again take control of loading your OS(s).

*ref:sahabcse*

---

### Post by deathscith on 2009-03-14
tried that, but because i dont have my vista home disk, i have an ultimate disk, so i cant click next. thus cant get to the command promt, thanks for the help tho

any other ideas?

---

### Post by meierfra. on 2009-03-14
> sudo apt-get install syslinux

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

Did you get any error messages while executing whose commands?
If not, then I would guess that either

1)  You are not booting from /dev/sda

or

2)  The boot flag is set to the wrong partition.

So make sure that the boot flags is set to the windows system partition, that the bios are set to boot from the windows drive and that you use the windows drive in "of=/dev/sda"

You can use "sudo fdisk -lu" to figure out whether the boot flag is set to the Windows partition.

You can also use "lilo" to restore your MBR:

```
sudo apt-get install lilo mbr
sudo lilo -M /dev/sda
```

And you can use lilo to set a boot flag. For example

```
sudo lilo -A2 /dev/sda
```
sets the boot flags to the second partition on /dev/sda (that is : to /dev/sda2)


**If none of this solved your problem**

In order to get a clearer picture of your setup, I suggest to boot from your Live CD and download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by deathscith on 2009-03-14
yea, so i was working with a live usb key, installed ubuntu onto it, and well, i installed a bunch of updates, and then ended up overloading it, its full, and ubuntu no longer boots up, i moved it to another machine and deleted the trash file, that freed up 40mb, i thought that would help, tried booting again and it crashed... again. it leaves me with the ability to type like im running dos, but no responce from any commands i attept, not even help, so im guessing that its just input and theres no output, any ideas as to help? i had done the syslinux thing and it said it was up to date, typed in the other command and it said there was nothing to fix, so no error from that, also tried the lilo -m, with no success, it gave me an error but i forget what it said exactly, i rebooted to test if the syslinux thing had worked and nope, now i cant even get into my ubuntu... im pretty boned right now, any ideas?

---

### Post by deathscith on 2009-03-14
alright, so im met with some success, i found a dsl (damn small linux) disk i had when i was trying to work on a 95 laptop for school (failed project). dsl is knoppix based but can i use that still for this? or should i continue testing for my ubuntu disk, i also have a whoppix disk laying around and a arch linux, to my own downfall none of them are marked... way to go me, so its a fun guessing game. yea, thats my update on my predicament

---

### Post by meierfra. on 2009-03-14
> any ideas?

Just following the directions at the end of my last post to download and run the "boot info script".  That should help to figure out what is going on.

---

### Post by meierfra. on 2009-03-14
How last messages crossed in cyberspace.

> Now i cant even get into my ubuntu.
Do you mean  you can't  boot from the Ubuntu  Live CD anymore?

You should be able  run the Boot Info script from any linux LiveCD.

---

### Post by deathscith on 2009-03-14
> **meierfra. said:**
> How last messages crossed in cyberspace.


Do you mean  you can't  boot from the Ubuntu  Live CD anymore?

You should be able  run the Boot Info script from any linux LiveCD.

what i meant was, i had installed ubuntu to a usb key, i was booting from that usb key to get this working, that was my live cd, that key, no longer works. so im looking for an alternative, i found an improperly burned ubuntu live cd, but that wont help me, im still looking for a live cd but as of right now, all i have to work with are dsl (knoppix based) and whoppix (again knoppix i believe)


right now im working on properly burning that ubuntu disk i found, hopefully it works out, btw youve been alot of help thus far, thanks

---

### Post by deathscith on 2009-03-14
so i came up with a quicker fix, im going to... aquire by means i cant say, (tho for those who know much about the internet probably know how im aquiring it if i cant say it.) yes, im going to aquire a vista home dvd instead and do the first post, seeing as the ultimate edition i had prevented me from doing that, the one im getting is the lite version because i dont have any blank dvds laying around, hopefully it works

---

### Post by meierfra. on 2009-03-14
Just get a legal Vista Rescue CD:

[http://www.pcworld.com/downloads/file/fid,71039/description.html]("http://www.pcworld.com/downloads/file/fid,71039/description.html")


Or use SuperGrub:

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by deathscith on 2009-03-14
getting the repair cd now, good call :3 saves me alot of time

---

### Post by deathscith on 2009-03-14
ok, so the repair cd didnt work, booted off it, tried to repair, said it wasnt supported, my os in the vista screen is 

windows vista (tm) home premium (recovered) and i try working with that, but no success, supergrub it? or use the lite vista im downloading, i'll look into the supergrub first since its quicker

---

### Post by deathscith on 2009-03-14
woot, supergrub cured it, its all working, boots fine, thanks alot :3

---

### Post by meierfra. on 2009-03-14
> supergrub cured it, its all working, boots fine, 

Good news.  I'm still wondering why "sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda" did not work. Maybe your Ubuntu LiveUSB was already corrupted. Oh well, we'll never know.

---

