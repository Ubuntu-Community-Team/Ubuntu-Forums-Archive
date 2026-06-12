---
title: "enlightenment"
date: 2005-02-14
forum: Desktop Environments
---

### Post by T31 on 2005-02-14
i have installed enlightenment using synaptic, till here everything ok but how can i added this to the sessions menu when ubuntu start?

i did try computer->desktop preferences->sessions but with no success

i only can use if i start a console failsafe session but i have no access to anything then

thx in advance

---

### Post by Qdlaty on 2005-02-14
Welcome to Enlightenment Family!

put a file engligtenment.desktop (or whatever.desktop) with:
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Enlightenment
Exec=/usr/local/bin/enlightenment
Icon=
Type=Application

into /usr/share/xsessions

You may need to change Exec value.

If you have any E1x questions don't please, ask.

---

### Post by T31 on 2005-02-15
thank u! it really works! :)
but it is a really empty desktop, how can i add menus? the menus they say show up clicking the 3rd button seems to dont show up :P

---

### Post by Qdlaty on 2005-02-15
There is a small (and a little slow) script adding most of GNOME, KDE, GTK and other menus.

Look for *e_gen_menu*
Mine is in /usr/share/e16/scripts

After the process is finished look into ~/.e16/menus for files like:
file_apps.menu
it's a first menu that appear after you click your desktop .
You may want to add some of your favourite apps puting a line like:
*"Name" /path/to/icon.png exec "application"*

Icons are small (18x18) - thats menu ;-)
Or if you dont want to use icon you must put a word NULL instead.

There is a lot of work ahead but effect is worth every minute.

You may look at my desktop at:

[Q-Enlighted](http://tinyurl.com/5c7lg)

---

### Post by paul cooke on 2005-02-15
can't find that script, but there is an entry in the middle click menu 

> Maintenance > Regenerate Menus

 that will generate the menus... it doesn't get all programs (misses Firefox) and it sticks kde programs in with the gnome stuff though.

:)

---

### Post by Qdlaty on 2005-02-15
Try to locate it with *locate* ;-)

The Maintenace->Regenerate menus in fact calls that script so you don't have to look for it.

This script is not perfect, it doesn't follow Ubuntu's menus, some of programs are missing, some I couldn't find in Gnome/KDE menu are present.
In fact, you don't use them all so edit the files I've mentioned before to suit your needs.

The only thing I would like to have right now in E is Gnome's Alt+F2  quick calling a command but somehow I'll figure out how to do it.

---

### Post by T31 on 2005-02-19
one thing, how to make these launch bars with icons? Ive seen plenty people with them.

and one more thing, this DE is really really reaaaaally fast! and I thought xfce was fast,

any good file manager to use with enlightenment?

:)

---

### Post by Qdlaty on 2005-02-19
What you can see on my screenshot is Engage. One nice peace of code but damn hard to configure if you don't know how to start. Most of people uses gDesklets.

If you like difficult task try evidence as file manager, if you prefere simple one - try ROX - it really rocks!

Perhaps I'll commit small HOW2 about E16. :grin:

---

### Post by T31 on 2005-02-19
YEAH!!! Really do it, this DE rocks!!! is the first time i see a desktop restart without to close any app that really impress!!!

this has a lot of potential  \\:D/ 

u have my vote for that how2   :-)

---

### Post by Qdlaty on 2005-02-19
1st of all I've to finish ironing ;-) I'm stuck with a pile higher that I'm!!

The problem is that I don't remember my installation process.
I can only do a configure&tweaking HOWTO. 
OK, give me a day.

BTW, give E17 a try! I'm working on it right now, it's even faster but more raw!

C Ya

---

### Post by songochain on 2005-03-02
[QUOTE=Qdlaty]1st of all I've to finish ironing ;-) I'm stuck with a pile higher that I'm!!

The problem is that I don't remember my installation process.
I can only do a configure&tweaking HOWTO. 
OK, give me a day.

BTW, give E17 a try! I'm working on it right now, it's even faster but more raw!

C Ya[/QUOTE]
 Dude i've hoary amd64. I saw a video of E17 and i luv this desktop!! but i dont find repositories to install it 
Thanks in advance

---

### Post by p!=f on 2005-03-02
[QUOTE=songochain]Dude i've hoary amd64. I saw a video of E17 and i luv this desktop!! but i dont find repositories to install it 
Thanks in advance[/QUOTE]
/etc/apt/sources.list
```

# Englightenment DR17
deb http://soulmachine.net/debian unstable/
#deb-src http://soulmachine.net/debian unstable/

```
/etc/apt/preferences
```

[~] > cat /etc/apt/preferences
Package: enlightenment
Pin: version 0.17.0_pre10*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.17.0_pre10*
Pin-Priority: 999

```
so that E17 has priority over E16.

---

### Post by songochain on 2005-03-03
I dont find e17 package ```

sudo apt-cache search enlightenment
e16-data - Enlightenment Window Manager Run Time Data Files

```
```
sudo apt-get install e
e16                    enlightenment          evms-cli
e16-data               enscript               evms-gui
e2fsck-static          eog                    evms-ha
e2fslibs               eog2                   evms-ncurses
e2fsprogs              epiphany-browser       evolution
ed                     epydoc-doc             evolution1.5
editor                 esound                 evolution-data-server
eggcups                esound-clients         evolution-exchange
eject                  esound-common          evolution-webcal
elf-binutils           ethtool                exim4
emacsen-common         evms                   ext2resize

```So i think that it isnt for amd64 yet

---

### Post by Qdlaty on 2005-03-04
Yeah, I'm finally back.
1st of all about E17:
do not expect too much, it isn't even on alpha stage. There is a lot of function missing (like alt+tab apps changing, you can not configure windows activation behavior - it follows mouse pointer, there are no short keys, weird clipboard support, no tray support). So, as you can see it VERY hard to use, but, when you get to this you'll have the most amazing, the fastest WM ever.
About installation, you don't need to look for reps, it is very easy to get E17 working using this script.

I'm waiting for comments

---

### Post by songochain on 2005-03-12
[QUOTE=Qdlaty]Yeah, I'm finally back.
1st of all about E17:
do not expect too much, it isn't even on alpha stage. There is a lot of function missing (like alt+tab apps changing, you can not configure windows activation behavior - it follows mouse pointer, there are no short keys, weird clipboard support, no tray support). So, as you can see it VERY hard to use, but, when you get to this you'll have the most amazing, the fastest WM ever.
About installation, you don't need to look for reps, it is very easy to get E17 working using this script.

I'm waiting for comments[/QUOTE]
 Ok i'm trying to use the script but i dont know how to use it :S so i need help

---

