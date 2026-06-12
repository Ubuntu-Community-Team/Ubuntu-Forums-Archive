---
title: "Ubuntu 5.10 won't install..."
date: 2006-01-10
forum: General Help
---

### Post by PryGuy on 2006-01-10
Hello all!
I got a strange problem here! I can't install Ubuntu 5.10 on my PC with ASUS P4GPL-X motherboard. The installation process freeses on the stage where it configures the APT repositories. I tried both variants with PC connected and not connected to the internet. No difference... I have DHCP and Breezy finds my network card and it appears that it configures everything okay (5.04 couldn't) if it helps. Any ideas?

---

### Post by frodon on 2006-01-10
I already got this problem and last time i met it (installing ubuntu to a friend ;) ) the install process froze 30 min on this step and i didn't get other problems after this step.

So, first, i would advice you to wait 45 min at least to see if the install process is still active.

---

### Post by PryGuy on 2006-01-10
[QUOTE=frodon]I already got this problem and last time i met it (installing ubuntu to a friend  ) the install process froze 30 min on this step and i didn't get other problems after this step.[/QUOTE]Have you had the internet connection on during that installation?

Well, I had these suspicions too, but anyway, I only had to wait about 10 minutes when I used to install Breezy on my Duron950 machine with the internet connection turned off and it was absolutely immediately when I had this PC connected. So I haven't expected it. I will do this trick and will wait 45 minutes, but we all understand it's not okay to sit and wait looking at your PC doing nothing. I'd like to inform developers about the bug.

---

### Post by frodon on 2006-01-10
lol, yes it's a little bit annoying to wait 45 min (especially if you're not sure it will work), in the case of my friend the computer had an internet connection but behind a proxy so at this step the install process couldn't reach internet.

Hope you will not wait 45min for nothing ;)

---

### Post by PryGuy on 2006-01-10
[QUOTE=frodon]Hope you will not wait 45min for nothing ;)[/QUOTE]Well, me too...:) But in my case I think the PC could see the internet 'cause my old PC with Duron 950 is connected to the same network with the same conditions. This is probably caused by the incorrectly working network card drivers. I'll try it again and will report later...;) So we'll see. Anyway, I think we have to inform developers, this bug appears to be very unpleasant IMHO.:(

---

### Post by lamego on 2006-01-10
I had the same problem installing ubuntu on vmware without network .
You don't need to wait all that time.
You just need to switch to the second terminal (I am not sure now, i think its CTRL-ALTF-F2) .
Check for the apt process which is hang (ps -ef) , then kill it with kill pid, this will skip the apt update process and continue the install.
You will be able to do the apt-update later after setting up the network...

---

### Post by PryGuy on 2006-01-10
Thank you very much! I'll try it!:)

---

### Post by renzokuken on 2006-01-10
i had exactly this problem myself

i solved it by only installing the server, by typing "server" as instructed at the first screen.

install went fine with no problems

then i simply did

# sudo apt-get update
#sudo apt-get install ubuntu-desktop gdm

....in order to install gnome and get the full desktop version of breezy

(u can also use "kubuntu-desktop" for KDE or "xubuntu-desktop" for XFCE4

---

### Post by PryGuy on 2006-01-10
Does anyone know how to contact the Ubuntu developer team? This thing really annoys me and I want to open their eyes on this problem.:D

---

### Post by renzokuken on 2006-01-10
we're not the only two that have had this problem......i nearly gave up on ubuntu till i found an obscure solution buried in the forums, but the solution above worked for me and a few others so give it a try

---

### Post by beerorkid on 2006-01-10
I have had a USB flight stick give me problems before.

also a brand new plextor DVD burner will only get so far and bork out.

I have to use an old DVD rom to install 64 or x86 on a AMD 3400+ 

just thought I would throw that out there

---

### Post by PryGuy on 2006-01-16
Well, the strangest thing is that I recieved my Ubuntu CDs (it took them only two weeks to deliver the CDs!) and tried to install Ubuntu from one of them, I knew it's ridiculous and that the image that is on the factory CD is absolutely the same, it is just like the one that I downloaded from the Ubuntu site, but it worked! Everything installed like a breeze (but it led me to another problem  [http://ubuntuforums.org/showthread.php?t=116580]("http://ubuntuforums.org/showthread.php?t=116580") :().
Any ideas why it happened (I mean the first case)?

---

### Post by PryGuy on 2006-01-18
I've got a nice solution for this problem, it will take some user interaction though :). Sit and wait till installer detects your networking hardware and then unplug the ethernet socket. Do it during the process of copying packages for instance. It worked for me, think it'll work for you.

---

### Post by Age One on 2006-01-18
[QUOTE=beerorkid]I have had a USB flight stick give me problems before.

also a brand new plextor DVD burner will only get so far and bork out.

I have to use an old DVD rom to install 64 or x86 on a AMD 3400+ 

just thought I would throw that out there[/QUOTE]


I had a very simmiler problem during my install. my newer DVD drive did not want to boot the install cd's, and when it finally did it only made it about half way through install before it decided it didn't want to do any more. I had a WAY (like 10 years) old cd drive laying around. I cracked open my case, plugged it in as the slave drive with the DVD, changed some settings in the BIOS, and then it installed.

---

