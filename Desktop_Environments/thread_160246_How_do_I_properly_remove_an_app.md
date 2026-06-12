---
title: "How do I properly remove an app?"
date: 2006-04-14
forum: Desktop Environments
---

### Post by ardchoille on 2006-04-14
Scenario:
I install an app with "sudo apt-get install <appname>" and then later decide I no longer want it. I did a test using 3ddesktop, here are the results:

app: 3ddesktop
deps: libimlib2 libungif4g

```

[user@~ 09:45:53]$ sudo updatedb
[user@~ 09:44:03]$ locate 3ddesktop
[user@~ 09:44:24]$ locate libimlib2
[user@~ 09:44:38]$ locate libungif4g
[user@~ 09:44:38]$

```

As you can see, 3ddesktop and its deps are not installed. So, I install 3ddesktop:

```

[user@~ 09:44:53]$ sudo apt-get install 3ddesktop
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libimlib2 libungif4g
Suggested packages:
  xbindkeys
The following NEW packages will be installed
  3ddesktop libimlib2 libungif4g
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 326kB of archives.
After unpacking 1143kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get: 1 http://archive.ubuntu.com dapper/main libungif4g 4.1.4-1 [57.2kB]
Get: 2 http://archive.ubuntu.com dapper/main libimlib2 1.2.1-2 [193kB]
Get: 3 http://archive.ubuntu.com dapper/universe 3ddesktop 0.2.9-5.1ubuntu1 [76.2kB]
Fetched 326kB in 3s (88.0kB/s)
Selecting previously deselected package libungif4g.
(Reading database ... 77660 files and directories currently installed.)
Unpacking libungif4g (from .../libungif4g_4.1.4-1_i386.deb) ...
Selecting previously deselected package libimlib2.
Unpacking libimlib2 (from .../libimlib2_1.2.1-2_i386.deb) ...
Selecting previously deselected package 3ddesktop.
Unpacking 3ddesktop (from .../3ddesktop_0.2.9-5.1ubuntu1_i386.deb) ...
Setting up libungif4g (4.1.4-1) ...

Setting up libimlib2 (1.2.1-2) ...

Setting up 3ddesktop (0.2.9-5.1ubuntu1) ...
[user@~ 09:45:53]$

```

And proof of the installation:

```

[user@~ 09:45:53]$ sudo updatedb
[user@~ 09:46:19]$ locate 3ddesktop
/etc/3ddesktop
/etc/3ddesktop/3ddesktop.conf
/var/lib/dpkg/info/3ddesktop.conffiles
/var/lib/dpkg/info/3ddesktop.list
/var/lib/dpkg/info/3ddesktop.md5sums
/var/cache/apt/archives/3ddesktop_0.2.9-5.1ubuntu1_i386.deb
/usr/share/doc/3ddesktop
/usr/share/doc/3ddesktop/README.Debian
/usr/share/doc/3ddesktop/TODO
/usr/share/doc/3ddesktop/README.windowmanagers
/usr/share/doc/3ddesktop/changelog.gz
/usr/share/doc/3ddesktop/copyright
/usr/share/doc/3ddesktop/changelog.Debian.gz
/usr/share/doc/3ddesktop/README.gz
/usr/share/3ddesktop
/usr/share/3ddesktop/digits.bmp
[user@~ 09:46:30]$ locate libimlib2
/var/lib/dpkg/info/libimlib2.shlibs
/var/lib/dpkg/info/libimlib2.list
/var/lib/dpkg/info/libimlib2.postinst
/var/lib/dpkg/info/libimlib2.postrm
/var/lib/dpkg/info/libimlib2.md5sums
/var/cache/apt/archives/libimlib2_1.2.1-2_i386.deb
/usr/share/doc/libimlib2
/usr/share/doc/libimlib2/copyright
/usr/share/doc/libimlib2/README
/usr/share/doc/libimlib2/TODO
/usr/share/doc/libimlib2/AUTHORS
/usr/share/doc/libimlib2/changelog.Debian.gz
/usr/share/doc/libimlib2/changelog.gz
[user@~ 09:46:39]$ locate libungif4g
/var/lib/dpkg/info/libungif4g.shlibs
/var/lib/dpkg/info/libungif4g.list
/var/lib/dpkg/info/libungif4g.postinst
/var/lib/dpkg/info/libungif4g.postrm
/var/lib/dpkg/info/libungif4g.md5sums
/var/cache/apt/archives/libungif4g_4.1.4-1_i386.deb
/usr/share/doc/libungif4g
/usr/share/doc/libungif4g/changelog.Debian.gz
/usr/share/doc/libungif4g/changelog.gz
/usr/share/doc/libungif4g/NEWS.gz
/usr/share/doc/libungif4g/gif89.txt.gz
/usr/share/doc/libungif4g/README
/usr/share/doc/libungif4g/lzgif.txt.gz
/usr/share/doc/libungif4g/copyright
/usr/share/doc/libungif4g/UNCOMPRESSED_GIF.gz
[user@~ 09:55:24]$

```

