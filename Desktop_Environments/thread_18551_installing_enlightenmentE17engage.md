---
title: "installing enlightenment/E17/engage"
date: 2005-03-07
forum: Desktop Environments
---

### Post by lizardking on 2005-03-07
1)I installed enlightenment from apt and now i want to try it even than metacity. I start it but enlightenment says to me to change my startup file. where are they and how can  I do??

2) Which is the difference between enlightenment and E17??

3) I installed also engage but i don't know how to configure it. Someone can tell me?

thanks and bye

---

### Post by Qdlaty on 2005-03-07
Mmm, I'm glad seeing more people using E!

1. Be more specific, what the prompt of changing startup look like?

2. E16 is quite usable, it has all features you know from all DM. E17 is in early alpha stage but if you get it to know you may use it. For now I recomend using E16

3. What do you want to know about engage? Do you want to make it as a start bar or what?

Where did you get from .debs you used to install?

Seem to me that I'll really make promised HowTo about Enlightenment.

For now I can show you my previos screen shot to give you a taste of what E16 may become:
[Q-Enligted](http://tinyurl.com/5c7lg)

---

### Post by lizardking on 2005-03-07
[QUOTE=Qdlaty]Mmm, I'm glad seeing more people using E!

1. Be more specific, what the prompt of changing startup look like?

2. E16 is quite usable, it has all features you know from all DM. E17 is in early alpha stage but if you get it to know you may use it. For now I recomend using E16

3. What do you want to know about engage? Do you want to make it as a start bar or what?

Where did you get from .debs you used to install?

Seem to me that I'll really make promised HowTo about Enlightenment.

For now I can show you my previos screen shot to give you a taste of what E16 may become:
[Q-Enligted](http://tinyurl.com/5c7lg)[/QUOTE]

1) if i do ```
$ enlightment
```  this is the warning...

[IMG]http://iack.altervista.org/prova2.jpg[/IMG] 

So i don't know what I have to do...

2)OK I will use enlightment (E16)
3) I don't know how to configure **Launcher**  and **system tray**  in Engage....Some help? I have isntalled it following this 3d: [Engage 3d](http://ubuntuforums.org/showthread.php?t=13957) 
this is the screenshot of my "bad" engage.

[IMG]http://iack.altervista.org/engage.jpg[/IMG] 



bye

---

### Post by Qdlaty on 2005-03-07
Hym, lets play ;-)

I assume you took your .debs from:  [http://j.portalier.free.fr/debian/](http://j.portalier.free.fr/debian/)
It's a little outdated rep. Instead add this:
deb [http://mirror.my-space.ath.cx/](http://mirror.my-space.ath.cx/) unstable/
to you sources.list
and do the reinstall.

Tell me, how you start your enligtenment? You need to make your own E.desktop file in /usr/share/xsessions/
Mine:
[Desktop Entry]
Encoding=UTF-8
# Custom entry - YAY
Name=E16
Comment=Enlightenment.16
Exec=E16
Icon=
Type=Application

And then restart GDM (by the time you love E you will also want to install Entrance instead GDM)

OK, now it's time for Engage:
Mine starts with this options:
engage -m 1 -i 1 -e gl -g 1 -R 0 -t gant_engage
where:
m - display mode (0 - on top, 1 - below)
i - ignore running (1 means this option is active) so runnig apps icons won't apear in engage
e - engine - gl or software (depends on your gfx card)
g - grabs icons of runnig apps (a tricky procedure to find icon of iconised app)
R - reserve amount of pixels at the bottom of the screen
t - name of theme used (you may find them in /usr/local/share/engage/themes)

to get more of options run engage --help

It's time for icons ;-)

I don't like the original way of creating them so I prefer to edit one installed already.
So, all icons are in .e/apps/engage/launcher
so copy /usr/local/share/engage/icons/xapp.eapp there and rename it like you like then edit it with *e_util_eapp_edit*
I think you'll find it very usefull ;-)
After you done all you may also want to put all icons into desired order. So in the same directory create file .order and put icons names (with extensions) in desired order.

I think that's all. Have fun ;-)

---

### Post by lizardking on 2005-03-07
[QUOTE=Qdlaty]
I don't like the original way of creating them so I prefer to edit one installed already.
So, all icons are in .e/apps/engage/launcher
so copy /usr/local/share/engage/icons/xapp.eapp there and rename it like you like then edit it with *e_util_eapp_edit*
I think you'll find it very usefull ;-)[/QUOTE]
Slow slow!!!
 Suppose that now I want only install Engage, what is *e_util_eapp_edit*?? a program? i don't understand.
Try to tell me in the most simple way how engege icons and theme works....Thanks U very much !!!  [-o< 

I'm with gnome 2.8 ubuntu warty 4.0

thanks bye

---

### Post by Qdlaty on 2005-03-07
OK,
e_util_eapp_edit is a program to edit eapp files.
Eapp is a special Enlightenment format for "icons". It consist of icon, file-path and few more options like window class name etc.
For Engage those files are located in .e/apps/engage/launchers
you just simply type e_util_eapp_edit file.eapp and change whatever you want and save the file back.
Unfortunately, e_util_eapp_edit is a part of E17 so you may need to download and compile it with some libraries. You may also try to use that one I've attached.

What more you want to know?

---

### Post by lizardking on 2005-03-08
this is the result when i lunch the attachmente:
```
lizardking@iac:~ $ e_util_eapp_edit
e_util_eapp_edit: error while loading shared libraries: libecore_file.so.1: cannot open shared object file: No such file or directory
lizardking@iac:~ $
``` 
However i isntalled already E17 but i don't have any binary called **e_util_eapp_edit** . I have a similiare binary:
```
lizardking@iac:~ $ enlightenment
enlightenment           enlightenment-config17  enlightenment_remote17
enlightenment17         enlightenment_eapp17
lizardking@iac:~ $ enlightenment_eapp17
ERROR: no file specified!
OPTIONS:
  -lang LANG                 Set the language properties to modify
  -set-name NAME             Set the application name
  -set-generic GENERIC       Set the application generic name
  -set-comment COMMENT       Set the application comment
  -set-exe EXE               Set the application execute line
  -set-win-name WIN_NAME     Set the application window name
  -set-win-class WIN_CLASS   Set the application window class
  -set-startup-notify [1/0]  Set the application startup notify flag to on/off
  -set-wait-exit [1/0]       Set the application wait exit flag to on/off
  -del-name                  Delete the application name
  -del-generic               Delete the application generic name
  -del-comment               Delete the application comment
  -del-exe                   Delete the application execute line
  -del-win-name              Delete the application window name
  -del-win-class             Delete the application window class
  -del-startup-notify        Delete the application startup notify flag
  -del-wait-exit             Delete the application wait exit flag
lizardking@iac:~ $
``` 
Is this the program I can use to do icons?
Moreover can you explain if Engage works endured in launchbar mode and in systray mode?

thaks and sorry...

---

