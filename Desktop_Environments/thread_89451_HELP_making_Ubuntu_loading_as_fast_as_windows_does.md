---
title: "HELP making Ubuntu loading as fast as windows does!"
date: 2005-11-12
forum: Desktop Environments
---

### Post by rado_london on 2005-11-12
Hi 
I just tested the loading time for Ubuntu 5.10 and Windows XP Home.I have HP Pavilion dv4145ea.
Here are the results:
```
GRUB-GNOME= 1 minute 26 seconds
GNOME-shutdown= 24 seconds
GRUB-WinXP= 47 seconds
WinXP-shutdown= 15 seconds
```
I would like you to help me making my Ubuntu loading at least as fast as Windows.
Thanks in advance

---

### Post by Zotova on 2005-11-12
You maybe be able to decrease the loading time slightly if you remove certain items from the startup (for example the time sync) but you will never get the speed as fast as xp. 

Mainly because of the way Linux works - I'm no expert but from what I gather Linux loads everything first and gives you a working environment when everything is loaded - where as xp loads a few things but then makes you wait once you are in the desktop whilst it loads the remaining things in the background. If you will xp cheats a bit.

---

### Post by canadianwriterman on 2005-11-12
Zotova is right. XP loads many systems processes, including all the anti-virus and anti-spyware programs, in the background after the desktop appears.

You may notice that, is you try to open a program in XP immediately after the desktop appears, it may take a long time to open, which the system is still busy loading processes.

In Linux, on the other hand, almost everything is loaded when the desktop appears and you can start using it right away.

---

### Post by rado_london on 2005-11-12
Thanks for the info. Im wondering which is the safe way of disabling these scrits,and also which of them I don't need(all of them have strange names):) :) :)

---

### Post by Zotova on 2005-11-12
If you do not want ubuntu to check and update the time when loading then this is how to do it easily:

sudo update-rc.d -f ntpdate remove

That for me made the loading process a lot quicker as I didn't have to wait for my router to connect to the internet and then get the time - it could connect to the net in the background.

---

### Post by rado_london on 2005-11-12
Cheers
What about other scripts.are there other completely useles scripts.I saw som HP Printing System script etc.

---

### Post by Elitist_Phoenix on 2005-11-12
"sudo update-rc.d -f ntpdate remove"

Tiny bit OT but I've been disabling services by
cd /etc/init.d/
chmod -x ntpdate


Is that okay?

---

### Post by Zotova on 2005-11-12
Well, unless you have a hp printer I'd presume that was safe to disable – try disabling it and see if everything still works on your printer – if it does you probably don't need it.

---

### Post by Zotova on 2005-11-12
[QUOTE=Elitist_Phoenix]"sudo update-rc.d -f ntpdate remove"

Tiny bit OT but I've been disabling services by
cd /etc/init.d/
chmod -x ntpdate


Is that okay?[/QUOTE]

The code I used on my system I got from a how-to someone wrote. I was under the impression that chmod -x ntpdate only disabled temporarily. Although I could be wrong.

---

### Post by rado_london on 2005-11-12
I dont even use printer.And still loads cups and HP printing and imaging system.How do disablee them(I mean the command).Also is LVM nessesary on laptops.
Cheers

---

### Post by Zotova on 2005-11-12
If you do not need a printer maybe uninstall the hp software and cups via synaptics?

---

### Post by rado_london on 2005-11-12
This is strange.Using Synaptic I removed ntpupdate,cups and HP printing and imaginig system.
Now ubuntu is loading for 1 minute 46 seconds.
Before uninstalling them it was 1 minute 26 seconds.
Any ideas?

EDIT: It was hanging on setting up network settings for no reason.

---

### Post by Zotova on 2005-11-12
Are you using wireless?

I had a problem where I had wireless turned on but I had also left my network card enabled so my network card was also trying to get an ip address thus slowing down the loading process. Disabling it fixed that.

Was the time you counted the first restart after you uninstalled the stuff? Maybe the second boot would be more accurate once everything is removed (just a stab in the dark there).

---

### Post by rado_london on 2005-11-12
After the second restart it didn't lack on the network configuring.Yes I use wireless. Now it loaded only for 1 minute 12 seconds.I need only 25 seconds off the boot time. What about the Enterprice Volume Manager and RAID drivers. What are they for? Are they important?
Cheers

---

### Post by Zotova on 2005-11-12
I have a feeling raid is to do with the hdd. The other I've never heard of so I'd wait for someone a tad more knowledgeable when it comes to Linux.

---

### Post by dcstar on 2005-11-12
Search for the "Removing IPv6" thread as well, that may help too.

---

### Post by allans on 2005-11-12
Check this out for a fast boot: [http://www.ubuntuforums.org/showthread.php?t=80423](http://www.ubuntuforums.org/showthread.php?t=80423)

It cut my boot up time down dramatically, but you loose the splash screen and laptop support is varied at best apparently.

Allan

---

### Post by spizkapa on 2005-11-12
You may want to look at this thread: [http://ubuntuforums.org/showthread.php?t=88806]("http://ubuntuforums.org/showthread.php?t=88806")

The init scripts are somewhat confusing but do:

man update-rc.d

and you'll be set, if you manage to read through it.

chmod-ing -x the scripts in /ect/init.d/ may work but it's a hack, not a solution. You really should just read the script and what it does and then disable it from loading with update-rc.d.

HTH.

---

