---
title: "Printer drivers for Lexmark Pinnacle Pro901 printer"
date: 2010-09-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by edhawk2 on 2010-09-30
I'm looking for printer drivers for a Lexmark Printer: Pinnacle Pro 901.  I'm using Ubuntu 8.04 on an old Dell laptop.

---

### Post by commonplace on 2010-10-06
They're available from Lexmark's US web site ([www.lexmark.com](www.lexmark.com)). Just go to Downloads, search for pro901, and grab the Linux drivers (as of this posting, the latest ones for Ubuntu are the Debian-based ones at the very bottom, version 1.5).

They're 32-bit only, though, so if you're running 64-bit, you might be out of luck. I'm actually running 64-bit Ubuntu and came across this thread trying to find a workaround. :)  But if you're on 32-bit, which it sounds like you probably are, you should be good to go.

/Kevin

---

### Post by Pifilatakanemu on 2010-10-27
Did you get it to work?

And what about the other functions of the "printer"?

I'm considering to buy me one for 100&#8364;.. seems to be a good prize if printing costs are around 1cent/ b&w-sheet.

edit:

I saw 

[Firmware update for Pro800-Pro900 Series printers 32 & 64 bit.]("http://support.lexmark.com/index?page=content&productCode=LEXMARK_PINNACLE_PRO901&actp=PRODUCT&id=DR20668&segment=DOWNLOAD&userlocale=DE_DE&locale=de")

at the German download page...

---

### Post by commonplace on 2010-10-27
> **Pifilatakanemu said:**
> Did you get it to work?

And what about the other functions of the "printer"?

I'm considering to buy me one for 100€.. seems to be a good prize if printing costs are around 1cent/ b&w-sheet.

edit:

I saw 

[Firmware update for Pro800-Pro900 Series printers 32 & 64 bit.]("http://support.lexmark.com/index?page=content&productCode=LEXMARK_PINNACLE_PRO901&actp=PRODUCT&id=DR20668&segment=DOWNLOAD&userlocale=DE_DE&locale=de")

at the German download page...


I was able to use the 32-bit drivers under 64-bit Ubuntu 10.10 and it worked fine. The process was a bit convoluted but it worked in the end.

(That link you gave for the 32-bit and 64-bit stuff is just the printer's firmware, which has nothing to do with the drivers or making the printer work on the computer. But yes, they do offer that in 64-bit, which is nice -- I used those first to update the firmware and that worked great. The drivers were definitely more difficult.)

I have ONLY tried it as a printer, which works perfectly. I haven't tried to scan from my laptop or use any of its other features or functions. I will try to do that and get back to you. :)

/Kevin

---

### Post by Pifilatakanemu on 2010-10-27
Hey Kevin,

that would be really great!

I scanned through some reviews and saw that the device offers some autonomous features but scanning from the laptop should be possible with Ubuntu...

I'll have to buy it as a commercial client so I would not have the possibility to return it. So your feedback is kindly expected! 

;)

---

### Post by commonplace on 2010-10-28
> **Pifilatakanemu said:**
> Hey Kevin,

that would be really great!

I scanned through some reviews and saw that the device offers some autonomous features but scanning from the laptop should be possible with Ubuntu...

I'll have to buy it as a commercial client so I would not have the possibility to return it. So your feedback is kindly expected! 

;)

Okay, my initial findings are not positive. So far, I'm unable to get scanning to work. As best I can tell, Lexmark only supports the Pro901 under Linux as a *printer* -- the rest of the features aren't supported under Linux.

I found and installed Lexmark's Network Scan Drivers, but they're designed for other network scanning devices, and as such, it doesn't appear to work with the Pro901.

I contacted Lexmark's technical support using their online support... and naturally, the online support only deals with Mac and Windows. For Linux, you have to call a separate number and ask for the "Linux department, they are the ones who handle Linux."

The number is 1-800-834-7814. I don't have time to call tonight, but maybe this coming weekend. (If you want to call, go for it, and be sure post your findings!)

I'll try to remember to post back here after I call 'em. :)  Don't be afraid to bump this thread if you haven't heard back from me by next week, though. hehe

/Kevin

---

### Post by darkmail752 on 2010-11-16
> **commonplace said:**
> I was able to use the 32-bit drivers under 64-bit Ubuntu 10.10 and it worked fine. The process was a bit convoluted but it worked in the end.

