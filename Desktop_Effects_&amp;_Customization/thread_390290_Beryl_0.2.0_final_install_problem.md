---
title: "Beryl 0.2.0 final install problem :/"
date: 2007-03-21
forum: Desktop Effects &amp; Customization
---

### Post by herbster on 2007-03-21
I am currently using "Version: 0.2.0+svn20070216-r4103+3v1ubuntu0" (from Terminal), which I downloaded a while ago and it has been working fine for some time with the usual minor things, so I saw the .2.0 final released and would like to upgrade. What I did is:

1. Go to Synaptic and completely uninstall all installed Beryl and Emerald packages
2. Install Beryl and Emerald via sudo apt-get install

Then I rebooted for good measure, logged into my XGL session, load up beryl-manager and click Beryl as window manager, and nothing happens except for my window title bars disappear. Also, when I open up the Beryl Settings Manager from the diamond icon on the tray, I ONLY get General Options, no window management, desktop, 3d effects, extras, etc. JUST "General Options." Very strange.

Then, I uninstalled it after 3 tries and the same results, reinstalled the 0.2.0svn I had been using and it is working fine. But, it was exactly as I had left it i.e., all settings, caps, skydome etc intact, so I'm wondering if I perhaps hadn't "completely" removed Beryl, or if it's just that my settings file was left alone and it's no big deal?

Someone please help!!! :(

---

### Post by Waappu on 2007-03-22
Hi

Try this to uninstall ```
sudo aptitude remove --purge-unused beryl emerald emerald-themes
rm -r ~/beryl
rm .beryl-managerrc
```

and re-install with command```
sudo aptitude install beryl emerald-themes
```

---

### Post by old_geekster on 2007-03-23
Install "Automatix Bleeder" and install Beryl from it.  It worked perfectly the first time for me.

Add this to your /etc/apt/sources.list:

#AUTOMATIX BLEEDER REPOS START
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
#AUTOMATIX BLEEDER REPOS END

---

