---
title: "[How To] Install additional plug-ins for compiz in Gutsy"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by super61 on 2007-12-17
Welcome.

For those who are using Gutsy and would like to have 3D Windows, Atlantis2, Snow, Stars, Atlantis, Screensaver, Anaglyph, Wallpaper, Tile, Freewins, Fireflies and Photowheel working with Gutsy's default compiz-fusion, I am presenting this guide.

I would not recommend this to anyone not knowing exactly what they are doing.

This tutorial assumes that:
1) You have a fresh install of Gutsy.
3) You have the proper drivers installed for your graphics card.
2) You already have Gutsy's default compiz working (0.6.1).
4) You are running as user and not root.

NOTE: Compiz-Fusion is installed by default in Ubuntu Gutsy and will work as long as you have a video card with appropriate drivers with the proper configuration. Installing and configuring drivers is beyond the scope of this tutorial, but there are plenty of guides to configure your graphics card on Gutsy; see the Hardware page on the Compiz Fusion Wiki for more information.

Getting the build dependencies
Install the packages required for compiling plugins:
Code:

sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool

Getting the plugin source tarballs
Make a compiz subdirectory in your home directory:
Code:

mkdir -p  ~/compiz/

Use the following commands to download the plugins you want to install:
Code:

wget -O /tmp/3d.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3'
wget -O /tmp/atlantis2.tar.gz 'http://gitweb.compiz-fusion.org/?p=users/smspillaz/atlantis2-0.6;a=snapshot;h=d50d17bcdef5a025699e6b1bc0d604a98d1b74b2;sf=tgz'
wget -O /tmp/snow.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugins/snow;a=snapshot;h=01d0ff6ec71dae4699bc990e0114569c8ad4e083'
wget -O /tmp/stars.tar.gz 'http://oreaus.googlepages.com/stars.tar.gz'
wget -O /tmp/atlantis.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugins/atlantis;a=snapshot;h=a47d7151444faccd66ea5cb884673cdebe5d7dff'
wget -O /tmp/screensaver.tar.gz 'http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f'
wget -O /tmp/anaglyph.tar.gz 'http://oreaus.googlepages.com/anaglyph.tar.gz'
wget -O /tmp/wallpaper.tar.gz 'http://gitweb.compiz-fusion.org/?p=fusion/plugins/wallpaper;a=snapshot;h=c2d19686e46ae171b6a0c04da9de1adbd74ae8be'
wget -O /tmp/tile.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugins/tile;a=snapshot;h=550c91fa188efd39c9cea43f894b45716b5cc6d5'
wget -O /tmp/freewins.tar.gz 'http://oreaus.googlepages.com/freewins.tar.gz'
wget -O /tmp/fireflies.tar.gz 'http://oreaus.googlepages.com/fireflies.tar.gz'
wget -O /tmp/photowheel-0.6.tar.gz 'http://gitweb.opencompositing.org/?p=users/b0le/photowheel;a=snapshot;h=41d8090b55b629f72bef55d785beaf468f31662f'


Extracting the source code

Example: For 3D Windows, you would do this:
Code:

tar -xf '/tmp/3d.tar.gz' -C ~/compiz/

This creates a directory at ~/compiz/3d.

Compiling a plugin after extraction
Switch to the directory created from extracting the tarball.

Example: For Freewins, you would do this:
Code:

cd ~/compiz/freewins-0.3-0.6

Once you are in the directory, you can compile the plugin:

Code:

make
make install

After compiling
Restart compiz and ccsm.


Removing a plugin
If for any reason you want to uninstall a plugin, the following command should be used.
Code:

make uninstall


NOTES:

    * For Atlantis2: By default, this plug-in uses too many system resources because of the number of models loaded. You might want to consider lowering some of the numbers in 'ccsm->Effects->Cube Atlantis->Numbers' after installation.

    * For Atlantis: This plug-in will show up as Cube Atlantis in ccsm as does atlantis2. Only one or the other should be installed/used at a time.

    * For Snow: There is no default texture. You can set one in 'ccsm->Extras->Snow->Texture'.

    * For Wallpaper: If you're using Desktop Cube, you don't need this plugin as you can set wallpapers via the Appearance tab in Cube's settings. This plugin is mostly targeted at Desktop Wall users, who need it in order to have multiple wallpapers. There is also a special syntax for defining the images attributes:
      Code:

      file:/path/to/file/pic.png:Opacity

      where Opacity is a value between 0 and 100. This should contain the absolute file path (ie. relative to /, not to your home directory).

    * For Fireflies: You might have to check Fireflies Over Windows in the Firefly settings.


