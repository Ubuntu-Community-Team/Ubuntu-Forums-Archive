---
title: "kde-fluxbox problem"
date: 2005-11-29
forum: Desktop Environments
---

### Post by alvid on 2005-11-29
After installing fluxbox I can not get back to kde. On the logon screen I mark kde to run and get the following messages:
'Starting up interprocess communications'
'No write access to /home/al/.iceauthority kde is unable to 
start dcopserver'
'Could not start ksmserver-ck your installation'
I can get at kde via iterm in fluxbox but half of the apps.do
not run.
I am just starting to learn Linux and fluxbox is over my head at this point.
Any detailed help would be appriciated.
Al.

---

### Post by shakin on 2005-11-29
Try running this:
```

rm home/al/.iceauthority

```

Then relogin to KDE.

---

### Post by alvid on 2005-11-29
Does not work. When i run rm home/al/.iceauthority no such file or dir. Even tried putting ice in caps?? and tried the command in kde while in fluxbox.

---

### Post by ace2005 on 2005-11-29
Go into fluxbox, open a terminal run "sudo konqueror" now navigate to you're home directory, the do View > Show Hidden Files, now select all of them and right click > properties, go into the permissions tab and try setting them all to "Can View & Modify Content"

That should do it

---

### Post by alvid on 2005-11-29
Thanks for your patience, but now I can not get into kde or konqueror with out getting 'error: /tmp/ksocket-alor id hi is owned by uid 1000 instead of uid 0' and numerous other errors. Maybe I will just delete my kubuntu partition via qtparted and start over. If I delete the partition will I still be able to boot into my windowsxp partition????
Thanks,
Al.

---

### Post by shakin on 2005-11-30
I mis-typed. Try this:

```

rm /home/al/.iceauthority

```

Assuming 'al' is your username.

---

### Post by alvid on 2005-11-30
Thanks for trying but suggestions did not work. I found the solution on another part of the forum.
1. sudo apt-get remove* --purge xserver.
2. sudo apt-get install xserver-xorg.
Also kde got uninstalled some how and reinstalled.
Great forum, dont know what I would do without it!!!!

---

### Post by nicholaspaul on 2005-12-12
For the record, and I have no idea why, this solution worked for me:

[COLOR="DarkSlateBlue"]

rm /home/fortyninecent/.ICEauthority


Assuming 'fortyninecent' is your username.[/COLOR]

---

### Post by GeneralZod on 2005-12-13
[QUOTE=nicholaspaul]For the record, and I have no idea why, this solution worked for me:

[COLOR="DarkSlateBlue"]

rm /home/fortyninecent/.ICEauthority


Assuming 'fortyninecent' is your username.[/COLOR][/QUOTE]

```

sudo rm ~/.ICEauthority

```

is probably optimal :)

---

