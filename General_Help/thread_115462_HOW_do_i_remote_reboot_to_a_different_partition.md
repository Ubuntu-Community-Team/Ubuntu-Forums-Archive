---
title: "HOW do i remote reboot to a different partition?"
date: 2006-01-10
forum: General Help
---

### Post by lysis on 2006-01-10
title explains it all.   i SSH into my box at home and would like to be able to reboot the PC and have it automatically select a different partition to boot from.  either bypassing grub for that one reboot . . . or maybe telling it to tell grub . . .


is this possible?


edit:

i would assume that this is a command i could type locally as well if i wanted to do something of this nature at home to bypass the grub loader.

---

### Post by inigmatus on 2006-01-10
I am interested in this solution too. I have xp on one drive, and ubuntu on a second drive, and they both share a FAT32 third drive for transferring files.

I would love to be able to figure out how to remotely switch between the two operating systems when I access my comp while on the road.

Any suggestions?

---

### Post by lysis on 2006-01-10
ok well i just thought of this.

we could manually edit the grub loader file to autoboot from a partition before we send the reboot command.   it's just a pain in the butt to go through all of that hassle just to reboot into another partition.

just an idea . . . let's run with it.

---

### Post by patrickfromspain on 2006-01-10
in suse, you can put reboot into windows (or whatever that's in grub). So, it's possible

---

### Post by lysis on 2006-01-10
you literally typed "reboot into windows" and it would do so?

i assume whatever the title is.

---

### Post by lysis on 2006-01-10
[QUOTE=patrickfromspain]in suse, you can put reboot into windows (or whatever that's in grub). So, it's possible[/QUOTE]
lysis@ubuntu:/download/news/decoded/THE ISLAND$ sudo reboot into testuntu
Password:
usage: reboot [-n] [-w] [-d] [-f] [-h] [-i]
        -n: don't sync before halting the system
        -w: only write a wtmp reboot record and exit.
        -d: don't write a wtmp record.
        -f: force halt/reboot, don't call shutdown.
        -h: put harddisks in standby mode.
        -i: shut down all network interfaces.

---

### Post by inigmatus on 2006-01-10
Cool, so you can reboot to Windows from ubuntu, remotely. Ok what about attempting a reboot from Windows to ubuntu remotely?

edit boot?

---

### Post by schilcha on 2006-01-10
[QUOTE=patrickfromspain]in suse, you can put reboot into windows (or whatever that's in grub). So, it's possible[/QUOTE]

AFAIK, SuSE does it with lilo -- at least they did up to 9.2

---

### Post by Whatsisname on 2006-01-10
you will have to edit your grub config and set the default partition prior to every reboot.

---

### Post by akshoslaa on 2006-01-10
I got sick if sitting infront of my computer waiting for linux to shutdown, then waiting through post so I could select windows from grub fr a quick game of whatever-I'm-playing-this-month...

So I wrote scripts to do it for me... :P (god I love Linux)

reboot_to_windows.sh
```

#!/bin/sh
zenity --question --text "Reboot to Windows NOW?"
val=$?
if [ "$val" = "0" ] ;
then
	cp /boot/grub/menu.lst /boot/grub/bak/menu.lst_$(date +%Y%m%d%H%M%S%N)
        cp /boot/grub/menu.lst /boot/grub/bak/menu.lst_BAK
	cp /boot/grub/menu.lst.windows /boot/grub/menu.lst
	shutdown -r now
fi

```
(dont forget to chmod +x it :P)

this makes a copy of your current menu.lst (where linux is the default) and replaces it with an edited copy you made previously where windows is the default. then issues the reboot comand. (you'll notice it also makes a seperate yime-stamped copy of your menu.lst file just in case. I've never needed it... but it certainly doesn't hurt... *shrugs* I'm allowed to be paranoid :P

The script needs to be run as sudo because users aren't allowd to mess with boot files, or usualy reboot the system. I added it to my sudoers file so it wouldn't need a password... but I'm running it visually, so it was easier that way.

sudo howto...
```

open a terminal and run:
$ sudo visudo

under the section:
# Members of the admin group may gain root privileges
add:
%admin  ALL=(ALL) NOPASSWD: /your/script/is/here/reboot_to_windows.sh

hit [CTRL]+X, Y, [ENTER]
then run:
$ sudo -l
you'll see a list of what you can run as sudo, your script should have NOPASSWD next to it.

```

Anyway... 

I've used Zenity for the 'are you sure?' function just because a) it shuts down quickly, there's no saving etc... so it makes sure you're ready before you run it... ansd I'm running it locally, not remotely, so I tend to launch it from a panel icon. You may need to alter it to use a text-based question,, (or remove the question altogether)

Step 2 is a bit harder, booting back to linux... (as windows is the default) I gave up on the open-source drivers fro this after mach failure and resorted to 'ext2fs anywhere' which means I can still get to my music while I'm playing games (take THAT EA!!1 *mutters about the music in NFS games* :P) Plus it meant I could read /boot from windows... so  wrote a batch file that simply did the reverse of the shell script, setting menu.lst_BAK back to the default and issuing shutdown from windows.

Back_to_Linux.bat
```

copy Z:\boot\grub\bak\menu.lst_BAK Z:\boot\grub\menu.lst
shutdown -s -t 0

```

Works like a charm

---

### Post by lysis on 2006-01-10
i GUESS i probably should've mentioned.  i don't use windows. 

i have two ubuntu installations.  one to test shit out before i break the one i use daily, and well . . . the one i use daily.  

i have a 3rd partition i'm about to install dapper on,  so yea . . .   


i DID notice dapper doesn't support my nic . . . or it won't work out of the box anyway.   but that's a different thread.


anyway; so grub doesn't have a switch or anything?  i have to manually edit?

---

### Post by akshoslaa on 2006-01-11
[QUOTE=lysis]i GUESS i probably should've mentioned.  i don't use windows. 

i have two ubuntu installations.  one to test shit out before i break the one i use daily, and well . . . the one i use daily.  

i have a 3rd partition i'm about to install dapper on,  so yea . . .   


i DID notice dapper doesn't support my nic . . . or it won't work out of the box anyway.   but that's a different thread.


anyway; so grub doesn't have a switch or anything?  i have to manually edit?[/QUOTE]

Fair enough... that just makes it easier :P

As far as I'm aware there's no reboot to [x] command for GRUB...  the method I use (above) will work just fine for multiple linux distros aswell... just mount the boot partition in each and set up a seperate 'default' file for each one...  and modify the scripts to eselect the one you want.

As a side note, if you update your kernel, it changes oyour menu.lst file so you'll need to recreate/edit your defaults when you do

---

### Post by lysis on 2006-01-11
well then what bootloader should i install to get this to work? lol

---

### Post by akshoslaa on 2006-01-12
[QUOTE=lysis]well then what bootloader should i install to get this to work? lol[/QUOTE]

well, my method is just using tjhe default grub install that ubuntu works with. If you can figure out how to install lilo you might get that nifty sounding reboot to [x] function... but I have no idea about that... (and neither does a very quick google)

---

### Post by datajack on 2006-01-12
There is a grub-reboot command which appears to do this.

---

### Post by akshoslaa on 2006-01-12
[QUOTE=datajack]There is a grub-reboot command which appears to do this.[/QUOTE]

well I'll be...

nifty, thanks :P

---

### Post by datajack on 2006-01-12
You don't want to know how many times I've gone through hoops getting things rebooting differently before I found this.

IIRC, it's just a one-off change to the boot process, I certainly remember using this (or something similar) in conjunction with a remote power switch to protect me from hosing a system after remotely upgrading the kernel.

---

### Post by lysis on 2006-01-12
[QUOTE=datajack]There is a grub-reboot command which appears to do this.[/QUOTE]
THANK YOU!!!!!


how did you find this?!?!?!?!?

---

