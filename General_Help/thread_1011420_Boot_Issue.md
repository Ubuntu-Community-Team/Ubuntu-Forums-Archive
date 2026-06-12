---
title: "Boot Issue"
date: 2008-12-14
forum: General Help
---

### Post by Reguardless on 2008-12-14
hello everyone.

I am having a boot issue with GRUB(as far as I know.) and can't for the life of me figure it out. I have searched around the forums and other websites but can't find an answer.
My dilemma is trying to boot Windows Vista. What happened was that I had Windows Vista on a 320GB SATA drive and I added a 28.3GB RAID drive and installed Ubuntu. But the mistake I made was not checking were the bootloader went. I installed it on the Vista drive, and it did some funky junk to my Vista drive. That made my drive give a "Boot Error 21". I figured out how to figure that out and got rid of that. Then, when I changed my BIOS around a bit, I got the bootloader to come back up and now when I load Vista(i changed the menu change speed to 50) it says "Loading Stage 2" and then go's back to the Bootloader menu.

any help would be mighty fine.

---

### Post by caljohnsmith on 2008-12-14
It sounds like you may have accidentally installed Grub to the boot sector of the Vista partition at some point. How about booting your Live CD, download the attached "boot_info6.sh.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info6.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will greatly clarify your setup and what the problem might be.

---

### Post by Reguardless on 2008-12-14
I must be having issues right now, but whever I type in the code you give me, I get an error. ```
ubuntu@ubuntu:~$ sudo ~/desktop/boot_info.sh.txt
sudo: /home/ubuntu/desktop/boot_info.sh.txt: command not found
```

Also, "booting from Live CD" is the CD you used to install, right? i'm usually not this slow about this stuff.

---

### Post by caljohnsmith on 2008-12-14
> **Reguardless said:**
> I must be having issues right now, but whever I type in the code you give me, I get an error. ```
ubuntu@ubuntu:~$ sudo ~/desktop/boot_info.sh.txt
sudo: /home/ubuntu/desktop/boot_info.sh.txt: command not found
```

Also, "booting from Live CD" is the CD you used to install, right? i'm usually not this slow about this stuff.
About the "Live CD", yes, that's just the Ubuntu install CD. The reason you are getting the error with that command is you are missing the "sh" after the "sudo", and also be sure to get the capitalization just right, because the commands are case-sensitive. That means the "Desktop" should be capitalized in that command. If you can simply copy/paste the command into the terminal, that would be best.

---

### Post by Reguardless on 2008-12-14
ahh. I did miss the "sh" in the command.

I have included the txt you told me give. hope it helps in my dilemma.

---

### Post by caljohnsmith on 2008-12-14
Unfortunately it looks like Grub was installed in the boot sector of the NTFS sda1 partition. Do you have a Windows Vista Install CD? If not, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). I would boot that, go to the command line, and run:
```
bootrec /fixboot

```
Hopefully that will repair the sda1 partition boot sector and not sda2, because sda2 is all ready OK. If it doesn't work, we can try another method. Also, what happens when you select the second Vista entry in your menu.lst? That should be the correct entry it looks like, assuming you are booting the sda drive on start up.

---

### Post by Reguardless on 2008-12-14
I will try the recovery disk.
The second Vista partition is actually a recovery drive. but it does nothing for me to boot to. But I may look into booting to it to see, cause I only slightly spent time in it.

---

### Post by caljohnsmith on 2008-12-14
> **Reguardless said:**
> I will try the recovery disk.
The second Vista partition is actually a recovery drive. but it does nothing for me to boot to. But I may look into booting to it to see, cause I only slightly spent time in it.
OK, that makes sense, so actually sda1 is your Vista partition; I was confused because sda1 didn't show any Vista boot files, but I just realized that's because it wasn't mounted since Grub corrupted its boot sector. If you run the "bootrec /fixboot", that might be all it takes to solve your problem. Let me know how it goes.

---

### Post by Reguardless on 2008-12-14
ok, I loaded the windows Vista Recovery disk but when I try to choose what hard drive, it tells me I have no hard drives. Even though I did not select a drive, I tried the command you gave me. Failure of course.
I am going to look more into the Recovery Disk not finding my HD's and will report back.

---

### Post by caljohnsmith on 2008-12-14
> **Reguardless said:**
> ok, I loaded the windows Vista Recovery disk but when I try to choose what hard drive, it tells me I have no hard drives. Even though I did not select a drive, I tried the command you gave me. Failure of course.
I am going to look more into the Recovery Disk not finding my HD's and will report back.
I think the Recovery CD might be having problems finding your drive because it is a SATA HDD. When you boot the Recovery CD, at the beginning does it say anything about "press F6 to load additional drivers" or something of that sort? I think you will need to provide it with a SATA driver, or if you can go into your BIOS and switch the SATA drive to use "IDE emulation", that has worked for others.

---

### Post by Reguardless on 2008-12-14
hmm, still no drives showing. neither the SATA nor the RAID drive. I might just go to my last option and just do a full drive wipe and rewrite the backup of the drive I did with ACRONIS. but i'm not sure about this..

---