Now we see that 3ddesktop and its deps are installed. Now, let's remove it with the --purge option:

```

[user@~ 09:55:24]$ sudo apt-get --purge remove 3ddesktop
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  3ddesktop*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 459kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 77715 files and directories currently installed.)
Removing 3ddesktop ...
Purging configuration files for 3ddesktop ...
[user@~ 09:56:17]$

```

We can already see that 3ddesktop was removed, but its deps were not. Now, we'll look to see if 3ddesktop and its deps were uninstalled:

```

[user@~ 09:56:17]$ sudo updatedb
[user@~ 09:57:21]$ locate 3ddesktop
/var/cache/apt/archives/3ddesktop_0.2.9-5.1ubuntu1_i386.deb
[user@~ 09:57:41]$ locate libimlib2
/var/lib/dpkg/info/libimlib2.shlibs
/var/lib/dpkg/info/libimlib2.list
/var/lib/dpkg/info/libimlib2.postinst
/var/lib/dpkg/info/libimlib2.postrm
/var/lib/dpkg/info/libimlib2.md5sums
/var/cache/apt/archives/libimlib2_1.2.1-2_i386.deb
/usr/share/doc/libimlib2
/usr/share/doc/libimlib2/copyright
/usr/share/doc/libimlib2/README
/usr/share/doc/libimlib2/TODO
/usr/share/doc/libimlib2/AUTHORS
/usr/share/doc/libimlib2/changelog.Debian.gz
/usr/share/doc/libimlib2/changelog.gz
[user@~ 09:58:27]$ locate libungif4g
/var/lib/dpkg/info/libungif4g.shlibs
/var/lib/dpkg/info/libungif4g.list
/var/lib/dpkg/info/libungif4g.postinst
/var/lib/dpkg/info/libungif4g.postrm
/var/lib/dpkg/info/libungif4g.md5sums
/var/cache/apt/archives/libungif4g_4.1.4-1_i386.deb
/usr/share/doc/libungif4g
/usr/share/doc/libungif4g/changelog.Debian.gz
/usr/share/doc/libungif4g/changelog.gz
/usr/share/doc/libungif4g/NEWS.gz
/usr/share/doc/libungif4g/gif89.txt.gz
/usr/share/doc/libungif4g/README
/usr/share/doc/libungif4g/lzgif.txt.gz
/usr/share/doc/libungif4g/copyright
/usr/share/doc/libungif4g/UNCOMPRESSED_GIF.gz
[user@~ 09:58:43]$

```

It seems that 3ddesktop was indeed removed, but its deps are still installed. If I install and uninstall apps on a regular basis, my hard drive would eventually fill up with packages that I am not using.

So, my question:  Using **only command line tools**, how do I uninstall an app **and** its deps and related config files? If this is not possible for some reason, how do I clean up my hard drive of all packages and config files which are no longer used/needed?

---

### Post by aysiu on 2006-04-14
apt-get will not remember what you installed along with a package.

If you want that functionality, you need to use aptitude: ```
sudo aptitude update
sudo aptitude install package
``` Later on, ```
sudo aptitude remove package
```

In the meantime, use *deborphan* to try to locate installed packages that have no other packages dependent on them.

---

### Post by ardchoille on 2006-04-14
[QUOTE=aysiu]apt-get will not remember what you installed along with a package.

