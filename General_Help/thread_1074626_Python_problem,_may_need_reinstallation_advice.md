---
title: "Python problem, may need reinstallation advice"
date: 2009-02-19
forum: General Help
---

### Post by jnewl on 2009-02-19
Ok, here's the deal: I did a stupid thing and now I need your help. (Yes, I know it was stupid. No need to rub it in :( )

I upgraded my Python installation to 3.0.1 and uninstalled the previous version (2.5, I think). Now it turns out that 3.0 isn't backwards-compatible with the previous versions and as a consequence one of my programs won't run. I get the following output when I try to run Cedega from the terminal:

[INDENT]Traceback (most recent call last):
  File "/home/jim/.cedega/.updater/cedega_updater.py", line 16, in <module>
    import pygtk
ImportError: No module named pygtk
  File "/home/jim/.cedega/.ui/app/classical/main.py", line 30
    print "ERROR: You must have Python version 2.3 or later to run Cedega"
                                                                         ^
SyntaxError: invalid syntax[/INDENT]

I've done everything I know how to correct this, to no avail. I've uninstalled Python 3.0, reinstalled versions 2.4 and 2.5, I've looked for python-gtk, pygtk, and every other variation I could think of in Synaptic to try to reinstall that (couldn't find it), I've downloaded pygtk from the pygtk website and tried to install it manually (no go; it couldn't find the Python header files)...

So that's where I'm at now. I need help either in manually fixing this Python snafu OR I need to know how to reinstall Ubuntu 8.10 without losing my configuration settings and existing data. (I started to do a reinstall myself, but got scared and backed out when it wanted to repartition my disk to create another Ubuntu partition.)

Can anyone help me with either of these two things?

---

### Post by snova on 2009-02-19
[quote=jnewl]I upgraded my Python installation to 3.0.1 and uninstalled the previous version (2.5, I think). Now it turns out that 3.0 isn't backwards-compatible with the previous versions and as a consequence one of my programs won't run.[/quote]

It should be possible to install them side-by-side, invoking Py3K as 'python3' or 'python3.0'.

> 
Traceback (most recent call last):
File "/home/jim/.cedega/.updater/cedega_updater.py", line 16, in <module>
  import pygtk
ImportError: No module named pygtk


python-gtk2?

> 
File "/home/jim/.cedega/.ui/app/classical/main.py", line 30
print "ERROR: You must have Python version 2.3 or later to run Cedega"
^
SyntaxError: invalid syntax


That should be fixed by reinstalling Python 2.5...

Well, let me get a little information about your system's Python installation:

```

which python python2.5
dpkg -s python python2.5 python3 python3.0

```

---

### Post by jnewl on 2009-02-19
Thanks very much for your reply!

> **snova said:**
> It should be possible to install them side-by-side, invoking Py3K as 'python3' or 'python3.0'.
Yes, I can have them both installed, but under the circumstances I figured it was better just to leave 3.0 out of the picture for now. I did try having them side by side before to see if it would make a difference. It didn't, so I removed it.


> python-gtk2?
Yes. Synaptic reports it as being installed.


> That should be fixed by reinstalling Python 2.5...
That's what I thought, too. Unfortunately, it wasn't.


> Well, let me get a little information about your system's Python installation:

```

which python python2.5
dpkg -s python python2.5 python3 python3.0

```

"which python python2.5" returns:

[INDENT]/usr/local/bin/python
/usr/bin/python2.5
[/INDENT]

"dpkg -s python python2.5 python3 python3.0" returns:

[INDENT]Package: python
Status: install ok installed
Priority: important
Section: python
Installed-Size: 624
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: python-defaults
Version: 2.5.2-1ubuntu1
Replaces: python-base, python-xmlbase, python2.3 (<= 2.3.2-6)
Provides: python-email, python-xmlbase
Depends: python2.5 (>= 2.5.2), python-minimal (= 2.5.2-1ubuntu1)
Suggests: python-doc (>= 2.5.2-1ubuntu1), python-tk (>= 2.5.2-1ubuntu1), python-profiler (>= 2.5.2-1ubuntu1)
Conflicts: python-base, python-bz2, python-central (<< 0.5.5), python-csv, python-xmlbase, python2.1 (<= 2.1.2), python2.3 (<< 2.3.5-14)
Description: An interactive high-level object-oriented language (default version)
 Python, the high-level, interactive object oriented language,
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
 .
 This package is a dependency package, which depends on Debian's default
 Python version (currently v2.5).
