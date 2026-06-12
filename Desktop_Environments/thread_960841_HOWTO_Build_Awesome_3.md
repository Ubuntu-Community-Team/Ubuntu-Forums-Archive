---
title: "HOWTO Build Awesome 3"
date: 2008-10-27
forum: Desktop Environments
---

### Post by Shinuza on 2008-10-27
This how-to purpose is to help you build Awesome 3 on Ubuntu Intrepid Ibex.

[SIZE=6][COLOR=Red]Table of contents:[/COLOR][/SIZE]

[INDENT][SIZE=4][COLOR=Black]1. What is Awesome 3[/COLOR][/SIZE]
[SIZE=4][COLOR=Black] 2. Why building?[/COLOR][/SIZE]
[SIZE=4][COLOR=Black] 3. Building[/COLOR][/SIZE]
[SIZE=4][COLOR=Black] 4. Troubleshooting[/COLOR][/SIZE]
[SIZE=4][COLOR=Black] 5. Infos and References[/COLOR][/SIZE]
[/INDENT] 

[[IMG]http://images.imagehotel.net/25dy6dwden.png[/IMG]]("http://www.imagehotel.net/?from=25dy6dwden.png")

[SIZE=6][COLOR=Red]1. What is Awesome 3[/COLOR][/SIZE]

**Awesome** is a dynamic [window manager]("http://en.wikipedia.org/wiki/Window_manager") for the [X Window System]("http://en.wikipedia.org/wiki/X_Window_System"). Its development began in September 2007 as a fork of [dwm]("http://en.wikipedia.org/wiki/Dwm"). It aims at being extremely small and fast and supports multiple layouts such as floating, [tiling]("http://en.wikipedia.org/wiki/Tiling_window_manager"), and maximized. Like many other [tiling window managers]("http://en.wikipedia.org/wiki/Tiling_window_manager"), it strives to make it possible for the user to productively manage windows without the use of the mouse.

[From Wikipedia]

Awesome 3 is very speedful, uses XCB and Lua for configuration, and provide pipes for which you can build widgets to enhance your experience.

[SIZE=6][COLOR=Red]2. Why building?[/COLOR][/SIZE]

At the time of writing Awesome version in Intrepid is 2.3.2-1 while the last release version is 3.x.

[SIZE=6][COLOR=Red]3. Building[/COLOR][/SIZE]

**Get utilities for building**

```
$ sudo apt-get install build-essential autoconf automake libtool gperf xmlto git git-core cmake

```[B]
Get dependencies for awesome[/B]

```

$ sudo apt-get install libx11-dev libxinerama-dev libxrandr-dev libpango1.0-dev libimlib2-dev libgtk2.0-dev libxcb-shm0-dev libxcb-render0-dev libxcb-randr0-dev libxcb-shape0-dev libcairo2-dev libxcb-xinerama0-dev liblua5.1-filesystem0 liblua5.1-logging libdirectfb-dev libxt-dev libx11-xcb-dev libev3 libev-dev libxcb-aux0


```**Get lua**

```

$ sudo apt-get install lua5.1 liblua5.1-0-dev

```**Get Xcb utils and compile (Version in Intrepid Ibex is too old)**

```

$ git clone git://anongit.freedesktop.org/git/xcb/util
$ cd util && ./autogen.sh && make && sudo make install

```**Get Awesome and compile**

```
$ wget http://awesome.naquadah.org/download/awesome-3.1.tar.gz && tar xzf awesome-3.1.tar.gz
$ cd awesome-3.1 && make && sudo make install
```[[Partially from Awesome Wiki]("http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-Ubuntu-git")]


**Finally, c****reate an entry in GDM**

Create a new .desktop file in /usr/share/xsessions, for example awesome.desktop
And copy paste : 

```

   [Desktop Entry]
   Encoding=UTF-8
   Name=Awesome!
   Comment=This session starts Awesome 3
   Exec=/usr/local/bin/awesome
   Type=Application

```Log out, choose your Awesome session, enjoy.
See 5 for configuration and extras.

[SIZE=6][COLOR=Red]4. Troubleshooting[/COLOR][/SIZE]

[B][COLOR=Red][SIZE=3]1. If cmake complains about _*cairo-xcb*_ :[/SIZE]
[/COLOR]
Get Cairo and compile [/B]

```
$ wget http://www.cairographics.org/releases/cairo-1.8.0.tar.gz && tar xzf cairo-1.8.0.tar.gz && cd cairo* && ./configure --enable-xcb && make && sudo make install
```You are not supposed to update Cairo with .deb at this point unless they are built with XCB support

Please tell me if you have any problem so I can update this how to.

[SIZE=6][COLOR=Red]5. [/COLOR][/SIZE][SIZE=6][COLOR=Red]Infos and References[/COLOR][/SIZE]


[LIST=1]
[*][Awesome webpage]("http://awesome.naquadah.org/")
[*][Wikipedia Article]("http://en.wikipedia.org/wiki/Awesome_%28window_manager%29")
[*][Awesome Wiki]("http://awesome.naquadah.org/wiki/index.php?title=Main_Page")
[*][Configure Awesome 3]("http://awesome.naquadah.org/wiki/index.php?title=Awesome_3_configuration")
[*][Contributed Widgets for Awesome ]("http://awesome.naquadah.org/wiki/index.php?title=User_Contributed_Widgets")
[/LIST]

---

### Post by cl0ckwork on 2008-10-27
everything seems to work until i get to compiling awesome

```
$ git clone git://git.naquadah.org/awesome.git && cd awesome.git && make && sudo make install
Initialized empty Git repository in /home/clockwork/awesome/.git/
remote: Counting objects: 17242, done.
remote: Compressing objects: 100% (5609/5609), done.
remote: Total 17242 (delta 13052), reused 15144 (delta 11613)
Receiving objects: 100% (17242/17242), 3.05 MiB | 89 KiB/s, done.
Resolving deltas: 100% (13052/13052), done.
bash: cd: awesome.git: No such file or directory

```

---

### Post by Shinuza on 2008-10-29
> **cl0ckwork said:**
> everything seems to work until i get to compiling awesome

```
$ git clone git://git.naquadah.org/awesome.git && cd awesome.git && make && sudo make install
Initialized empty Git repository in /home/clockwork/awesome/.git/
remote: Counting objects: 17242, done.
remote: Compressing objects: 100% (5609/5609), done.
remote: Total 17242 (delta 13052), reused 15144 (delta 11613)
Receiving objects: 100% (17242/17242), 3.05 MiB | 89 KiB/s, done.
Resolving deltas: 100% (13052/13052), done.
bash: cd: awesome.git: No such file or directory

```
That's odd, apprently git creates awesome/.git instead of awesome.git

From your home try ```
$ mv awesome/.git ~/awesome.git
``` and then 

```
$ cd awesome.git && make && sudo make install
```

---

### Post by Vinno on 2008-10-31
(04:49 PM)[vinno@vinno:~/awesome/.git]$ ls
branches  config  description  HEAD  hooks  index  info  logs  objects  refs
(04:50 PM)[vinno@vinno:~/awesome/.git]$ make
make: *** No targets specified and no makefile found.  Stop.
(04:50 PM)[vinno@vinno:~/awesome/.git]$

Lost now.

---

### Post by Gorbon Treeman on 2008-10-31
can anyone provide a .deb for awesome3 ?

thanx...

---

### Post by jo_hann on 2008-11-01
Shinuza, i experienced a problem with your provided dependency package list: ```
libgtk2.0-devlibxcb-shm0-dev
``` could not be found. But the following did the job for me: ```
libxcb-shm0-dev
```

Also i would suggest to also install the following: ```
doxygen, luadoc, asciidoc
```. That should be needed for the useful man-pages...
Also ```
libdbus-1-dev
``` could be installed if needed....

EDIT:
Also you missed to include ```
libxcb-aux0-dev
```
So here is the corrected, full list to copy-and-paste: ```
apt-get install build-essential autoconf automake libtool gperf xmlto git git-core cmake libx11-dev libxinerama-dev libxrandr-dev libpango1.0-dev libimlib2-dev libxcb-aux0-dev libxcb-render0-dev libxcb-randr0-dev libxcb-shape0-dev libcairo2-dev libxcb-xinerama0-dev liblua5.1-filesystem0 liblua5.1-logging libdirectfb-dev libxt-dev libx11-xcb-dev libev3 libev-dev lua5.1 liblua5.1-0-dev doxygen luadoc asciidoc libdbus-1-dev
```

Greetings
jo_hann

---

### Post by jpt2433 on 2008-11-02
> **Shinuza said:**
> That's odd, apprently git creates awesome/.git instead of awesome.git

From your home try ```
$ mv awesome/.git ~/awesome.git
``` and then 

```
$ cd awesome.git && make && sudo make install
```


you shouldn't actually do the mv, simply 
```
 # cd awesome && make && sudo make install
```

---

### Post by super.rad on 2008-11-05
Had same problem as cl0ckwork jo_hann but installed libxcb-shm0-dev and had to use the command jtp2433 posted and all worked perfectly.
Thanks for the howto, been wanting to check out awesome 3 for a while now

EDIT: Tried it and now removing it, don't get on with tiling window managers at all. If i want a window manager I think I'll stick to openbox :p

---

### Post by damog on 2008-11-06
> **cl0ckwork said:**
> everything seems to work until i get to compiling awesome

```
$ git clone git://git.naquadah.org/awesome.git && cd awesome.git && make && sudo make install

```

You just do:

```

git clone git://git.naquadah.org/awesome.git && cd awesome && make && sudo make install

```

git takes the last directory on the clone url and creates it without the .git part

:guitar:

---

### Post by Shinuza on 2008-11-23
> **jo_hann said:**
> Shinuza, i experienced a problem with your provided dependency package list: ```
libgtk2.0-devlibxcb-shm0-dev
``` could not be found. But the following did the job for me: ```
libxcb-shm0-dev
```

Greetings
jo_hannTypo, updated.

> **jpt2433 said:**
> you shouldn't actually do the mv, simply 
```
 # cd awesome && make && sudo make install
```
Please see below :)
> **damog said:**
> You just do:

