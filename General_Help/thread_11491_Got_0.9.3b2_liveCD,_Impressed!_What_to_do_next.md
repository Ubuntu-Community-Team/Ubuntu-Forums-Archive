---
title: "Got 0.9.3b2 liveCD, Impressed! What to do next?"
date: 2005-01-17
forum: General Help
---

### Post by tv123 on 2005-01-17
Hi Folks,

I downloaded 0.9.3b2 developer release of gnoppix (liveCD), and it firedup a nice
gnome desktop shortly! Very fine work, folks!  Thanks  =D> 

I am now wondering how to install it to my harddrive.
I'd appreciate step-by-step instructions on how to go about doing this
(I am guessing "morphix" installer will be used somehow), including how
to make a working entry into an already existing grum menu (from
a "Kanotix" installation in another partition), and procedures for
making initrd image if needed.

Also, could you please let me know how to obtain the kernel source
for this release?

Thanks in advance.
Tom

---

### Post by node on 2005-01-17
gnoppix ?
did u see the url of this forum ? :D

---

### Post by tv123 on 2005-01-17
[QUOTE=node]gnoppix ?
did u see the url of this forum ? :D[/QUOTE]

Thanks for the pithy reply, Chief :)

I thought that Ubuntu and Gnoppix are working together now. Besides,
the forum link from Gnoppix redirected me to this forum. I am not sure
what the exact status of the merger is, but I'd appreciate if anyone could
share their knowledge on doing a HD install of a live CD of ubuntu or
Gnoppix.

Thanks
Tom

---

### Post by jobdrb on 2005-01-17
Please, where You got a 0.93b that is a Live CD?

