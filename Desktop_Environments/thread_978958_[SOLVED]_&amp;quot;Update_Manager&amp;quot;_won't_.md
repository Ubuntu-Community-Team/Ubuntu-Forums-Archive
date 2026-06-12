---
title: "[SOLVED] &amp;quot;Update Manager&amp;quot; won't run; Pango broken"
date: 2008-11-11
forum: Desktop Environments
---

### Post by Valacosa on 2008-11-11
I am currently running Ubuntu 7.10 (Gutsy Gibbon) and would like to upgrade to Ubuntu 8.04.1 LTS (Hardy Heron). But my problem is **Update Manager doesn't run. At all.** If I click the icon in the System->Administration menu, nothing happens. 

I also tried running the update manager from the console, using the command:
```
gksu "update-manager -c -d"
```
And I get the following error:
```
ImportError: could not import pango
k-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
ImportError: could not import pango
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk.glade
ImportError: cannot import name Widget from gtk
```

My problem is exactly the same as described in the Ubuntu forums post [here]("http://ubuntuforums.org/showthread.php?t=420782"), but no solution is attached. Also, the packages named in [this solution]("http://ubuntuforums.org/showthread.php?t=540938") aren't available anymore.

[This post]("http://ubuntuforums.org/archive/index.php/t-123415.html") had some suggestions which helped me narrow down the problem. If I load python and try to import Pango, this is what happens:
```
Python 2.5.1 (r251:54863, Jul 31 2008, 23:17:40) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pango
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: /var/lib/python-support/python2.5/gtk-2.0/pango.so: undefined symbol: pango_gravity_get_for_matrix
>>> 
```

So update-manager seems to not work because **Python can't import Pango**. What's more, I downloaded the alternate-installation CD in an attempt to follow the non-network upgrade instructions [here]("http://www.ubuntu.com/getubuntu/upgrading-8.04"), but [FONT="Courier New"]cdromupgrade[/FONT] doesn't work either!

Is there a fix out there? I'd really rather not nuke my system and start from scratch. 

Things I have already tried:
[LIST]
[*]Setting the environment variable PYTHONPATH
[*]Reinstalling libpango1.0-common, libatk1.0-1, and a host of other packages
[/LIST]

---

### Post by Valacosa on 2008-11-15
Well, I fixed it. Thanks for all the help, guys.  **cricket**

Seriously though, it's all working again. [FONT="Courier New"]update-manager[/FONT] works, [FONT="Courier New"]pygtk-demo[/FONT] works, and [FONT="Courier New"]mupen64[/FONT] works. If any GTK+ or GLADE application stops working, and you have reason to believe Pango is at fault, here's what I did to solve the problem. 

First, I found out what version of Pango I had installed. You can do this with the command 
```
dpkg -l libpango1.0-common
```
You'll get a response like this:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name               Version            Description
+++-==================-==================-====================================================
ii  libpango1.0-common 1.18.3-0ubuntu1    Modules and configuration files for the Pango

```

Then I navigated to the Pango website, [here]("http://www.pango.org/"). Their [download section]("http://ftp.gnome.org/pub/GNOME/sources/pango/") has pretty much every version ever released. I saw that I had 1.18.3 installed, so I grabbed that one. 

*Do not* download the latest version. The latest version of Pango will depend on the latest version of Cario, GTK+, and a bunch of other things you probably don't have. If you download the version you supposedly already have installed, compiling will be a lot easier. 

That's right, we're going to compile this sucker. It's pretty easy, though, in the best case scenario. Once I unzipped the tarball, all I had to do is change to the directory with the source code in it and type three magic commands:
```

./configure
make
sudo make install

```
I don't consider this an *optimal* solution. If you don't already have any of the GNOME development tools installed, the [FONT="Courier New"]configure[/FONT] script will probably complain until you install them. And this solution requires you to be at least a little comfortable in the shell. But it solved the problem for me, maybe it'll work for you.

---

