---
title: "alt tab across desktops?"
date: 2006-06-07
forum: Desktop Environments
---

### Post by hotani on 2006-06-07
Is this possible? Why would I want to be locked out of the other desktops when I alt-tab? Hopefully I'm missing a setting somewhere. It just seems that if I choose to 'show windows from all workspaces' in the Window List prefs that it would activate for alt tab as well.

I'm used to my desktop switcher in OS X that would 'see' all apps open across desktops when alt-tabbing. Actually, don't read into that too much - the desktop switcher had nothing to do with it, but it would not interfere with the default OS X behavior during alt-tab. However, it would stay true to the apps' locations and native desktops which was nice. 

Usually when I'm working, I'll have several apps open across desktops - then alt tab to all of them from anywhere. In Ubuntu, I can't do this so usually (unfortunately) end up working with everything in "Workspace 1." :(

---

### Post by AModlin on 2006-06-07
If you install XGL I know that the Alt-tab will tab across all desktops, along with quite a few other nice organization features.

---

### Post by hotani on 2006-06-07
Sweet, where do I go to switch this on?

j/k

If I ever have time to mess with it (here at work), I'll set it up. Good to know the capability exists.

---

### Post by AModlin on 2006-06-07
Here you go: 
[http://doc.gwos.org/index.php/EyeCandyDapper](http://doc.gwos.org/index.php/EyeCandyDapper)

---

### Post by hotani on 2006-06-07
Well, I gave it a shot... (work shmerk).

Nothing happened. Pretty much what I expected. Here's what I did get out of it: [my lock screen function stopped working again!!!](http://www.ubuntuforums.org/showthread.php?t=191317) SWEET!

guess i'll go back and "open a terminal window...." Jeez, I hope no 'normal people' ever try to do this stuff. Yikes.

Scratch that - I got it, just needed to reboot rather than restart GDM. However... Back to the original issue: I now only have one desktop. That's right, I can't switch desktops AT ALL now. *sigh*

---

### Post by hotani on 2006-06-07
XGL/Compiz: I give up.

I started this about 5 hours ago and after about 15 reboots, more ctrl+alt+backspaces than I care to count, I'm throwing in the towel. I went in and commented out everything in the gdm.conf-custom file so now at least Firefox is usable and I have all 4 desktops back.

Holy. Fawking. Hell. What a waste of time.

---

### Post by hotani on 2006-06-08
Day 2: decided to take another shot at it, and now (knocks firmly on desk) everything seems to be working correctly. 

My problem was that I had enabled compiz via synaptic and was using XGL. At one point yesterday I realized I should be using the aiglx stuff, and set that up but did not reinstall the compiz which is set up to work with aiglx. Once I did that today, and messed with some configs, I got it all going.

Long process to go through, but I can now alt-tab between desktops! :D

NOTE: this is not the default behavior of the 'switcher' plugin in Compiz. You have to 1st make sure the box is checked that reads "all desktops." Then you need to go to shortcuts -> plugins -> switcher and change <Control> to <Alt> for it to default to all desktops, otherwise you would have to contort your hand to hit alt+ctrl+tab to get all of them in there.

So as you can tell, I was a bit frustrated yesterday with this, but now that it is up and running I can say it was worth it in the end - very cool stuff.

---

### Post by hotani on 2006-08-31
Bumping this because I still haven't found a good non-compiz way to do this.

For a variety of reasons (please don't get me started), I do not want to run Compiz. Is there some other way to alt-tab across desktops? I think multiple desktops is truly wasted without this feature. Am I the only one who thinks this?

---

### Post by imaiden22 on 2006-08-31
call me simplistic, but i chose to take advantage of using multiple desktop simply by giving shortcuts to each individual desktop (f9-f12) and i have a torrent workspace and a media workspace and an internet browsing workspace and it suits me just fine...i like to reserve my alt-tab for switching programs in the current desktop and not to mention i almost hung myself trying to get xgl/compiz to work, but im not going down that dark road for a while...safe to say thats my suggestion!

---

### Post by hotani on 2006-08-31
I may have to do that. A single key mapped to each desktop would make the switch a tad easier. 

However, I would like to treat all the desktops like one big one, and keep things spread out - alt-tabbing between apps when necessary without the extra step of switching desktops. It seems like this would be a natural use of the multiple desktop system, but apparently the gnome folks don't see it that way.

---

### Post by christhemonkey on 2006-08-31
> **hotani said:**
> I may have to do that. A single key mapped to each desktop would make the switch a tad easier. 

However, I would like to treat all the desktops like one big one, and keep things spread out - alt-tabbing between apps when necessary without the extra step of switching desktops. It seems like this would be a natural use of the multiple desktop system, but apparently the gnome folks don't see it that way.


Ctrl+Alt+left_arrow_key changes to left hand workspace
Ctrl+Alt+right_arrow_key changes to right hand workspace

There are more shortcuts like that, but i forget them.

---

### Post by hotani on 2006-08-31
yeah I know about those - and use them to switch between desktops. But what I really want is to be able to have all open apps in all desktops show up in the alt-tab box instead of just the ones in the current workspace.

---

### Post by it.henrik on 2006-08-31
so what you want is a huge virtual desktop  :)
if you have a monitor with a resolution of 1600x1200 .. you can set up a virutal desktop that is (1600x4)x1200 and now you would have a desktop that is 4 times as wide as your screen.

In this way you can alt+tab through all your windows

---

### Post by skroops on 2007-12-19
bumping this because I would like to do this as well, and there was never a solution.

is there a way to alt-tab between all applications regardless of the desktop they are on without using compiz?

---

### Post by hotani on 2007-12-19
After all that, the best non-compiz way I found was to use a different window manager. Xfwm4 will span all desktops and can be used with gnome. Or you could just use Xubuntu.

---

