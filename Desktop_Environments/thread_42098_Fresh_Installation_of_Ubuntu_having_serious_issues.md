---
title: "Fresh Installation of Ubuntu having serious issues"
date: 2005-06-16
forum: Desktop Environments
---

### Post by veraction on 2005-06-16
System Specs:
[list]
[*]AMD Athlon XP 2500+, MMX, 3DNow, ~1.5GHz
[*]512 MB DDR Crucial RAM, 333 MHz (underclocked to 266)
[*]ATI Radeon 9200 AGP
[*]Asus A7V8X-X Mobo
[*]Western Digital 20GB Hard Drive
[/list] 

I currently an running a dual boot system, Ubuntu / Windows XP Professional. The Windows XP works great - no lockups, can play games, fairly fast, etc.

However, when I boot to Ubuntu I encounter a few different problems that seem to occur randomly, at any time:
[list]
[*]Computer freezes completely & becomes unresponsive
[*]Various gnome type programs quit unexpectedly 
[*]Am randomly booted to login screen
[/list] 

I've also had these problems when Ubuntu was the only OS installed on the computer.

I think it must be a driver problem, since I'd think it couldn't be a hardware problem since Windows XP works so well.  ](*,) 

Any ideas?

---

### Post by tread on 2005-06-16
ATI drivers for Linux suck at the moment (or so I've been told). Check your xorg.conf and see if ATI drivers are being loaded .. try disabling them.


Heres some tips I saw in other threads (hint hint: use search :))

1. try removing or commenting out the "RenderAccel" option in your xorg.conf
2. replace 'ati' for 'vesa' in the /etc/X11/xorg.conf

---

### Post by veraction on 2005-06-16
1. Don't see a RenderAccel anyplace in the file
2. Just changed "ati" to "vesa" & now I can't see anything - its complately FUBAR'ed. Now I'm trying to change it back in recovery mode using vi editor but have no idea how to save after changing the file. I've been google'ing it with no help. I've tried holding shift then pressing Z then Z & all I get is two capital Z's as expected. Also not sure how :wq works..

 ](*,)

[edit] Nvm, I figured it out (how to save in vi). had to press ESC then ZZ

---

### Post by veraction on 2005-06-16
/bump

still have no idea what to do.. i've had this problem for months

---

### Post by w9cw on 2005-06-16
I'm running the same CPU with another motherboard with 1GB ram, but with an older ATI video card which uses the stock ATI RagePro drivers.  Everything works fine.

Good luck with drivers for the Radeon.  It seems like most Linux distros are more nVidia friendly - why I'm not sure.

---

### Post by tread on 2005-06-17
I believe that is because nvidia releases drivers on a regular basis while ati doesn't. Ati recently did release some drivers, but the performance improvement was negligible. 

I wish I could help you, but I don't have any experience configuring ati. All the best .. as no one seems to  be willing to take up this thread you will have to search the boards. I have seen the question asked and answered often enough, so you should find an answer. Also, search on other Linux sites .. those solutions are easily modified/adapted to ubuntu.

---

### Post by veraction on 2005-06-18
Well, I installed the linux video drivers from [www.ati.com](www.ati.com), but that doesn't seem to have changed anything. I thought it was fixed, but I crashed to login screen while writing my 'success' reply.

Now I have no more ideas :(

---

### Post by neighborlee on 2005-06-18
[QUOTE=tread]I believe that is because nvidia releases drivers on a regular basis while ati doesn't. Ati recently did release some drivers, but the performance improvement was negligible. 

I wish I could help you, but I don't have any experience configuring ati. All the best .. as no one seems to  be willing to take up this thread you will have to search the boards. I have seen the question asked and answered often enough, so you should find an answer. Also, search on other Linux sites .. those solutions are easily modified/adapted to ubuntu.[/QUOTE]

It is not just ati..I and others have similar locks with nvidia too..X crashes and leaves mouse and keyboard working..

shrug
cu
nl

---

### Post by veraction on 2005-06-18
it's not like these crashes are rare. i'm lucky if I can go 4 minutes without one crash

---

### Post by zue on 2005-06-19
[QUOTE=veraction]it's not like these crashes are rare. i'm lucky if I can go 4 minutes without one crash[/QUOTE]
 Well, I also just installed ubuntu (hoary) on my shiny new  computer and am having the same problems, except mine doesn't even get far enough to crash.  When I log in I get a nice brown screen that says ubuntu with no panels and mouse and keyboard are completely useless.  I also have an ATI Radeon motherboard.  I am a linux newbie and have no idea where to start to fix this.  The funny part is, I'm using the live cd for warty warthog right now, and it's working just fine.  I dunno... maybe I should try another linux distro?  I really don't want to install windows.

---

### Post by neighborlee on 2005-06-19
[QUOTE=neighborlee]It is not just ati..I and others have similar locks with nvidia too..X crashes and leaves mouse and keyboard working..

shrug
cu
nl[/QUOTE]

I did however see on one fourm post to switch to lower nvida driver of 6629 which I did..so far on a new install of around 3 days and computer on all of those days, I've not had any crashes, so nvidia users anyway try 6629 ..if it does ill report back.

cu
nl

---

### Post by veraction on 2005-06-19
Well, I think I'm gonna have to give up. I don't know what else to do.

I'm either gonna try a different distro of linux or buy a newer video card.

too bad windows is > ubuntu   ](*,)

---

### Post by neighborlee on 2005-06-21
[QUOTE=neighborlee]I did however see on one fourm post to switch to lower nvida driver of 6629 which I did..so far on a new install of around 3 days and computer on all of those days, I've not had any crashes, so nvidia users anyway try 6629 ..if it does ill report back.

cu
nl[/QUOTE]

okay well..either my puter is overheating ( no temp controlls atm sorry ) or its some interaction with x/gnome or something ubuntu is doing ..I flat dont know but wanted to update to say it happened again..I opened 'run as different user' and bam locked up X tight...trying to reboot had 'cupsd' lockup to point I had to shutdown completely..

just a fyi in case it helps someone diagnose this issue

cheers
nl

---

### Post by veraction on 2005-06-22
Well, I switched to SUSE LINUX, even though I like Ubuntu much better.

Oh well, problem solved :(

---

### Post by desdinova on 2005-06-22
I wouldn't worry too much about it - Linux is all Linux - we're all family - I used Suse for a long while and its a good solid distro - I changed over as I felt like a change plus I wanted Gnome 2.10 ;-) (was on 9.2)

---

