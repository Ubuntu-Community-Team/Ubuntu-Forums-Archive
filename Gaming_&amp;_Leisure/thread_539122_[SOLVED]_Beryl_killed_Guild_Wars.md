---
title: "[SOLVED] Beryl killed Guild Wars"
date: 2007-08-30
forum: Gaming &amp; Leisure
---

### Post by blakecraw on 2007-08-30
Ok this is completely beyond me so I came here for some help.

I have been running GW via wine for a couple months, and it has worked perfectly. Today, I decided to try to run GW with Beryl as my active window manager, and it didn't work. Ok, no big deal. However, when I now try to run GW with openbox, or any other window manager, it gets to 100% then crashes.

I haven't changed a single thing manually, so does anybody know what could have happened and more importantly how to fix it?

I don't want to download a new Gw.dat file unless that's the last possible option, since I'm on a university network and I have limited bandwidth for the semester, which I don't want to burn through.

blakecraw

---

### Post by Tyke91 on 2007-08-30
i had the same problem, unfortunately, the only solution i found was to do a re install/download.

if you have your cd, it would help to install from that i guess (dunno... the cd should have major zones like ascalon and things pre-loaded)

if you found a way to torrent it, would taht save you bandwidth?

---

### Post by Ferrat on 2007-08-30
> **blakecraw said:**
> Ok this is completely beyond me so I came here for some help.

I have been running GW via wine for a couple months, and it has worked perfectly. Today, I decided to try to run GW with Beryl as my active window manager, and it didn't work. Ok, no big deal. However, when I now try to run GW with openbox, or any other window manager, it gets to 100% then crashes.

I haven't changed a single thing manually, so does anybody know what could have happened and more importantly how to fix it?

I don't want to download a new Gw.dat file unless that's the last possible option, since I'm on a university network and I have limited bandwidth for the semester, which I don't want to burn through.

blakecraw

If you don't want to waste your band then just go to a either openconnection place if you got one near, a internet café or similar and see if you can't get a hold of a install disk online or backup, since it's free to download that shouldn't be a problem?

Don't know much about GW acctually just installed it (like an hour ago to try out)  but I know I always had 2-3 backups of WoW when I played since big crashes often corrupted the MPQ files and required a reinstall. 

And if you do get a hold of it, back up the first thing you do ;)

---

### Post by Polygon on 2007-08-31
you can try repairing your gw.dat file, using this command

according to the site i got this from,** THIS CAN TAKE A LONG TIME**

```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -repair
```

---

### Post by blakecraw on 2007-08-31
I guess I'll have to get the install discs mailed to me, since I left them at home when I moved. Fortunately that will save a big chunk of the downloading. 

Thanks for the suggestions, I'll post more info in a week or so after I've tried that.

---

### Post by dorath on 2007-08-31
> **Tyke91 said:**
> i had the same problem, unfortunately, the only solution i found was to do a re install/download.

Same here. :-\

---

### Post by gundumfx on 2007-08-31
> **Polygon said:**
> you can try repairing your gw.dat file, using this command

according to the site i got this from,** THIS CAN TAKE A LONG TIME**

```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -repair
```

this code is  good it worked

---

### Post by blakecraw on 2007-09-08
EDIT: In my haste to test it out after reinstalling from the cds I forgot the -dsound argument, so I thought it didn't work at first

It works again! (after reinstalling from the cds, -repair didn't help)

thanks for the help,

Blake

---

