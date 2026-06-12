---
title: "Trouble installing ubunto 10.10. help please!"
date: 2011-02-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rouse5369 on 2011-02-19
I am trying to install Ubunto 10.10. i downloaded ubuntu from the ubunto website. wrote the image to a disk. i tried rebooting with the disk and it goes so far and say it has encountered problems and will start the desk top so we can see and fix errors. and then it justs freezes.
 
ive tried deleting partitions, adiing partitions. its a 60 g hdd. i allowed 65 percent for C: and 35percent for extended partition for D:
 
I tried agaian to install ubunto as sole operating system and same results as above.
 
I have a Dell C840, pentium4 2ghz mobile processor.
512m ram but bios only reckognizes 256. ram are of different speed.
new 1 g ram coming. 512 matched set. pc2700 333mhz 512mb sodimm 
nvidya graphics Geforce 4 44o go
60 g HDD
DVD /CDRW drive
i was running windows xp professional
but had slowed to a crawl after all windows updates were installed driving me nuts, now im pulling my hair out trying to install ubunto.
 
Any help is appreciated.
 
I am a Newbie and hopefully a Linux lifer. be gentle!! lol
 
Gerald Rouse

---

### Post by metalf8801 on 2011-02-19
How did you fallow the steps to burn the iso to a CD on the Ubuntu download page?


Did you check the MD5SUM 
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

Check the CD integrity
[http://ubuntuforums.org/showthread.php?t=1471727](http://ubuntuforums.org/showthread.php?t=1471727)

Just a few things to try first 
Please repost if you already did this or if it doesn't help

---

### Post by Rouse5369 on 2011-02-19
im trying to understane the m5 hash, but its gonna take a min. i burnt the image to a dvd rw. does that matter?

---

### Post by Rouse5369 on 2011-02-19
i dont know if this Linux is gonna wwork for me, im no computer guru and from what i read i thought this was gonna be as easy as installing windows and its definately not

---

### Post by Rouse5369 on 2011-02-19
what does it mean by open a terminal?? does this mean open dos command in windows?

---

### Post by Rouse5369 on 2011-02-19
it says md5sum is not a command on my computer

---

### Post by metalf8801 on 2011-02-19
> **Rouse5369 said:**
> what does it mean by open a terminal?? does this mean open dos command in windows?

I think your reading how to check the MD5sum on Linux 

what you need to do is to down load Windmd5sum 
[http://download.cnet.com/WinMd5Sum-Portable/3000-2381_4-75099291.html?tag=mncol;6](http://download.cnet.com/WinMd5Sum-Portable/3000-2381_4-75099291.html?tag=mncol;6)
That should just run without needing to be installed 

start with that and I'll brb

Sorry wrong download 

ok here are the steps for checking the MD5Sum
1. download and install Windm5sum from [http://download.cnet.com/WinMD5Sum/3000-2381_4-10115915.html?tag=mncol;1](http://download.cnet.com/WinMD5Sum/3000-2381_4-10115915.html?tag=mncol;1)

2. Find the Ubuntu iso you downloaded and Right-click on it then click Send To, then winMD5Sum. 

3. Wait for winMD5Sum to load and finish the checksum (this may take a significant amount of time depending on your computer's performance).

4. Copy the md5 hash from [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) that makes with the version of Ubuntu you downloaded. Its most likely going to be ubuntu-10.10-desktop-i386.iso which has a md5 hash of 59d15a16ce90c8ee97fa7c211b7673a8 and past it into the bottom text box in WindMD5sum 

5. Click "Compare"

---

### Post by Rouse5369 on 2011-02-19
using wind5sum it says sums are the same

---

### Post by metalf8801 on 2011-02-19
> **Rouse5369 said:**
> using wind5sum it says sums are the same

Ok good 
Can you tell me how you burned the Ubuntu iso to the DVD-rw? That way I will know if you did it the right way or not

---

### Post by Rouse5369 on 2011-02-19
als now have booted the laptop to ubunto and pressed enter key, i selected check disk and it came back with no errors

---

### Post by Rouse5369 on 2011-02-19
i downloaded the image file to my desktop, i downloaded ifra recorder. i then wrote image to disk with that software

---

### Post by Rouse5369 on 2011-02-19
Thank you for your help so far, really do apprecite it. do you have an instant messenger we could use??

---

### Post by metalf8801 on 2011-02-19
> **Rouse5369 said:**
> Thank you for your help so far, really do apprecite it. do you have an instant messenger we could use??

yeah I was thinking the same thing are you on IRC? If so what's your screen name. If not send me a private message with your screen name for ether AIM or Yahoo IM 
[http://ubuntuforums.org/member.php?u=400120](http://ubuntuforums.org/member.php?u=400120)

---