If you want that functionality, you need to use aptitude: ```
sudo aptitude update
sudo aptitude install package
``` Later on, ```
sudo aptitude remove package
```

In the meantime, use *deborphan* to try to locate installed packages that have no other packages dependent on them.[/QUOTE]
Thank you very much. However, using aptitude doesn't remove a package AND its deps and config files. Some files are still left behind. See my next post.

---

### Post by ardchoille on 2006-04-14
Well it seems my joy was short-lived. Either I did something wrong or aptitude doesn't uninstall everything either:

I uninstalled 3ddesktop, libimlib2 and libungif4g (including all of their config files). Then I did a sudo updatedb, then locate returned nothing for the three packages. So, I know everything was uninstalled and removed. Then I did a sudo aptitude install 3ddesktop and then:

```

[user@~ 10:39:55]$ sudo aptitude remove 3ddesktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  libimlib2 libungif4g
The following packages will be REMOVED:
  3ddesktop
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1143kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 77715 files and directories currently installed.)
Removing 3ddesktop ...
Removing libimlib2 ...
Removing libungif4g ...
[user@~ 10:40:47]$ sudo updatedb
[user@~ 10:42:05]$ locate 3ddesktop
/etc/3ddesktop
/etc/3ddesktop/3ddesktop.conf
/var/lib/dpkg/info/3ddesktop.list
/var/cache/apt/archives/3ddesktop_0.2.9-5.1ubuntu1_i386.deb
[user@~ 10:42:11]$ locate libimlib2
/var/lib/dpkg/info/libimlib2.list
/var/lib/dpkg/info/libimlib2.postrm
/var/cache/apt/archives/libimlib2_1.2.1-2_i386.deb
[user@~ 10:42:42]$ locate libungif4g
/var/lib/dpkg/info/libungif4g.list
/var/lib/dpkg/info/libungif4g.postrm
/var/cache/apt/archives/libungif4g_4.1.4-1_i386.deb
[user@~ 10:42:50]$

```

There are still files on my hard drive that I won't need. How do I get rid of them all?

This is why I re-install the OS every six months.. it's the only way I know of to keep the hard drive clean and free of files/packages I no longer use. If anyone has a better suggestion as to how to remove a package and all its deps and config files, or how to clean up the hard drive of files/packages I no longer use/want, then I am open to suggestions.

---

### Post by aysiu on 2006-04-14
These four files are bothering you?
/etc/3ddesktop
/etc/3ddesktop/3ddesktop.conf
/var/lib/dpkg/info/3ddesktop.list
/var/cache/apt/archives/3ddesktop_0.2.9-5.1ubuntu1_i386.deb

The first is just a directory.
The fourth is an archived .deb package. You can change your Synaptic settings (or maybe an apt-get or aptitude parameter) to not keep .deb packages after you've installed the software.

I promise you a .conf and .list file aren't cluttering up your hard drive. Other than that, I don't know what to tell you.

How about not installing programs you'll later decide you don't need? 

Seriously. If it bothers you that much to have the programs not fully uninstall, not even leaving a trace of anything behind, do this:

The next time you feel like installing a program you're not sure you want to keep, pop in a Ubuntu live CD and install it via the live CD. Play around with it for a bit. If you decide you don't like it, reboot, and no harm done. The app was "installed" only to your computer's RAM. If you decide you do like it, install it on your hard drive installation.

Otherwise, suck it up, or manually delete those two extra files.

---

### Post by ardchoille on 2006-04-14
[QUOTE=aysiu]These four files are bothering you?
/etc/3ddesktop
/etc/3ddesktop/3ddesktop.conf
/var/lib/dpkg/info/3ddesktop.list
/var/cache/apt/archives/3ddesktop_0.2.9-5.1ubuntu1_i386.deb

The first is just a directory.
The fourth is an archived .deb package. You can change your Synaptic settings (or maybe an apt-get or aptitude parameter) to not keep .deb packages after you've installed the software.

I promise you a .conf and .list file aren't cluttering up your hard drive. Other than that, I don't know what to tell you.

How about not installing programs you'll later decide you don't need? 

Seriously. If it bothers you that much to have the programs not fully uninstall, not even leaving a trace of anything behind, do this:

