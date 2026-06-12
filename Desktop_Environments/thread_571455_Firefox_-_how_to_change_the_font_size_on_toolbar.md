---
title: "Firefox - how to change the font size on toolbar"
date: 2007-10-09
forum: Desktop Environments
---

### Post by satimis on 2007-10-09
Hi folks,


Ubuntu 7.04 server amd64
Fluxbox desktop
Firefox

Where can I change the font size of Firefox top toolbar? 

Edit -> Preference  does not help
View -> Toolbar -> Customize  also does not help.


Please advice.  TIA


satimis

---

### Post by RedSquirrel on 2007-10-09
I'm not sure if you can change the toolbar text itself. You can, however, change the application font in your ~/.gtkrc-2.0. For example:

```
gtk-font-name = "Sans 8"
```

If you use one of the GTK theme switchers (e.g., gtk-theme-switch or gtk-chtheme), then you should put that line in ~/.gtkrc-2.0.mine.

The alternative, of course, is to show only icons in the toolbar:

View -> Toolbars -> Customize...

Then **Show:** Icons.

---

### Post by satimis on 2007-10-09
> **RedSquirrel said:**
> I'm not sure if you can change the toolbar text itself. You can, however, change the application font in your ~/.gtkrc-2.0. For example:

Thanks for your advice.

I don't have this file.

$ ls -a /home/satimis/ | grep .gtkrc
No printout

$ ls -a /home/satimis/ | grep gtk*```

.gtk-bookmarks

```

$ apt-cache policy gtk
W: Unable to locate package gtk

$ apt-cache policy GTK
W: Unable to locate package GTK

I can change the fonts on webpage on;

Edit -> Preferences -> Content -> Fonts and Colors -> Advance.

but not the fonts on Toolbar

> 
The alternative, of course, is to show only icons in the toolbar:

View -> Toolbars -> Customize...

Then **Show:** Icons.
It is already there.

satimis

---

### Post by RedSquirrel on 2007-10-09
If you don't have that ~/.gtkrc-2.0 file, just create it. ;)

The setting will apply to all of your GTK+ 2.0 applications. There may be a way to make it apply only to Firefox, but it's not something I have looked into.

