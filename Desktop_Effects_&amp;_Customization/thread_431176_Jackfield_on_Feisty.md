---
title: "Jackfield on Feisty?"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by coldstatue on 2007-05-02
I have searched and found a great deal of posts about jackfield, but not regarding Feisty. I am pretty new to Linux, and am currently, finally, making 'the switch'... for good. So with that background, please understand that I need pretty specific descriptions and instructions. Any help is appreciated.

I just downloaded all the files from the link on this page

[http://kryogenix.org/code/jackfield/download](http://kryogenix.org/code/jackfield/download)

as the developer says not to use the tarbal anymore. I just copied all the files into a jackfield folder in my home directory, then made a widget directory within that.

I have read the install info at 

[http://www.kryogenix.org/days/2006/07/07/a-few-notes-on-installing-jackfield](http://www.kryogenix.org/days/2006/07/07/a-few-notes-on-installing-jackfield)

I did change my directory in Control.py, but when I do

 LD_LIBRARY_PATH=/usr/lib/firefox python jackfield/Control.py start showing

i get 

Traceback (most recent call last):
  File "jackfield/Control.py", line 7, in <module>
    import jackfield_dbus
  File "/home/coldstatue/jackfield/jackfield_dbus.py", line 56, in <module>
    raise NotImplementedError("D-Bus "+dbus.version+" untested!")
TypeError: cannot concatenate 'str' and 'tuple' objects


and when I try 

LD_LIBRARY_PATH=/usr/lib/firefox python jackfield/Widget.py /home/coldstatue/jackfield/widgets/

i get

jackfield/Widget.py:64: DeprecationWarning: raising a string exception is deprecated
  raise "Not a complete widget"
Traceback (most recent call last):
  File "jackfield/Widget.py", line 256, in <module>
    w = Widget(pth)
  File "jackfield/Widget.py", line 64, in __init__
    raise "Not a complete widget"
Not a complete widget


It doesn't seem to matter what widget I have in the directory.


Any help? The one thing I'm missing from Windows is quality widgets. I don't like KDE, so screenlets, gdesklets, and adesklets (though I can't get the last to work) are my only viable options at this point. Screenlets is ok, but I'd like better.

Thanks.

---

### Post by lcohen999 on 2007-06-12
I thought I would bump this...

---

### Post by Rabidmonkey1 on 2007-06-14
bump.

if someone could come up with a step-by-step tutorial for newbs, it would be greatly appreciated :D

---

### Post by shingalated on 2007-07-15
I couldn't figure it out either...screenlets orks okay I guess, except it has a huge memory leak on my computer.  If I leave it running for a few days, python will be using around 150 MB!

---

### Post by loneowais on 2007-08-05
i also get the same errot....but as author said, dont use tarball anymore....

i downloaded the latest from SVN...now the error is gone...infact control.py is gone....it has a new directory structure...

but now i get this error

```
owais@owais-desktop:~/Desktop/jackfield/jackfiled/trunk$ LD_LIBRARY_PATH=/usr/lib/firefox python /home/owais/Desktop/jackfield/jackfiled/trunk/jackfield.py /home/owais/Library/Widgets

Traceback (most recent call last):
  File "/home/owais/Desktop/jackfield/jackfiled/trunk/jackfield.py", line 53, in <module>
    from MainWindow import MainWindow
  File "/home/owais/Desktop/jackfield/jackfiled/trunk/MainWindow.py", line 1, in <module>
    import gtk, gtkmozembed, os, tempfile, gconf, urllib, Image, atexit
ImportError: No module named Image
```

---

### Post by loneowais on 2007-08-05
Jackfield is one of the best things that can happen to GNOME.....i think guys at Gnome should take Jackfield seriously & include it as a project to embed in Gnome

---

### Post by iheartubuntu on 2008-03-13
BUMP

Did anyone ever figure out how to get Jackfield to work? Thanks. Looks promising!

---

### Post by jegb on 2008-04-28
To solve this problem:

> **loneowais said:**
> i also get the same errot....but as author said, dont use tarball anymore....

i downloaded the latest from SVN...now the error is gone...infact control.py is gone....it has a new directory structure...

but now i get this error

```
owais@owais-desktop:~/Desktop/jackfield/jackfiled/trunk$ LD_LIBRARY_PATH=/usr/lib/firefox python /home/owais/Desktop/jackfield/jackfiled/trunk/jackfield.py /home/owais/Library/Widgets

Traceback (most recent call last):
  File "/home/owais/Desktop/jackfield/jackfiled/trunk/jackfield.py", line 53, in <module>
    from MainWindow import MainWindow
  File "/home/owais/Desktop/jackfield/jackfiled/trunk/MainWindow.py", line 1, in <module>
    import gtk, gtkmozembed, os, tempfile, gconf, urllib, Image, atexit
ImportError: No module named Image
```

install python-imaging package (synaptic or apt-get).
You get into another one error message more cryptic:
```
Segmentation fault (core dumped)

```
Any help?

---

### Post by coldstatue on 2008-04-29
The last response prompted me to come read this thread again. I have gotten by with gdesklets on my desktop and screenlets on my lap. Here we are, two days short of my 1-year anniversary of switching to Linux (exclusively - I dual-booted for 6 months first) and I haven't looked back.  

Still, I would love to see some improvements in the desklets area, as a Gnome adherent. 

Jackfield would rock my socks.

---

