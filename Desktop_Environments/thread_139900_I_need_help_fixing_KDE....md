---
title: "I need help fixing KDE..."
date: 2006-03-05
forum: Desktop Environments
---

### Post by kitpierce on 2006-03-05
I was tinkering around installing themes and what not (btw, Crystal Window Decorations rocks) and ran into a problem restarting KDE.  My log in would always hang at "Restoring Session."  I followed the directions [here]("http://www.ubuntuforums.org/showthread.php?t=106218&highlight=restoring+session") about moving my /home/username/.kde folder.  This solved my splash screen lock-up problem but created a couple others...

Most notably my keyboard shortcuts for Run Command (Alt+F2) and Katapult (Alt+Space) no longer work.  I  tried using KControl to reset my shortcut for Katapult but it still doesn't work and I never did see how to set my Run Command shortcut back to what it was.

Currently running Breezy with KDE 3.5.  Any ideas?

---

### Post by aysiu on 2006-03-05
This may sound rather extreme, but how about just creating a fresh, new user profile (make sure you make it an admin user)--if you're using KUser, make sure the new user has all the permissions your old user had.

Then, just start using the new user instead.

---

### Post by kitpierce on 2006-03-05
I think that's part of my "problem" actually.  When I moved the old /home/username/.kde folder and logged in as myself again it creates a new, blank user setting.  While this actually had some unintended benefits, I would still need to set up the two previously mentioned shortcuts.

Evidently this is something that isn't standard fare for KDE but rather something that Kubuntu does as a little tweak.  By reverting to a stock KDE profile I have lost the Kubuntu specific shortcuts...  Any ideas on how to restore the original shortcuts?

*thinkout out loud* Would **sudo apt-get remove katapult** followed by **sudo apt-get install katapult** do the trick?  What about the run command shortcut?

---

### Post by aysiu on 2006-03-05
Creating a new user should do the trick.

Removing Katapult won't for two reasons: 1. removing Katapult doesn't remove its settings and 2. I don't think the shortcut that launches Katapult is a Katapult setting.

It sounds as if your user profile is so screwed up it won't even let you modify the KControl settings. Please just create a new user.

If you really like your current username, you can create a new user (with all the same privileges), make sure that new user works. Then, delete your old user, including the user's home folder. Then, finally re-create your old user (with the same privileges).

---

### Post by kitpierce on 2006-03-05
Does it matter that I am currently using the same user ID that I was earlier?  All I did was use the mv command for my kde settings folder and logged in as the same user.

---

### Post by aysiu on 2006-03-05
[QUOTE=kitpierce]Does it matter that I am currently using the same user ID that I was earlier?  All I did was use the mv command for my kde settings folder and logged in as the same user.[/QUOTE] I don't know. Ordinarily, moving settings folders just allows KDE to recreate the settings anew, but it seems as if things are really screwed up, which is why I suggested creating a new user.

---

### Post by kitpierce on 2006-03-05
Duly noted.  I will try the new user suggestion and post results.  Thanks again for the tip.  *crosses fingers*

---

### Post by aysiu on 2006-03-05
I'm crossing my fingers, too...

---

### Post by Mez on 2006-03-07
rm -rf ~/.kde/share/config/katapultrc

---

### Post by Mez on 2006-03-07
or

dcop katapult Katapult showLauncher 

this will load katapult - and then hit ctrl+c and clcik configure global shortcuts

You may not have katapult running - if the above doesnt work - then try running it  (open a konsole and type katapult &

if you need more help - email me

mez (at) thekatapult (dot) org (dot) uk

---

### Post by kitpierce on 2006-03-08
Thanks Mez for the hints.  Unfortunately I had given up and reinstalled Kubuntu, but knowing me I will find a way to mess this up again and I will try your clue.  Thanks again to everyone who helped out!

---

