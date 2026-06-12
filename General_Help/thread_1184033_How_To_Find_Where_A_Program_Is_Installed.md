---
title: "How To Find Where A Program Is Installed"
date: 2009-06-10
forum: General Help
---

### Post by Russell_S on 2009-06-10
Hi, I'm very new to Linux and am still quite near the bottom of the steep learning curve.

What I would like to know is how to find out where a program is installed. For instance, I installed Enemy Territory game but now want to remove it. There is an enemy-territory entry under Applications-->Other but I don't know where that is pointing to. In Windows (which I'm used to) I would right click on the shortcut and get properties. This would then tell me what folder the shortcut was pointing to, so I was wondering whether there is an equivalent in Linux.


Many thanks

Russell

---

### Post by maheshasolkar on 2009-06-10
Hope this helps:

  [https://help.ubuntu.com/community/EnemyTerritory#Uninstalling](https://help.ubuntu.com/community/EnemyTerritory#Uninstalling)

---

### Post by michy99 on 2009-06-10
The way to remove a program depends on how you installed it. If you installed it with Synaptic Package Manager, Add/Remove or apt-get, you can use the same method to remove them.

If you downloaded a .deb package from somewhere, you can remove it with```
sudo dpkg -r packagename
```

---

### Post by Russell_S on 2009-06-10
Thanks very much for helping me out.

I followed the link and entered this:-
```
sudo rm -rf /usr/local/games/enemy-territory/ && sudo rm -f /usr/local/bin/et && rm -rf $HOME/.etwolf
```Which appears to have removed Enemy Terrirtory. However, the entry is still in Applications-->Other-->enemy-territory. How do I now remove this entry from the list.

Also:-
> The way to remove a program depends on how you installed it.How would you go about removing an application a year later when you may not remember how you installed it. Also, if you installed from a .deb package you downloaded, and "sudo dpkg -r packagename" will remove it, does that mean that you have to have the original downloaded file in order to uninstall later. In view of this is it wise to keep any packages you install manually just in case you need to uninstall later down the line.

Sorry about all the questions but I'm trying to learn so that in the future I'll know what to do.


Regards

Russell

---

### Post by jonobr on 2009-06-10
to find a program you could also use the which command

heres me looking for a few programs (of course you need the right name)

```


me@munster:~$ which perl
/usr/bin/perl
me@munster:~$ which seamonkey
/usr/bin/seamonkey
me@munster:~$ which kvpnc
/usr/bin/kvpnc
me@munster:~$ 

```

---

### Post by hayden92 on 2009-06-10
You can also try the "whereis" command:

whereis <program>

---

### Post by doas777 on 2009-06-10
> **jonobr said:**
> to find a program you could also use the which command

heres me looking for a few programs (of course you need the right name)

```


me@munster:~$ which perl
/usr/bin/perl
me@munster:~$ which seamonkey
/usr/bin/seamonkey
me@munster:~$ which kvpnc
/usr/bin/kvpnc
me@munster:~$ 

```

beet me too it. :)

---

### Post by Russell_S on 2009-06-10
That's great guys, just what I was looking for.

Many thanks.

---

### Post by mortenkjeldgaard on 2009-06-10
You shouldn't remove the binaries "manually" using rm. Rather, remove the package. Sometimes, it's not obvious what package a binary is part of, but you can use for example:

> dpkg -S /usr/bin/perl

which in this case tells you:

> perl-base: /usr/bin/perl

so here, the package is perl-base, and you remove that like this:

> apt-get remove perl-base

---

### Post by maheshasolkar on 2009-06-10
> **Russell_S said:**
> Thanks very much for helping me out.

I followed the link and entered this:-
```
sudo rm -rf /usr/local/games/enemy-territory/ && sudo rm -f /usr/local/bin/et && rm -rf $HOME/.etwolf
```Which appears to have removed Enemy Terrirtory. However, the entry is still in Applications-->Other-->enemy-territory. How do I now remove this entry from the list.



Right-click on the *Applications* menu in the top-left corner of your screen and click on *Edit Menus*. It will bring up a menu editor where you can select any menu item and delete it (*Right-click -> Delete*).

---

### Post by Agent ME on 2009-06-10
> **maheshasolkar said:**
> Right-click on the *Applications* menu in the top-left corner of your screen and click on *Edit Menus*. It will bring up a menu editor where you can select any menu item and delete it (*Right-click -> Delete*).
Enemy Territory will still show up on other user's menus then.

Do it the proper way, and remove Enemy Territory's .desktop file.

Find it first - I know it's somewhere under the /usr directory and I think the filename is "et.desktop":
```
find /usr -name "et.desktop"
```
That will tell you where the file is. Then delete it:
```
sudo rm /location/of/file/et.desktop
```

---

### Post by Russell_S on 2009-06-11
> **maheshasolkar said:**
> Right-click on the *Applications* menu in the top-left corner of your screen and click on *Edit Menus*. It will bring up a menu editor where you can select any menu item and delete it (*Right-click -> Delete*).
Thanks for that. I tried right clicking on the entries themselves and on the sub-menus but not actually on Applications.
Sometimes you just need the blindingly obvious pointing out.

Also, that's really useful about finding out what a package is named so you can remove it.
I'm learning lots today.


Many thanks

---

### Post by Russell_S on 2009-06-11
> **Agent ME said:**
> Enemy Territory will still show up on other user's menus then.

Do it the proper way, and remove Enemy Territory's .desktop file.

Find it first - I know it's somewhere under the /usr directory and I think the filename is "et.desktop":
```
find /usr -name "et.desktop"
```That will tell you where the file is. Then delete it:
```
sudo rm /location/of/file/et.desktop
```

Sorry, I didn't see you post when I replied earlier, but thanks for the input.

I did as you suggested and it worked like a charm.


Once again thanks to all who replied with help and advice, it is really appreciated.


Russell

---

