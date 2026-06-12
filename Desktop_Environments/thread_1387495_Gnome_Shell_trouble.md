---
title: "Gnome Shell trouble"
date: 2010-01-21
forum: Desktop Environments
---

### Post by MichaelRX8 on 2010-01-21
Hi. I installed gnome-shell from apt on a new partition install of Ubuntu 64 bit. Before doing updates it worked just fine. Now when I run "gnome-shell --replace I get this error

michael@michael-laptop:~$ gnome-shell --replace
Error: glXCreateContext failed
Failed to start shell
Cannot register the panel shell: there is already one running.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 265, in <module>
    shell = start_shell()
  File "/usr/bin/gnome-shell", line 138, in start_shell
    (server_glx_extensions, client_glx_extensions, glx_extensions) = _get_glx_extensions()
  File "/usr/bin/gnome-shell", line 75, in _get_glx_extensions
    server_glx_extensions = set(re.split("\s*,\s*", glxinfo_map['server glx extensions'].strip()))
KeyError: 'server glx extensions'

Anybody got any ideas?
 
         Thanks in advance.

---

### Post by wojox on 2010-01-21
Did you try setting the [ModulePath]("http://www.linuxquestions.org/questions/fedora-35/compiz-0.7.8-fedora-core-10-replace-fatal-glxcreatecontext-failed-686923/")

---

### Post by MichaelRX8 on 2010-01-22
Ummm...I'm not quite that smart yet. I know what a path is, but can you be more specific?

      thanks

---

### Post by MichaelRX8 on 2010-01-22
No one?

---

### Post by dwflo on 2010-01-22
@MichaelRX8,

Do not feel alone, still trying to figure it out!!!

Dave

---

### Post by tjsummers51l on 2010-01-22
If you can boot into another windows manager like KDE, I would try uninstalling all of the gnome components in synaptic package manager and then reinstall .

---

### Post by ucdminer on 2010-01-23
> **MichaelRX8 said:**
> Hi. I installed gnome-shell from apt on a new partition install of Ubuntu 64 bit. Before doing updates it worked just fine. Now when I run "gnome-shell --replace I get this error

michael@michael-laptop:~$ gnome-shell --replace
Error: glXCreateContext failed
Failed to start shell
Cannot register the panel shell: there is already one running.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 265, in <module>
    shell = start_shell()
  File "/usr/bin/gnome-shell", line 138, in start_shell
    (server_glx_extensions, client_glx_extensions, glx_extensions) = _get_glx_extensions()
  File "/usr/bin/gnome-shell", line 75, in _get_glx_extensions
    server_glx_extensions = set(re.split("\s*,\s*", glxinfo_map['server glx extensions'].strip()))
KeyError: 'server glx extensions'

Anybody got any ideas?
 
         Thanks in advance.

I was also facing this trouble. All I did is to reinstall my Nvidia driver. I earlier had 190.53, I am now using 195.30. Everything is fine now :)

---

### Post by MichaelRX8 on 2010-01-23
Thanks ucdminer. I was using the same driver, I went ahead and installed the older one from Ubuntu's driver installer and it seems to be fine now.

---