The next time you feel like installing a program you're not sure you want to keep, pop in a Ubuntu live CD and install it via the live CD. Play around with it for a bit. If you decide you don't like it, reboot, and no harm done. The app was "installed" only to your computer's RAM. If you decide you do like it, install it on your hard drive installation.

Otherwise, suck it up, or manually delete those two extra files.[/QUOTE]
I'm sorry, please forgive me.. I was under the assumption that "uninstall" or "remove" meant "uninstall/remove everything that was installed". I had no idea that "uninstall" meant "remove some things and leave various files laying around so the user has to go out of their way, after using package **manager**, and manually remove files".

Silly me.

---

### Post by aysiu on 2006-04-14
[QUOTE=ardchoille]I'm sorry, please forgive me.. I was under the assumption that "uninstall" or "remove" meant "uninstall/remove everything that was installed". I had no idea that "uninstall" meant "remove some things and leave various files laying around so the user has to go out of their way, after using package **manager**, and manually remove files".

Silly me.[/QUOTE] Maybe you should file a bug report on it:
[https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by ardchoille on 2006-04-14
[QUOTE=aysiu]These four files are bothering you?
/etc/3ddesktop
/etc/3ddesktop/3ddesktop.conf
/var/lib/dpkg/info/3ddesktop.list
/var/cache/apt/archives/3ddesktop_0.2.9-5.1ubuntu1_i386.deb

The first is just a directory.
The fourth is an archived .deb package. You can change your Synaptic settings (or maybe an apt-get or aptitude parameter) to not keep .deb packages after you've installed the software.

I promise you a .conf and .list file aren't cluttering up your hard drive. Other than that, I don't know what to tell you.

How about not installing programs you'll later decide you don't need? 

Seriously. If it bothers you that much to have the programs not fully uninstall, not even leaving a trace of anything behind, do this:

The next time you feel like installing a program you're not sure you want to keep, pop in a Ubuntu live CD and install it via the live CD. Play around with it for a bit. If you decide you don't like it, reboot, and no harm done. The app was "installed" only to your computer's RAM. If you decide you do like it, install it on your hard drive installation.

Otherwise, suck it up, or manually delete those two extra files.[/QUOTE]
Well, it's just my opinion that a proper package manager would do proper package management so the user wouldn't have to go that far out of their way to perform what you suggested. Or something to let the user know that "the depencies for a previously installed application are now dependencies for a subsiquently installed applicatiion. Would you like both applications to be removed? (Y/n)" or something to that effect.

But, maybe my expectations are too high. I'll see if I can find a better package manager than what Ubuntu offers.

---

### Post by aysiu on 2006-04-14
[QUOTE=ardchoille]But, maybe my expectations are too high. I'll see if I can find a better package manager than what Ubuntu offers.[/QUOTE] I think you should file a bug report. I don't know what else there is in Debian-based distros besides Synaptic, apt-get, aptitude, and Adept.

---

### Post by ardchoille on 2006-04-14
[QUOTE=aysiu]I think you should file a bug report. I don't know what else there is in Debian-based distros besides Synaptic, apt-get, aptitude, and Adept.[/QUOTE]
Good idea. Thank you very much for the replies. Oh, and I really like your avatar. Did you design that yourself?

**UPDATE:** Bug #39589 filed at [https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by aysiu on 2006-04-14
[QUOTE=ardchoille]Good idea. Thank you very much for the replies. Oh, and I really like your avatar. Did you design that yourself?[/QUOTE] Actually, my wife did. I like it, too. I have no design sense myself.

P.S. I hope I didn't come off as cheeky or mean in this thread. I'm just trying to be practical, and I think your best bet may be filing a bug report and manually deleting in the meantime.

---

### Post by ardchoille on 2006-04-14
[QUOTE=aysiu]Actually, my wife did. I like it, too. I have no design sense myself.[/QUOTE]
I love graphics design and I am quite good at it. However, I can't code to save my life.

[QUOTE=aysiu]P.S. I hope I didn't come off as cheeky or mean in this thread. I'm just trying to be practical, and I think your best bet may be filing a bug report and manually deleting in the meantime.[/QUOTE]
No worries. You are still one of the great folks who's replies I look forward to :)
I filed the bug and manually removed the files. It's just a huge pet peave of mine that one never cause another human being to go out of their way.

**Possible fix**
Perhaps apt-get and aptitude need new options:

**--also-remove-deps**   Unless those deps become deps of a subsequently installed package, in which case inform the user as to why the deps cannot be removed without removing a subsequently installed package.

---

### Post by aysiu on 2006-04-14
[QUOTE=ardchoille]I love graphics design and I am quite good at it. However, I can't code to save my life.[/quote] You got me beat. I can't design *or* code.

> 
Perhaps apt-get and aptitude need new options:

**--also-remove-deps**   Unless those deps become deps of a subsequently installed package, in which case inform the user as to why the deps cannot be removed without removing a subsequently installed package. Actually, I think *aptitude* is supposed to do this already. The trick is that you have to install it with *aptitude* in order for the *aptitude remove* to know which dependencies were installed with it.

---

### Post by ardchoille on 2006-04-14
[QUOTE=aysiu]You got me beat. I can't design *or* code.

 Actually, I think *aptitude* is supposed to do this already. The trick is that you have to install it with *aptitude* in order for the *aptitude remove* to know which dependencies were installed with it.[/QUOTE]
Yes, I uninstalled everything, did a sudo updatedb and locate <file_name> to confirm that everything was uninstalled. Then I did sudo aptitude install 3ddesktop and used aptitude to remove it and that is what left those extra files I had to remove manually.

No problem, since I only installed this one package and kept an eye on everything to know where everything was installed. It's when I sudo apt-get install <300 packages here> that I can't keep everything straight - in which case I feel that I shouldn't have to keep it all straight, it's the package manager's job to keep it all straight.

---

### Post by ardchoille on 2006-04-14
[QUOTE=aysiu]You got me beat. I can't design *or* code.

 Actually, I think *aptitude* is supposed to do this already. The trick is that you have to install it with *aptitude* in order for the *aptitude remove* to know which dependencies were installed with it.[/QUOTE]
Yes, I uninstalled everything, did a sudo updatedb and locate <file_name> to confirm that everything was uninstalled. Then I did sudo aptitude install 3ddesktop and used aptitude to remove it and that is what left those extra files I had to remove manually.

No problem, since I only installed this one package and kept an eye on everything to know where everything was installed. It's when I sudo apt-get install <300 packages here> that I can't keep everything straight - in which case I feel that I shouldn't have to keep it all straight, it's the package manager's job to keep it all straight.

---

### Post by ardchoille on 2006-08-01
Looks like someone is actively working on this :)

