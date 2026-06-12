---
title: "Upgraded to Jaunty and now Firefox doesn't work"
date: 2009-05-13
forum: General Help
---

### Post by ninjaaron on 2009-05-13
It pops into the application bar that it's starting, then it thinks for a little while, then it disappears.

---

### Post by Maheriano on 2009-05-13
> **ninjaaron said:**
> It pops into the application bar that it's starting, then it thinks for a little while, then it disappears.
Happens to me A LOT. I had to go into synaptic and completely remove everything associated with it, then reinstall it and now it works. Most of the time. Happens on my desktop which was an upgrade and is still on EXT3 and the other was a fresh install on my Dell laptop which is EXT4.

EDIT - I should mention it doesn't happen on my desktop, ever. Just the laptop.

---

### Post by albert ozzy on 2009-05-13
1-) System > Administration > System Monitor > Processes(tab) - End all processes containing word "firefox"
---try to start it now. if it doesnt work:
2-) run firefox in safe mode with this command: 
> firefox -safe-modeThis'll work if the problem's caused by an addon or wrong config file.if it doesnt work:
3-) Go to home> .mozilla > firefox. This is where firefox stores your profile if you didn't change it. It should be a directory with a random name (e.g: ashdadfad.default) Make a backup of your profile directory (Cos it contains all your bookmarks,passwords,history,addons etc.) Then delete the folder. Again make a backup or you will lose all your bookmarks and passwords.
---try to start now

---

### Post by ninjaaron on 2009-05-13
Ok, that safe-mode thing worked, and I'm now posting from firefox. Will it open normally now, or am I stuck using safe-mode indefinitely?

---

### Post by sir_nasty on 2009-05-13
it just confirms that either your config file or one of your addons is causing the issues, now go into manage the addons and possibly remove 1 or 2 and test it...

---

### Post by ninjaaron on 2009-05-13
I have a feeling it's the config file. It was doing some weird stuff with the display before I upgraded (taking up the whole screen, so I had to use other workspaces to do stuff).

Anyway, I can't seem to find this config file.

I looked in "~/.mozilla/firefox" and I checked the 'profiles.ini'

Didn't seem to be anything significant there, and I'm not sure where else to look.

...

Ok, Also tried removing the folder that profiles.ini refers to, and that didn't work either (I've put them back, by the way).

safe-mode is still working, but I can't use youtube. :mad:

(or any java movies, I presume)

---

### Post by evilbuntu on 2009-05-13
i had the same problem on 8.04 and always had to end process.

nothing i did fixed it, and it wasnt an add on.

unfortunatley from my reading its some kind of bug and sometimes reverting to an older firefox (which you cn probably scrounge up somewhere) can fix it but i never go that far with it. my 9.04 upgrade settled it out.

---

### Post by zaurus on 2009-05-14
I also upgraded and have a different problem.
I cannot bookmark anything, cannot use back, forward, reload org home function. If I start it as a root from command line it works normally.
Any suggestion as how to fix this problem?

KR

---

### Post by albert ozzy on 2009-05-14
@zaurus: If you dont have permission to write into your profile directory that can be the issue. Check your profile folder's location and permissions. You can check profiles.ini file mentioned above or you can use firefox profile manager> firefox -P

For the problem above: firefox also stores some addons in /usr/lib/firefox-addons/extensions .Ubufox extension (located there) caused some problems in some of my installation.Please check and see if it helps.

---

### Post by zaurus on 2009-05-14
> **albert ozzy said:**
> @zaurus: If you dont have permission to write into your profile directory that can be the issue. Check your profile folder's location and permissions. You can check profiles.ini file mentioned above or you can use firefox profile manager

For the problem above: firefox also stores some addons in /usr/lib/firefox-addons/extensions .Ubufox extension (located there) caused some problems in some of my installation.Please check and see if it helps.

Thanks! I just created a new Default User profile and it works.
Still cannot understand why it did not work with the default profile, permissions were OK.

KR

---

