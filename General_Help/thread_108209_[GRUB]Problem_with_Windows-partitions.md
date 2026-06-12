---
title: "[GRUB]Problem with Windows-partitions"
date: 2005-12-25
forum: General Help
---

### Post by RaptorRaider on 2005-12-25
According to GParted, my configuration looks like this:

/dev/sda:
/dev/sda1: 23GB, Ubuntu 5.10
/dev/sda2: 2GB, Swap
/dev/sda4: Eh...? (Extended)
__/dev/sda5: Vista build 5270
/dev/sda3: new XP

/dev/sdb:
/dev/sdb1: old XP

After installing GRUB, only Ubuntu appeared in the menu.
It took me many hours to succesfully add the old XP:

title            Microsoft Windows XP Professional
root             (hd1,0)
map              (hd0) (hd1)
map              (hd1) (hd0)
makeactive
chainloader      +1


When I add the other two, I get errors:


"A disk read error occurred":

title            Microsoft Windows XP Professional
root             (hd0,2)
map              (hd2) (hd0)
map              (hd0) (hd2)
makeactive
chainloader      +1


"Invalid device request":

title            Microsoft Windows Vista
root             (hd0,4)
map              (hd4) (hd0)
map              (hd0) (hd4)
makeactive
chainloader      +1


rootnoverify doesn't help.


What am I doing wrong?

---

### Post by RaptorRaider on 2005-12-25
Just read the GRUB manual, and like I suspected it is the "map"-parameter which is causing problems.
"map (hd2) (hd0)", "map (hd0) (hd2)" and "map (hd4) (hd0)", "map (hd0) (hd4)" won't work because I need to map partitions, not drives.

How do I do this?

---

### Post by rcerreto on 2005-12-25
If I remember well, the ill behaved windows not only wants to be installed on the first HD (that's why you need performing the map trick) but it wants to be able to acces its first partition as well.

My suggestion is that you use grub to start just one windows installation, the one on the second disk. Keeping two entries in menu.lst: one for ubuntu and the other one for windows.

Then try using the windows bootloader to start the other two installations.
You'll have to edit C:\boot.ini

---

### Post by RaptorRaider on 2005-12-25
I was afraid of that.

I have never edited boot.ini before - what is supposed to be in there?
Can you make that up from the information in the first post?

---

### Post by Ocxic on 2005-12-25
i don't think you'll be able to mod the boot.ini to boot linux, and should just leave it alone. 
try:
"A disk read error occurred"
title Microsoft Windows XP Professional
root (hd0,2)
map (hd0,2) (hd0,0)
map (hd0,0) (hd2,0)
makeactive
chainloader +1


"Invalid device request"
title Microsoft Windows Vista
root (hd0,4)
map (hd0,4) (hd0,0)
map (hd0,0) (hd0,4)
makeactive
chainloader +1

---

### Post by RaptorRaider on 2005-12-25
[QUOTE=Ocxic]i don't think you'll be able to mod the boot.ini to boot linux, and should just leave it alone. 
try:
"A disk read error occurred"
title Microsoft Windows XP Professional
root (hd0,2)
map (hd0,2) (hd0,0)
map (hd0,0) (hd2,0)
makeactive
chainloader +1


"Invalid device request"
title Microsoft Windows Vista
root (hd0,4)
map (hd0,4) (hd0,0)
map (hd0,0) (hd0,4)
makeactive
chainloader +1[/QUOTE]
Thank you for your suggestion, but might I advise you to read a thread carefully before responding? :p 
The "map"-parameter can only map drives, not partitions.

Also we are not trying to get boot.ini to boot Linux, which is very possible BTW, but we are trying to get boot.ini to boot Windows, which should be fairly easy for those who are experienced in doing so.


I just tried:
> [boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(1)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(1)rdisk(0)partition(5)\WINDOWS="Microsoft WIndows Vista" /fastdetect
and
> [boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(1)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(1)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft WIndows Vista" /fastdetect
Both are not working.

---

### Post by RaptorRaider on 2005-12-26
Is there nobody around who knows how to correctly edit boot.ini's? :( 


Should nobody "know" (read: respond), the best option would be to use the XP Setup to launch Recovery Console and let that do the job, right?

---

### Post by rcerreto on 2005-12-26
[QUOTE=RaptorRaider] we are trying to get boot.ini to boot Windows, which should be fairly easy for those who are experienced in doing so.[/QUOTE]
Exactly! Unfortunately I'm not one of them :) 

Too bad I can't understand the exact meaning of multi,disk,rdisk,partition.

What beats me is that at least your first entry:
[I][operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect[/I]
should work.

For the following entries it's a matter of guessing the parameters but not for the first.
BTW: why not trying multi(0)disk(1)rdisk(**1**)partition(3)  ?
          one more silly attempt shouldn't hurt

---

### Post by RaptorRaider on 2005-12-26
> Too bad I can't understand the exact meaning of multi,disk,rdisk,partition.
You can see the exact meaning of those [here]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prmc_str_masc.asp").

My thought is that either every SATA HDD has it's own controller, so multi() should be 1, or every SATA HDD is on the same controller, so disk() should be 1.
rdisk() **seems** irrelevant.

Edit:
Oops.
If I'm understanding it correctly, disk() is the irrelevant one and rdisk() should be 1 if every SATA HDD is on the same controller.

---

### Post by RaptorRaider on 2005-12-26
Success!

Well, at least partially.

> multi(0)disk(0)rdisk(1)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
Is booting my second XP partition just fine.
> multi(0)disk(0)rdisk(1)partition(5)\WINDOWS="Microsoft WIndows Vista" /fastdetect
Didn't work, but when replaced with:
> multi(0)disk(0)rdisk(1)partition(4)\WINDOWS="Microsoft WIndows Vista" /fastdetect
It says it cannot find \system32\hal.dll.

hal.dll is Windows' "Hardware Abstraction Layer"; does anyone think it would be safe to copypaste it from a Windows XP partition?
Or is this not the right forum to ask that? :p

---

### Post by ShirishAg75 on 2005-12-26
I had the same issues & ended up re-installing XP & hence grub is gone. I'm going to start a thread asking how to get grub-reinstalled as there isn't a good one for Ubuntu & this should've been for the wiki. 

Although there is a way to copy & paste hal.dll but many a times that doesn't work. The only way is if u had a win'98 install also then u could access the partition & backup stuff.

---