[https://launchpad.net/bugs/39589](https://launchpad.net/bugs/39589)

Looks like the apt program in Edgy will have a new option "--auto-remove". I just got an email:

> 
The current version of apt in edgy has support for the tracking of automatically installed dependencies. This means that if you install 3ddesktop and it requires libimlib2 when you remove 3ddesktop later apt will know that it can auto-remove libimlib2 too.

Use:

$ sudo apt-get remove --auto-remove 3ddesktop

to use this feature. Feedback is welcome.

Cheers,
 Michael

** Changed in: apt (Ubuntu)
     Assignee: (unassigned) => Michael Vogt
       Status: Needs Info => Fix Released

-- Package manager not correctly managing packages [https://launchpad.net/bugs/39589](https://launchpad.net/bugs/39589) 


I'm sure glad I filed that bug :)

---

### Post by verbatim210 on 2006-08-03
hey aysiu, i did...

sudo aptitude remove apache2
sudo aptitude install apache2

and my apache is still broken.  whats going on, something to do with the conf file?

[I] * Forcing reload of apache 2.0 web server...                                                                                                                                : No such file or directorybled/*.load
: No such file or directorybled/*.conf
: No such file or directorynf
: No such file or directorynf
: No such file or directory^.#]*
: No such file or directorynf
: No such file or directoryabled/[^.#]*
apache2: Could not determine the server's fully qualified domain name, using 127
httpd (pid 8425) already running[/I]

but when i installed the default apache2.conf still had problems, instead of the above jiberish it outputted "* Forcing reload of apache 2.0 web server...  fail"

---

### Post by verbatim210 on 2006-08-03
i've also tried 
sudo aptitude purge apache2

---

