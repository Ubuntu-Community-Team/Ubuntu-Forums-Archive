---
title: "Ubuntu 9.10-waiting to mount /dev/mapper/cryptswap1 in /etc/fstab at startup"
date: 2009-12-27
forum: Desktop Environments
---

### Post by elegie on 2009-12-27
From looking at Internet sites and forums, the following issue may well have come up with other users. When the Ubuntu 9.10 release has been configured to use an encrypted swap partition, a message like the following appears when the OS boots up:

```
One of the mounts listed in /etc/fstab cannot yet be mounted
swap: Waiting for /dev/mapper/cryptswap1
Press ESC to enter a recovery shell
```The message is displayed for a short time, and in each case, the boot process seems to proceed normally afterwards. When the Ubuntu software was installed, the "Require password to log in and to decrypt my home directory" (or something like that) option was chosen when specifying information for the initial user. Later on, a subsequent user was added, but without an encrypted home directory. This subsequent user's home directory and the user account were deleted. After this, a user account was added with the specification that the home directory be encrypted. This was probably done with the adduser --encrypt-home <username> command. It is not clear as to whether having an encrypted home directory means that the swap partition (in this case, /dev/sda4,) is automatically encrypted. When the ecryptfs-setup-swap command was used, it displayed a warning about the hibernate functionality being affected by the usage of encrypted swap. Confirming the warning seemed to do processing on the system, presumably to setup the encrypted swap.

A startup message about mounting /dev/mapper/cryptswap1 may raise concerns for less experienced users, and the ability to enter a recovery shell might pose security issues (locking a system at the bootloader might not be the most convenient arrangement.) As such, it might be useful to look into the cause of this issue. This message seems to come up even with version 2.6.31-16-generic of the kernel.

---

### Post by fishyf on 2010-01-07
Well, today I attempted up upgrade from Jaunty to Karmic using the Update Manager.
After a number of hours, I have now arrived at a boot screen that displays this message and does not proceed.
I am able to go to the recovery console, but there is no obvious fix.

Swap seems to stay waiting for cryptsetup to create the encrypted partition, and so there's no progress.

It's not just an inconvenient message, it results in a broken computer.

---

### Post by fishyf on 2010-01-07
By the way, a quick fix is to use an unencrypted swap by deleting the entry in /etc/crypttab and adding an entry in /etc/fstab.

---

### Post by Justin_West on 2010-01-22
I am very avid supporter of Ubuntu, but I think this is a very serious issue that should be addressed.  I bought my very first netbook with Ubuntu 9.10 pre-installed, as well.  When I had a chance to show it off 3-4 days later to my friends at work, I got this error at startup and my netbook froze.  I had to power off the notebook 3-4 times before it finally went through to the Ubuntu login screen.

It was kind of embarrassing and ruined whatever chance I had of convincing some of my friends to make a switch to Ubuntu.

> By the way, a quick fix is to use an unencrypted swap by deleting the entry in /etc/crypttab and adding an entry in /etc/fstab.

Many people who are new to Ubuntu would not understand what the above means...

---

### Post by espressobeanie on 2010-01-31
Yes. Please explain in n00b speek.

---

### Post by jwmuelle on 2010-02-01
I know there will be folks more qualified than I to help (and I only peruse these forums a couple times a week)... but to start, need additional information about your configuration.  For the direction I'd go - need to know your disk config.  Attach the output of:  sudo parted --list     

Also, attach the contects of /etc/crypttab   and   /etc/fstab

crypttab is the definitions for the encrypted drives/partitions.
fstab is the definitions for all the automatic mount points.


use  "man crypttab", "man fstab", "man mkswap", and "man swapon"   to get an idea of where this might lead.

You'll essentially want to remove the definitions referencing an encrypted swap partition (crypttab, fstab), you may need to delete the encrypted partition and add a new one,  format a "normal" swap partition (mkswap), activate it (swapon), and add it to mount when the system starts (fstab).

---

### Post by lenu on 2010-02-20
i just want a working system of ubuntu server with encryption enabled, at the moment it seems impossible. is the solution to simply drop encryption or what is one supposed to do in order to get a working /home encryption? i just downloaded the ubuntu 9.10 server edition and did a fresh install on a new computer, but the above mentioned error message keeps me from proceeding during the boot process.

---

