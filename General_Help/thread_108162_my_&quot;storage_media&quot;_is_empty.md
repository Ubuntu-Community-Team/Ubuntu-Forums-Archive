---
title: "my &quot;storage media&quot; is empty"
date: 2005-12-25
forum: General Help
---

### Post by nikolai.m on 2005-12-25
hi
wierdest thing...just last night when i fresh installed Kbreezy i started of course setting it up to my likings. yesturday when i would go to "storage media" (media:/) i would get see my cd and hd drives. after i installed and removed some programs to make Kbreezy more to my taste....when i go to storage media - it's empty!!! where did my cd/hd drives go?
thnx in advance for your help

---

### Post by ltmon on 2005-12-25
Do you know which programs you installed/removed?

Can you check adept that the "hal" and "dbus" packages are still installed?

Cheers,

L.

---

### Post by nikolai.m on 2005-12-25
[QUOTE=ltmon]Do you know which programs you installed/removed?

Can you check adept that the "hal" and "dbus" packages are still installed?

Cheers,

L.[/QUOTE]

yes, both of them are installed

---

### Post by Rzulf on 2005-12-27
I have the same problem but i can see floppy. Can it be because I have both ubuntu-desktop and kubuntu-desktop installed??

---

### Post by Rzulf on 2005-12-27
in gnome it works fine :/

---

### Post by 40%TUX on 2005-12-27
same here....
so.....there is a problem...but no solution!...i hate when that happends

(i bet there is solution, it just people who are more enlightened then me want share wisdom :( )

---

### Post by GoldBuggie on 2005-12-27
dbus, hal & pmount should be installed
doing a groups <USER> i am connected to
```
groups forest
forest : forest adm dialout cdrom floppy audio dip src video plugdev lpadmin scanner admin
``` doing a
```
groups hal
hal : hal cdrom floppy plugdev
``` 
To add to a group use ```
adduser <user> <group>
``` 
The groups of hal are important. Then you can look at making hal superuser by commenting out the last line in */etc/default/hal*

Note that these things aren't a straight solution they just might help. According to kde ppl the problem lies not within kde but it lies with hal. There is a bug in how it sends some information etc.

---

### Post by 40%TUX on 2005-12-28
> dbus, hal & pmount should be installed
 i got 'em all

> 
To add to a group use ```
adduser <user> <group>
``` 
The groups of hal are important. Then you can look at making hal superuser by commenting out the last line in */etc/default/hal*
what did you mean exctly here?-i have to add myself to group hal? or.... would you, please, explane!
thnx

---

### Post by GoldBuggie on 2005-12-28
In konsole do a **groups hal **and make sure that **plugdev** is there. If not then do a **sudo adduser hal plugdev**.

The other thing was that you should(or can try) to open up the file */etc/default/hal*.
**kdesu kate /etc/default/hal**

The last line will be "**#**DAEMON_OPTS=--retain-privileges". Remove the **#** so that the last line becomes "DAEMON_OPTS=--retain-privileges". Restart and try again. If it doesn't change anything then just put # back.

---

### Post by 40%TUX on 2005-12-28
[QUOTE=GoldBuggie]In konsole do a **groups hal **and make sure that **plugdev** is there. If not then do a **sudo adduser hal plugdev**.

The other thing was that you should(or can try) to open up the file */etc/default/hal*.
**kdesu kate /etc/default/hal**

The last line will be "**#**DAEMON_OPTS=--retain-privileges". Remove the **#** so that the last line becomes "DAEMON_OPTS=--retain-privileges". Restart and try again. If it doesn't change anything then just put # back.[/QUOTE]
i did all this and finaly i got my partitions to see .... :D , but none of my cdroms ..:confused: .
strangest thing is that when i first installed kubuntu i could see it all - drives, cd roms ...even memory stick!!!
what could change?...i mean i havn't installed anything special (kdevelop, build-esentials, xine, gimp, opera, java, upgraded OOo1.9 to 2.0**, kmymoney and of course frozen bubble...that's it...really):confused: 

ok...if you can give me some explanation thnx...otherwise thnx anyway...
chears

---

### Post by 40%TUX on 2005-12-30
[QUOTE=GoldBuggie]In konsole do a **groups hal **and make sure that **plugdev** is there. If not then do a **sudo adduser hal plugdev**.

The other thing was that you should(or can try) to open up the file */etc/default/hal*.
**kdesu kate /etc/default/hal**

The last line will be "**#**DAEMON_OPTS=--retain-privileges". Remove the **#** so that the last line becomes "DAEMON_OPTS=--retain-privileges". Restart and try again. If it doesn't change anything then just put # back.[/QUOTE]
well...on my older computer i did clean install and befor updating the system i looked at /etc/default/hal and line you refering to was with #, and i could see all my 3 cdroms and 2 partitions!!!
now i'm gonna update system and see if something changes....
i'll ceep posting..

---

### Post by roach of discord on 2005-12-31
I also have your problem, and did uncomment that line.  

I too can see my partitions, but no cdroms.  Very odd.

---

### Post by 40%TUX on 2005-12-31
(to avoid confusion in conversation -  i am nikolai.m)
well...after update i opened up "storage media" folder and everything was there....and then i turned computer off and went to sleep...today "storage media" is EMPTY!!!!!!!!!!!!:confused:  what tha?!!!!!

---

