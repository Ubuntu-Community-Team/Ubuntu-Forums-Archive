---
title: "Update manager"
date: 2006-06-18
forum: Desktop Environments
---

### Post by christooss on 2006-06-18
When I start Ubuntu Update manager doesn't check if something new happend in repositories. There were changes so..

What to do? I have expirienced such problems in breezy to but when I was on dapper beta it worked perfectly

---

### Post by mlind on 2006-06-18
[QUOTE=christooss]When I start Ubuntu Update manager doesn't check if something new happend in repositories. There were changes so..

What to do? I have expirienced such problems in breezy to but when I was on dapper beta it worked perfectly[/QUOTE]

Is update-notifier process running and /etc/apt/sources.list populated (not-empty) ?

```

ps -A | grep update-notifier

```

---

### Post by christooss on 2006-06-18
yes to both questions :(

I will check again tomorow if update-notifier starts

---

### Post by christooss on 2006-06-19
Update-notifier starts at boot but it doesn't work

Today there was one update   acpi-support but update notifier didn't recognised it

---

### Post by FredB on 2006-06-19
I noticed that update manager is kinda idiot. I made a daily sudo apt-get update followed by a sudo apt-get dist-upgrade in order to be up-to-date.

---

### Post by Moebius on 2006-07-03
I'm also experiencing this problem.

To see if there is an update available, I have to go to System -» Administration -» Update Manager

There I have to press check for it to finally find some updates.

Was the method used in Breezy changed when Dapper was released? Shouldn't it always check all the "un-comented" entries in the source.list?

Further notes, Yes the update-notifier daemon is running on startup, Yes my sources.list has the appropriate permissions and is populated.

---

### Post by warjowuch on 2006-08-02
Hello there,
I have the same handicap on my install. update-notifier loads, sources.list had read permissions for root, group and others (should be enough, shouldn't it?) but it does not check for updates...
Any solution? It would be appreciated, otherwise I'll just remove it, it would be senseless to use/load it when it does not work.

Greetings!

---

### Post by mgmiller on 2006-08-03
Same problem here.  It recently just stopped working.  It still works on a clean install of Dapper on another machine I have.  But on my Breezy to Dapper upgrade, it does not.  I just tried using synaptic package manager to do a reinstall of both the update-manager and update-notifier packages.  We'll see if that helps.

---

### Post by Statik on 2006-08-04
I've been having the same problem, update-notifier not running on boot, even though I added it to the sessions startup list. So I  thought I'd try re-installing . . . funny thing, it wasn't even installed anymore. Weird. I'll see if it works next reboot.

Statik

---

### Post by roman_PL on 2006-08-05
Same to me. Not working on my home machine (upgrade from badger), working fine on my other computer (clean install). Maybe it's time to fill buglist for u-n?

---

