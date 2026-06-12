---
title: "How do I kiosk Gnome ?"
date: 2005-03-13
forum: Desktop Environments
---

### Post by gmc on 2005-03-13
Greeting All,

Earlier to day I was talking to my neighbor, who is a caretaker for a rooming house nearby. A few months back, he built an old Pentium 2 450Mhz machine with 386M of ram and a 5G hard drive. He installed Windows98 on the machine and put it into the common room for the tenants of the rooming house to use for Internet access, writing (letters, resumes, etc...) and a few basic games. Now the problem is that the tenants keep installing software downloaded from the Internet (not to mention viruses, worms and spyware) and mucking about with the machine's configuration, thus rendering the machine unstable and unusable most of the time.

After some discussion, I convinced him that Ubuntu :-) would be ideal for the job, however I've run into a few snags. My idea was it install Ubuntu, configure a test user, then copy the dot configuration files and directories into the /etc/skel so when we add a user/tenant, the account would be completely configured and ready to go. I also though that by using Linux' basic file attributed, I could stop the tenants from modifying basic settings and screwing things up. 

I know KDE has a kiosk mode that will limit what the users can change but I'm not a KDE user (heck I've only just recently started using Gnome, was a WindowMaker user for 5 years) and it seems a bit complicated to setup. Though I did try unsuccessfully. I also tried XFCE4 as that also has a kiosk mode, but it didn't take me long to decide that wouldn't work. So I've kind of got my heart set on using Gnome.

What I'd like to do is remove the following options (in hoary)

Applications->Run Application
Applications->System Tools
Computer->Disks
Computer->Network
Computer->Desktop Preferences (only some of the options)
Computer->System Configuration
Computer->Lock Screen

I was able to remove all the sub-options from some of these menus but when I logout and login, these removed options return automatically. :-(

Does anyone know how to remove these menu options or force them to ask for a password ? Any help or suggestions are greatly appreciated.

Thanks
Gord

---

### Post by bored2k on 2005-03-13
[QUOTE=gmc]Greeting All,

Earlier to day I was talking to my neighbor, who is a caretaker for a rooming house nearby. A few months back, he built an old Pentium 2 450Mhz machine with 386M of ram and a 5G hard drive. He installed Windows98 on the machine and put it into the common room for the tenants of the rooming house to use for Internet access, writing (letters, resumes, etc...) and a few basic games. Now the problem is that the tenants keep installing software downloaded from the Internet (not to mention viruses, worms and spyware) and mucking about with the machine's configuration, thus rendering the machine unstable and unusable most of the time.

After some discussion, I convinced him that Ubuntu :-) would be ideal for the job, however I've run into a few snags. My idea was it install Ubuntu, configure a test user, then copy the dot configuration files and directories into the /etc/skel so when we add a user/tenant, the account would be completely configured and ready to go. I also though that by using Linux' basic file attributed, I could stop the tenants from modifying basic settings and screwing things up. 

I know KDE has a kiosk mode that will limit what the users can change but I'm not a KDE user (heck I've only just recently started using Gnome, was a WindowMaker user for 5 years) and it seems a bit complicated to setup. Though I did try unsuccessfully. I also tried XFCE4 as that also has a kiosk mode, but it didn't take me long to decide that wouldn't work. So I've kind of got my heart set on using Gnome.

What I'd like to do is remove the following options (in hoary)

Applications->Run Application
Applications->System Tools
Computer->Disks
Computer->Network
Computer->Desktop Preferences (only some of the options)
Computer->System Configuration
Computer->Lock Screen

I was able to remove all the sub-options from some of these menus but when I logout and login, these removed options return automatically. :-(

Does anyone know how to remove these menu options or force them to ask for a password ? Any help or suggestions are greatly appreciated.

Thanks
Gord[/QUOTE]
 I don't know the "normal" way, but you can always remove the user's permission.
For example if you make /usr/bin/nautilus not readable/executable by the user, there is no way he could access home/disks/ [he would in terminal though, but you're making him not be allowed to do this ;)].

All of those buttons are just icons for commands, you just have to figure out wich ones they are. [gnome-control-center, etc].

Soon enough someone will come up with a *real* solution I think.

Btw, your avatar -- > Rockin' !   \\:D/

---

### Post by gmc on 2005-03-13
Hi bored2k

Thanks for the compliment. Actually I'm onto something here. I discovered a program called gconf-editor. I've been able to disable the Computer->Lock Screen option, I just need to find the appropriate entries for the other options. 

If anyone can help with that, I'd be very grateful

Thanks
Gord

---

### Post by lordofkhemenu on 2005-03-13
[QUOTE=gmc]Hi bored2k

Thanks for the compliment. Actually I'm onto something here. I discovered a program called gconf-editor. I've been able to disable the Computer->Lock Screen option, I just need to find the appropriate entries for the other options. 

If anyone can help with that, I'd be very grateful

Thanks
Gord[/QUOTE]
gconf editor is good stuff (but frowned upon. why? dunno. guess they want you to use the applets for each feature)
You can disable the command line (and save to disk, printing and print setup)  in **[color=SeaGreen]desktop |lockdown[/color]**
Under **[color=SeaGreen]apps|panel|general[/color]** there is an option for 'enable program list'. With that unchecked the list of known programs (preferences, root terminal, gconf (oh no!),etc. will not be available. If they don't know the name they can't run it (and with terminal gone and command line disabled above..not much good, eh? 8-) )
You ***really*** want to check out **[color=SeaGreen]apps|panel|global[/color]**...
(disable force quit, disable lock screen, disable log out...).
That should get ya started. Just explore all the sections...interesting stuff in there :D

Oh yeah, and congrats and kudos on bringing someone over from The Dark Side.=D>

---

### Post by dare2dreamer on 2005-03-18
If all you are trying to provide is a browser only solution, you might consider doing some checking into mini-distros like kiosk-cd or knocking up something similar yourself.

I'm currently working on a livecd (damnsmalllinux remaster) that boots to nothing but firefox, but am hitting the wall locking down the browser to one tabs-only interface with no menus. Once I sort that up, I'll likely release a copy for people.

---

