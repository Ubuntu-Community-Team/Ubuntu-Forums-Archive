---
title: "[SOLVED] Need to find a way to automatically launch compiz-fusion"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by st33med on 2007-08-06
I have a problem with Compiz-Fusion. I have no borders when I start up, so I tried to do this:
```
:~$ compiz --replace ccp
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```
And of course, as you can see, it doesn't go well, as well as it doesn't launch compiz. (NOTE: I have a Intel 945GM that handles direct rendering) However when I add any of these things to the beginning of the code above:
```
LIBGL_ALWAYS_INDIRECT=1/TRUE
LIBGL_ALWAYS_INDIRECT=0/FALSE
LIBGL_ALWAYS_INDIRECT= #nothing here, not a typo
```
It works. Then I read somewhere about the glxinfo...
glxinfo tells me I have the GLX_EXT_texture_from_pixmap on the server, client, and OpenGl extensions, but not on the GLX extensions (which is version 1.2). 
I also tried putting this in 'Sessions' Startup programs:
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp &
```
But that does not start it.

So, can you please help me in, either getting a startup script to do that, or fix the GLX extension problem so I can have compiz --replace ccp & in Startup programs.

Regards,
st33med

EDIT: I have already tried to make a script called 'compiz-start', make it executable, and added it to startup scripts. That did not work.

---

### Post by jpereira on 2007-08-07
Try this in the sessions:

LIBGL_ALWAYS_INDIRECT=1 && compiz --replace ccp &

---

### Post by st33med on 2007-08-07
Nice try, jpereira, but that didn't work.

---

### Post by jpereira on 2007-08-07
Have you tried the --indirect-rendering parameters to compiz? 

compiz --indirect-rendering --replace ccp &

( check out compiz --help )

---

### Post by st33med on 2007-08-07
Yeah, I have (I have already mentioned that my card supports direct rendering. Proof?)

```
:~$ glxinfo | grep direct
direct rendering: Yes

```

Doesn't help... hmmm...

---

### Post by st33med on 2007-08-07
Also odd:
```
:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
Make sure you have the 'restricted' component enabled
bash: fglrxinfo: command not found

```

What's fglrxinfo?

---

### Post by Ub1476 on 2007-08-07
Install emerald theme manager, and..

compiz --replace -c emerald

Should fix the border thing. Now just go to Preferences>Sessions>Add   .. Write the command and name (like CF + Emerald ).

---

### Post by st33med on 2007-08-07
Ub, I already have it.

---

### Post by st33med on 2007-08-08
bump.

---

### Post by st33med on 2007-08-09
Now, I reinstalled CF with the current script. However, I switched the windows manager to compiz, but it gave me an error message:
```
andrew@andrew-laptop:~$ fusion-icon
* Using the GTK Interface
ini init, size 0
Backend     : ini
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
* Searching for installed applications...
/usr/local/bin/ccsm
/usr/local/bin/compiz
/usr/local/bin/gtk-window-decorator
/usr/local/bin/emerald
/usr/bin/metacity
/usr/bin/kwin
* gnome session
* Intel found, exporting: INTEL_BATCH=1
* No GLX_EXT_texture_from_pixmap present with direct rendering context
... present with indirect rendering, exporting: LIBGL_ALWAYS_INDIRECT=1
* Executing: LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp --indirect-rendering
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 129, in <module>
    choose_interface()
  File "/usr/bin/fusion-icon", line 101, in choose_interface
    import_interface(interface)
  File "/usr/bin/fusion-icon", line 66, in import_interface
    exec('import ' + module)
  File "<string>", line 1, in <module>
  File "/usr/share/fusion-icon/interface_gtk.py", line 22, in <module>
    from libfusionicon import *
  File "/usr/share/fusion-icon/libfusionicon.py", line 339, in <module>
    start_wm()
  File "/usr/share/fusion-icon/libfusionicon.py", line 163, in start_wm
    start_compiz()
  File "/usr/share/fusion-icon/libfusionicon.py", line 183, in start_compiz
    subprocess.Popen(compiz_command)
  File "/usr/lib/python2.5/subprocess.py", line 593, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```
What is happening?

---

### Post by st33med on 2007-08-09
I have found out why I couldn't execute that script. My user privileges were not correct for the file, so it never ran...

Now I just need to figure out why my fusion icon won't start...

---

