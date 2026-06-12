---
title: "Problem booting from external HDD"
date: 2009-01-30
forum: General Help
---

### Post by Kriips on 2009-01-30
I liked the idea of having Ubuntu with me wherever I went. So what I did (or tried to do) was install Ubuntu on my Verbatim 160GB external HDD so I could use Ubuntu wherever I went simply plugging it in and booting from the external hard drive.

I installed Ubuntu on a laptop with Vista as the primary OS. And it works fine: if I plug in the external drive, It loads up GRUB and boots Ubuntu. The real problem comes when I try to do the same with my desktop computer (which runs XP btw). I set BIOS to boot from the HDD first and then it just stalls after a while only showing me a black screen with one blinking line on the top-left corner. I'm guessing that's where it checks for the boot devices in the order I've told it to. But it does not load up GRUB, it just stalls there.

I'd appreciate all the help I can get so thanks in advance.

---

### Post by blazemore on 2009-01-30
This happens to me if I have my ipod plugged in when I turn on the PC.

Check to see if you have any unneccesary USB storage devices inserted.

Also, check the boot order in your BIOS:
1 External hard drive
2 Internal Hard drive
3 any
4 thing
5 else

---

### Post by Kriips on 2009-01-30
well, it did turn out that in the BIOS boot priority list I had memory card readers in the end of the priority list but removing them didnt help I'm afraid :(

---

### Post by blazemore on 2009-01-30
And you're sure you don't have any other devices plugged in? ipod for example...?

---

### Post by Kriips on 2009-01-30
3 more USB ports are used:

1. Headset power suply
2. Sony Ericsson phone connector with no phone on the other end
3. Mouse cord

and the external HD is plugged into the front USB port not the rear

---

### Post by Kriips on 2009-01-30
I also tried hooking it up to the rear USB ports but nothing

---

### Post by blazemore on 2009-01-30
Hmm. I don't know if you want to do this, but it might help.
Open up your external hard drive, take it out, and connect it internally.
Boot off that and see if it works.

However, personally I wouldn't be bothered to do that. Maybe someone has had this problem?

---

### Post by Jameshardy88 on 2009-01-30
ive got ubuntu installed on one of my external Hard drives it also works perfectly whilst on the desktop it was installed on, however if i transfer to to any computer it just fails to recognise it. I don't know if this means that it is restricted to only being used on the computer from which it was first installed or not though?

---

### Post by Kriips on 2009-01-30
I hope that's not the case :(

The whole point having Ubuntu on an external HDD is being able to use the same Ubuntu intallation anywhere

---

### Post by thestig_992 on 2009-01-30
I have usb DSL, which doesnt work on my computer, but works on most others, even with my internal hdd grub pointing at the usb. I spose that some PCs just dont support external OSs for some reason

---

### Post by Kriips on 2009-01-30
What I don't get is why doesnt it even load GRUB up :/

---

### Post by blazemore on 2009-01-30
It's not an arbitrary restriction. This isn't Windows.

---

### Post by Kriips on 2009-01-30
is there any way to boot without GRUB even asking you?

---

### Post by Kriips on 2009-01-30
I actually reinstalled Ubuntu from my winXP computer and it still gives the same result... i'm guessing that it's my computer's fault :/

---

### Post by blazemore on 2009-01-30
> **Kriips said:**
> is there any way to boot without GRUB even asking you?

No, since Grub is the Ubuntu bootloader.
It boots Ubuntu directly, unlike booting Windows from Grub, which simply passes control to the Windows bootloader.

---

### Post by caljohnsmith on 2009-01-30
Kriips, it may be an issue with how the HDD is configured in BIOS if you can't even get Grub to load on start up; but first I think it would help to get a better picture of your setup on that HDD to make sure there isn't anything else that's obviously an issue. How about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by Kriips on 2009-01-30
Hmm, I've managed to somehow save GRUB onto my internal HD and now i can't boot without having the external HD plugged in cause it starts giving errors :/ (actually, it screwed up my mbr as well so i had to fix that)

How can I delete it?

---

### Post by caljohnsmith on 2009-01-30
To restore a Windows MBR to your Windows drive, how about first doing:
```
sudo fdisk -lu
```
Find which is your Windows drive, and then try:
```
sudo apt-get install lilo
sudo lilo -M /dev/[COLOR="Blue"]sda[/COLOR] mbr
```
But replace "sda" if the Windows drive is another drive. Then you should be able to boot directly into Windows again. It would really help if you can post the output of the script from my previous post, so then we can get a clearer picture of your setup.

---

### Post by Kriips on 2009-01-30
I got the mbr back using 'fixmbr' in the recovery console using the windows CD, the output of the other commands coming soon

---

### Post by Kriips on 2009-01-30
```
kaarel@external-HDD:~$ sudo apt-get install lilo
[sudo] password for kaarel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lilo is already the newest version.
lilo set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 241 not upgraded.
kaarel@external-HDD:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.
kaarel@external-HDD:~$ 
```

---

### Post by Kriips on 2009-01-30
Good news is that it worked perfectly, bad news, I still haven't gotten around the original problem :(

---

### Post by Kriips on 2009-01-30
> **caljohnsmith said:**
> Kriips, it may be an issue with how the HDD is configured in BIOS if you can't even get Grub to load on start up; but first I think it would help to get a better picture of your setup on that HDD to make sure there isn't anything else that's obviously an issue. How about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

I did what you asked and attached the file to this post as it was quite long

---

### Post by blazemore on 2009-01-30
You could install Grub onto your external hdd. I'm not sure how to go about doing that though

---

### Post by caljohnsmith on 2009-01-30
It looks like you have Grub installed correctly to your Ubuntu drive, so if it doesn't boot when connected to your other computer, it might be an issue with the other computer, specifically BIOS settings. Is your Ubuntu HDD SATA or USB? If it is USB, does the BIOS of that computer support booting USB drives? Also, what HDD-related settings do you have in the BIOS of that computer? Look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc.

---

### Post by Kriips on 2009-01-30
I actually reinstalled Ununtu from the desktop computer onto the (USB) external HDD and now it also runs on the laptop... I'm guessing problem solved... for now anyways.

Thanks for all the help everybody! Really appreciate it :)

---

