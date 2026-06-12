---
title: "Someone help out a noob please"
date: 2005-10-15
forum: Desktop Environments
---

### Post by tegllc on 2005-10-15
I'm new to Linux and ubuntu.  I've downloaded and burned the image to a cd.  When I reboot, my laptop does not automatically recognize the boot cd.  So I tried going in and changing the BIOS settings to look for a boot cd first.  Then on reboot, I got what appeared to be a DOS command line.  I'm not exactly sure because I'm not all that familiar with DOS.  Whatever it was, it didn't look like the sreenshots showing an install of ubuntu.

I figure I am not burning the image to cd correctly or my system is not recognizing to boot from cd.  I've used NERO Burning ROM 6.3.1.10 with CD-Rs.

A few questions:  When I download the ubuntu package (zip file), do I have to do anything to it?  I assumed I should unzipped it into its own folder (so I did) and I dropped that folder into NERO to burn.  Should I have only burned certain files?  It didn't look like it.

Do I have to tell my computer to recognize the Boot CD instead of going into Windows?  The first few times I rebooted, expecting ubuntu to appear Windows came back, so I went in and changed the BIOS (or whatever it is called) to look for a Boot CD - then the next reboot I got DOS.

Can someone point me in the right direction?  I know I'm close, but this is frustrating and so far a big waste of time.  Although it may sound like I'm a complete idiot I'm not (really!). I just don't work with command lines and the internals at all.  So I'm a foreigner to all this and need some handholding.  I've googled for some answers and down some searches on here, and thought this is my next step - ask the gurus.

Any and all help is appreciated.  Thanks!

---

### Post by Lord Illidan on 2005-10-15
How did you download a zip file? It should be an iso file... Did you download from the official mirrors?

Once you get the iso file, don't burn it as data, and don't open it as winrar. Instead using Nero, burn it as an image file to a cd..(when I say image, I don't mean jpeg...)

---

### Post by Underhill on 2005-10-15
You should not "unzipped" the file. You should burn it directly. Fire up Nero, select "Burn Image" from the "File Menu", and choose the file. I can't give you the exact instructions because you didn't mention what version of Nero you're using but basically that's about it. Find "Burn Image" or "Burn ISO" or "create a CD from an image file" in Nero.

---

### Post by tegllc on 2005-10-15
When I downloaded from the ubuntu website I received a zip file.  
"ubuntu-5.10-live-i386
WinRAR archive
642.554 KB

---

### Post by Lord Illidan on 2005-10-15
No, not a zip file... in that case it is an iso file...probably you can't see the extension in XP...
Burn it as an image file, don't unzip it however in winrar...Use the inbuilt help in nero to search for "iso"

---

### Post by chaumurky on 2005-10-15
[quote=Lord Illidan]No, not a zip file... in that case it is an iso file...probably you can't see the extension in XP...
Burn it as an image file, don't unzip it however in winrar...Use the inbuilt help in nero to search for "iso"[/quote]

Don't you hate OS's second guessing what you want to do?! It doesn't show the extension either - double whammy... :(

---

### Post by xmastree on 2005-10-15
> Then on reboot, I got what appeared to be a DOS command lineLook at [**this**]("http://www.xmastree.34sp.com/ubuntu/burn") to see how to correctly burn your CD using Nero and Windows XP.

Hope this helps.

---

### Post by tegllc on 2005-10-15
Thanks for the help.  It looks like I did not burn it correctly.  Will attempt and follow-up when done.  Thanks again!

---

### Post by xmastree on 2005-10-15
If you have any CDRW available, use one. It's cheaper when you make a mistake...

---

### Post by Lord Illidan on 2005-10-15
Burn at a low speed too.. Preferably no faster than 8x... Better wait 10 mins and have a working distro then not wait then get a bad one because you were too impatient..

---

### Post by tegllc on 2005-10-15
Thanks for the tip on burning at a slow speed - will do.

I cannot get my system to recognize the bootable cd.  I have the image on a cd, just as that link that was shared showed me how to do (thanks!).  I hit F2 on reboot to enter bios/set-up (or whatever it is called) and go to drives.  I put CD/DVD drive 1st and hardrive second and still it boots to wondows.  

Any ideas on what I'm doing wrong now???:confused:

---

### Post by xmastree on 2005-10-15
What do you see if you look at the disc using explorer?

---

### Post by tegllc on 2005-10-15
folders:
.dsk 
bin
casper
disctree
dists
doc
install
isolinux
pics
pool
preseed
programs

files:
autorun
md5sum
README.
start (pic)
start
start
ubuntu

---

### Post by xmastree on 2005-10-15
Well that seems to be correct. Do you have any other bootable CDs, like a Windows installer you could try? Just to see if your computer will boot from the CD.

---

### Post by tegllc on 2005-10-15
unfortunately, I have no other bootable cds.

Was I doing the right thing by hitting F2 and changing the order?  I figured it was the only thing I could do...

---

### Post by xmastree on 2005-10-15
[QUOTE=tegllc]Was I doing the right thing by hitting F2 and changing the order? [/QUOTE]Absolutely.

What do you see when it's booting? With mine, from memory, if there's a CD in the drive which isn't bootable there's a message along the lines of:
searching for boot record..... not found...
Then it proceeds to boot from the hard drive.

Does yours give any indication that it's **trying** to boot from the CD?

---

### Post by tegllc on 2005-10-15
My system seems to give no indication of ANY attempt to boot from cd.

---

### Post by xmastree on 2005-10-15
Strange... It should at least try and fail, if it sees the disc in there.

I'm no expert on laptops, so I may be out of my depth a little here...

Are you sure you saved the BIOS settings?
Do you have a different computer in which you could try the disc? All you have to do is confirm it will boot, so there's no risk of damaging the other computer's OS. Just turn it off once you see it's booted from the CD and no harm will be done.

I just looked again at your first post. You got a command line... that seems to suggest it is booting from the CD. Try that one again to confirm is is booting from it. If it is, then I can't think why your new one won't boot, unless it's faulty... :-(

---

### Post by Jalinux on 2005-10-15
It sounds as if you are still not burning the ISO image currectly.  If you visit the official site (and it sounds as if you have), you will recieve the OS as an ISO.  If Nero is giving you problems, visit [http://www.download.com/DeepBurner/3000-2646_4-10402901.html?tag=lst-0-1](http://www.download.com/DeepBurner/3000-2646_4-10402901.html?tag=lst-0-1) .
I believe it should do the trick.   It's pretty self explanatory with its use.

---

### Post by tegllc on 2005-10-17
UPDATE:  I took the CD to another compuetr and it booted up ubuntu no problem.  I got it up and running with minimal problems.  So it must be a problem with my laptop.  Thank you all for helping.

I'm looking forward to exploring ubuntu and Linux, as this is all new to me.  I won't be able to use linux for work, but for the home computer that we us to just surf the net and do email - it should be a good fix. Thanks again for the help!

---