--

If there are any problems, please check the prerequisites first, then ensure you have followed all instructions and typed all commands correctly. Each should return without errors. If all is in order and there are still issues, then post any problems or suggested changes here. Many thanks to crdlb, Fyda and Deciare for making this a decent guide. Try #compiz-fusion on irc.freenode.net to get further support.

Enjoy,

Scott 

i did not make this guide it was from here [HTML]http://forum.compiz-fusion.org/showthread.php?t=5303[/HTML]
all credit goes too Scott im Jeff

---

### Post by K.Mandla on 2007-12-20
Moved to Desktop Effects and Customization.

---

### Post by chrisccoulson on 2007-12-20
Thanks for posting this. There is also a script to automate some of this [here]("http://ubuntuforums.org/showthread.php?t=620000")

---

### Post by xaxas on 2007-12-20
```
root@gutsy:~# wget -O /tmp/3d.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugi ns/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef 3d21dbbb3'
--20:11:26--  http://gitweb.opencompositing.org/?p=fusion/plugi%20ns/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef%203d21dbbb3
           => `/tmp/3d.tar.gz'
Resolving gitweb.opencompositing.org... 195.114.19.35
Connecting to gitweb.opencompositing.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
20:11:26 ERROR 403: Forbidden.


```

:(( any ideas ? I'm new to this :(( plz plz i want the 3d effect :D and maybe snow :D
I have gutsy and was logged in as root :(

---

### Post by PinkFloyd102489 on 2007-12-20
> **xaxas said:**
> ```
root@gutsy:~# wget -O /tmp/3d.tar.gz 'http://gitweb.opencompositing.org/?p=fusion/plugi ns/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef 3d21dbbb3'
--20:11:26--  http://gitweb.opencompositing.org/?p=fusion/plugi%20ns/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef%203d21dbbb3
           => `/tmp/3d.tar.gz'
Resolving gitweb.opencompositing.org... 195.114.19.35
Connecting to gitweb.opencompositing.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
20:11:26 ERROR 403: Forbidden.


```

