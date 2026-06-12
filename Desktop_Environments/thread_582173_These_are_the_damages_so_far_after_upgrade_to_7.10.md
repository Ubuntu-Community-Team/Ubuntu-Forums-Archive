---
title: "These are the damages so far after upgrade to 7.10"
date: 2007-10-19
forum: Desktop Environments
---

### Post by madelman on 2007-10-19
1.  I  lost  my splash window
2. keyring lost. I had fixed this issue in 7.04 so I did not have to type this kyring every time I log in. Now it does not work. It asks again the keyring.
3. When log out and switch users, a bunch of messages are displayed, this is not nice and looks like the machine is going to start throwing bytes all over the place.
4. No sound when shutting down and again, a bunch of messages displayed on the screen
5. Everything seems slower to display now on the screen. Even connecting to internet, all web sites response is slower.
6. When you open any application Firefox used to be the only one very slow to start, now all the applications show "starting..." for a while. 
7.It screwed my Pidgin. It reinstalled a version that is not compiled with ssl support, so MSN service cannot start. I had to compiled Pidgin in 7.04 and worked, now again I have to download , recompile and see if that works. 


All of these did not happen with 7.04, so I am sure the upgrade is going to be another 3-4 hours figuring out in internet how to resolve all these issues.

Can't you just upgrade the kernel and something that does not affect applications?

Is there anyway to downgrade to 7.04?

---

### Post by nick944 on 2007-10-19
Yeah, 7.10 has a LOT of bugs. It makes me want to dowgrade back to 7.04.

---

### Post by FredB on 2007-10-20
> **nick944 said:**
> Yeah, 7.10 has a LOT of bugs. It makes me want to dowgrade back to 7.04.

Such as ? Can you list them ?

A good upgrade is a clean install upgrade. Upgrade on a previous install is always buggy.

For your info, I am using Gutsy since beta, and no big problem or big bad bugs.

---

### Post by mortsahl on 2007-10-20
For me 7.10 is very slow.  The apearance app just hangs.  I was really looking forward to 7.10 and now I'm sorry I installed it.

---

### Post by bluedragon436 on 2007-10-20
When I upgraded my install from 7.04 to 7.10 the only real issue I was having at the time was no sound when I shutdown, but after having a reason to want to load 7.10 from a fresh start now I am having all kinds of issues such as:

