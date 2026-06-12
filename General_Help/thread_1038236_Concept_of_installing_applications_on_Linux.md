---
title: "Concept of installing applications on Linux"
date: 2009-01-12
forum: General Help
---

### Post by NeonBible on 2009-01-12
Linux newbie here.  I am just trying to understand how applications are installed under Linux.

Ubuntu gives us the luxury of a package manager. We look up the repository and hit install.

But I notice a lot of Linux apps only have the source available.  What do I need to do if I want to install one of these apps and they are not availble for a the repository or built specifically for Ubuntu/Debian?

Also if I uninstall an app using package manager, does it remove everything which it had installed in the first place?  One thing I love about Mac is that I can just drag the app into the trash can, and delete a few pref files in the usual places.  Windows just creates a bit mess.  How does Linux sit in with this respect?

---

### Post by ugm6hr on 2009-01-12
To learn how to compile from source - see the Compiling section in this tutorial: [http://ubuntuforums.org/showthread.php?t=644478](http://ubuntuforums.org/showthread.php?t=644478)

If you use Add/Remove or Synaptic to uninstall, it will uninstall most additional (now unnecessary) components.  However, "aptitude" used from the command line is slightly more powerful and removes everything, provided it is used to install in the first place.  Synaptic uses "apt-get" (I believe), and I don't know if there is a GUI way to remove all unnecessary files.

This is what I recommend if you use the GUI installation procedure:
```
sudo apt-get remove package_name
sudo apt-get autoremove
```

If you want to remove the downloaded .debs, this has to be done en masse:
```
sudo apt-get clean
```

You can use "purge" instead of "remove" to delete .debs as you go, but I don't think it works with autoremove.

---

### Post by mcduck on 2009-01-12
You have two options when uninstalling packages with the Synaptic PAckage Manager (or actually any package management tool).

"Mark for Removal" will only remove the package but leaves it's configuration files around. So if you re-install the package you don't need to configure it again.

"Mark for Complete Removal" will also remove the configuration files.

Since other packages may have been installed as dependencies for the original package you installed, you may wish to also remove them. The package manager knows what packages were installed as dependencies for something else and are not needed any more. In Synaptic, click the Status-button in the bottom left corner, and select "Installed (auto removable)" from the list on the left side.

The same things can be done from terminal. "sudo apt-get remove *package*" will remove the package but leave configuration files. "sudo apt-get purge *package*" will completely remove it, and "sudo apt-get autoremove" will remove all packages that were installed as dependencies but are no more needed.

Since Linux doesn't have registry like Windows even leaving the configuration files around would not create such a mess. They are just small text files that do nothing if the original program isn't used. (the biggest problem with Windows is that every setting is written into registry, which is a single file used for _everything_ and quickly grows into massive sizes which is what causes the system to become slower and slower over time)

Which ever way you remove the packages, personal setting files created in user's home directories will not be removed. You can remove them by hand if you want to but once again, they are only small text files, often smaller than 1kB in size.

---

### Post by NeonBible on 2009-01-12
Awesome thank you!

---

### Post by NeonBible on 2009-01-12
Oh I want to install XMMS using this - [http://www.pvv.ntnu.no/~knuta/xmms/](http://www.pvv.ntnu.no/~knuta/xmms/)

It mentions it does not add an entry to the menu.

How do I run it? I assume console, but where is it stored?

---

### Post by ugm6hr on 2009-01-12
Probably in /usr/bin/

Out of interest... XMMS is no longer developed.  What's wrong with audacious or XMMS2?

---

### Post by WitchCraft on 2009-01-12
> **NeonBible said:**
> 
I am just trying to understand how applications are installed under Linux.


Linux applications are installed from *.deb files, called debian packages.

A .deb file is the equivalent of setup.exe on windows.

The .deb file contains the program's description, it's dependencies, version, name, maintainer, author, etc, as well as installation scripts, post-installation scripts, and post removal scripts (and the program and its data, of course).

.deb files are installed by the progam dpkg.
To install for example "codeblocks.deb", you go to the console to the same directory as codeblocks.deb, and type:
dpkg -i codeblocks.deb

now the thing is that codeblocks.deb might depend on g++, wxwidgets, and other .debs. This is called dependencies.

Now if you have a large program, it might have a lot of dependencies, and worse, you might not know them all, and to find them out, install them in the right order etc. is very complex (it's called the dpkg-hell...).

That's why apt was written.
apt reads the .deb for you, gets all the dependencies (and the dependencies dependencies and so on...) and installs them for you. That's why apt is called a dpkg frontend.

apt gets it's information from a server REPOSITORY.
A repository is just a (very large) collection of .debs, plus a list of all these debs.

Now, apt must find repositories. it doesn't now where they are.
So there is a config file for apt: /etc/apt/sources.list
which lists all the repositories your apt searches.

You can add and remove repositories by adding / removing them from sources.list.

You'll find many more repositories on the internet than just the ubuntu and the debian ones. For example google distributes it's linux software via their own repository.


Now the way apt installs applications is, it downloads all the package lists from all repositories in sources.list.

then it searches all the package lists for the file you want to install, when it finds it, it downloads that file's dependency list from the server and resolves dependencies. it generates a list of everything it has to install, informs you if you have a conflict, eg. must remove another package to install your program, and informs you about the size your program will fill on the disk. You confirm with -y or abort with n

Then apt downloads all the .debs and passes them in the right order to dpkg.


Because the .debs must be transmitted over internet, they are compressed. You can just uncompress a .deb, and you will see that a .deb is basically only a (special) kind of .zip archive.



Progams that are on the repositories when through a process:
first they were sourcecode
then they were compiled for a specific system, eg. IntrepidIbex on i386 or amd64.
Compiling the sourcecode, using various tools, gives you the binaries.
Then these binaries are relieved of any debug info, copied to a package directory.
then an installation scrips gets written, an info file containing author, dependencies, description gets added to the package directory etc.
then the package directory gets compressed, and gets the file extension .deb
Then you can install it.


Or you can install directly from source, without makeing a .deb.
You have the sourcecode, and most of the times type:
```

./configure 
make
make install

```
and if everything went well, you're done.
Of course, ./configure make and make install will need a compiler, build dependencies and various other programs, which you might not have on your system, thus the procedure resulting in errors...



PS: APT doesn't check the repositories for package lists just because you install something.
You need to tell apt that manually by typing:
```

apt-get update

```

If you add a new repository for the first time, it's especially important, because if you don't run apt-get update, you will have the repository in your sources.list, but apt will not find anything, because you did not update the package list...


to search all repositories for example for g++, type:
```

apt-cache search g++

```

to install g++
```

apt-get install g++

```

to get the source of g++
```

apt-get source g++

```

to get the build-dependencies for g++
```

apt-get build-dep g++

```


to uninstall g++
```

apt-get remove g++

```

If you have problems installing some dependencies, type:
```

apt-get -f install PACKAGE_NAME

```

If APT bothers you about some packages that are no longer requires, run:
```

sudo apt-get autoremove

```

Note: The way that dpkg/apt handeles a package, you need to remove the package once it is partially installed (for example when an installation fails because power goes out).


If you run
```

sudo apt-get clean

```
it will clear all downloaded installer files.

If you don't want to always have to confirm an install with y[es], run:
```

apt-get -y install PACKAGE_NAME

```

---

