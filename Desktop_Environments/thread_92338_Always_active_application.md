---
title: "Always active application"
date: 2005-11-19
forum: Desktop Environments
---

### Post by rockz on 2005-11-19
How i make a application always active, this app isn't minimize when i click in "show desktop" button like gdesklet, i need to run this app like gdesklet always on desktop never minimized. How i do this?

---

### Post by taurus on 2005-11-19
Are you talking about running weather with gdesklets???  If that's the case, you need to install a weather applet first before you can call it...  Head over to http:/gdesklets.gnomedesktop.org and check out those applets.  Otherwise, you can install a few that comes with Breezy,

sudo apt-get install gdesklets-data

---

### Post by rockz on 2005-11-19
No... i dont need run gdesklet but run a application (conky) like the gdesklet (always show on desktop)

---

### Post by taurus on 2005-11-19
Yes, I know what conky does because I have it running on my Fluxbox too.  Now, I don't understand your question at all...  What do you mean by minimizing app?  You are not talking about conky, are you?

---

### Post by rockz on 2005-11-19
Yes, I talk about conky, to run it in gnome i need to use a new window to conky (conky -o) and when I minimize all apps (show desktop button) conky is minimized too, and o need that conky is not minimized with other applications.

---

### Post by taurus on 2005-11-19
Do you happen to run nautilus with your Gnome???  I believe you are because you are using -o with conky since it requires it own window...  What happens if you just run conky by itself but do all your settings in ~/.conkyrc???

---

### Post by rockz on 2005-11-19
When i run conky without -o all icons on desktop disappear. If icons dont disappear all my problems are solved too, because without -o conky isnt minimized.

---

### Post by taurus on 2005-11-19
Are you running nautilus with your Gnome???

---

### Post by rockz on 2005-11-19
Yes i run nautilus with my gnome. Can i have icons in desktop without nautilius?

---

### Post by taurus on 2005-11-19
If you plan to run nautilus, then you must set it in your ~/.conkyrc for it to have it own window...  Look for a line that says 

# Create own window instead of using desktop (required in nautilus)
own_window no

and change it to yes.

Yes, you can have icons on your desktop without running nautilus.  You can use idesk to do that....

---

