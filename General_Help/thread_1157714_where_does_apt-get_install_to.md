---
title: "where does apt-get install to?"
date: 2009-05-13
forum: General Help
---

### Post by slk0 on 2009-05-13
When I install a program with apt-get, how can I determine what directory it was installed to?

Example: I installed ViewVC with the command

  sudo apt-get install viewvc

and it says it installed correctly.  However, the documentation for this program ([http://viewvc.tigris.org/source/browse/*checkout*/viewvc/trunk/INSTALL](http://viewvc.tigris.org/source/browse/*checkout*/viewvc/trunk/INSTALL)) says to run various commands inside the ViewVC installation directory, and it doesn't say what that directory is.

I've had the same problem with other programs as well.  Often I can find it by trial and error just poking around in /usr/bin, /usr/lib, /etc, /opt, and so on, but is there a more systematic way?  I am fairly new to Linux and longing for the consistency of "C:\Program Files" on Windows.

---

### Post by geraldvillorente on 2009-05-13
I'm using the "locate" command for this kind of task...

---

### Post by stathol on 2009-05-13
If the package has already been installed, you can list the files that it installs with:

```
dpkg -L [package name]
```

If you want to list the files installed by a package that hasn't yet been installed, you can use apt-file:

```
apt-file list [package name]
```

However, this won't work if you haven't built a cache for apt-file yet, and may give bad info if the cache is out-of-date. Either way, you can update it with:

```
sudo apt-file update
```

Presently I seem to be getting some weird 404 errors with the jaunty repositories when I do this :confused:, but maybe you'll have better luck...

---

### Post by stathol on 2009-05-13
Oh, and more generically, if you want a better feel for how files are organized in Linux, check out:

[Filesystem Hierarchy Standard](http://www.pathname.com/fhs/)

Probably no one on earth follows it 100%, but Ubuntu and most distros attempt to be generally in compliance with it.

---

### Post by MaxIBoy on 2009-05-13
As a general answer to your question, the .deb package itself says where all the files need to go (i.e. the .deb package could say /home/a_user_that_doesn't_exist/foo/chicken/rice/random/stuff and all those directories would be created.)

Stathol has the best answer for your particular problem, though.

---

### Post by dcstar on 2009-05-13
> **slk0 said:**
> When I install a program with apt-get, how can I determine what directory it was installed to?
.........

[LIST=1]
[*]Firstly, don't use the command line when Synaptic (or whatever GUI tool there is) will do the job perfectly - that is what these things are for.
[*]Secondly, in Synaptic you simply look at the properties of the installed packages to see where the files are installed.
[/LIST]

---

### Post by MaxIBoy on 2009-05-13
> **dcstar said:**
> 
[LIST=1]
[*]Firstly, don't use the command line when Synaptic (or whatever GUI tool there is) will do the job perfectly - that is what these things are for.
[*]Secondly, in Synaptic you simply look at the properties of the installed packages to see where the files are installed.
[/LIST]

You must be thinking of DOS, the BASH shell is really easy to use. Be careful how you describe the command line, otherwise people start to flip out when you give them command line instructions.

---