[http://library.gnome.org/devel/gtk/stable/GtkSettings.html](http://library.gnome.org/devel/gtk/stable/GtkSettings.html)

---

### Post by satimis on 2007-10-10
> **RedSquirrel said:**
> If you don't have that ~/.gtkrc-2.0 file, just create it. ;)

The setting will apply to all of your GTK+ 2.0 applications. There may be a way to make it apply only to Firefox, but it's not something I have looked into.

[http://library.gnome.org/devel/gtk/stable/GtkSettings.html](http://library.gnome.org/devel/gtk/stable/GtkSettings.html)
Hi,


Thanks for your advice.

Would installing gtk draw the lib-files of GNOME.  I don't have it running on this server.

I run Firefox occasionally for searching tech document om Internet.  I don't expect installing GNOME libraries and/or its packages on server.

B.R.
satimis

---

### Post by RedSquirrel on 2007-10-10
You already have it installed. GTK+ is the toolkit used for a large number of programs, Firefox included. It's _not_ the same thing as installing the gnome libraries that are needed for the GNOME desktop environment.

[http://www.gtk.org/](http://www.gtk.org/)

All you have to do is create the ~/.gtkrc-2.0 file and put that line in it and it will affect the font size of your GTK+ 2.0 applications. You can even change the font that is used.

---

### Post by satimis on 2007-10-10
> **RedSquirrel said:**
> You already have it installed. GTK+ is the toolkit used for a large number of programs, Firefox included. It's _not_ the same thing as installing the gnome libraries that are needed for the GNOME desktop environment.

[http://www.gtk.org/](http://www.gtk.org/)

All you have to do is create the ~/.gtkrc-2.0 file and put that line in it and it will affect the font size of your GTK+ 2.0 applications. You can even change the font that is used.
Thanks for your advice.  I got it done.

Performed following steps;

$ nano ~/.gtkrc-2.0

adding : ```

gtk-font-name = "Sans 16"

```
on the file.

Restarted X

That is all.


Any suggestion on increasing the font size on the bottom toolbar of Fluxbox, the desktop manager?  TIA


satimis

---

### Post by RedSquirrel on 2007-10-11
> **satimis said:**
> Thanks for your advice.  I got it done.

Performed following steps;

$ nano ~/.gtkrc-2.0

adding : ```

gtk-font-name = "Sans 16"

```on the file.

Restarted X

Actually, you should be able to see the changes just by restarting the individual applications. 

You would only end up restarting X if you login on the console, since you would quit Fluxbox and then run the usual 'startx'. If you are using a display manager (e.g., gdm), logging out and logging back in again would make absolutely sure the new setting is applied *everywhere*. 




> **satimis said:**
>  Any suggestion on increasing the font size on the bottom toolbar of Fluxbox, the desktop manager?

You'll have to learn about configuring Fluxbox styles. It's not hard. ;)

Have a look at the fluxstyle man page:

```
man fluxstyle
``````
~$ man fluxstyle | grep toolbar.*.font
Reformatting fluxstyle(1), please wait...
           toolbar.clock.font:             <font>
           toolbar.iconbar.focused.font: <font>
           toolbar.iconbar.unfocused.font: <font>
           toolbar.workspace.font:         <font>

```This guide seems pretty good, although I haven't looked at it in a while:
[http://wiki.archlinux.org/index.php/Fluxbox_Style_Guide](http://wiki.archlinux.org/index.php/Fluxbox_Style_Guide)

The default styles should be in /usr/local/share/fluxbox/styles. If you are going to modify those styles, I would advise you to copy the style configuration file and any associated pixmaps to your local ~/.fluxbox/styles directory. For example:

```
cp -r /usr/local/share/fluxbox/styles/Emerge ~/.fluxbox/styles/
```

---

### Post by satimis on 2007-10-11
> **RedSquirrel said:**
> Actually, you should be able to see the changes just by restarting the individual applications. 

Noted with thanks.

> 
You would only end up restarting X if you login on the console, since you would quit Fluxbox and then run the usual 'startx'. If you are using a display manager (e.g., gdm), logging out and logging back in again would make absolutely sure the new setting is applied *everywhere*. 
I don't have gdm running on this box which is a server, with only a few X packages installed.

I recall the commands I should run to kill Firefox are;

$ ps ax | grep firefox
to get the UID, then

$ sudo kill UID
that is all.


Now I'm facing another problem which I just discovered.

On Firefox
File -> Print
File -> Page Setup
File -> Preview
all make Firefox to freeze.

I don't know whether my recent work does matter.  How to stop "~/.gtkrc-2.0" running rather to delete it nor rename it?  TIA


> 
You'll have to learn about configuring Fluxbox styles. It's not hard. ;)

Have a look at the fluxstyle man page:

```
man fluxstyle
``````
~$ man fluxstyle | grep toolbar.*.font
Reformatting fluxstyle(1), please wait...
           toolbar.clock.font:             <font>
           toolbar.iconbar.focused.font: <font>
           toolbar.iconbar.unfocused.font: <font>
           toolbar.workspace.font:         <font>

```This guide seems pretty good, although I haven't looked at it in a while:
[http://wiki.archlinux.org/index.php/Fluxbox_Style_Guide](http://wiki.archlinux.org/index.php/Fluxbox_Style_Guide)

The default styles should be in /usr/local/share/fluxbox/styles. If you are going to modify those styles, I would advise you to copy the style configuration file and any associated pixmaps to your local ~/.fluxbox/styles directory. For example:

```
cp -r /usr/local/share/fluxbox/styles/Emerge ~/.fluxbox/styles/
```
Yes, sure.  I'll learn configuring Fluxbox styles later.  I'm not on that box.  Thanks


Edit:

I still can't find my solution.  Steps performed as follows;

satimis@ubuntu:~$ ls -al /usr/share/fluxbox/styles/Emerge/```

total 20
drwxr-xr-x 3 root root 4096 2007-09-06 22:30 .
drwxr-xr-x 4 root root 4096 2007-09-06 22:30 ..
drwxr-xr-x 2 root root 4096 2007-09-06 22:30 pixmaps
-rw-r--r-- 1 root root 5449 2006-09-29 00:54 theme.cfg

```

satimis@ubuntu:~$ ls -al ~/.fluxbox```

total 36
drwx------  2 satimis satimis 4096 2007-10-09 23:05 .
drwxr-xr-x 18 satimis satimis 4096 2007-10-12 09:15 ..
-rw-r--r--  1 satimis satimis 2920 2007-10-09 23:05 fluxbox-menu
-rw-r--r--  1 satimis satimis 3556 2007-10-09 22:17 init
-rw-r--r--  1 satimis satimis  306 2007-09-06 22:30 keys
-rw-r--r--  1 satimis satimis  107 2007-09-06 23:02 menu
-rw-r--r--  1 satimis satimis 2403 2007-10-09 23:05 menudefs.hook
-rw-r--r--  1 satimis satimis   66 2007-09-06 22:30 menu.origin
-rw-r--r--  1 satimis satimis    0 2007-10-11 23:18 slitlist
-rwxr-xr-x  1 satimis satimis 1085 2007-09-06 22:39 startup

```

satimis@ubuntu:~$ mkdir ~/.fluxbox/styles
No complaint

satimis@ubuntu:~$ cp -r /usr/share/fluxbox/styles/Emerge/ ~/.fluxbox/styles
No complaint

satimis@ubuntu:~$ ls -al ~/.fluxbox/styles```

total 12
drwxr-xr-x 3 satimis satimis 4096 2007-10-12 11:35 .
drwx------ 3 satimis satimis 4096 2007-10-12 11:34 ..
drwxr-xr-x 3 satimis satimis 4096 2007-10-12 11:35 Emerge

```


On Fluxbox desktop
Right-click -> Restart
to restart Fluxbox


Right-click -> Styles -> Emerge

The height of the bottom bar and the font size are smaller than my current styles, "Clean".


satimis@ubuntu:~$ ls -al ~/.fluxbox/styles/Emerge```

total 20
drwxr-xr-x 3 satimis satimis 4096 2007-10-12 11:35 .
drwxr-xr-x 3 satimis satimis 4096 2007-10-12 11:35 ..
drwxr-xr-x 2 satimis satimis 4096 2007-10-12 11:35 pixmaps
-rw-r--r-- 1 satimis satimis 5449 2007-10-12 11:35 theme.cfg

```

satimis@ubuntu:~$ ls -al ~/.fluxbox/styles/Emerge/pixmaps```

total 80
drwxr-xr-x 2 satimis satimis 4096 2007-10-12 11:35 .
drwxr-xr-x 3 satimis satimis 4096 2007-10-12 11:35 ..
-rw-r--r-- 1 satimis satimis  402 2007-10-12 11:35 bullet.xpm
-rw-r--r-- 1 satimis satimis  723 2007-10-12 11:35 close-pressed.xpm
-rw-r--r-- 1 satimis satimis  873 2007-10-12 11:35 close-unfocus.xpm
-rw-r--r-- 1 satimis satimis  865 2007-10-12 11:35 close.xpm
-rw-r--r-- 1 satimis satimis  737 2007-10-12 11:35 icon-pressed.xpm
-rw-r--r-- 1 satimis satimis  722 2007-10-12 11:35 icon-unfocus.xpm
-rw-r--r-- 1 satimis satimis  714 2007-10-12 11:35 icon.xpm
-rw-r--r-- 1 satimis satimis  751 2007-10-12 11:35 max-pressed.xpm
-rw-r--r-- 1 satimis satimis  841 2007-10-12 11:35 max-unfocus.xpm
-rw-r--r-- 1 satimis satimis  863 2007-10-12 11:35 max.xpm
-rw-r--r-- 1 satimis satimis  404 2007-10-12 11:35 selected.xpm
-rw-r--r-- 1 satimis satimis  663 2007-10-12 11:35 stick-pressed.xpm
-rw-r--r-- 1 satimis satimis  768 2007-10-12 11:35 stick-unfocus.xpm
-rw-r--r-- 1 satimis satimis  790 2007-10-12 11:35 stick.xpm
-rw-r--r-- 1 satimis satimis  738 2007-10-12 11:35 stuck-pressed.xpm
-rw-r--r-- 1 satimis satimis  843 2007-10-12 11:35 stuck-unfocus.xpm
-rw-r--r-- 1 satimis satimis  865 2007-10-12 11:35 stuck.xpm
-rw-r--r-- 1 satimis satimis  406 2007-10-12 11:35 unselected.xpm

```

Which file shall I edit?  Thanks


B.R.
satimis


satimis

---

### Post by satimis on 2007-10-12
Hi RedSquirrel,


Further to my late posting, I found it is NOT the problem of ".gtkrc-2.0".  After deleting it the freezing problem remains, including reboot.

What I found is as follows (after freezing);

$ ps ax | grep firefox```

 4924 ?        Ss     0:00 /bin/sh -c firefox
 4925 ?        Sl     0:04 /usr/lib/firefox/firefox-bin
 4983 pts/0    S+     0:00 grep firefox

```

$ kill 4925
Firefox closes

$ ps ax | grep firefox```

 4985 pts/0    S+     0:00 grep firefox

```

$ kill 4985```

bash: kill: (4985) - No such process

```
I can't kill it.  Would it matter?

Fire fox can be restarted w/o problem.


satimis

---

### Post by RedSquirrel on 2007-10-12
> **satimis said:**
> I recall the commands I should run to kill Firefox are;

$ ps ax | grep firefox
to get the UID, then

$ sudo kill UID


No need for sudo if you started firefox as your regular user. You can also use killall:

```
killall firefox-bin
```> **satimis said:**
> Now I'm facing another problem which I just discovered.

On Firefox
File -> Print
File -> Page Setup
File -> Preview
all make Firefox to freeze.

I don't know whether my recent work does matter.  How to stop "~/.gtkrc-2.0" running rather to delete it nor rename it?  TIA

Just rename the file. I'm not sure what's causing the freezing. I haven't had that problem.



> **satimis said:**
> The height of the bottom bar and the font size are smaller than my current styles, "Clean".


satimis@ubuntu:~$ ls -al ~/.fluxbox/styles/Emerge```

total 20
drwxr-xr-x 3 satimis satimis 4096 2007-10-12 11:35 .
drwxr-xr-x 3 satimis satimis 4096 2007-10-12 11:35 ..
drwxr-xr-x 2 satimis satimis 4096 2007-10-12 11:35 pixmaps
-rw-r--r-- 1 satimis satimis 5449 2007-10-12 11:35 theme.cfg

Which file shall I edit?  Thanks

In this case, **theme.cfg**. For styles that do not have any pixmaps, the configuration file is a text file with the same name as the style.

You just have to look for lines that have the word "font" in them.

[code]~$ grep font  .fluxbox/styles/Emerge/theme.cfg 
!menu.title.font:
!menu.frame.font:
!window.font:
!window.label.focus.font:
*.font: sans-8
!toolbar.clock.font:
!toolbar.workspace.font:
!toolbar.iconbar.focused.font:
!toolbar.iconbar.unfocused.font:

```In this case, all of the fonts are "sans-8". The '*.font' means the setting applies to all fonts, for every component of Fluxbox. As you see, you can also specify the fonts for each component. The "!" means that that line is commented (the setting is not applied). Just remove the "!" if you want to use those lines. You will sometimes see "#" for commented lines as well.




> **satimis said:**
> Further to my late posting, I found it is NOT the problem of ".gtkrc-2.0".  After deleting it the freezing problem remains, including reboot.

What I found is as follows (after freezing);

$ ps ax | grep firefox```

 4924 ?        Ss     0:00 /bin/sh -c firefox
 4925 ?        Sl     0:04 /usr/lib/firefox/firefox-bin
 4983 pts/0    S+     0:00 grep firefox

```$ kill 4925
Firefox closes

$ ps ax | grep firefox```

 4985 pts/0    S+     0:00 grep firefox

```$ kill 4985```

bash: kill: (4985) - No such process

```I can't kill it.  Would it matter?

Look carefully at the output of your second ps|grep command. You are trying to kill 4985, which is the process associated with the command 'grep firefox'. That process has already terminated, so when you try to kill it, you get "No such process".

---

### Post by satimis on 2007-10-13
Hi RedSquirrel,

I fixed the font size on toolbar.  Thanks.

The only remaining problem is Firefox frogen on selecting "Page Setup/Print Previes/Print".  Other items don't have problem.  I'll google around to check a possible solution.


Edit:

What do follows represent?```

toolbar.font:                        -*-lucidatypewriter-medium-r-normal-*-10-100-75-75-m-60-iso8859-* ???
window.font:                         -misc-8x8 system font-medium-r-normal--9-90-100-100-m-100-iso8859-* ???
menu.title.font:                     -*-lucidatypewriter-medium-r-normal-*-10-100-75-75-m-60-iso8859-* ???
menu.frame.font:                     -*-lucida-medium-r-normal-*-10-100-*-*-*-*-iso8859-* ???

```
Thanks


B.R.
satimis

---

### Post by satimis on 2007-10-14
Hi RedSquirrel,


I found something interesting.

On Fluxbox desktop drop-menu;
-> Styles -> there are many styles, such as Artwiz, BlueFlux, Clean, etc.  Emerge is also there.

Taking "Clean" as example.  It refers to;
/usr/share/fluxbox/styles/Clean

$ cat /usr/share/fluxbox/styles/Clean```

! "Clean"
! A Fluxbox theme by: skypher of perplexity
! 2001

toolbar:                             Interlaced
toolbar.color:                       rgb:CC/CC/CC

toolbar.button:                      Raised
toolbar.button.color:                rgb:CC/CC/CC
toolbar.button.picColor:             rgb:10/10/10

toolbar.button.pressed:              Sunken
toolbar.button.pressed.color:        rgb:80/80/80

toolbar.clock:                       Raised
toolbar.clock.color:                 rgb:CC/CC/CC
toolbar.clock.textColor:             rgb:10/10/10

toolbar.label:                       Raised
toolbar.label.color:                 rgb:CC/CC/CC
toolbar.label.textColor:             rgb:10/10/10

toolbar.windowLabel:                 Raised
toolbar.windowLabel.color:           rgb:CC/CC/CC
toolbar.windowLabel.textColor:       rgb:10/10/10

toolbar.justify:                     right

menu.title:                          Raised Gradient Horizontal Interlaced
menu.title.color:                    rgb:90/BB/CC
menu.title.colorTo:                  rgb:CA/CD/CF
menu.title.textColor:                rgb:10/10/10
menu.title.justify:                  Right

menu.frame:                          Gradient PipeCross
menu.frame.color:                    rgb:CC/CC/CD
menu.frame.colorTo:                  rgb:CA/CD/CE
menu.frame.textColor:                rgb:10/10/10
menu.frame.justify:                  Right

menu.hilite:                         Raised
menu.hilite.color:                   rgb:40/40/40
menu.hilite.textColor:               rgb:CC/CC/CC

menu.bullet:                         Diamond
menu.bullet.position:                Right


window.title.focus:                  Raised Interlaced
window.title.focus.color:            rgb:CC/CC/CD

window.title.unfocus:                Flat Solid
window.title.unfocus.color:          rgb:BE/BE/BE

window.label.focus:                  Solid Interlaced Flat
window.label.focus.color:            rgb:CA/CA/CB
window.label.focus.textColor:        rgb:10/10/10

window.label.unfocus:                Flat Solid
window.label.unfocus.color:          rgb:BE/BE/BE
window.label.unfocus.textColor:      rgb:09/09/09

window.button.focus:                 Raised Bevel1 Solid
window.button.focus.color:           rgb:CC/CC/CC
window.button.focus.picColor:        rgb:10/10/10

window.button.unfocus:               Flat Solid
window.button.unfocus.color:         rgb:CA/CA/CA
window.button.unfocus.picColor:      rgb:09/09/09

window.button.pressed:               Sunken Bevel1 Solid
window.button.pressed.color:         rgb:80/80/80

window.frame.focus:                  Flat
window.frame.focus.color:            rgb:CC/CC/CC
window.frame.unfocus:                Flat
window.frame.unfocus.color:          rgb:BE/BE/BE

window.handle.focus:                 Raised Solid
window.handle.focus.color:           rgb:CC/CC/CC
window.handle.unfocus:               Flat Solid
window.handle.unfocus.color:         rgb:BC/BC/BC

window.grip.focus:                   Raised Gradient Diagonal Interlaced
window.grip.focus.color:             rgb:9B/9B/9B
window.grip.focus.colorTo:           rgb:80/80/80
window.grip.unfocus:                 Raised Gradient Diagonal
window.grip.unfocus.color:           rgb:9B/9B/9B
window.grip.unfocus.colorTo:         rgb:80/80/80

!                                    ----------- tab - explicit for fluxbox, the best wm out there[tm] (;
window.tab.justify:                  Right
window.tab.label.unfocus:            Flat Solid
window.tab.label.unfocus.color:      rgb:AC/AC/AC
window.tab.label.unfocus.textColor:  black
window.tab.label.focus:              Raised Solid
window.tab.label.focus.color:        rgb:CC/CC/CC
window.tab.label.focus.textColor:    black
window.tab.borderWidth:              1
window.tab.borderColor:              rgb:10/10/10
!                                    ----------- (fluxbox.sourceforge.net)
window.tab.font:                     -*-lucidatypewriter-medium-r-normal-*-10-100-75-75-m-60-iso8859-*

window.justify:                      Right

toolbar.font:                        -*-lucidatypewriter-medium-r-normal-*-10-100-75-75-m-60-iso8859-*
window.font:                         -misc-8x8 system font-medium-r-normal--9-90-100-100-m-100-iso8859-*
menu.title.font:                     -*-lucidatypewriter-medium-r-normal-*-10-100-75-75-m-60-iso8859-*
menu.frame.font:                     -*-lucida-medium-r-normal-*-10-100-*-*-*-*-iso8859-*

borderColor:                         rgb:10/10/10

bevelWidth:                          1
borderWidth:                         1
handleWidth:                         2

background: flat
background.color: rgb:9A/9A/90

```

The fonts used are;
toolbar.font:                        -*-lucidatypewriter-medium-r-normal-*-10-100-75-75-m-60-iso8859-*
window.font:                         -misc-8x8 system font-medium-r-normal--9-90-100-100-m-100-iso8859-*
menu.title.font:                     -*-lucidatypewriter-medium-r-normal-*-10-100-75-75-m-60-iso8859-*
menu.frame.font:                     -*-lucida-medium-r-normal-*-10-100-*-*-*-*-iso8859-*


However they are NOT available on this box;


$ cat /etc/X11/xorg.conf```

....
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
....

```

satimis@ubuntu:~$ ls /usr/share/fonts/X11/ | grep cyrillic
satimis@ubuntu:~$ ls -al /usr/share/fonts/X11/ | grep cyrillic
satimis@ubuntu:~$ ls -al /usr/share/fonts/X11/ | grep 100dpi
satimis@ubuntu:~$ ls -al /usr/share/fonts/X11/ | grep 75dpi
All NO printout.  The directories don't exist.

$ ls -al /usr/share/fonts/X11/misc```

total 14680
drwxr-xr-x 2 root root  20480 2007-09-08 22:05 .
drwxr-xr-x 6 root root   4096 2007-09-27 17:01 ..
-rw-r--r-- 1 root root   5004 2006-12-20 21:08 10x20-ISO8859-10.pcf.gz
-rw-r--r-- 1 root root   5139 2006-12-20 21:08 10x20-ISO8859-11.pcf.gz
-rw-r--r-- 1 root root   5201 2006-12-20 21:08 10x20-ISO8859-13.pcf.gz
-rw-r--r-- 1 root root   4903 2006-12-20 21:08 10x20-ISO8859-14.pcf.gz
-rw-r--r-- 1 root root   5047 2006-12-20 21:08 10x20-ISO8859-15.pcf.gz
-rw-r--r-- 1 root root   4991 2006-12-20 21:08 10x20-ISO8859-16.pcf.gz
-rw-r--r-- 1 root root   5093 2006-12-20 21:08 10x20-ISO8859-1.pcf.gz
-rw-r--r-- 1 root root   4941 2006-12-20 21:08 10x20-ISO8859-2.pcf.gz
-rw-r--r-- 1 root root   4821 2006-12-20 21:08 10x20-ISO8859-3.pcf.gz
-rw-r--r-- 1 root root   5052 2006-12-20 21:08 10x20-ISO8859-4.pcf.gz
-rw-r--r-- 1 root root   4913 2006-12-20 21:08 10x20-ISO8859-5.pcf.gz
-rw-r--r-- 1 root root   4961 2006-12-20 21:08 10x20-ISO8859-7.pcf.gz
-rw-r--r-- 1 root root   4468 2006-12-20 21:08 10x20-ISO8859-8.pcf.gz
-rw-r--r-- 1 root root   5084 2006-12-20 21:08 10x20-ISO8859-9.pcf.gz
-rw-r--r-- 1 root root   5425 2006-12-20 21:08 10x20-KOI8-R.pcf.gz
....
.....

```


$ ls -al /usr/share/fonts/X11/Type1/```

total 60
drwxr-xr-x 2 root root  4096 2007-09-27 17:01 .
drwxr-xr-x 6 root root  4096 2007-09-27 17:01 ..
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 a010013l.pfb -> ../../type1/gsfonts/a010013l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 a010015l.pfb -> ../../type1/gsfonts/a010015l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 a010033l.pfb -> ../../type1/gsfonts/a010033l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 a010035l.pfb -> ../../type1/gsfonts/a010035l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 b018012l.pfb -> ../../type1/gsfonts/b018012l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 b018015l.pfb -> ../../type1/gsfonts/b018015l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 b018032l.pfb -> ../../type1/gsfonts/b018032l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 b018035l.pfb -> ../../type1/gsfonts/b018035l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 c059013l.pfb -> ../../type1/gsfonts/c059013l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 c059016l.pfb -> ../../type1/gsfonts/c059016l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 c059033l.pfb -> ../../type1/gsfonts/c059033l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 c059036l.pfb -> ../../type1/gsfonts/c059036l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 d050000l.pfb -> ../../type1/gsfonts/d050000l.pfb
-rw-r--r-- 1 root root  4326 2007-09-27 17:01 encodings.dir
-rw-r--r-- 1 root root 28397 2007-09-27 17:01 fonts.alias
-rw-r--r-- 1 root root  7439 2007-09-27 17:01 fonts.dir
-rw-r--r-- 1 root root  7439 2007-09-27 17:01 fonts.scale
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n019003l.pfb -> ../../type1/gsfonts/n019003l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n019004l.pfb -> ../../type1/gsfonts/n019004l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n019023l.pfb -> ../../type1/gsfonts/n019023l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n019024l.pfb -> ../../type1/gsfonts/n019024l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n019043l.pfb -> ../../type1/gsfonts/n019043l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n019044l.pfb -> ../../type1/gsfonts/n019044l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n019063l.pfb -> ../../type1/gsfonts/n019063l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n019064l.pfb -> ../../type1/gsfonts/n019064l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n021003l.pfb -> ../../type1/gsfonts/n021003l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n021004l.pfb -> ../../type1/gsfonts/n021004l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n021023l.pfb -> ../../type1/gsfonts/n021023l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n021024l.pfb -> ../../type1/gsfonts/n021024l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n022003l.pfb -> ../../type1/gsfonts/n022003l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n022004l.pfb -> ../../type1/gsfonts/n022004l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n022023l.pfb -> ../../type1/gsfonts/n022023l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 n022024l.pfb -> ../../type1/gsfonts/n022024l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 p052003l.pfb -> ../../type1/gsfonts/p052003l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 p052004l.pfb -> ../../type1/gsfonts/p052004l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 p052023l.pfb -> ../../type1/gsfonts/p052023l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 p052024l.pfb -> ../../type1/gsfonts/p052024l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 s050000l.pfb -> ../../type1/gsfonts/s050000l.pfb
lrwxrwxrwx 1 root root    32 2007-09-27 17:01 z003034l.pfb -> ../../type1/gsfonts/z003034l.pfb

```

$ cd /usr/share/fonts/X11/Type1/
satimis@ubuntu:/usr/share/fonts/X11/Type1$ cat fonts.alias```

!! fonts.alias -- automatically generated file.  DO NOT EDIT.
!! To modify, see update-fonts-alias(8).
!! /etc/X11/fonts/Type1/gsfonts-x11.alias
"-adobe-avant garde gothic-book-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-avant garde gothic-book-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-avant garde gothic-book-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-avant garde gothic-book-o-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-avant garde gothic-book-o-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-avant garde gothic-book-o-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-avant garde gothic-demi-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-avant garde gothic-demi-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-avant garde gothic-demi-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-avant garde gothic-demi-o-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-avant garde gothic-demi-o-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-avant garde gothic-demi-o-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-15"
-adobe-avantgarde-medium-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-avantgarde-medium-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-avantgarde-medium-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-avantgarde-medium-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-1"
-adobe-avantgarde-medium-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-2"
-adobe-avantgarde-medium-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-15"
-adobe-avantgarde-demi-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-avantgarde-demi-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-avantgarde-demi-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-avantgarde-demi-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-1"
-adobe-avantgarde-demi-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-2"
-adobe-avantgarde-demi-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-15"
-adobe-avantgarde-book-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-avantgarde-book-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-avantgarde-book-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-avantgarde-book-o-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-1"
-adobe-avantgarde-book-o-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-2"
-adobe-avantgarde-book-o-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-15"
-adobe-avantgarde-demi-o-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-1"
-adobe-avantgarde-demi-o-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-2"
-adobe-avantgarde-demi-o-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-itc avant garde gothic-book-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-itc avant garde gothic-book-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-itc avant garde gothic-book-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw gothic l-book-r-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-itc avant garde gothic-book-o-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-itc avant garde gothic-book-o-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-itc avant garde gothic-book-o-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw gothic l-book-o-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-itc avant garde gothic-demi-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-itc avant garde gothic-demi-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-itc avant garde gothic-demi-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-itc avant garde gothic-demi-o-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-itc avant garde gothic-demi-o-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-itc avant garde gothic-demi-o-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-15"
"-urw-urw gothic l-demi-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-1"
"-urw-urw gothic l-demi-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-2"
"-urw-urw gothic l-demi-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw gothic l-demibold-r-normal--0-0-0-0-p-0-iso8859-15"
"-urw-urw gothic l-demi-o-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-1"
"-urw-urw gothic l-demi-o-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-2"
"-urw-urw gothic l-demi-o-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw gothic l-demibold-o-normal--0-0-0-0-p-0-iso8859-15"
!
-adobe-bookman-light-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw bookman l-light-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-bookman-light-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw bookman l-light-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-bookman-light-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw bookman l-light-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-bookman-light-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw bookman l-light-i-normal--0-0-0-0-p-0-iso8859-1"
-adobe-bookman-light-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw bookman l-light-i-normal--0-0-0-0-p-0-iso8859-2"
-adobe-bookman-light-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw bookman l-light-i-normal--0-0-0-0-p-0-iso8859-15"
-adobe-bookman-demi-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw bookman l-demibold-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-bookman-demi-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw bookman l-demibold-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-bookman-demi-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw bookman l-demibold-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-bookman-demi-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw bookman l-demibold-i-normal--0-0-0-0-p-0-iso8859-1"
-adobe-bookman-demi-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw bookman l-demibold-i-normal--0-0-0-0-p-0-iso8859-2"
-adobe-bookman-demi-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw bookman l-demibold-i-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-itc bookman-light-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw bookman l-light-r-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-itc bookman-light-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw bookman l-light-r-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-itc bookman-light-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw bookman l-light-r-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-itc bookman-light-i-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw bookman l-light-i-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-itc bookman-light-i-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw bookman l-light-i-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-itc bookman-light-i-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw bookman l-light-i-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-itc bookman-demi-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw bookman l-demibold-r-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-itc bookman-demi-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw bookman l-demibold-r-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-itc bookman-demi-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw bookman l-demibold-r-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-itc bookman-demi-i-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw bookman l-demibold-i-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-itc bookman-demi-i-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw bookman l-demibold-i-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-itc bookman-demi-i-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw bookman l-demibold-i-normal--0-0-0-0-p-0-iso8859-15"
"-urw-urw bookman l-regular-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw bookman l-light-r-normal--0-0-0-0-p-0-iso8859-1"
"-urw-urw bookman l-regular-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw bookman l-light-r-normal--0-0-0-0-p-0-iso8859-2"
"-urw-urw bookman l-regular-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw bookman l-light-r-normal--0-0-0-0-p-0-iso8859-15"
"-urw-urw bookman l-regular-i-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw bookman l-light-i-normal--0-0-0-0-p-0-iso8859-1"
"-urw-urw bookman l-regular-i-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw bookman l-light-i-normal--0-0-0-0-p-0-iso8859-2"
"-urw-urw bookman l-regular-i-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw bookman l-light-i-normal--0-0-0-0-p-0-iso8859-15"
"-urw-urw bookman l-bold-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw bookman l-demibold-r-normal--0-0-0-0-p-0-iso8859-1"
"-urw-urw bookman l-bold-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw bookman l-demibold-r-normal--0-0-0-0-p-0-iso8859-2"
"-urw-urw bookman l-bold-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw bookman l-demibold-r-normal--0-0-0-0-p-0-iso8859-15"
"-urw-urw bookman l-bold-i-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw bookman l-demibold-i-normal--0-0-0-0-p-0-iso8859-1"
"-urw-urw bookman l-bold-i-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw bookman l-demibold-i-normal--0-0-0-0-p-0-iso8859-2"
"-urw-urw bookman l-bold-i-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw bookman l-demibold-i-normal--0-0-0-0-p-0-iso8859-15"
!
-adobe-courier-medium-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus mono l-regular-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-courier-medium-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus mono l-regular-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-courier-medium-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus mono l-regular-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-courier-medium-o-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus mono l-regular-o-normal--0-0-0-0-p-0-iso8859-1"
-adobe-courier-medium-o-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus mono l-regular-o-normal--0-0-0-0-p-0-iso8859-2"
-adobe-courier-medium-o-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus mono l-regular-o-normal--0-0-0-0-p-0-iso8859-15"
-adobe-courier-bold-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus mono l-bold-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-courier-bold-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus mono l-bold-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-courier-bold-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus mono l-bold-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-courier-bold-o-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus mono l-bold-o-normal--0-0-0-0-p-0-iso8859-1"
-adobe-courier-bold-o-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus mono l-bold-o-normal--0-0-0-0-p-0-iso8859-2"
-adobe-courier-bold-o-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus mono l-bold-o-normal--0-0-0-0-p-0-iso8859-15"
-adobe-courier-medium-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus mono l-regular-o-normal--0-0-0-0-p-0-iso8859-1"
-adobe-courier-medium-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus mono l-regular-o-normal--0-0-0-0-p-0-iso8859-2"
-adobe-courier-medium-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus mono l-regular-o-normal--0-0-0-0-p-0-iso8859-15"
-adobe-courier-bold-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus mono l-bold-o-normal--0-0-0-0-p-0-iso8859-1"
-adobe-courier-bold-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus mono l-bold-o-normal--0-0-0-0-p-0-iso8859-2"
-adobe-courier-bold-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus mono l-bold-o-normal--0-0-0-0-p-0-iso8859-15"
!
-adobe-helvetica-medium-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus sans l-regular-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-helvetica-medium-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus sans l-regular-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-helvetica-medium-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus sans l-regular-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-helvetica-medium-o-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus sans l-regular-i-normal--0-0-0-0-p-0-iso8859-1"
-adobe-helvetica-medium-o-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus sans l-regular-i-normal--0-0-0-0-p-0-iso8859-2"
-adobe-helvetica-medium-o-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus sans l-regular-i-normal--0-0-0-0-p-0-iso8859-15"
-adobe-helvetica-medium-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus sans l-regular-i-normal--0-0-0-0-p-0-iso8859-1"
-adobe-helvetica-medium-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus sans l-regular-i-normal--0-0-0-0-p-0-iso8859-2"
-adobe-helvetica-medium-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus sans l-regular-i-normal--0-0-0-0-p-0-iso8859-15"
-adobe-helvetica-bold-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus sans l-bold-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-helvetica-bold-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus sans l-bold-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-helvetica-bold-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus sans l-bold-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-helvetica-bold-o-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus sans l-bold-i-normal--0-0-0-0-p-0-iso8859-1"
-adobe-helvetica-bold-o-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus sans l-bold-i-normal--0-0-0-0-p-0-iso8859-2"
-adobe-helvetica-bold-o-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus sans l-bold-i-normal--0-0-0-0-p-0-iso8859-15"
-adobe-helvetica-bold-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-nimbus sans l-bold-i-normal--0-0-0-0-p-0-iso8859-1"
-adobe-helvetica-bold-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-nimbus sans l-bold-i-normal--0-0-0-0-p-0-iso8859-2"
-adobe-helvetica-bold-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-nimbus sans l-bold-i-normal--0-0-0-0-p-0-iso8859-15"
-adobe-helvetica-medium-r-narrow--0-0-0-0-p-0-iso8859-1 "-urw-nimbus sans l-regular-r-condensed--0-0-0-0-p-0-iso8859-1"
-adobe-helvetica-medium-r-narrow--0-0-0-0-p-0-iso8859-2 "-urw-nimbus sans l-regular-r-condensed--0-0-0-0-p-0-iso8859-2"
-adobe-helvetica-medium-r-narrow--0-0-0-0-p-0-iso8859-15 "-urw-nimbus sans l-regular-r-condensed--0-0-0-0-p-0-iso8859-15"
-adobe-helvetica-medium-o-narrow--0-0-0-0-p-0-iso8859-1 "-urw-nimbus sans l-regular-i-condensed--0-0-0-0-p-0-iso8859-1"
-adobe-helvetica-medium-o-narrow--0-0-0-0-p-0-iso8859-2 "-urw-nimbus sans l-regular-i-condensed--0-0-0-0-p-0-iso8859-2"
-adobe-helvetica-medium-o-narrow--0-0-0-0-p-0-iso8859-15 "-urw-nimbus sans l-regular-i-condensed--0-0-0-0-p-0-iso8859-15"
-adobe-helvetica-bold-r-narrow--0-0-0-0-p-0-iso8859-1 "-urw-nimbus sans l-bold-r-condensed--0-0-0-0-p-0-iso8859-1"
-adobe-helvetica-bold-r-narrow--0-0-0-0-p-0-iso8859-2 "-urw-nimbus sans l-bold-r-condensed--0-0-0-0-p-0-iso8859-2"
-adobe-helvetica-bold-r-narrow--0-0-0-0-p-0-iso8859-15 "-urw-nimbus sans l-bold-r-condensed--0-0-0-0-p-0-iso8859-15"
-adobe-helvetica-bold-o-narrow--0-0-0-0-p-0-iso8859-1 "-urw-nimbus sans l-bold-i-condensed--0-0-0-0-p-0-iso8859-1"
-adobe-helvetica-bold-o-narrow--0-0-0-0-p-0-iso8859-2 "-urw-nimbus sans l-bold-i-condensed--0-0-0-0-p-0-iso8859-2"
-adobe-helvetica-bold-o-narrow--0-0-0-0-p-0-iso8859-15 "-urw-nimbus sans l-bold-i-condensed--0-0-0-0-p-0-iso8859-15"
!
"-adobe-new century schoolbook-medium-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-century schoolbook l-regular-r-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-new century schoolbook-medium-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-century schoolbook l-regular-r-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-new century schoolbook-medium-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-century schoolbook l-regular-r-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-new century schoolbook-medium-i-normal--0-0-0-0-p-0-iso8859-1" "-urw-century schoolbook l-medium-i-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-new century schoolbook-medium-i-normal--0-0-0-0-p-0-iso8859-2" "-urw-century schoolbook l-medium-i-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-new century schoolbook-medium-i-normal--0-0-0-0-p-0-iso8859-15" "-urw-century schoolbook l-medium-i-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-new century schoolbook-bold-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-century schoolbook l-bold-r-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-new century schoolbook-bold-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-century schoolbook l-bold-r-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-new century schoolbook-bold-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-century schoolbook l-bold-r-normal--0-0-0-0-p-0-iso8859-15"
"-adobe-new century schoolbook-bold-i-normal--0-0-0-0-p-0-iso8859-1" "-urw-century schoolbook l-bold-i-normal--0-0-0-0-p-0-iso8859-1"
"-adobe-new century schoolbook-bold-i-normal--0-0-0-0-p-0-iso8859-2" "-urw-century schoolbook l-bold-i-normal--0-0-0-0-p-0-iso8859-2"
"-adobe-new century schoolbook-bold-i-normal--0-0-0-0-p-0-iso8859-15" "-urw-century schoolbook l-bold-i-normal--0-0-0-0-p-0-iso8859-15"
-adobe-newcenturyschlbk-medium-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-century schoolbook l-regular-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-newcenturyschlbk-medium-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-century schoolbook l-regular-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-newcenturyschlbk-medium-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-century schoolbook l-regular-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-newcenturyschlbk-medium-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-century schoolbook l-medium-i-normal--0-0-0-0-p-0-iso8859-1"
-adobe-newcenturyschlbk-medium-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-century schoolbook l-medium-i-normal--0-0-0-0-p-0-iso8859-2"
-adobe-newcenturyschlbk-medium-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-century schoolbook l-medium-i-normal--0-0-0-0-p-0-iso8859-15"
-adobe-newcenturyschlbk-bold-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-century schoolbook l-bold-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-newcenturyschlbk-bold-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-century schoolbook l-bold-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-newcenturyschlbk-bold-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-century schoolbook l-bold-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-newcenturyschlbk-bold-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-century schoolbook l-bold-i-normal--0-0-0-0-p-0-iso8859-1"
-adobe-newcenturyschlbk-bold-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-century schoolbook l-bold-i-normal--0-0-0-0-p-0-iso8859-2"
-adobe-newcenturyschlbk-bold-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-century schoolbook l-bold-i-normal--0-0-0-0-p-0-iso8859-15"
"-urw-century schoolbook l-medium-r-normal--0-0-0-0-p-0-iso8859-1" "-urw-century schoolbook l-regular-r-normal--0-0-0-0-p-0-iso8859-1"
"-urw-century schoolbook l-medium-r-normal--0-0-0-0-p-0-iso8859-2" "-urw-century schoolbook l-regular-r-normal--0-0-0-0-p-0-iso8859-2"
"-urw-century schoolbook l-medium-r-normal--0-0-0-0-p-0-iso8859-15" "-urw-century schoolbook l-regular-r-normal--0-0-0-0-p-0-iso8859-15"
"-urw-century schoolbook l-regular-i-normal--0-0-0-0-p-0-iso8859-1" "-urw-century schoolbook l-medium-i-normal--0-0-0-0-p-0-iso8859-1"
"-urw-century schoolbook l-regular-i-normal--0-0-0-0-p-0-iso8859-2" "-urw-century schoolbook l-medium-i-normal--0-0-0-0-p-0-iso8859-2"
"-urw-century schoolbook l-regular-i-normal--0-0-0-0-p-0-iso8859-15" "-urw-century schoolbook l-medium-i-normal--0-0-0-0-p-0-iso8859-15"
!
-adobe-palatino-medium-r-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw palladio l-regular-r-normal--0-0-0-0-p-0-iso8859-1"
-adobe-palatino-medium-r-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw palladio l-regular-r-normal--0-0-0-0-p-0-iso8859-2"
-adobe-palatino-medium-r-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw palladio l-regular-r-normal--0-0-0-0-p-0-iso8859-15"
-adobe-palatino-medium-i-normal--0-0-0-0-p-0-iso8859-1 "-urw-urw palladio l-medium-i-normal--0-0-0-0-p-0-iso8859-1"
-adobe-palatino-medium-i-normal--0-0-0-0-p-0-iso8859-2 "-urw-urw palladio l-medium-i-normal--0-0-0-0-p-0-iso8859-2"
-adobe-palatino-medium-i-normal--0-0-0-0-p-0-iso8859-15 "-urw-urw palladio l-medium-i-normal--0-0-0-0-p-0-iso8859-15"
"-urw-urw chancery l-medium-i-normal--0-0-0-0-p-0-iso8859-1" "-urw-urw chancery l-medium-i-normal-medium-0-0-0-0-p-0-iso8859-1"
"-urw-urw chancery l-medium-i-normal--0-0-0-0-p-0-iso8859-2" "-urw-urw chancery l-medium-i-normal-medium-0-0-0-0-p-0-iso8859-2"
"-urw-urw chancery l-medium-i-normal--0-0-0-0-p-0-iso8859-15" "-urw-urw chancery l-medium-i-normal-medium-0-0-0-0-p-0-iso8859-15"
!
"-adobe-zapf dingbats-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific" -urw-dingbats-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
-adobe-zapfdingbats-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific -urw-dingbats-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
"-itc-itc zapf dingbats-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific" -urw-dingbats-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
"-adobe-itc zapf dingbats-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific" -urw-dingbats-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
-urw-dingbats-regular-r-normal--0-0-0-0-p-0-adobe-fontspecific -urw-dingbats-medium-r-normal--0-0-0-0-p-0-adobe-fontspecific
!
! For Sketch (normal = medium, regular = medium):
!
-bitstream-charter-normal-r-normal--0-0-0-0-p-0-iso8859-1 -bitstream-charter-medium-r-normal--0-0-0-0-p-0-iso8859-1
-bitstream-charter-normal-r-normal--0-0-0-0-p-0-iso8859-2 -bitstream-charter-medium-r-normal--0-0-0-0-p-0-iso8859-2
-bitstream-charter-normal-r-normal--0-0-0-0-p-0-iso8859-15 -bitstream-charter-medium-r-normal--0-0-0-0-p-0-iso8859-15
-bitstream-charter-normal-i-normal--0-0-0-0-p-0-iso8859-1 -bitstream-charter-medium-i-normal--0-0-0-0-p-0-iso8859-1
-bitstream-charter-normal-i-normal--0-0-0-0-p-0-iso8859-2 -bitstream-charter-medium-i-normal--0-0-0-0-p-0-iso8859-2
-bitstream-charter-normal-i-normal--0-0-0-0-p-0-iso8859-15 -bitstream-charter-medium-i-normal--0-0-0-0-p-0-iso8859-15
-adobe-utopia-regular-r-normal--0-0-0-0-p-0-iso8859-1 -adobe-utopia-medium-r-normal--0-0-0-0-p-0-iso8859-1
-adobe-utopia-regular-r-normal--0-0-0-0-p-0-iso8859-2 -adobe-utopia-medium-r-normal--0-0-0-0-p-0-iso8859-2
-adobe-utopia-regular-r-normal--0-0-0-0-p-0-iso8859-15 -adobe-utopia-medium-r-normal--0-0-0-0-p-0-iso8859-15
-adobe-utopia-regular-i-normal--0-0-0-0-p-0-iso8859-1 -adobe-utopia-medium-i-normal--0-0-0-0-p-0-iso8859-1
-adobe-utopia-regular-i-normal--0-0-0-0-p-0-iso8859-2 -adobe-utopia-medium-i-normal--0-0-0-0-p-0-iso8859-2
-adobe-utopia-regular-i-normal--0-0-0-0-p-0-iso8859-15 -adobe-utopia-medium-i-normal--0-0-0-0-p-0-iso8859-15

```


$ cd /usr/share/fonts/X11/misc
satimis@ubuntu:/usr/share/fonts/X11/misc$ cat fonts.alias```

!! fonts.alias -- automatically generated file.  DO NOT EDIT.
!! To modify, see update-fonts-alias(8).
!! /etc/X11/fonts/misc/xfonts-base.alias
! $Xorg: fonts.alias,v 1.3 2000/08/21 16:42:31 coskrey Exp $
fixed        -misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-1
variable     -*-helvetica-bold-r-normal-*-*-120-*-*-*-*-iso8859-1
5x7          -misc-fixed-medium-r-normal--7-70-75-75-c-50-iso8859-1
5x8          -misc-fixed-medium-r-normal--8-80-75-75-c-50-iso8859-1
6x9          -misc-fixed-medium-r-normal--9-90-75-75-c-60-iso8859-1
6x10         -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-1
6x12         -misc-fixed-medium-r-semicondensed--12-110-75-75-c-60-iso8859-1
6x13         -misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-1
6x13bold     -misc-fixed-bold-r-semicondensed--13-120-75-75-c-60-iso8859-1
7x13         -misc-fixed-medium-r-normal--13-120-75-75-c-70-iso8859-1
7x13bold     -misc-fixed-bold-r-normal--13-120-75-75-c-70-iso8859-1
7x13euro     -misc-fixed-medium-r-normal--13-120-75-75-c-70-iso8859-15
7x13eurobold -misc-fixed-bold-r-normal--13-120-75-75-c-70-iso8859-15
7x14         -misc-fixed-medium-r-normal--14-130-75-75-c-70-iso8859-1
7x14bold     -misc-fixed-bold-r-normal--14-130-75-75-c-70-iso8859-1
8x13         -misc-fixed-medium-r-normal--13-120-75-75-c-80-iso8859-1
8x13bold     -misc-fixed-bold-r-normal--13-120-75-75-c-80-iso8859-1
8x16         -sony-fixed-medium-r-normal--16-120-100-100-c-80-iso8859-1
9x15         -misc-fixed-medium-r-normal--15-140-75-75-c-90-iso8859-1
9x15bold     -misc-fixed-bold-r-normal--15-140-75-75-c-90-iso8859-1
10x20        -misc-fixed-medium-r-normal--20-200-75-75-c-100-iso8859-1
12x24        -sony-fixed-medium-r-normal--24-170-100-100-c-120-iso8859-1
nil2         -misc-nil-medium-r-normal--2-20-75-75-c-10-misc-fontspecific

heb6x13      -misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-8
heb8x13      -misc-fixed-medium-r-normal--13-120-75-75-c-80-iso8859-8

k14          -misc-fixed-medium-r-normal--14-*-*-*-*-*-jisx0208.1983-0
a14          -misc-fixed-medium-r-normal--14-*-*-*-*-*-iso8859-1
r14          -misc-fixed-medium-r-normal--14-*-*-*-*-*-jisx0201.1976-0
rk14         -misc-fixed-medium-r-normal--14-*-*-*-*-*-jisx0201.1976-0
r16          -sony-fixed-medium-r-normal--16-*-*-*-*-*-jisx0201.1976-0
rk16         -sony-fixed-medium-r-normal--16-*-*-*-*-*-jisx0201.1976-0
r24          -sony-fixed-medium-r-normal--24-*-*-*-*-*-jisx0201.1976-0
rk24         -sony-fixed-medium-r-normal--24-*-*-*-*-*-jisx0201.1976-0
kana14       -misc-fixed-medium-r-normal--14-*-*-*-*-*-jisx0201.1976-0
8x16kana     -sony-fixed-medium-r-normal--16-120-100-100-c-80-jisx0201.1976-0
8x16romankana -sony-fixed-medium-r-normal--16-120-100-100-c-80-jisx0201.1976-0
12x24kana     -sony-fixed-medium-r-normal--24-170-100-100-c-120-jisx0201.1976-0
12x24romankana -sony-fixed-medium-r-normal--24-170-100-100-c-120-jisx0201.1976-0
kanji16      -jis-fixed-medium-r-normal--16-*-*-*-*-*-jisx0208.1983-0
kanji24      -jis-fixed-medium-r-normal--24-*-*-*-*-*-jisx0208.1983-0

hanzigb16st "-isas-song ti-medium-r-normal--16-160-72-72-c-160-gb2312.1980-0"
hanzigb24st "-isas-song ti-medium-r-normal--24-240-72-72-c-240-gb2312.1980-0"
hanzigb16fs "-isas-fangsong ti-medium-r-normal--16-160-72-72-c-160-gb2312.1980-0"

olcursor   "-sun-open look cursor-----12-120-75-75-p-160-sunolcursor-1"
olglyph-10 "-sun-open look glyph-----10-100-75-75-p-101-sunolglyph-1"
olglyph-12 "-sun-open look glyph-----12-120-75-75-p-113-sunolglyph-1"
olglyph-14 "-sun-open look glyph-----14-140-75-75-p-128-sunolglyph-1"
olglyph-19 "-sun-open look glyph-----19-190-75-75-p-154-sunolglyph-1"

-misc-fixed-medium-r-normal--7-50-100-100-c-50-iso8859-1 -misc-fixed-medium-r-normal--7-70-75-75-c-50-iso8859-1
-misc-fixed-medium-r-normal--8-60-100-100-c-50-iso8859-1 -misc-fixed-medium-r-normal--8-80-75-75-c-50-iso8859-1
-misc-fixed-medium-r-normal--9-80-100-100-c-60-iso8859-1 -misc-fixed-medium-r-normal--9-90-75-75-c-60-iso8859-1
-misc-fixed-medium-r-normal--10-70-100-100-c-60-iso8859-1 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-1
-misc-fixed-medium-r-semicondensed--12-90-100-100-c-60-iso8859-1 -misc-fixed-medium-r-semicondensed--12-110-75-75-c-60-iso8859-1
-misc-fixed-medium-r-semicondensed--13-100-100-100-c-60-iso8859-1 -misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-1
-misc-fixed-bold-r-semicondensed--13-100-100-100-c-60-iso8859-1 -misc-fixed-bold-r-semicondensed--13-120-75-75-c-60-iso8859-1
-misc-fixed-medium-r-normal--13-100-100-100-c-70-iso8859-1 -misc-fixed-medium-r-normal--13-120-75-75-c-70-iso8859-1
-misc-fixed-bold-r-normal--13-100-100-100-c-70-iso8859-1 -misc-fixed-bold-r-normal--13-120-75-75-c-70-iso8859-1
-misc-fixed-medium-r-normal--13-100-100-100-c-80-iso8859-1 -misc-fixed-medium-r-normal--13-120-75-75-c-80-iso8859-1
-misc-fixed-bold-r-normal--13-100-100-100-c-80-iso8859-1 -misc-fixed-bold-r-normal--13-120-75-75-c-80-iso8859-1
-misc-fixed-medium-r-normal--14-110-100-100-c-70-iso8859-1 -misc-fixed-medium-r-normal--14-130-75-75-c-70-iso8859-1
-misc-fixed-medium-r-normal--15-120-100-100-c-90-iso8859-1 -misc-fixed-medium-r-normal--15-140-75-75-c-90-iso8859-1
-misc-fixed-bold-r-normal--15-120-100-100-c-90-iso8859-1 -misc-fixed-bold-r-normal--15-140-75-75-c-90-iso8859-1
-misc-fixed-medium-r-normal--20-140-100-100-c-100-iso8859-1 -misc-fixed-medium-r-normal--20-200-75-75-c-100-iso8859-1
-misc-fixed-medium-r-semicondensed--13-100-100-100-c-60-iso8859-8 -misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-8
-misc-fixed-medium-r-normal--13-100-100-100-c-80-iso8859-8 -misc-fixed-medium-r-normal--13-120-75-75-c-80-iso8859-8
-sony-fixed-medium-r-normal--16-150-75-75-c-80-iso8859-1 -sony-fixed-medium-r-normal--16-120-100-100-c-80-iso8859-1
-sony-fixed-medium-r-normal--16-150-75-75-c-80-jisx0201.1976-0 -sony-fixed-medium-r-normal--16-120-100-100-c-80-jisx0201.1976-0
-sony-fixed-medium-r-normal--24-230-75-75-c-120-iso8859-1 -sony-fixed-medium-r-normal--24-170-100-100-c-120-iso8859-1
-sony-fixed-medium-r-normal--24-230-75-75-c-120-jisx0201.1976-0 -sony-fixed-medium-r-normal--24-170-100-100-c-120-jisx0201.1976-0
-jis-fixed-medium-r-normal--16-110-100-100-c-160-jisx0208.1983-0 -jis-fixed-medium-r-normal--16-150-75-75-c-160-jisx0208.1983-0
-jis-fixed-medium-r-normal--24-170-100-100-c-240-jisx0208.1983-0 -jis-fixed-medium-r-normal--24-230-75-75-c-240-jisx0208.1983-0

```

Therefore on selecting "Clean" the fonts are very small.  They are not available on this box.  Other styles are the same, with small fonts.


B.R.
satimis

---

### Post by RedSquirrel on 2007-10-14
You seem to be missing some font packages. The meta package for Xorg should pull in the necessary font packages.

If you are using dapper:

```
 sudo apt-get install x-window-system-core
```

For edgy, feisty, gutsy:

```
 sudo apt-get install xorg
```

Look at the dependencies of the appropriate meta package for your system and you'll see that there are some font packages listed there.

---

### Post by satimis on 2007-10-14
> **RedSquirrel said:**
> You seem to be missing some font packages. The meta package for Xorg should pull in the necessary font packages.

If you are using dapper:

```
 sudo apt-get install x-window-system-core
```

For edgy, feisty, gutsy:

```
 sudo apt-get install xorg
```
I'm running feisty.  However I found both of them on repo;

$ apt-cache policy xorg```

xorg:
  Installed: (none)
  Candidate: 1:7.2-0ubuntu11
  Version table:
     1:7.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com feisty/main Packages

```

$ apt-cache policy x-window-system-core```

x-window-system-core:
  Installed: (none)
  Candidate: 1:7.2-0ubuntu11
  Version table:
     1:7.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com feisty/universe Packages

```
Are they similar?


> 
Look at the dependencies of the appropriate meta package for your system and you'll see that there are some font packages listed there.
Please explain in more detail.  How to check them?  TIA


B.R.
satimis

---

### Post by RedSquirrel on 2007-10-14
> **satimis said:**
> I'm running feisty.  However I found both of them on repo;

$ apt-cache policy xorg```

xorg:
  Installed: (none)
  Candidate: 1:7.2-0ubuntu11
  Version table:
     1:7.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com feisty/main Packages

```$ apt-cache policy x-window-system-core```

x-window-system-core:
  Installed: (none)
  Candidate: 1:7.2-0ubuntu11
  Version table:
     1:7.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com feisty/universe Packages

```Are they similar?

x-window-system-core merely installs xorg. You can check this with:

```
apt-cache show x-window-system-core
```If you are using feisty, you should install the **xorg** package. Here is part of its description:

> It provides the X libraries, an X server, **a set of fonts**, and a group of basic X clients and utilities.
Here are the font dependencies I was referring to:

$ apt-cache show xorg
>  ...
Depends: xserver-xorg, libgl1-mesa-glx, libgl1-mesa-dri, libglu1-mesa, **[COLOR=Blue]xfonts-base (>= 1:1.0.0-1), xfonts-100dpi (>= 1:1.0.0-1), xfonts-75dpi (>= 1:1.0.0-1), xfonts-scalable (>= 1:1.0.0-1)[/COLOR]**, xbase-clients (>= 1:1.0.1-1), xutils (>= 1:1.0.1-1), xkb-data, xterm | x-terminal-emulator
...



---

### Post by satimis on 2007-10-15
Hi RedSquirrel,


Performed following steps;


$ sudo apt-get install xorg```

....
.....
warning: /etc/X11/fonts/X11R7/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /etc/X11/fonts/X11R7/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

```

The diretories don't exist.  Whether I have to create them manually first and reinstall xorg afterwards.


Restarted X

Now the font size becomes even smaller than before if selecting other styles NOT Emerge.  The latter is NOT affected.


$ cat /etc/X11/xorg.conf```

....
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
...

```
The last line was created automatically during installation of xorg

Shall I delete following 2 lines```

        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"

```
???

$ sudo find / -name 75dpi -type d```

/usr/share/fonts/X11/75dpi
/etc/X11/fonts/75dpi

```
Fonts found on /usr/share/fonts/X11/75dpi/

$ ls /etc/X11/fonts/75dpi/```

xfonts-75dpi.alias

```

$ sudo find / -name 100dpi -type d```

/usr/share/fonts/X11/100dpi
/etc/X11/fonts/100dpi

```

Fonts found on /usr/share/fonts/X11/100dpi/

$ ls /etc/X11/fonts/100dpi/```

xfonts-100dpi.alias

```


B.R.
satimis

---

### Post by RedSquirrel on 2007-10-16
> **satimis said:**
> ```
warning: /etc/X11/fonts/X11R7/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /etc/X11/fonts/X11R7/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

```The diretories don't exist.  Whether I have to create them manually first and reinstall xorg afterwards.

I don't have them either. I believe things were moved to the /usr/share/fonts/X11 directory instead. *I* don't think you need to worry about this, but you can google & search the forums and see what you come up with...



> **satimis said:**
>  Now the font size becomes even smaller than before if selecting other styles NOT Emerge.  The latter is NOT affected.

You can change the font in the Fluxbox style to suit yourself as explained earlier.


> **satimis said:**
>  Shall I delete following 2 lines```

        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"

```???

I just leave them.

---

### Post by satimis on 2007-10-17
Hi RedSquirrel,


I found out the trick on resetting fonts of Fluxbox as follow;

1)
Edit ~/.fluxbox/init
adding following line on it```

session.styleOverlay: ~/.fluxbox/overlay

```

2)
Create following file;
~/.fluxbox/overlay

and add following lines on it```

menu.title.font: sans-16:bold
menu.frame.font: sans-14
toolbar.clock.font: sans-16:bold
toolbar.workspace.font: sans-16:bold
.font: sans-16

```

3)
Restart X

That is all.  Fonts on toolbar, menu_tile, menu_frame, etc. of all styles change.


B.R.
satimis

---