1.Still no shutdown sound
2.Very slow to start up in the first place, usually takes approx. 3mins. to actually start up (tried to start up in "safe mode", and it seemed to start a bit faster, but only after being given a chance to type exit.
3.Almost everything is slow to open


I think I am actually going to go back to 7.04 and do the upgrade again, that seemed to be the best running.

---

### Post by kostin on 2007-10-20
How to downgrade to 7.04 with saving all users settings and data?

---

### Post by LordKelvan on 2007-10-20
@mortsahl:  If the appearance app/dialog is hanging for you, you might want to try removing the gtk-qt-engine package.

---

### Post by Southtown on 2007-10-20
> **kostin said:**
> How to downgrade to 7.04 with saving all users settings and data?
I'm just guessing, but isn't the 7.04 boot image backed up and made a secondary option in grub? I installed 7.10 into a seperate partition so I dunno.

---

### Post by bigboy_pdb on 2007-10-20
madelman, I was very disappointed with the upgrade and found that it caused a number of problems in my system and that a fresh install was better. You might get better results by backing up your files and re-installing Ubuntu. Even if you could downgrade (which I don't think that you can), that doesn't mean that your problems would be fixed. It would probably cause more problems.

1. Regarding the splash screen missing when you log into the system, the developers decided to remove the splash screen because it made the log in process take longer. To restore it, open the Configuration Editor (using the command "gconf-editor") and click the check box for /apps/gnome-session/options/show_splash_screen.

2. The keyring manager appears to have been changed so that it no longer asks for a password when the user is logging in (I'm basing this solely on my experiences with the program and I could be wrong so it would be good if other people could verify that the keyring manager's behaviour has changed for them as well). Those changes might have affected your original changes. The program itself is still there. You can open it by using the command "gnome-keyring-manager".

5 & 6. I've noticed this behaviour as well.

7. Pidgin is now installed with GNOME so that might have affected your original Pidgin installation.

You should probably file bug reports for the problems that weren't already reported on "launchpad.net".

---

### Post by alf on 2007-10-20
Another problem: the pop-up menu for a removable disk (USB pen-drive) doesn't show the 'eject' option anymore. It shows the unmount option insteady. So I have to open a terminal and execute 'eject /dev/sdb' to disconnect my pen-drive properly.

---

### Post by wormite on 2007-10-20
I'm experiencing 6 and it's very annoying, I have looked around alot but there's no solution to this.
I hope someone can help out there to solve this.

---

### Post by garretwp on 2007-10-21
I am surprised many of you are having performance issues. I did a clean install of 7.10 and kept my home partition intact. My boot up is really fast, much much faster then 7.04. The system seems to be humming along great. I am running on an AMD X2 4200 with 2GB ram.

- Garrett

---

### Post by Malvolio on 2007-10-21
I'm having something of a missing icon problem with the latest Ubuntu (Gutsy). I place my panels on the sides instead of the top and bottom because I'm on a widescreen laptop and having them on the sides maximizes the vertical space. Because the panels are sideways Feisty's program bars would display icons instead of the headers. After upgrading to Gutsy those icons disappeared, replaced with ".." instead making identifying which button is which a hassle. What do I need to reinstall or where can I find the option to bring these icons back?

---

### Post by Malvolio on 2007-10-21
My posts seem to have a destructive effect.  I found a fix by bumping the panels from a size of 24 to a size of 30 but I liked the smaller size, personally.

---

### Post by z0phi3l on 2007-10-21
> **alf said:**
> Another problem: the pop-up menu for a removable disk (USB pen-drive) doesn't show the 'eject' option anymore. It shows the unmount option insteady. So I have to open a terminal and execute 'eject /dev/sdb' to disconnect my pen-drive properly.

Unmount IS the proper way to "eject" an USB pen drive.

---

### Post by Melcar on 2007-10-21
Only minor complaints for me.  I did a clean install to ensure proper functionality.  I too have noticed the increased load times when launching apps, and even the increased boot time when the OS loads up (I initially thought my computer stopped responding).  The lack of  boot screen is more of an annoyance that anything else.  I also can't seem to change the background color of the splash screen (it just stays at ugly brown no matter what colors I select).  So far everything is working thought, so I can't really complain.

---

### Post by madelman on 2007-10-21
I found other issue with my upgrade. 

When I hibernate my laptop, it goes down without problems then when I turn it on it comes back and my wireless network is not listed and not found therefore I cannot connect to the network. I have to reboot my machine in order to get my wireless router listed in the network manager. 

It looks like the network you were connected before going to hibernate is the one lost when it comes back.

---

### Post by tehtrk on 2007-10-23
> **FredB said:**
> Such as ? Can you list them ?

A good upgrade is a clean install upgrade. Upgrade on a previous install is always buggy.

For your info, I am using Gutsy since beta, and no big problem or big bad bugs.

Good helpful info, but I figured since the Update Manager was the recommended means to upgrade as per the release announcements, it would be the best way to do it. 

Overall, I prefer Feisty. Every 2.6.22 kernel is buggy for me (ubuntu and vanilla versions). I have used linux for years now(Gentoo primarily, then Fedora), with Feisty being my first Ubuntu version. People, please don't take this the wrong way, but It almost seems like too many changes were made that couldn't be fully tested within the release cycle. I fell in love with linux again after I tried out Feisty, but Gutsy is really bringing back some of that gentoo-ish, always fixing things feeling for me...

Hopefully it's just a few minor fixes, and all will be stable!

---

### Post by brn on 2007-10-23
I upgraded my desktop machine from Feisty to Gutsy and have so far seen only one big problem:  The networked printer is no longer accessible from my laptop which is still running Feisty.  I have yet to see any great advantage in Gutsy and am thinking of doing a clean re-install of Feisty if I can't get network printing for the laptop back..

---

### Post by alf on 2007-10-25
Well... when I execute the "unmount", my MP4 player display image that indicates that the player is connected to a computer.
When I execute the eject, then it returns to the main menu, as it was really disconnected.
So I think that is 'safer' to execute the eject than execute only the unmount.
In 7.04, the default option was 'ejecte'.

---

### Post by donfletcher on 2007-10-25
Does anyone use the database application and try to develop a new database using the wizzard? Mine responds that the Java engine is defective, so get a better Java engine.

I do not know if this is something I should try to do. Might I be better to reinstall 7.04?
I totally cower at the thought of putting in a bug report.

---

### Post by denham2010 on 2007-10-25
> **Melcar said:**
> I also can't seem to change the background color of the splash screen (it just stays at ugly brown no matter what colors I select).

Hi Melcar,

I am having the same issue with the splash screen. has anyone found a fix for that?

The only other issue I have is the first time I open the Gnome Menu, it can take up to a minute to appear. Any time after the first, it appears instantly. Does anyone know what may be causing this?

Thanks.

---

### Post by Happy_Man on 2007-10-25
> **denham2010 said:**
> Hi Melcar,

I am having the same issue with the splash screen. has anyone found a fix for that?

The only other issue I have is the first time I open the Gnome Menu, it can take up to a minute to appear. Any time after the first, it appears instantly. Does anyone know what may be causing this?

Thanks.
That's in the background menu. Down at the bottom, there is a choice to set a color. Set that, and it'll change the background at login.

---

### Post by denham2010 on 2007-10-26
> **Happy_Man said:**
> That's in the background menu. Down at the bottom, there is a choice to set a color. Set that, and it'll change the background at login.

Thanks Happy_Man, unfortunately, that is the problem I am having. Changing that color is having no effect on the splash. I have set all my background colors (wherever I have found them - including the cube background in compiz-fusion) to black, yet the splash screen background remains in the Ubuntu Human theme color.

Any other ideas?

---

### Post by tact on 2007-10-26
> **mortsahl said:**
> For me 7.10 is very slow.  The apearance app just hangs.  I was really looking forward to 7.10 and now I'm sorry I installed it.

It could be due to this issue known back even in feisty...  check it out, adjust your hosts file if needed and see if you experience faster response...

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048)

---

### Post by J@n on 2007-10-26
Tact,

Tx man. That was the (simplest) solution for my box. Response is 4 times faster. And it only took 1 minute to realise this performance upgrade.

J@n

---

### Post by Schapie123 on 2007-10-27
I first did an upgrade, and then a complete reinstall of Gutsy. But in both cases logging off doesn't seem to end sessions properly. Applications have double appearances in the system monitor, and my system switches into snail-mode when I log off and back in. This is a 'big' problem for me, because I use my system both locally, and remotely with NX when I'm at my girlfriend's place. Having to reboot in stead of just logging off after ending a session is really annoying.

---

### Post by dukejib on 2007-10-27
Hi, I am using 7.10 , and haven't found any bug yet, infact it runs better than 7.04.
My system is P4 Company Evo n800v , 512 ram, 1.8 G CPU, dual boot with windows xp.
Only Problem, which I face is when using Firefox, with almost 12-15 tabs opened with lots of graphics, which is same on my windows too.
By the way, I am glad, i dont have to install ntfs3g , it comes packaged.:)

---

### Post by zgoda on 2007-10-27
The fan on my laptop's CPU never stops, the battery takes ages to recharge, CPU never idles. I observed the same with original 6.06. I downgraded to 5.10 and wait until 6.10.
The fonts are displayed blurry, while they was sharp on 7.04.
All that makes me wonder if I should downgrade back to 7.04 and wait for better release.

---

