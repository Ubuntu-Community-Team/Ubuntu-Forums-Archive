---
title: "Help... I made a stuped misstake with e17"
date: 2007-10-14
forum: Desktop Environments
---

### Post by reza81 on 2007-10-14
I Just installed e17 & after running "sudo ./easy_e17.sh -i" I realized I cant loose the eviorment I am running atm... 

What is the syntax to uninstall all of this packeges & e17?

also see the how to e17:
[http://ubuntuforums.org/showthread.php?p=3533664&posted=1#post3533664](http://ubuntuforums.org/showthread.php?p=3533664&posted=1#post3533664)

Now I don't dare to shutdown my system :(

please help

---

### Post by lucidapparition on 2007-10-14
It looks like:
```
sudo sh easy_e17.sh -ccc
```
Should uninstall it. But if you followed those instructions, you shouldn't lose your current environment, as it installs e17 to /opt/e17 which is not a standard PATH.

---

### Post by reza81 on 2007-10-15
thanks for your replay 

```

reza@reza-desktop:~$ sudo ./easy_e17.sh -ccc

------------------------------- Easy_e17.sh 1.1.4 ------------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'wtfoo' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
--------------------------------------------------------------------------------
  Updates:         http://omicron.homeip.net/projects/#easy_e17.sh
  Support:         #e.de, #get-e (irc.freenode.net)
                   morlenxus@gmx.net
  Patches:         Generally accepted, please contact me!
--------------------------------------------------------------------------------


----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  CVS path:        /home/reza/e17_cvs
  CVS server:      :pserver:anonymous@anoncvs.enlightenment.org:/var/cvs/e
  Logs path:       /tmp/easy_e17/install_logs
  OS:              Linux (Distribution: debian)

  Libraries:       imlib2 edb eet evas ecore efreet epeg embryo edje epsilon esmart emotion engrave etk etk_extra evolve ewl exml enhance e_dbus
  Applications:    e entrance eclair evfs edje_viewer edje_editor elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies exhibit expedite extrackt
  Miscellaneous:   engage enthrall rage scrot
  Modules:         alarm bling cpu deskshow emu flame forecasts language mail mem mixer moon net news photo rain screenshot slideshow snow taskbar tclock uptime weather winselector wlan
  Skipping:        imlib2 edb emotion entrance eclair evfs edje_viewer edje_editor elicit evolve e_dbus elitaire emphasis empower engycad scrot entrance_edit_gui entropy ephoto estickies exhibit expedite extrackt engage enthrall rage emu flame moon rain screenshot snow language 

  Script action:   MISSING!
--------------------------------------------------------------------------------

------------------------------- Bad script argument ----------------------------
  Unknown argument '-ccc'!
--------------------------------------------------------------------------------



```

But it's an unknown argument!

---

### Post by lucidapparition on 2007-10-15
Try the command:
```
sudo sh easy_e17.sh --clean --clean --clean
```
If that doesn't work perhaps you have a different version than the one I am looking at. You can bring up a list of arguments by typing:
```
sh easy_e17.sh --help
```

---

