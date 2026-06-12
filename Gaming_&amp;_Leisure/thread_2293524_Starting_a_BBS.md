---
title: "Starting a BBS"
date: 2015-09-05
forum: Gaming &amp; Leisure
---

### Post by GettingNowhere on 2015-09-05
Hi all.

I have posted this here, as in the olden days, this is where the experts on 56K modems would hide.

I have a pal miles away who has an old mac with no means of getting his data off it save for a little RJ11 socket at the back.
So I thought, lets make a BBS and it can phone me up and upload all the files. And it would remind me of the old days.  Bargain!

I loaded Dosbox, Renegade BBS and Fossil, and got the thing up and running on localhost with no great problems.  The problem is when I try to get the modem to answer the phone line.  It doesn't.

For those who might still remember Renegade, it's a config problem, but I don't know where any of the configs are except n1.conf (attached).
I'm using [https://ssl.instructables.com/id/Renegade-BBS-in-Ubuntu-Linux-Telnet-Multi-Node/#step1](https://ssl.instructables.com/id/Renegade-BBS-in-Ubuntu-Linux-Telnet-Multi-Node/#step1) to set it up.

I have a USR 56K Message Modem on ttyS0.  It responds OK to ATZ but not to  ATA.  It just says error.  I do have an apparently good string to put in (AT&F1&K0&I0S33=32S15=128S27=64), but I can't manually put it into Renegade as it's too long.
I tried Renegade with BNU: same thing.  

Are the  configs set to the "Windows Com1" port or ttyS0?  I also tried with S0=1 in the  modem init string but it still doesn't answer.
Any help would be appreciated.

Cheers!

Ubuntu Trusty Tahr on an HP desktop.

---

### Post by TheFu on 2015-09-06
If I recall correctly ... it has been 17 yrs since I used any dialup modems ... the com port needs to be set to 8N1 first and 38800bps ... is a common serial port speed.  I bet there is a usenet FAQ about this stuff somewhere.

But ... an alternative:

If you have broadband, setup an sftp server for him to access over a dial-up ISP. Juno used to be free.  Or he could put the files on a $69 tablet and sftp them when connected from the local McDs or library.

Don't forget how slow 56Kb is ... **any** wifi access he can find for 5 minutes will save an hour on a 56kb modem.  Plus, it is doubtful you and he would connect at 56K - 36.6K is much more likely.

---

### Post by coldraven on 2015-09-07
Jeepers! I used to install modems on MSDOS and Xenix systems when a 4800 baud cost $600 and now I cannot remember how I did it :(
The only solution that I can think of would entail a visit to your friend. Extract the files then give him a second hand laptop running Ubuntu and bin the Mac!

I just bought a HP Compaq 6715b* for about $80. It has an internal Winmodem and had Vista installed. I would use Vista to get the modem working, connect to the Mac using a crossover cable** and get the files. Then nuke Vista with Ubuntu and plug in an external $10 USB  modem because I don't think that Linux supports the Winmodem in this model.

*2GHz AMD Dual core, 2GB, 1280x800 lovely matte screen
**or use a $2 dual RJ11 socket to connect the two modem cables (I'm not entirely sure that this would work)

Good luck with this project, I'll pop back to see how it went.

---

### Post by GettingNowhere on 2015-09-07
Thanks for the replies.

I have to admit it was 2am when I stopped trying to get it to work.
Turns out all I had to do was switch everything off and go to sleep.
On reboot, it works.
I dialled in with my mobile phone, although it didn't pick up itself, I pressed A and it answered with the old tones we used to love.
I will get back to you if my mate can connect.

The Mac only has two outputs: SCSI and RJ11. Years ago I used to have a SCSI CD writer. Not now..  Pity.
I'm looking up Freola to see if that will help him, failing that I'll get him to phone my BBS.

I'll keep you posted.

---

### Post by efflandt on 2015-09-07
A 56K modem is 53K max due to some regulation about power limits or something on phone lines. But that is only if connected to an ISP or other modem digitally connected to the phone company. Analog to analog modem, the maximum speed is 33.6K.

If you go the phone route, wouldn't ppp be somewhat easier (once you recall how to set that up)? How many people remember how to use xmodem or zmodem to transfer files over a terminal, especially if it involves multiple directories. With a ppp dial up connection they could use ftp or sftp (or scp) depending upon what is available on your computer.

At one time my dad brought home a CP/M computer from work with 8 inch floppies and wanted to copy some Wordstar files from it. It was close enough to MS DOS that I got it up and running (but floppies had to be manually mounted) and got it communicating over null modem serial cable between terminal programs on each. But I had no clue how to transfer files over serial from the CP/M computer.

Before the Internet as we know it, I used BBS's or text based CompuServe to download programs and Windows updates. At that time CompuServe was $6/hr for 300 baud or $12/hr for 1200 baud, so I only used 1200 baud when downloading files. 300 baud was just about slow enough to read before it scrolled up off of the screen.

---