```

git clone git://git.naquadah.org/awesome.git && cd awesome && make && sudo make install

```

git takes the last directory on the clone url and creates it without the .git part

:guitar:Thanks for the reply, my version of git left .git at the end of the directory name, updated.

---

### Post by ~LoKe on 2008-12-04
Installed extra packages.  Now when I log into Awesome it leaves me with a blank screen and black cursor.  Can't do anything.

---

### Post by Dangling on 2008-12-05
> **~LoKe said:**
> Installed extra packages.  Now when I log into Awesome it leaves me with a blank screen and black cursor.  Can't do anything.

Same here. Then I built awesome from the stable 3.0 tarball with same results. But I didn't (couldn't) uninstall the git version before installing the stable version. Maybe that makes a difference.

---

### Post by ~LoKe on 2008-12-06
Any ideas?

---

### Post by Shinuza on 2008-12-18
I just tried compiling from the git repository and I had the same problem as yours.
Compiling form the stable 3.1 version worked well.

---

### Post by antage on 2009-01-05
Take a look at .deb of awesome 3.1 stable in my ppa:
```
deb http://ppa.launchpad.net/antage/ubuntu intrepid main
deb-src http://ppa.launchpad.net/antage/ubuntu intrepid main
```
It's NMU package, I took source package from Debian's experimental branch.

