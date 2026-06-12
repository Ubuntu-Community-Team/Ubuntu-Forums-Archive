---
title: "Can't Find Application in Unity"
date: 2011-05-10
forum: Desktop Environments
---

### Post by MaxCarnage on 2011-05-10
Alright, I just updated to 11.04 today after deciding I couldn't just read about Unity anymore and wanted to experience it for myself. I'll save my thoughts for the Experiences forum; suffice to say that so far I think that it's organized and, for the most part, intuitive.

That said, I am having a problem finding an application that I know is installed. I use Crossover Games to run Steam, and though Steam is running just fine (just played a quick game of TF2 to make sure) I cannot for the life of me find Crossover. In 10.10, it was under Applications > Games. In Unity, it will not show up no matter how I search for it (Steam, however, does with no issues). I have searched for Crossover, codeweaver, cross, code, games, etc, to no avail.

Any tips or comments on how I may find this application? It shows up in my Installed Software in Software Center even! Argh! :)

---

### Post by WthIteh on 2011-05-11
The Dash uses .desktop files for showing installed/searched files/apps.
So first find the .desktop file of your application which just like prior versions is (probably) under /usr/share/app-install/desktop folder.
Then try to search for that name in the Dash to find it there :)

---

### Post by MaxCarnage on 2011-05-11
Thanks; that helped!

---

### Post by Light-kun on 2012-05-02
Hi.
Your answer didn't helped.
I see many apps here: /usr/share/app-install/desktop 
But still can't find them in Alt+f2, Super or Alt search bars.

For example,  I have these rows:
-rw-r--r-- 1 root root 1.2K Apr 17 19:36 abiword:abiword.desktop
-rw-r--r-- 1 root root  271 Apr 17 19:38 zatacka:zatacka.desktop

tried to search "abi", "word", "zata", "zatacka".

---

### Post by ravisghosh on 2012-05-21
> **WthIteh said:**
> The Dash uses .desktop files for showing installed/searched files/apps.
So first find the .desktop file of your application which just like prior versions is (probably) under /usr/share/app-install/desktop folder.
Then try to search for that name in the Dash to find it there :)

I just installed GIMP and i got .desktop file for it in the said folder, but it simply would not show up in unity menu. However, it does show up if I log in GNOME.

---

