---
title: "Problem with gnome"
date: 2010-06-06
forum: Desktop Environments
---

### Post by cqc on 2010-06-06
Hi, i have a big problem. Everything on my desktop [COLOR=#000000]disappeard only thing left is desktop background and cursor. Im using dual boot with win xp. My grafic card is radeon 9200. I need help as fast as possible.
Thanks
[/COLOR]

---

### Post by lol768 on 2010-06-06
Do you mean all the icons on the desktop have disappeared?
Or the menus have gone etc?

**If only the icons have disappeared (and you can still see the applications menu etc): **

If you go to a terminal (*Alt+f2* and type in terminal, if that doesn't work try *Control + Alt + F2* and use *Control + Alt + F7* to get back to the desktop) and enter the following command:

```
cd Desktop; ls -l
```You can copy and paste this using (*Control + C* and *Control + **Shift** + V* in the terminal)
The command goes into the desktop folder and lists all files. It may be that your desktop is set to hide the files on the desktop somehow.
If you the terminal says total 0, then all the files on the desktop have gone. If not please copy (*Control + **Shift*** *+* *C*) and paste (*Control + V* ) into a reply to this post so I can have a look at permissions etc.

**If all menus etc have gone:**

If all the menus have gone the only thing I can think of doing is re-installing gnome - however this is a last resort, hopefully someone with more knowledge of GNOME will help you out (I mainly use kde).

---

### Post by cqc on 2010-06-06
> **lol768 said:**
> Do you mean all the icons on the desktop have disappeared?
Or the menus have gone etc?

**If only the icons have disappeared (and you can still see the applications menu etc): **

If you go to a terminal (*Alt+f2* and type in terminal, if that doesn't work try *Control + Alt + F2* and use *Control + Alt + F7* to get back to the desktop) and enter the following command:

```
cd Desktop; ls -l
```You can copy and paste this using (*Control + C* and *Control + **Shift** + V* in the terminal)
The command goes into the desktop folder and lists all files. It may be that your desktop is set to hide the files on the desktop somehow.
If you the terminal says total 0, then all the files on the desktop have gone. If not please copy (*Control + **Shift*** *+* *C*) and paste (*Control + V* ) into a reply to this post so I can have a look at permissions etc.

**If all menus etc have gone:**

If all the menus have gone the only thing I can think of doing is re-installing gnome - however this is a last resort, hopefully someone with more knowledge of GNOME will help you out (I mainly use kde).
everything is gone no menus, no icons... only cursor and desktop background
terminal says:
> stojakov@ubuntu:~$ cd Desktop; ls -l
bash: cd: Desktop: No such file or directory
&#1091;&#1082;&#1091;&#1087;&#1085;&#1086; 5112
drwxr-xr-x 2 stojakov stojakov    4096 2010-06-05 23:38 Dokumenta
drwxr-xr-x 3 stojakov stojakov    4096 2010-05-29 15:16 eagle
-rw-r--r-- 1 stojakov stojakov     179 2010-05-21 23:49 examples.desktop
drwxr-xr-x 2 stojakov stojakov    4096 2010-05-21 23:25 Javno
drwxr-xr-x 8 stojakov stojakov    4096 2010-06-02 16:00 JDownloader
-rw-r--r-- 1 stojakov stojakov       0 2010-06-02 17:50 khgk.jdc
drwxr-xr-x 2 stojakov stojakov    4096 2010-05-21 23:25 Muzika
-rw-r----- 1 stojakov stojakov  125944 2010-05-31 16:30 out.jpeg
-rw-r----- 1 stojakov stojakov 5034798 2010-05-31 14:52 out.pnm
-rw-r--r-- 1 stojakov stojakov   15548 2010-05-23 15:00 PCB.00007141.backup
drwxr-xr-x 4 stojakov stojakov    4096 2010-06-03 19:06 Radna povr&#353;
drwxr-xr-x 3 stojakov stojakov    4096 2010-05-23 00:26 Slike
drwxr-xr-x 2 stojakov stojakov    4096 2010-05-21 23:25 &#352;abloni
drwxrwxr-x 2 stojakov stojakov    4096 2010-05-23 13:47 Ubuntu One
drwxr-xr-x 2 stojakov stojakov    4096 2010-05-21 23:25 Video
drwxr-xr-x 2 stojakov stojakov    4096 2010-06-06 13:01 &#1055;&#1088;&#1077;&#1091;&#1079;&#1080;&#1084;&#1072;&#1114;&#1072;
drwxr-xr-x 4 stojakov stojakov    4096 2010-06-04 14:04 &#1096;&#1090;&#1072;&#1084;&#1087;&#1072;&#1085;&#1077; &#1087;&#1083;&#1086;&#1095;&#1077;


---

### Post by wojox on 2010-06-06
Try resetting the panels. Run these two commands:

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

---

### Post by cqc on 2010-06-06
> **wojox said:**
> Try resetting the panels. Run these two commands:

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```
nothing happpend

---

### Post by cqc on 2010-06-06
I have created another account with the same name and everything returned to normal, it looks fine for now. Anyway is there any drivers for my display card ati radeon 9200 i wanna higher res.?

---