---

### Post by josedb on 2009-01-06
I got this error

```
jose@jose-laptop:~/util/awesome-3.1$ make
Running cmake…
-- cat -> /bin/cat
-- ln -> /bin/ln
-- grep -> /bin/grep
-- git -> /usr/bin/git
-- hostname -> /bin/hostname
-- gperf -> /usr/bin/gperf
-- asciidoc -> /usr/bin/asciidoc
-- xmlto -> /usr/bin/xmlto
-- gzip -> /bin/gzip
-- lua -> /usr/bin/lua
-- luadoc -> /usr/bin/luadoc
-- Looking for doxygen...
-- Looking for doxygen... - found /usr/bin/doxygen
-- Looking for dot tool...
-- Looking for dot tool... - NOT found
-- checking for module 'dbus-1'
--   found dbus-1, version 1.2.4
-- Configuring lib/naughty.lua
-- Configuring lib/revelation.lua
-- Configuring lib/awful/widget.lua
-- Configuring lib/awful/titlebar.lua
-- Configuring lib/awful/client.lua

-- Configuring lib/awful/hooks.lua
-- Configuring lib/awful/prompt.lua
-- Configuring lib/awful/menu.lua
-- Configuring lib/awful/completion.lua
-- Configuring lib/awful/placement.lua
-- Configuring lib/awful/tag.lua
-- Configuring lib/awful/screen.lua
-- Configuring lib/awful/init.lua
-- Configuring lib/awful/util.lua
-- Configuring lib/awful/layout.lua
-- Configuring lib/beautiful.lua
-- Configuring lib/tabulous.lua
-- Configuring lib/invaders.lua
-- Configuring config.h
-- Configuring awesomerc.lua
-- Configuring themes/default/theme
-- Configuring themes/sky/theme
-- Configuring awesome-version-internal.h
-- Configuring awesome.doxygen
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jose/util/awesome-3.1/.build-jose-laptop-i486-linux-gnu-4.3.2
Running make Makefile…
Building…
[  8%] Built target generated_sources
Scanning dependencies of target awesome
[  9%] Building C object CMakeFiles/awesome.dir/awesome.c.o
[ 11%] Building C object CMakeFiles/awesome.dir/client.c.o
/home/jose/util/awesome-3.1/client.c: En la función ‘luaA_client_index’:
/home/jose/util/awesome-3.1/client.c:1458: error: ‘xcb_get_wm_class_reply_t’ no tiene un miembro llamado ‘class’
/home/jose/util/awesome-3.1/client.c:1466: error: ‘xcb_get_wm_class_reply_t’ no tiene un miembro llamado ‘name’
make[3]: *** [CMakeFiles/awesome.dir/client.c.o] Error 1
make[2]: *** [CMakeFiles/awesome.dir/all] Error 2
make[1]: *** [all] Error 2
make: *** [cmake-build] Error 2

```