:(( any ideas ? I'm new to this :(( plz plz i want the 3d effect :D and maybe snow :D
I have gutsy and was logged in as root :(


That means that you arent able to access the file on the remote server. Nothing to do with being root.

If you want the 3D plugin, use the one here. [http://ubuntuforums.org/showthread.php?t=620000](http://ubuntuforums.org/showthread.php?t=620000)

---

### Post by kokomonjo on 2007-12-21
matt@kokomonjo:~$ tar -xf '/tmp/wallpaper.tar.gz' -C ~/compiz/
matt@kokomonjo:~$ cd ~/compiz/wallpaper-0.3-0.6
bash: cd: /home/matt/compiz/wallpaper-0.3-0.6: No such file or directory
matt@kokomonjo:~$ make
make: *** No targets specified and no makefile found.  Stop.
matt@kokomonjo:~$ make install
make: *** No rule to make target `install'.  Stop.

Everything else went ok until this point. is there something I am doing wrong? I am new to coding and linux and ubuntu. I am using 7.10 64-bit version. I am trying to figure out how to have multiple wallpapers on my desktops on the cube. i tried this "* For Wallpaper: If you're using Desktop Cube, you don't need this plugin as you can set wallpapers via the Appearance tab in Cube's settings. This plugin is mostly targeted at Desktop Wall users, who need it in order to have multiple wallpapers." but i do not have this option in ccsm. so i am looking for the plugin and how to install it. and help would be appreciated.

---

### Post by jryprt on 2007-12-21
> **kokomonjo said:**
> matt@kokomonjo:~$ tar -xf '/tmp/wallpaper.tar.gz' -C ~/compiz/
matt@kokomonjo:~$ cd ~/compiz/wallpaper-0.3-0.6
bash: cd: /home/matt/compiz/wallpaper-0.3-0.6: No such file or directory
matt@kokomonjo:~$ make
make: *** No targets specified and no makefile found.  Stop.
matt@kokomonjo:~$ make install
make: *** No rule to make target `install'.  Stop.

Everything else went ok until this point. is there something I am doing wrong? I am new to coding and linux and ubuntu. I am using 7.10 64-bit version. I am trying to figure out how to have multiple wallpapers on my desktops on the cube. i tried this "* For Wallpaper: If you're using Desktop Cube, you don't need this plugin as you can set wallpapers via the Appearance tab in Cube's settings. This plugin is mostly targeted at Desktop Wall users, who need it in order to have multiple wallpapers." but i do not have this option in ccsm. so i am looking for the plugin and how to install it. and help would be appreciated.

Here is what I did to get it in compiz 
erry@jerry-desktop:~$ wget -O /tmp/wallpaper.tar.gz 'http://gitweb.compiz-fusion.org/?p=fusion/plugins/wallpaper;a=snapshot;h=c2d19686e46ae171b6a0c04da9de1adbd74ae8be'
--13:07:49--  [http://gitweb.compiz-fusion.org/?p=fusion/plugins/wallpaper;a=snapshot;h=c2d19686e46ae171b6a0c04da9de1adbd74ae8be](http://gitweb.compiz-fusion.org/?p=fusion/plugins/wallpaper;a=snapshot;h=c2d19686e46ae171b6a0c04da9de1adbd74ae8be)
           => `/tmp/wallpaper.tar.gz'
Resolving gitweb.compiz-fusion.org... 195.114.19.35
Connecting to gitweb.compiz-fusion.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]

    [ <=>                                 ] 8,718         55.86K/s             

13:07:50 (55.56 KB/s) - `/tmp/wallpaper.tar.gz' saved [8718]

jerry@jerry-desktop:~$ tar -xf '/tmp/wallpaper.tar.gz' -C ~/compiz/
jerry@jerry-desktop:~$ cd ~/compix/wallpaper
bash: cd: /home/jerry/compix/wallpaper: No such file or directory
jerry@jerry-desktop:~$ cd ~/compiz/wallpaper
jerry@jerry-desktop:~/compiz/wallpaper$ make
convert   : wallpaper.xml.in -> build/wallpaper.xml
bcop'ing  : build/wallpaper.xml -> build/wallpaper_options.h
bcop'ing  : build/wallpaper.xml -> build/wallpaper_options.c
schema    : build/wallpaper.xml -> build/compiz-wallpaper.schema
compiling : wallpaper.c -> build/wallpaper.lo
compiling : build/wallpaper_options.c -> build/wallpaper_options.lo
linking   : build/libwallpaper.la
jerry@jerry-desktop:~/compiz/wallpaper$ sudo make install
[sudo] password for jerry:
install   : /home/jerry/.compiz/plugins/libwallpaper.so
install   : /home/jerry/.compiz/metadata/wallpaper.xml
install   : build/compiz-wallpaper.schema
jerry@jerry-desktop:~/compiz/wallpaper$ 

Now I need to figure how to set it up any help out there.
Or should I start a new post.

---

### Post by BDNiner on 2007-12-21
This worked great, i really missed the 3d windows.

---

### Post by kokomonjo on 2007-12-22
Hi Jryprt i did what you said but when i got to the point where is says you enter in the command "make" nothing happens. 

"jerry@jerry-desktop:~/compiz/wallpaper$ make
convert : wallpaper.xml.in -> build/wallpaper.xml
bcop'ing : build/wallpaper.xml -> build/wallpaper_options.h
bcop'ing : build/wallpaper.xml -> build/wallpaper_options.c
schema : build/wallpaper.xml -> build/compiz-wallpaper.schema
compiling : wallpaper.c -> build/wallpaper.lo
compiling : build/wallpaper_options.c -> build/wallpaper_options.lo
linking : build/libwallpaper.la"

none of this happens so what am I doing wrong? everything else does exactly what you have posted but when i enter make "matt@kokomonjo:~/compiz/wallpaper$" this pops up again.  i dont get any of the convert or compiling. Thanks for the help.

---

### Post by kokomonjo on 2007-12-22
I just tried one other time and got this message after make....

matt@kokomonjo:~/compiz/wallpaper$ make
linking   : build/libwallpaper.lalibtool: link: `build/wallpaper.lo' is not a valid libtool object
make: *** [build/libwallpaper.la] Error 1

at first i got when i entered make this popped up again "matt@kokomonjo:~/compiz/wallpaper$"

but after starting completely over i got the error.

---

