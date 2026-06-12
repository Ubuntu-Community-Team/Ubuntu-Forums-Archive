---
title: "How to install E17 on screwed Jaunty"
date: 2009-08-20
forum: Desktop Environments
---

### Post by mukul_s on 2009-08-20
Hi,

I recently upgraded openGeu8.10 to 9.04 and it got converted to Ubuntu Jaunty.  Gnome was installed as default DE. I wanted to get rid of Gnome and install openGEU packages once again.
By mistake before doing tht, I uninstalled some Gnome libraries and packages. So now I am not able to login to Desktop or anything. System boots shows gdm , accepts my login details, then it crashes and I am back to login screen.

 Now, is it possible to install E17 on this screwed machine?? If yes, how?

Regards
Mukul

---

### Post by naxa on 2009-09-17
In your case, I would hit Ctrl-Alt-F1 in gdm, which would bring me to a text terminal. One can login there and do stuff like apt-get install ...

---

### Post by Tux Aubrey on 2009-09-17
No guarantees[SIZE="2"]#[/SIZE], but......

from the terminal, use nano (with sudo) to edit /etc/apt/sources.list and add the repo:

```
deb http://packages.enlightenment.org/ubuntu jaunty main extras
```

get the enlightenment package key:

```
wget http://packages.enlightenment.org/repo.key
```

add it:

```
sudo apt-key add repo.key
```

```
sudo apt-get update
```

```
sudo apt-get install e17 emodule-bling emodule-calendar emodule-cpu emodule-deskshow emodule-diskio emodule-edgar emodule-efm-nav emodule-efm-path emodule-efm-pathbar emodule-extramenu emodule-flame emodule-mail emodule-mem emodule-notification emodule-places emodule-screenshot emodule-taskbar emodule-tiling emodule-trash emodule-winselector emodule-wlan wicd 
```

(note "wicd" - not an enlightenment package but a useful network manager for non-gnome systems)

This should give you a functional and fairly up-to-date e17 desktop with enough modules to get you setup (these are actually the only ones I personally use and know are stable and functional - which is why I don't recommend installing emodules-all).

Once you have a desktop working, you can browse the e17 repo in synaptic and install additional modules if you want (but very much at your own risk).

Please note that I haven't personally used these jaunty repos (However I'm doing much the same with Karmic and having no e17 related problems - only Karmic ones!)

 [SIZE="2"]#[/SIZE] oh, OK, you can have your money back if this doesn't work.

see [http://packages.enlightenment.org](http://packages.enlightenment.org) for further info.

---

### Post by mukul_s on 2009-09-17
Guys somehow I managed to convert my system to Karmic Xubuntu. Now I am running the latest dev release of Karmic. 
I don't want to use "http://packages.enlightenment.org" because it has very old snapshot. It dates back to some 29July svn.
Any tips how to get latest E17 on Karmic now?? I also read that alpha was due on 6th sep but no release new by now :(

---

### Post by Tux Aubrey on 2009-09-17
> **mukul_s said:**
> Guys somehow I managed to convert my system to Karmic Xubuntu. Now I am running the latest dev release of Karmic. 
I don't want to use "http://packages.enlightenment.org" because it has very old snapshot. It dates back to some 29July svn.
Any tips how to get latest E17 on Karmic now?? I also read that alpha was due on 6th sep but no release new by now :(

Honestly, I'm using both the current svn version on one (Jaunty) machine and the repo version on another (Karmic) and there is no observable difference for the user.  

The process for setting up the svn is full of traps and the "tidying up" of the e17 code base that is going on right now breaks things daily.  To do that on top of the Karmic alpha (which is one of the buggiest I've ever experienced) would be a full time occupation - and a probable shortcut to lifelong dependence on drugs and therapy. Do your national health system a favor and avoid it.

---

### Post by f4k1r on 2009-09-23
Please help me out i am having problem installing on intrepid using the easy script.I run into this error.I'm not sure if it is a problem with my svn install.

------------------------------ Easy_e17.sh 1.2.6 ------------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti
--------------------------------------------------------------------------------
  Updates:         [http://omicron.homeip.net/projects/#easy_e17.sh](http://omicron.homeip.net/projects/#easy_e17.sh)
  Support:         #e.de, #get-e (irc.freenode.net)
                   [email]morlenxus@gmx.net[/email]
  Patches:         Generally accepted, please contact me!
--------------------------------------------------------------------------------


----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /home/charan/e17_src/
  Source url:      [http://svn.enlightenment.org/svn/e/trunk](http://svn.enlightenment.org/svn/e/trunk)
  Logs path:       /tmp/easy_e17/install_logs
  OS:              Linux (Distribution: debian)

  Packages:        eina eet evas ecore efreet e_dbus embryo edje esmart exchange e entrance
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_player edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall exalt-client exhibit rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys mpdule notification b_and_w 

  Source conflict: solve automatically
  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 1/3 -------------------------------
- running some basic system checks
- source checkout/update
--------------------------------------------------------------------------------


------------------------------- Basic system checks ----------------------------
- creating script dirs ....... ok
- 'automake' available ....... ok
- 'gcc' available ............ ok
- 'make' available ........... ok
- 'svn' available ............ ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok (/etc/ld.so.conf.d/e17.conf)
- setting compile options .... ok
--------------------------------------------------------------------------------

----------------------------- Source checkout/update ---------------------------
- updating sources (please wait, this won't output much) ...
svn: REPORT of '/svn/e/!svn/vcc/default': Could not parse response status line ([http://svn.enlightenment.org](http://svn.enlightenment.org))
svn: OPTIONS of 'http://svn.enlightenment.org/svn/e/trunk': could not connect to server ([http://svn.enlightenment.org](http://svn.enlightenment.org))
FAILED! Next attempt 3 in 5 seconds

---

### Post by Tux Aubrey on 2009-09-23
f4k1r - I strongly suspect a problem with your svn installation or a dependency.

See [THIS BLOG]("http://devplant.net/2009/06/19/svn-problems-in-debian-squeeze-testing/") for a (possible) work around.

It is quite a while since I ran any svn scripts on Feisty so I can't actually replicate the problem (my script on Jaunty works fine).


NOT RELATED TO YOUR CURRENT PROBLEM, BUT....

I don't know how long ago you downloaded that script, but the settings look quite limited (which may be deliberate on your part or just a safety thing by morlenxus).  Just for reference (or if you solve the current problem and get stuck in a script loop), here's my own current "packages" list (from line 27 of the script - /usr/bin/easy_e17.sh):

> eina eet evas ecore efreet embryo edje esmart emotion ewl exml e_dbus e entrance edje_editor elicit elitaire enna enthrall empower emprint ephoto estickies expedite exquisite extrackt eyesight e_phys rage alarm bling calendar cpu configmenu deskshow diskio drawer efm_nav efm_path emu exalt-client execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo places rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan

and this is my current "skip" list (in /etc/easy_e17.conf):

> enhance exml imlib2 edb edje_player edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall exalt exalt-client exhibit rage drawer emu moon news penguins rain snow language photo efm_path efm_nav e_phys mpdule notification

(Note: I _don't_ use entrance)

---

