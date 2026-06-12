---
title: "[SOLVED] I need dock apps to build a sort of panel in Openbox"
date: 2007-07-25
forum: Desktop Environments
---

### Post by jdackle on 2007-07-25
I originally posted this in [another thread]("http://ubuntuforums.org/showthread.php?t=509474") in the wrong section: "Desktop Effects & Customization".
I then realized not only was it posted to the wrong section I'd also NOT get the answers I need... :(

So, here's basically the original post:

I'm using **Openbox+ROX-Desktop** on Dapper Drake (6.06.1)

This is the essential stuff I need for my Dock which is to function as a panel:
1. Workspace switcher
2. Taskbar (with good visibility; my eyesight isn't perfect... lol)
3. System-tray (GNOME and KDE compatible)
4. GNOME-like (in terms of content) Menu (possibility of having a "Places" menu greatly apreciated :) )
5. Clock (possibly with calendar, but not essential).

Again, all of this as **Dock-apps**!
All suggestion are very welcome! ;)
**And I need those dockapps** to
1. Be **fast and light**;
2. Work with **Openbox's Dock**.

And if you can't suggest a good dockapp to the effects, web-listings such as [dockapps.org]("http://www.dockapps.org/") will be most welcome as well. :)

Thanks! :)


P.S.: In case you're wondering where I'm coming from with this, check [this thread]("http://ubuntuforums.org/showpost.php?p=3063117&postcount=6"). Thanks! :)

---

### Post by kerry_s on 2007-07-25
if those are your requirements, your using the wrong wm, you should go for icewm, it has all those, you can use rox for the file manager, background & desktop icons. You don't have to install anything else to complete it, it will be smaller & faster than openbox with a third party panel or dockapps. 

ayusha (did i spell that right) is a big icewm user and can help you get the setup you want. She also has a nice how to, to get a trim icewm install> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by kerry_s on 2007-07-26
here's what it would look like.
i used->
sudo apt-get install icewm icewm-common icemc

i haven't done nothing but change the theme & start the apps i had in fluxbox.

---

### Post by RedSquirrel on 2007-07-26
You might want 'icewm-themes' as well. Some of them look pretty nice. :)

---

### Post by kerry_s on 2007-07-26
> **RedSquirrel said:**
> You might want 'icewm-themes' as well. Some of them look pretty nice. :)

bloatware :) , most of them suck, better to just grab one you like from freshmeat or the icewm site, why waist 18.5mb on themes you won't use.

Hey redsquirrel, i told you i could put that desktop on anything and it would look the same. you wouldn't even know i was using icewm unless i had the taskbar up. i have it on auto hide, it looks exactly like my fluxbox & and uses exactly the same resources.

---

### Post by RedSquirrel on 2007-07-26
> **kerry_s said:**
> bloatware :) , most of them suck, better to just grab one you like from freshmeat or the icewm site, why waist 18.5mb on themes you won't use.

... because it's fun just clicking through all of them (if you can spare the disk space). I agree with you that it is bloat and doesn't conform to our policy of only installing the things we actually use. ;)


> **kerry_s said:**
> Hey redsquirrel, i told you i could put that desktop on anything and it would look the same. you wouldn't even know i was using icewm unless i had the taskbar up. i have it on auto hide, it looks exactly like my fluxbox & and uses exactly the same resources.

Yeah, that's pretty cool. :)

---

### Post by jdackle on 2007-07-27
Thank you so much to both of you, kerry_s and RedSquirrel! :)

And even more specially to kerry_s who, sorry RedSquirrel but it's true, kerry_s has been my saviour in this whole light and fast WMs/DEs deal! :D


So... I did install IceWM. Only I added the following packages to the list kerry_s gave:
- iceme (another menu editor; has pros and cons compared to icemc)
- icepref and iceconf (general icewm configuration; though I actually ended up editing the ~/icewm/preferences file manually... lol)

I later did install, following RedSquirrel's tip, icewm-themes and I msut say I thought some of them were pretty awsome! ;) I specially liked aeteria but later chose 18k as it's still beautiful though much much simpler and rather fited my "plans".
After reading kerry_s's post on the package size... Well I removed icewm-themes, stuck with yellomotif (from the default list) and downloaded 6 other themes from freshmeat (including aeteria and 18k, plus a few Ubuntu-Human like themes). I haven't unpacked them yet though, will do when I get the time to actually contemplate and make a choice... ;)

Thanks so much for your help. Yes, IceWM+ROX-Desktop are fast! 8-)

This ["HOWTO: Setup Icewm with Rox-Filer" thread]("http://ubuntuforums.org/showthread.php?t=171203") by Peter76 also helped me a lot to get started and tweaking a few things.
The system's not exactly as I want it yet but it's perfectly functional and will have to do til I get more spare time.

Again, thank you both! :)

---

### Post by kerry_s on 2007-07-27
ah finally, you found something that works. remember icewm themes go in ~/.icewm/themes ,you create it, here i was trying to put it in ~/.themes & wondering why it wasn't working.  also for easy unpacking grab "unp" it can unpack anything easy you just hit> shift+! < and type> unp (first few letters & tab to auto complete). real easy. I'm still playing with it, so let me know if you need help with something.

here's the usual pics, i'll put the bar out, but it's set up to autohide & pops up when you move to the bottom of the screen.

---

### Post by RedSquirrel on 2007-07-28
> **jdackle said:**
> kerry_s has been my saviour in this whole light and fast WMs/DEs deal!

You're in good hands. kerry_s is a master of lightweight installs. :)

---

### Post by kerry_s on 2007-07-28
> **RedSquirrel said:**
> You're in good hands. kerry_s is a master of lightweight installs. :)

i think your far better than me, at least you take the time to compile yours. i simply refuse to compile, never was any good at it anyways, but i still do believe if speed is your true goal, compiling to your system is the best option. to me it's more work for just that little bit of kick and not worth it on anything 300mhz 128ram and up, it's already fast enough you barely notice the difference. :lolflag:

---

