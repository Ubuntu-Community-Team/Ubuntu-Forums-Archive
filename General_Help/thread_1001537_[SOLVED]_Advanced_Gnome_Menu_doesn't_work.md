---
title: "[SOLVED] Advanced Gnome Menu doesn't work"
date: 2008-12-04
forum: General Help
---

### Post by eternalnewbee on 2008-12-04
Hi there.
After reading about **Advanced Gnome Menu** in one of the threads (can't remember which one) I decided to try it out myself.
So I installed it, and it shows up both in Accessories (Advanced Gnome Menu) and in Preferences (Advanced Gnome Menu Configurator),
but clicking on it doesn't start up anything.
Any ideas on what to do to get it to work?

---

### Post by Forlong on 2008-12-04
The menu runs in the tray, so after you execute it, there should be a blue icon ion the tray showing up. Clicking on it will show the menu.

If it still doesn't work, run
```
advancedgnomemenu
``` in a terminal.

---

### Post by eternalnewbee on 2008-12-04
Hi forlong.
Really appreciate your help (feels like a dejavu...)
This is the output of the command:

:~$ advancedgnomemenu
Running installed agm, modifying PYTHONPATH.
Cannot read config: /home/bird/.AGM_config Using default-one
Traceback (most recent call last):
  File "./AGM.py", line 34, in <module>
    from AGM.AGM_Main_Window import AGM
  File "/usr/local/lib/python/AGM/AGM_Main_Window.py", line 26, in <module>
    import AGM.AGM_CairoWin as CairoWin
  File "/usr/local/lib/python/AGM/AGM_CairoWin.py", line 24, in <module>
    conf=config()
  File "/usr/local/lib/python/AGM/AGM_default_config.py", line 121, in __init__
    self.read_conf()
  File "/usr/local/lib/python/AGM/AGM_default_config.py", line 184, in read_conf
    fav_changes=self.read_fav_apps()
  File "/usr/local/lib/python/AGM/AGM_default_config.py", line 192, in read_fav_apps
    file=open(self.favorites_path, "r")
IOError: [Errno 2] No such file or directory: '/home/bird/.AGM_fav_app'
bye bye

---

### Post by Forlong on 2008-12-04
Looks like your version is not up-to-date.
What's the output of ```
dpkg -l | grep agm
```

---

### Post by eternalnewbee on 2008-12-04
> Looks like your version is not up-to-date.
What's the output of```
 dpkg -l grep agm
``` 
~$ dpkg -l | grep agm
ii  agm                                       0.5-1                                 Advanced Gnome Menu
There it is.

---

### Post by Forlong on 2008-12-04
Alright, go here: [http://www.sciallo.net/AGM/index.php?page=dati.php](http://www.sciallo.net/AGM/index.php?page=dati.php) and download **agm_0.6.0-1_all.deb**
This one should work.

---

### Post by eternalnewbee on 2008-12-04
> Alright, go here: [http://www.sciallo.net/AGM/index.php?page=dati.php](http://www.sciallo.net/AGM/index.php?page=dati.php) and download agm_0.6.0-1_all.deb
This one should work.
On my way...

---

### Post by eternalnewbee on 2008-12-04
Thanks forlong. Mission accomplished.

---