I download from gnoppix.org ([http://source.rfc822.org/pub/local/gnoppix/gnoppix/beta/hoary_0.9.3b2-i386.iso](http://source.rfc822.org/pub/local/gnoppix/gnoppix/beta/hoary_0.9.3b2-i386.iso))

I got only a Install version, not a Live CD

any ideas?

---

### Post by jobdrb on 2005-01-17
[QUOTE=jobdrb]Please, where You got a 0.93b that is a Live CD?

I download from gnoppix.org ([http://source.rfc822.org/pub/local/gnoppix/gnoppix/beta/hoary_0.9.3b2-i386.iso](http://source.rfc822.org/pub/local/gnoppix/gnoppix/beta/hoary_0.9.3b2-i386.iso))

I got only a Install version, not a Live CD

any ideas?[/QUOTE]

Solved

---

### Post by fabinho on 2005-01-18
[QUOTE=jobdrb]Solved[/QUOTE]

Please, how do you run as live CD?

---

### Post by fabinho on 2005-01-18
[QUOTE=tv123]Hi Folks,

I downloaded 0.9.3b2 developer release of gnoppix (liveCD), and it firedup a nice
gnome desktop shortly! Very fine work, folks!  Thanks  =D> 

I am now wondering how to install it to my harddrive.
I'd appreciate step-by-step instructions on how to go about doing this
(I am guessing "morphix" installer will be used somehow), including how
to make a working entry into an already existing grum menu (from
a "Kanotix" installation in another partition), and procedures for
making initrd image if needed.

Also, could you please let me know how to obtain the kernel source
for this release?

Thanks in advance.
Tom[/QUOTE]



Tom, burn the ISO image as a multisession CD and after record the files morphixinstaller and gengrubmenu2 in the CD folder /dev (they will be automatically installed).

You'll find the files here:
[http://source.rfc822.org/pub/local/gnoppix/gnoppix/installer/](http://source.rfc822.org/pub/local/gnoppix/gnoppix/installer/)

---

### Post by tv123 on 2005-01-18
[QUOTE=fabinho]Tom, burn the ISO image as a multisession CD and after record the files morphixinstaller and gengrubmenu2 in the CD folder /dev (they will be automatically installed).

You'll find the files here:
[http://source.rfc822.org/pub/local/gnoppix/gnoppix/installer/](http://source.rfc822.org/pub/local/gnoppix/gnoppix/installer/)[/QUOTE]

fabinho: thanks for the tip. I guess k3b will allow me to do the multisession
CD. I noticed that the CD doesn't have a preexisting /dev directory, and so 
I will try to create this folder before burning the second stage.

This is what happened when I tried originally:  The installation boot sequence failed to
recognize the Intel Pro 2200 B/G wireless card, and so, when I chose to "not configure
network at this time" option, it proceeded to launch me into a "live CD" session", and
that's it; I had a desktop that was usable as a desktop, but not doing anything installation-wise.
I tried to "hack it" into installing to HD: manually setup networking, apt-get update etc, and then
dowloaded morhpixinstaller, gengrubmenu2, osporber installed them, and then ran morphixinstaller
by invoking it from the cmd line, and when prompted, asked it to isntall :"grub" on the root
partition. It did install stuff on to the partition, but left no kernel and no initrd in the
/boot directory for me to point to in my grub menu from the "Kanotix" installed linux
(Kanotix is simply superb BTW, except for not having Xorg, and Gnome!)
in another partition. I tried the ones from the /install directory, but it didn't boot.

Will just having these two files on the cd change things upon booting?

Thanks,
Tom

---

### Post by jobdrb on 2005-01-18
[QUOTE=fabinho]Please, how do you run as live CD?[/QUOTE]


Hi Fabinho,

First, follow the instructions, You feel that will be Install, but, not.

IF ok the GNome will appears, otherwise

If FAIL to start X, choose OK in the messages, login as root (no password needed)
and edit [pico  /etc/X11/xorg.conf] in the "device" section
In my case, startx X fail (nvidia) then I remove the UseFB line, and then startx

Job

from Florianopolis - Brasil
The Island of Magic ;-)

---

### Post by jobdrb on 2005-01-18
[QUOTE=tv123]fabinho: thanks for the tip. I guess k3b will allow me to do the multisession
CD. I noticed that the CD doesn't have a preexisting /dev directory, and so 
I will try to create this folder before burning the second stage.

This is what happened when I tried originally:  The installation boot sequence failed to
recognize the Intel Pro 2200 B/G wireless card, and so, when I chose to "not configure
network at this time" option, it proceeded to launch me into a "live CD" session", and
that's it; I had a desktop that was usable as a desktop, but not doing anything installation-wise.
I tried to "hack it" into installing to HD: manually setup networking, apt-get update etc, and then
dowloaded morhpixinstaller, gengrubmenu2, osporber installed them, and then ran morphixinstaller
by invoking it from the cmd line, and when prompted, asked it to isntall :"grub" on the root
partition. It did install stuff on to the partition, but left no kernel and no initrd in the
/boot directory for me to point to in my grub menu from the "Kanotix" installed linux
(Kanotix is simply superb BTW, except for not having Xorg, and Gnome!)
in another partition. I tried the ones from the /install directory, but it didn't boot.

Will just having these two files on the cd change things upon booting?

Thanks,
Tom[/QUOTE]


Hi, I think that the use of morphixinstaller are incorrect, because 0.93b its not base in the morphix more. :) Read the announces and discussion.

You will need to wait until, Hoary is out. 


for the moment, try currently Ubuntu.

---

### Post by fabinho on 2005-01-18
[QUOTE=jobdrb]Hi, I think that the use of morphixinstaller are incorrect, because 0.93b its not base in the morphix more. :) Read the announces and discussion.

You will need to wait until, Hoary is out. 


for the moment, try currently Ubuntu.[/QUOTE]



You are right. 

My idea just work on Gnoppix 8.2.2. And the correct folder name is /deb (the place to put .deb files in Morphix).

---

### Post by amu on 2005-01-24
[QUOTE=node]gnoppix ?
did u see the url of this forum ? :D[/QUOTE]

and? dude, you've no idea :)

---

