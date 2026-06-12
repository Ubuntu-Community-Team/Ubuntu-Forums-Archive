---
title: "Dellbuntu 6400 screen permanantly UberBright following LinuxMint installation"
date: 2007-12-24
forum: Dell  Ubuntu Support
---

### Post by dr johnson on 2007-12-24
I have a Dell/Ubuntu laptop computer, Inspiron 6400, bought in july of this year (it must have been one of the first Dellbuntus in the UK!).

Anyway I installed Linux Mint 4.0 last week and something very unwelcome happened. As the install process was drawing to a close, the screen went almost entirely white and I was unable to see anything except by looking down the screen at an angle of about ten degrees. Even then of course, things were only just comprehensible :-/

A few seconds later, the install process finished, and I rebooted the computer. I noticed that the very bright screen was still blazing away even when the computer was just starting to crank into life-I mean right from the very first moment that anything happened at the monitor. The computer was practically unusable, and I couldn't diagnose the problem.

After an hour or so's totally fruitless attempts at sorting the thing out, I made a fresh install of Ubuntu 7.10; the problem still was there, it never went away. Suddenly after about half an hour's trying to pinpoint (again) the problem, the monitor suddenly apparently corrected itself, such that it was infact rendering better than it had ever done before! (The screen always had a slightly dirty pink tint to it--that was now banished, and the screen was showing stuff lovely and clear).

So, I reinstalled Linux Mint (Uh Oh...) and all seemed well this time as the installation process was underway. As I hit the restart prompt, and as the computer booted down, the screen was fine. But immediately it started booting up, the problem reappeared. So I then reinstalled Ubuntu 7.10, thinking the problem would right itself again. No such luck! I've been squinting down the screen for hours now trying to cajole it into autoheal but it won't play.

A few other relevant points (sorry, this is long, I'm just trying to give you all the facts I have.)
1) I tried altering the Gamma settings, that didn't work.
2) If I try to change the screen brightness using the hot keys, or the BIOS settings, the screen does indeed dim ever so slightly, but still is ghastly and utterly unusable.
3) If I take a screenshot, and then view that screenshot image on another computer, the screenshot looks fine, no sign of any excess brightness.
4) If I ask Totem to open up a video file, Totem opens up a window JUST before the video file has actually loaded and during this period--just for a small fraction of a second--the portion of the desktop that you can see "through" that window shows up exactly correctly.

Edited to add xorg.conf file:
[http://www.jonathanriley.net/xorg.conf.txt](http://www.jonathanriley.net/xorg.conf.txt)
I just posted this at the LM forum too; if somebody at one forum can help, I will post the answer to the other forum. It's good to spread knowledge around I guess.
[http://linuxmint.com/forum/viewtopic.php?f=59&t=7962&p=49424#p49424](http://linuxmint.com/forum/viewtopic.php?f=59&t=7962&p=49424#p49424)

---

### Post by roseysdaddy on 2007-12-24
that sounds like an issue with the monitor itself, not in the way it's being initialized.  you've checked the connection in the back to be tight?

---

### Post by dr johnson on 2007-12-24
roseysdaddy,
Thanks for the swift reply. The computer is a laptop though, so I guess the connection can't be the problem.

---

### Post by dr johnson on 2007-12-24
...

---

### Post by dr johnson on 2007-12-24
Pix! Two photos of the offending Dell laptop next to my iBook.
First pic, they are both running from battery power:
[IMG]http://www.jonathanriley.net/IMAG0001.JPG[/IMG]


...and second, they are both powered from the mains:
[IMG]http://www.jonathanriley.net/IMAG0002.JPG[/IMG]

my eyes are hurting, the Dell is a brick!

---

### Post by neptho on 2007-12-25
This is going to sound really odd, but go into your BIOS and check the settings; if they're not 'ultra high' for mains/AC, then your NVRAM is corrupt and you'll want to reflash your BIOS.

I've fixed countless 'broken' Dells this way.

---

### Post by dr johnson on 2008-01-12
Thanks neptho,
Sorry to have tarried so in getting back to you!

The settings in BIOS are absolutely irrelevant to the problem, as indeed you suggest. If I turn the setting right down, I just get a dim, but still indecipherable image at the screen.

Flashing the BIOS eh? That's a big one, and I've never done it. A google search does not look encouraging. Have you (or anybody else) got any advice?

I guess I need to start here:
[http://support.dell.com/support/edocs/systems/ins6400/en/sm/flshbios.htm#wp1000425](http://support.dell.com/support/edocs/systems/ins6400/en/sm/flshbios.htm#wp1000425)
[http://www.dellcommunity.com/supportforums/board?board.id=insp_bios](http://www.dellcommunity.com/supportforums/board?board.id=insp_bios)
/trepidation

---

### Post by neptho on 2008-01-19
I've actually created a thread here on how to flash the BIOS, but it appears there are much easier means.

[This](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate) is almost what I proposed, precisely, on how I did my update on my 6400.

[This appears to be a much easier way to do it](http://linux.dell.com/wiki/index.php/Repository/firmware), but I have not tested to see if it works.

---

### Post by dr johnson on 2008-02-10
neptho,
**: [This]("http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate") is almost what I proposed, precisely, on how I did my update on my 6400.**

Well, I did as you did, but when I got to the command "getSystemId", I got the reply "could not instantiate SMBIOS table"
Will keep hacking, albeit in the dark!

BTW, the reason I have been leaving this problem on the backburner for a while is that I was working on [this]("http://jonathanriley.net/lch.html") private little bit of research. It's an interesting read, especially for Europeans who might be ignorant of some cool 19th century American feats of Engineering ;-)

---

### Post by neptho on 2008-02-12
Did you remember to 'sudo' the command?

---

### Post by dr johnson on 2008-02-18
Once again, thanks neptho for your replies. I did indeed forget to prefix with sudo, but i tried it with sudo just now and got stuck following the dellBiosUpdate command (also sudoed!). I think I'm going to have to send it back to Dell.

---

