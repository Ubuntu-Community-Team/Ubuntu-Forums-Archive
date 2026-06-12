---
title: "Blocked Desktop (Gnome)"
date: 2008-09-18
forum: Desktop Environments
---

### Post by nahuel_89p on 2008-09-18
Hi people, I installed the app "ubuntu tweak" to customize my desktop, among other things that aren't really important.
The point is that suddenly, my icons on my desktop disappeared. Besides, my desktop has another worrying symptoms: it doesnt response to the right-click, which means that the right-click menu isn't displayed...
Also, I can't drag and drop any icon from a folder to my desktop, it just "rebounds". Lastly, I cant make any selection with my pointer, by saying this i mean that the classic square that is drawn every time you hold the left click and move the pointer isn't shown.  
Summarizing, my desktop is blocked.
I restarted everything i modified with the tweak app, but the desktop is still blocked. I think that the last drop was the activation of the option "nautilus with root privileges) or "nautilus with wallpaper". I deactivated both, but nothing comes to normal.
The bar (panel) in my desktop works ok. Screenlets works ok too, and i clarify that im currently working with emerald and compiz.
What do you suggest?

P.d: I can see my icons in the "desktop" folder.

Thanks in advance! And sorry for my english, i hope you understood everything i wrote, I'm Argentinian.

---

### Post by forger on 2008-09-18
type in terminal: nautilus

does it show any output?

---

### Post by nahuel_89p on 2008-09-18
No, i only get a nautilus windows, as expected.
Btw, i tryied "gconf-edit" and checking if the "gnome draws desktop" value was activated, and it was.
Thanks for the quick answer.

---

### Post by forger on 2008-09-18
You could do the following:
1) ```
killall -9 nautilus
nautilus
```
if it doesn't fix it, try solution (2)

2) **[COLOR="Red"]WARNING: This solution can lead to problems and loss of data! It comes with no warranty![/COLOR]**
Backup nautilus preferences:
```
gconftool-2 --dump /apps/nautilus/preferences > $HOME/nautilus-backup.xml
```

Unset nautilus preferences, reinstall nautilus and restart gnome:
```
gconftool-2 --recursive-unset /apps/nautilus/preferences
sudo apt-get install --reinstall nautilus
sudo /etc/init.d/gdm restart
```

If anything goes wrong, you can restore your nautilus:
(Note: If you *can't load terminal*, press **CTRL-ALT-F1** and login)
```
gconftool-2 --load $HOME/nautilus-backup.xml
sudo /etc/init.d/gdm restart
```

---

### Post by nahuel_89p on 2008-09-18
When I enter "killall -9 nautilus", i only get a nautilus windows, just as if i would have written "nautilus" instead.

Regarding the solution 2... it seems to radical for what i suspect is a simple (mis)configuration problem. Anyway thanks for your help, i will do it in case I dont come up with a safer solution.

Any other suggestions?

---

### Post by forger on 2008-09-18
I just put that banner in case some newbie comes along and starts experimenting. Plus, I don't want to feel responsible if anything does go wrong.
The 'data loss' I'm referring to is the customisation of nautilus, such as the width of the panes or the customised values menu edit > preferences.

If you ask me, you were actually going radical by using unverified (i.e. not in ubuntu repositories) applications such as ubuntu tweak.. you've actually done damage just by using ubuntu tweak, so sometimes radical fixes radical :)

And it's really not that radical, all you do is to remove all your customised preferences for nautilus, which nautilus will reconfigure once you restart gnome desktop and login.

The above command was tested twice by myself and does revert the preferences to the default ones. But as always, I give no guarranties :)

---

### Post by nahuel_89p on 2008-09-18
Ok, you convinced me and I've just done it, but my desktop is still blocked.
You are right when you say that I shouldn't have installed tweak.
My nautilus preferences are just like before, everythings fine... buy my desktop has no solution...
do you think that i should try to post this in the Desktop Effects & Customization category?

---

### Post by forger on 2008-09-18
Well I would choose the "General help", you could get more replies that way :)

I have one more suggestion:
**[COLOR="Red"]WARNING: This solution can lead to problems and loss of data! It comes with no warranty![/COLOR]**

Backup the nautilus config folder:
```
mv $HOME/.nautilus $HOME/nautilus-backup
```
Backup the whole nautilus gconf tree:
```
gconftool-2 --dump /apps/nautilus > $HOME/nautilus-backup-all.xml
```

Unset nautilus preferences, reinstall nautilus and restart gnome:
Code:
```
gconftool-2 --recursive-unset /apps/nautilus
sudo apt-get install --reinstall nautilus
sudo /etc/init.d/gdm restart

```

This will reset everything related to nautilus in your username account, let's hope this fixes it :)


If anything goes wrong, you can restore your nautilus:
(Note: If you can't load terminal, press CTRL-ALT-F1 and login)
Code:
```

mv $HOME/nautilus-backup $HOME/.nautilus
gconftool-2 --load $HOME/nautilus-backup-all.xml
sudo /etc/init.d/gdm restart
```

---

### Post by nahuel_89p on 2008-09-18
Nothing. The only difference is that at the very beggining, when the desktop is just loading, i can see for a second the hard drive icons (i had set them invisible before), plus my icons, but now placed in the default order, at the left side of the screen (i had  them placed at the right side).
My icons are still there, in the "desktop" folder.
My desktop is still blocked.

I'm afraid this is serious... but the fact that at the begging i can see the icons for a second, doesn't tell you something else?

---

### Post by forger on 2008-09-18
Hm.. seems ubuntu-tweak has a process that sets the nautilus configuration back to ubuntu-tweak's own custom values? :confused:

Can you purge ubuntu-tweak?
```
sudo apt-get purge ubuntu-tweak
```

Then restart gnome:
```
sudo /etc/init.d/gdm restart
```

If it's not fixed, try the commands from the previous post again

---

### Post by nahuel_89p on 2008-09-18
I've uninstalled ubuntu-tweak using synaptic, and i did it two reboots ago.
I posted this in "general help". I hope trovald linus reads it hehe.

btw: when I restart gnome using  "sudo /etc/init.d/gdm restart" the bash (dont know how to say... the black screen with white characters) do some stuff for a few seconds and the i have to reboot manually because the bash just stops doing process, and allows me to write, but without a prompt.
I don't think is big deal because everything restarts ok after rebooting manually.

---

### Post by forger on 2008-09-18
> **nahuel_89p said:**
> I've uninstalled ubuntu-tweak using synaptic, and i did it two reboots ago.

So you uninstalled using "remove completely" in synaptic?
Otherwise, do the apt-get purge command :)

Other than the above, I don't know how to help you further, maybe someone else knows :)

---