---

### Post by dreadatour on 2009-01-14
> **josedb said:**
> I got this error

```
jose@jose-laptop:~/util/awesome-3.1$ make
Running cmake…
-- cat -> /bin/cat
-- ln -> /bin/ln
-- grep -> /bin/grep
-- git -> /usr/bin/git
-- hostname -> /bin/hostname
-- gperf -> /usr/bin/gperf
-- asciidoc -> /usr/bin/asciidoc
-- xmlto -> /usr/bin/xmlto
-- gzip -> /bin/gzip
-- lua -> /usr/bin/lua
-- luadoc -> /usr/bin/luadoc
-- Looking for doxygen...
-- Looking for doxygen... - found /usr/bin/doxygen
-- Looking for dot tool...
-- Looking for dot tool... - NOT found
-- checking for module 'dbus-1'
--   found dbus-1, version 1.2.4
-- Configuring lib/naughty.lua
-- Configuring lib/revelation.lua
-- Configuring lib/awful/widget.lua
-- Configuring lib/awful/titlebar.lua
-- Configuring lib/awful/client.lua

-- Configuring lib/awful/hooks.lua
-- Configuring lib/awful/prompt.lua
-- Configuring lib/awful/menu.lua
-- Configuring lib/awful/completion.lua
-- Configuring lib/awful/placement.lua
-- Configuring lib/awful/tag.lua
-- Configuring lib/awful/screen.lua
-- Configuring lib/awful/init.lua
-- Configuring lib/awful/util.lua
-- Configuring lib/awful/layout.lua
-- Configuring lib/beautiful.lua
-- Configuring lib/tabulous.lua
-- Configuring lib/invaders.lua
-- Configuring config.h
-- Configuring awesomerc.lua
-- Configuring themes/default/theme
-- Configuring themes/sky/theme
-- Configuring awesome-version-internal.h
-- Configuring awesome.doxygen
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jose/util/awesome-3.1/.build-jose-laptop-i486-linux-gnu-4.3.2
Running make Makefile…
Building…
[  8%] Built target generated_sources
Scanning dependencies of target awesome
[  9%] Building C object CMakeFiles/awesome.dir/awesome.c.o
[ 11%] Building C object CMakeFiles/awesome.dir/client.c.o
/home/jose/util/awesome-3.1/client.c: En la función ‘luaA_client_index’:
/home/jose/util/awesome-3.1/client.c:1458: error: ‘xcb_get_wm_class_reply_t’ no tiene un miembro llamado ‘class’
/home/jose/util/awesome-3.1/client.c:1466: error: ‘xcb_get_wm_class_reply_t’ no tiene un miembro llamado ‘name’
make[3]: *** [CMakeFiles/awesome.dir/client.c.o] Error 1
make[2]: *** [CMakeFiles/awesome.dir/all] Error 2
make[1]: *** [all] Error 2
make: *** [cmake-build] Error 2

```

Try to change file "awesome-3.1/client.c" (/home/jose/util/awesome-3.1/client.c for you) this way:

on line 1458 change "hint.class" to "hint.class_name"
on line 1566 change "hint.name" to "hint.instance_name"

This helps for me =))

Cheers.

---

### Post by deuce868 on 2009-01-17
There's a PPA in launchpad that works great. I just started using Awesome this week. 