### Post by jose_Afonso on 2010-02-23
in my computer the problem was originated on /etc/crypttab list, have listed the swap partition like sda5, but this partition not exist, the swap device is /dev/sda2,the message no more with:
 $sudo gedit /etc/crypttab & # open the document in text editor
and fixing the error renaming sda5 to sda2
if your problem is like this can to be corrected simply...

sorry by my english... is very, very bad, so, i used google translate to write this message... any questions contact me:D

---

### Post by erdalronahi on 2010-02-23
I got the same problem on a computer that I set up for a friend. Extremely embarassing. 

The original 2.6.31-14 kernel still worked until today, while after the update to kernel 2.6.31-19, I got the said error about the swap. 

Now also the 2.6.31-14 kernel gives this error, and the computer does not boot anymore. Extremely annoying. I do not even have a possibility to boot into recovery mode. 

Any ideas?

---

### Post by Anhedonia on 2010-02-24
In my text only server install this is what causes the crash to recovery console.

(not when it loads the file but as soon as i push left or right interestingly enough, at some point it did let me edit a file and save before crashing on the next one and never being right again despite 3 reinstalls)

Ive now read five. different threads with a bunch of users not knowing whats going on and "apparently" no decent solution in sight. Argh.

---

### Post by erdalronahi on 2010-02-25
While trying to fix this issue, I ran the text-mode installer off a USB stick again. When I came to the "partitioning" section, I saw that the installer did not see the swap partition (/dev/sda5 in my case) as a swap partition. After I had reformatted the partition as linux-swap, the problem disappeared. 

So for me two things were necessary:
1. keep the swap partition unencrypted by modifying fstab and crypttab
2. actually format the swap partion as a swap partition

Hope this helps others.

---

### Post by progone on 2010-08-25
I barely have a clue to how to fix it like you did.  Once in a blue moon I get the crypts1 error. 


I wish I could fix it.

---

### Post by TerryRiegle on 2010-08-30
FYI
Just set up Ubuntu 10.04.1 LTS on an old machine as a test for the new OS release.  This same machine has been running Ubuntu 8.04 LTS since it's first release with no problems.

 During boot I am getting the same error message as mentioned here.  If you don't respond to the error message the machine does continue to boot and appears to function.  (Haven't worked with it too long yet so I can't say that there are absolutely no side effects.  Did notice that machine fails to power down properly during shut down.  Shutdown appears to hang.  Don't know if this is related or not.)

Machine is old 500MHz Intel PIII.  Install was from alternate install CD. Option to encrypt files in home folder was selected during install.  Ubuntu 10.04.1 is the only OS installed on this machine.  Option to use entire disk with one partition for swap file and remaining partitioned for all other files; was selected.   Update manager has completed all updates available.   No other modifications have been made to the systems files or configuration; they are as the install CD made them.

Just throwing this out to let all know that, as of this date, there is still something not quite right out there.

---

### Post by FerroPower on 2011-08-08
Hi, I too face similar problem with my kubuntu, my machine crashed while I was editing an encrypted drive which was loaded using Truecrypt, After that my swap was unusable and everytime I use to get the error waiting to mount the cryptswap1. I ignored it for many days but since my swap was not usable I was searching through forums Thanks to you guys I was able to get my swap area back. 

All I did was edit the /etc/crypttab remove the line where it points to crypted swap
save the file and reboot
and then use mkswap to make your swap partition usable
in my case it was **mkswap /dev/sda5 **
it gives me UUID for sda5 for eg. [U]7a371f8a-8143-45ca-8078-7d8b422d4d26
[/U]
open the  fstab for editing e.g. [FONT=Courier New][COLOR=Blue]**sudo kate /etc/fstab**[/COLOR][/FONT]

use the UUID which you got and add the line to point to swap. 
in **my case** it was like 
[FONT=Courier New][COLOR=DeepSkyBlue]UUID=7a371f8a-8143-45ca-8078-7d8b422d4d26  swap swap defaults 0 0
[COLOR=Black]
Thats it ! it worked for me.

[COLOR=Red]**P.S. I am using Kubuntu 11.04. be sure to check your version of ubuntu before applying anything.**[/COLOR]
[/COLOR] 
[/COLOR][/FONT]

---

### Post by malapradej on 2011-09-16
Ferropower #14 - thanks for the advice. Solved my problem. I am on ubuntu natty....

---

### Post by mohave on 2012-03-05
Thank you FerroPower!

From Oneiric 11.10 fighting to get swap to hibernate ;)

---

