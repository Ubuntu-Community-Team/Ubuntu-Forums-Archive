---
title: "Hangs for a few seconds every startup"
date: 2006-06-21
forum: Desktop Environments
---

### Post by jeffreyvergara.NET on 2006-06-21
[Here's]("http://ubuntuforums.org/showthread.php?t=198702") the original post I made in "Hardware Help" I figured it's not a hardware so I decided to make another thread.

The Problem is this:

I installed Ubuntu Dapper 6.06, I'm sucessful installing it without giving me error. The problem is that every startup (on the logon screen), after the Floppy Drive's Led (disk activity) Lights up, My Hard disk Led (Red Light) begins to Freeze even though I am doing anything. Im still able to login but the Red Light still on Freeze, and after a few seconds/minutes (havn't timed it yet) My PC just Hang, but after a few seconds, around 5-10sec. the Hang is gone and so the freezed Red Light. Then everything is fine.

My Solutions:
Clean Installed using Ubuntu DVD in Text Mode = [COLOR="red"]HANG PROBLEM[/COLOR]
Clean Installed using Ubuntu DVD in Norma (Graphical)l Mode = [COLOR="red"]HANG PROBLEM[/COLOR]
Replaced Harddisk and redo the process above = [COLOR="red"]HANG PROBLEM[/COLOR]

Clean Installed using Ubuntu CD in Text Mode = [COLOR="red"]HANG PROBLEM[/COLOR]
Clean Installed using Ubuntu CD in Normal (Graphical) Mode = [COLOR="red"]HANG PROBLEM[/COLOR]
Replaced Harddisk and redo the process above = [COLOR="red"]HANG PROBLEM[/COLOR]

Clean Installation using Breezy worked! No problem at all.

My PC Specs:
P4 2.0ghz
1.0gb RAM
128mb Geforce MX 5200
ASUS P4PE-x board

80GB Primary Master
 - 1.0GB "linux-swap"
 - 14gb  " / "
 - 65gb " /home "

40GB Primary Slave
 - 18gb Window$ XP NTFS
 - 22gb FAT32

No Secondary Master (I don't know why, can't make my DVD-rw master)
Secondary Slave
 - DVD-+RW

---

### Post by Malac on 2006-06-21
[quote=jeffreyvergara.NET]
No Secondary Master (I don't know why, can't make my DVD-rw master)
Secondary Slave
- DVD-+RW[/quote] 
That may be your problem right there.
If there is no Secondary Master, Ubuntu will try to find one and then give up.
This will probably be the disk activity(red light) you are seeing.

I don't know what your hardware knowledge level is so please forgive if this is too basic. 
And you didn't say if they were ATA, whatever. I'm assuming IDE here.

Turn off and unplug your machine from the mains.
Open the case and find the drive which should be Secondary Master.
Check the small jumper plug is on the correct two pins.
You can usually find pictures of these settings on the internet or it sometimes involves removing the drive to see the diagrams of the jumper settings which are on the tops of some drives.
For master it should be on "Master" or "Cable Select" sometimes abbreviated to "CS".
If setting it to "Cable Select" make sure it is on the end connector of the Cable.
Also Check the Secondary Slave is set to "Slave" on the jumpers as this can confuse the BIOS if both drives are set to "Master".
Again if setting slave to "Cable Select" this time make sure Slave drive is on the middle connector of the Cable.
I prefer setting the "Master"/"Slave" myself rather than using "Cable Select"as I'm generally not moving drives around that much but neither should make a difference.

Okay once you have confirmed the jumper settings are set correctly.
Turn on the computer and enter the BIOS.
This involves hitting a key repeatedly until it brings up the BIOS screen.
Unfortunately different motherboards require different keys but it will probably be F2, Esc or one of the other Function keys, you'll just have to try until you find it.
Check in the BIOS that both drives are listed and are set to "auto detect" or something similar as if the settings have been set manually this too may confuse BIOS therefore OS.
If doing all this throws up nothing odd or doesn't fix the problem then it may be that Dapper is more sensitive to hardware errors than XP.
XP does tend to assume you don't know what you are doing and trys it's hardest to sort a working system out, usually using the lowest common denominator. Whereas Linux tends to want you to sort out your own settings allowing customisation freedom. Each approach has it's merits. :-)

Let me know if none of this works and we'll try something else.

---

### Post by jeffreyvergara.NET on 2006-06-21
Thanks Malac, I forgot to change the pin of my DVD-rw, it's now detected as Secondary Master, however I still got the same problem. But when I disable the dvdrom drive it works ok, no hangs... no DVD-rw.. T_T it's just weird that I did not have this kind of problem in Breezy.

---

### Post by Malac on 2006-06-21
Okay as that is now Secondary Master and XP still works with it but Dapper doesn't, says to me it is software/config file related.

I'd open your /etc/fstab file and just check you have the right file system/privileges setup for each partition. If all looks right try issuing ```
sudo mount -a
``` in a terminal and look out for any errors.

I had something similar once but it turned out to be that the OS had got stuck in a loop re-checking the hard disk for errors every boot instead of every 30 boots, which is the default.

I managed to fix it by editing my /etc/fstab file and commenting out all but my root partition, in my case /dev/hda2(by putting a # sign in front of each line).
Then rebooting letting it sit there do it's thing then re-edit /etc/fstab and reinstate the other partitions one at a time, rebooting in between each edit.
This worked for me but may be completely unrelated to your problem.

This may be shot in the dark but it maybe something to do with your harddisk controller has been changed in the Dapper Release and it's possibly broken it for your setup.
In which case a bug report is in order.

Let me know how it goes.

---

### Post by jeffreyvergara.NET on 2006-06-21
Hello, I did your advice but the problem is not fixed. maybe It's better for me to use breezy?

---

### Post by jeffreyvergara.NET on 2006-06-24
can someone help me here?

---

### Post by antivert on 2006-06-24
I'm noticing strange IDE hanging problems (with my hard drives) in kernel version 2.6.15.-23 and 2.6.15-25. DMA timeouts, "lost interrupts", etc. But it doesn't do it at all with kernel version 2.6.12-10. That is to say, it works perfectly. 

Looks to me as if certain ide chipsets have been affected by the upgrade. Something to check out!

---

### Post by jeffreyvergara.NET on 2006-06-24
yeah.. maybe it's the kernel version... it does not hang in breezy

---

### Post by jeffreyvergara.NET on 2006-06-26
[QUOTE=antivert]I'm noticing strange IDE hanging problems (with my hard drives) in kernel version 2.6.15.-23 and 2.6.15-25. DMA timeouts, "lost interrupts", etc. But it doesn't do it at all with kernel version 2.6.12-10. That is to say, it works perfectly. 

Looks to me as if certain ide chipsets have been affected by the upgrade. Something to check out![/QUOTE]

anyone filed this as a bug?

---

### Post by jeffreyvergara.NET on 2006-06-29
what if I try installing other ubuntu releases (xubuntu, kubuntu)? I think I prefer xubuntu...

---

### Post by jeffreyvergara.NET on 2006-07-05
any updates? im still experiencing this problem

---

