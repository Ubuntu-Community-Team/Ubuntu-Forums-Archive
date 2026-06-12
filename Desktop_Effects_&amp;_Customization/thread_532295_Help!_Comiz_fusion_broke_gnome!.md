---
title: "Help! Comiz fusion broke gnome!"
date: 2007-08-22
forum: Desktop Effects &amp; Customization
---

### Post by Killerah on 2007-08-22
Hey guys, I've been using beryl for a long time and love it (and before beryl came out I was using compiz), and then I read about compiz fusion on digg.com and I thought "oh sweet! It's the best of both worlds! I've gotta try it!". So I the CF installer-updater thread, snagged the file, ran it, and it didn't work. Bum rap, so I uninstall that, and then I try the method described in this thread [http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+fusion) and lo and behold it actually works (and faster than beryl did)! I'm still logged in and I get bored of the default compiz window style so I want to make it work with emerald. And the only way I could see that would make that work would be to create the options that make compiz and emerald start when I logged in to gnome. So I did that and I logged out, I try to log back in to my gnome-xgl session and it doesn't even log in! It comes up with some error message that says "session lasted less than 10 seconds" and then when I click ok it goes back to the gdm login. I checked if gnome without xgl would work, and it did for a while, but now even that doesn't work, and I'm stuck using kde without xgl which I'm not a big fan of. 

So any help would be greatly appreciated, I just want my gnome to work like it used to (and preferably with compiz fusion).

Thanks
Nate

---

### Post by Chymera on 2007-08-22
have you tried recovery mode?
In the worse possible scenario you could go delete compiz and emerald in kde and then revert to gnome, if that doesnt do it delete the gnome components altogether and reinstall them (like going kubuntu, and back :-P )

---

### Post by Killerah on 2007-08-22
Recovery mode gets farther than regular gnome, but I can't even see the bars that go on the top and bottom of the screen. I've tried the compiz and emerald thing which didn't work, maybe reinstalling gnome will do the trick.

---

### Post by jimbo99 on 2007-08-22
I can't offer any help but I can offer condolences.  The latest couple of compiz-fusion are really borked.  Not sure what they are doing there at the project.  It looks like they took a compiz focus when I think their focus should have been on the beryl side of things.

Yeah, it has those plugins and they are nice.  There are a slew of issues though that I don't think would have gotten through if they focused on Beryl as the main architecture.

Have you tried this command at the run prompt?

compiz --replace -c emerald &

---

### Post by Killerah on 2007-08-23
Hmm, well I reinstalled gnome, restarted and I can get into gnome even with XGL running (with a little glitchyness at start up), but as soon as I try that command it wigs out and my x session gets restarted and I get put back at the gdm screen again.

---

### Post by Killerah on 2007-08-25
Ok, now I can't even get into gnome OR kde! I can get to gdm or kdm, but not past them. When I try to login my screen flashes a couple of times and turns off, I can't switch to other sessions by pressing alt+f1-6 or anything like that, I can't do anything but hold down the power button and wait for my machine to turn off. All I did to get here was uninstall and reinstall compiz. Does anyone know how I can restore proper function to my ubuntu installation?

---

### Post by Killerah on 2007-08-27
Anybody? Anybody?

---

