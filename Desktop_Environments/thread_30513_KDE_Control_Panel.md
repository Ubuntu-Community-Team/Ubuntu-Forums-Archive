---
title: "KDE Control Panel"
date: 2005-04-29
forum: Desktop Environments
---

### Post by otterit on 2005-04-29
Strange Problem.

I'm trying to modify the network settings using KDE's Control Panel. 

* K  -->  Control Center  -->  Internet and Network  -->  Network Settings

When I access this screen, the options are locked.  After clicking on "Administrator Mode", the options are still locked.

Is this by design?

-- JHW

---

### Post by fitzrik on 2005-04-29
[QUOTE=otterit]Strange Problem.

I'm trying to modify the network settings using KDE's Control Panel. 

* K  -->  Control Center  -->  Internet and Network  -->  Network Settings

When I access this screen, the options are locked.  After clicking on "Administrator Mode", the options are still locked.

Is this by design?

-- JHW[/QUOTE]
 My guess is its a bug. I had Kubuntu installed for a short while (pre release) but I got rid of it. I think I got around it by running comething like the folowing in shell.

sudo kcmshell network

I'm not at a linux box so can't check what it was exactly but you might want to have a look at that.

Richard

---

### Post by dave9191 on 2005-04-29
You can also use 

sudo kcontrol 

to bring up the whole control center in admin mode.

---

### Post by otterit on 2005-04-29
I used the sudo kcontrol and that worked fine.

Any idea if this can be coded directly into the Kcontrol icon?

I tried adding 'sudo' and it didn't do a thing.

??

---

### Post by vanshark on 2005-04-29
I got mine working doing the following

sudo kwrite /etc/sudoers

(add this line to the bottom of the config file)

system_username ALL=(ALL) ALL

Jim

You'll need to restart your PC for it to take effect

---

### Post by feight on 2005-04-29
[QUOTE=otterit]I used the sudo kcontrol and that worked fine.

Any idea if this can be coded directly into the Kcontrol icon?

I tried adding 'sudo' and it didn't do a thing.

??[/QUOTE]
 I also am having an issue with the networking section of the KDE Control Center. When I leave it set to default settings, with a dynamic IP address, it works fine. If I administer the settings and change it to static and change the ip address it saves the information fine. When I fill the default gateway in and save the settings the number does not save and when I hit OK kcmshell crashes with a sigsegv signal.

It was late at night, I only had a half hour to play with it and I was more interested in making it work properly than actually solving my issue so I haven't attemped changing it through a shell yet. I can change my ip address in a shell if necessary but I was hoping there was a functionality fix someone could suggest for ease of use.

---

### Post by ubersoft on 2005-04-29
I have found that most of the parts of kcontrol that require you to log in as admin are in danger of either:

 - never getting around to prompting you for a password as the process gets lost somewhere between your mouse click and the password prompt

 - prompting you for a password and then wandering off as it supposedly trundles off to load the admin screen

 - crashing and crashing, and then crashing again.

It's happened to me for networking, it's happened when I've tried to load fonts, it's happened when I've tried to change the login fonts... there's something very buggy about going into admin mode in kcontrol.

---

### Post by brk3 on 2005-04-29
I have the same problem, trying to go into admin mode just goes back to the starting screen. Must be just a bug.. hopefully will be fixed next time

---

### Post by walkeral on 2005-04-29
I had the Administrator problem as well. There were 2 fixes I found (from somewhere else on this forum) that worked:

1) Delete everything in /var/tmp/kdecache (the one with your username in it)
2) Check the /etc/kde3/kdm/kdmrc file. Somewhere in the file it says "RootLogin" - this should be set to true.

---

### Post by dave9191 on 2005-04-29
>  	I had the Administrator problem as well. There were 2 fixes I found (from somewhere else on this forum) that worked:

1) Delete everything in /var/tmp/kdecache (the one with your username in it)
2) Check the /etc/kde3/kdm/kdmrc file. Somewhere in the file it says "RootLogin" - this should be set to true.

well that worked a treat :) my control center works like it should. Im guessing that the kubuntu team left the root login to false like in ubunut for security , but messed up the control panel as a result. 

Dave

---

### Post by escuchamezz on 2005-04-29
kcontrol is a complete joke in kubuntu, if microsoft released a control panel like this then peoples complaints will go through the roof. But ofcourse since it's a communist OS then we shouldn't criticise it and only thank the community (who are young ugly teenagers who will stop working on it once they get laid).
Once again it proves that Linux is still stuck in the 80's, a command line OS, the GUI is immature to say the least.

---

### Post by ubersoft on 2005-04-29
[QUOTE=escuchamezz]kcontrol is a complete joke in kubuntu, if microsoft released a control panel like this then peoples complaints will go through the roof. But ofcourse since it's a communist OS then we shouldn't criticise it and only thank the community (who are young ugly teenagers who will stop working on it once they get laid).
Once again it proves that Linux is still stuck in the 80's, a command line OS, the GUI is immature to say the least.[/QUOTE]
 Er... right...

Or MAYBE there's a REASON they still call it BETA.

Maybe.

---

### Post by dave9191 on 2005-04-29
A complete joke... what a short sighted post. One minor oversight made the admin function unworkable. Lets compare that to the MS admin function in control panel... .there isnt one. Something thats been pissing me off whenever you want to change a setting as and are running the unprivalaged account. 

If you dont like what Linux is, why are you here. Linux is developing at a constantly growing rate thats already exceded what windows has done. And no its not developed by teenagers, it has backing from large companies. Bah.. why am even bothering to reply to that...

---

### Post by feight on 2005-04-29
[QUOTE=escuchamezz]kcontrol is a complete joke in kubuntu, if microsoft released a control panel like this then peoples complaints will go through the roof. But ofcourse since it's a communist OS then we shouldn't criticise it and only thank the community (who are young ugly teenagers who will stop working on it once they get laid).
Once again it proves that Linux is still stuck in the 80's, a command line OS, the GUI is immature to say the least.[/QUOTE]

What are you talking about? Kubuntu/Ubuntu is free, and yet one little problem occurs and you're ready to start sniping it? Kubuntu does everything for me that XP does but faster, more reliably, and if I have a problem I actually get help (from some of the people that helped to code it).

Another thing, as much as many Linux users may dislike some things about Microsoft and their software, they've built in quite a few functions that let you use Linux in 'tandem' with Windows. I don't know about you, but I'm still waiting for some options in Windows that let me read Linux partitions as something other than "Healthy (unknown partition)" or gives me a built-in, Linux compatible, boot manager.

The truth be told, there are already Linux distributions out there that (if you stick with distro specific software as Windows would have you do) is at least as easy to run as Windows and a hell of a lot more stable. If Linux had more professionaly made games it would get a hell of a lot more research and development and yet it runs this well mostly from the work of volunteers.

By the way, I like this incarnation of Ubuntu so much, I actually picked up shop and made my main desktop Linux only. As soon as tablet functionality is fully implemented you can bet my laptop will be entirely Linux as well.

---