Original-Maintainer: Matthias Klose <doko@debian.org>
Package: python2.5
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 10844
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 2.5.2-11.1ubuntu1
Replaces: idle-python2.5 (<< 2.4.3+2.5b2-2), python-tk (<< 2.4.3-2), python2.5-dev (<< 2.5.1), python2.5-minimal (<< 2.5)
Provides: python2.5-celementtree, python2.5-cjkcodecs, python2.5-ctypes, python2.5-elementtree, python2.5-plistlib, python2.5-wsgiref
Depends: python2.5-minimal (= 2.5.2-11.1ubuntu1), mime-support, libbz2-1.0, libc6 (>= 2.7), libdb4.6, libncursesw5 (>= 5.6+20071006-3), libreadline5 (>= 5.2), libsqlite3-0 (>= 3.5.9), libssl0.9.8 (>= 0.9.8f-5)
Suggests: python2.5-doc, python-profiler
Conflicts: idle-python2.5 (<< 2.4.3+2.5b2-2), python-central (<< 0.5.9), python-tk (<< 2.4.3-2)
Description: An interactive high-level object-oriented language (version 2.5)
 Version 2.5 of the high-level, interactive object oriented language,
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
Homepage: [http://python.org/](http://python.org/)
Original-Maintainer: Matthias Klose <doko@debian.org>
Python-Version: 2.5
Package `python3' is not installed and no info is available.

Package: python3.0
Status: purge ok not-installed
Priority: optional
Section: python
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.[/INDENT]

---

### Post by snova on 2009-02-19
> **jnewl said:**
> "which python python2.5" returns:

[INDENT]**/usr/local/bin/python**
/usr/bin/python2.5
[/INDENT]

Interesting, that might be the culprit... lets see:

```
file /usr/local/bin/python
/usr/local/bin/python --version
ls /usr/local/bin
```

---

### Post by jnewl on 2009-02-19
> **snova said:**
> Interesting, that might be the culprit... lets see:

```
file /usr/local/bin/python
/usr/local/bin/python --version
ls /usr/local/bin
```
"file /usr/local/bin/python" returns:

[INDENT]/usr/local/bin/python: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), not stripped
[/INDENT]


/usr/local/bin/python --version" returns:

[INDENT]Python 3.0.1[/INDENT]

(Aha!)


"ls /usr/local/bin" returns:

[INDENT]2to3        LotROLinux      python3.0         tor          vidalia
bchunkcue   nvidia-xconfig  python3.0-config  tor-gencert
bchunkcue~  pydoc           python-config     torify
idle        python          smtpd.py          tor-resolve
[/INDENT]

(Double aha! But how should I fix it?)

---

### Post by snova on 2009-02-19
Do you still have the source distribution you installed from (with build system)? Then, you could hopefully:

```
make uninstall
```

Otherwise, we'd be removing files from /usr/local manually, which isn't the greatest solution, but quite doable.

---

### Post by jnewl on 2009-02-19
Yes, I have an Ubuntu 8.10 disc, if that's what you're asking. Will doing a "make uninstall" put any of my data in jeopardy? (Sorry I don't know as much about this as I should, but that's why I came here :) )

EDIT: Doh. You're only talking about uninstalling Python, right? If so, I've only done that via the package manager up 'til now.

---

### Post by snova on 2009-02-19
> **jnewl said:**
> Yes, I have an Ubuntu 8.10 disc, if that's what you're asking. Will doing a "make uninstall" put any of my data in jeopardy? (Sorry I don't know as much about this as I should, but that's why I came here :) )

Turns out, there is no uninstall target in the Makefile (and I can't find something else), so we might be stuck deleting files manually. Oh well.

> EDIT: Doh. You're only talking about uninstalling Python, right? If so, I've only done that via the package manager up 'til now.

Edit: I'm assuming you installed Py3K from source, since the package manager never uses /usr/local.

Press Alt-F2, type in **gksudo nautilus**, and navigate to /usr/local.

In bin, remove: 2to3 python3.0 python3.0-config pydoc python-config idle smtpd.py

In lib, I expect there will be a 'python3.0' directory. It can also be removed.

Possibly another 'python3.0' directory in include, remove.

By now, Py3K should be completely gone.

Now, open another terminal and we'll check:

```
which python python3 python3.0
file /usr/bin/python
```

There might be a little bit left to do (putting symlinks back, not sure), but probably not much. Try to run your app.

---

### Post by jnewl on 2009-02-19
> **snova said:**
> Edit: I'm assuming you installed Py3K from source, since the package manager never uses /usr/local.
Oops. Yeah, you're right. I originally installed from source, but subsequently updated the software source so the package manager would have access to 3.0. After that, when I deleted 3.0, I did it from the package manager.

> Press Alt-F2, type in **gksudo nautilus**, and navigate to /usr/local.

In bin, remove: 2to3 python3.0 python3.0-config pydoc python-config idle smtpd.py

In lib, I expect there will be a 'python3.0' directory. It can also be removed.

Possibly another 'python3.0' directory in include, remove.

By now, Py3K should be completely gone.

Now, open another terminal and we'll check:

```
which python python3 python3.0
file /usr/bin/python
```

There might be a little bit left to do (putting symlinks back, not sure), but probably not much. Try to run your app.

Ok, I followed your instructions to the letter.

"which python python3 python3.0" returns:

[INDENT]/usr/local/bin/python[/INDENT]


"file /usr/bin/python" returns:

[INDENT]/usr/bin/python: symbolic link to `python2.5'
[/INDENT]


However, now attempting to run the app yields:

[INDENT]Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
Fatal Python error: Py_Initialize: can't initialize sys standard streams
ImportError: No module named encodings.utf_8
Aborted
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
Fatal Python error: Py_Initialize: can't initialize sys standard streams
ImportError: No module named encodings.utf_8
Aborted[/INDENT]

---

### Post by snova on 2009-02-19
> **jnewl said:**
> "which python python3 python3.0" returns:

[INDENT]/usr/local/bin/python[/INDENT]

Oops, looks like I missed one. Delete that too.

> "file /usr/bin/python" returns:

[INDENT]/usr/bin/python: symbolic link to `python2.5'
[/INDENT]

Nothing unusual here, that's good...

I'd guess the program in question has a **/usr/bin/env python** shebang at the top of the file, which is causing it to use the one in /usr/local in preference to the standard one in /usr/bin. Once it's removed, it should be fine... I hope.

---

### Post by jnewl on 2009-02-19
Omigod. I give up. You know that one, tiny, little reason you're not supposed to be logged in as root when you're messing around with critical files? I just validated it. I got distracted and accidentally deleted the python executable in both my /usr/local/bin and /usr/bin directories. Now I don't have an executable, nor did it go to the trash bin where I can recover it.

I think I'm gonna cry. I can't figure out how to reinstall the executable as it isn't part of either the "python" or "python2.5" packages (unless I'm missing something). AAARGH!

It's my own fault. You've been a huge help, snova. Thanks mucho.

---

### Post by snova on 2009-02-19
> **jnewl said:**
> Omigod. I give up. You know that one, tiny, little reason you're not supposed to be logged in as root when you're messing around with critical files? I just validated it. I got distracted and accidentally deleted the python executable in both my /usr/local/bin and /usr/bin directories. Now I don't have an executable, nor did it go to the trash bin where I can recover it.

I think I'm gonna cry. I can't figure out how to reinstall the executable as it isn't part of either the "python" or "python2.5" packages (unless I'm missing something). AAARGH!

It's my own fault. You've been a huge help, snova. Thanks mucho.

Nah, that's easy to put back. It's not even a program, it's just a symlink.

```
sudo ln -s python2.5 /usr/bin/python
```

---

### Post by jnewl on 2009-02-19
Yessssss! You are the man, snova! Everything's working perfectly now. Jesus, I can't thank you enough for your help. Not only did you get me up and running again, I've learned quite a bit in the process.

Thank you thank you thank you!

---

