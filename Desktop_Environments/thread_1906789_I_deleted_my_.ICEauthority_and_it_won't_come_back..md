---
title: "I deleted my .ICEauthority and it won't come back."
date: 2012-01-09
forum: Desktop Environments
---

### Post by comp666 on 2012-01-09
In an attempt to fix the "Could not update ICEauthority file /home/kevin/.ICEauthority" error, I sudo rm my ICEauthority because someone said it would be created when I login again. Well, I've restarted and logged in but .ICEauthority hasn't been recreated and I'm still getting the "Could not update ICEauthority" error. Any ideas? I'm running ubuntu version 11.04 and gnome version 2.32.1.

---

### Post by prshah on 2012-01-10
> **comp666 said:**
> In an attempt to fix the "Could not update ICEauthority file /home/kevin/.ICEauthority" error, I sudo rm my ICEauthority because someone said it would be created when I login again. Well, I've restarted and logged in but .ICEauthority hasn't been recreated and I'm still getting the "Could not update ICEauthority" error. Any ideas? I'm running ubuntu version 11.04 and gnome version 2.32.1.

It is not enough to just delete the .ICEauthority file. You also need to create a new blank file, and set the correct permissions. For example```

cd /home/kevin
sudo touch .ICEauthority # creates blank file with name .ICEauthority
sudo chown kevin:kevin .ICEauthority # makes "kevin" owner of the file
sudo chmod 600 .ICEauthority # sets permissions to "-rw-------" (read/write access to owner only)

```

You don't need to use sudo if you are in the recovery console or if you are logged in as kevin on a virtual terminal (Eg Ctrl+Alt+F1..F3).

Please post back with results.

---

### Post by comp666 on 2012-01-10
I just did exactly what you said but unfortunately my new .ICEauthority file isn't being populated after rebooting.

-rw-------   1 kevin  kevin         0 2012-01-09 21:59 .ICEauthority

---

### Post by typhoon_tip on 2012-01-10
> **comp666 said:**
> I just did exactly what you said but unfortunately my new .ICEauthority file isn't being populated after rebooting.

-rw-------   1 kevin  kevin         0 2012-01-09 21:59 .ICEauthority

Urgh, try changing "kevin" in the above series of commands to your real username pal, it will work.

---

### Post by comp666 on 2012-01-10
I did use my real username, it's the name before the "@" right?

kevin@Dice:~$ cd ~
kevin@Dice:~$ pwd
/home/kevin
kevin@Dice:~$ sudo touch .ICEauthority
kevin@Dice:~$ sudo chown kevin:kevin .ICEauthority
kevin@Dice:~$ sudo chmod 600 .ICEauthority
kevin@Dice:~$ ls -la | grep .ICEauthority
-rw-------   1 kevin  kevin         0 2012-01-10 09:20 .ICEauthority

I also tried giving Group and Others read and write access as well but no luck.

---

### Post by prshah on 2012-01-10
> **comp666 said:**
> 
I also tried giving Group and Others read and write access as well but no luck.

Changing permissions on .ICEauthority only exacerbate the problem. 600 is correct permissions, and the output you have shown looks correct.

Please also check your home directory permissions/ownership; it should be as:```

ls -ld ../kevin /home
drwxr-xr-x 35 kevin kevin 12288 2012-01-10 19:36 ../kevin
drwxr-xr-x  5 root     root      4096 2011-01-14 23:01 /home

```

Sharing a common home folder between various distros is an absolute no-no; are you doing this?

---

### Post by comp666 on 2012-01-10
omg tytytyty so much. My ../kevin belonged to 1016:1016 for some reason. I chowned it and now it works!

---

### Post by prshah on 2012-01-10
> **comp666 said:**
> My ../kevin belonged to 1016:1016 for some reason. I chowned it and now it works!

Good to know it's solved. However, a note for others who may find this solution useful: do not RECURSIVELY chown or chmod your home directory!

Eg, in this example, this would be fine```
sudo chown kevin:kevin /home/kevin
``` but this will lead to TERRIBLE DISASTER:```
sudo chown [color=red]-R[/color] kevin:kevin /home/kevin
```

Same applies to permissions.

---

### Post by mlupton on 2012-01-11
[FONT=Georgia][SIZE=2]Wow, I had no idea fixing that issue was that simple. I had been trying for the longest time to use [FONT=Courier New]chown[FONT=Garamond] on the .ICEauthority file itself to no avail. Also I wonder what the "1016" ownership represents, I had the same issue on my machine. This certainly taught me never to use [FONT=Courier New]sudo [FONT=Georgia]for graphical applications ever again, [FONT=Courier New]gksudo[FONT=Georgia] could have prevented me from having this problem in the first place. Thanks for all the help.[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/SIZE][/FONT]

---

### Post by ethanjyx on 2013-03-04
sudo chown kevin:kevin /home/kevin: This works for me!!!

---

