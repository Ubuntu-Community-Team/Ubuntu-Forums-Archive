---
title: "I need a virus please!"
date: 2005-12-26
forum: Desktop Environments
---

### Post by anil_robo on 2005-12-26
Hi all! I know it sounds weird, but I need to download a windows virus on my linux box. I just want to check if clamav works, and how well. Any help would be greatly appreciated. Please send me link to some website which contains viruses.

Thanks :D

---

### Post by MartinG on 2005-12-26
[QUOTE=anil_robo]Hi all! I know it sounds weird, but I need to download a windows virus on my linux box. I just want to check if clamav works, and how well. Any help would be greatly appreciated. Please send me link to some website which contains viruses.

Thanks :D[/QUOTE]```
sudo apt-get install clamav-testfiles
```

---

### Post by Perfect Storm on 2005-12-26
I got the flu, interrested? :mrgreen:

---

### Post by ardchoille on 2005-12-26
[QUOTE=Artificial Intelligence]I got the flu, interrested? :mrgreen:[/QUOTE]
ROFLMAO!!!!!!!

---

### Post by anil_robo on 2005-12-26
[quote=MartinG]```
sudo apt-get install clamav-testfiles
```[/quote] 
THanks! I actually installed clamtk (gui frontend for clamav) and did a recursive scan to the testfiles (/usr/share/clamav-testfiles). It identified all the "test" viruses. I could see that the default action was set to "do nothing". Other options available were "quarantine" and "delete". Details with pics here: [http://www.ubuntuforums.org/showthread.php?t=104001#19](http://www.ubuntuforums.org/showthread.php?t=104001#19)

I believe clamav is just a scanner, not a realtime virus monitor. I'm so sorry for asking this, but probably you can understand my paranoia given that I've used windows for 11 years now - my question is: Is there any way I can schedule virus scans of my hard disk on a regular basis, if not in realtime? I'm asking this just to make my windows partitions secure (which I have mounted in Ubuntu).

---

### Post by bscbrit on 2005-12-26
I use clamav on my mail server - the viruses cannot affect linux but I don't want to be responsible for passing them on to a windows user.

Everyday, it correctly identifies at least 2 viruses and quarantines them accordingly.  Just recently, I and many others on this ISP, were subjected to a massive viral attack resulting in over 160 individual infected files arriving in my inbox each day.  Clamav caught everyone.

I am not saying it is perfect but it does work.  It is not only a scanner but it only needs to check emails.  After all, your linux data cannot be infected (or not by any significant virus that would pose a danger) from any other source unless you wish to insert a floppy disk or USB drive and copy unknown data on to your machine that way.  Windows viruses cannot run on linux and therefore, even if you do download one, it is not able to do anything. This may change in the future but, for the time being lets enjoy our freedom from such things.  Clamav will do the job.

A windows virus that appears on your linux drive while you have windows mounted _is not_ a threat.  Just don't put it on your windows drive _and then start windows_, otherwise it might be!

---

### Post by dcstar on 2005-12-26
[QUOTE=anil_robo]
......
my question is: Is there any way I can schedule virus scans of my hard disk on a regular basis, if not in realtime? I'm asking this just to make my windows partitions secure (which I have mounted in Ubuntu).[/QUOTE]
You can set up a cron job to do virtually anything in Linux on a schedule - do "man cron" or "man crontab" for more info.

Once you get the hang of it, it's pretty easy to get things going.

As far as your Virus concerns go, I have ClamAV integrated with Evolution so it scans all my incoming e-mails and shows me the infected ones.

These won't affect my Linux system, but at least I know how much infected Spam is arriving each day (too much.........)!

---

