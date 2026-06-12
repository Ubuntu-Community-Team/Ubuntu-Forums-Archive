---
title: "Quantum GIS (QGIS) installation and Ubuntu"
date: 2009-06-06
forum: Education &amp; Science
---

### Post by badaveil on 2009-06-06
I have installed QGIS on my Ubuntu 8.0.4 pc and it works perfectly well. Novice me has finally learned the ropes and listed how to do it at [http://forum.qgis.org/viewtopic.php?f=3&t=4820](http://forum.qgis.org/viewtopic.php?f=3&t=4820)

[IMG]http://lh6.ggpht.com/_yJ5Rhn3UxL4/SgcQoyjfvPI/AAAAAAAACG4/eWc-Ntj2xhw/s800/buffering%40ftools.png[/IMG]

---

### Post by thirdreplicator on 2009-09-17
This worked for me on Jaunty.  I haven't tested these instructions from scratch.  I reconstructed them from my history.  Hope it helps somebody. (Mileage may vary.)

*****

svn co [https://svn.osgeo.org/qgis/branches/Release-1_0_2](https://svn.osgeo.org/qgis/branches/Release-1_0_2) qgis_1.0.2

sudo apt-get install libqt4-core libqt4-dbg    libqt4-dev libqt4-gui libqt4-qt3support libqt4-sql lsb-qt4 qt4-designer   qt4-dev-tools qt4-doc qt4-qtconfig uim-qt gcc libapt-pkg-perl resolvconf

sudo apt-get install cmake
sudo apt-get install grass libgrass-dev libgdal1-1.4.0-grass
sudo apt-get install libda4
sudo apt-get install flex
sudo apt-get install bison
sudo apt-get install libgsl0ldbl libgsl0-dev
sudo apt-get install libgdal-dev
sudo apt-get install pyqt-tools
sudo apt-get install python-dbus
sudo apt-get install python-qt4
sudo apt-get install pyqt4-dev-tools
sudo ln -s /usr/bin/pyuic /usr/bin/pyuic4

mkdir -p build
cd build
ccmake ..
# press c
# press g
# press q to exit
make
sudo make install

***
# to run the program type, for example:

qgis &

---

### Post by badaveil on 2009-09-17
I too just upgraded to Jaunty. I feel your method is too long.

As for me, firstly I went over to file system/etc/apt/source list/authentication and imported the the key file qgis homepage/download. Secondly, I went over to file system/etc/apt/source list/third-party software and added the 2 ppa.launchpad.net script taken from qgis homepage/download. Thirdly I closed that screen and immediately files were download from the qgis repository.

That's all that was needed.

---

### Post by christianshearer on 2009-09-21
Hi, I just followed the instructions from the second post here, and seemed to follow, and my computer seemed to do stuff all the way down, but when I came to this last section, I am not sure if my computer did anything:


mkdir -p build
cd build
ccmake ..
# press c
# press g
# press q to exit
make
sudo make install

I think that my beginner terminal skills may be at fault.  Anyway, at this point I do have Qt 4 programs in my Applications, but I still do not see QGIS.  

Please let me know what I can do, in very simple terms.  Thanks
Christian

Here is my terminal output from that point on (you will see how clueless I am in the terminal, but hey, I'm trying)

christianshearer@christianshearer-laptop:~$ mkdir -p build
christianshearer@christianshearer-laptop:~$ cd build
christianshearer@christianshearer-laptop:~/build$ ccmake ..


christianshearer@christianshearer-laptop:~/build$ ccmake
ccmake version 2.6-patch 2
Usage

  ccmake <path-to-source>
  ccmake <path-to-existing-build>

Options
  -C <initial-cache>          = Pre-load a script to populate the cache.
  -D <var>:<type>=<value>     = Create a cmake cache entry.
  -U <globbing_expr>          = Remove matching entries from CMake cache.
  -G <generator-name>         = Specify a makefile generator.
  -Wno-dev                    = Suppress developer warnings.
  -Wdev                       = Enable developer warnings.

Generators
  Unix Makefiles              = Generates standard UNIX makefiles.
  CodeBlocks - Unix Makefiles = Generates CodeBlocks project files.
  Eclipse CDT4 - Unix Makefiles
                              = Generates Eclipse CDT 4.0 project files.
  KDevelop3                   = Generates KDevelop 3 project files.
  KDevelop3 - Unix Makefiles  = Generates KDevelop 3 project files.

christianshearer@christianshearer-laptop:~/build$ # press c
christianshearer@christianshearer-laptop:~/build$ # press g
christianshearer@christianshearer-laptop:~/build$ q
bash: q: command not found
christianshearer@christianshearer-laptop:~/build$ # press q to exit
christianshearer@christianshearer-laptop:~/build$ make
make: *** No targets specified and no makefile found.  Stop.
christianshearer@christianshearer-laptop:~/build$ sudo make install
make: *** No rule to make target `install'.  Stop.
christianshearer@christianshearer-laptop:~/build$ qgis
bash: qgis: command not found
christianshearer@christianshearer-laptop:~/build$

---

### Post by christianshearer on 2009-09-23
Hey!  I did it, only with the help of Ubuntu forums and the awesome people helping here. Thanks so much to badaveil, ajgreeny, and technophobia.

 I'll try to tell you what I did.

First Go to **System -> Administration -> Software Sources**

(enter your password)

"**Third Party Software**" Tab

Click "**+Add**"

When it prompts you for a APT Line, enter:

deb [http://ppa.launchpad.net/qgis/ubuntu/](http://ppa.launchpad.net/qgis/ubuntu/) jaunty main

click on "**Add Source**"
Then click "**Reload**" to update

At this point I got a "NO PUBKEY" error, but not to worry, because we have added the source.

Now, open your terminal type the following:

```

~$ gksudo gedit /etc/apt/sources.list
```

(A window should open, and you should see your newly added source, [http://ppa.launchpad.net/qgis/ubuntu/](http://ppa.launchpad.net/qgis/ubuntu/))

close that window with the x in the corner

then type into the terminal:
```

~$ sudo apt-get install qgis
```

(it should install)

[COLOR="Purple"]if it doesn't then try this:
```

~$ sudo apt-get update
```

that will do some stuff then try this again:
```
~$ sudo apt-get install qgis
```[/COLOR]


then:
```

~$ qgis
```

And walla! It should open. Or you can find it automatically added to programs:
[B]
Applications -> Education -> Quantum GIS[/B]


This whole community of open-sources is awesome. I feel like I just kicked microsoft in the balls, and it feels good.

---

### Post by christianshearer on 2009-09-29
I have an amendment to that previous post.

After having QGIS for a week, I realized I had the unstable version.

So, in that first step, when loading a APT line, load this instead (stable):

deb [http://ppa.launchpad.net/qgis/stable/ubuntu/](http://ppa.launchpad.net/qgis/stable/ubuntu/) jaunty main


otherwise follow the directions, and you should have it.

Peace
C

---

### Post by gemniii on 2009-11-07
[quote=christianshearer;8028044
Peace
C[/quote]

Sir -
You are truly commended.
I've been using Linux off and on since the 10 floppy 0.92 distro.  
Then the last time I installed QGIS on Ubuntu it was two clicks.
Now it's gotten "dropped" and the PPA does not work.
/edit
I first tried to install it on 9.10, and dropped back to 9.04 before I found your message.

---

### Post by badaveil on 2009-11-08
Well I'm now on Ubuntu 9.10 and have installed QGIS 1.3 MIMAS. They are both functioning well so much for it being unstable. I do keep for my own personal reference below how to install qgis in case you want to know:

[LIST]
[*]Import qgis public key from qgis download page to system file/ext/apt/source.list/authentication( Need to copy and paste public key to gedit text editor and upload to authentication by using /authentication/import key file) ;
[*]Copy &#8220;deb [http://ppa.launchpad.net/qgis/unstable/](http://ppa.launchpad.net/qgis/unstable/) ubuntu karmic main&#8221; to file system/ext/apt/source.list/third-party software (note "unstable" not stable version used here);
[*]Copy &#8220;deb-src [http://ppa.launchpad.net/qgis/unstable/](http://ppa.launchpad.net/qgis/unstable/) ubuntu karmic main&#8221; to file system/ext/apt/source.list/third-party software (note "unstable" not stable version used here);
[*]Select close to upload files
[*]Open Synapatic Package Manager, in search type "qgis", mark for installation qgislib, python & qgis packages
[/LIST]

So far so good.

---

### Post by jdelgado on 2009-11-10
How about the GRASS 6.4 plugin for QGIS? I haven't found it for Karmic...

Does anybody know if it was already released?

greetings

ze

---

### Post by badaveil on 2009-11-11
> **jdelgado said:**
> How about the GRASS 6.4 plugin for QGIS? I haven't found it for Karmic...

Does anybody know if it was already released?

greetings

ze

Sorry, no idea:-(

---

### Post by Herman on 2009-11-19
Thank you, badaveil, I am using Karmic and your advice in post #8 worked well for me.

---

### Post by badaveil on 2009-11-19
> **Herman said:**
> Thank you, badaveil, I am using Karmic and your advice in post #8 worked well for me.

You made my day:D when my experiences is not put to waste. I am very happy for you.

---

### Post by crpenaherrera on 2009-11-21
Hello everyone,

What about installing QGIS in ubuntu 9.04 64bits? 

CP

---

### Post by badaveil on 2009-11-21
> **crpenaherrera said:**
> Hello everyone,

What about installing QGIS in ubuntu 9.04 64bits? 

CP
Since QGIS is free, why don't you give it a try then tell us the result?

---

### Post by Herman on 2009-11-22
A couple of other programs I think make good companions with Quantum GIS in Ubuntu are gnumeric spreadsheet and inkscape.

I found out that gnumeric spreadsheet is handy for adding columns in .csv files. I'm using a GPS which logs positions in plain text files. I found I can  easily turn those into .csv files and open .csv files with gnumeric spreadsheet, add columns and edit them as I like. When I'm finished, I save as a .csv again. The .csv files made with gnumeric seem to be perfectly compatible with Quantun GIS.

I wanted to add my own custom icons to the ones that come standard in Quantum GIS, and I found it easiest to make them in GIMP. The images files Quantum can use are .svg files, but GIMP can't save as .svg, so I need inkscape to finish the job and convert the image files to .svg format.

Quantum GIS seems to be working okay in my 64bit Jaunty and Karmic installations. I have an i386 installation which I'm using for my GIS work mainly though.

---

### Post by researcher123 on 2009-11-29
I have Ubuntu 9.10 karmic. Can I install following these steps? Please advice

---

### Post by badaveil on 2009-11-30
> **researcher123 said:**
> I have Ubuntu 9.10 karmic. Can I install following these steps? Please advice

Follow steps in message #8. I'm using Ubuntu 9.10 too and it works;)

---

### Post by fabio sela on 2009-12-11
> **jdelgado said:**
> How about the GRASS 6.4 plugin for QGIS? I haven't found it for Karmic...

Does anybody know if it was already released?

greetings

ze
The qgis-grass-plugin comes with the qgis installation on ubuntu 9.10. It works perfectly, as far as I can see! In my case I needed to remove my old GRASS installation before installing qgis. With "sudo apt-get install qgis" GRASS 6.4 was installed automatically (I have no idea why, but it is very comfortable!). Hope this helps.

---

### Post by fabio sela on 2009-12-18
> **fabio sela said:**
> The qgis-grass-plugin comes with the qgis installation on ubuntu 9.10. It works perfectly, as far as I can see! In my case I needed to remove my old GRASS installation before installing qgis. With "sudo apt-get install qgis" GRASS 6.4 was installed automatically (I have no idea why, but it is very comfortable!). Hope this helps.

Sorry, some corrections here: for Karmic it is better just to use the current gis-repository on [https://launchpad.net/~ubuntugis]("https://launchpad.net/%7Eubuntugis") to use both GRASS and QGIS. With this repository put into your sources-list, you can install the latest versions of GRASS and QGIS with qgis-plugin working without any problems.

---

### Post by arma0012 on 2009-12-21
I'm a noob so please bear with me. I'm using 9.10 and trying to install qgis and have added the stable PPA but when I update the package I'm told that it can't download the repository indexes, specifically:

'Failed to fetch [http://ppa.launchpad.net/qgis/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/qgis/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.'

Can someone please tell me what i'm doing wrong?

Cheers,
Sam

---

### Post by badaveil on 2009-12-25
> **arma0012 said:**
> I'm a noob so please bear with me. I'm using 9.10 and trying to install qgis and have added the stable PPA but when I update the package I'm told that it can't download the repository indexes, specifically:

'Failed to fetch [http://ppa.launchpad.net/qgis/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/qgis/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.'

Can someone please tell me what i'm doing wrong?

Cheers,
Sam

Try to follow steps under message 8 except change “.../unstable/ ubuntu karmic main” to ".../stable ubuntu kore main" in the 2 required steps. I hope that works.

---

### Post by Evan Roy on 2010-02-01
> **christianshearer said:**
> Hey!  I did it, only with the help of Ubuntu forums and the awesome people helping here. Thanks so much to badaveil, ajgreeny, and technophobia.

 I'll try to tell you what I did.

First Go to **System -> Administration -> Software Sources**

(enter your password)

"**Third Party Software**" Tab

Click "**+Add**"

When it prompts you for a APT Line, enter:

deb [http://ppa.launchpad.net/qgis/ubuntu/](http://ppa.launchpad.net/qgis/ubuntu/) jaunty main

click on "**Add Source**"
Then click "**Reload**" to update

At this point I got a "NO PUBKEY" error, but not to worry, because we have added the source.

Now, open your terminal type the following:

```

~$ gksudo gedit /etc/apt/sources.list
```(A window should open, and you should see your newly added source, [http://ppa.launchpad.net/qgis/ubuntu/](http://ppa.launchpad.net/qgis/ubuntu/))

close that window with the x in the corner

then type into the terminal:
```

~$ sudo apt-get install qgis
```(it should install)

[COLOR=Purple]if it doesn't then try this:
```

~$ sudo apt-get update
```that will do some stuff then try this again:
```
~$ sudo apt-get install qgis
```[/COLOR]


then:
```

~$ qgis
```And walla! It should open. Or you can find it automatically added to programs:
[B]
Applications -> Education -> Quantum GIS[/B]


This whole community of open-sources is awesome. I feel like I just kicked microsoft in the balls, and it feels good.


Hello everyone!!Very new to this whole thing and very excited also.I tried to install QGIS 'exactly' as you said (as I hardly know these stuff till now).After the installation finishes I saw that QGIS comes under the Education tab but when clicked only the splash screen comes and crashes...!!no idea what happened!!but I need this thing very badly...kindly help!!

---

### Post by badaveil on 2010-02-02
Evans

Mmmm, I too just found out that QGIS amended the command lines after QGIS 1.4 came about, so I'm amending the relevant lines as below:

[LIST]
[*]Import qgis public key from qgis download page to system file/ext/apt/source.list/authentication( Need to copy and paste public key to gedit text editor and upload to authentication by using /authentication/import key file) ;
[*]Copy
deb [http://ppa.launchpad.net/ubuntuqgis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntuqgis/ubuntugis-unstable/ubuntu) karmic main (I can't seem to get message to type "...nstable" to write as "ubuntugis-unstable")
 to file system/ext/apt/source.list/third-party software (note "unstable" not stable version used here);
[*]Copy
deb-src [http://ppa.launchpad.net/ubuntuqgis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntuqgis/ubuntugis-unstable/ubuntu) karmic main (I can't seem to get message to type "...nstable" to write as "ubuntugis-unstable")
 to file system/ext/apt/source.list/third-party software (note "unstable" not stable version used here);
[*]Select reload to upload files
[*]Open Synapatic Package Manager, in search,type "qgis", mark for installation qgis then "apply"
[/LIST]

Thanks for your message. I wouldn't have updated this topic if not for you.

---

