---
title: "How to set up GTKRadiant"
date: 2006-06-03
forum: Gaming &amp; Leisure
---

### Post by Dingo_aus on 2006-06-03
GTKRadiant is software that allows you to create maps for games such as Quake 1 - 4, Doom 3, ET etc etc

It is now GPL'd and available from [http://www.qeradiant.com/]("http://www.qeradiant.com/")

The latest beta binaries are usually available as .rpm packages from the front page there.

To install it for Ubuntu, this is what I found worked for me.
(I presume you have set up universe repositories etc already)

Download the gtkradiant*.rpm available and note where you put it. 

(Install "alien" on your ubuntu distro if you don't have it already. You can do this via adept or the synaptic package manager)

Make sure you close adept or synaptic after this step so alien an access the package database.

Open a console and change dir to the directory where you downloaded the .rpm to.

run "alien gtkradiant*.rpm"

This will produce a .deb file in the same directory downloaded the rpm to.

Install that .deb file (you can just click on it from a konqueror window if you want)

This will install GTKRadiant on your system. The executable is found at "/opt/gtkradiant/radiant.x86"

Before you can run it though you will need to fire up adept (or synaptic or whatever) again and install the "libgtkglext" library.

now run "/opt/gtkradiant/radiant.x86" and enjoy!


EDIT: BTW if you are using KDE like I am you will probably want to disable "Ctrl-Tab" desktop switching so Ctrl-Tab can be used with GTKRadiant instead. To do this, open a console and type "kcontrol" and then goto "Regional & Accessibility" > "Keyboard Shortcuts" and edit "Walk through desktop list" to "none" - that disables it.

---

### Post by amunimanghi on 2006-06-24
This is exactly what I did: ```

**ameen@manghi:~$** cd Desktop
**[B][B]ameen@manghi:~**/Desktop$[/B][/B] sudo alien -d gtkradiant-1.5.0-2006-03-02.i386.rpm
Password:
gtkradiant_1.5.0-8_i386.deb generated
**ameen@manghi:~/Desktop$** sudo apt-get install libgtkglext
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtkglext
**ameen@manghi:~/Desktop$** sudo apt-get update
Get:1 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://us.archive.ubuntu.com dapper Release
Ign http://wine.budgetdedicated.com dapper Release.gpg
Get:5 http://us.archive.ubuntu.com dapper-updates Release [30.9kB]
Hit http://archive.ubuntu.com dapper Release
Hit http://wine.budgetdedicated.com dapper Release
Hit http://archive.ubuntu.com dapper/universe Sources
Ign http://wine.budgetdedicated.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Get:6 http://users.lichtsnel.nl dapper-seveas Release.gpg [309B]
Hit ftp://cipherfunk.org dapper Release.gpg
Ign http://wine.budgetdedicated.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/main Packages
Get:7 http://us.archive.ubuntu.com dapper/restricted Packages [4571B]
Hit http://us.archive.ubuntu.com dapper/main Sources
Get:8 http://us.archive.ubuntu.com dapper/restricted Sources [1478B]
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://us.archive.ubuntu.com dapper/multiverse Sources
Get:9 ftp://ftp.free.fr dapper Release.gpg
Hit http://users.lichtsnel.nl dapper-seveas Release
Get:10 http://security.ubuntu.com dapper-security Release [30.9kB]
Hit http://wine.budgetdedicated.com dapper/main Packages
Get:11 http://us.archive.ubuntu.com dapper-updates/main Packages [37.7kB]
Get:12 ftp://cipherfunk.org dapper Release [1387B]
Hit http://users.lichtsnel.nl dapper-seveas/all Packages
Hit http://wine.budgetdedicated.com dapper/main Sources
Get:13 http://us.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:14 http://us.archive.ubuntu.com dapper-updates/main Sources [22.1kB]
Get:15 http://us.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:16 http://us.archive.ubuntu.com dapper-updates/universe Packages [8363B]
Get:17 http://us.archive.ubuntu.com dapper-updates/multiverse Packages [866B]
Get:18 http://us.archive.ubuntu.com dapper-updates/universe Sources [1823B]
Hit http://users.lichtsnel.nl dapper-seveas/all Sources
Get:19 http://us.archive.ubuntu.com dapper-updates/multiverse Sources [427B]
Get:20 http://security.ubuntu.com dapper-security/main Packages [25.1kB]
Ign ftp://ftp.free.fr dapper Release.gpg
Get:21 http://security.ubuntu.com dapper-security/restricted Packages [4253B]
Get:22 http://security.ubuntu.com dapper-security/main Sources [6227B]
Get:23 http://security.ubuntu.com dapper-security/restricted Sources [974B]
Get:24 http://security.ubuntu.com dapper-security/universe Packages [5271B]
Get:25 http://security.ubuntu.com dapper-security/multiverse Packages [1677B]
Get:26 http://security.ubuntu.com dapper-security/universe Sources [639B]
Get:27 ftp://ftp.free.fr dapper Release
Get:28 ftp://cipherfunk.org dapper/main Packages
Get:29 http://security.ubuntu.com dapper-security/multiverse Sources [533B]
Ign ftp://cipherfunk.org dapper/main Packages
Ign ftp://ftp.free.fr dapper Release
Get:30 ftp://cipherfunk.org dapper/main Sources
Get:31 ftp://ftp.free.fr dapper/free Packages
Ign ftp://ftp.free.fr dapper/free Packages
Get:32 ftp://ftp.free.fr dapper/non-free Packages
Ign ftp://cipherfunk.org dapper/main Sources
Hit ftp://cipherfunk.org dapper/main Packages
Ign ftp://ftp.free.fr dapper/non-free Packages
Hit ftp://cipherfunk.org dapper/main Sources
Get:33 ftp://ftp.free.fr dapper/free Sources
Ign ftp://ftp.free.fr dapper/free Sources
Get:34 ftp://ftp.free.fr dapper/non-free Sources
Ign ftp://ftp.free.fr dapper/non-free Sources
Hit ftp://ftp.free.fr dapper/free Packages
Hit ftp://ftp.free.fr dapper/non-free Packages
Hit ftp://ftp.free.fr dapper/free Sources
Hit ftp://ftp.free.fr dapper/non-free Sources
Fetched 186kB in 29s (6341B/s)
Reading package lists... Done
**ameen@manghi:~/Desktop$** sudo apt-get install libgtkglext
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtkglext
ameen@manghi:~/Desktop$
```

It seems that I don't have libgtkglext. I have all of the neccesary sources. Is it possible to download the file and install it? If so, how would I install it?

---

### Post by tkmn on 2006-06-25
I searched for it and found out the correct name is libgtkglext1.

```
sudo apt-get install libgtkglext1
```

```
apt-cache search *name*
```

For Quake 3 and Enemy Territory, I recommend the stable version.

[linux-radiant-1.4.0.run]("http://www.qeradiant.com/?data=files&files_id=75")

---

### Post by amunimanghi on 2006-06-25
Okay thanks, it worked. I'm going to try to make a level for Jedi Academy.

---

### Post by Rashid584 on 2006-08-10
I tried it with 1 on the end, it still didn't work :(

-Rashid

---

### Post by billyfoxtrot on 2006-10-02
Rashid,

Try searching for the package in Synaptic.  I found it there.

The problem I'm having is I get a segmentation fault every time I try to run the program.  I see the splash screen and then a box pops up, but every time I click OK, I get the segfault.  Anyone know how I could fix this?  By the way, I'm trying to use the latest 1.5.0 beta version.

---

### Post by Rashid584 on 2006-10-03
Yeah, I tried with adept (KDE) didnt find it :(

-Rashid

---

### Post by CalcProgrammer1 on 2006-10-15
I installed it with the alien thing.  It works for editing maps but I can't get it to build them.  I added the enginepath_linux thing to ja.game and then I tried changing [RadiantPath] and [EnginePath] in ja.game/default_build_menu.xml but it won't build... I also then tried to make and compile a map for Quake 3 (which I don't have) to see if it would compile.  Nope, it did not.  Does anyone know how to get q3map2 or the build menu to work right?

---

### Post by henriquemaia on 2006-11-13
I have installed the libgtkglext1 and I'm still getting the error:

```
./radiant.x86: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory
```
.
Any ideas how to solve this?

---

### Post by billyfoxtrot on 2006-11-14
> **henriquemaia said:**
> I have installed the libgtkglext1 and I'm still getting the error:

```
./radiant.x86: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory
```
.
Any ideas how to solve this?

Did you try installing the libgtkglext dev package as well?

---

### Post by dmn_clown on 2006-11-14
> **Dingo_aus said:**
> GTKRadiant is software that allows you to create maps for games such as Quake 1 - 4, Doom 3, ET etc etc

It is now GPL'd and available from [http://www.qeradiant.com/]("http://www.qeradiant.com/")

The latest beta binaries are usually available as .rpm packages from the front page there.

To install it for Ubuntu, this is what I found worked for me.
(I presume you have set up universe repositories etc already)

Download the gtkradiant*.rpm available and note where you put it. 

(Install "alien" on your ubuntu distro if you don't have it already. You can do this via adept or the synaptic package manager)

Make sure you close adept or synaptic after this step so alien an access the package database.

Open a console and change dir to the directory where you downloaded the .rpm to.

run "alien gtkradiant*.rpm"

This will produce a .deb file in the same directory downloaded the rpm to.

Install that .deb file (you can just click on it from a konqueror window if you want)

This will install GTKRadiant on your system. The executable is found at "/opt/gtkradiant/radiant.x86"

Before you can run it though you will need to fire up adept (or synaptic or whatever) again and install the "libgtkglext" library.

now run "/opt/gtkradiant/radiant.x86" and enjoy!


EDIT: BTW if you are using KDE like I am you will probably want to disable "Ctrl-Tab" desktop switching so Ctrl-Tab can be used with GTKRadiant instead. To do this, open a console and type "kcontrol" and then goto "Regional & Accessibility" > "Keyboard Shortcuts" and edit "Walk through desktop list" to "none" - that disables it.

It's actually better to ignore that binary as many of the bugs within it have been fixed, you should download and build the latest client from their subversion repository that also includes more features.  (Builds on AMD64 and x86)

---

### Post by lakersforce on 2007-04-03
It would be great if someone wrote a guide describing how to get the latest version from svn and how to get Gtkradiant 1.5 (and upwards) up and run.

---

### Post by fragmented_user on 2007-05-09
> **lakersforce said:**
> It would be great if someone wrote a guide describing how to get the latest version from svn and how to get Gtkradiant 1.5 (and upwards) up and run.

If someone would tell me how to build a deb file for this, I would gladly do it.

---

### Post by fragmented_user on 2007-05-09
UPDATE: I was having issues installing due to the install.py script not sanity checking and attempting to execute win32 specific instructions. I used the instructions here [http://tremulous.net/phpBB2/viewtopic.php?t=4204](http://tremulous.net/phpBB2/viewtopic.php?t=4204) and have been able to succecfully compile install and run gtkradiant.

---

### Post by rcatman on 2007-06-17
For some reason ID makes it extremely difficult to download the SVN GTKRadiant source code. Too many file directories, ugh! I spent an hour looking all around for the rpm file. I gave up and gathered the tools to compile radiant but stumbled upon the rpm file. 

[http://zerowing.idsoftware.com/files/radiant/nightly/1.5/]("http://zerowing.idsoftware.com/files/radiant/nightly/1.5/")

 obvious? No. Not at all.
Just follow dingo_aus' how-to. 

Easy steps to follow in my word.
1. Download the latest gtkradiant*.rpm file. (for me it was [http://zerowing.idsoftware.com/files/radiant/nightly/1.5/gtkradiant-1.5.0-2006-03-02.i386.rpm]("http://zerowing.idsoftware.com/files/radiant/nightly/1.5/gtkradiant-1.5.0-2006-03-02.i386.rpm")) and save the rpm file on your desktop.
2. Either a) open up synaptic and search for 'alien', click on package 'alien' and click the apply button to install the package. Alien is a program to convert packages for other linux distro's to your current one. In this situation we're converting a red hat package (rpm) to a debiain package (deb) which we can click and install :)
    Or     b) Open up a console and type 'sudo apt-get install alien'. There might be some packages to install along with alien so just enter 'y' even if the package can't be verified.
3. Open up a terminal. Change the current working directory to your desktop (where you saved the rpm file in step 1) by typing 'cd $HOME/Desktop' in the terminal.
4. Now, the rpm file will be gtkradiant-1.5.0 * something something. In the terminal type 'sudo alien gtkradiant-1.5.0-2006-03-02.i386.rpm'. Keep in mind that was the name of the file when I downloaded it, it may have changed. You can usually type in most of the name and hit the tab button, the shell should fill in the rest of the filename for you.

After a few minutes or so you should have a deb package on your desktop. Install it like any normal deb package by opening it up with your pointer. 

To open you'll have to cd into /opt/gtkradiant and open radiant by typing ./radiant.x86

---

### Post by fontenot_1031 on 2007-07-22
Would anyone happen to know how to setup Nexiuz on GTKRadiant.  It appears on the list of games, but I can't make any maps for it.

---

### Post by rjlee on 2007-11-14
I have installed gtkradiant and I have libgtkglext1-dev installed through apt-get.

The commands I used to install were:
```
	sudo apt-get install scons g++ zlib1g-devel libgtk2.0-dev libgtkglext1-dev libxml2-dev libmhash-dev
	mkdir ~/src && cd ~/src
	svn checkout https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/trunk/ ./GtkRadiant
	svn checkout https://zerowing.idsoftware.com/svn/radiant.gamepacks/Q3Pack/trunk/ ./GtkRadiant/games/Q3Pack
	cd GtkRadiant/
	scons SETUP=0
	python ./install.py

```

I have also tried installing the two least old rpm packages from [http://zerowing.idsoftware.com/files/radiant/nightly/1.5/](http://zerowing.idsoftware.com/files/radiant/nightly/1.5/) through alien, and they have the same effect.

I am using Ubuntu 7.10, upgraded from the factory-installed 7.04, on a Dell Inspiron 6400 (Intel graphics with Compiz).

I have attached a screenshot of what happens when I start up; basically I can't see the window as it is drawn in the background grey. If I try and drag out a box with the mouse, then the left and top panes show correctly, but any attempt to do anything else, including moving the window or switching desktops, breaks it again. The correct window contents flickers into and out of view when I drag any slider.

Does anyone know of a solution to this problem? If not, can anyone suggest an alternative program for editing OpenArena maps, or possibly have a non-broken .deb that I could try?

Many thanks for any help!

Yours,

Robert Lee

---

### Post by merlwiz79 on 2008-05-17
Made a .deb of GtkRadiant 1.5 here: [http://alientrap.org/forum/viewtopic.php?t=3093](http://alientrap.org/forum/viewtopic.php?t=3093)

---

### Post by MinkeyMan on 2008-06-01
Here's a deb file I've built from source. I edited the code to make it more 1024x768 friendly and to use xdg-open instead of plain old firefox. I've included all the game definitions I could find, I had to create one by hand (openarena).

[Download "gtkradiant_1.5.0_i386.deb"]("http://www.filecrunch.com/fileDownload.php?sub=aa08bf2141f0ca1f26529d94ef76ef08&fileId=152959")

This file has been tested on a virtual machine with nothing installed, so it grabs the required dependencies fine. Enjoy.

---

### Post by kale- on 2008-08-09
hello,
does anyone have this .deb above. for some reason, i cant open the download page

would be turbo great if someone can upload it somewhere again

---

### Post by detrate on 2008-08-09
> **fontenot_1031 said:**
> Would anyone happen to know how to setup Nexiuz on GTKRadiant.  It appears on the list of games, but I can't make any maps for it.

You're going to have to be more descriptive about that error, perhaps [this how to](http://www.nexuizninjaz.com/forum/showthread.php?tid=91) can help you.



**Here's a mirror of the deb file**: [http://www.nexuizninjaz.com/downloads/gtkradiant_1.5-svn20080512-1_i386.deb](http://www.nexuizninjaz.com/downloads/gtkradiant_1.5-svn20080512-1_i386.deb)

---

### Post by kale- on 2008-08-09
hello

found the same packet from nexuiz site earlier but for some reason it doesnt have quake 3 as an option for a game :( which is the second of 2 games im building maps

---

### Post by bffpheonix on 2011-12-19
I know. This is a very old post - but I also tried to install gtk radiant on ubunu and wanted to share this:

The svn repository has moved. See [http://icculus.org/news/news.php?id=4634](http://icculus.org/news/news.php?id=4634). 

check out the radiant:
 ```
 svn co svn://svn.icculus.org/gtkradiant/GtkRadiant/trunk GtkRadiant

```

then you probably want some gamepacks. You can view the available gamepacks here: [http://svn.icculus.org/gtkradiant-gamepacks/](http://svn.icculus.org/gtkradiant-gamepacks/)

move into ./GtkRadiant/install/installs:
```

cd GtkRadiant/install/installs

```get the gamepack you want
```

svn co svn://svn.icculus.org/gtkradiant-gamepacks/HalfLifePack/trunk ./HalfLifePack
svn co svn://svn.icculus.org/gtkradiant-gamepacks/Q3Pack/trunk ./Q3Pack
etc...

```to compile go back to folder gtkradiant
```

scons SETUP=0
python ./install.py

```still - I don't have the dependency list. However, I'm pretty sure this is a good way...

---

