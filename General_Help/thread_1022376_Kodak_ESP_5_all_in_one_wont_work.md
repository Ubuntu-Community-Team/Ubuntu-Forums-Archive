---
title: "Kodak ESP 5 all in one wont work"
date: 2008-12-26
forum: General Help
---

### Post by oisuxx on 2008-12-26
i got this printer/scanner/copier for my girlfriend for christmas. the problem is i cant get it to work correctly in ubuntu 8.10. is there a way to get this to work? or is there a alternative that i can get that will work out of the box from best buy? thats where i bought this one, and id need to get store credit since the thing is open.

any help is appreciated :)

thanks in advance!

---

### Post by oilchangeguy on 2008-12-26
a quick check of [www.openprinting.org](www.openprinting.org) shows your printer is not listed. linux has a habit of only working with a few printers. my lexmark is a boat anchor as far as linux.

---

### Post by oisuxx on 2008-12-26
man that sucks! thanks for the link. guess next time ill just have to do some research, or just do a dual boot :(

now 3 things keep making me go back to windows! her webcam, this new printer, and my pic microprocessor programmer!

---

### Post by wolfen69 on 2008-12-26
in the future, keep in mind that HP printers are best for linux. they autoconfigure when you plug them in. can you return the kodak printer? and yes, always do some research before buying hardware for linux.

---

### Post by fragos on 2008-12-27
I was wondering about that printer. Kodak's ink technology is very interesting -- less expensive cartridges and the colors don't fade.

---

### Post by oisuxx on 2008-12-28
yea thats why i got it initially for her. i eneded up taking it back, and getting an hp photosmart C6280. that ink is insane, its like 6 cartridges at 10 bux a pop to replace. it works perfect though, so it was a trade off i guess, ease of use vs. cheaper ink.

---

### Post by fragos on 2008-12-28
Make sure you have "HPLIP Toolbox" installed. It will show you the ink levels in each cartridge.

---

### Post by printerinkperson on 2009-07-31
Stinkyink now offer   ink cartridges for the   [Kodak   ESP5 ink]("http://www.stinkyinkshop.co.uk/acatalog/Kodak-ESP5-ink.html?utm_source=forums&utm_medium=forums&utm_campaign=forums"). Oh and it's free delivery too!

---

### Post by SteveGreene57 on 2010-11-19
[B]Hello,
I'm new to Ubuntu.
I'm out off work now for being disable.
 So now I have a lot of time on my hands till it is time to check out.
I see where no one has update on this. 
I have a Kodak all in one 
model ESP 5250 and running the latest ver of Ubuntu.
 I ran this driver and it works great on this printer
.
Just putting in a update in case someone else is trying to do this
Thanks 
Until:popcorn::D
[/B]

---

### Post by repager on 2010-12-10
That's good news but what driver did you use?

---

### Post by tredegar on 2010-12-10
> **repager said:**
> That's good news but what driver did you use?
My guess is he used [this one]("http://sourceforge.net/projects/cupsdriverkodak/reviews/")

---

### Post by mr911189 on 2011-04-07
yes it works fine search for the kodak driver on **sourceforge** someone made one :D it works well on several kodak printers

---

### Post by fragos on 2011-04-07
> **mr911189 said:**
> yes it works fine search for the kodak driver on **sourceforge** someone made one :D it works well on several kodak printers

 Dose it just print or does scanning also work with that driver?

---

### Post by Pandyman on 2011-07-28
The driver seems to be the wrong architecture (i386) for my computer.
Mine is X86-64 GNU/LINUX
I sure am getting tired of buying ink for my Epson Printer.
Help

---

### Post by tredegar on 2011-07-29
> The driver seems to be the wrong architecture (i386) for my computer.

Why do you say that?
There are reports of it working perfectly on 64-bit systems.

---

### Post by Pandyman on 2011-07-29
When I try to download from sourceforge I get the message it is the wrong
architecture for my computer.  Although it works on some 64 bit systems it does not on mine as mine is not i386.

---

### Post by tredegar on 2011-07-30
Then my guess is that you are downloading the *.i386.deb file.
This is the wrong file for you.
You need the source code in the *.tar.gz file. 
Download that file, uncompress it and read the INSTALL and README files.
Then compile the code.

---

### Post by Pandyman on 2011-07-30
Thanks tredegar, I'll let you know if I succeed and then get a Kodak printer.

---

### Post by paulnewall on 2011-10-31
This driver is now included in ubuntu 11.10

---

### Post by paulnewall on 2012-01-14
Also there is a 64 bit deb file here
[http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)
 
And a scanner driver here
[http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/]("http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/")

---