(That link you gave for the 32-bit and 64-bit stuff is just the printer's firmware, which has nothing to do with the drivers or making the printer work on the computer. But yes, they do offer that in 64-bit, which is nice -- I used those first to update the firmware and that worked great. The drivers were definitely more difficult.)

I have ONLY tried it as a printer, which works perfectly. I haven't tried to scan from my laptop or use any of its other features or functions. I will try to do that and get back to you. :)

/Kevin

Hello Kevin,

How did you get the drivers to work? I am also using Ubuntu 10.10 under 64-bit, and downloaded two different possible drivers for the pro901 from Lexmark. I have been unable to get them to work, they both keep saying...

"dpkg: error processing lexmark-legacy-wsu-1.0-1.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:"

Thx Joe

---

### Post by commonplace on 2010-11-17
> **darkmail752 said:**
> Hello Kevin,

How did you get the drivers to work? I am also using Ubuntu 10.10 under 64-bit, and downloaded two different possible drivers for the pro901 from Lexmark. I have been unable to get them to work, they both keep saying...

"dpkg: error processing lexmark-legacy-wsu-1.0-1.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:"

Thx Joe

I ended up using a different file. I uploaded it to Ubuntu One just now. I *think* this is all you need. :)  I knew I should have documented it at the time!

Anyway, download [the file]("http://ubuntuone.com/p/PmC/") to its own folder, open up a terminal, and run:

```
sudo dpkg --force-architecture -iG *.deb
```

Then restart CUPS:

```
sudo restart cups
```

Then I think you just add the printer normally. (Sorry, I forget what I had to do exactly.) I think when you go to Printing and click Add, just wait a minute and on the left you'll see a new printer type (Lexmark Backend or something similar) and then you choose that and go from there, which hopefully is self-explanatory.

If you get stuck, post back and let me know and maybe I'll remember. Just know that it can definitely be done, so you're not wasting your time. :)  Still no go on network scanning, though, and I don't think it's going to work for the foreseeable future, which stinks. But I'm happy with the printing.

/Kevin

---

### Post by zylx on 2010-11-18
Lexmark published new drivers for linux, which also include 64 bit version. Works perfect for me. Still no support for direct scanning to pc, but it isn't very annoying with scanning to pendrive or via email directly from printer touchscreen.

---

### Post by commonplace on 2010-11-20
> **zylx said:**
> Lexmark published new drivers for linux, which also include 64 bit version. Works perfect for me. Still no support for direct scanning to pc, but it isn't very annoying with scanning to pendrive or via email directly from printer touchscreen.

Thanks! I didn't know they'd put out new drivers. (Once I got it working, I didn't check back.) I'll stick with what I have, but it's good to know that the next time I reinstall or setup a new machine, I can use "real" drivers. :)

/Kevin

---

### Post by ntdoherty on 2012-07-11
I know this thread is pretty old, but I thought I'd post here instead of creating a new one.

I'm running Ubuntu 12.04 LTS 32bit

I'm trying to set up a Lexmark Pinnacle Pro901 printer. 

There used to be drivers for Ubuntu and many other Linux systems on the Lexmark website, but now the Linux/Unix operating system menu only offers Fedora 10 and OpenSUSE as options for driver downloads.

Does anyone know what happened here? Or know how I can get ahold of the drivers for Ubuntu that used to be available? 

I'm running with drivers for a slightly different printer, but they don't allow me to really set up my print completely. I can print and scan to e-mail, etc., but I cannot scan directly to the computer.

So, my question is, where did the Ubuntu drivers go?


Thanks,
Nate

---

### Post by thexcguy on 2012-08-06
It looks like you can find Lexmark's drivers for various versions of Ubuntu [here]("http://support.lexmark.com/index?locale=EN&page=product&userlocale=EN_US&productCode=LEXMARK_PINNACLE_PRO901&focusedTab=DOWNLOADS#2"). I haven't tested these yet with my 64-bit install of 12.04, but fingers crossed that it'll work out.

---

### Post by ntdoherty on 2012-08-06
Thanks muchly. I'll check those out. The one I've got now is functional, but not totally.

NtD

---

### Post by thexcguy on 2012-08-29
I was able to use the driver for Ubuntu 11.10 x64 with JRE on my 64-bit install of 12.04. Printer is connected via ethernet. Have not tested scanning.

---

