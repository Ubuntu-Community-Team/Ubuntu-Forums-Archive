---
title: "Can't change icons..."
date: 2006-01-26
forum: Desktop Environments
---

### Post by Garyu on 2006-01-26
Well, I've had some trouble changing icons. I tried the tips at [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694) (great eyecandy howto), and it makes things somewhat better, but not at all good.

So I want to change an icon in my panel. I right-click the icon, select Properties, then I click on the icon image and a very short list of icons pops up. What I can see and change is what exists in one specific /usr/share/icons/subfolder. I can select from a few different icons in this directory, but the subfolder is different between different apps, so the selection is not at all what I want it to be. So I click on Browse... to find my /home/<user>/.icons directory where all of my really nice icons are installed. But when I go to this directory, all of the png's and svg's are greyed out, so I can't change them. :(

I suspect that maybe (and I'm really just guessing now) this might have something to do with the applications being installed/owned by root? No matter, I just want to know how to change my icons. It worked so well in Hoary, why not now in Breezy where everything else works perfectly...? *sigh*

---

### Post by kaamos on 2006-01-26
It's a usability bug. From the browse dialog you have to find the path to the **directory** you want to use items from. Then click ok and you get back to the dialog but no icons are showing. Insert the cursor the line with the directory path and press enter. Now the icons should be visible..

---

### Post by Garyu on 2006-01-26
[QUOTE=kaamos]It's a usability bug. From the browse dialog you have to find the path to the **directory** you want to use items from. Then click ok and you get back to the dialog but no icons are showing. Insert the cursor the line with the directory path and press enter. Now the icons should be visible..[/QUOTE]

*sigh* no wonder I couldn't figure it out... but how could this be a part of Breezy when it was working fine in Hoary? Someone has been messing up their homework. :P

well, thanx anywayz, now I can change icons even though a bug-fix would be in place imo.

---

### Post by Perfect Storm on 2006-01-26
It properly won't fix the bug in breezy, but wait for Dapper.


Here's another tip'n'trick to change your gnome icons and applications:

Find out what the diffrent icons are called you wanna change. Put the new icons in with the same name in the /home/<username>/.icons/<name of the icon theme>/128x128/app


killall gnome-panel to see the changes in the panel.

---

