---
title: "The CUPS server could not be contacted"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Weman on 2005-12-18
Hi there

I cannot access "system/administration/printers" without getting the message "The CUPS server could not be contacted"

I have tried "/etc/init.d/cupsys restart" and get the response:
 "* Restarting Common Unix Printing System: cupsd                         [ ok ]"

I have tried to reinstall all CUPS part I can find in "Synaptic package manager".
I have tried "http://localhost:631" and from there I could send at test page, but it did not fix anything.
Everything worked fine yesterday but now I have no access to printer, what may have happened? Anybody  have a clue. I found some guys with similar problem and one of them solved it by restarting CUPS but I have tried that as I mentioned.

// Weman from Sweden

---

### Post by Weman on 2005-12-20
Now I found this?

[http://lists.debian.org/debian-printing/2005/09/msg00067.html](http://lists.debian.org/debian-printing/2005/09/msg00067.html)

Could be the bug.

// weman

---

### Post by Bomper on 2006-01-01
1:- sudo gedit /etc/network/interfaces

   2.- And the end of file:

       auto lo

---

### Post by Weman on 2006-01-02
Hi, "Bomper" thank's for the hint.

Unfortunally it did not help, but it disconnected me from LAN and my router.

Now I have tried another older computer (300mHz PackardBell) and it too has support for both IPV4 and IPV6 but CUPS works just fine so the problem with IPV6 and CUPS 1.1 is no single explanation either.

I'm still waiting for the problem to solve itself since I've run out of ideas.

Weman

---

### Post by saultpastor on 2006-01-06
Same thing happening here.  I think it occurred after installing the new kernel for breezy offered by the update manager.  I held off for a couple of weeks because I don't like kernel upgrades.  I don't know if it is related but...

I will try booting to the old Kernel

---

### Post by saultpastor on 2006-01-06
Nope, still gone, should've check before writing....still searching

---

### Post by Weman on 2006-01-07
Hi, Yes I think I have tried that too without any luck, but I too think it happened when I installed something, I've made som small changes in the conf files to get LAN working with my winXP-box. But the same changes are made too an older computer and there CUPS still works fine. All hints I have found and changes I have tried in conf files that did not help is carefully restored. My LAN works fine both ways winXP-Ubuntu. I'm still hoping the next update will fix it.

Thank's anyway, keep me posted if you find anything.

//Weman

---

### Post by Abandon on 2006-01-07
You could try my cupsd.conf. Its one that is "borrowed" from Mandriva 2006 and it works like a charm.

[http://www.digiplace.nl/images/cupsd.conf.file](http://www.digiplace.nl/images/cupsd.conf.file)

---

### Post by zappa86 on 2006-01-07
Hmm. Does it work if you restart your computer? Make sure your loopback ethernet adapter is up go into the console and under super user type:
```
ifup lo
```
I know sometimes when my wireless card cant find the internet startup of ubuntu takes too long so I <ctrl> c the startup and it does not get a chance to bring up the lo.

---

### Post by Weman on 2006-01-07
Hi, thanks Abandon for the conf-file. I tried it but no luck still.

Hi, thanks zappa86 for the hint about ethernet. I don't have a loopback ethernet adapter, but when typing in terminal I get this:

root@w-dell:/home/ake# ifup lo
ifup: interface lo already configured
root@w-dell:/home/ake#

Anyway I have no problem with my LAN, works fine between Ubuntu, Internet and winXP computers. I have 2 Ubuntu boxes and 3 winXP boxes. I can move my files to any other computer by LAN and print from there.

// Weman

---

### Post by bdd4 on 2006-01-13
[QUOTE=Bomper]1:- sudo gedit /etc/network/interfaces

   2.- And the end of file:

       auto lo[/QUOTE]

I recently installed breezy and get the same CUPS error. "auto lo"  did 
not work for me. Also it prevented me from getting on the internet.

bdd4

---

### Post by kenweill on 2006-01-13
I was just having the same problem and have just fixed it.

What I did?

1. System --> Administration --> Services
2. Uncheck "Print Service (cupsys)".
3. Restart my computer.
4. System --> Administration --> Services
5. Chech "Print Service (cupsys)".

I have no idea how it works. I don't know why it was fixed in this way.
But it fixed my problem "The CUPS server could not be contacted".

And just hoping it would work for you too.

---

### Post by Weman on 2006-01-14
Thanks kenweill for the hint, it did not help me though.
I think there should be a simple explanation since the CUPS server is there, I can restart it from terminal and access it from "http://localhost:631/" but not from Gnome or KDE. Still hoping for a miracle, before reinstalling Breezy, there's no guarantie that that helps either.
// Weman

---

### Post by bdd4 on 2006-01-14
SOLUTION TO "cups server could not be contacted": as of 1-15-06:

1. Apparently there is a bug somewhere in the updates for breezy 5.10 after you install them.

2. I reinstalled breezy from my cd which I downloaded from the ubuntu site about 
december 15, 2005.

3. I have carefully loaded a number of utilities but NOT THE UPGRADES!

4. I can assert SYSTEM, ADMINISTRATIION, PRINTING and CUPS starts just fine.
I can then add a printer.

5. now we need "hotshot" help to solve the real problem.

bdd4


[QUOTE=Weman]Hi there

I cannot access "system/administration/printers" without getting the message "The CUPS server could not be contacted"

I have tried "/etc/init.d/cupsys restart" and get the response:
 "* Restarting Common Unix Printing System: cupsd                         [ ok ]"

I have tried to reinstall all CUPS part I can find in "Synaptic package manager".
I have tried "http://localhost:631" and from there I could send at test page, but it did not fix anything.
Everything worked fine yesterday but now I have no access to printer, what may have happened? Anybody  have a clue. I found some guys with similar problem and one of them solved it by restarting CUPS but I have tried that as I mentioned.

// Weman from Sweden[/QUOTE]

---

### Post by Weman on 2006-01-15
OK, bdd4, 

Very interesting. I agree with your conclusion. I have an older PC with the same Breezy in but not so many added programs and a fully functional CUPS, it has not been updated for some weeks. I will update one package at the time and restart and watch what happens. If nothing happens then I will try to write down the difference between the two installations and post a new reply.
// Weman

---

### Post by Weman on 2006-01-15
So now I have updated all programs in my older PC and CUPS is still there.
I have compared (in menus) which more programs I have added in the PC with the CUPS problem according to list below, and then removed some of them.
That did not make any difference. Anyway I think I installed most of them after the CUPS problem occurred. I realize though that removing with Gnome Program Installation tool may not result in a complete removal. 
// Weman

Graphics:
Dia (removed)
Pdf-viewer
Webcamera Canorama (removed)

Internet:
Nvu
Thunderbird e-mail (surely installled after CUPS problem)

Sound Video:
Gnome Baker (removed)

Programming:
Hexadecimal editor
Kdvelop (surely installled after CUPS problem)
Kompare
Nvu
Scite Text edtitor

Assessories:
Baobab (removed)
KDE Print & Fax (surely installled after CUPS problem)
Kjobviewer (surely installled after CUPS problem)

System tools:
Configure Debian (removed)
Configure Network card (removed)
Gnome Apt Software (removed)
Kdiskfree (removed)
Kickstart (removed)
KsysV (removed) (surely installled after CUPS problem)
Kynaptic (surely installled after CUPS problem)
Gnome Keyringmanager (removed) (surely installled after CUPS problem)
Root terminal
Kfastdisk (removed)

System Settings:
Art manager
Energy settings
Splash screen

System Administration:
Bootup manager

---

### Post by Weman on 2006-01-17
Hi, now I have posted a bug report via [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/) 

 Bug #28812 in Ubuntu: "CUPS server could not be contacted"

/ Weman

---

### Post by Weman on 2006-04-05
So finally my problem is solved. I got a hint after posting a bug report.

[https://launchpad.net/malone/bugs/28812](https://launchpad.net/malone/bugs/28812)

It was:

I couldn't start gnome-cups-manager as well, until i edited client.conf:
>sudo gedit /etc/cups/client.conf
>
>and changed whatever name of the server to:
>ServerName localhost
>
>After that I restarted cupsys:
>sudo /etc/init.d/cupsys restart
>

That did the trick, i can finally access printer manager in Gnome and print.
I've been trying since before christmas.

/ Weman  :)  :)  :)

---