[https://launchpad.net/~ericdrex/+archive](https://launchpad.net/~ericdrex/+archive)

---

### Post by kutya61 on 2009-02-06
This howto works with Awesome 3.1.2 also, and i had to make the same changes in client.c:
> on line 1458 change "hint.class" to "hint.class_name"
on line 1466 change "hint.name" to "hint.instance_name"

---

### Post by kernel_script on 2009-03-02
Hi folks, more awesome 3x stable PPAs for Ubuntu 8.10:


> [https://launchpad.net/~aguignard/+archive/ppa](https://launchpad.net/~aguignard/+archive/ppa)
I installed my awesome 3.1.2-1 stable through this PPA, installs ok, session login ok, overall awesome works as a charm, no problems spotted till now, but i just logged and tested a few things for a few minutes, no robust tests made. I didn't tried the PPAss below, since this one worked great.

[https://launchpad.net/~saispo/+archive/ppa](https://launchpad.net/~saispo/+archive/ppa)

[https://launchpad.net/~aguignard/+archive/ppa](https://launchpad.net/~aguignard/+archive/ppa)


And great tread Shinuza, thanks for share the HOWTO : ]

---

### Post by weavex on 2009-04-29
HOWTO Build Awesome 3.2.1 in Ubuntu 9.04 Jaunty Jackalope, please.

I tried but it didn't work for me.

---

### Post by kernel_script on 2009-04-29
> **weavex said:**
> HOWTO Build Awesome 3.2.1 in Ubuntu 9.04 Jaunty Jackalope, please.

I tried but it didn't work for me.

Only build it serves you?

If you don't mind, you can use a PPA, see my previous post before yours for more info and links.

---

### Post by weavex on 2009-04-30
> **kernel_script said:**
> Only build it serves you?

If you don't mind, you can use a PPA, see my previous post before yours for more info and links.

I've tried the PPA, but i can't find Awesome in Synaptic. Only the packages named "ppa1~jaunty1".

Do you use Awesome 3.2.1 in Ubunu 9.04??

---

### Post by kernel_script on 2009-05-01
> **weavex said:**
> I've tried the PPA, but i can't find Awesome in Synaptic. Only the packages named "ppa1~jaunty1".

Do you use Awesome 3.2.1 in Ubunu 9.04??

No.

Try this PPA:
[https://launchpad.net/~aguignard/+archive/ppa](https://launchpad.net/~aguignard/+archive/ppa)

But choose "**The Intrepid Ibex**" instead of "**The Jaunty Jackalope**" right after 
[I]"apt sources.list entries
Display sources.list entries for:"[/I]

I never had too much problems using older Ubuntu versions PPAs on the current one, but sometimes it lack dependencies, try your luck.

---

### Post by weavex on 2009-05-04
> **kernel_script said:**
> No.

Try this PPA:
[https://launchpad.net/~aguignard/+archive/ppa]("https://launchpad.net/%7Eaguignard/+archive/ppa")

But choose "**The Intrepid Ibex**" instead of "**The Jaunty Jackalope**" right after 
[I]"apt sources.list entries
Display sources.list entries for:"[/I]

I never had too much problems using older Ubuntu versions PPAs on the current one, but sometimes it lack dependencies, try your luck.

Thanks, it worked perfectly! :)

---

### Post by kernel_script on 2009-05-04
> **weavex said:**
> Thanks, it worked perfectly! :)

Glad to hear! You're welcome : ]

---

### Post by kernel_script on 2009-06-13
Hello again,

I just found a PPA for Jaunty with **awesome 3.3** plus a **awesome-extra** package with *wicked* and *shifty*! :D

**Here:**
[https://launchpad.net/~akos-ladanyi/+archive/ppa](https://launchpad.net/~akos-ladanyi/+archive/ppa)

---

### Post by Nythain on 2009-07-07
> **kernel_script said:**
> Hello again,

I just found a PPA for Jaunty with **awesome 3.3** plus a **awesome-extra** package with *wicked* and *shifty*! :D

**Here:**
[https://launchpad.net/~akos-ladanyi/+archive/ppa]("https://launchpad.net/%7Eakos-ladanyi/+archive/ppa")
thanks for that... was using the other ppa, just switched for awesome-extra :)

---

### Post by kernel_script on 2009-07-07
> **Nythain said:**
> thanks for that... was using the other ppa, just switched for awesome-extra :)

You're welcome : ]

---

### Post by orengolan on 2009-07-14
X crashes on me when I open a terminal (Win+Enter).

The error is - can't find the file ~/.cache/awesome/lastwallpaper.png
(btw, I have this file, without the extension)

any ideas?


btw, i am upgrading from V 2.3.4.

---

