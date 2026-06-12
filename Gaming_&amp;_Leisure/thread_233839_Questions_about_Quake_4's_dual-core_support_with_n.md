---
title: "Questions about Quake 4's dual-core support with new patches"
date: 2006-08-10
forum: Gaming &amp; Leisure
---

### Post by MetalMusicAddict on 2006-08-10
I noticed with the new patches for Quake 4 "Multiple CPU/Core" support has been added. When I run Quake 4 on [my new system]("http://www.ubuntuforums.org/showthread.php?t=224416") though "Multiple CPU/Core" is greyed out in the "Advanced Options" page.

I have the 1.3 patch installed. A vNidia card with the newiest repo drivers. Newiest 32-bit "K7" kernel (Which SMP support). Installed all in Xubuntu.

Can anyone with Quake4 and dual-core/CPUs help?

---

### Post by Gnobody on 2006-08-10
[LEFT]Type: quake4-smp in a terminal and see what that does for you.  Also, go into the menu and see if SMP is enabled in the advanced options
[/LEFT]

---

### Post by MetalMusicAddict on 2006-08-10
OK. I finally found info on this. Theres 2 ways to do it.

_Way one:_
[LIST=1]
[*] After the game loads, open the console by holding down **Ctrl + Alt + Tilde(~)**. A window should now pop down from the top of the screen.
[*] At the prompt, type **r_useSMP "1"** and press enter.
[*] Close the console by pressing the **Tilde(~)** key.
[/LIST]
[U]
Way two:[/U]
Go to your .quake4 folder in your home folder. You might have it hidden. In the q4base dir you will see a file called **Quake4Config.cfg** Open that and add a line to it that looks like this: **seta r_useSMP "1"**. This is where I usually add options but I didnt know it was as easy as this. :)

Well I hope this helps others.

---

### Post by MetalMusicAddict on 2006-08-11
So is any gettin kinda crappy preformance on a AMD 64? Im gettin glitches with my new system where I didnt get them with my AMD 2600+. 

So far:
[LIST]
[*]Menus take forever to load.
[*]I get little hick-ups with lighting effects.
[*]I get lock-ups when a new area has to load.
[/LIST]
I ran it through a terminal to see if it gave me anything and all it really errors on is some sound dropping. Nothing really.


Heres what I got:
[LIST]
[*]Mobo: Gigabyte GA-M55SLI-S4
[*]CPU: Athlon 64 X2 4600
[*]GFX: eVGA Geforce 7900GT 256MB
[*]RAM: Corsair XMS2 1GB
[*]HD: Western Digital Raptor 74GB 10k RPM
[/LIST]

Maybe I need a newier driver? I have the newiest one from the repos?

Any tips?

---

### Post by MetalMusicAddict on 2006-09-25
Just for anyone who drops by the thread. I had too new a card. The Dapper repo drivers werent enough for my 7900GT. I used the drivers from nVidia and everything flys now. ;)

---

### Post by engsub on 2008-04-20
> **MetalMusicAddict said:**
> OK. I finally found info on this. Theres 2 ways to do it.

_Way one:_
[LIST=1]
[*] After the game loads, open the console by holding down **Ctrl + Alt + Tilde(~)**. A window should now pop down from the top of the screen.
[*] At the prompt, type **r_useSMP "1"** and press enter.
[*] Close the console by pressing the **Tilde(~)** key.
[/LIST]
[U]
Way two:[/U]
Go to your .quake4 folder in your home folder. You might have it hidden. In the q4base dir you will see a file called **Quake4Config.cfg** Open that and add a line to it that looks like this: **seta r_useSMP "1"**. 

I found a 3rd way.  You can launch **quake4-smp** from the command line.  You can also change your launch icon to point to quake4-smp.

---

### Post by godvalve on 2008-11-10
> **engsub said:**
> I found a 3rd way.  You can launch **quake4-smp** from the command line.  You can also change your launch icon to point to quake4-smp.

Brilliant! Thank you for this little piece of info. You rock! :guitar:

---

