---
title: "I want to use Python"
date: 2005-11-03
forum: Desktop Environments
---

### Post by otware on 2005-11-03
OK I am learning Python. I have been informed that my time will be better spent learning python that c++. I have python on windows.
Now I really love the idea of making applications that run on practically any OS. 

However, I cannot seem to run Python on Ubuntu. There is no icon for it, which i9s hardly surprising. But even by typing 'python' into terminal, i cannot seem to run it. I know it it there, but how do i bring up the window?

---

### Post by psychicdragon on 2005-11-03
Hi, 

Python is a programming language. Running python with no arguments brings you into the Python interactive shell. Which allows you to run Python commands line-by-line. Try entering **print "Hello!**" into the shell and see what happens.

To execute a python program you would enter something like this into the terminal:
```
python foo.py
```
foo.py being the name of the Python program.

Here are some links:
[Python Documentation]("http://docs.python.org/")
[Dive into Python]("http://diveintopython.org/")
[PyGTK]("http://www.pygtk.org/") (For writing GUI programs using GTK)

DIve into Python is a really good tutorial.

---

### Post by GeneralZod on 2005-11-03
Python is a command-line tool, so, as you note, it would have no icon.

Simply typing "python" into a terminal, if it is installed, will take you into interactive mode within the terminal, which isn't that much use.  There really is no "window" to bring up: python is simply an interpreter for the python language, so its sole purpose is to run python scripts.

What exactly happens when you type "python" and press enter?  If it outputs something like this

```

Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

then it is working correctly; otherwise, something is wrong :)

Hope this helps,
Simon

---

### Post by swerner on 2005-11-03
When you type python at the terminal you should get:
```
Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

```
If you don't that's really strange, because it most certainly required by Ubuntu, you really have to try hard to uninstall it.  What you are probably wanting is a Python IDE (Integrated Development Environment).  I suggest Eric, at the command line type
```
sudo apt-get install eric
```
Or you can install using synaptic.  Once installed you will have a new menu entry at Application>Programming>Eric Python IDE.

Enjoy ;)

---

### Post by otware on 2005-11-03
yes that is what happens when i type python into command line.

and thanks for the eric (Idle) tip, what I want is the IDE.

---

### Post by otware on 2005-11-04
OK 'sudo apt-get install eric' doesn't work.
'E: Couldn't find package eric'

---

### Post by psychicdragon on 2005-11-04
You need to enable the extra repositories. Here's a Howto from the wiki: [URL="https://wiki.ubuntu.com/AddingRepositoriesHowto"]
Click me![/URL]

---

### Post by otware on 2005-11-04
ok i enabled the universe and mulitiverse, and all of the official ubuntu repositories. do you think I will need any others?

---

### Post by otware on 2005-11-04
OK it tries to download some files automatically. for some reason it was 'downloading' stuff from the cdrom, and now the cd drive won't open.

---

### Post by psychicdragon on 2005-11-04
nautilus can unmount the cdrom for you.

or 
```
umount /media/cdrom
eject
```

---

### Post by SickTwist on 2005-11-04
You can disable using the CD as a repository if you'd rather install everything from the Internet (much easier if you have broadband). Put a "#" (without quotes) at the beginning of the line that starts with "deb cdrom". Then update your list of available packages:
```
sudo apt-get update
```

---

### Post by Shaggy on 2005-11-04
Its getting files off the cdrom more than likely because you never took the cdrom off of your repository list when you did your original install, so that's the first place it looks.  You can remove it using either the command line like the poster above me said, or using synaptic.

Now for a good IDE to use for python I like DrPython.  Make sure you have universe and multiverse in your repositories and it should be right there.

---

### Post by otware on 2005-11-04
i'll remove the cd repository, thanks for the advise.

i had some trouble adding universe and multiverse repositories using synaptic - it said that they were obsolete or something (can't remember exact wording, but something to that effect). So i need to know how to add repositories in either terminal or using text configuration files.

---

### Post by Kyral on 2005-11-04
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

(Go Aysiu for having this in his sig :P)

---

### Post by otware on 2005-11-06
Im gonna add the extra repositories soon. btw synaptic will install all this for me, won't it? (just when i used kubuntu, kynaptic didn't actually install some of the packages, and left them for me to install manually or something).

---

### Post by swerner on 2005-11-06
Synaptic will install it no probllem.

---

### Post by otware on 2005-11-06
OK I can't update my repository list. it gives me this error message when i use synaptic to update it. 
> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)


what am i supposed to do about this?

---

### Post by grumpymole on 2005-11-06
otware,

IIRC, you get these messages the first time you run update against new repositories.  They are indicating that they cannot find any previous records of these reporistories on your local system.

In synaptic, do a Reload and it should download lists from these repositories to your local disk and fix these errors.

---

### Post by minnew on 2006-05-07
[QUOTE=swerner]When you type python at the terminal you should get:
```
Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

```
If you don't that's really strange, because it most certainly required by Ubuntu, you really have to try hard to uninstall it.  What you are probably wanting is a Python IDE (Integrated Development Environment).  I suggest Eric, at the command line type
```
sudo apt-get install eric
```
Or you can install using synaptic.  Once installed you will have a new menu entry at Application>Programming>Eric Python IDE.

Enjoy ;)[/QUOTE]


I tried to install Eric, but I got several dependency warnings that would not let me install...tried both with synaptic and at the command line, as above...
what could be wrong?

thanks

---

### Post by swerner on 2006-05-08
[QUOTE=minnew]I tried to install Eric, but I got several dependency warnings that would not let me install...tried both with synaptic and at the command line, as above...
what could be wrong?

thanks[/QUOTE]

What dependancy warnings did you get?

---

