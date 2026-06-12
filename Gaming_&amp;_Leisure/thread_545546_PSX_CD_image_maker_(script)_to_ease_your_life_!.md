---
title: "PSX CD image maker (script) to ease your life !"
date: 2007-09-07
forum: Gaming &amp; Leisure
---

### Post by verb3k on 2007-09-07
[COLOR="Red"][SIZE="4"]UPDATE: Another version of PSXIM featuring a GUI has been released. If you prefer using graphical user interfaces see this topic: [http://ubuntuforums.org/showthread.php?t=664656](http://ubuntuforums.org/showthread.php?t=664656)[/SIZE] [/COLOR]

Hi all,

A while back , I started backing up some of my valuable PSX games to protect them from extinction ( you know , games like Resident Evil and Silent Bomber :) )  but the process was a little bit tiring and time consuming , so I decided to write a script to take care of it , then I thought about making it portable , and finally I decided to optimize it and share it with you. This script eases the process of backing up your PSX games using cdrdao. It creates a directory and places the backup files  in  it, and clearly you can play your backups using a PSX emulator like epsxe  while keeping the game's CDs in a safe place. Hope you benefit from  it , and comments are warmly welcome.

Using the script is easy , first download the script attached below and then install it by opening a terminal and entering the following commands respectively (assuming you downloaded the script to your Desktop) :
```

$ cd Desktop
$ chmod a+x psxim.sh
$ sudo cp ./psxim.sh /usr/bin/psxim

```

Now the script is installed , let's use it ....
The script can be used as follows:
```

#Usage:
$ psxim <game_name> <device> [<output_directory>]

#Example:
$ psxim silent_bomber /dev/hda /home/user/Desktop

```
Note that the output directory is optional. If it is not given , the current working directory will be used instead.

If you don't know the device name of your CD/DVD drive just enter the game name only and psxim will list all cdrom drives on your machine. Example:
```

user@ubuntu:~$ psxim resident_evil

No device name supplied... it should be one of these:
/dev/hda
/dev/hdb

Usage  : psxim <game_name> <device> [<output_directory>]
Example: psxim silent_bomber /dev/hda /home/user/Desktop
user@ubuntu:~$ 
```
In the above example , psxim told me about the CD/DVD drives on my system , it may be different in yours.

One last thing , if you want to include spaces in your game's name you must put the name between quotation marks ("") like this:

```
$ psxim "Resident Evil" /dev/hdb /home/user/Desktop
```

If you include spaces without quotation , the script will not function properly, so be careful.

[COLOR="Red"]Additional notes:[/COLOR]
1-Using CD-RW drives to back your games is preferred , because I've noticed some games may not be backed up correctly using CD-ROM drives.(thanks for acoustibop for the tip)
2-In case you don't know, PSX refers to the popular gaming console PlayStation (or sometimes called PlayStation one )


I am really interested in knowing whether it works for you , so feedback is really appreciated.

Thanks in advance,
verb3k

**Update (June 10 2008 ) :**
Another minor change (Note that the download counter drops to zero every time the file is changed here :) so it doesn't represent the number of people who tried the script)

**Update (September 25 2007) :**
Minor correction.
Removed a useless message string.

---

### Post by acoustibop on 2007-09-07
Actually, most people with IDE optical drives usually seem to to have them on the second IDE channel, verb3k, which would be /dev/hdc and/or /dev/hdd.

One thing I've noticed about ripping Playstation games, especially if they're copy or mod protected, is that -RW drives often work better than -ROM drives; this is because they can often read the subcode sectors better.

---

### Post by verb3k on 2007-09-08
Thanks for replying acoustibop,
PSXIM will detect any CD drive whether in first or second channel ...you can try this command :
```

grep cdrom /etc/fstab | cut -f 1 -d " "

```
This command will list any drive that has been detected on your system by the kernel , it takes any line which has the word "cdrom" in /etc/fstab and will display the device name only.

And you are right , I've noticed that some games will not be read properly on CD-ROM drives ,but will be in CD-RW or DVD-RW  drives , thanks for reminding me , I will include this in the topic :)

 thanks your your time.
verb3k

---

### Post by verb3k on 2007-09-08
It seams that only few people have tried the script :(

---

### Post by po0f on 2007-09-09
verb3k,

I wrote one myself I already use.

Just give it time, people will find your script.  :)

---

### Post by mr.baggy on 2007-09-12
Just what i was looking for, thanks a lot.

---

### Post by verb3k on 2007-09-14
I am happy that some people have benefited from the script 
Thanks for your feedback

---

### Post by Ledah on 2007-09-21
Thank you!

I had a lot problems with the creation of  working PSX images. Nothing worked (dd, k3b, kiso, ...).

Finally there's a simple method to do this :grin:

---

### Post by Airsix on 2007-12-23
oooh there is someone more now :)

I have been searching for something like this for hours, 
then finally i found your script, i used it, and i succeed in my goal. 

There problem is for sure related to some restriction/protection of 
psx cd's. Well done! :)

Oh if it could help: i have tried this script also with mandriva :KS 2008 one, and it works fine too :)

Great job, man!8) \\:D/

---

### Post by DKnight on 2008-01-01
Nice script!

---

### Post by boltronics on 2008-10-01
Nice. Thanks verb3k!

---

### Post by lonewaster on 2010-07-13
Thanks for this. 
Takes a while to rip, but in the end it's worth it.

**Is it piracy if I download a copy of a game I already have??**

---

### Post by frankake on 2011-04-30
first thanks for the script, it works very well !
second if you're using a SATA drive and not a IDE device, it's not /dev/hda, it's /dev/sr0 (at least in Xubuntu)

---

### Post by mips on 2011-04-30
AcetoneISO will do the same for you.

---

