---
title: "screenlets-manager wont start"
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by akshayas1986 on 2007-12-27
Hi everyone,

I have Compiz Fuzion on my machine and have enabled screenlets. When my GNOME starts, even the screenlets start. But now I have to change settings of one of the screenlets. When I start screenlets-managet on shell, I get this error and nothing happens. 

> LISTED PATH NOT EXISTS: /usr/local/share/screenlets/Calender1
LISTED PATH NOT EXISTS: /usr/local/share/screenlets/crystal_blue
akshayas@linaxe:~$ LISTED PATH NOT EXISTS: /usr/local/share/screenlets/Calender1
LISTED PATH NOT EXISTS: /usr/local/share/screenlets/crystal_blue
Unable to load 'Googlemaps' from /usr/local/share/screenlets/Googlemaps: libgtkembedmoz.so: cannot open shared object file: No such file or directory 
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 589, in <module>
    app = ScreenletsManager()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 133, in __init__
    self.load_screenlets()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 259, in load_screenlets
    info = ScreenletInfo(s, meta['name'], meta['info'], meta['author'], 
TypeError: 'NoneType' object is unsubscriptable


Could someone tell me what the problem is??

Thanks and regards

---

### Post by jomann on 2007-12-27
ok first off all screenlets is not good... sorry but what you need is this

you need the right repo's, though

"sudo apt-get install gdesklets"

when finished type

"gdesklets" in terminal or go to applications->accessories-> gdesklets

it's hase more widgets than screenlets and it's better

---

### Post by revertex on 2008-01-08
@jomann, 

can you tell us why  screenlets is not good? 

sorry, but your answer doesn't make more sense to recommend ppl to dump linux and install windows just because yahoo widgets is way more cool than any *nix *desklets.

not mention that is dead easy to use and have zillions of widgets.

adesklets and gdesklets have some issues with compiz and alpha transparency and gdesklets development seems defunct for a while, that's why screenlets born.

@akshayas1986,

if these files really exist, recheck permissions.

can you post the output of ```
ls -al /usr/local/share/screenlets
``` please?

best regards.

---

### Post by ST.x on 2008-01-09
> **revertex said:**
> 
@akshayas1986,

if these files really exist, recheck permissions.

can you post the output of ```
ls -al /usr/local/share/screenlets
``` please?

best regards.
I have the same problem:

> **Stx said:**
> Yep im getting something very similar.

```

&#9492;&#9472;($)&#9472;> screenlets-manager
The Pidgin Session is not present
Unable to load 'Pidgin' from /home/seynthantx/.screenlets/Pidgin: global name 'pidgin' is not defined 
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 589, in <module>
    app = ScreenletsManager()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 133, in __init__
    self.load_screenlets()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 259, in load_screenlets
    info = ScreenletInfo(s, meta['name'], meta['info'], meta['author'], 
TypeError: 'NoneType' object is unsubscriptable

```I changed from compiz fusion from repos to GIT version and I cant launch the manager, but I can run for example the NowPlaying screenlet by running it from the terminal. Should I compile screenlets as well? (I have all dependencies)

```

total 72
drwxr-xr-x 18 seynthantx seynthantx 4096 2007-12-14 18:20 .
drwxr-xr-x 24 root       root       4096 2008-01-08 01:43 ..
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Calendar
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Clock
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Control
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 CopyStack
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 CPUMeter
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Example
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Flower
drwxr-xr-x  2 seynthantx seynthantx 4096 2008-01-08 01:43 Launcher
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 MailCheck
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Notes
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Pager
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Picframe
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Ruler
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Storage
drwxr-xr-x  3 seynthantx seynthantx 4096 2008-01-08 01:43 Test
drwxr-xr-x  2 seynthantx seynthantx 4096 2008-01-08 01:43 Windowlist

```

---

### Post by revertex on 2008-01-09
@ST.x

try run ```
/usr/local/share/screenlets-manager/screenlets-manager.py
```

from a terminal, this way you will see if there is any error message.

The most common error is ```
ImportError: No module named rsvg
``` due missing dependencies in screenlet package.

If you get this error just install python-gnome2-desktop.

Note that you dont need screenlet manager to install/run screenlets.

To install just drop your screenlets in $HOME/.screenlets or /usr/local/share/screenlets.

to run write a little bash script like:

```
#!/bin/bash
python $HOME/.screenlets/anysceenlet/myscreenlet.py
```
or ```
#!/bin/bash
python /usr/local/share/screenlets/anysceenlet/myscreenlet.py
```

name it whatever you want like screenlet-start.
replace anysceenlet/myscreenlet.py by the correct path/name of the screenlet you want, make the script executable, and drop it in $HOME/bin, or preferably in /usr/local/bin.

you can launch multiples widgets using the same script, just put one per line

to finish go to menu >  system >  preferences > sessions and create a new entry point to your script

---

### Post by ST.x on 2008-01-09
ok i've fixed it by removing the pidgin screenlet that was in home/.screenshots, it was the one showing up in the messages as well. Thanks for your help anyway : )

---

