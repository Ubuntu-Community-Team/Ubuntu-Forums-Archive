---
title: "booting up problem"
date: 2009-05-07
forum: General Help
---

### Post by calmpey09 on 2009-05-07
[FONT=Arial][SIZE=3][COLOR=Purple]***hello.. want to ask how to stop the "Starting up bluetooth" during the boot up... i've waited for so long until it says OK. but it doesnt appear. its not loading also. what will i do? i just installed  ubuntu 9.04 on my laptop.. help pls.. my laptop has NO BLUETOOTH***[/COLOR][/SIZE][/FONT]

---

### Post by halovivek on 2009-05-07
Hi please go to system- my preferences - check session
in that you can find the bluetooth option as start up and you can remove that one

---

### Post by calmpey09 on 2009-05-07
***[FONT=Arial][SIZE=3][COLOR=Purple]it didnt go to its dektop... it wont start up...  it also didnt load!!!!!!!!![/COLOR][/SIZE][/FONT]***

---

### Post by Yellow Pasque on 2009-05-07
Boot to recovery mode:
If you're not using bluetooth, simply remove it:
```
apt-get --purge remove bluez*
```
Note: This will probably ask to remove the ubuntu-desktop metapackage. It is safe to remove this package, as it just points to other packages and doesn't contain software. If it asks to remove non-bluetooth packages, please abort the command by pressing 'n'

I actually removed bluetooth from my fresh 9.04 install (along with a bunch of other stuff I don't need) before I started using my Jaunty.

---

### Post by geirha on 2009-05-07
I think a better solution would be to just disable the init script for bluetooth, rather than removing a package that ubuntu-desktop depends on.

In a recovery mode root shell, that would be
```
update-rc.d -f bluetooth remove
```

---

### Post by calmpey09 on 2009-05-07
[COLOR=Purple]***[FONT=Arial][SIZE=3]it logged after i put the codes and boot it up. i restart it but its just the same thing...[/SIZE][/FONT]***[/COLOR] :confused:

---

### Post by calmpey09 on 2009-05-07
***[SIZE=3][COLOR=Purple]plz.... can you tell me a step by step process on how to do it and where to put the codes..... i'm new here. and i really like ubuntu.... plz anyone?[/COLOR][/SIZE]***

---

