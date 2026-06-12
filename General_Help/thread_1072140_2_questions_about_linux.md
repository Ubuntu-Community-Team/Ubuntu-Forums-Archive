---
title: "2 questions about linux"
date: 2009-02-17
forum: General Help
---

### Post by stek_87 on 2009-02-17
Hello!

I'm a bit new to linux and I have questions I would like to get answered.

I am going to put windows in realtion to my questions about linux..

In windows we have c:\program files for installed applications. What is the corresponding path(s) in linux?

In windows there is a register which can be edited by regedit. The register is a database that contains a lot of information and settings for the OS and for almost every installed application that is installed. Is there any similar "function" in linux?

If **yes**, where is it? How can I edit it? What is it used for?
If **no**, why doesn't linux need this "function"

RGDS
/S

---

### Post by dzark on 2009-02-17
Yeahbutno..

As for c:/program files.. There is a /bin for really low level commands (like cp & mv - copy and move) and the low level config files are generally in /etc...

More userspace orientated programs end up in /usr/bin, with shared libraries and such in /usr/share, manual (documentation) pages in /usr/man

As for a registry, it's a major achillies heel in design. A similar program exists, called gconf-editor (for gnome), but settings files are split into a directory/file style, and only really affects userspace desktopy stuff.

Try going to your home directory, pressing Ctrl-H to view hidden, and entering folders called .gconf2 and .config

As for why it's not needed, most of your settings are editable in the preferences of that particular application, or during normal use. The majority of my regedt32 use is removing startup crap (System->Preferences->Session), trying to fix broken install/uninstalls, or other nasty-ness that simply doesn't really happen.

---

### Post by x33a on 2009-02-17
for linux filesystem structure, read here.

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

as for the registry, linux doesn't store configuration that way. all information is stored in conf files. most of these files are located under /etc.

read more on the same in the above link.

---

### Post by stek_87 on 2009-02-17
Thanks! That answered my questions 100%.

Here comes one more.

If a program consists of .conf -files in /etc/... for settings and program files in /usr/bin, I guess it is possible to simply move an application from one system to another. Am i right? How many places will I have to copy files from? (I understand it will depend on what application it is..)

/S

---

### Post by dzark on 2009-02-17
Totally depends on the application...

Easiest way, is to find the .deb file that it gets installed with (will probably be in /var/cache/apt/archives) and take that and the .conf file to your usb/whatever..

Install first, then move the orig program.conf to program.conf.back and the edited one in place ;) 

That way you have an original backup to refer to for when things go wrong (and .conf files take up very little room)

---

### Post by stek_87 on 2009-02-17
> **dzark said:**
> Totally depends on the application...

Easiest way, is to find the .deb file that it gets installed with (will probably be in /var/cache/apt/archives) and take that and the .conf file to your usb/whatever..

Install first, then move the orig program.conf to program.conf.back and the edited one in place ;) 

That way you have an original backup to refer to for when things go wrong (and .conf files take up very little room)

sounds pretty smart, and easy :)

How about Uninstalling an application? I know I can uninstall many apps by typing apt-get remove *application*, but how about those applications which is installed by running a .deb -file?

Do we have same problem with linux, that it's hard to completly get rid of an earlier installed application?

/S

---

### Post by x33a on 2009-02-17
deb files can be removed using 
```
dpkg -r filename
```
or through synaptic.

---

### Post by dzark on 2009-02-17
APT is great for handling dependencies these days..
```

sudo aptitude remove programname
```

will uninstall a program, sometimes leaving behind a small bit of config i find usefull incase you re-install it later (what is a 1kilobyte file these days?)

If you're having issues with config files being persistent, use

```
sudo aptitude purge programname
```

that'll remove all config

Both of these two options are also quite obvious if you're using Synaptic Packet Manager (essentially a GUI for apt) .. Right click on a program, and it gives you the install, reinstall, remove and 'completely remove including all config files'

---

### Post by stek_87 on 2009-02-17
> **x33a said:**
> deb files can be removed using 
```
dpkg -r filename.deb
```
or through synaptic.

Thanks.

And this command removes everything that the .deb file installed in the first place?

The issue in windows, leaving some parts of program (in registry) does not exist in linux?

---

### Post by geirha on 2009-02-17
> **stek_87 said:**
> sounds pretty smart, and easy :)

How about Uninstalling an application? I know I can uninstall many apps by typing apt-get remove *application*, but how about those applications which is installed by running a .deb -file?

Do we have same problem with linux, that it's hard to completly get rid of an earlier installed application?

/S

Any package installed via the repositories **and** via .deb files are uninstallable with apt, so the procedure is the same. You'll need to use the package's name as the argument to apt-get remove. You can usually identify that from the name of the .deb-package. Everything up to the first '_' is the package name. Also you can search for installed packages with
```

aptitude search '~i foo'   # lists all installed packages that contains the word "foo".

```

If you are curious as to what files a particular package installs, you can do ```
dpkg -L *package-name*
```

---

### Post by stek_87 on 2009-02-17
> **dzark said:**
> APT is great for handling dependencies these days..
```

sudo aptitude remove programname
```

will uninstall a program, sometimes leaving behind a small bit of config i find usefull incase you re-install it later (what is a 1kilobyte file these days?)

If you're having issues with config files being persistent, use

```
sudo aptitude purge programname
```

that'll remove all config

Both of these two options are also quite obvious if you're using Synaptic Packet Manager (essentially a GUI for apt) .. Right click on a program, and it gives you the install, reinstall, remove and 'completely remove including all config files'

Ok.
I'm only running ubuntu linux in cli. But thanks anyway.

What command is the best way to go in cli?
dpkg -r filename.deb or aptitude remove programname?

---

### Post by dzark on 2009-02-17
Aptitude seems a bit more advanced/bloated than dpkg.. Both work on the same model, package list etc. Dpkg does exactly what you tell it, while aptitude will tend to give a bit more helpful solutions to newbies when dealing with dependencies, also telling you if packages are unused, and offer to automagically remove them.

---

### Post by geirha on 2009-02-17
> **stek_87 said:**
> Thanks.

And this command removes everything that the .deb file installed in the first place?

The issue in windows, leaving some parts of program (in registry) does not exist in linux?

Uninstalling a package it will remove its binaries, libraries, documentation, etc. Basically all files you see when you run ```
dpkg -L *package-name*
``` on an installed package. If it has configuration in /etc, this is not uninstalled. If you also want that configuration gone, you need to purge the package ```
sudo aptitude purge *package-name*
```
To get a list of packages which are uninstalled, but still has configuration around, run ```
aptitude search '~c'
```

Lastly, GUI applications that you run as your own user, usually stores configuration in your homefolder. Some use gconf, some use a hidden directory, and some just use a hidden file. Open nautilus on your homefolder ( Places -> Home folder ), hit Ctrl+h to toggle showing hidden files, and have a look. The configuration files usually has the same name as the application (or close to it); some applications put it in the hidden directory .config, which is the newer, preferred place to put configuration.

Neither removing nor purgin a package will ever remove files from your homedir, so you need too clean that up yourself if you want all traces gone.

---

### Post by x33a on 2009-02-17
> **dzark said:**
> Aptitude seems a bit more advanced/bloated than dpkg.. Both work on the same model, package list etc.

apt is a frontend for dpkg, and aptitude is a frontend for apt. so dpkg is always involved with installation (apart from compiling).

[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

---

### Post by stek_87 on 2009-02-17
Thanks alot to dzark, x33a and geirha who have taken time to answer my questions.

Now I am satisfied (for the moment) ;)

These answers was for me very helpful!

/S

---

