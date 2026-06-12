---
title: "HAL doesn't initialize on logon"
date: 2006-03-04
forum: Desktop Environments
---

### Post by w.f.voogd on 2006-03-04
I don't know exactly since when, but when i login i get the message 'Failed to initialize hal'. When i reinstall hal, it works fine, until my next login.

I tried to find a log in order to further analyze the problem, but i couldnt find a hal log or anything..

Does anybody have any idea what might be wrong, or could give me some pointers on what to check?

Any help greatly appreciated,

cheers & breezes

Willem

---

### Post by w.f.voogd on 2006-03-05
okay, so i must have tinkered with things i forgot i tinkered with...
The problem was that the dbus wasn't running.

A System->Administration->Boot-Up Manager showed no activation 'x' in front. Turning it on and saving solved things...

(Boot-Up Manager is installed via 'sudo apt-get install bum' or of course by clicking bum in synaptic...

Just replying the solution in the odd event that another ubuntu user is as stupid as me to play with settings you dont know about ;)

edit: changed Manager to Administration, tx stanz... also added the apt-get command.

---

### Post by stanz on 2006-03-07
Hi w.f.voogd,
another stupid ubuntu user here... ;)....
Can you offer some more details on your fix?
* A System->Manager->Boot-Up Manager showed no activation 'x' in front. Turning it on and saving solved things...*
I'm thinking your heading into your panal, "System"?
From there...I see "Preferences" & "Administration" only.
In those...I find no "Boot-Up Manager"
Are we on different versions? I have already re-installed HAL, also...with no 
change, as yet.
Well, Thanks for the posting- i hope your still around & I can get fixed too!! :)

---

### Post by stanz on 2006-03-08
Hi All,
I've noticed that my 'Disk Mounter', that we can add to the panal~ is invisible- but, 'still there'...i know- but to some one- it'll make sense.
Even in the window, that comes up when we choose to 'add to panal', the icon is gone- but not the id for it. I can still choose this, and remove it from the panal...but- visually it ain't there!??
Any help be~ a help!

---

### Post by w.f.voogd on 2006-03-11
Ah well i see, i must have installed the boot-manager via synaptic, it seems it's not in the default setup...

well you could try to get dbus running by hand:

sudo /etc/init.d/dbus start

if that doesnt work, well, i dont know really...
if it does work, you have to enable dbus start at boot time somehow, i guess the easiest way is to install the forementioned boot-manager... (sudo apt-get install bum)

System->manager sould be System->Administration
(I'm using dutch language, so i'm translating from dutch to english, quite errorprone as you see..., i could of course select english before i post, but i'm just ehm.. lazy ;))

edit:added apt-get command for boot-manager...

---

### Post by stanz on 2006-04-07
Hi All..Hi w.f.voogd...
just gone thru another reinstall, and surfing for needed info & tweaks.
This 'bum' is an awesome tool...there's another post, ` [HERE-]("http://www.ubuntuforums.org/showthread.php?t=89491") `...that
heads into deep detail & tweaks!!
Later All !

---

