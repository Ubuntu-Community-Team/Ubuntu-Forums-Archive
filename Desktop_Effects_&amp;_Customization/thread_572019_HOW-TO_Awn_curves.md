---
title: "HOW-TO: Awn curves"
date: 2007-10-10
forum: Desktop Effects &amp; Customization
---

### Post by nikoPSK on 2007-10-10
I know a bunch of you have been asking about how to get AWN or avant-window-navigator to look like this:
 
**Black Theme:**
[IMG]http://www.abload.de/img/awnwhe.png[/IMG]
 
**Milk Theme:**
[IMG]http://img03.picoodle.com/img/img03/9/10/14/f_withreflectm_5c40045.png[/IMG]
 
 
[CENTER][SIZE=7]**INFO**[/SIZE][/CENTER]
 
**Now to clarify this**, this will just be a dock style. If you don't like it you can easily revert to the "Flat Bar" or "3D Look". This is in early development and it 's quite stable, This is AWN so it will require a window composter such as Beryl or Compiz.
 
This will not change your icons to OSX style like the first image. The screen-shot provided above has had those changes made to it. i don't care much for those icons, but meek has given me the link to the set he used: [here]("http://gnome-look.org/content/show.php/OSX?content=31618"). To change the icon of a launcher right click then change icon
 
 
I won't enclose an image of my dock because I don't know how to get a high-res screenshot like the other ones.:(
 
 
[CENTER]**[SIZE=7]Installation[/SIZE]**[/CENTER]
 
**Now for the fun part!**
 
 
**If you have avant already installed, remove it:**
```
sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
```**Install bazaar, gnome-common and M4. **
**Applications/ Accessories/ Terminal**
 
```
sudo apt-get install bzr m4 gnome-common
```**Then, Install awn curves:**
*(I know it seems tempting but copy the first two lines one at a time.)*
```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev 
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
cd awn-curves
./autogen.sh && make
sudo make install
```**stay in the awn-curves folder throughout all the instructions I give!**
make sure you have your AWN repositories, input the corresponding code into the terminal:
 
**32-BIT**
```
wget http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr-dev_0.2.0-bzr158-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr_0.2.0-bzr158-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/python-libawn-bzr_0.2.0-bzr158-1_i386.deb 
sudo gdebi *.deb
```[B]64-BIT
[/B]```
wget http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/avant-window-navigator-bzr_0.2.0-bzr166-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/awn-core-applets-bzr_0.2.0-bzr300-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/libawn-bzr-dev_0.2.0-bzr166-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/libawn-bzr_0.2.0-bzr166-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/python-libawn-bzr_0.2.0-bzr166-1_amd64.deb 
sudo gdebi *.deb
```Done, thanks Reacocard. :-)

[CENTER]**[SIZE=7]Q & A:[/SIZE]**[/CENTER]

 
**Q: How do I add awn-to my start-up???**
 
A: System > prefernces > sessions
 
then add this command:
```
avant-window-navigator
```**Q: How do I update awn-curves?**
 
A: Do this:
```
cd ~/awn-curves
bzr update
./autogen.sh && make && sudo make install
```**Q: My theme isn't appearing!**
 
A: Make sure to actually select it, click apply then refresh awn. If it still doesn't go, close awn, apply the theme in awn manager them open awn.
 
**Q: Awn isn't launching!!!**
 
A: Type both these commands one after the other into terminal and give me the output.
 
```
avant-window-navigator
```and
 

```
awn-manager
```[B]Q: Awn Disappeared!

[/B]A: To re-launch awn just press ALT+F2 and type "avant-window-navigator" to launch awn once more. 

[B]Q: Can I Hide my awn-curves folder located in my home folder when done?

[/B]A: Yes! You can do so by adding a period in front of the name so it looks like this: .awn-curves . To see it when needed, press Control+H or go View, Show Hidden Files. 


[CENTER][SIZE=7]**REMOVAL**[/SIZE][/CENTER]

 
**To remove awn-curves:**
 
Delete the awn-curves directory from your home folder then:
```
sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
```**Site: **[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=853&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=853&page=1&isLive=true)
 
(I had to look for this for ages then i found something on google telling me how to do this then I found the actual site a week later.):KS
Hope this can help!

---

### Post by nikoPSK on 2007-10-13
Here are screen shots with:
 
1. Human theme with the curves bar (Download below)
2. Milk theme (Download below)
3. Black (Download below, My personal favorite and the one in the screen-shot.) :)
4. Purple theme by belyel (Download below)
5. Glass theme by shafin
 
Here are the themes:
 
[Human Theme]("http://www.mediafire.com/?2xxcg0lnu0p")
[Milk Theme]("http://kerlz.de/downloads/milk.tgz")
[Black Theme]("http://kerlz.de/downloads/black.tgz")[URL="http://www.mediafire.com/?cz1capmgcdn"]
Purple Theme[/URL] [URL="http://mahdee.jameel.googlepages.com/Glass.tgz"]
Glass Theme 
[/URL]  
 
 
To install these themes just download 'em. No extraction required Then go to themes/ add and locate the theme which you want to install.
Submit your themes and I will put 'em here to and give links to download 'em!
 
I love docks and I think these are a great themes. Please leave replies here and on the official site! :)
 
EDIT: Nevermind, I got it back... :popcorn:

---

### Post by MNICY on 2007-10-14
ok, i have a problem.
i get this when i type ./autogen.sh && make

```
/usr/bin/gnome-autogen.sh

checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.61

checking for automake >= 1.9...

  testing automake-1.10... 
not found.
  testing automake-1.9... 
found 1.9.6

checking for libtool >= 1.5...

  testing libtoolize... 
found 1.5.22

checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.12.11

checking for intltool >= 0.30...

  testing intltoolize... 
found 0.35.5

checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.21

Checking for required M4 macros...


Checking for forbidden M4 macros...

**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.


Processing ./configure.in


Running libtoolize...


Running glib-gettextize... Ignore non-fatal messages.

Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.


Running intltoolize...


Running aclocal-1.9...

/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE

Running autoconf...


Running autoheader...


Running automake-1.9...


Processing ./awn-curves/configure.in


Running libtoolize...

You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `..'.

Running glib-gettextize... Ignore non-fatal messages.

Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.


Running intltoolize...

intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite
```

---

### Post by martijntje on 2007-10-14
How stable is this? I have AWN running now, which sometimes crashes, but always comes back when i run 'avant-window-navigator' again.  I like eyecandy, but i want to maintain a stable-enough system.

---

### Post by nikoPSK on 2007-10-14
This is quite stable and should run fine. As I said it's just a dock style so you can revert to 3d.:)

Mnicy,
> ok, i have a problem.
i get this when i type ./autogen.sh && make

Have you installed awn/ awn dependencies? Try reacocard's guide here: [http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")

---

### Post by dmber on 2007-10-14
worked perfectly!

thank you very much.

---

### Post by nikoPSK on 2007-10-14
Your welcome! I hope this helped. Everyone has been asking and I think icons on a curve is a great idea. Also thanks to reacocard for linking to my how-to:KS

---

### Post by dmber on 2007-10-14
this installed perfectly.  thank you very much.

two questions:

1. my icons "peek" when hidden using auto-hide.  screenshot:

[IMG]http://i240.photobucket.com/albums/ff189/maebemae/Screenshot.png[/IMG]

but they fully hide after about ten seconds or so.  i do nothing to make them fully hide, they just do it.

2. what is the "symmetry" slider for?  what exactly is it making symmetrical?

---

### Post by nikoPSK on 2007-10-14
The developer is working on the icon hiding problem (bar needs to move lower). symmetry gives the option to switch between asymmetric and symmetric look. like:
asymmetric |---o------| symmetric:) It should be working.

btw, nice desktop:p

---

### Post by MNICY on 2007-10-14
> **nikoPSK said:**
> Have you installed awn/ awn dependencies? Try reacocard's guide here: [http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")
i assume you mean this:
```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
```
i did this, but i still get the same error when i try to install curves.
Im going to uninstall and reinstall and see if that works.

---

### Post by dmber on 2007-10-14
cool.  thanks for the info.

i just got the Green Tango icon pack yesterday and thought i'd go all-green.

---

### Post by nikoPSK on 2007-10-14
I don't know. Sure give a re-installation a try:KS

---

### Post by datelus on 2007-10-14
datelus@skaistulis:~$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)

this is what i get :(
im a gusty user

---

### Post by MNICY on 2007-10-14
Did not work :(

---

### Post by nikoPSK on 2007-10-14
> **datelus said:**
> datelus@skaistulis:~$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)

this is what i get :(
im a gusty user

I am too. It should work. Have you got a composter running? (compiz, I know it's included but have you enabled desktop effects?):)

---

### Post by nikoPSK on 2007-10-14
> **MNICY said:**
> Did not work :(

ummmm... You're using feisty? It should...:( Try clearing all traces of awn

```
sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
``` 

Then do the code I have given at forst page.:)

---

### Post by MNICY on 2007-10-14
Well, this is kind of annoying.
I have no idea why it does not work...
i can install awn from source fine, but i just get errors with awn-curves :(

---

### Post by nikoPSK on 2007-10-14
mabye it's just not meant for you... XD

Anyways I'm using gutsy and it's fine, Mabye you can wait 4 days until gutsy final?:KS

---

### Post by MNICY on 2007-10-14
awww... but its so long :p
yah, i guess that would be best.

---

### Post by datelus on 2007-10-14
rr im using extra effects. defoult awn works, but thres a problem too: when i close a window it still aperas in the dock only with a name "no name" and i cant do a damn thing :/

---

### Post by nikoPSK on 2007-10-14
> **datelus said:**
> rr im using extra effects. defoult awn works, but thres a problem too: when i close a window it still aperas in the dock only with a name "no name" and i cant do a damn thing :/

okay. I see go to synaptic then (system/ administration then synaptic package manager) search:

compizconfig-settings-manager

Install it. Now go to appearance visual effects click custom. Awn-curves should now work:)

---

### Post by datelus on 2007-10-14
just removed everything, reinstalled and installed settings-manager.
now it displays 
```
Screen is composited.
APPLET : /usr/lib/awn/applets/trash.desktop
Segmentation fault (core dumped)

``` and still no pretty-dock 
guess im doomed :)

---

### Post by nikoPSK on 2007-10-14
> **datelus said:**
> just removed everything, reinstalled and installed settings-manager.
now it displays 
```
Screen is composited.
APPLET : /usr/lib/awn/applets/trash.desktop
Segmentation fault (core dumped)

``` and still no pretty-dock 
guess im doomed :)

gutsy = 4 days = pretty dock?:lolflag:

---

### Post by nikoPSK on 2007-10-14
okay. Lets see, Youve installed the bar look? Try going to bar appearance and cuvres look. Send a screen-shot of problems too please.:)

---

### Post by datelus on 2007-10-14
i doubt that anything will change in this place, when the full version comes out. any ideas why icons still stay in their place when i close the window? :D (in not curves version) ?



Youve installed the bar look? Try going to bar appearance and cuvres look
was this for me? :D

---

### Post by nikoPSK on 2007-10-14
You mean the icon lingers after you have closed the window? They should close. Have you mabye applied some new thing and havn't clicked refresh?:KS

---

### Post by datelus on 2007-10-14
hmm you know what? it works now.. all i did - i removed these 
avant-window-navigator-bzr 
awn-core-applets-bzr 
libawn-bzr
libawn-bzr-dev 
python-libawn-bzr
 
now i have to remove that little white line :)

[http://foto.inbox.lv/sys6/08-12-2006/Screenshot-1.png](http://foto.inbox.lv/sys6/08-12-2006/Screenshot-1.png)

---

### Post by nikoPSK on 2007-10-14
great! 

bar= seperator can be removed.:)

---

### Post by datelus on 2007-10-14
thanks for the help :]

---

### Post by nikoPSK on 2007-10-14
welcome! 

PS I am still a newb at ubuntu. Only a month in, but that doesn't mean I know nothing!:lolflag:

---

### Post by nikoPSK on 2007-10-14
> **datelus said:**
> hmm you know what? it works now.. all i did - i removed these 
avant-window-navigator-bzr 
awn-core-applets-bzr 
libawn-bzr
libawn-bzr-dev 
python-libawn-bzr
 
now i have to remove that little white line :)

[http://foto.inbox.lv/sys6/08-12-2006/Screenshot-1.png](http://foto.inbox.lv/sys6/08-12-2006/Screenshot-1.png)

My bad, Sorry that should just be an applet loading. If it stays white just right click refresh or remove the applet. :)

For me when I start up awn they appear (white line) then get replaced by the particular applet:)

---

### Post by nikoPSK on 2007-10-14
> **dmber said:**
> cool.  thanks for the info.

i just got the Green Tango icon pack yesterday and thought i'd go all-green.

Please submit your green theme in curves look:)

---

### Post by nikoPSK on 2007-10-15
> **MNICY said:**
> i assume you mean this:
```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
```
i did this, but i still get the same error when i try to install curves.
Im going to uninstall and reinstall and see if that works.

Try doing this:

Goto synaptic then search for these:

avant-window-navigator-bzr
awn-core-applets-bzr
libawn-bzr
libawn-bzr-dev
python-libawn-bzr

remove 'em and now try.:guitar:

---

### Post by mk04 on 2007-10-15
When I get to the "./autogen.sh && make" part it says:

bash: ./autogen.sh: No such file or directory


I'm running Edgy Eft....

---

### Post by nikoPSK on 2007-10-15
> **mk04 said:**
> When I get to the "./autogen.sh && make" part it says:

bash: ./autogen.sh: No such file or directory


I'm running Edgy Eft....
I think its not available for edgy... (Awn) I will ask about that then get back to you:)

---

### Post by reacocard on 2007-10-15
> **mk04 said:**
> When I get to the "./autogen.sh && make" part it says:

bash: ./autogen.sh: No such file or directory


I'm running Edgy Eft....

Did you cd to the right place? The terminal has to be in the same folder as the ./autogen.sh file.

---

### Post by mk04 on 2007-10-15
Yup. Just like the instructions said on the first page. BTW, I am currently running AWN.

---

### Post by reacocard on 2007-10-15
> **mk04 said:**
> Yup. Just like the instructions said on the first page. BTW, I am currently running AWN.

odd. try deleting the folder and starting the guide over from the start, I heard launchpad was having some issues the other day so it's entirely possible bzr just missed a file because of that.

---

### Post by madmatrixz3000 on 2007-10-15
hey i have a problem, I followed this guide and the curve guide and then AWN stops working!

What do I do to bring up the AWN

---

### Post by cudaman73 on 2007-10-15
> **madmatrixz3000 said:**
> hey i have a problem, I followed this guide and the curve guide and then AWN stops working!

What do I do to bring up the AWN

alt+f2 -> enter avant-window-navigator   ?

Btw, I just wanted to say, followed this guide, installed the milk theme, and I love it!

[http://img.photobucket.com/albums/v295/Cub3r7/screens/ssawn.png](http://img.photobucket.com/albums/v295/Cub3r7/screens/ssawn.png)

There's a screenshot. :D

Thanks a bunch!

---

### Post by nikoPSK on 2007-10-15
> **cudaman73 said:**
> alt+f2 -> enter avant-window-navigator   ?

Btw, I just wanted to say, followed this guide, installed the milk theme, and I love it!

[http://img.photobucket.com/albums/v295/Cub3r7/screens/ssawn.png](http://img.photobucket.com/albums/v295/Cub3r7/screens/ssawn.png)

There's a screenshot. :D

Thanks a bunch!

Welcome! What theme are you using? It looks great:p

---

### Post by cudaman73 on 2007-10-15
I was using SolidSlateModified with emerald, and milk for awn, but I've since changed it.

I absolutely love the window decorations in vista, so i've installed a non-GPL (:O) vista-styled theme, as seen here:

[http://img.photobucket.com/albums/v295/Cub3r7/screens/ss10152007.png](http://img.photobucket.com/albums/v295/Cub3r7/screens/ss10152007.png)

---

### Post by nikoPSK on 2007-10-15
```
sudo apt-get moo
```

XD what is the one you're using? Anyways I should give that a try.:popcorn:

---

### Post by cudaman73 on 2007-10-15
Actually, I used cowsay instead of moo :P

but yeah. It's called Vista-Compiz. It's probably one of the cleaner themes I've seen with emerald.

I'm loving it.

---

### Post by nikoPSK on 2007-10-15
> **cudaman73 said:**
> Actually, I used cowsay instead of moo :P

but yeah. It's called Vista-Compiz. It's probably one of the cleaner themes I've seen with emerald.

I'm loving it.

though, when i ask emerald to fetch themes, none appear. :( But yah, Im glad it worked good for most of you and keep posting your input/ output/ questions/ problems:KS

---

### Post by cudaman73 on 2007-10-16
At the bottom of the window, if you want it to get non-GPL'd themes, it tells you what to do.

```
svn ls https://svn.generation.no/emerald-themes
```

It'll ask you to accept the certificate, and then it'll get 'em right :D

---

### Post by Havek on 2007-10-16
I start to install it and then i get the error message :
```
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

```

How do i get m4 macors?

---

### Post by nikoPSK on 2007-10-16
> **Havek said:**
> I start to install it and then i get the error message :
```
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

```

How do i get m4 macors?

what version of ubu? I will look into it once I get the version:)

---

### Post by hanzomon4 on 2007-10-17
Oh dude... This is the good stuff

---

### Post by nikoPSK on 2007-10-17
> **hanzomon4 said:**
> Oh dude... This is the good stuff

welcome, And gutsy's only a day away!:popcorn:

---

### Post by Havek on 2007-10-17
> **nikoPSK said:**
> what version of ubu? I will look into it once I get the version:)

I am on Gusty.

---

### Post by KCPokes on 2007-10-17
Installs without errors but when I select the curved look it doesn't actually change to curve, rather it just looks like a variant of the flat bar.  I normally use the 3D look, which works fine, so I don't think its a AWN issue, per se.

---

### Post by dmontalvao on 2007-10-18
Hi! I had the same problem and found this thread. I have this working now on Gutsy. Here's what I did after starting reading the whole thread:

1) Post #1 (page 1) from nikoPSK - I followed his steps. PROBLEM: AWN stopped running (If I restarted it).

2) Post #16 (page 2) from nikoPSK - I removed, then reinstalled, as he said, but the problem seemed to persist. I don't think this step is needed.

3) Post #21 (page 3) from nikoPSK - I installed compizconfig-settings-manager in Synaptic, went to System->Preferences->Appearance->Visual Effects and chose custom. After this, AWN was still not running.

4) Post#27 (page 3) by datelus and Post#33 (page 4) by nikoPSK - This is what first confused me, but what made it work. lol. When I went to Synpatic i noticed these were not installed in my machine: awn-core-applets-bzr and libawn-bzr-dev. Well, instead of removing as they said, I added :P. And now I have it working perfectly.

I have no idea what I did. Maybe that's why "newb" and "noob" sound similar ;).

I hope this helps.

Cheers!
aka Lord Von M

---

### Post by Sturmeh on 2007-10-18
None of the above actually fixed my problem... :\

How to remove curves!!! :(

---

### Post by nikoPSK on 2007-10-18
> **dmontalvao said:**
> Hi! I had the same problem and found this thread. I have this working now on Gutsy. Here's what I did after starting reading the whole thread:

1) Post #1 (page 1) from nikoPSK - I followed his steps. PROBLEM: AWN stopped running (If I restarted it).

2) Post #16 (page 2) from nikoPSK - I removed, then reinstalled, as he said, but the problem seemed to persist. I don't think this step is needed.

3) Post #21 (page 3) from nikoPSK - I installed compizconfig-settings-manager in Synaptic, went to System->Preferences->Appearance->Visual Effects and chose custom. After this, AWN was still not running.

4) Post#27 (page 3) by datelus and Post#33 (page 4) by nikoPSK - This is what first confused me, but what made it work. lol. When I went to Synpatic i noticed these were not installed in my machine: awn-core-applets-bzr and libawn-bzr-dev. Well, instead of removing as they said, I added :P. And now I have it working perfectly.

I have no idea what I did. Maybe that's why "newb" and "noob" sound similar ;).

I hope this helps.

Cheers!
aka Lord Von M

I will talk to meek and reacocard about this.

> **KCPokes said:**
> Installs without errors but when I select the curved look it doesn't actually change to curve, rather it just looks like a variant of the flat bar.  I normally use the 3D look, which works fine, so I don't think its a AWN issue, per se.

Usually, it doesn't change right away for me. A quick refresh helps.

> **Sturmeh said:**
> None of the above actually fixed my problem... :\

How to remove curves!!! :(

I think that's impossible but you should be able to change back to another bar look.

---

### Post by Rupertronco on 2007-10-18
> **Sturmeh said:**
> None of the above actually fixed my problem... :\

How to remove curves!!! :(

It's actually very easy. Go to your awn-curves directory (in a terminal), and type ```
sudo make uninstall
```

This will remove awn-curves.

---

### Post by dynamethod on 2007-10-18
Heyas, i installed AWN no problems and it was running smoothly, (cept i couldnt get a curved bar), however now the bar has dissapeared :S, ive tried restarting AWN but nothing, i dont have 'autohide' ticked so its not that, i can access teh config menu for AWN but thats it, i cant see the bar anymore :S

and ya i got a compisitor(using compiz fusion)

---

### Post by hanzomon4 on 2007-10-18
Ah hell, It causes a segfault on gutsy

---

### Post by nikoPSK on 2007-10-18
> **hanzomon4 said:**
> Ah hell, It causes a segfault on gutsy

Sorry? I had it fine under gutsy tribe 5 and up. I haven't put it on the final yet. 

> **dynamethod said:**
> Heyas, i installed AWN no problems and it was running smoothly, (cept i couldnt get a curved bar), however now the bar has dissapeared :S, ive tried restarting AWN but nothing, i dont have 'autohide' ticked so its not that, i can access teh config menu for AWN but thats it, i cant see the bar anymore :S

and ya i got a compisitor(using compiz fusion)

Post those non-awn-curves related questions [here]("http://ubuntuforums.org/showthread.php?t=385981")

> **Rupertronco said:**
> It's actually very easy. Go to your awn-curves directory (in a terminal), and type ```
sudo make uninstall
```

This will remove awn-curves.

I've added that to my guide now.

---

### Post by Rupertronco on 2007-10-18
Glad I could help, and I think your guide is now in the Main AWN thread.

---

### Post by Vadi on 2007-10-19
I just installed AWN on Gutsy from reaocard instructions, and it was working okay. Then I installed this, installed both themes, but changing them didn't do anything. I tried quitting AWN and starting it again, but not it won't start!

Here's what the terminal says:

vadi@vadi-laptop:~/imts/imts/awn-curves$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)
vadi@vadi-laptop:~/imts/imts/awn-curves$ 


I'm using the stock version of Compiz.

---

### Post by endlesssnowfall on 2007-10-19
Seg fault here as well, on Gutsy, using custom configuration of Compiz Fusion.

---

### Post by pvdk on 2007-10-19
Hi, installed the ann-curves as explained, but when running the .autogen.sh && make I got this error:
[I]
philippe@philippe:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.2.0
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?[/I]

When I installed the tarball glib-2.2.0 there was a M4 macros map, Who knows what to do ... I'm not that familiar with scripts and cmd line installs.

Thanks

---

### Post by Vadi on 2007-10-19
Try sudo apt-get install m4 (or if you're in Gutsy, just click this link ([click]("apt:m4")))

And niko should include this in his first instruction too then.

Usually, when something is missing, head over for synaptic and search for it, and it'll get installed.

---

### Post by ajeetraj on 2007-10-19
I just followed the link how to install awn and i did everything what i was asked for...but when i run it i get this error in the terminal and nothing happens....any ideas? I am a noob otherwise i would have tried to solve it :(

 dpu@deepu:~/Desktop/avant-window-navigator$ avant-window-navigator avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory
dpu@deepu:~/Desktop/avant-window-navigator$ 


please help!

thanks!

---

### Post by Vadi on 2007-10-19
Try applications - assessories - avant window navigator.

---

### Post by ajeetraj on 2007-10-19
I did but still nothing happend! please help!

---

### Post by ajeetraj on 2007-10-19
so no one can help me eh :(

---

### Post by Vadi on 2007-10-19
Are you on Gutsy?

If you're on gutsy, and read a few pages back, you'll realise it's broken right now for Gutsy.

---

### Post by ajeetraj on 2007-10-19
yes i am on gutsy! oh so its broken. i see! 

thanks a lot for letting me know :)

---

### Post by Vadi on 2007-10-19
Yep, so just keep in touch with this thread, I'm sure they'll fix it soon :)

---

### Post by Rupertronco on 2007-10-19
> **Vadi said:**
> Are you on Gutsy?

If you're on gutsy, and read a few pages back, you'll realise it's broken right now for Gutsy.

Curves is not broken on Gutsy. You just have to install awn and curves from source as opposed to the pre-compiled packages. For information on how to install awn from source check out their page on launchpad.

[https://launchpad.net/awn](https://launchpad.net/awn)

I have awn curves and all of the applets working flawlessly on Gutsy right now.

---

### Post by Vadi on 2007-10-19
I tried compiling it from source, and it had error in it, so I just used reaocards.

It's great that you do, but in this thread specifically, they're broken. Since we're mortals here, and just want to get our curves without knowing how to compile things, we'll wait until this is fixed ;)

---

### Post by nikoPSK on 2007-10-19
> **Rupertronco said:**
> Glad I could help, and I think your guide is now in the Main AWN thread.

Yes reacocard put that there a week ago.

> **Vadi said:**
> Try sudo apt-get install m4 (or if you're in Gutsy, just click this link ([click]("apt:m4")))


And niko should include this in his first instruction too then.

Usually, when something is missing, head over for synaptic and search for it, and it'll get installed.

Thanks you, Sorry I have been away for a day and have not had time to answer questions or fix problems on this thread. Should I add m4 to my guide?

> **Rupertronco said:**
> Curves is not broken on Gutsy. You just have to install awn and curves from source as opposed to the pre-compiled packages. For information on how to install awn from source check out their page on launchpad.

[https://launchpad.net/awn](https://launchpad.net/awn)

I have awn curves and all of the applets working flawlessly on Gutsy right now.

Okay, how can you install curves from source. (So I can add it to my guide;))

---

### Post by harakiri1976 on 2007-10-19
[COLOR="Red"][B][B]Hello guys! 

I'm having problems with awn:(

I installed everything as it is described in the 1st post. Everything went ok. I restarted and went:
 
 System -> Preferences -> Awn Manager


 ...nothing happened:( So, I tried "calling" it using the command line and I got this:[/B][/B][/COLOR]

nuno@nuno-desktop:~$ awn-manager 
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:187: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 167, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 187, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue
[COLOR="Red"][COLOR="Red"][B]
 I restarted again and the problem is the same:(
 If I "call" awn-applet-activation I get this:[/B][/COLOR][/COLOR]

nuno@nuno-desktop:~$ awn-applet-activation 

** (awn-applet-activation:6554): WARNING **: You need to provide a uid for this applet
[COLOR="Red"][B]
If you guys have some clues, please send me some possibly tips, ok? or email me.


[email]hakariri1976@gmail.com[/email]

 Thanks[/B][/COLOR]

---

### Post by PharaohSD on 2007-10-19
> **harakiri1976 said:**
> [COLOR="Red"][B][B]Hello guys! 

I'm having problems with awn:(

I installed everything as it is described in the 1st post. Everything went ok. I restarted and went:
 
 System -> Preferences -> Awn Manager


 ...nothing happened:( So, I tried "calling" it using the command line and I got this:[/B][/B][/COLOR]

nuno@nuno-desktop:~$ awn-manager 
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:187: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 167, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 187, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue
[COLOR="Red"][COLOR="Red"][B]
 I restarted again and the problem is the same:(
 If I "call" awn-applet-activation I get this:[/B][/COLOR][/COLOR]

nuno@nuno-desktop:~$ awn-applet-activation 

** (awn-applet-activation:6554): WARNING **: You need to provide a uid for this applet
[COLOR="Red"][B]
If you guys have some clues, please send me some possibly tips, ok? or email me.


[email]hakariri1976@gmail.com[/email]

 Thanks[/B][/COLOR]




pyro@hydroflouric:~$ awn-manager
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:187: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 167, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 187, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue
[COLOR="Red"][SIZE="4"]
// we have the same problem[/SIZE][/COLOR]

I'm on 7.10 AMD64

anyone got any ideas?



I used this to install 
```
------
#first of all you need bazaar i can't remember the name of the package right now but i'm sure you'll get by yoursel, or searching here in lounchpad
#install dependency // edit sources list and add bazar to it
sudo apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common
#get files from launchpad bazaar
cd ~
bzr branch http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves
#configure, compile, and the install as super user
cd awn-curves
./autogen.sh && make && sudo make install
#if you want extra applets... and i'm shure you want do:



ah i think is worted to mention how to uninstal if you used bazar:
----------------------------------------------------------------------------------------------------------------------------------
cd ~/awn-curves
sudo make uninstall
cd ~/awn-extras/trunk/awn-applets/awn-core-applets
sudo make uninstall
#and if you want to remove the sources do:
cd ~
rm -Rf awn-curves
rm -Rf awn-extras

sorry i did a mistake:
#if you want extra applets... and i'm shure you want, do:
cd ~
mkdir awn-extras
cd awn-extras
bzr branch http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk
cd trunk/awn-applets/awn-core-applets
./autogen.sh && make && sudo make install
```

---

### Post by nikoPSK on 2007-10-19
...sorry guys... Gutsy had a problem, And I can't re-install it:( So Im kin-of stuck right now. I will let you know when I get gutsy up.

---

### Post by rahulthewall3000 on 2007-10-19
Ok, previously I installed awn-curves when I installed the normal awn installed. I removed both of them and then installed awn-curves. Now, when I try to start it I get the following error:

avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory

Can anyone tell me what the problem might be, and btw I am on gutsy!

Thanks
Rahul

---

### Post by rahulthewall3000 on 2007-10-19
Ok, that was stupid of me. I should have installed awn as well, which I did now and everything works now!

---

### Post by nikoPSK on 2007-10-19
> **rahulthewall3000 said:**
> Ok, that was stupid of me. I should have installed awn as well, which I did now and everything works now!

XD. Sorry I will add that you need awn installed first. My fault. :p

---

### Post by Vadi on 2007-10-19
I did install awn first, so I don't think this is an issue. Installing awn-curvers actually broke my awn.

---

### Post by Vadi on 2007-10-19
Actually, this is really odd, but it works now.

I did install a few packages between now and then, that might have fixed it :/

---

### Post by Havek on 2007-10-19
I need some help, awn runs fine and i am using it now, but i still ge the m4 error when trying to install.  I checked and it is installed on my computer so i don't know why this error is still coming up can it be anything else?

Error: ```
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

```

---

### Post by GraFF on 2007-10-20
I did everything as described in the first post, with no errors whatsoever, and this is what i get..

How can I at least return to the original theme that comes with awn? I've come to realize (too late though), that I like it better.

---

### Post by Marc Hoffman on 2007-10-20
I followed this guide using Gutsy- at first awn worked- then stopped when curves was installed due to a seg dump. I then checked all the required packages mentioned throughout this thread were installed- found a couple missing and now all is well. The milky bar looks great.

Thanks for the guide.

---

### Post by Vadi on 2007-10-20
> **Havek said:**
> I need some help, awn runs fine and i am using it now, but i still ge the m4 error when trying to install.  I checked and it is installed on my computer so i don't know why this error is still coming up can it be anything else?

Error: ```
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

```


Hm... check synaptic, do you also have autoconf installed (there are a lot of versions of it, but we just want any, I think). Along with the m4 of course.

---

### Post by Havek on 2007-10-20
> **Vadi said:**
> Hm... check synaptic, do you also have autoconf installed (there are a lot of versions of it, but we just want any, I think). Along with the m4 of course.

Yes i have this all installed and it still gives me the same error.

---

### Post by Vadi on 2007-10-20
Well, AWN is still version 0.2 or something - so it's not a finished product yet. Gutsy also just came out, so some things may have changed, and awn's authors didn't adapt it to that yet. So just keep checking back on this thread occasionally, maybe it'll be fixed. Or when reaocard updates his awn repository, check your awn then also :)

---

### Post by dmacdonald111 on 2007-10-20
Thanks for the how to. I have everything working nicely. I do have a couple of issues, but I am posting those on the official forum rather than here as your instructions worked. Thanks!

---

### Post by nikoPSK on 2007-10-20
> **GraFF said:**
> I did everything as described in the first post, with no errors whatsoever, and this is what i get..

How can I at least return to the original theme that comes with awn? I've come to realize (too late though), that I like it better.

That's not what it's supposed to look like.... Anyways just go to dock style then 3D look or the other one. Check my screenys (2nd post). Thats what it's supposed to look like...

> **Havek said:**
> I need some help, awn runs fine and i am using it now, but i still ge the m4 error when trying to install.  I checked and it is installed on my computer so i don't know why this error is still coming up can it be anything else?

Error: ```
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

```

Installing m4 or awn or curves?

> **Marc Hoffman said:**
> I followed this guide using Gutsy- at first awn worked- then stopped when curves was installed due to a seg dump. I then checked all the required packages mentioned throughout this thread were installed- found a couple missing and now all is well. The milky bar looks great.

Thanks for the guide.

Please give me the packages that were missing. Im new to ubuntu and Im trying to make this guide easy to use and helpful.

---

### Post by Dropknee on 2007-10-20
> **datelus said:**
> hmm you know what? it works now.. all i did - i removed these 
avant-window-navigator-bzr 
awn-core-applets-bzr 
libawn-bzr
libawn-bzr-dev 
python-libawn-bzr
 
now i have to remove that little white line :)

[http://foto.inbox.lv/sys6/08-12-2006/Screenshot-1.png](http://foto.inbox.lv/sys6/08-12-2006/Screenshot-1.png)

Thanks!!! this fix my segmentation fault problem, now work like charm :)

---

### Post by Dropknee on 2007-10-20
Ok I install back the package mentioned above to see what happen, and the dock still working.....

The strange thing about this is when I uninstall the above package, the program still installed, now, the question is.... How can I uninstall the dock completely from my system? I don´t want to do that now, but is good to know.

thanks

---

### Post by nar57981 on 2007-10-20
> **nikoPSK said:**
> Installing m4 or awn or curves?

You were talking to someone else, but I'm getting the same error message. I followed step by step your list of instructions. The only line that I didn't type in my terminal was the one that you said to skip if AWM was already installed.
I tried redoing the "sudo...M4" code again but it said that nothing was downloaded/upgraded after.

Thanks for the guide, hope it gets working in 7.10 better soon

---

### Post by nikoPSK on 2007-10-20
> **nar57981 said:**
> You were talking to someone else, but I'm getting the same error message. I followed step by step your list of instructions. The only line that I didn't type in my terminal was the one that you said to skip if AWM was already installed.
I tried redoing the "sudo...M4" code again but it said that nothing was downloaded/upgraded after.

Thanks for the guide, hope it gets working in 7.10 better soon

reason is: I get it too. I think the developer is trying to get a gutsy version.

---

### Post by Dropknee on 2007-10-20
> The only line that I didn't type in my terminal was the one that you said to skip if AWM was already installed

You need to do that line too, because when he said than you don´t need that line is because he suppose you do the compile method. Use that line to install all the dev package you need to compile the Awn-Curve.

---

### Post by nikoPSK on 2007-10-20
> **Dropknee said:**
> ```
The only line that I didn't type in my terminal was the one that you said to skip if AWM was already installed
```

You need to do that line too, because when he said than you don´t need that line is because he suppose you do the compile method. Use that line to install all the dev package you need to compile the Awn-Curve.

my bad, I removed that. It has some packages that you need.:) (Awn still no worky for me in gutsy final.) Ill see what I can do:KS

---

### Post by nikoPSK on 2007-10-20
to completely remove awn, do this:

```
sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
```

And un-install curves. (I tell how on first page of this thread.)

---

### Post by Dropknee on 2007-10-20
I got a question, I install the theme you provide us, but, I see a glass one in the 3 screenshots, where can I get that theme? is the default one?? because is this glass looking one is the default, how can I get the default one? I uninstall the black one, to get the default, but the black theme still applied, any tip to reset to the default one?

Thanks and sorry to bother.

---

### Post by Morton's Red Stapler on 2007-10-20
ok, i have awn working perfect in gutsy, the problem i am having is getting curves to work, i did not install using source, i used the apt-get command, but when i install curves, it shows up in my settings menu, but when i select it just reverts to a flat theme, how can i get this to work properly? (sry if this is a repetitive question, but i have read the entire topic and got no answer to this question)

---

### Post by nikoPSK on 2007-10-20
> **Morton's Red Stapler said:**
> ok, i have awn working perfect in gutsy, the problem i am having is getting curves to work, i did not install using source, i used the apt-get command, but when i install curves, it shows up in my settings menu, but when i select it just reverts to a flat theme, how can i get this to work properly? (sry if this is a repetitive question, but i have read the entire topic and got no answer to this question)

If you've installed everything right. Goto your home folder then copy the awn-curves folder into your usr/share directory.

---

### Post by nikoPSK on 2007-10-20
> **Dropknee said:**
> I got a question, I install the theme you provide us, but, I see a glass one in the 3 screenshots, where can I get that theme? is the default one?? because is this glass looking one is the default, how can I get the default one? I uninstall the black one, to get the default, but the black theme still applied, any tip to reset to the default one?

Thanks and sorry to bother.

If you would read, Milk theme located above. Click on the link to download the theme.:) then drag the file into your themes, apply and refresh! In the screenshot Im using milk!;)

---

### Post by Espreon on 2007-10-20
This is what I get when I try to run it in the terminal:

```

avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory

```

Autogen.sh:

```

/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE
Running autoconf...
Running autoheader...
Running automake-1.9...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a Python interpreter with version >= 2.3.5... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... yes
checking for pygtk-codegen-2.0... /usr/bin/pygtk-codegen-2.0
checking for pygtk defs... /usr/share/pygtk/2.0/defs
checking for PYCAIRO... yes
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.34... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  ar bg ca cs da de de_DE el en_AU en_GB es eu fa fi fi_FI fr fr_FR gl he hr hu it it_IT ja ka ko nb nl nn no_NO pl pt_BR pt ro ru ru_RU sk sr sv tr zh_CN zh_HK zh_TW
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.8.0... yes (version 2.14.1)
checking for AWN... yes
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
configure: creating ./config.status
config.status: creating Makefile
config.status: creating awn-manager/Makefile
config.status: creating libawn/Makefile
config.status: creating src/Makefile
config.status: creating awn-applet-activation/Makefile
config.status: creating applets/Makefile
config.status: creating data/Makefile
config.status: creating data/active/Makefile
config.status: creating po/Makefile.in
config.status: creating pyawn/Makefile
config.status: creating awn.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

```

---

### Post by nikoPSK on 2007-10-20
sorry, copy the awn-curves folder from your home folder into usr/share. I'm trying to get it up under gutsy too. Will have updates hopefully by tomorrow:popcorn:

---

### Post by sixstorm on 2007-10-20
Thanks!  I've never really used AVN very much but this gives a nice appeal to it.  Here's my desktop, fresh 7.10 AMD64:

[IMG]http://img85.imageshack.us/img85/1487/710screenmv9.png[/IMG]

Sorry if it's too big.

---

### Post by Khuezy on 2007-10-20
I installed the curve and I have the "curve option" under the flat and 3d look but my awn isn't curving. Help please. Thanks.

---

### Post by nikoPSK on 2007-10-20
goto /home/NAME/awn-curves/src (replace NAME with your username) and run avant-window-navigator and it works...:confused: I will try to get the one under apps to work.:)

---

### Post by Espreon on 2007-10-20
> **sixstorm said:**
> Thanks!  I've never really used AVN very much but this gives a nice appeal to it.  Here's my desktop, fresh 7.10 AMD64:.

Dude, if you wanted to protect the IM usernames by blurring them,  you shoulda blur the other guy's name out too, plus I can see your IM username by looking at the window bar.... in your screenshot.

---

### Post by Espreon on 2007-10-20
> **nikoPSK said:**
> sorry, copy the awn-curves folder from your home folder into usr/share. I'm trying to get it up under gutsy too. Will have updates hopefully by tomorrow:popcorn:

I still get that error.....

---

### Post by nikoPSK on 2007-10-21
> **Espreon said:**
> I still get that error.....

waaaaaah! I'm having problems too.My friend said that helped, but it didn't. I will wait. Sorry about the problems with gutsy final everyone. I will see what I can do. :(

---

### Post by nikoPSK on 2007-10-21
gutsy final users! it will work now! YAY! see the important on the first post.:KS

---

### Post by Selfish Meme on 2007-10-21
I also found that like others just reinstalling these packages after installing curves and moving the awn-curves directory to /usr/share worked too...

avant-window-navigator-bzr
awn-core-applets-bzr
libawn-bzr
libawn-bzr-dev
python-libawn-bzr

Now my only problem is making the applet icons uniformly sized.

Also a problem with the curves uninstall is that AWN loses track of the themes module and thats why it wont start after you uninstall awn-curves.

---

### Post by nikoPSK on 2007-10-21
I tried moving the awn-curves from my home to usr/shared didn't work:( how did it go for you?

---

### Post by nikoPSK on 2007-10-21
> **Selfish Meme said:**
> I also found that like others just reinstalling these packages after installing curves and moving the awn-curves directory to /usr/shared worked too...

avant-window-navigator-bzr
awn-core-applets-bzr
libawn-bzr
libawn-bzr-dev
python-libawn-bzr

Now my only problem is making the applet icons uniformly sized.

Also a problem with the curves uninstall is that AWN loses track of the themes module and thats why it wont start after you uninstall awn-curves.

how do you move it? It won't let me so I use the terminal to move it. Is there any way to move it without terminal?:confused:

---

### Post by Selfish Meme on 2007-10-21
I upgraded to Gutsy, so I am not sure if my experience will help on a fresh install, I had the same problems as others with the segmentation fault, I uninstalled curves and AWN still didn't work (because of the missing themes module) I reinstalled curves and it started working again but just with flat bars and I could not open the manager, I moved the directory and reinstalled those packages and now it works fine.

---

### Post by nikoPSK on 2007-10-21
It suddenly works now....:confused::lolflag::guitar:

---

### Post by Selfish Meme on 2007-10-21
sudo mv awn-curves /usr/share/awn-curves

---

### Post by Espreon on 2007-10-21
> **nikoPSK said:**
> It suddenly works now....:confused::lolflag::guitar:

Me too.... Maybe it was my reboot...

---

### Post by Raj_Dharwad on 2007-10-21
Hi Niko,

i am running on Gutsy Final Release, AWN curves is not lauching from Apps nor from RUN, please let me know if there is any fix for this... 

anybody who has faced this issue?

Regards,

Raj

---

### Post by GraFF on 2007-10-21
> **nikoPSK said:**
> That's not what it's supposed to look like.... Anyways just go to dock style then 3D look or the other one. Check my screenys (2nd post).


I understand that :) Deleting the installed themes leaves me with what is on the shot, and going from flat to 3d-view changes only the tilt.. Still can't get the original skin back. :(
this is the best i can get:

---

### Post by k3ano on 2007-10-21
I followed the instructions (I think I followed them correctly)  but the theme didn't look right.  After restarting my comp AWN will load but the manager wont.

Does anyone know where I've gone wrong? :confused:

---

### Post by takuhii on 2007-10-21
Can't someone just compile this in Gutsy/Feisty and post it here for us to download. I can't get the MAKE process to run correctly.

---

### Post by nikoPSK on 2007-10-21
you know what everyone? I didn't put awn in my usr/share. Im in gutsy final. and I didnt reboot. I removed awn/ awn-curves. Followed my guide. Went to [reacocard's guide]("http://ubuntuforums.org/showthread.php?t=385981") put the gutsy repos, then downloaded everything and installed awn, And it worked. (!) So heres what I did:

```
sudo apt-get install bzr
sudo apt-get install m4
sudo apt-get install gnome-common
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
cd awn-curves
./autogen.sh && make
sudo make install
```

Then I added the repos to my list: 

type this in terminal:

```
gksudo "gedit /etc/apt/sources.list"
```

Then add these at the bottom of the list:

```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

then do these last codes:

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
```

finally,

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

;) Hope it helps! If it does tell me!

---

### Post by Syirrus on 2007-10-21
For those of use who are getting the following error message when trying to run awn-curves:
```

Screen is composited.
APPLET : /usr/lib/awn/applets/trash.desktop
Segmentation fault (core dumped)

```

A solution that work for me was running awn out of the /home/$username/awn-curves/src/.avant-window-navigator

It worked like a charm.

---

### Post by nikoPSK on 2007-10-21
> **Syirrus said:**
> For those of use who are getting the following error message when trying to run awn-curves:
```

Screen is composited.
APPLET : /usr/lib/awn/applets/trash.desktop
Segmentation fault (core dumped)

```

A solution that work for me was running awn out of the /home/$username/awn-curves/src/.avant-window-navigator

It worked like a charm.

yes that was a solution for me too. Foll my guide now. Awn should work from apps,:guitar:

---

### Post by Morton's Red Stapler on 2007-10-21
:popcorn: alls working now, ty for the updates and fast responses. i love the way it looks

---

### Post by k3ano on 2007-10-21
Ok, I've got mine to work now :D

1 tiny problem though, my "Trash" applet appears really small, everything else is fine.

EDIT: Ok, I just resized the bar a bit in the preferences and everything is A-OK.  :D

---

### Post by nikoPSK on 2007-10-21
> **k3ano said:**
> Ok, I've got mine to work now :D

1 tiny problem though, my "Trash" applet appears really small, everything else is fine.

EDIT: Ok, I just resized the bar a bit in the preferences and everything is A-OK.  :D

Mine does too. Glad it works. I guess the trick was to put it first :lolflag:

---

### Post by MNICY on 2007-10-21
Im going to try again now, with a fresh install of gutsy (I just love partitions, i can install gutsy and keep my feisty intact in case i want to switch back, and i can transfer my documents easily)

wish me luck! :)

---

### Post by MNICY on 2007-10-21
Worked perfectly!
thanks so much.
Did it on a fresh install of Ubuntu Gutsy (amd46)

---

### Post by hagarid on 2007-10-21
:confused:Not sure what I did wrong. I followed the instructions to the letter
Install awn curves:
Code:

sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves
cd awn-curves
./autogen.sh && make
sudo make install

I was doing "./autogen.sh && make" when the message 

shift: 370: can't shift that many

Happened It was after allot of other stuff but wasn't sure if you needed all the other stuff to figure it out. If you do need it I will post the whole action it said. Thank you in advance if you can figure out just how I screwed up. I am new at this and thought I was getting the hang of it but guess not LOL

---

### Post by nikoPSK on 2007-10-21
ummmmmmmmmmmmmmmmmmmmmmmmmm... :confused: uhhhhhhh.... hun....... I haven't a clue:( Just give it another shot. :popcorn:

Yes everyone! Guide is final now! (And it works!!!) Im so happy. I had to figure this out on my own. But I guess installing awn after works:p

---

### Post by speadskater on 2007-10-21
Awn manager is not opening. when i try to launch it.  i installed it step by step, but i can't seem to get this app to open.


edit:

when i look under:
/home/josh/.config/awn/launchers

there is nothing... which probably could explain why it's not launching.

can anyone help me with this fix?

---

### Post by nikoPSK on 2007-10-22
search synaptic for awn-manager.:guitar:

---

### Post by hopelessone on 2007-10-22
i get errors...

please help...

made it all the way till the last line here is what happened...

shane@lotus:~/awn-curves$ [COLOR="Red"]sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libglib2.0-0 (>= 2.14.0) but 2.13.7-1ubuntu5 is to be installed
                              Depends: libgtk2.0-0 (>= 2.12.0) but 2.11.6-1ubuntu3 is to be installed
                              Depends: libpango1.0-0 (>= 1.18.2) but 1.17.5-1ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr129-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libglib2.0-0 (>= 2.14.0) but 2.13.7-1ubuntu5 is to be installed
                        Depends: libgtk2.0-0 (>= 2.12.0) but 2.11.6-1ubuntu3 is to be installed
                        Depends: libpango1.0-0 (>= 1.18.2) but 1.17.5-1ubuntu1 is to be installed
                        Depends: librsvg2-2 (>= 2.18.1) but 2.18.0-1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
[COLOR="Red"]E: Broken packages[/COLOR]
shane@lotus:~/awn-curves$ 

what should i do?

thanks

---

### Post by Lucrezia on 2007-10-22
help :(

> 

calipso@calipso:~$ awn-manager
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:187: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 167, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 187, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue



---

### Post by dynamethod on 2007-10-22
SS of AWN on my desktop :P

---

### Post by boob11 on 2007-10-22
thnx

---

### Post by speadskater on 2007-10-22
> **nikoPSK said:**
> search synaptic for awn-manager.:guitar:

There's nothing there...

---

### Post by nikoPSK on 2007-10-22
Is it just the manager that isn't launching? Or awn and the manager?

---

### Post by hagarid on 2007-10-22
OK tried again and got the same message?? figured I should post the rest of what it said. 

*****@****-desktop:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... not found.
***Error***: You must have automake >= 1.9 installed
  to build avant-panel-menu.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz](http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz)

checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
/usr/bin/gnome-autogen.sh: 370: --print-ac-dir: not found
ACLOCAL=''
AUTOCONF='autoconf'
AUTOCONF_VERSION='2.61'
AUTOHEADER='autoheader'
COLORTERM='gnome-terminal'
DBUS_SESSION_BUS_ADDRESS='unix:abstract=/tmp/dbus-D29ECBjKK0,guid=50f7768e7de50c2fe950e300471cb62f'
DESKTOP_SESSION='default'
DIE='1'
DISPLAY=':0.0'
ECHO_C=''
ECHO_N='-n'
FORBIDDEN_M4MACROS=' gnome-cxx-check.m4'
GDMSESSION='default'
GDM_LANG='en_US.UTF-8'
GDM_XSERVER_LOCATION='local'
GLIB_GETTEXTIZE='glib-gettextize'
GLIB_GETTEXTIZE_VERSION='2.14.1'
GNOME_DESKTOP_SESSION_ID='Default'
GNOME_KEYRING_PID='5525'
GNOME_KEYRING_SOCKET='/tmp/keyring-U494wO/socket'
GTK_RC_FILES='/etc/gtk/gtkrc:/home/****/.gtkrc-1.2-gnome2'
HISTCONTROL='ignoreboth'
HOME='/home/****'
IFS='.'
INTLTOOLIZE='intltoolize'
INTLTOOLIZE_VERSION='0.36.2'
LANG='en_US.UTF-8'
LESSCLOSE='/usr/bin/lesspipe %s %s'
LESSOPEN='| /usr/bin/lesspipe %s'
LIBTOOLIZE='libtoolize'
LIBTOOLIZE_VERSION='1.5.24'
LOGNAME='*****'
LS_COLORS='no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:'
OLDPWD='/home/****'
OPTIND='1'
PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'
PKG_CONFIG='pkg-config'
PKG_CONFIG_VERSION='0.22'
PKG_NAME='avant-panel-menu'
PPID='6110'
PS1='$ '
PS2='> '
PS4='+ '
PWD='/home/****/awn-curves'
REQUIRED_AUTOCONF_VERSION='2.53'
REQUIRED_AUTOMAKE_VERSION='1.9'
REQUIRED_DOC_COMMON_VERSION='2.3.0'
REQUIRED_GETTEXT_VERSION='0.12'
REQUIRED_GLIB_GETTEXT_VERSION='2.2.0'
REQUIRED_GNOME_DOC_UTILS_VERSION='0.4.2'
REQUIRED_GTK_DOC_VERSION='1.0'
REQUIRED_INTLTOOL_VERSION='0.30'
REQUIRED_LIBTOOL_VERSION='1.5'
REQUIRED_M4MACROS=' libtool.m4 glib-gettext.m4 intltool.m4 pkg.m4'
REQUIRED_PKG_CONFIG_VERSION='0.14.0'
SESSION_MANAGER='local/****-desktop:/tmp/.ICE-unix/5528'
SHELL='/bin/bash'
SHLVL='1'
SSH_AGENT_PID='5565'
SSH_AUTH_SOCK='/tmp/ssh-vCxiAh5528/agent.5528'
TERM='xterm'
USER='roy'
USERNAME='roy'
WANT_AUTOCONF_2_5='1'
WINDOWID='56623185'
WINDOWPATH='7'
XAUTHORITY='/home/****/.Xauthority'
XDG_DATA_DIRS='/usr/local/share/:/usr/share/:/usr/share/gdm/'
XDG_SESSION_COOKIE='4f502d2a3ed71fa8924ccc0047188300-1193063982.96979-1866004702'
_='./autogen.sh'
automake_progs='automake-1.10 automake-1.9'
boldface=''
ch_actual_version=''
ch_cur='22'
ch_min='14'
ch_min_version='1.7'
ch_save_IFS=' 
'
ch_status='0'
cm_macrodirs=''
configure_ac='./configure.in'
configure_files='./awn-curves/configure.in
./configure.in'
dirname='.'
normal=''
srcdir='.'
vc_actual_version='0.22'
vc_checkprog='pkg-config'
vc_checkprogs='pkg-config'
vc_comparator='>='
vc_min_version='0.14.0'
vc_package='pkg-config'
vc_source=''"'"'http://www.freedesktop.org/software/pkgconfig/releases/pkgconfig-0.14.0.tar.gz'
vc_status='0'
vc_variable='PKG_CONFIG'
want_gettext='false'
want_glib_gettext='true'
want_gnome_doc_utils='false'
want_gtk_doc='false'
want_intltool='true'
want_libtool='true'
want_pkg_config='true'
shift: 370: can't shift that many
*****@****-desktop:~/awn-curves$ 

Is there some thing I did wrong or is there another way to install it??:confused:

Thanks again

---

### Post by Mikey_S on 2007-10-22
Works great thanks alot for all the info!!! here's my desktop!!

---

### Post by nikoPSK on 2007-10-22
> **hagarid said:**
> OK tried again and got the same message?? figured I should post the rest of what it said. 

*****@****-desktop:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... not found.
***Error***: You must have automake >= 1.9 installed
  to build avant-panel-menu.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz](http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz)

checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
/usr/bin/gnome-autogen.sh: 370: --print-ac-dir: not found
ACLOCAL=''
AUTOCONF='autoconf'
AUTOCONF_VERSION='2.61'
AUTOHEADER='autoheader'
COLORTERM='gnome-terminal'
DBUS_SESSION_BUS_ADDRESS='unix:abstract=/tmp/dbus-D29ECBjKK0,guid=50f7768e7de50c2fe950e300471cb62f'
DESKTOP_SESSION='default'
DIE='1'
DISPLAY=':0.0'
ECHO_C=''
ECHO_N='-n'
FORBIDDEN_M4MACROS=' gnome-cxx-check.m4'
GDMSESSION='default'
GDM_LANG='en_US.UTF-8'
GDM_XSERVER_LOCATION='local'
GLIB_GETTEXTIZE='glib-gettextize'
GLIB_GETTEXTIZE_VERSION='2.14.1'
GNOME_DESKTOP_SESSION_ID='Default'
GNOME_KEYRING_PID='5525'
GNOME_KEYRING_SOCKET='/tmp/keyring-U494wO/socket'
GTK_RC_FILES='/etc/gtk/gtkrc:/home/****/.gtkrc-1.2-gnome2'
HISTCONTROL='ignoreboth'
HOME='/home/****'
IFS='.'
INTLTOOLIZE='intltoolize'
INTLTOOLIZE_VERSION='0.36.2'
LANG='en_US.UTF-8'
LESSCLOSE='/usr/bin/lesspipe %s %s'
LESSOPEN='| /usr/bin/lesspipe %s'
LIBTOOLIZE='libtoolize'
LIBTOOLIZE_VERSION='1.5.24'
LOGNAME='*****'
LS_COLORS='no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:'
OLDPWD='/home/****'
OPTIND='1'
PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'
PKG_CONFIG='pkg-config'
PKG_CONFIG_VERSION='0.22'
PKG_NAME='avant-panel-menu'
PPID='6110'
PS1='$ '
PS2='> '
PS4='+ '
PWD='/home/****/awn-curves'
REQUIRED_AUTOCONF_VERSION='2.53'
REQUIRED_AUTOMAKE_VERSION='1.9'
REQUIRED_DOC_COMMON_VERSION='2.3.0'
REQUIRED_GETTEXT_VERSION='0.12'
REQUIRED_GLIB_GETTEXT_VERSION='2.2.0'
REQUIRED_GNOME_DOC_UTILS_VERSION='0.4.2'
REQUIRED_GTK_DOC_VERSION='1.0'
REQUIRED_INTLTOOL_VERSION='0.30'
REQUIRED_LIBTOOL_VERSION='1.5'
REQUIRED_M4MACROS=' libtool.m4 glib-gettext.m4 intltool.m4 pkg.m4'
REQUIRED_PKG_CONFIG_VERSION='0.14.0'
SESSION_MANAGER='local/****-desktop:/tmp/.ICE-unix/5528'
SHELL='/bin/bash'
SHLVL='1'
SSH_AGENT_PID='5565'
SSH_AUTH_SOCK='/tmp/ssh-vCxiAh5528/agent.5528'
TERM='xterm'
USER='roy'
USERNAME='roy'
WANT_AUTOCONF_2_5='1'
WINDOWID='56623185'
WINDOWPATH='7'
XAUTHORITY='/home/****/.Xauthority'
XDG_DATA_DIRS='/usr/local/share/:/usr/share/:/usr/share/gdm/'
XDG_SESSION_COOKIE='4f502d2a3ed71fa8924ccc0047188300-1193063982.96979-1866004702'
_='./autogen.sh'
automake_progs='automake-1.10 automake-1.9'
boldface=''
ch_actual_version=''
ch_cur='22'
ch_min='14'
ch_min_version='1.7'
ch_save_IFS=' 
'
ch_status='0'
cm_macrodirs=''
configure_ac='./configure.in'
configure_files='./awn-curves/configure.in
./configure.in'
dirname='.'
normal=''
srcdir='.'
vc_actual_version='0.22'
vc_checkprog='pkg-config'
vc_checkprogs='pkg-config'
vc_comparator='>='
vc_min_version='0.14.0'
vc_package='pkg-config'
vc_source=''"'"'http://www.freedesktop.org/software/pkgconfig/releases/pkgconfig-0.14.0.tar.gz'
vc_status='0'
vc_variable='PKG_CONFIG'
want_gettext='false'
want_glib_gettext='true'
want_gnome_doc_utils='false'
want_gtk_doc='false'
want_intltool='true'
want_libtool='true'
want_pkg_config='true'
shift: 370: can't shift that many
*****@****-desktop:~/awn-curves$ 

Is there some thing I did wrong or is there another way to install it??:confused:

Thanks again

Well, you don't have automake. [http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz]("http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz") ther 'yare

---

### Post by Morton's Red Stapler on 2007-10-22
niko is right, you have to install curves, then, while still cd'ed in the awn-curves folder, install AWN AFTER awn curves. this is what my desktop looks like.
[[IMG]http://img401.imageshack.us/img401/2885/screenshot9cr9.th.png[/IMG]](http://img401.imageshack.us/my.php?image=screenshot9cr9.png)



oh yeah, hey niko, "there is no cow level"

---

### Post by Vadi on 2007-10-22
> **nikoPSK said:**
> Well, you don't have automake. [http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz]("http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz") ther 'yare

You need to keep in mind that if he didn't realize he needs automake, I *really* doubt he'll breeze through the .tar.gz file.

To make your life easier, just click on this link if you're on gutsy - [apt:automake1.9]("apt:automake1.9") in firefox, and voila!

---

### Post by hagarid on 2007-10-22
Wah-Hooo!! finally got it up and working.

---

### Post by hagarid on 2007-10-22
Actually found Automake in Synaptic and installed it from there. I had forgotten to   re-enable visual effects in Appearance Preference. But once it was done see post above works great!! Thakns for the help and concern.

---

### Post by siege911 on 2007-10-22
> **nikoPSK said:**
> Is it just the manager that isn't launching? Or awn and the manager?

I'm having the same issue. I go to System -> Preferences -> Awn Manager and nothing happens. Nothing at all. No errors. No manager. Nothing,

---

### Post by Pandemic187 on 2007-10-22
```
E: Couldn't find package libgnome-vfs-dev
```
I keep getting this when using apt-get. Anyone know why?

---

### Post by speadskater on 2007-10-22
> **nikoPSK said:**
> Is it just the manager that isn't launching? Or awn and the manager?

not sure... but here is what happens when i type it into the terminal

josh@josh-laptop:~$ awn-manager
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:187: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 167, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 187, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue

---

### Post by nikoPSK on 2007-10-22
Im pretty sure this is just an awn issue. because other people are having the same problems in just awn.

---

### Post by nikoPSK on 2007-10-22
> **Morton's Red Stapler said:**
> niko is right, you have to install curves, then, while still cd'ed in the awn-curves folder, install AWN AFTER awn curves. this is what my desktop looks like.
[[IMG]http://img401.imageshack.us/img401/2885/screenshot9cr9.th.png[/IMG]](http://img401.imageshack.us/my.php?image=screenshot9cr9.png)



oh yeah, hey niko, "there is no cow level"

??? Cow level? Starcraft related? Or diablo... or something else?:lolflag:

---

### Post by speadskater on 2007-10-22
> **nikoPSK said:**
> Im pretty sure this is just an awn issue. because other people are having the same problems in just awn.

so there's no fix yet?

---

### Post by nikoPSK on 2007-10-22
Finding out as we speak. It's not just awn curves, it's general awn. Seen a couple problems on R's guide as well that have been posted. i'll update you and (if) there is a way I'll tell you how to fix it.

---

### Post by speadskater on 2007-10-22
thanks.  i'm really looking forward to using awn

---

### Post by nikoPSK on 2007-10-22
:D

Well, I havn't switched to fulltime awn yet. Making the transition slowly...

---

### Post by speadskater on 2007-10-22
why of course.  Linux has so many different themes and customizations that you can't just pick one.

---

### Post by hopelessone on 2007-10-22
nikoPSK - Did you know why it gave me those errors i posted on page 14 of this topic??

thanks

---

### Post by BoardDWorld on 2007-10-23
Thanks for the tutorial, it's up and running nicely on my fresh Gutsy install. Just one thing though,is it not possible to use a custom .png for app launcher icons?

Also I have that "tiny trash can" bug people are reporting.

---

### Post by hopelessone on 2007-10-23
ok...

Totally wiped my hard drive ...did a **FRESH** install of Gusty 7.10 and NOW it installed without error...

the upgrade from 7.04 -> 7.10 didn't

**how do i use it?** i clicked on System>>Preferences>>AWN Manager and nothing happens??

ubuntu@ubuntu-desktop:~$ awn-manager
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:187: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 167, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 187, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue

rebooted and instead went to Applications >> Accessories >> AWN Manager and it worked !!

thanks..

---

### Post by Bishop Hill on 2007-10-23
I have a couple of problems with AWN.

First, when I close a program from awn (by pressing one of the icons on te bar) from it the motions lag, Why? I have compiz and everything installed and they run perfectly, so it cant be my graphics card.

Second, I cant get those damn curves to work. Everything works, except the curves. When I try 

```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
cd awn-curves
./autogen.sh && make
sudo make install
```

I get

```

daniel@daniel-laptop:~/glib-2.2.0/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.2.0
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

daniel@daniel-laptop:~/glib-2.2.0/awn-curves$ sudo make install
make: *** Ingen regel för att skapa målet "install".  Stannar.
```

The last part is probably translated into "no rule to create the target "install". Stops".

How do I solve this? I noticed a lot of people in this thread had the same problem, but they weren't solved=(

edit:

Ok, I don't have glib-gettext.m4, is that the problem? How do I solve it?

Also, I use gutsy gremlin 7.10=)

---

### Post by hopelessone on 2007-10-23
i had the same its from a broken download redo -

**sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev**

and 

**bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves**

then continue worked for me...

---

### Post by SCGreg on 2007-10-23
had a quick scout through the thread but I can't see anything relating... when I try to enable the seperator to split running processes and applications, nothing happens - any ideas? I've even set the colour to red and opacity 100% to make sure it's not there.. they're not even split up so applications are one side, processes are another

[[IMG]http://img515.imageshack.us/img515/2109/screenshotlt1.th.png[/IMG]](http://img515.imageshack.us/my.php?image=screenshotlt1.png)

(arrow enabled for clarity)

---

### Post by nikoPSK on 2007-10-23
> **Bishop Hill said:**
> I have a couple of problems with AWN.

First, when I close a program from awn (by pressing one of the icons on te bar) from it the motions lag, Why? I have compiz and everything installed and they run perfectly, so it cant be my graphics card.

Second, I cant get those damn curves to work. Everything works, except the curves. When I try 

```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
cd awn-curves
./autogen.sh && make
sudo make install
```

I get

```

daniel@daniel-laptop:~/glib-2.2.0/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.2.0
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

daniel@daniel-laptop:~/glib-2.2.0/awn-curves$ sudo make install
make: *** Ingen regel för att skapa målet "install".  Stannar.
```

The last part is probably translated into "no rule to create the target "install". Stops".

How do I solve this? I noticed a lot of people in this thread had the same problem, but they weren't solved=(

edit:

Ok, I don't have glib-gettext.m4, is that the problem? How do I solve it?

Also, I use gutsy gremlin 7.10=)

[here]("http://packages.ubuntu.com/gutsy/devel/gettext") is gettext. It also appears you don't have autoconf. [there you are.]("http://packages.ubuntu.com/gutsy/devel/autoconf"):)

---

### Post by nikoPSK on 2007-10-23
> **SCGreg said:**
> had a quick scout through the thread but I can't see anything relating... when I try to enable the seperator to split running processes and applications, nothing happens - any ideas? I've even set the colour to red and opacity 100% to make sure it's not there.. they're not even split up so applications are one side, processes are another

[[IMG]http://img515.imageshack.us/img515/2109/screenshotlt1.th.png[/IMG]](http://img515.imageshack.us/my.php?image=screenshotlt1.png)

(arrow enabled for clarity)

Unfortunately separators in curves only increase the length between items without a graphical representation. (Please just attach your images rather that giving links, I don't like the ads.):)

---

### Post by SCGreg on 2007-10-23
> **nikoPSK said:**
> Unfortunately separators in curves only increase the length between items without a graphical representation. (Please just attach your images rather that giving links, I don't like the ads.):)

cool - so long as it's a known problem, and isn't just me being an idiot!

---

### Post by Rupertronco on 2007-10-23
> **nikoPSK said:**
> Yes reacocard put that there a week ago.



Thanks you, Sorry I have been away for a day and have not had time to answer questions or fix problems on this thread. Should I add m4 to my guide?



Okay, how can you install curves from source. (So I can add it to my guide;))

Sorry I haven't been around for a few days, but I'll put up a post as how to install it from source this evening.

---

### Post by d3mon on 2007-10-23
sorry people..but i have two n00b questions..

1st...I followed the instructions from begining of this post and i installed AWN and curves..it works perfectly if i run it in terminal from /home/$username/awn-curves/src/..so my question is: how to make this autostart when i log in so that i don't have to run it manually?

2nd..how can i get rid off those white dots under the icons in the dock?

---

### Post by d3mon on 2007-10-23
ups, sorry..i solved the part with white dots..heh

---

### Post by hagarid on 2007-10-23
> **d3mon said:**
> sorry people..but i have two n00b questions..

1st...I followed the instructions from begining of this post and i installed AWN and curves..it works perfectly if i run it in terminal from /home/$username/awn-curves/src/..so my question is: how to make this autostart when i log in so that i don't have to run it manually?

2nd..how can i get rid off those white dots under the icons in the dock?

See you got the dots taken care of. The auto start thing I did through "Sessions" It is easy and I not just saying that because I am stupid and I figured it out. 

1. go System>Preferences>Sessions click and open. 

2. Under "Startup Programs" tab hit add

3. Type "avant window navigator" in Name window (Not sure if you have to type it all but better safe than sorry.)

4. Type "avant-window-navigator" in command window. Or browes to that folder where you put it and hit 'ok' button

5. finally just make sure there is a check in the box by your new entry. and restart to make sure it is working. :)

Hope ths helped.

---

### Post by nikoPSK on 2007-10-23
Why do people always beat me too it? Anyways thanks:) Oh and for the gutsy/ source thing. That's pretty much solved. (I figured you had to install curves first then awn.):KS

---

### Post by nikoPSK on 2007-10-23
> **hopelessone said:**
> i had the same its from a broken download redo -

**sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev**

and 

**bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves**

then continue worked for me...

Updated it.:)

---

### Post by Morton's Red Stapler on 2007-10-23
> **nikoPSK said:**
> ??? Cow level? Starcraft related? Or diablo... or something else?:lolflag:

the SC cheat to unlock all levels

---

### Post by supaman2slick on 2007-10-23
hey guys, I think I have everything installed and working. One thing, I don't have the curve option. I just have flat and 3d. Am I missing something? By the way, when awn is running, the terminal window is always open? Is there a way to get rid of that?

---

### Post by nikoPSK on 2007-10-24
> **Morton's Red Stapler said:**
> the SC cheat to unlock all levels

yes I knew that... I thought you had a hidden meaning or something:lolflag: I try not to cheat in sc though:D Oh dude that curves option isn't available and terminal is running in the background. What does the terminal say? If you close the terminal does awn close too? And if the option isn't apperaing try thus again:

```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
cd awn-curves
./autogen.sh && make
sudo make install
```

---

### Post by Martin_sensei on 2007-10-24
Hello all,

I tried this as per the instructions on the first page.  All went well, no errors were reported.  However when I click on the AWN manager entry on the System > Preferences manager, nothing happens.  Not even a busy icon.

an I start AWN curves another way to catch any errors? I would love to get this working!

By the way I am using an ATI card with XGL and compiz fusion.

Cheers
Martin

---

### Post by supaman2slick on 2007-10-24
> **nikoPSK said:**
>  Oh dude that curves option isn't available and terminal is running in the background. What does the terminal say? If you close the terminal does awn close too? And if the option isn't apperaing try thus again:



Yea the terminal says some unintelligible stuff and when i close the terminal, awn dies. the only think i can do is minimize that terminal...

---

### Post by thinktyler on 2007-10-24
when i try and to install gnome-commons I get please insert gutsy gibbon install disk in CD-ROM/ - the problem is when I do my CD-ROM is located in CD-ROM1 - I have tried to update the fstab with no luck... Any ideas?

---

### Post by d3mon on 2007-10-24
> **Martin_sensei said:**
> Hello all,

I tried this as per the instructions on the first page.  All went well, no errors were reported.  However when I click on the AWN manager entry on the System > Preferences manager, nothing happens.  Not even a busy icon.

an I start AWN curves another way to catch any errors? I would love to get this working!

By the way I am using an ATI card with XGL and compiz fusion.

Cheers
Martin

Try first running AWN from Applications > Accessories > Awant Window Navigator
If it still doesn't work try to run it from yours home directory, find AWN-curves,go to src directory,and run avant-window-navigator  
(Home/$username/awn-curves/src/.awant-window-navigator)

---

### Post by stfury on 2007-10-24
my install constantly hangs after ---

bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves

it says on the right of the terminal part 1/4 

i left it for like 30 mins now response pls help

---

### Post by Blind Buzzard on 2007-10-24
AWN was working fine for me, but after installing the "curves" the way that it is walked through in the beginning of this post, and rebooting, it will not startup again.

I am on Gutsy and if I go to applications>accessories>avant windows manager nothing happens.  If I go to system>preferences>awn manager the manager does open up.

Anyone experienced this issue after installing curves and rebooting?

---

### Post by timmyw29 on 2007-10-24
I wish this had worked, but I got python header errors trying to automake... tried to install them but it won't let me because of dependency issues. I get the feeling I'd have to do *yet another* reinstall of gutsy. I've done 3 in the past week. *mopes his way back to normal awn*

Edit: I can't help myself... Going to try force version on pango, libgnome-desktop-dev etc etc until I can get them all installed. I must have the curves. There is no compromise.

---

### Post by nikoPSK on 2007-10-24
> **thinktyler said:**
> when i try and to install gnome-commons I get please insert gutsy gibbon install disk in CD-ROM/ - the problem is when I do my CD-ROM is located in CD-ROM1 - I have tried to update the fstab with no luck... Any ideas?

goto synaptic repositiries then uncheck the cd. Also for the aen-manager thing not-running is not happening to me. I'll give awn a re-install when I get home and see if it happens to me too.

---

### Post by Jeffers on 2007-10-24
When I use this command in the Terminal:
```
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
```
It gets stuck on Fetch Phase 1/4.  Anything I need to know about here?

---

### Post by nikoPSK on 2007-10-24
> **Jeffers said:**
> When I use this command in the Terminal:
```
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
```
It gets stuck on Fetch Phase 1/4.  Anything I need to know about here?

it doesn't just wait.

---

### Post by 127.0.0.1 on 2007-10-24
i edited the milk theme:

i like glassy :) 

EDIT: ack the attachment came out crapy, uploaded: [[IMG]http://img139.imageshack.us/img139/5707/screenshot1yc9.th.jpg[/IMG]](http://img139.imageshack.us/my.php?image=screenshot1yc9.jpg)

---

### Post by noefear on 2007-10-24
curves worked great. I followed your howto from top to bottom..worked like a charm.

I have milk and black theme, but where can get some others like the "glassy" and "human" theme?

thanks!

---

### Post by nikoPSK on 2007-10-24
> **noefear said:**
> curves worked great. I followed your howto from top to bottom..worked like a charm.

I have milk and black theme, but where can get some others like the "glassy" and "human" theme?

thanks!

human theme [http://www.mediafire.com/?2xxcg0lnu0p](http://www.mediafire.com/?2xxcg0lnu0p), And glassy I don't have a clue. PS you can create your own as well;) Oh and person with glassy theme. Are you using curves for it? Because it doesn't look like it. Oh and everyone. I re-installed awn and curves. But I don't get the problem...:confused:

---

### Post by nikoPSK on 2007-10-24
AHA! everyone! If you want your trash applet bigger just apply the human theme then black.... ?:)

---

### Post by 127.0.0.1 on 2007-10-24
> **nikoPSK said:**
> human theme [http://www.mediafire.com/?2xxcg0lnu0p](http://www.mediafire.com/?2xxcg0lnu0p), And glassy I don't have a clue. PS you can create your own as well;) Oh and person with glassy theme. Are you using curves for it? Because it doesn't look like it. Oh and everyone. I re-installed awn and curves. But I don't get the problem...:confused:

Me? no, i am using 3-D look. same app though :P

---

### Post by Neo4 on 2007-10-24
> **nikoPSK said:**
> I know a bunch of you have been asking about how to get AWN or avant-window-navigator to look like this:

Black Theme:
[IMG]http://www.abload.de/img/awnwhe.png[/IMG]

Milk Theme:
[IMG]http://img03.picoodle.com/img/img03/9/10/14/f_withreflectm_5c40045.png[/IMG]




Now to clarify this, this will just be a dock style. If you don't like it you can easily revert to the "Flat Bar" or "3D Look". This is in early development and it 's quite stable, This is AWN so it will require a window composter such as Beryl or Compiz.

This will not change your icons to OSX style like the first image. The screen-shot provided above has had those changes made to it. i don't care much for those icons, but meek has given me the link to the set he used: [here]("http://gnome-look.org/content/show.php/OSX?content=31618"). To change the icon of a launcher right click then change icon



I won't enclose an image of my dock because I don't know how to get a high-res screenshot like the other ones.:(


Now for the fun part!


If you have avant already installed, remove it:
```
sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
```

Install bazaar, gnome-common and M4. 
Applications/ Accessories/ Terminal

```
sudo apt-get install bzr
sudo apt-get install m4
sudo apt-get install gnome-common
``` 

Then, Install awn curves:
```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
cd awn-curves
./autogen.sh && make
sudo make install
```


make sure you have your AWN repositories:

press ALT+F2, 
type: 

gksudo "gedit /etc/apt/sources.list" 

Press Run then add the corresponding code at the bottom:

Feisty:
```
deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
```

Gutsy:
```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```


Save and close that, then resume work in the terminal,
```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
```

Then finally:
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

[Milk Theme]("http://kerlz.de/downloads/milk.tgz")
[Black Theme]("http://kerlz.de/downloads/black.tgz")

To install these themes just download 'em. No extraction required Then go to themes/ add and locate the theme which you want to install.

To remove awn-curves:

Open a terminal, cd to your awn-curves directory, and type ```
sudo make uninstall
```

Site: [http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=853&page=1&isLive=true]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=853&page=1&isLive=true")

(I had to look for this for ages then i found something on google telling me how to do this then I found the actual site a week later.):KS
Hope this can help!

can you tell me the icon theme name of the 2nd pic?

thanks :)

---

### Post by nikoPSK on 2007-10-24
hmmmm, I will be sure to find out:)

---

### Post by thespankguy on 2007-10-25
i'm extremely new to linux. i followed the steps correctly, but when i get to "cd awn-curves" it says "bash: cd: awn-curves: No such file or directory" 

am i not in the correct directory?

---

### Post by timmyw29 on 2007-10-25
Well... persistence and learning was the key with this one. Just had to force version on about 5 packages in Synaptic so that it'd let me install the dependencies etc to be able to build it. And now it works excellently.
Great guide, cheers for this.

@thespankguy
> **thespankguy said:**
> i'm extremely new to linux. i followed the steps correctly, but when i get to "cd awn-curves" it says "bash: cd: awn-curves: No such file or directory" 

am i not in the correct directory?

there's no ':' after "cd", just a space. That could be the problem. Alternatively, check that the directory is actually made after you've typed ```
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
```

---

### Post by Martin_sensei on 2007-10-25
> **d3mon said:**
> Try first running AWN from Applications > Accessories > Awant Window Navigator
If it still doesn't work try to run it from yours home directory, find AWN-curves,go to src directory,and run avant-window-navigator  
(Home/$username/awn-curves/src/.awant-window-navigator)

Thanks D3Mon I hand't actually started AWN before trying to start the manager.  All working fine now!

---

### Post by nikoPSK on 2007-10-25
> **thespankguy said:**
> i'm extremely new to linux. i followed the steps correctly, but when i get to "cd awn-curves" it says "bash: cd: awn-curves: No such file or directory" 

am i not in the correct directory?

folder should be in your home directory. And everyone: if curves fails at first, goto your awncurves>src>avant-window-navigator then click run. If you want  to you can add it to your startup by going to sessions.

---

### Post by Neo4 on 2007-10-25
and the icon theme no news?

---

### Post by nikoPSK on 2007-10-25
finding out, unfortunately that one was just on google but it uses the milk theme. I emailed the blog dude.

---

### Post by Vadi on 2007-10-25
We really need a .deb for awn-curves :)

---

### Post by nikoPSK on 2007-10-25
> **Vadi said:**
> We really need a .deb for awn-curves :)

I would make one if I knew how:) If you could show me I would do it.

---

### Post by Vadi on 2007-10-25
I don't know myself. I'm positive it's somewhere in help.ubuntu.com/community though :)

---

### Post by reacocard on 2007-10-25
> **nikoPSK said:**
> I would make one if I knew how:) If you could show me I would do it.

here's the guide I learned on: [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

note that for this you can probably borrow a lot of my AWN packaging, just adapting it as needed.

EDIT: if you make packages and they work well I can host them for you

---

### Post by matteospqr on 2007-10-25
Hello!
I installed avant and it works nicely but I just cant figure out how to add new themes.
When I try adding them in the themes menu it doesnt work. Ive tried adding the tar and also the single folder but it says it is not a valid theme.
No idea!!

What could I try?

thanks!

---

### Post by dmber on 2007-10-25
well i went against my better judgement and followed this tutorial.  before gutsy there was no uninstall involved (you'll see i posted a couple weeks ago on the first few page about how great the how to used be).  i don't know why but i just had this sinking feeling that if i followed this new how to that involved uninstalling AWN something would go wrong.

i went through with it anyway and now AWN will not start.  AWN manager does, but no dock.

what changed that we have to uninstall now?

---

### Post by nrune on 2007-10-25
Thanks very much for the howto.  Very cool dock that was missed when I upgraded to Gutsy

Mike

---

### Post by nikoPSK on 2007-10-25
uhhh, the awn-uninstall helped me. Plus you have to install curves first then awn over it.:KS

And thanks Reacocard once again. When I get a little time today or tomorrow I will give that a shot   ^^

---

### Post by Morton's Red Stapler on 2007-10-26
> **nikoPSK said:**
> uhhh, the awn-uninstall helped me. Plus you have to install curves first then awn over it.:KS

And thanks Reacocard once again. When I get a little time today or tomorrow I will give that a shot   ^^

i have notices that you also have install awn in the same folder as curves, ie: while you are still cd'ed in the curves folder run ```
sudo apt-get install avant-window-navigator-bzr
``` THIS MUST BE DONE WHILE THE TERMINAL IS STILL IN THE CURVES FOLDER!!!! i had alot of the problems that you are all listing, and did this and it worked perfectly. here is a screenshot of what my desktop looks like
[ATTACH]47929[/ATTACH]

---

### Post by Morton's Red Stapler on 2007-10-26
> **noefear said:**
> curves worked great. I followed your howto from top to bottom..worked like a charm.

I have milk and black theme, but where can get some others like the "glassy" and "human" theme?

thanks!

see my above screenshot, all i did was alter the theme that was loaded, you can make it any color, or shade you like, mine is transparent with a faint blue outline, i like transparency on my desktop

---

### Post by dmber on 2007-10-26
i got it all figured out eventually. i had done something wrong because removing AWN was a pain.  ever removing everything from Synaptic that mentioned AWN didn't remove it.  but i finally got it gone and it works now.

russ

---

### Post by hopelessone on 2007-10-27
is there a fix fot the small trash icon yet?

currently i have to resize the bar to get it going every time...

taa...

---

### Post by jba6511 on 2007-10-27
I get to the step to install awn curves and get an Abort error. I am performing this on a clean install of Gutsy. Any ideas?

[PHP]blake:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autotools-dev is already the newest version.
autotools-dev set to manual installed.
libgnome2-common is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
python-dev is already the newest version.
python-gconf is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 gconf indent libart-2.0-dev libatk1.0-dev
  libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev
  libbonobo2-dev libbonoboui2-dev libcairo2-dev libdbus-1-dev libesd0-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgail-dev libgconf-dev
  libgconf11 libgcrypt11-dev libglade2-dev libglib1.2-dev libgnome-keyring-dev
  libgnome-vfs-common libgnome-vfs0 libgnomecanvas2-dev libgnomeui-dev
  libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev libhal-dev
  libhal-storage-dev libice-dev libidl-dev libjpeg62-dev liblzo2-dev
  liboaf-dev liboaf0 libopencdk8-dev liborbit-dev liborbit0 liborbit2-dev
  libpango1.0-dev libpng12-dev libpopt-dev libselinux1-dev libsepol1-dev
  libsm-dev libstartup-notification0-dev libstdc++6-4.1-dev libtasn1-3-dev
  libwrap0-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml1 libxml2-dev
  libxrandr-dev libxrender-dev libxres-dev oaf python-gobject-dev
  python-pyorbit-dev x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-resource-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc nfs-common
  libcairo2-doc libgail-doc libgcrypt11-doc glade glade-gnome libglib2.0-doc
  gnome-vfs-extfs libgnome2-doc libgnomecanvas2-doc libgnomeui-doc gnutls-doc
  gnutls-bin libgtk2.0-doc hal-doc libpango1.0-doc imagemagick
  libstdc++6-4.1-doc
Recommended packages:
  orbit orbit2 python-gnome2-extras-dev docbook-xsl
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 gconf indent libart-2.0-dev
  libatk1.0-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev
  libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libcairo2-dev
  libdbus-1-dev libdbus-glib-1-dev libesd0-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgail-dev libgconf-dev libgconf11
  libgconf2-dev libgcrypt11-dev libglade2-dev libglib1.2-dev libglib2.0-dev
  libgnome-desktop-dev libgnome-keyring-dev libgnome-vfs-common
  libgnome-vfs-dev libgnome-vfs0 libgnome2-dev libgnomecanvas2-dev
  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev
  libgtk2.0-dev libhal-dev libhal-storage-dev libice-dev libidl-dev
  libjpeg62-dev liblzo2-dev liboaf-dev liboaf0 libopencdk8-dev liborbit-dev
  liborbit0 liborbit2-dev libpango1.0-dev libpng12-dev libpopt-dev
  libselinux1-dev libsepol1-dev libsm-dev libstartup-notification0-dev
  libstdc++6-4.1-dev libtasn1-3-dev libwnck-dev libwrap0-dev libx11-dev
  libxau-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml1
  libxml2-dev libxrandr-dev libxrender-dev libxres-dev oaf python-cairo-dev
  python-gnome2-dev python-gobject-dev python-gtk2-dev python-pyorbit-dev
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-resource-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 100 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.0MB/28.9MB of archives.
After unpacking 100MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.[/PHP]

---

### Post by nikoPSK on 2007-10-27
well, that happens to me on a wide variety of occasions.... I say give it another shot. It doesn't seem you're missing and other packages....

---

### Post by jba6511 on 2007-10-27
fixed it. I was being stupid and highlighting the first two lines together. Did them individually and everything went through.

---

### Post by Dorv on 2007-10-27
Ok, so I had this working just fine following the instructions.  However, I had to reinstall Gutsy last night after I corrupted something that I was to noobish to fix.  When I followed the instructions the exact same way, AWN works, but I don't have curves in the selection box.  I tried removing everything, and reinstalling, still to no avail.

Any ideas?

---

### Post by itsbradman on 2007-10-27
worked perfectly!  thanks!!!

---

### Post by godofwar on 2007-10-27
genius, its amazing!

---

### Post by GearedForWar on 2007-10-27
For some reason I installed it and now I cant get it to show up.  I put in the applets from the awn menu but it still won't show.

---

### Post by ronmarley1 on 2007-10-27
Thanks for the How-To.  Works like a champ!

---

### Post by nikoPSK on 2007-10-27
> **Dorv said:**
> Ok, so I had this working just fine following the instructions.  However, I had to reinstall Gutsy last night after I corrupted something that I was to noobish to fix.  When I followed the instructions the exact same way, AWN works, but I don't have curves in the selection box.  I tried removing everything, and reinstalling, still to no avail.

Any ideas?

Well, I would say not to remove it again. Just mabye delete the awn-curves folder In you home folder and then retry the instructions.

> **GearedForWar said:**
> For some reason I installed it and now I cant get it to show up.  I put in the applets from the awn menu but it still won't show.

Hmmmm, Could you try typing:
```
avant-window-navigator
``` 
In the terminal for me? Give me the output.

And everyone, Thank meek as well, hes the one who designed it;)

---

### Post by GearedForWar on 2007-10-28
> **nikoPSK said:**
> 



Hmmmm, Could you try typing:
```
avant-window-navigator
``` 
In the terminal for me? Give me the output.



Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

And when I tried running it from the terminal(compiz)  it just messed up my screen by enlarging what ever window I had open and made the enlarged window in a background with the normal one there.

---

### Post by nikoPSK on 2007-10-28
> **GearedForWar said:**
> Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

And when I tried running it from the terminal(compiz)  it just messed up my screen by enlarging what ever window I had open and made the enlarged window in a background with the normal one there.

so, you're in gutsy? Goto synaptic and  install 

**compizconfig-settings-manager **

and then goto window decoration and in the command thing type: 

**gtk-window-decorator --replace **

That should work. Are you running compiz from appearance visual effects tab?

---

### Post by Dorv on 2007-10-29
Different problems on my uninstall/reinst

Screen is composited.
APPLET : /usr/lib/awn/applets/main-menu.desktop
Segmentation fault (core dumped)
ivey@uSerenity:~/awn-curves$ 
(awn-applet-activation:19247): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:19247): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

---

### Post by nikoPSK on 2007-10-29
> **Dorv said:**
> Different problems on my uninstall/reinst

Screen is composited.
APPLET : /usr/lib/awn/applets/main-menu.desktop
Segmentation fault (core dumped)
ivey@uSerenity:~/awn-curves$ 
(awn-applet-activation:19247): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:19247): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

for reinstall just delete the awn-curves folder from you home directory and then look in 

**usr/bin** and 
**usr/share**

for items. to remove them: 

```
sudo chown -R username name of directory
```

replace username with your username and the directory with say: /usr/share

---

### Post by Dorv on 2007-10-29
I just went the really long way around, and reinstalled Gusty.  Probably Overkill, but I think I learn more about the OS trying to reinstall all of the individual pieces multiple times.  I will post later this evening to see if I can get Curves back (Funny part is that I like the 3D look better, but again, I'm just trying to learn).

---

### Post by Vadi on 2007-10-29
Has anyone had an issue with awn crashing when there's a new notification randomly? I use the flashlight effect for it. It doesn't happen always either, so it's hard to diagnose. I'm not sure if it's curves related either.

---

### Post by nikoPSK on 2007-10-29
> **Vadi said:**
> Has anyone had an issue with awn crashing when there's a new notification randomly? I use the flashlight effect for it. It doesn't happen always either, so it's hard to diagnose. I'm not sure if it's curves related either.

hmm? never had that before... Anyways I just re-installed gutsy and I have no problems with anything including awn-manager so it could either be awn (not curves;)) or your system,

---

### Post by Morton's Red Stapler on 2007-10-29
> **Vadi said:**
> Has anyone had an issue with awn crashing when there's a new notification randomly? I use the flashlight effect for it. It doesn't happen always either, so it's hard to diagnose. I'm not sure if it's curves related either.
i have had this same issue, AWN is still "bzr" meaning that it is NOT stable software, so there are bugs. all i have to do is restart AWN and alls well. if its a perfectly stable OS and software you're looking for, it doesnt exist, ALL os's have issues and bugs, so there is really nothing you can do but to deal with it. as for keeping llinux as stable as possible, AWN as in alot of other software is not going to do it, if you want a rock solid as little bugs as possible, just go with the basic main distro install and add nothing. sorry to sound so harsh, and you may know all of this, but there many many users who do not, and complain when something gos wrong, so i figured i would put this warning in here.

---

### Post by nikoPSK on 2007-10-29
thats fine:) yes bzr does mean not final yet so remember that. I have not had the issue so I don't have a clue what's happening. The reason may be that I don't use awn full time. I seem to stick to panels...

---

### Post by tasomaniac on 2007-10-30
I got this error ```
bzr: ERROR: Target directory "awn-curves" already exists.
``` when i tried to install awn-curves

---

### Post by nikoPSK on 2007-10-30
when you cd to it? or bzr download it?

---

### Post by studo77 on 2007-10-30
Just to give an error example for you.

I installed using this howto, and et seems to work, but this message is given to me in terminal (if i start it there):
** (avant-window-navigator:24461): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

I am running a 7.10 64bit distro-delivered Restricted drivers for my X1600 graphics.

Can i adjust the width of this? or does it depend on how many icons there are?

---

### Post by Morton's Red Stapler on 2007-10-30
> **studo77 said:**
> Just to give an error example for you.

I installed using this howto, and et seems to work, but this message is given to me in terminal (if i start it there):
** (avant-window-navigator:24461): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

I am running a 7.10 64bit distro-delivered Restricted drivers for my X1600 graphics.

Can i adjust the width of this? or does it depend on how many icons there are?
you need to resize the bar to get more icons on, as far as i can tell there is no way to resize the icons themselves.

---

### Post by nikoPSK on 2007-10-30
> **tasomaniac said:**
> I got this error ```
bzr: ERROR: Target directory "awn-curves" already exists.
``` when i tried to install awn-curves

well does it? Look in your home folder and delete it if there is already a directory. This is probably because an install that didn't finish or you're trying to reinstall with out removing traces of all awn, curves and related apps.

---

### Post by Espreon on 2007-11-01
Oi!

It won't even start here are my outputs:

```

spanek@spanek-laptop:~/awn-curves$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)

```

When I install the packages from the Avant bzr repos AWN works fine, but I like the curves style rather than the 3D and Flat looks.

---

### Post by jayaramk on 2007-11-01
> **dmber said:**
> this installed perfectly.  thank you very much.

two questions:

1. my icons "peek" when hidden using auto-hide.  screenshot:

[IMG]http://i240.photobucket.com/albums/ff189/maebemae/Screenshot.png[/IMG]

but they fully hide after about ten seconds or so.  i do nothing to make them fully hide, they just do it.

2. what is the "symmetry" slider for?  what exactly is it making symmetrical?


how do i decrease size of the bar on the top????

---

### Post by nikoPSK on 2007-11-01
go to preferences and tweak around. Actually I'm at school right now using windows. So when I get back I will clarify.:)

---

### Post by mistybudda on 2007-11-01
"how do i decrease size of the bar on the top????"

Right click on the bar then go to preferences and un-mark the box labelled  "expand". Took a me a while to figure that one out as well! :grin:

---

### Post by nikoPSK on 2007-11-01
thanks for solving that one!:)

---

### Post by nikoPSK on 2007-11-01
i dont see that option....

---

### Post by pcostanza on 2007-11-01
Stupid question----why do we have to uninstall AWN if we already have it installed?  Meaning, why can't we just install the new themes to AWN?  Sorry, I'm a virgin.

---

### Post by nikoPSK on 2007-11-02
well unfortunately that is the only fix so far for gutsy. I know its a bit dumb but I found that the workaround was putting awn over curves. Sorry, only way.:(

---

### Post by SomeGuyDude on 2007-11-02
I get a "size mismatch" problem. First I thought I could "dodge" it by simply going to the url of the .deb and then installing it via that thing, but then I got an update that gave me the same problem.

crew@crew-laptop:~/awn-curves$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnash-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  avant-window-navigator-bzr
The following packages will be upgraded:
  awn-core-applets-bzr
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1283kB/1586kB of archives.
After unpacking 1466kB of additional disk space will be used.
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator awn-core-applets-bzr 0.1.0-bzr155-1 [1283kB]
Fetched 1B in 0s (2B/s)                        
Failed to fetch [http://download.tuxfamily.org/syzygy42/pool/gutsy/avant-window-navigator/awn-core-applets-bzr_0.1.0-bzr155-1_i386.deb](http://download.tuxfamily.org/syzygy42/pool/gutsy/avant-window-navigator/awn-core-applets-bzr_0.1.0-bzr155-1_i386.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
crew@crew-laptop:~/awn-curves$

Now aside from having no idea how to fix this, I don't know how to go backwards. The hell is going on?

---

### Post by reacocard on 2007-11-02
> **SomeGuyDude said:**
> I get a "size mismatch" problem. First I thought I could "dodge" it by simply going to the url of the .deb and then installing it via that thing, but then I got an update that gave me the same problem.

crew@crew-laptop:~/awn-curves$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnash-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  avant-window-navigator-bzr
The following packages will be upgraded:
  awn-core-applets-bzr
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1283kB/1586kB of archives.
After unpacking 1466kB of additional disk space will be used.
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator awn-core-applets-bzr 0.1.0-bzr155-1 [1283kB]
Fetched 1B in 0s (2B/s)                        
Failed to fetch [http://download.tuxfamily.org/syzygy42/pool/gutsy/avant-window-navigator/awn-core-applets-bzr_0.1.0-bzr155-1_i386.deb](http://download.tuxfamily.org/syzygy42/pool/gutsy/avant-window-navigator/awn-core-applets-bzr_0.1.0-bzr155-1_i386.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
crew@crew-laptop:~/awn-curves$

Now aside from having no idea how to fix this, I don't know how to go backwards. The hell is going on?

ah sorry, my bad. should be fixed now, apt-get update and try again.

---

### Post by SomeGuyDude on 2007-11-02
Looks like everything installed fine.

EDIT: all's well! No idea what I did but it's fixed now. :P

---

### Post by nikoPSK on 2007-11-02
I should work on that .deb....

question though: what do I put in for the code to download?

---

### Post by Bagheera06 on 2007-11-04
Hi ... mine was working perfectly, then I updated and now I get this :

Screen is composited.
APPLET : /usr/lib/awn/applets/taskman.desktop
libawn/awn-shared.c: shmget: : Invalid argument

If I remove awn-curves it works .... any hints? Running on Gutsy 7.10

---

### Post by nikoPSK on 2007-11-04
that's odd... it appears every thing's fine.... hmmm...

well it says this for you:
```
libawn/awn-shared.c: shmget: : Invalid argument
```

Unfortunately I don't know what it means....

---

### Post by Ehtetur on 2007-11-04
> **Bagheera06 said:**
> Hi ... mine was working perfectly, then I updated and now I get this :
Screen is composited.
I'm glad I ain't the only who that got that error...

I fixed it by doing this:
from within ~/awn-curves:
> sudo make uninstall 

I noticed that libawn-bzr and python-libawn-bzr got installed when I did:
> sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr,

So I brought up synaptic, searched for and uninstalled anything related to avant or awn.

After that, I just followed nikoPSK's instructions to rm the awn stuff; install awn-curves; and install avant-window-manager and it's dependencies.

Now my AWN has the sweet curvy bar.  :twisted:

---

### Post by averagebeatboy on 2007-11-04
Infra_Red_Dude,

With his PHENOMENAL changing the Ubuntu look to a Mac-ish one in version 3.0  has made two fantastic themes that are the best I have seen yet! At this point, I would not use any others.  They are already adjusted for you as a default which is very nice, but the default can be changed if you wish.  

Big shouts out to Nico and Infra_red_guy!  I've been a little sick, so the mail has to wait.  (-:  I promise to get to it when I am feeling better.

Cheers,

Averagebeatboy

---

### Post by wford002 on 2007-11-05
So after reading this I noticed several people had the same issue as me, that after installing curves the awn manager came up but the dock itself wouldn't start, although there were no errors. I was able to fix this just by opening up synaptic, searching awn, and marked for reinstall everything that had to do with awn. after this everything worked fine.

Also, I know this isn't an awn question, but looking at the screenshots I was wondering how to horizontally shrink my panel? Under panel properties I can only adjust the panel height. Thanks.

---

### Post by nikoPSK on 2007-11-05
unfortunately not possible (yet). You can adjust symmetry though.:KS

---

### Post by reacocard on 2007-11-05
> **wford002 said:**
> So after reading this I noticed several people had the same issue as me, that after installing curves the awn manager came up but the dock itself wouldn't start, although there were no errors. I was able to fix this just by opening up synaptic, searching awn, and marked for reinstall everything that had to do with awn. after this everything worked fine.

Also, I know this isn't an awn question, but looking at the screenshots I was wondering how to horizontally shrink my panel? Under panel properties I can only adjust the panel height. Thanks.

uncheck 'expand' in the panel properties.

---

### Post by nikoPSK on 2007-11-05
> **reacocard said:**
> uncheck 'expand' in the panel properties.

I don't see that option....:(

---

### Post by reacocard on 2007-11-06
> **nikoPSK said:**
> I don't see that option....:(

gnome-panel, not awn

---

### Post by hvc123 on 2007-11-06
has any1 got an update for this the [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) does not exist i get a 404 error


ta

---

### Post by plun on 2007-11-06
> **hvc123 said:**
> has any1 got an update for this the [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) does not exist i get a 404 error
ta

This URL works

```
sudo apt-get install bzr
```

```
bzr co https://code.launchpad.net/~awn-curves-team/awn/awn-curves
```

Have Fun...:)

---

### Post by hvc123 on 2007-11-06
nice one.....

i have a small issue. im @work and we have a http_proxy 80 i dont get any errors from bzr i have internet access in my terminal yet i cannot connect..


i have entered the http_proxy and https_proxy yet no connect..

---

### Post by plun on 2007-11-06
> **hvc123 said:**
> nice one.....

i have a small issue. im @work and we have a http_proxy 80 i dont get any errors from bzr i have internet access in my terminal yet i cannot connect..
i have entered the http_proxy and https_proxy yet no connect..

OK, I am not sure about proxy issues and Bazaar

You can also try http

> plun@dunder:~$ bzr co [http://code.launchpad.net/~awn-curves-team/awn/awn-curveshttp://code.launchpad.net/%7Eawn-curves-team/awn/awn-curves/](http://code.launchpad.net/~awn-curves-team/awn/awn-curveshttp://code.launchpad.net/%7Eawn-curves-team/awn/awn-curves/)

**is redirected to** [https://code.launchpad.net/~awn-curves-team/awn/awn-curves/](https://code.launchpad.net/~awn-curves-team/awn/awn-curves/)


About Bazaar:
[http://bazaar-vcs.org/](http://bazaar-vcs.org/)

Manuals:
[http://doc.bazaar-vcs.org/latest/en/user-guide/index.html](http://doc.bazaar-vcs.org/latest/en/user-guide/index.html)

---

### Post by hvc123 on 2007-11-06
yer i get the redirect


sudo bzr co [http://code.launchpad.net/~awn-curves-team/awn/awn-curves](http://code.launchpad.net/~awn-curves-team/awn/awn-curves)
[http://code.launchpad.net/%7Eawn-curves-team/awn/awn-curves/](http://code.launchpad.net/%7Eawn-curves-team/awn/awn-curves/) is redirected to [https://code.launchpad.net/~awn-curves-team/awn/awn-curves/](https://code.launchpad.net/~awn-curves-team/awn/awn-curves/)
 but nohing happens after that..

also i tried without the sudo.

---

### Post by hvc123 on 2007-11-06
ok i got it installed now but when i select Curve on bar type it looks like this

---

### Post by plun on 2007-11-06
> **hvc123 said:**
> ok i got it installed now but when i select Curve on bar type it looks like this

Well.. you must explore AWNs manager...:)

Manu System > Preferences > Awn manager > General  >  Tab > Bar appearance

Change to curves look.  > Restart AWN

You can also find preferences and close with right click on dock ( a little tricky, corners (3D Bar) and in the end (curves))

---

### Post by hvc123 on 2007-11-06
dude as per my post i have selected Curves. it does change from flat to 3d to curves i will show you......

flat

3d

curves

---

### Post by hvc123 on 2007-11-06
any1 help ??

---

### Post by nikoPSK on 2007-11-06
sorry I have been busy... But Have you been clicking refresh between each? Sometimes my thing does not load right away so I refresh... If worse comes to worse just cklose awn. Select the bar look, then start it again.

---

### Post by yonexFactory on 2007-11-07
I got it installed and I can run it from a terminal, but the last step of the instructions gives me this:

```
nick@theNorseman:~/awn-curves$ sudo apt-get install avant-window-navigator-bzr 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package avant-window-navigator-bzr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package avant-window-navigator-bzr has no installation candidate
```

Any way to fix this?

---

### Post by hvc123 on 2007-11-07
"sorry I have been busy... But Have you been clicking refresh between each? Sometimes my thing does not load right away so I refresh... If worse comes to worse just cklose awn. Select the bar look, then start it again."


NICE 1 it now works 

i shut it down then chose curved, fired it back up and it works !!!

---

### Post by Goronok on 2007-11-07
Do you guys have Curves running on Gutsy?   I can get AWN to run by itself without any problems whatsoever.  As soon as install with Curves, i get a segmentation fault every time  i go to run AWN.   Anyone else have this problem?..  any thoughts to fix this issue?

Thanks,

---

### Post by nikoPSK on 2007-11-07
> **yonexFactory said:**
> I got it installed and I can run it from a terminal, but the last step of the instructions gives me this:

```
nick@theNorseman:~/awn-curves$ sudo apt-get install avant-window-navigator-bzr 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package avant-window-navigator-bzr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package avant-window-navigator-bzr has no installation candidate
```

Any way to fix this?


copy one line at a time.

---

### Post by yonexFactory on 2007-11-07
Copy one line of what at a time?

---

### Post by nikoPSK on 2007-11-07
```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
cd awn-curves
./autogen.sh && make
sudo make install
```

all that, do it one line at a time.

---

### Post by yonexFactory on 2007-11-07
Ah, I see. That's what I did (more than once) and it still doesn't want to work.

---

### Post by nikoPSK on 2007-11-07
quite odd, give it another go. Tell me if it says the same thing.

---

### Post by alize on 2007-11-07
anyone know why I can't select "custom" in System>Appearance>visual effects ??

I click on custom, close the window, and when I open it back up again it is still on "extra"

im using gutsy btw...

---

### Post by dmber on 2007-11-07
do you have CCSM installed?

i used Advanced Desktop Effects Settings (CCSM) and everything works (animation all the "custom stuff), but when i go to appearance/Visual Effects, Gutsy always puts itself to Normal.  even on "normal" everything works for me.

---

### Post by nikoPSK on 2007-11-07
> **dmber said:**
> do you have CCSM installed?

i used Advanced Desktop Effects Settings (CCSM) and everything works (animation all the "custom stuff), but when i go to appearance/Visual Effects, Gutsy always puts itself to Normal.  even on "normal" everything works for me.

CRAP! why do I always get beaten to it?

(thanks russ.)

---

### Post by yonexFactory on 2007-11-08
Tried it again and it said the same thing. I also tried removing the residual config from synaptic in hopes that would help, but no luck.

---

### Post by nikoPSK on 2007-11-08
> **yonexFactory said:**
> Tried it again and it said the same thing. I also tried removing the residual config from synaptic in hopes that would help, but no luck.

well, i would probably suggest holding off until I get my .deb up then.

---

### Post by yonexFactory on 2007-11-08
Alright, that works for me. Thanks for the help anyway. :)

---

### Post by de_valentin on 2007-11-08
Works for me thanks it's great. All I need now is a new more fitting wallpaper:)

---

### Post by nikoPSK on 2007-11-08
I would suggest looking here:

[www.gnome-look.org](www.gnome-look.org)
[www.compiz-theme.org](www.compiz-theme.org)

---

### Post by tdrusk on 2007-11-08
you should add 
```
sudo apt-get autoremove
```
to the uninstall section. I tried to just go backwords and uninstall what you told me to install and i accidentally removed half of gnome-desktop.

---

### Post by nikoPSK on 2007-11-08
really?

---

### Post by tdrusk on 2007-11-09
> **nikoPSK said:**
> really?

yeah. I don't know why. I was using apt-get. It just wanted to remove my whole ubuntu-desktop package.

---

### Post by kaos13 on 2007-11-09
Is there a way to move it to the top?

---

### Post by reacocard on 2007-11-09
> **kaos13 said:**
> Is there a way to move it to the top?

not yet, it is a planned feature for AWN 0.3

---

### Post by super.rad on 2007-11-09
Thanks worked perfectly. Is there going to be an option for more than one dock at once in future releases?

---

### Post by kaos13 on 2007-11-09
> **reacocard said:**
> not yet, it is a planned feature for AWN 0.3


Thanks for the fast reply

---

### Post by reacocard on 2007-11-09
> **super.rad said:**
> Thanks worked perfectly. Is there going to be an option for more than one dock at once in future releases?

again, planned for 0.3

---

### Post by Pulshion on 2007-11-09
Please help

dmitriy@linux:~$ avant-window-navigator 
Screen is composited.
APPLET : /usr/lib/awn/applets/awn-system-monitor.desktop
Segmentation fault (core dumped)
dmitriy@linux:~$ 
(awn-applet-activation:21946): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:21946): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

---

### Post by nikoPSK on 2007-11-10
so you get this:

dmitriy@linux:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/lib/awn/applets/awn-system-monitor.desktop
Segmentation fault (core dumped)
dmitriy@linux:~$ 

hmmm, well you did everything exactly? Was this your first install of awn or had you had it before then removed it? (Or had problems then removed it to try again.)

---

### Post by polyphemus on 2007-11-11
I am pretty new to linux and when I try to install the awn curves it will compile and then ask for y/n. I answer yes and then the installer aborts. 

screen:
```
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/bin/awn*
[sudo] password for polyphemus:
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/bin/avant*
polyphemus@polyphemus-desktop:~$ sudo rm -rf /usr/local/lib/awn
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/share/applications/avant*
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/share/applications/awn*
polyphemus@polyphemus-desktop:~$ sudo rm -rf /usr/local/share/avant-window-navigator
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/lib/libawn*
polyphemus@polyphemus-desktop:~$ sudo rm -rf /usr/local/include/libawn
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/lib/libawn*
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/lib/pkgconfig/awn.pc
polyphemus@polyphemus-desktop:~$ sudo rm -rf /usr/local/share/awn-core-applets
polyphemus@polyphemus-desktop:~$ sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
polyphemus@polyphemus-desktop:~$ sudo apt-get install bzr m4 gnome-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bzr is already the newest version.
m4 is already the newest version.
gnome-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
polyphemus@polyphemus-desktop:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autotools-dev is already the newest version.
autotools-dev set to manual installed.
libgnome2-common is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
python-gconf is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 gconf indent libart-2.0-dev libatk1.0-dev
  libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev
  libbonobo2-dev libbonoboui2-dev libcairo2-dev libdbus-1-dev libesd0-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgail-dev libgconf-dev
  libgconf11 libgcrypt11-dev libglade2-dev libglib1.2 libglib1.2-dev
  libgnome-keyring-dev libgnome-vfs-common libgnome-vfs0 libgnomecanvas2-dev
  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev
  libgtk1.2 libgtk1.2-common libhal-dev libhal-storage-dev libice-dev
  libidl-dev libjpeg62-dev liblzo2-dev liboaf-dev liboaf0 libopencdk8-dev
  liborbit-dev liborbit0 liborbit2-dev libpango1.0-dev libpng12-dev
  libpopt-dev libselinux1-dev libsepol1-dev libsm-dev
  libstartup-notification0-dev libstdc++6-4.1-dev libtasn1-3-dev libwrap0-dev
  libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxft-dev libxi-dev libxinerama-dev libxml1 libxml2-dev libxrandr-dev
  libxrender-dev libxres-dev oaf python-gobject-dev python-pyorbit-dev
  python2.5-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-resource-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc nfs-common
  libcairo2-doc libgail-doc libgcrypt11-doc glade glade-gnome libglib2.0-doc
  gnome-vfs-extfs libgnome2-doc libgnomecanvas2-doc libgnomeui-doc gnutls-doc
  gnutls-bin libgtk2.0-doc hal-doc libpango1.0-doc imagemagick
  libstdc++6-4.1-doc
Recommended packages:
  orbit orbit2 python-gnome2-extras-dev docbook-xsl
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 gconf indent libart-2.0-dev
  libatk1.0-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev
  libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libcairo2-dev
  libdbus-1-dev libdbus-glib-1-dev libesd0-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgail-dev libgconf-dev libgconf11
  libgconf2-dev libgcrypt11-dev libglade2-dev libglib1.2 libglib1.2-dev
  libglib2.0-dev libgnome-desktop-dev libgnome-keyring-dev libgnome-vfs-common
  libgnome-vfs-dev libgnome-vfs0 libgnome2-dev libgnomecanvas2-dev
  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev
  libgtk1.2 libgtk1.2-common libgtk2.0-dev libhal-dev libhal-storage-dev
  libice-dev libidl-dev libjpeg62-dev liblzo2-dev liboaf-dev liboaf0
  libopencdk8-dev liborbit-dev liborbit0 liborbit2-dev libpango1.0-dev
  libpng12-dev libpopt-dev libselinux1-dev libsepol1-dev libsm-dev
  libstartup-notification0-dev libstdc++6-4.1-dev libtasn1-3-dev libwnck-dev
  libwrap0-dev libx11-dev libxau-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxml1 libxml2-dev libxrandr-dev libxrender-dev libxres-dev
  oaf python-cairo-dev python-dev python-gnome2-dev python-gobject-dev
  python-gtk2-dev python-pyorbit-dev python2.5-dev x11proto-composite-dev
  x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-resource-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 105 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.0MB/31.9MB of archives.
After unpacking 109MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
polyphemus@polyphemus-desktop:~$ 

```

any help would be appreciated

---

### Post by nikoPSK on 2007-11-11
> **polyphemus said:**
> I am pretty new to linux and when I try to install the awn curves it will compile and then ask for y/n. I answer yes and then the installer aborts. 

screen:
```
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/bin/awn*
[sudo] password for polyphemus:
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/bin/avant*
polyphemus@polyphemus-desktop:~$ sudo rm -rf /usr/local/lib/awn
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/share/applications/avant*
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/share/applications/awn*
polyphemus@polyphemus-desktop:~$ sudo rm -rf /usr/local/share/avant-window-navigator
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/lib/libawn*
polyphemus@polyphemus-desktop:~$ sudo rm -rf /usr/local/include/libawn
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/lib/libawn*
polyphemus@polyphemus-desktop:~$ sudo rm -f /usr/local/lib/pkgconfig/awn.pc
polyphemus@polyphemus-desktop:~$ sudo rm -rf /usr/local/share/awn-core-applets
polyphemus@polyphemus-desktop:~$ sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
polyphemus@polyphemus-desktop:~$ sudo apt-get install bzr m4 gnome-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bzr is already the newest version.
m4 is already the newest version.
gnome-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
polyphemus@polyphemus-desktop:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autotools-dev is already the newest version.
autotools-dev set to manual installed.
libgnome2-common is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
python-gconf is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 gconf indent libart-2.0-dev libatk1.0-dev
  libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev
  libbonobo2-dev libbonoboui2-dev libcairo2-dev libdbus-1-dev libesd0-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgail-dev libgconf-dev
  libgconf11 libgcrypt11-dev libglade2-dev libglib1.2 libglib1.2-dev
  libgnome-keyring-dev libgnome-vfs-common libgnome-vfs0 libgnomecanvas2-dev
  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev
  libgtk1.2 libgtk1.2-common libhal-dev libhal-storage-dev libice-dev
  libidl-dev libjpeg62-dev liblzo2-dev liboaf-dev liboaf0 libopencdk8-dev
  liborbit-dev liborbit0 liborbit2-dev libpango1.0-dev libpng12-dev
  libpopt-dev libselinux1-dev libsepol1-dev libsm-dev
  libstartup-notification0-dev libstdc++6-4.1-dev libtasn1-3-dev libwrap0-dev
  libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxft-dev libxi-dev libxinerama-dev libxml1 libxml2-dev libxrandr-dev
  libxrender-dev libxres-dev oaf python-gobject-dev python-pyorbit-dev
  python2.5-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-resource-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc nfs-common
  libcairo2-doc libgail-doc libgcrypt11-doc glade glade-gnome libglib2.0-doc
  gnome-vfs-extfs libgnome2-doc libgnomecanvas2-doc libgnomeui-doc gnutls-doc
  gnutls-bin libgtk2.0-doc hal-doc libpango1.0-doc imagemagick
  libstdc++6-4.1-doc
Recommended packages:
  orbit orbit2 python-gnome2-extras-dev docbook-xsl
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 gconf indent libart-2.0-dev
  libatk1.0-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev
  libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libcairo2-dev
  libdbus-1-dev libdbus-glib-1-dev libesd0-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgail-dev libgconf-dev libgconf11
  libgconf2-dev libgcrypt11-dev libglade2-dev libglib1.2 libglib1.2-dev
  libglib2.0-dev libgnome-desktop-dev libgnome-keyring-dev libgnome-vfs-common
  libgnome-vfs-dev libgnome-vfs0 libgnome2-dev libgnomecanvas2-dev
  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev
  libgtk1.2 libgtk1.2-common libgtk2.0-dev libhal-dev libhal-storage-dev
  libice-dev libidl-dev libjpeg62-dev liblzo2-dev liboaf-dev liboaf0
  libopencdk8-dev liborbit-dev liborbit0 liborbit2-dev libpango1.0-dev
  libpng12-dev libpopt-dev libselinux1-dev libsepol1-dev libsm-dev
  libstartup-notification0-dev libstdc++6-4.1-dev libtasn1-3-dev libwnck-dev
  libwrap0-dev libx11-dev libxau-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxml1 libxml2-dev libxrandr-dev libxrender-dev libxres-dev
  oaf python-cairo-dev python-dev python-gnome2-dev python-gobject-dev
  python-gtk2-dev python-pyorbit-dev python2.5-dev x11proto-composite-dev
  x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-resource-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 105 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.0MB/31.9MB of archives.
After unpacking 109MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
polyphemus@polyphemus-desktop:~$ 

```

any help would be appreciated


Copy one line at a time:

```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
```

then

```
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
```

then:

```
cd awn-curves
./autogen.sh && make
sudo make install
```

---

### Post by jithu2k1 on 2007-11-11
try "Y" instead of "y"

That would solve the installation problem

---

### Post by polyphemus on 2007-11-11
Thanks Niko your solution worked :)

---

### Post by nikoPSK on 2007-11-12
So I take it it's running smoothly? Everyone: I can't seem to make a .deb since curves isn't just a patch... We will all probably have to wait 'till curves merges with awn officially which is a shame. In the meantime I'll see if there is something I can do about the .deb.:)

If we have any .deb experts here please [check this out!]("http://ubuntuforums.org/showthread.php?t=607339")

---

### Post by mega on 2007-11-14
today's updates killed awn

megadeth@megadeth-laptop:~/devel/awn-curves$ avant-window-navigator

** (avant-window-navigator:18674): WARNING **: Failed to make connection to session bus: Failed to connect to socket /tmp/dbus-nros7mWeK6: Connection refused

** (avant-window-navigator:18674): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (avant-window-navigator:18674): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:18674): WARNING **: There was an error requesting the name: There was an error requesting the name: There was an error requestin
*** glibc detected *** avant-window-navigator: double free or corruption (!prev): 0x081e2cb8 ***

---

### Post by reacocard on 2007-11-14
> **mega said:**
> today's updates killed awn

megadeth@megadeth-laptop:~/devel/awn-curves$ avant-window-navigator

** (avant-window-navigator:18674): WARNING **: Failed to make connection to session bus: Failed to connect to socket /tmp/dbus-nros7mWeK6: Connection refused

** (avant-window-navigator:18674): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (avant-window-navigator:18674): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:18674): WARNING **: There was an error requesting the name: There was an error requesting the name: There was an error requestin
*** glibc detected *** avant-window-navigator: double free or corruption (!prev): 0x081e2cb8 ***

looks like awn is having trouble finding dbus, try rebooting if you haven't already.

---

### Post by manaleak34 on 2007-11-14
I've tried most everything but I can't seem to get my bar to be curved. It has the style and reflection and all that stuff, it just doesn't curve. Any ideas?

Never mind I'm dumb and didn't see the curves look option.

---

### Post by nikoPSK on 2007-11-14
was that an edit? Hope everything fine.

---

### Post by isamu0001 on 2007-11-15
te doy las gracias desde Chile... al sur del mundo, usamos ubuntu

Thank you from Chile ... South of the world, we use ubuntu

---

### Post by ExBuM on 2007-11-18
I think I installed this fine but I'm not sure what to do to get it to start. 
I clicked awn manager in system > prefrences and the awn manager appears. How do I get the dock to appear?

---

### Post by nikoPSK on 2007-11-18
applications > accessories > avant window navigator 
 
or in the terminal type
 
```
avant-window-navigator
```

---

### Post by ExBuM on 2007-11-18
EDIT: Never mind I just messed up my uninstallation the first time :]
Thanks ^^

---

### Post by fisting_mayfield on 2007-11-19
Another Gutsy user getting the segmentation fault.

I followed the guide step by step, no problems at all until:

chloe@Gaz-nux:~$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)


AWN was working, but I can't get curves working.  Trying to get it working from within the directory isn't working for me either.

---

### Post by Dark Hornet on 2007-11-19
Great guide.....installed, and it worked with no issues---Thanks!

:guitar:

---

### Post by tafsen on 2007-11-19
awn-manager 
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:188: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 168, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 188, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue


I even tried to restart my computer.

---

### Post by wip3out on 2007-11-19
> **tafsen said:**
> awn-manager 
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:188: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 168, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 188, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue


I even tried to restart my computer.

Ditto. Is there any way of setting that "Key" or ignoring it?

---

### Post by svtfmook on 2007-11-19
awn works for me, but no curves.

gutsy 64

---

### Post by boob11 on 2007-11-19
good man >>

---

### Post by nikoPSK on 2007-11-19
> **fisting_mayfield said:**
> Another Gutsy user getting the segmentation fault.
 
I followed the guide step by step, no problems at all until:
 
chloe@Gaz-nux:~$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)
 
 
AWN was working, but I can't get curves working. Trying to get it working from within the directory isn't working for me either.
 
well, did you follow exactly? All I have to say is when that happened to me usually it would solve itself by removing awn+all traces of curves the re-installing.
 
> **tafsen said:**
> awn-manager 
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:188: DeprecationWarning: raising a string exception is deprecated
raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
File "/usr/local/bin/awn-manager", line 200, in <module>
awnmanager = AwnManager()
File "/usr/local/bin/awn-manager", line 101, in __init__
self.prefManager = awnPreferences(self.wTree)
File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 168, in __init__
self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 188, in setup_color
raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
 
Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue
 
 
I even tried to restart my computer.
 
try same as above. Sorry that's the only fix I've so far figured out.:(

---

### Post by ve1uxe on 2007-11-19
I had the very same issue with the segmentation fault.  To fix this condition, from within synaptic, I marked the following packages for re-installation: awn-core-applets-bzr, libawn-bzr, and python-libawn-bzr.  After these reapplied to my system, awn-curves works like a champ.

---

### Post by Dark Hornet on 2007-11-19
Ok...I have this installed perfectly, however, I am having a couple of odd issues:

1.  Applets that I put on the AWN bar seem to come and go randomly.

2.  Sometimes the entire bar will disappear--again randomly--causing me to restart AWN.

3.  How do I get this to start on start up.

Thanks for the guide, and I hope someone can help me.

---

### Post by nikoPSK on 2007-11-19
no clue for the first two, but goto system preferences sessions

then add 

avant-window-navigator :)

---

### Post by Dark Hornet on 2007-11-19
--that worked..thanks...now I just need to fix my other issues.

---

### Post by ericesque on 2007-11-20
AWN is gone when I bring my computer out of the screensaver.  I'll start it with a terminal and see what it says.  Anyone else experiencing this?

---

### Post by tafsen on 2007-11-20
I tried re-install it, but I still got the same error.

---

### Post by jonray74 on 2007-11-20
this guide was great. It worked for me and I now have AWN on my desktop with Black theme.

Thanks! :D

---

### Post by Dark Hornet on 2007-11-20
ericesque--I have a similar issue--when my pc wakens from sleep, my AWN still works, I just have some missing Applets.

---

### Post by nikoPSK on 2007-11-20
> **ericesque said:**
> AWN is gone when I bring my computer out of the screensaver. I'll start it with a terminal and see what it says. Anyone else experiencing this?
 
yes run it from the terminal then when your screensaver comes on tell and it dissapears gimme the output.
 
> **tafsen said:**
> I tried re-install it, but I still got the same error.
 
hmmm, could you give me the error again?:)

---

### Post by sweetfishremix on 2007-11-21
The following extra packages will be installed:
  gconf indent libgconf-dev libgconf11 libglib1.2 libglib1.2-dev
  libgnome-vfs-common libgnome-vfs0 libgtk1.2 libgtk1.2-common liboaf-dev
  liboaf0 liborbit-dev liborbit0 libstartup-notification0-dev libwrap0-dev
  libxml1 libxres-dev oaf python-pyorbit-dev x11proto-resource-dev
Suggested packages:
  nfs-common gnome-vfs-extfs
Recommended packages:
  orbit python-gnome2-extras-dev
The following NEW packages will be installed:
  gconf indent libgconf-dev libgconf11 libglib1.2 libglib1.2-dev
  libgnome-desktop-dev libgnome-vfs-common libgnome-vfs-dev libgnome-vfs0
  libgtk1.2 libgtk1.2-common liboaf-dev liboaf0 liborbit-dev liborbit0
  libstartup-notification0-dev libwnck-dev libwrap0-dev libxml1 libxres-dev
  oaf python-cairo-dev python-gnome2-dev python-pyorbit-dev
  x11proto-resource-dev
0 upgraded, 26 newly installed, 0 to remove and 0 not upgraded?.
Need to get 4191kB of archives.
After unpacking 16.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

WHy does it abort after typing in y?

---

### Post by Dark Hornet on 2007-11-21
--I had the same issue...it worked for me when I typed out the word "yes".

---

### Post by sweetfishremix on 2007-11-21
Ok Ran into a new problem

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems
vu@vu-laptop:~/awn-curves$

And everytime I update it again the same message shows up.... T___T
I'm so close to getting a dock T___T So close T____T

---

### Post by nikoPSK on 2007-11-21
> sweetfishremix 	 		**Re: HOW-TO: Awn curves**
 		The following extra packages will be installed:
  gconf indent libgconf-dev libgconf11 libglib1.2 libglib1.2-dev
  libgnome-vfs-common libgnome-vfs0 libgtk1.2 libgtk1.2-common liboaf-dev
  liboaf0 liborbit-dev liborbit0 libstartup-notification0-dev libwrap0-dev
  libxml1 libxres-dev oaf python-pyorbit-dev x11proto-resource-dev
Suggested packages:
  nfs-common gnome-vfs-extfs
Recommended packages:
  orbit python-gnome2-extras-dev
The following NEW packages will be installed:
  gconf indent libgconf-dev libgconf11 libglib1.2 libglib1.2-dev
  libgnome-desktop-dev libgnome-vfs-common libgnome-vfs-dev libgnome-vfs0
  libgtk1.2 libgtk1.2-common liboaf-dev liboaf0 liborbit-dev liborbit0
  libstartup-notification0-dev libwnck-dev libwrap0-dev libxml1 libxres-dev
  oaf python-cairo-dev python-gnome2-dev python-pyorbit-dev
  x11proto-resource-dev
0 upgraded, 26 newly installed, 0 to remove and 0 not upgraded?.
Need to get 4191kB of archives.
After unpacking 16.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

WHy does it abort after typing in y?

copy one line at a time

>  		Ok Ran into a new problem

W: GPG error: [http://download.tuxfamily.org]("http://download.tuxfamily.org/") gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems
vu@vu-laptop:~/awn-curves$

And everytime I update it again the same message shows up.... T___T
I'm so close to getting a dock T___T So close T____T

hmmm, could you try again, or will it say the same thing... brb futurama.:p

---

### Post by sweetfishremix on 2007-11-21
Ok I got it installed ;D YAY! Thank you for everyones help.
One last Question....How do I make it turn on during start up? I don't want to always have to turn it on T_T

---

### Post by nikoPSK on 2007-11-22
system > preferences > sessions

then add:

avant-window-navigator

:)What did you do to fix it?:)

---

### Post by sweetfishremix on 2007-11-22
I skiped sudo apt-get update this process and just went to the next one....LOL

---

### Post by ericesque on 2007-11-22
I had issues with AWN quiting randomly.  I tried running it from terminal--which seemed to stop the more predictable 'random' quits, but when it finally did crash, the terminal didn't give me anything!

Sorry, not much of a bug report!  I removed curves and went back to the standard AWN.  No crashes.

---

### Post by Dark Hornet on 2007-11-22
How do I add icons like Firefox, etc to my AWN bar?

---

### Post by reacocard on 2007-11-22
> **Dark Hornet said:**
> How do I add icons like Firefox, etc to my AWN bar?

drag them onto the task/launcher part of the bar, either from the applications menu or from /usr/share/applications.

---

### Post by Dark Hornet on 2007-11-22
Got it.....thanks!

---

### Post by nikoPSK on 2007-11-22
Thanks Reacocard, crap I always get beaten:lolflag:

---

### Post by reacocard on 2007-11-23
> **nikoPSK said:**
> Thanks Reacocard, crap I always get beaten:lolflag:

I know how that goes, it happens all the time on my guides. I don't mind at all really, it means less work for me and occasionally I learn something new as well. It also makes those asking questions happier as they get an answer faster, as well as those answering, since they get to help contribute back to the community. Everyone wins!

---

### Post by nikef on 2007-11-23
Hi all,i am using gutsy gibbon 7.10

after many hours of trying to make this work i got a result :)

i have got the dock working,and i am using the black theme
does any1 know how i can stop the the dock from dropping below the bar at the bottom ,i have added  a pick of my desktop

thanks,for any help

---

### Post by bigern75 on 2007-11-23
Works perfect the first time every time. This project has come along way in the oast few months. Keep up the good work!!:guitar:

---

### Post by Dark Hornet on 2007-11-23
--Well, after playing around with MANY different options, I think I finally have my desktop, and screen saver like I want it...although I may change it next week...lol.  Thanks for all the help everyone.  Feel free to check out a couple of screenshots I have attached.  The first one is just my basic desktop, and the second is my screensaver (the plugin for Compiz).

:guitar:

---

### Post by nikoPSK on 2007-11-23
> **nikef said:**
> Hi all,i am using gutsy gibbon 7.10
 
after many hours of trying to make this work i got a result :)
 
i have got the dock working,and i am using the black theme
does any1 know how i can stop the the dock from dropping below the bar at the bottom ,i have added a pick of my desktop
 
thanks,for any help
 
nope, you just have top delete or move the bar or add parts of the bottom bar to the top one;)
 
> **Dark Hornet said:**
> --Well, after playing around with MANY different options, I think I finally have my desktop, and screen saver like I want it...although I may change it next week...lol. Thanks for all the help everyone. Feel free to check out a couple of screenshots I have attached. The first one is just my basic desktop, and the second is my screensaver (the plugin for Compiz).
 
:guitar:
 
I like it! Could you gimme your wallpaper?
 
And all that have beensaying nice work, thanks to meek as well! :D

---

### Post by Dark Hornet on 2007-11-23
nikoPSK--I thought I got the background from [www.gnome-look.org](www.gnome-look.org), but I can't seem to find it.  I will upload it tonight when i get home...

---

### Post by nikoPSK on 2007-11-23
Okay, thanks! Hope everything worked without a hitch!

---

### Post by nikef on 2007-11-23
[QUOTE=nikoPSK;3824954]nope, you just have top delete or move the bar or add parts of the bottom bar to the top one;)
 

 
thanks,i managed to auto hide the bar,thanks for all the hard work you have put into the awn curves :)

---

### Post by dbbolton on 2007-11-24
Anyone know what's causing these white lines? 

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/awnlines.png[/IMG]

Edit: I had to add the trash applet, then remove it. (I guess I still some old config files that were screwing with it.)

---

### Post by Dark Hornet on 2007-11-24
nikoPSK--Here is a link so you can download my background Image...Have fun!

[http://themesandbackgrounds.googlepages.com/backgrounds](http://themesandbackgrounds.googlepages.com/backgrounds)

It would seem that this is a digitalblasphemy Image.---Just wanna give credit where credit is due.

---

### Post by nikoPSK on 2007-11-24
> **dbbolton said:**
> Anyone know what's causing these white lines? 

Edit: I had to add the trash applet, then remove it. (I guess I still some old config files that were screwing with it.)

applets failing to load. Just remove them and add them again, if they still don't just remove them.

---

### Post by nikoPSK on 2007-11-24
> **Dark Hornet said:**
> nikoPSK--Here is a link so you can download my background Image...Have fun!

[http://themesandbackgrounds.googlepages.com/backgrounds](http://themesandbackgrounds.googlepages.com/backgrounds)

It would seem that this is a digitalblasphemy Image.---Just wanna give credit where credit is due.

thanks alot! (who likes the new look for stacks applet?:D)

---

### Post by Dark Hornet on 2007-11-24
Checking them out now...

---

### Post by nikoPSK on 2007-11-24
you gotta right click it then go to preferences (the stacks applet) then choose use experimental gui.

---

### Post by Dark Hornet on 2007-11-24
looks cool...still trying to get the hang of using it though.

**edit**--this is sweet, I just saw a youtube video on it.  Can you add application launchers to it, or is it just for files/folders?

---

### Post by nikoPSK on 2007-11-24
app launchers too. I do seem to prefer the leopard version though. I like how when you click they glide up and once one has started you can see the one underneath. Also in grid view (in leopard) you can see the files moving to their spaces.

---

### Post by Dark Hornet on 2007-11-24
--yeah, i like the leopard version better...no worries, i will just drag the apps i want to launch to the AWN bar....this is great!!!  :guitar:

---

### Post by nikoPSK on 2007-11-24
lol, yes, but I am a leopard user but i seem to prefer linux.

---

### Post by dummyhead3 on 2007-11-24
WOHOO!! after having about every problem listed here, got it working, thank you!!!

---

### Post by nikoPSK on 2007-11-24
I hope it wasn't too bad for you.

---

### Post by nikef on 2007-11-25
Any1 have any ideas why my dock disappears  after a couple hours  or so,Edit,i know how to get it back 

thanks  :)

Trish

---

### Post by nikoPSK on 2007-11-25
no idea why it would dissapear, how do make it come back? Or just run it from the terminal,

(type this in the termainal)

```
avant-window-navigator
```

then when It disappears give me the terminal output.

---

### Post by ronacc on 2007-11-25
I'm running hardy and 64bit so that may be part of the problem. syzygy42's gutsy deb works but does not have curves , so I tried compiling ,first removed completly with synaptic then also as per the first post. autogen ran ok but I had to make from a root terminal because it would error from sudo ??? then made install as sudo . starting it from terminal as user segfaults . starting it from terminal as sudo gives this.

/apps/avant-window-navigator/title/shadow_color unset, setting now
/apps/avant-window-navigator/title/background unset, setting now
/apps/avant-window-navigator/title/font_face unset, setting now
Screen is composited.
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_shared_mem_create
ron@ron-desktop:~$ 

BTW  I agree with your choice of authors !

---

### Post by nikoPSK on 2007-11-25
sorry my rm instructions are a bit unclear. Mabye you didn't completely remove awn/ curves? Try:

sudo chown -R (your username without brackets) (directory without brackets)

in usr/lib
usr/ share
usr/ bin

and any other places you think awn would be. Also remove your awn-curves folder from your home folder. the only error I see is this one:

avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_shared_mem_create

so that means the awn shared memory is undefined. I have no clue what to do with that but try removing *completely* and trying again.

---

### Post by ronacc on 2007-11-25
I'll try again , I thought I had removed everything , I did the synaptic>remove completly first because I had installed the .deb with synaptic then I followed the instructions in the first post of this thread. this time I'll also at the end do a search on /usr for awn and avant and remove anything that shows up.

---

### Post by rune0077 on 2007-11-25
> **nikoPSK said:**
> who likes the new look for stacks applet?

They look pretty neat. Could you tell me where to download them and how to install them (if I already have AVN installed, which I do)? Thanks eversomuch.

---

### Post by nikoPSK on 2007-11-25
just update your avant-window-navigator-bzr. It should be there. Then add the applet, right click it and choose use experimental gui. 

@ronacc, if you put it in with the deb still remove it like I told you. Trust me, when I tried removing it with synaptic once it still launched.... also I forgot to mention do this

```
sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
```

now this won't kill your home directory or ubuntu system. I think the don't follow anything with rm rf in it in the signatures is a bit dumb. It should be don't follow any commands you don't know or better yet look them up or ask here about them first.

---

### Post by ronacc on 2007-11-25
I went through and thoroughly nuked everything refering to awn or avant in /usr (all sub dirs) and /home and /root it did seem to compile cleaner this time but now segfaults both as user and sudo. it may have to do with the fact that hardy isn't even to alpha yet and my install is part hardy and part residual gutsy , I'm going to back off and try again when hardy is all there . thanks for the help.

---

### Post by nikoPSK on 2007-11-25
Welcome, I hope everythings fine, You're in hardy? :confused:

---

### Post by ronacc on 2007-11-25
yeah I'm a glutton for punishment as soon as something goes release I do a clean install change the repos to the developement version and off to the races again even before the put out the first alpha cd.

---

### Post by nikoPSK on 2007-11-26
I'm like that too, but never seen a hardy cd up for grabs, where'd you get it?

(lol, off topic...)

---

### Post by CosmicFlux on 2007-11-26
Hi,

I've followed all instructions but the docking bar isn't displayed. All the new options come up in the AWN manager, there just isn't a bar displayed on my desktop...

---

### Post by ronacc on 2007-11-26
the cd wont be out for a few days yet but the repos opened about a month ago .

[https://wiki.ubuntu.com/QATeam/HardySchedule](https://wiki.ubuntu.com/QATeam/HardySchedule)

thats why I said this system was half gutsy and half hardy.They open the repos for the new version a couple of days after the curren one goes release but the first alpha cd don't come out until about a month later to give them time to get everything updated .

---

### Post by JunSeok Kang on 2007-11-26
this really helped. (Of course, the guide itself rocks too!)
> **ve1uxe said:**
> I had the very same issue with the segmentation fault.  To fix this condition, from within synaptic, I marked the following packages for re-installation: awn-core-applets-bzr, libawn-bzr, and python-libawn-bzr.  After these reapplied to my system, awn-curves works like a champ.

---

### Post by rune0077 on 2007-11-26
> **nikoPSK said:**
> just update your avant-window-navigator-bzr. It should be there. Then add the applet, right click it and choose use experimental gui. 


Nah, I updated the darn thing but nothing changed. I think it needs a seperate package or something. Nevermind, I can live without it (hopefully).

---

### Post by nikoPSK on 2007-11-26
> **CosmicFlux said:**
> Hi,
 
I've followed all instructions but the docking bar isn't displayed. All the new options come up in the AWN manager, there just isn't a bar displayed on my desktop...
 
type:
 
```
avant-wondow-navigator
```
 
in terminal, give me the output. Also type this:
 
```
awn-manager
```
 
most likely a seg fault:(

---

### Post by nikef on 2007-11-26
> **nikoPSK said:**
> no idea why it would dissapear, how do make it come back? Or just run it from the terminal,

(type this in the termainal)

```
avant-window-navigator
```

then when It disappears give me the terminal output.

thank you,my pc has been running all day,and the dock has not disappeared ,only when i closed it my self  :)

i think it just needed to settle down


thanks again   :)

---

### Post by craigyjack on 2007-11-26
Ah dude, thanks so much for this tutorial! Curves looks really sweet. you have completed my dock experience fully. I was using the 3d look for AWN, but the curves is beastly awesome now, but especially with that black theme which just completed the package. especially the white dots under the open apps (the default way for awn sucked).

I have now eradicated all panels in my desktop (no gnome-panel running anymore :) and everything is replaced with AWN, and it looks and acts amazing for my desktop.

thanks for the final step in completing my panel-to-dock desktop transition.

---

### Post by nikoPSK on 2007-11-26
welcome! I haven'y switched completely to awn but am making the transistion.

---

### Post by peterson2k4 on 2007-11-26
for one reason or another I am not given the "curves look" option.  I have only "3d look" and "flat bar" to choose from

---

### Post by CosmicFlux on 2007-11-27
Thanx! Works now!

Does anyone know how to get it to load at start-up?

---

### Post by mozetti on 2007-11-27
> **CosmicFlux said:**
> Thanx! Works now!

Does anyone know how to get it to load at start-up?

Just add it to your startup programs in the Preferences-Sessions menu:

avant-window-navigator

Mine took a little while to start up last time I rebooted my computer, but I don't do that often so I didn't bother to find out why. In case you start it manually, and then it starts up on it's own, just kill one of the instances from the terminal (or you could probably close it with the mouse, too).

---

### Post by shavenlunatic on 2007-11-27
ooohh.. black is pretty... cheers for this

---

### Post by CosmicFlux on 2007-11-27
I tired to add it but I dont know the path. I typed in the name but it said text contained whitespace...

---

### Post by nikoPSK on 2007-11-27
goto system > prefernences > sessions

add

avant-window-navigator 

and type description

awn. I'll add this to the top of my guide so this question doesn't show up anymore.

---

### Post by Miroku on 2007-11-27
hello

thanks for this helpful thread, kiba's physics thing was getting annoying with all of its options, lol.

i had a question, how can i turn off the text that comes on top of the icon when i hover over it?

TIA.

also, is there a way to change the icons of the applets? theres gotta be a way, but its just not clickin for me tonight. lol. thx. =]

---

### Post by nikoPSK on 2007-11-27
right click the applet then change icon. I thought there was a way to disable text but can't seem to find it.

---

### Post by Miroku on 2007-11-27
> **nikoPSK said:**
> right click the applet then change icon. I thought there was a way to disable text but can't seem to find it.

right clicking the applets (such as the trash can, show desktop applet) doesnt give me that option. the change icon option only comes up when i right click running aplications.

when i right click the 'show desktop applet', there is no options at all.

---

### Post by octesian on 2007-11-28
Works spectacularly!  Thanks!

---

### Post by Miroku on 2007-11-28
another question, why is it that sometimes the dock just disappears? its nice and all but is there any way to make it permanently stay? it doesnt give me an error or anything. it just disappears and then i have to run it again. thanks.

---

### Post by rune0077 on 2007-11-28
> **Miroku said:**
> another question, why is it that sometimes the dock just disappears?

It's a bug. Nobody claimed AWN was completely stable, but most of the time it is. However, there's still certain things that makes it crash.

---

### Post by mozetti on 2007-11-28
> **Miroku said:**
> another question, why is it that sometimes the dock just disappears? its nice and all but is there any way to make it permanently stay? it doesnt give me an error or anything. it just disappears and then i have to run it again. thanks.

Yeah, that's because it's crashing. The way to make it stop doing that is to fix whatever bug(s) are making it crash.:D

---

### Post by nikoPSK on 2007-11-28
The community has been working hard on awn. All of this should be fixed by the next major awn-release.

---

### Post by Miroku on 2007-11-28
> **mozetti said:**
> Yeah, that's because it's crashing. The way to make it stop doing that is to fix whatever bug(s) are making it crash.:D

hehe..ill get right on it!

---

### Post by nikoPSK on 2007-11-28
funny, I've never had awn crash....

---

### Post by ronacc on 2007-11-28
after a bunch of updates came down in preperation for the hardy alpha1 cd due tommorrow I decided to try again . autogen and make ran ok but I got a couple of wierd errors right at the end of install about relinking awn.la  ,  I went ahead and finished up all the steps and awn started with no segfault  but also no curves . I went back to my awn-curves build dir and ran sudo make install again and this time got no errors and curves was there when I restarted awn . I can't get the seperator between launchers and tasks to show up but otherwise it seems to work :)

---

### Post by nikoPSK on 2007-11-28
actually no separators work but glad you got it going.

---

### Post by craigyjack on 2007-11-28
> **nikoPSK said:**
> funny, I've never had awn crash....

When I had AWN with the 3D look before I installed awn-curves, AWN basically never crashed, very stable. But I have installed awn-curves and use the curves with black theme now, it crashes on occasion. But I also have several other applets on my dock now, so its either applets or awn-curves that are crashing it. 

But yeah, not complaining, and I'm sure that when the next release of AWN and awn-curves comes out it will work very nice!

Also, is awn-curves going to integrated in the AWN project, or is it staying independent?, because it would be nice to have a awn-curves repo, or it be included in the AWN repos for gutsy sometime in the future.

AWN is still buggy, stable but buggy, and I'm looking forward to releases in the future. :)

Oh, also, I've noticed lots of people voting the black theme as the best, and for anyone that likes dark themes, or just dark icons and not theme, this is the best icon theme I have ever found came in my opinion. It is a amazing dark icon theme, its awesome because of both the icons plain and because they are dark themed. check it out if you like that kind of theme > [http://dbgthekafu.deviantart.com/art/black-white-icon-thema-70416981](http://dbgthekafu.deviantart.com/art/black-white-icon-thema-70416981)

thanks,
craig

---

### Post by nikoPSK on 2007-11-28
Love the theme, yes waiting desperately for next major awn release!

---

### Post by Dark Hornet on 2007-11-29
Yup, I have the Black and White Theme installed on my box now...and loving it!  :guitar:

---

### Post by Belyel on 2007-11-29
I've attached a sweet purple theme, you can see it below (click for biggen)
[URL="http://web.engr.oregonstate.edu/~sniderst/desktop.png"]
[IMG]http://web.engr.oregonstate.edu/~sniderst/desktop.thumb.png[/IMG][/URL]

---

### Post by nikoPSK on 2007-11-29
thanks, ill submit a screenshot with it and give you credit.

---

### Post by rundee_f on 2007-11-30
Oh my!

Beautiful!! But i experienced sometimes it shuts down suddenly and also shuts my CompizFusion Effects.. what happened?

overall, excellent! thanx niko! :)

---

### Post by nikoPSK on 2007-11-30
welcome, welcome! I think it's just still buggy. awn-curves adds to that bugginess, but It's not that bad.

---

### Post by rundee_f on 2007-11-30
yups.. that makes my friends a lot more jealous with my Ubuntu+desktop.. :lolflag:

---

### Post by nikoPSK on 2007-11-30
lol, I've never had awn-crash.:popcorn:

---

### Post by cerupcat on 2007-11-30
I've made it to the last step, but I can't get it to install. I'm getting this error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr142-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages

```

I've only had ubuntu installed for a day, so I'm still new to this. Any help would be appreciated.

---

### Post by nikoPSK on 2007-11-30
are you using hardy alpha?

---

### Post by cerupcat on 2007-11-30
Not that I know of. I'm not really sure what that is even. =\

---

### Post by markp1989 on 2007-11-30
thanks for the how to, looks exactly how i wanted it to.

i prefered the black theme, but the milk theme goes better with the current theme.

---

### Post by rundee_f on 2007-11-30
> **cerupcat said:**
> I've made it to the last step, but I can't get it to install. I'm getting this error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr142-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages

```

I've only had ubuntu installed for a day, so I'm still new to this. Any help would be appreciated.

probably u should try to re-install (or re-download perhaps better) the dependancies needed (the error ones)..

---

### Post by nikoPSK on 2007-11-30
> **markp1989 said:**
> thanks for the how to, looks exactly how i wanted it to.

i prefered the black theme, but the milk theme goes better with the current theme.

I love!

> **rundee_f said:**
> probably u should try to re-install (or re-download perhaps better) the dependancies needed (the error ones)..

Just redo the tut, remove awn and try again.

---

### Post by daimengrui on 2007-12-01
mine worked on the first try.  however i observed the following bugs

1. when creating launcher from awn manager the item gets doubled and it does not appear on the panel.
2. Sometimes the icons freezes and some applet isnt working correctly
3. Launchers created by dragging them from the desktop is not permanently stored.  when you exit awn and start again the launchers disappears.  hope this gets fixed as well.

anyway thanks for the great app, i hope a purely binary install be available soon! 

awn curves is great, it should be part of the standard package for awn.

---

### Post by nikoPSK on 2007-12-01
most likely your awn is a bit screwed up, I never get any of those bugs. You could try reporting them.

---

### Post by daimengrui on 2007-12-02
hmm i dont think so.. i did the step by step instructions to the dot.

ok... have been using it for more than 2 days now.  and the weird thing is that it started to stabilize already...

i have not got the random bugs that occured before.  I can now drag launchers from the desktop and place them to awn.. and rebooted and theyre always there.

how do we update it with the bugfixes made by the recent release of awn sources?

here is my [screen]("http://picasaweb.google.com/oj.delosreyes/Deskshots/photo#5139326052365908978")

[IMG]http://lh5.google.com/oj.delosreyes/R1KN0LguO_I/AAAAAAAABBM/cBO0ZobnP0c/s144/Screenshot.png[/IMG]

---

### Post by stomponthis on 2007-12-02
Great thread NIKO,

Encountered a problem....
The last code to execute 
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```
Gave me the following output
```
Package avant-window-navigator-bzr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  avant-window-navigator
E: Package avant-window-navigator-bzr has no installation candidate

```

I changed it, to get it to work 

```
sudo apt-get install avant-window-navigator awn-core-applets
```

It worked but I have no curves!  That command only has to do with installing AWN eh? And not the curves itself?  Hmmmm, troubleshooting!
Great guide tho. Big ups

---

### Post by hopelessone on 2007-12-02
hi,

i get this when trying to uninstall it:

ubuntu@ubuntu-desktop:~$ sudo rm -f /usr/local/bin/awn*
sudo: must be setuid root
ubuntu@ubuntu-desktop:~$ 

what do i do?

thanks

---

### Post by nikoPSK on 2007-12-02
> **daimengrui said:**
> hmm i dont think so.. i did the step by step instructions to the dot.

ok... have been using it for more than 2 days now.  and the weird thing is that it started to stabilize already...

i have not got the random bugs that occured before.  I can now drag launchers from the desktop and place them to awn.. and rebooted and theyre always there.

how do we update it with the bugfixes made by the recent release of awn sources?

here is my [screen]("http://picasaweb.google.com/oj.delosreyes/Deskshots/photo#5139326052365908978")

[IMG]http://lh5.google.com/oj.delosreyes/R1KN0LguO_I/AAAAAAAABBM/cBO0ZobnP0c/s144/Screenshot.png[/IMG]

it's working then, good. Awn will update automatically because you put in the stuff in the sources file.

> **stomponthis said:**
> Great thread NIKO,

Encountered a problem....
The last code to execute 
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```Gave me the following output
```
Package avant-window-navigator-bzr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  avant-window-navigator
E: Package avant-window-navigator-bzr has no installation candidate

```I changed it, to get it to work 

```
sudo apt-get install avant-window-navigator awn-core-applets
```It worked but I have no curves!  That command only has to do with installing AWN eh? And not the curves itself?  Hmmmm, troubleshooting!
Great guide tho. Big ups

bzr, maybe the server was down? I get that with packages sometimes and I try like a day or an hour later and it goes. Hope all goes well and enjoy!

> **hopelessone said:**
> hi,

i get this when trying to uninstall it:

ubuntu@ubuntu-desktop:~$ sudo rm -f /usr/local/bin/awn*
sudo: must be setuid root
ubuntu@ubuntu-desktop:~$ 

what do i do?

thanks

are you logged in as root?

---

### Post by Jabb3r on 2007-12-03
Hi the program seems to be working, thanks for the guide, but it doesn't appear on the desktop I want it too. I'm running compiz fusion and that aint doing the cude thing, it's just flipping the screens, Thanks

Edit: Got compiz fusion mostly working, just a slight issue, but still not sure how to set which screen Awn uses,

Gutsy Gibbon
Nviidia 8800GT
NVIDIA-Linux-x86_64-169.04 drivers

Thanks

---

### Post by daimengrui on 2007-12-03
so awn-curves will be automatically updated as well via update manager? sorry new to ubuntu here.

should i delete the source "awn-curves" dir from my home dir?

attached is a screenshot of the update manager...hmmm how come the updates for awn is grayed?

---

### Post by kyds3k on 2007-12-03
i've been trying all morning to get this to work but i keep getting:

E: Couldn't find package avant-window-navigator

i made sure these lines were at the end of my sources file:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator

no go!  help!

---

### Post by nikoPSK on 2007-12-03
> **daimengrui said:**
> so awn-curves will be automatically updated as well via update manager? sorry new to ubuntu here.
 
should i delete the source "awn-curves" dir from my home dir?
 
attached is a screenshot of the update manager...hmmm how come the updates for awn is grayed?
 
just update as you normally would.
 
> **Jabb3r said:**
> Hi the program seems to be working, thanks for the guide, but it doesn't appear on the desktop I want it too. I'm running compiz fusion and that aint doing the cude thing, it's just flipping the screens, Thanks
 
Edit: Got compiz fusion mostly working, just a slight issue, but still not sure how to set which screen Awn uses,
 
Gutsy Gibbon
Nviidia 8800GT
NVIDIA-Linux-x86_64-169.04 drivers
 
Thanks
 
enable desktop cube, cube rotate and go to general options, desktop size set the top to 4. Awn uses all desktops.
 
> **kyds3k said:**
> i've been trying all morning to get this to work but i keep getting:
 
E: Couldn't find package avant-window-navigator
 
i made sure these lines were at the end of my sources file:
 
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
 
no go! help!
 
Couldn't find the package avant-wondow-navigator? or the bzr...:confused:

---

### Post by reacocard on 2007-12-03
> **kyds3k said:**
> i've been trying all morning to get this to work but i keep getting:

E: Couldn't find package avant-window-navigator

i made sure these lines were at the end of my sources file:

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator

no go!  help!

the package name is avant-window-navigator-bzr, not avant-window-navigator.

EDIT: oh, feisty? the feisty repo is no longer maintained, sorry. upgrade to gutsy or compile AWN from source

---

### Post by daimengrui on 2007-12-03
tried to update but the tick box for awn is grayed/disabled in the updated manager window.  any idea why this is so?

---

### Post by jouka on 2007-12-03
> **cerupcat said:**
> I've made it to the last step, but I can't get it to install. I'm getting this error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr142-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages

```

I've only had ubuntu installed for a day, so I'm still new to this. Any help would be appreciated.

add these to sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

and do 'sudo apt-get update' and you're ready to go.

---

### Post by onion221 on 2007-12-03
any1 know how to get the awn stacks  applet to fan out like in Leopard?

---

### Post by reacocard on 2007-12-03
> **onion221 said:**
> any1 know how to get the awn stacks  applet to fan out like in Leopard?

right-click and select 'use experimental gui'

---

### Post by nikoPSK on 2007-12-03
> **jouka said:**
> add these to sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

and do 'sudo apt-get update' and you're ready to go.

He quite possibly have done that? did you follow instructions correctly whatever your name is?

> **onion221 said:**
> any1 know how to get the awn stacks  applet to fan out like in Leopard?

yes, as reacocard mentioned. Thanks R :D

---

### Post by onion221 on 2007-12-03
> **reacocard said:**
> right-click and select 'use experimental gui'
Yea I've tried that option, when I click it the box does not shade in and the stack doesn't work any more. Any ideas?

---

### Post by hopelessone on 2007-12-04
hi,

i'm trying to uninstall it i did su to root and it's still in the menu's and I can't install the updates from ubuntu or use Synaptic Package Manager...

what can i do to fix this?

thanks..

---

### Post by jouka on 2007-12-04
> **nikoPSK said:**
> He quite possibly have done that? 

Most likely he hasn't done that. At least that fixed the similar problem for me so it's worth of trying.

---

### Post by nikoPSK on 2007-12-04
> **onion221 said:**
> Yea I've tried that option, when I click it the box does not shade in and the stack doesn't work any more. Any ideas?

check the stacks applet that looks like a drawer. then what reacocard said. I have no clue why The stack isn't working anymore, you might want to bring that up on the awn forums.

> **hopelessone said:**
> hi,

i'm trying to uninstall it i did su to root and it's still in the menu's and I can't install the updates from ubuntu or use Synaptic Package Manager...

what can i do to fix this?

thanks..

follow the uninstall a little more down in my first post. (and ubununtu is designed for sudo but whaever:p....
> **jouka said:**
> Most likely he hasn't done that. At least that fixed the similar problem for me so it's worth of trying.

okay, but If you follow the guide correctly That appears... :p

---

### Post by rune0077 on 2007-12-04
> **onion221 said:**
> Yea I've tried that option, when I click it the box does not shade in and the stack doesn't work any more. Any ideas?

It's a bad Python script in the applet. You need to download the fixed script from [http://www.mediafire.com/?5zblavmixhc](http://www.mediafire.com/?5zblavmixhc), then use it to replace the one already in the stacks applet, then make and make install. That fixed it for me.

---

### Post by noremac on 2007-12-04
Really enjoy Awn Curves. Works well and looks great. I too am experiencing the problem where the program just disappears, but will wait for the newest update to see what happens. 

Thanks!
-Cameron

---

### Post by onion221 on 2007-12-04
Thanks dude, how do I install the .py file? Im new to linux learning the ropes.


EDit: nvm I think I know how to do it I just replace the .py in the awn-extras/awn-applets/awn-extras-applets/src/stacks I read it on the awn forum. Thanks.

---

### Post by rune0077 on 2007-12-04
> **onion221 said:**
> Thanks dude, how do I install the .py file? Im new to linux learning the ropes.


EDit: nvm I think I know how to do it I just replace the .py in the awn-extras/awn-applets/awn-extras-applets/src/stacks I read it on the awn forum. Thanks.

After replacing it, you need to install it from the terminal. Make sure you're in the directory where you just replaced the script, then type "make" and then "sudo make install".

---

### Post by Escipion on 2007-12-04
Great I got it runing on the first try but I don't know why the isn't any theme to select... any help folks???

---

### Post by onion221 on 2007-12-04
Wait, I'm supposed to put it in the folder and then reinstall awn-extras? Sounds complicated..Grr

---

### Post by onion221 on 2007-12-04
> **rune0077 said:**
> After replacing it, you need to install it from the terminal. Make sure you're in the directory where you just replaced the script, then type "make" and then "sudo make install".

I'm in

 "usr/lib/awn/applets/stacks"

So I type "make" "sudo make install usr/lib/awn/applets/stacks/stacks_applet.py"

Do I put the /stacks_applet.py at the end?

---

### Post by nikoPSK on 2007-12-04
> **noremac said:**
> Really enjoy Awn Curves. Works well and looks great. I too am experiencing the problem where the program just disappears, but will wait for the newest update to see what happens. 
 
Thanks!
-Cameron
 
dissapearing is likely awn (could be curves) only had it happen to me twice...
 
> **Escipion said:**
> Great I got it runing on the first try but I don't know why the isn't any theme to select... any help folks???
 
Download the thame in the second post of this thread and select your theme. Apply and refresh.

---

### Post by rune0077 on 2007-12-04
> **onion221 said:**
> I'm in

 "usr/lib/awn/applets/stacks"

So I type "make" "sudo make install usr/lib/awn/applets/stacks/stacks_applet.py"

Do I put the /stacks_applet.py at the end?

After typing "make" just type "sudo make install", nothing else.

---

### Post by onion221 on 2007-12-04
YEEEES!! Thanks Man! haha I love linux now. I was cursing the very concept of linux a minute ago because I thought I messed up but I didnt. I couldn't access the folder to actually put the .py in it so I had to change the permissions first.  I had to type this ```
sudo chown -R username:username /usr/lib/awn/applets
``` so if any has that problem just type that in the terminal if its the same directory.

---

### Post by nikoPSK on 2007-12-04
glad it works for you.

---

### Post by YoDaddeh on 2007-12-04
Thank you! It works wonderfully! :KS

---

### Post by nikoPSK on 2007-12-04
great! At least you didn't have any problems. :popcorn:

---

### Post by YoDaddeh on 2007-12-04
> **nikoPSK said:**
> great! At least you didn't have any problems. :popcorn:

I did at first but I figured it out quickly enough :)

Thanks again for the great How To.

---

### Post by Dropknee on 2007-12-04
I try to reinstall the AWN and use the removal step so I can do all again but now I cant use sudo, I got this

sudo: must be setuid root

I guess the problem is because of the chown command

Any help?

---

### Post by nikoPSK on 2007-12-04
not because of ch own. I would think you are root.... restart?

---

### Post by Dropknee on 2007-12-04
Ok I solve my problem with this:

[QUOTE=BLTicklemonster;1467656]I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

--------------------------------------------------------------

I got this from [here]("http://ubuntuforums.org/showthread.php?t=219767") and this resolve my problem

---

### Post by hopelessone on 2007-12-05
hi,

I think i made a mistake....you wrote:

[COLOR="Green"]sudo chown -R yourname directory

Replace yourname with your user name and directory with say usr/share

Look in these three places:

usr/lib
usr/share
usr/bin[/COLOR]

i did:
[COLOR="Red"]sudo chown -R James /usr/lib
sudo chown -R James /usr/share
sudo chown -R James /usr/bin[/COLOR]

is that right? if not how can i change it back? as i can't use Synaptic and get Ubuntu updates anymore !! Arrrrr...heehee

thanks...

---

### Post by jken146 on 2007-12-05
> To remove awn-curves:

Delete your awn-curves folder from your home folder. Now use this command:

Code:
[B]
sudo chown -R yourname directory[/B]

Replace yourname with your user name and directory with say usr/share

Look in these three places:

usr/lib
usr/share
usr/bin

for traces of awn and remove them. Then to run another check run this:
Code:

sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/



Why is there a step to chown some directories in /usr??  The owner should *always* be root!  Plus you go on to use sudo to remove files from within those directories, which makes chowning them in the first place completely pointless!

---

### Post by skenliv on 2007-12-05
> **jken146 said:**
> Why is there a step to chown some directories in /usr??  The owner should *always* be root!  Plus you go on to use sudo to remove files from within those directories, which makes chowning them in the first place completely pointless!

Not if you want to break into someones system.
Im having large stability and network problems when AWN curves is installed.
So im removing it in favor for the real AWN, seems it has more than 20 bugfixes
over the AWN-Curves version. Nothing has been done on AWN-Curves for a month.

---

### Post by nikoPSK on 2007-12-05
sorry, meek has been busy. I will ask him when The next updates/ whatever come. Remember, people don't always have time for certain things. I'm removing the vhown commands due to they may harm your system and adding them to the rm list when I get home.

---

### Post by skenliv on 2007-12-05
Not to worry, i know that people build this on their free time and im thankful for it.
Ive moved to the original awn and i dont have any performance or stability issues anymore.

---

### Post by Narender on 2007-12-06
great it worked for me on gutsy.
with one problem

to install awn curves i hade to remove my old installation first.

now experimental gui for stacks has stopped working.
is there a solution...

thanks

---

### Post by nikoPSK on 2007-12-06
well, I don't work on the stacks applet but I'm sure you can head over to the thread on the awn forum.

---

### Post by aquafortis on 2007-12-06
hey Niko, awesome guide.  Very well written.  I'm running into a little bit of a problem though and I hope you can help..  I followed your instructions step by step and I'm running into a problem running with AWN refusing to launch.

This is the error I get:

$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)

awn-manager seems to be running fine.

I know this error message is really vague but maybe you've come across this problem before?  I could really use some help here

---

### Post by nikoPSK on 2007-12-06
definitely before. Many times, you've got a seg fault and I still haven't found a fix for it besides re-installing. This may seem like a dumb question but do you have a window composter running?

I know the new metacity includes whatever so you can run awn without compiz....

---

### Post by dysphasi on 2007-12-06
Excellent guide, thank you! Only problem at the mo is that I can't get the experimental GUI to work with the stacks applet. I had a look on the awn forums and managed to find a new stacks_gui_curved.py that should solve the problem.

Only thing is, how would I go about using this .py file now? Sorry if this is a really basic question, I'm still learning! The forum mentions putting it "in the src/stacks directory where you normally compile"...where might I find this folder?

---

### Post by numbah_one's on 2007-12-07
i managed to install awn on gutsy, i can also see the settings managr,i download the black and human theme but i cant see it?  i installed it using synaptic, also it fails to load settings manager on my kubuntu/desktop session? have i installed it in a wrong way?

---

### Post by rhanex on 2007-12-07
hi,
 i already have awn installed but, like others said "there's a big ugly black background thing". So i decided to use "awn curves" instead, but the problem is when i am going to remove my awn (typing on the terminal) 

rhanex@X-ZODIA:~$ sudo rm -f /usr/local/bin/awn*
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/bin/avant*
rhanex@X-ZODIA:~$ sudo rm -rf /usr/local/lib/awn
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/share/applications/avant*
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/share/applications/awn*
rhanex@X-ZODIA:~$ sudo rm -rf /usr/local/share/avant-window-navigator
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/lib/libawn*
rhanex@X-ZODIA:~$ sudo rm -rf /usr/local/include/libawn
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/lib/libawn*
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/lib/pkgconfig/awn.pc
rhanex@X-ZODIA:~$ sudo rm -rf /usr/local/share/awn-core-applets
rhanex@X-ZODIA:~$ sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/

(after i pressed enter i got this)
rhanex@X-ZODIA:~$ 



it did not do anything.. should  i skip this and move on??
any help would be appreciated. tanx in advance

---

### Post by nikoPSK on 2007-12-07
> **dysphasi said:**
> Excellent guide, thank you! Only problem at the mo is that I can't get the experimental GUI to work with the stacks applet. I had a look on the awn forums and managed to find a new stacks_gui_curved.py that should solve the problem.

Only thing is, how would I go about using this .py file now? Sorry if this is a really basic question, I'm still learning! The forum mentions putting it "in the src/stacks directory where you normally compile"...where might I find this folder?

no clue,sorry, I am not involved in stacks.

> **numbah_one's said:**
> i managed to install awn on gutsy, i can also see the settings managr,i download the black and human theme but i cant see it?  i installed it using synaptic, also it fails to load settings manager on my kubuntu/desktop session? have i installed it in a wrong way?

Follow the guide exactly

> **rhanex said:**
> hi,
 i already have awn installed but, like others said "there's a big ugly black background thing". So i decided to use "awn curves" instead, but the problem is when i am going to remove my awn (typing on the terminal) 

rhanex@X-ZODIA:~$ sudo rm -f /usr/local/bin/awn*
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/bin/avant*
rhanex@X-ZODIA:~$ sudo rm -rf /usr/local/lib/awn
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/share/applications/avant*
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/share/applications/awn*
rhanex@X-ZODIA:~$ sudo rm -rf /usr/local/share/avant-window-navigator
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/lib/libawn*
rhanex@X-ZODIA:~$ sudo rm -rf /usr/local/include/libawn
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/lib/libawn*
rhanex@X-ZODIA:~$ sudo rm -f /usr/local/lib/pkgconfig/awn.pc
rhanex@X-ZODIA:~$ sudo rm -rf /usr/local/share/awn-core-applets
rhanex@X-ZODIA:~$ sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/

(after i pressed enter i got this)
rhanex@X-ZODIA:~$ 



it did not do anything.. should  i skip this and move on??
any help would be appreciated. tanx in advance

it worked. The reason you didn't get asked because of the f option. It removed all right.

---

### Post by dysphasi on 2007-12-07
> **dysphasi said:**
> Excellent guide, thank you! Only problem at the mo is that I can't get the experimental GUI to work with the stacks applet. I had a look on the awn forums and managed to find a new stacks_gui_curved.py that should solve the problem.

Only thing is, how would I go about using this .py file now? Sorry if this is a really basic question, I'm still learning! The forum mentions putting it "in the src/stacks directory where you normally compile"...where might I find this folder?

Ok, managed to answer myself, I didn't realise (being a bit dim as usual)that I'd need to compile from source to update individual applets...I decided to thus start from scratch, uninstalled everything and reinstalled from source.

The best guide I found for this was [here](http://kishandr.wordpress.com/2007/10/19/how-to-install-avant-and-applets-and-also-avant-curves-from-source/) 
Just had a couple of hiccups along the way compiling (it wanted me to install a few more dev dependencies, but nothing too much).
I obtained the additional dependencies as follows:
```

sudo apt-get install libgnome-menu-dev librsvg2-dev libgtop2-dev libnotify-dev libvte-dev

```
I also needed to do the following on my desktop installation:
```

sudo ln -s /usr/local/lib/libawn.so.0 /usr/lib/libawn.so.0

```

After updating the stacks_gui_curved.py with the one from [this post](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1093&page=5&isLive=true) unfortunately the experimental gui STILL didn't work.

Then I did as follows, editing stacks_applet.py (not stacks_gui_curved.py):

_(1) Changing line 190:_
[color=red]self.gui = stacks_gui_curved.StacksGuiCurved(self)[/color]
to
[color=red]self.gui = StacksGuiCurved(self)[/color]


_(2) Changing line 193:_
[color=red]self.gui = stacks_gui_dialog.StacksGuiDialog(self)(self)[/color]
to
[color=red]self.gui = StacksGuiDialog(self)(self)[/color]

_(3) I then added the following to the top of the file:_
[color=red]from stacks_gui_curved import *[/color]
[color=red]from stacks_gui_dialog import *[/color]

Now I have a great looking leopardesque experimental gui for the stacks applet...at last! :guitar:

nb, sure everyone but I would have worked this out first time around, but within the terminal you need to navigate to the folder you downloaded the awn-extras to originally (In my case [color=red]~/avant-window-navigator/awn-extras/awn-applets/awn-extras-applets[/color] and recompile as follows:

```

cd ~/avant-window-navigator/awn-extras/awn-applets/awn-extras-applets
./autogen.sh && make && sudo make install

```

---

### Post by rhanex on 2007-12-07
[B]im stuck in this part, after i typed this
[/B]
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves

**then in my terminal:**
rhanex@X-ZODIA:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autotools-dev is already the newest version.
autotools-dev set to manual installed.
libgnome2-common is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
python-gconf is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 gconf indent libart-2.0-dev libatk1.0-dev
  libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev
  libbonobo2-dev libbonoboui2-dev libcairo2-dev libdbus-1-dev libesd0-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgail-dev libgconf-dev
  libgconf11 libgcrypt11-dev libglade2-dev libglib1.2 libglib1.2-dev
  libgnome-keyring-dev libgnome-vfs-common libgnome-vfs0 libgnomecanvas2-dev
  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev
  libgtk1.2 libgtk1.2-common libhal-dev libhal-storage-dev libice-dev
  libidl-dev libjpeg62-dev liblzo2-dev liboaf-dev liboaf0 libopencdk8-dev
  liborbit-dev liborbit0 liborbit2-dev libpango1.0-dev libpng12-dev
  libpopt-dev libselinux1-dev libsepol1-dev libsm-dev
  libstartup-notification0-dev libstdc++6-4.1-dev libtasn1-3-dev libwrap0-dev
  libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxft-dev libxi-dev libxinerama-dev libxml1 libxml2-dev libxrandr-dev
  libxrender-dev libxres-dev oaf python-gobject-dev python-pyorbit-dev
  python2.5-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-resource-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc nfs-common
  libcairo2-doc libgail-doc libgcrypt11-doc glade glade-gnome libglib2.0-doc
  gnome-vfs-extfs libgnome2-doc libgnomecanvas2-doc libgnomeui-doc gnutls-doc
  gnutls-bin libgtk2.0-doc hal-doc libpango1.0-doc imagemagick
  libstdc++6-4.1-doc
Recommended packages:
  orbit orbit2 python-gnome2-extras-dev docbook-xsl
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 gconf indent libart-2.0-dev
  libatk1.0-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev
  libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libcairo2-dev
  libdbus-1-dev libdbus-glib-1-dev libesd0-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgail-dev libgconf-dev libgconf11
  libgconf2-dev libgcrypt11-dev libglade2-dev libglib1.2 libglib1.2-dev
  libglib2.0-dev libgnome-desktop-dev libgnome-keyring-dev libgnome-vfs-common
  libgnome-vfs-dev libgnome-vfs0 libgnome2-dev libgnomecanvas2-dev
  libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev
  libgtk1.2 libgtk1.2-common libgtk2.0-dev libhal-dev libhal-storage-dev
  libice-dev libidl-dev libjpeg62-dev liblzo2-dev liboaf-dev liboaf0
  libopencdk8-dev liborbit-dev liborbit0 liborbit2-dev libpango1.0-dev
  libpng12-dev libpopt-dev libselinux1-dev libsepol1-dev libsm-dev
  libstartup-notification0-dev libstdc++6-4.1-dev libtasn1-3-dev libwnck-dev
  libwrap0-dev libx11-dev libxau-dev libxcomposite-dev libxcursor-dev
  libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev
  libxinerama-dev libxml1 libxml2-dev libxrandr-dev libxrender-dev libxres-dev
  oaf python-cairo-dev python-dev python-gnome2-dev python-gobject-dev
  python-gtk2-dev python-pyorbit-dev python2.5-dev x11proto-composite-dev
  x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-resource-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 105 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.0MB/31.9MB of archives.
After unpacking 109MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
rhanex@X-ZODIA:~$ 
[B]
and then i moved to the next code:[/B]

rhanex@X-ZODIA:~$ cd awn-curves
bash: cd: awn-curves: No such file or directory
rhanex@X-ZODIA:~$ 

**then jump to another:**
rhanex@X-ZODIA:~$ rm reacocard.asc
rm: cannot remove `reacocard.asc': No such file or directory
rhanex@X-ZODIA:~$ 

[B]hmm..  it wont let me unpack? or it wont let me to continue??
how should i solve this kind of problem?[/B]

---

### Post by nikoPSK on 2007-12-07
you gotta copy the first two lines seperately like.

the sudo apt, get that to finish
then the second wait for that
then copy the cd and all below together.

---

### Post by YoDaddeh on 2007-12-07
Okay I'm encountering a problem, my awn-manager won't load anymore.

I run it in a terminal and it returns:

```
No module named gtk
```

and my stack icon is gone along with my trash icon.

I'm confused and I don't know how to fix it. Removing it and reinstalling it didn't help :(

---

### Post by nikoPSK on 2007-12-07
when did it start not working?

---

### Post by YoDaddeh on 2007-12-07
> **nikoPSK said:**
> when did it start not working?

Yesterday

Why? :confused:

---

### Post by rhanex on 2007-12-07
[B]Awn isn't launching
here's the output[/B]
rhanex@X-ZODIA:~$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)
rhanex@X-ZODIA:~$

---

### Post by nikoPSK on 2007-12-07
> **rhanex said:**
> [B]Awn isn't launching
here's the output[/B]
rhanex@X-ZODIA:~$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)
rhanex@X-ZODIA:~$

well, we have a seg fault... :( Darn, I ened to experiment with ways to fix these but All I can say is remove and start over.... Sorry.

> **YoDaddeh said:**
> Yesterday

Why? :confused:

Did you do anything in particular before? Was it working before?

---

### Post by YoDaddeh on 2007-12-07
> **nikoPSK said:**
> 
Did you do anything in particular before? Was it working before?

Now that you Mention it, I have noticed a few things acting rather funny, I went to modify the look of pidgin and I think I deleted /usr/share/pixmaps/ folder when I moved the new images to it. ](*,)

Is there any way I can redo it without redoing the system?

---

### Post by nikoPSK on 2007-12-07
I'm sure there is some reconfigure command

sudo dpkg-reconfigure ????

look around, or just jump in and go for a clean gutsy install.

---

### Post by YoDaddeh on 2007-12-07
> **nikoPSK said:**
> I'm sure there is some reconfigure command

sudo dpkg-reconfigure ????

look around, or just jump in and go for a clean gutsy install.

Looks like it might just be easier to do a clean install. I know this sounds crazy but I should put xp back on so I can really game :lolflag:

I'll probably end up dual booting again :)

Thanks for your help

---

### Post by nikoPSK on 2007-12-07
NO!!!111111 If you are truly a gamer (like me) visit the ubuntu gamers arena and get cedega.

---

### Post by nikoPSK on 2007-12-07
cedega not at the arena, just check it out. Cedega = easier to install windows games and A wide variety of support.

---

### Post by YoDaddeh on 2007-12-07
> **nikoPSK said:**
> cedega not at the arena, just check it out. Cedega = easier to install windows games and A wide variety of support.

I'm broke. I don't own any form of e money so I think thats out of the question. I heard Cedega costs money. I'll look into it though.

---

### Post by nikoPSK on 2007-12-07
wait I'll pm you....

---

### Post by numbah_one's on 2007-12-07
i followed everything you said but i cant seem to get it to work on my laptop? do i need some 3d enabled video card for it to work?,im using an old pentium III hp mobile cpu 1133mhz

---

### Post by YoDaddeh on 2007-12-07
> **numbah_one's said:**
> i followed everything you said but i cant seem to get it to work on my laptop? do i need some 3d enabled video card for it to work?,im using an old pentium III hp mobile cpu 1133mhz

You should have your visual effects turned on for avant to work. (Restricted drivers enabled, compiz, etc)

---

### Post by nikoPSK on 2007-12-07
I read that metacity has built in composite now....

---

### Post by Gourgi on 2007-12-08
yeesssss
i just did it !
very nice look indeed
i experienced a "segment fault" error when trying to open avant-window-navigator  i 
started synaptic and i searched and checked for re-install everyhting related to awn/avant 
and then ... no errors :D 

is there a way to keep the awn-curves folder and use bzr to update the files so that i can install it again and be up-to-date ?
if so which is the command for doing it ? (bzr check ?)

---

### Post by nikoPSK on 2007-12-08
I don't know, I never got a seg fault from my instructions... Well good for you though:D.

---

### Post by nhtrung on 2007-12-09
hello,

I followed the guide. The Avant Window Navigator and Awn manager appeared in the panel. Hoever, I could not run it from the panel or from terminal. It just does not run, not giving any error. The only error that I get is when I run sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr.
Here's the error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr151-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages

The package python-libawn-bzr and libawn-bzr cannot be installed although I have installed libpango.

I forgot that when I tried to run it in terminal, I got the following error:

avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory

Anyone knows what happened?

---

### Post by nikoPSK on 2007-12-09
are your universe and multiverse repos enabled?

---

### Post by nhtrung on 2007-12-09
Yes, I did.

I forgot that when I tried to run it in terminal, I got the following error:

avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory

---

### Post by nikoPSK on 2007-12-09
would you try reinstalling? Sorry, I *_really_* need to find a different way...

---

### Post by nhtrung on 2007-12-09
Yes. I have tried many times. I tried the avant window without curve but the same thing happened.
Then I uninstall it and reinstall using your guide line by line but no luck. It's weird. I am using Gutsy with Compiz Fusion, everything else is okie

---

### Post by nhtrung on 2007-12-09
I have figured it out. This magic command helped me out:
sudo ldconfig

Thanks anyway for your very quick reply

---

### Post by nikoPSK on 2007-12-09
np:popcorn:

---

### Post by craigyjack on 2007-12-10
hey,
i was just wondering if awn-curves has been updated anytime recently. I am currently using it, but i dont know how to see if the source code has been updated or whatnot, and i was just wondering if i should recompile the newest code, because i always like having the most current installs :)

any changes so that i should update, or is there no need to right now?
thanks,
craig

---

### Post by dysphasi on 2007-12-10
> **craigyjack said:**
> hey,
i was just wondering if awn-curves has been updated anytime recently. I am currently using it, but i dont know how to see if the source code has been updated or whatnot, and i was just wondering if i should recompile the newest code, because i always like having the most current installs :)

any changes so that i should update, or is there no need to right now?
thanks,
craig

All you need to do is go into the folder you compiled it from, e.g. '~/awn-curves' and do a 'bzr update' to check what version you have and whether it can be updated. If there is an update then let it run and after it has updated recompile as usual. To clarify, you'd be doing as follows from the terminal:
```

cd ~/awn-curves
bzr update
./autogen.sh ; make ; sudo make install

```

---

### Post by antisocialist on 2007-12-10
avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)
allan@allan-laptop:~$ awn-manager
allan@allan-laptop:~$ 


awn wont launch, is it becuase i forgot to close it while i uninstalled it and installed awn-curves?

---

### Post by craigyjack on 2007-12-10
> **dysphasi said:**
> All you need to do is go into the folder you compiled it from, e.g. '~/awn-curves' and do a 'bzr update' to check what version you have and whether it can be updated. If there is an update then let it run and after it has updated recompile as usual. To clarify, you'd be doing as follows from the terminal:
```

cd ~/awn-curves
bzr update
./autogen.sh ; make ; sudo make install

```

Thanks! I will be checking for updates now.
-Craig

---

### Post by nikoPSK on 2007-12-10
> **antisocialist said:**
> avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)
allan@allan-laptop:~$ awn-manager
allan@allan-laptop:~$ 
 
 
awn wont launch, is it becuase i forgot to close it while i uninstalled it and installed awn-curves?
 
possibly, but it shouldn't affect anything... *sigh* try a reinstall.
 
> **dysphasi said:**
> All you need to do is go into the folder you compiled it from, e.g. '~/awn-curves' and do a 'bzr update' to check what version you have and whether it can be updated. If there is an update then let it run and after it has updated recompile as usual. To clarify, you'd be doing as follows from the terminal:
```

cd ~/awn-curves
bzr update
./autogen.sh ; make ; sudo make install

```
 
I will add that to my guide :lolflag: I forgot to mention.

---

### Post by nikoPSK on 2007-12-10
[quote=meek]At the moment I don't really have the time to fix the problems. Especially for the applet icons that aren't updated. There's no way to get it work in 0.2. At least there's no solution that isn't very complex. 0.3 will make it needless anyhow.
There will be better ways to implement the curves-look in 0.3. No crashes (because of shared memory), Icons can be updated.
[[IMG]http://www.planetblur.org/hosted/awnforum/engine/grafts/newdefault/images/qq.png[/IMG]]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=853&page=1&isLive=true#")
  


  So the best is just to wait, I think.
[/quote]

Quote. from the awn forums.

---

### Post by Gourgi on 2007-12-11
> **dysphasi said:**
> 
```

cd ~/awn-curves
bzr update
./autogen.sh ; make ; sudo make install

```
that was what i was looking for ...
thanks for the tip !

---

### Post by Joco_Ultimate on 2007-12-11
I am a real noob with linux but I would really like to have this dock working. When I press Alt F2 and add the line and press run I don't know what to do. You say add the two lines at the bottom but I don't see where to add them. Please help =)

---

### Post by dysphasi on 2007-12-11
> **Gourgi said:**
> that was what i was looking for ...
thanks for the tip !

np ;)

---

### Post by Vadi on 2007-12-11
> **Joco_Ultimate said:**
> I am a real noob with linux but I would really like to have this dock working. When I press Alt F2 and add the line and press run I don't know what to do. You say add the two lines at the bottom but I don't see where to add them. Please help =)

After you press alt+f2, copy/paste that gedit line, and press enter. It'll prompt you for your password, and then open the text editor with a huge list. Scroll down to the bottom of the list, and copy/paste those two lines at the bottom. And then continue with the instructions :)

---

### Post by nikoPSK on 2007-12-11
> **Gourgi said:**
> that was what i was looking for ...
thanks for the tip !

np, I forgot (!) to add that when I created my guide:lolflag:

> **Joco_Ultimate said:**
> I am a real noob with linux but I would really like to have this dock working. When I press Alt F2 and add the line and press run I don't know what to do. You say add the two lines at the bottom but I don't see where to add them. Please help =)

If it doesn't open from alt+f2 run the same command in the terminal.

---

### Post by Vadi on 2007-12-11
Hrm. Awn-curves isn't appearing in my theme list for awn (and yes, I followed everything perfectly).

So I did an update then, and I get the following now:

> $ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)
vadi@vadi-laptop:~/awn-curves$

But when I launch it from alt+f2, it works. No curves though.

---

### Post by nikoPSK on 2007-12-11
> **Vadi said:**
> Hrm. Awn-curves isn't appearing in my theme list for awn (and yes, I followed everything perfectly).

So I did an update then, and I get the following now:



But when I launch it from alt+f2, it works. No curves though.

does it work from your curves folder? /home/XXX/awn-curves/src

where xxx is your username. Run the avant-window-navigator.

---

### Post by dysphasi on 2007-12-11
> **Vadi said:**
> Hrm. Awn-curves isn't appearing in my theme list for awn (and yes, I followed everything perfectly).

So I did an update then, and I get the following now:



But when I launch it from alt+f2, it works. No curves though.

I had that somewhere along the line when I first tried to compile everything from source. If that's what you want to do, I followed the guide that I've linked to on [[color=blue]_page 46_[/color]](http://ubuntuforums.org/showthread.php?p=3909813#post3909813) of this thread.

Either way though, the only way I got around the problem was by wiping everything and starting over from scratch. Bit of a pain, but couldn't get anything else to work for me.

---

### Post by dshuck on 2007-12-12
Does anyone know if there is something wrong with the Feisty repo?  I followed all instructions from page 1, installing all dependencies, walking through the compilation, adding the sources, apt-get update (no errors on the awm repo), yet when I get to the line:

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

I get:
```
E: Couldn't find package avant-window-navigator-bzr

```

If I just try to do:
sudo apt-get install awn-core-applets-bzr

I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  awn-core-applets-bzr: Depends: libawn-bzr but it is not installable
                        Depends: libawn-bzr but it is not installable
E: Broken packages


```

any idea what I am missing here?

---

### Post by nikoPSK on 2007-12-12
> **dshuck said:**
> Does anyone know if there is something wrong with the Feisty repo?  I followed all instructions from page 1, installing all dependencies, walking through the compilation, adding the sources, apt-get update (no errors on the awm repo), yet when I get to the line:

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

I get:
```
E: Couldn't find package avant-window-navigator-bzr

```

If I just try to do:
sudo apt-get install awn-core-applets-bzr

I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  awn-core-applets-bzr: Depends: libawn-bzr but it is not installable
                        Depends: libawn-bzr but it is not installable
E: Broken packages


```

any idea what I am missing here?

broken packages... I've had this before. I will ask reacocard and just try reinstalling for now.

---

### Post by reacocard on 2007-12-12
> **dshuck said:**
> Does anyone know if there is something wrong with the Feisty repo?  I followed all instructions from page 1, installing all dependencies, walking through the compilation, adding the sources, apt-get update (no errors on the awm repo), yet when I get to the line:

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

I get:
```
E: Couldn't find package avant-window-navigator-bzr

```

If I just try to do:
sudo apt-get install awn-core-applets-bzr

I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  awn-core-applets-bzr: Depends: libawn-bzr but it is not installable
                        Depends: libawn-bzr but it is not installable
E: Broken packages


```

any idea what I am missing here?

feisty repo is completely unsupported now.  upgrade to gutsy or compile from source.

@nikoPSK: you should remove the feisty repo from the guide.

---

### Post by dshuck on 2007-12-12
Ahhh well that at least makes sense.  I would love to upgrade, but I am in the middle of a heavy development cycle on this machine with a delivery date fast approaching.  I would have to spend a day resetting up all the friggin app servers I am running on here.  In the words of Mr. T, I have no time for jibba jabba. :)  I will upgrade the second this code gets delivered though.... guarantee.

---

### Post by nikoPSK on 2007-12-12
> **reacocard said:**
> feisty repo is completely unsupported now.  upgrade to gutsy or compile from source.

@nikoPSK: you should remove the feisty repo from the guide.

Okay, thanks reacocard.

---

### Post by Miroku on 2007-12-12
hello again

is there any way to avoid setting up a custom icon for each individual application over and over again? 

the problem is with a program like pidgin. i must set an icon for every person that IMs me. i cant just choose one icon and have it show every time a different person IMs me. another example is whenever i open a .doc file in openoffice. i'll open a file, set the icon but then when i open a different file that is also .doc, avant uses some old, crappy looking icon that i must change again. it happens in a bunch of other programs too. like in irc, i change the icon and then when i join a channel on a server, the icon switches to the original (not the custom one i set). can someone please help. 

the rest of avant is amazing!! thanks to all the efforts by everyone that contributed. l

et me know if im not being clear about the problem im having. TIA.

---

### Post by reacocard on 2007-12-12
> **Miroku said:**
> hello again

is there any way to avoid setting up a custom icon for each individual application over and over again? 

the problem is with a program like pidgin. i must set an icon for every person that IMs me. i cant just choose one icon and have it show every time a different person IMs me. another example is whenever i open a .doc file in openoffice. i'll open a file, set the icon but then when i open a different file that is also .doc, avant uses some old, crappy looking icon that i must change again. it happens in a bunch of other programs too. like in irc, i change the icon and then when i join a channel on a server, the icon switches to the original (not the custom one i set). can someone please help. 

the rest of avant is amazing!! thanks to all the efforts by everyone that contributed. l

et me know if im not being clear about the problem im having. TIA.

icon handling is still slightly buggy and I don't think the window matching rules are powerful enough to do what you describe yet. Ideally this sort of thing would be implemented in the applications themselves, ie. the application tells awn what the icon for each window should be over DBUS. unfortunately I do not think the pidgin plugin supports that yet.

---

### Post by mtacqua on 2007-12-12
> **rune0077 said:**
> It's a bad Python script in the applet. You need to download the fixed script from [http://www.mediafire.com/?5zblavmixhc](http://www.mediafire.com/?5zblavmixhc), then use it to replace the one already in the stacks applet, then make and make install. That fixed it for me.

The updated file is not at the link, I am having the same issues.  Anyone know where the update is?


Also. I wanted to add the open office shortcuts to the stacks, and other programs.  What is the easiest way?

Sorry to hijack, I did a search for my issue and this thread came up.  I didn't even look at the title.  I'll just edit this post instead if replying.  I looked the link and it all works now.  I figured out what was going on w/ the oo shortcuts.  I was dragging them to the desktop then to folder for the stack shortcuts.  The command in the launcher had %U after the cmd, I removed that and it worked.

---

### Post by nikoPSK on 2007-12-12
I am sorry, this is the awn-curves thread. If you want you can make a new thread about the stacks applet problems.

---

### Post by dysphasi on 2007-12-13
> **mtacqua said:**
> The updated file is not at the link, I am having the same issues.  Anyone know where the update is?


Also. I wanted to add the open office shortcuts to the stacks, and other programs.  What is the easiest way?

What is your trouble with stacks at the moment? Is it plain not working? Have a ganders at my post on [[color=blue]_page 46_[/color]](http://ubuntuforums.org/showthread.php?p=3909813#post3909813) of this thread 

There's a link there to where you can get the updated python script and I've also detailed how to get stacks working. Hope this helps :-s

To add shortcuts to the stacks you need to link the stacks applet to a chosen folder that contains the shortcuts that you want: Right click the stacks applet -> Preferences -> Open -> Click on 'Browse for other folders' -> Select the folder that you want with your shortcuts in > Cick apply > Click apply again in the main window and it should be set up for you.

---

### Post by Tristam Green on 2007-12-13
OK.  I succesfully installed AWN two days ago, after two separate tries.  I figured today I'd test my luck with AWN-Curves.  No dice.  I followed the precise steps in the OP, and when I fired up avant-window-navigator (GUI icon or CLI command), my old AWN reappears, without any kind of curves option?

What have I done wrong?

output of bzr update:
```
Tree is up to date at revision 169.
```



HELP! ~Tristam

---

### Post by kaizah on 2007-12-14
My awm dock is messed up now. right now when i start awn. I see the bar, but the background is completely white.. on the entire desktop, like 50 pixels high!

I followed all the steps of this post, and i was trying the different looks, it started the flatbar, i changed to 3d look ( everything was still fine here ), then i changed to curves! and my problem started. I tried reinstalling by removing all the directories, and reinstalling.. but it´s not helping.

what can i do? how to fix if it´s fixable, or how to remove if removable..

---

### Post by Gyatak on 2007-12-14
Thanks for you time and effort with this. Everything seemed to install correctly, but now I can't get AWN to launch. Here's what I get when I enter **avant-window-navigator** into the terminal:

```
$ avant-window-navigator
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
Segmentation fault (core dumped)
bill@cinnabar:~$ /usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)

(awn-applet-activation:22091): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:22091): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

```When I enter **awn-manager** into the console, the AWN manager comes up as it should with the extra features added.

Any idea what I should do?

Thanks again!

P.S. I just ran the **avant-window-navigator** command immediately after re-boot and received a different response than what's listed above. Thought this would be useful:

```
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
Segmentation fault (core dumped)
bill@cinnabar:~$
(awn-applet-activation:7340): Gdk-WARNING **: GdkWindow 0x3a0001f unexpectedly d
estroyed

(awn-applet-activation:7340): Gdk-WARNING **: GdkWindow 0x3a00004 unexpectedly d
estroyed
The program 'awn-applet-activation' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 157 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_get_qdata:                                     assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_set_qdata_                                    full: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_unref: ***                                    ertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)

(awn-applet-activation:7336): Gdk-CRITICAL **: gdk_window_get_origin: assertion                                     `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:7336): Gdk-CRITICAL **: gdk_window_get_origin: assertion                                     `GDK_IS_WINDOW (window)' failed

```

Nevermind, guys. I found the uninstall instructions further up in these posts.

---

### Post by nikoPSK on 2007-12-14
> **kaizah said:**
> My awm dock is messed up now. right now when i start awn. I see the bar, but the background is completely white.. on the entire desktop, like 50 pixels high!

I followed all the steps of this post, and i was trying the different looks, it started the flatbar, i changed to 3d look ( everything was still fine here ), then i changed to curves! and my problem started. I tried reinstalling by removing all the directories, and reinstalling.. but it´s not helping.

what can i do? how to fix if it´s fixable, or how to remove if removable..

reinstall... :(

> **Tristam Green said:**
> OK.  I succesfully installed AWN two days ago, after two separate tries.  I figured today I'd test my luck with AWN-Curves.  No dice.  I followed the precise steps in the OP, and when I fired up avant-window-navigator (GUI icon or CLI command), my old AWN reappears, without any kind of curves option?

What have I done wrong?

output of bzr update:
```
Tree is up to date at revision 169.
```

I do not know. I will try updating when I get home



HELP! ~Tristam

> **Gyatak said:**
> Thanks for you time and effort with this. Everything seemed to install correctly, but now I can't get AWN to launch. Here's what I get when I enter **avant-window-navigator** into the terminal:

```
$ avant-window-navigator
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
Segmentation fault (core dumped)
bill@cinnabar:~$ /usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)

(awn-applet-activation:22091): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:22091): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

```

When I enter **awn-manager** into the console, the AWN manager comes up as it should with the extra features added.

Any idea what I should do?

Thanks again!

reinstall. If you want to remove look down in my guide. Under the bog bold font "remove".

---

### Post by nbayiha on 2007-12-15
u can try sudo ldconfig  in the folder awn.

---

### Post by Gyatak on 2007-12-16
Thanks, everyone. I got it working. Very cool!

---

### Post by nikoPSK on 2007-12-16
np enjoy.

---

### Post by Swmmrman on 2007-12-16
Are there any themes other then then the ones listed in the op?  Been digging threw but not finding any

---

### Post by InsaneSith on 2007-12-16
> **Swmmrman said:**
> Are there any themes other then then the ones listed in the op?  Been digging threw but not finding any
[Gnome-Look.org](http://gnome-look.org/content/search.php?xsortmode=new&search=1&type=0&name=awn) has a few.

---

### Post by andrewabc on 2007-12-16
Using AWN, either the curves, 3d bar, flat bar, some icons do not align correctly. Sometimes one icon is lower or higher than the others. When it is higher and AWN autohides you can see the top of an icon. When lower the bottom of the icon is cut off.

Any ides? Seems to be mostly with the trash applet icon. Also if I enable "show separator between launchers and tasks" all the icons disappear.

I guess this is more of a general AWN question than curves related. I still havn't figured out what symmetry bar does. I change it and I notice no difference

[[IMG]http://img142.imageshack.us/img142/7696/trashlowerju4.th.png[/IMG]](http://img142.imageshack.us/my.php?image=trashlowerju4.png)
[[IMG]http://img141.imageshack.us/img141/1166/screenshot1xk3.th.png[/IMG]](http://img141.imageshack.us/my.php?image=screenshot1xk3.png)

---

### Post by Dark Hornet on 2007-12-16
yeah...i have had similar issues, and I have found that restarting AWN usually fixes it.  I think this is a bug that the devs of AWN curves are currently working on.

---

### Post by fmartinez on 2007-12-16
Worked Great! No issues!!!!!! Thanks nikoPSK

---

### Post by nikoPSK on 2007-12-16
> **andrewabc said:**
> Using AWN, either the curves, 3d bar, flat bar, some icons do not align correctly. Sometimes one icon is lower or higher than the others. When it is higher and AWN autohides you can see the top of an icon. When lower the bottom of the icon is cut off.

Any ides? Seems to be mostly with the trash applet icon. Also if I enable "show separator between launchers and tasks" all the icons disappear.

I guess this is more of a general AWN question than curves related. I still havn't figured out what symmetry bar does. I change it and I notice no difference

[[IMG]http://img142.imageshack.us/img142/7696/trashlowerju4.th.png[/IMG]]("http://img142.imageshack.us/my.php?image=trashlowerju4.png")
[[IMG]http://img141.imageshack.us/img141/1166/screenshot1xk3.th.png[/IMG]]("http://img141.imageshack.us/my.php?image=screenshot1xk3.png")

symmetry makes it ---0--- symmetric -0----- asymmetric.  @fmartinez glad you enjoy.

---

### Post by Othonas on 2007-12-17
Hello..I am a new guy in ubuntu an i am experiencing some problems in getting to work this toolbar.
In the last command ( sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr ) I get this output:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr151-1) but 0.2.0-bzr141-1 is to be installed
  awn-core-applets-bzr: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages
 So I cannot install the toolbar properly. Also, I cannot unistall the previous AWN toolbar (the simple edition) with the commands given. I don't know why, but I can run the simple edition at any time..
Any help welcome..

---

### Post by nikoPSK on 2007-12-17
are you in hardy development?

---

### Post by Dark Hornet on 2007-12-17
It looks like you don't have the correct dependencies installed....did you add these two repositories?

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

---

### Post by Othonas on 2007-12-17
I've checked what you said and I have already added these dependencies..Any other ideas??

---

### Post by Othonas on 2007-12-17
Maybe the problem is that I cannot uninstall the "normal" AWN...Can you help do it?

---

### Post by Dark Hornet on 2007-12-17
Well, I don't have "normal" AWN installed...infact, if you do this guide tells you to uninstall it.   Sorry, but I am not an expert with AWN curves, I just followed the guide at the beginning of this thread, and it worked great.  I will answer whatever I can though...Good luck!

---

### Post by fantan on 2007-12-17
Hello everybody,

I tried to install AWN-curves according to this thread but when I try to run the following commands, 

cd awn-curves
./autogen.sh && make
sudo make install 
I've got the following messages:

"Processing ./configure.in
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `..'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in
Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).
Running intltoolize...
intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite"

Of course, I can't select curve insteed of "flat bar" or "3D look" in the awn-manager, because it isn't there. 
As a result, I can't setting up also the downloaded themes "milk.tgz" and "black.tgz". 

Can anybody tell me what to do in this case?

Thank you for advance!

Best regards,
fantan

---

### Post by reacocard on 2007-12-17
> **Othonas said:**
> Hello..I am a new guy in ubuntu an i am experiencing some problems in getting to work this toolbar.
In the last command ( sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr ) I get this output:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr151-1) but 0.2.0-bzr141-1 is to be installed
  awn-core-applets-bzr: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages
 So I cannot install the toolbar properly. Also, I cannot unistall the previous AWN toolbar (the simple edition) with the commands given. I don't know why, but I can run the simple edition at any time..
Any help welcome..

you need to have ubuntu-updates enabled and your entire system up-to-date.

---

### Post by ddrake89 on 2007-12-20
I installed it sucessfully, but i cant get it to work i have 7.10 (gusty).......The manager will open and i can change all of the settings but no cool bar......BTW, i'm new at ubuntu ive been at it 3 days, i installed compiz just today and everything on it works but the water effect... Plz help me though

---

### Post by dysphasi on 2007-12-20
How did you install? As per the instructions in this how-to you should really be able to go to Applications -> Accessories -> Avant Window Navigator.

Have you tried Applications -> Accessories -> Terminal and from the terminal typed:
avant-window-navigator
? Worth a shot if not.

---

### Post by taavi7 on 2007-12-21
my awn preferences window isnt appearing..does anyone know how to make it appear?

never mind..got it work :D

---

### Post by averyh on 2007-12-21
I installed everything and I saw no errors.  When i click on the program to load it terminates instantly.  This is the copied code from the commands you suggested to input if the program wouldn't start  

> 
/apps/avant-window-navigator/force_monitor unset, setting now
/apps/avant-window-navigator/monitor_width unset, setting now
/apps/avant-window-navigator/monitor_height unset, setting now
/apps/avant-window-navigator/panel_mode unset, setting now
/apps/avant-window-navigator/auto_hide unset, setting now
/apps/avant-window-navigator/auto_hide_delay unset, setting now
/apps/avant-window-navigator/keep_below unset, setting now
/apps/avant-window-navigator/bar/bar_height unset, setting now
/apps/avant-window-navigator/bar/bar_pos unset, setting now
/apps/avant-window-navigator/bar/bar_angle unset, setting now
/apps/avant-window-navigator/bar/icon_offset unset, setting now
/apps/avant-window-navigator/bar/rounded_corners unset, setting now
/apps/avant-window-navigator/bar/corner_radius unset, setting now
/apps/avant-window-navigator/bar/render_pattern unset, setting now
/apps/avant-window-navigator/bar/pattern_uri unset, setting now
/apps/avant-window-navigator/bar/pattern_alpha unset, setting now
/apps/avant-window-navigator/bar/glass_step_1 unset, setting now
/apps/avant-window-navigator/bar/glass_step_2 unset, setting now
/apps/avant-window-navigator/bar/glass_histep_1 unset, setting now
/apps/avant-window-navigator/bar/glass_histep_2 unset, setting now
/apps/avant-window-navigator/bar/border_color unset, setting now
/apps/avant-window-navigator/bar/hilight_color unset, setting now
/apps/avant-window-navigator/bar/show_separator unset, setting now
/apps/avant-window-navigator/bar/sep_color unset, setting now
/apps/avant-window-navigator/window_manager/show_all_windows unset, setting now
/apps/avant-window-navigator/window_manager/launchers unset, setting now
/apps/avant-window-navigator/app/active_png unset, setting now
/apps/avant-window-navigator/app/use_png unset, setting now
/apps/avant-window-navigator/app/arrow_color unset, setting now
/apps/avant-window-navigator/app/arrow_offset unset, setting now
/apps/avant-window-navigator/app/tasks_have_arrows unset, setting now
/apps/avant-window-navigator/app/name_change_notify unset, setting now
/apps/avant-window-navigator/app/alpha_effect unset, setting now
/apps/avant-window-navigator/app/icon_effect unset, setting now
/apps/avant-window-navigator/title/text_color unset, setting now
/apps/avant-window-navigator/title/shadow_color unset, setting now
/apps/avant-window-navigator/title/background unset, setting now
/apps/avant-window-navigator/title/font_face unset, setting now
Screen is composited.
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_shared_mem_create

when I do awn-manager the actually gui comes up.  when I go to load anything while having Konsole up it gives me this message > Traceback (most recent call last):
  File "/usr/local/share/avant-window-navigator/awn-manager/awnLauncher.py", line 213, in add
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
  File "/usr/lib/python2.5/subprocess.py", line 593, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory


I cannot open anything at all, but I can see all the applets and all.

Thanks guys.

---

### Post by Joeb454 on 2007-12-22
Great guide - worked for me :) Though I don't really use awn much :p

---

### Post by taavi7 on 2007-12-22
i have a little problem with the last step. 
when i type sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
it sais that  Couldn't find package avant-window-navigator-bzr.
 what is the problem?

btw im running feisty :)

---

### Post by nikoPSK on 2007-12-22
> **averyh said:**
> I installed everything and I saw no errors.  When i click on the program to load it terminates instantly.  This is the copied code from the commands you suggested to input if the program wouldn't start  



when I do awn-manager the actually gui comes up.  when I go to load anything while having Konsole up it gives me this message 

I cannot open anything at all, but I can see all the applets and all.

Thanks guys.

KDE might be your problem right  there.

> **taavi7 said:**
> i have a little problem with the last step. 
when i type sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
it sais that  Couldn't find package avant-window-navigator-bzr.
 what is the problem?

btw im running feisty :)

the older repos are removed, it should work, try again. :D

---

### Post by reacocard on 2007-12-22
> **taavi7 said:**
> i have a little problem with the last step. 
when i type sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
it sais that  Couldn't find package avant-window-navigator-bzr.
 what is the problem?

btw im running feisty :)

feisty is unsupported in the repo used. you'll have to either compile all of awn from source or upgrade to gutsy.

---

### Post by Vadi on 2007-12-22
Meh, I really-really hope development picks up on awn curves again. I don't like the normal awn, I feel that it's unoriginal with the boxy thing, no matter what skin you put on it.

And awn-curves makes awn randomly segfault when an icon does the notification bouncing :(

---

### Post by sujoy on 2007-12-23
is it possible to put the dock on the top of the screen or on the sides rather than keep it the bottom? and what about two docks? say one at the top and one at the side? how do i do this?

---

### Post by Vadi on 2007-12-23
I couldn't find such options in AWN. It is possible in Kiba dock, but that project isn't actively developed anymore.

---

### Post by bharadwaj on 2007-12-23
thank you this was very easy and useful walk through

---

### Post by sujoy on 2007-12-23
> **Vadi said:**
> I couldn't find such options in AWN. It is possible in Kiba dock, but that project isn't actively developed anymore.

ya, and sorry for asking it, later i saw at the awn forum that it is not possible. they will perhaps add it in the next release

---

### Post by nikoPSK on 2007-12-23
> **Vadi said:**
> I couldn't find such options in AWN. It is possible in Kiba dock, but that project isn't actively developed anymore.
 
I don't seem to like it either. Meek has been very busy and has left the project alone for awhile. :(

---

### Post by mincho on 2007-12-23
Works Perfectly On Intel DG965ryck with gma x3000......with compiz fusion

---

### Post by anyo409 on 2007-12-23
worked like a charm ........ pretty cool stuff

---

### Post by reacocard on 2007-12-24
> **sujoy said:**
> ya, and sorry for asking it, later i saw at the awn forum that it is not possible. they will perhaps add it in the next release

support for multiple bars and different positions is scheduled for awn 0.3. no idea how long that'll be though, probably several months at the least.

---

### Post by sujoy on 2007-12-24
would be a great addition though. specially the positional constraint is disappointing.

---

### Post by Ajd on 2007-12-24
It installed without any errors, but I was getting the following error.

```
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_shared_mem_create
```

This was fixed by running
 sudo apt-get reinstall awn-core-applets-bzr libawn-bzr python-libawn-bzr

---

### Post by sujoy on 2007-12-24
its working fine for me , almost perfect but the only problem is that it vanishes at times. like when i maximise a window and its covered, now when i minimise it, i see that awn is gone. It just simply goes off the system monitor's record too.

---

### Post by Vadi on 2007-12-24
It's a bug in awn-curves. Sadly, as I understand the creator doesn't have time to fix it.

And it crashes, not vanishes, heh.

---

### Post by nikoPSK on 2007-12-25
> **Vadi said:**
> It's a bug in awn-curves. Sadly, as I understand the creator doesn't have time to fix it.

And it crashes, not vanishes, heh.

ya, really sorry about that... maybe I could help pick it up? :confused:

---

### Post by Vadi on 2007-12-25
Go ahead! :)

---

### Post by Vadi on 2007-12-25
Edit: Ignore this "fix", Apparently AWN can crash as soon as it starts up too. The script will make it go in an endless loop, it'll be impossible to kill (even after you've closed the terminal running it, and it's impossible to track down in the system monitor), and the only solution to that would be to reboot.

:(

---

### Post by nikoPSK on 2007-12-25
> **Vadi said:**
> Go ahead! :)

thanks for the script! (Did you make it?) :confused: I'd have to learn a bit more about awn before I join. I'm reading up on it as much as I can. :)

---

### Post by MRCeltic on 2007-12-25
Just wondering if you could give me a hand when i paste the last command 

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr


I get this error

Code:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr151-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages


Any Idea of a quick and easy fix?

---

### Post by UlisseOpenMind on 2007-12-27
I have a dot instead of arrow under the icon ... how can i solve this?
then when i open swiftweasel (only this) a new icon appears, instead of an arrow/dot under the existing icon ... i have never had this problem bfore -.-

---

### Post by nikoPSK on 2007-12-27
> **MRCeltic said:**
> Just wondering if you could give me a hand when i paste the last command 

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr


I get this error

Code:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr151-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages


Any Idea of a quick and easy fix?

a reinstall will solve this... :\

> **UlisseOpenMind said:**
> I have a dot instead of arrow under the icon ... how can i solve this?
then when i open swiftweasel (only this) a new icon appears, instead of an arrow/dot under the existing icon ... i have never had this problem bfore -.-

The dot indicates it's a running program. If there isn't a launcher the icon will pop up or whatever transition and have a dot underneath. The developer is working on an arrow/ dot selection for users.

---

### Post by awiggin on 2007-12-27
I followed all the instructions.  But after I type in this line:
> **nikoPSK said:**
> 

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```[CENTER]**[SIZE=7]Q & A:[/SIZE]**[/CENTER]


I get:

> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
E:  Couldn't find package avant-window-navigator-bzr


Please help!

-awiggin

---

### Post by westyonfire on 2007-12-27
Hi could some one please help me. 
After I put "bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves" in the console my connection dropped out. i had to reboot to get it working again. After reboot i did the command again and it says the 'awn-curves' folder already exists. I 'cd awn-curves' then absent mindedly tried "bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves" again so i think it installed it badly. I thin what i need to do is completely remove the awn-curves directory again and do the "bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves" part again. But i dont know how. Would anyone help me out please?

---

### Post by reacocard on 2007-12-27
> **westyonfire said:**
> Hi could some one please help me. 
After I put "bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves" in the console my connection dropped out. i had to reboot to get it working again. After reboot i did the command again and it says the 'awn-curves' folder already exists. I 'cd awn-curves' then absent mindedly tried "bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves" again so i think it installed it badly. I thin what i need to do is completely remove the awn-curves directory again and do the "bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves" part again. But i dont know how. Would anyone help me out please?

```
rm -r awn-curves
```

---

### Post by a-converted-sparky on 2007-12-27
Hi guys

Im a newbie (their i have sed it! lol)

i have got awn manager installed, loving it (no errors or problems) ...
.but i do not have the option in bar appearance to change to curve look?

I only 2 options which are flat or 3d? any ideas what i have done wrong?

Using Ubuntu 7.10 - Gutsy

---

### Post by a-converted-sparky on 2007-12-27
sorted!

i redone this bit:

bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves

complied and installed it, i have now have all options

---

### Post by rahulsharma on 2007-12-28
hey i installed the awn its working fine except when i have to add the things like word launcher, movie player it get adds to it but when i restart my computer they disappear and only the launcher which i have added by preferences->applets only they remain rest disappears. I was wondering is there any specific way to add stuff to it what i usually do is  drag it to the dock. But i would definitely say this is a good one.

---

### Post by heyster on 2007-12-29
Add me to the ones who also got it working.:KS
But there are a few things which I can not solve with the help of the search and google.

- even with the command nautilus \folder\to\add\ I can not add a folder to the dock
- is there a workaround to see the most used or resent used programs on the right side?
- when will the stack (like Leopard has) feature be available?

Many thanks

---

### Post by reacocard on 2007-12-29
> **heyster said:**
> Add me to the ones who also got it working.:KS
But there are a few things which I can not solve with the help of the search and google.

- even with the command nautilus \folder\to\add\ I can not add a folder to the dock
- is there a workaround to see the most used or resent used programs on the right side?
- when will the stack (like Leopard has) feature be available?

Many thanks

for the second, no

for the other two, stacks are already available via the awn-extras project (awn-core-applets-bzr package in the repo), and a stacks folder can double as a folder launcher as middle-clicking a stacks icon will open that folder in the file browser.

---

### Post by heyster on 2007-12-30
> **reacocard said:**
> for the second, no

for the other two, stacks are already available via the awn-extras project (awn-core-applets-bzr package in the repo), and a stacks folder can double as a folder launcher as middle-clicking a stacks icon will open that folder in the file browser.

Many thanks reacocard.
It looks much nice!

---

### Post by anyo409 on 2007-12-30
works great - here is a video

[http://www.youtube.com/watch?v=3W_Gw6Fl7Ns](http://www.youtube.com/watch?v=3W_Gw6Fl7Ns)

---

### Post by hhhhhx on 2007-12-30
i made my own

---

### Post by nikoPSK on 2007-12-30
> **anyo409 said:**
> works great - here is a video

[http://www.youtube.com/watch?v=3W_Gw6Fl7Ns](http://www.youtube.com/watch?v=3W_Gw6Fl7Ns)

very, very nice! Glad it worked out for you.

---

### Post by a-converted-sparky on 2007-12-31
How do u get the effect when u close windows etc ... the magical sparkly effect? i have awn manager, compiz, emerald etc all install and do not see that effect?

I am a newbie btw, go easy.

---

### Post by Vadi on 2007-12-31
System - Preferences - Advanced Desktop Effects Settings. If you don't have the option there get it here ([click]("apt:compizconfig-settings-manager")) and it'll be there.

Then find the "animations", and for the close animation experiement with a bunch. I don't remember the name of that particular effect.

---

### Post by a-converted-sparky on 2007-12-31
cheers - i must of overlooked it, their is sooo much to take in!
HAPPY XMAS by the way peeps ...and soon to be new year!

---

### Post by Lord DarkPat on 2007-12-31
PLS HELP!!!
when I run "./autogen.sh && make", it says "glib-gettext.m4" not found!!

---

### Post by Lord DarkPat on 2007-12-31
Please!! This looks painfully good (never mind the oxymoron)

---

### Post by a-converted-sparky on 2007-12-31
hi mate, i think you used the burn effect, but u must have specified over colours for the effect,

i.e
fire colour, fire particles, smoke etc ... could you let me know what values you specified and the duration of the effect, many thanks

---

### Post by ispy on 2007-12-31
I am having trouble installing on Gutsy. It keeps telling me every so often to insert the installation cd. :confused:

why would it do this?

---

### Post by nikoPSK on 2007-12-31
> **ispy said:**
> I am having trouble installing on Gutsy. It keeps telling me every so often to insert the installation cd. :confused:

why would it do this?

goto administration > software sources and then on the first tab uncheck the cd. :D

---

### Post by reacocard on 2007-12-31
> **ispy said:**
> I am having trouble installing on Gutsy. It keeps telling me every so often to insert the installation cd. :confused:

why would it do this?

in system->administration->software sources uncheck any entries for CDs/DVDs, then apt-get update and try again.

---

### Post by confused_user on 2008-01-02
Hi, after following the instructions i am unable to start the dock.

i get this when i try to run it

matt@eng20:~$ avant-window-navigator 
Screen is composited.
Segmentation fault (core dumped)

any ideas?

---

### Post by wesley_of_course on 2008-01-02
> **confused_user said:**
> Hi, after following the instructions i am unable to start the dock.

i get this when i try to run it

matt@eng20:~$ avant-window-navigator 
Screen is composited.
Segmentation fault (core dumped)

any ideas?

        Good Day !  After reading the thread this happens to  a few of us ; me included ! But Post's 
   # ' s  27 , 53 , 91,  111, 123  helped to fix my candy and its sweet . Good Luck and post back.

---

### Post by Holleywood on 2008-01-03
Thank you for this how-to, nikoPSK. Everything worked fine for me. I had tried to use kiba dock, to no avail. Anyway, thanks for this. :)

---

### Post by nikoPSK on 2008-01-03
> **wesley_of_course said:**
> Good Day ! After reading the thread this happens to a few of us ; me included ! But Post's 
# ' s 27 , 53 , 91, 111, 123 helped to fix my candy and its sweet . Good Luck and post back.
 
Thanks alot!
 
> **confused_user said:**
> Hi, after following the instructions i am unable to start the dock.
 
i get this when i try to run it
 
matt@eng20:~$ avant-window-navigator 
Screen is composited.
Segmentation fault (core dumped)
 
any ideas?
 
I would say reinstall... :(
 
> **Holleywood said:**
> Thank you for this how-to, nikoPSK. Everything worked fine for me. I had tried to use kiba dock, to no avail. Anyway, thanks for this. :)
 
No problem Holleywood. I am glad you enjoyed. PS try again on kiba... It's very fun (but pointless :p)

---

### Post by a-converted-sparky on 2008-01-04
Hi, im still having problems getting compiz to accept the overide values i enter for the burn animation, below is a screenshot

[http://img2.freeimagehosting.net/uploads/e922828519.png]("http://img2.freeimagehosting.net/uploads/e922828519.png")

if that image doesnt turn out right, the settings i have entered in the options field are:

fire_color=#9932CC, fire_particles=700,fire_smoke=1, 

do i need to prefix it with something?

can anyone help?

Many thanks

---

### Post by cartisdm on 2008-01-04
After a few tweaks I got it running and it looks great.  Personally I love the black theme.  Does anyone know where the best/easiest place to acquire new applets would be?

I also attached a screenshot so you can see my progress

---

### Post by Dark Hornet on 2008-01-04
Nice screenshot!

---

### Post by ispy on 2008-01-04
> **nikoPSK said:**
> goto administration > software sources and then on the first tab uncheck the cd. :D

Thanks, I needed that. a workaround I developed was to type "cancel" when it asked me to insert the cd, but that got kind of annoying... thanks all of you!

:)

---

### Post by Covered in Dog Hair on 2008-01-04
I'm having trouble getting this to work. I'm running 7.10 and I have followed all of your steps. But when I try to start AWN a box flashes in the upper left corner then it disappears.  So I tried to start it in terminal and this is the error it gave

zach@zach-desktop:~$ avant-window-navigator
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_shared_mem_create
zach@zach-desktop:~$ 

I've tried to find out if I'm running compiz and it says I have the files downloaded in the package manager

---

### Post by nikoPSK on 2008-01-04
> **cartisdm said:**
> After a few tweaks I got it running and it looks great.  Personally I love the black theme.  Does anyone know where the best/easiest place to acquire new applets would be?

I also attached a screenshot so you can see my progress

Applets at the awn forums and I love your screenshot.

> **Covered in Dog Hair said:**
> I'm having trouble getting this to work. I'm running 7.10 and I have followed all of your steps. But when I try to start AWN a box flashes in the upper left corner then it disappears.  So I tried to start it in terminal and this is the error it gave

zach@zach-desktop:~$ avant-window-navigator
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_shared_mem_create
zach@zach-desktop:~$ 

I've tried to find out if I'm running compiz and it says I have the files downloaded in the package manager

MAke sure you have your graphics card driver installed and then goto system > Preferences > Appearance. Then goto the Desktop Effects tab and enable one of the options. If you want to customize compiz even more get compizconfig-settings-manager in synaptic.

> **ispy said:**
> Thanks, I needed that. a workaround I developed was to type "cancel" when it asked me to insert the cd, but that got kind of annoying... thanks all of you!

:)

No Problem, We are all here to help

nikoPSK

---

### Post by war59312 on 2008-01-05
Seems to be a server issue at the moment:

> will@will-laptop:~/awn-curves$ wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
--04:54:15--  [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
           => `reacocard.asc'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... failed: Connection refused.

Any thoughts? Thanks!

---

### Post by reacocard on 2008-01-05
> **war59312 said:**
> Seems to be a server issue at the moment:



Any thoughts? Thanks!

most likely my host (tuxfamily) was just down at that time. It appears to be working fine now, so give it another try.

---

### Post by Rainz3 on 2008-01-06
I installed this using your instructions verbatim and it comes up and works but, It looks like the regular awn not the curved one :( Is there something in the manager I have to enable?

---

### Post by insidepower on 2008-01-06
> **tafsen said:**
> awn-manager 
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:188: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 168, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 188, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue


I even tried to restart my computer.

==================================================
I also having the similar problem and have solved it. 

Please refer to [http://wiki.awn-project.org/index.php?title=FAQ#How_do_I_start_AWN.3F](http://wiki.awn-project.org/index.php?title=FAQ#How_do_I_start_AWN.3F) title:  I installed AWN, but I can't run awn-manager.

AWN must be run at least once before you may run awn-manager. 

and to run it just type "avant-window-navigator &" and you will see the cool and inspiring awn pop out... 

and awn-manager run correctly afterwards!!

cheers =)

---

### Post by Swmmrman on 2008-01-07
> **Rainz3 said:**
> I installed this using your instructions verbatim and it comes up and works but, It looks like the regular awn not the curved one :( Is there something in the manager I have to enable?

Just go into awn manager and make sure curves look is selected.  If you cant select curves look.  You may need to install again.

---

### Post by Maikelv on 2008-01-07
I have a problem, The "curves" option does not shop up , I just get flat & 3d. AWN works though....

---

### Post by Swmmrman on 2008-01-07
I get that first install attempt everytime.  I just remove and try again.  Second time it works.  Not sure exaclty why.
Not sure if its relevant.  But this occurs everytimg on 64 but not 32.  From my experience

---

### Post by nikoPSK on 2008-01-07
> **Rainz3 said:**
> I installed this using your instructions verbatim and it comes up and works but, It looks like the regular awn not the curved one :( Is there something in the manager I have to enable?

goto the theme and select curved look.

> **Swmmrman said:**
> I get that first install attempt everytime.  I just remove and try again.  Second time it works.  Not sure exaclty why.
Not sure if its relevant.  But this occurs everytimg on 64 but not 32.  From my experience

don't know what it the real issue here as I a 32 bit.

---

### Post by a-converted-sparky on 2008-01-08
> **Maikelv said:**
> I have a problem, The "curves" option does not shop up , I just get flat & 3d. AWN works though....

I had this problem, i had to redo this bit:

bzr co [http://bazaar.launchpad.net/~awn-cur...awn/awn-curves](http://bazaar.launchpad.net/~awn-cur...awn/awn-curves) awn-curves

complied and installed it,now  all options available

---

### Post by nikef on 2008-01-09
Hi Niko
sorry to bother you

but my awn dock keeps disappearing,after so many hours on the pc  :(

i dont know how to get it back,so i just reboot my pc 

do you have any ideas ?

---

### Post by nikoPSK on 2008-01-09
> **nikef said:**
> Hi Niko
sorry to bother you
 
but my awn dock keeps disappearing,after so many hours on the pc :(
 
i dont know how to get it back,so i just reboot my pc 
 
do you have any ideas ?
 
That has been a revelent problem... could be just awn. Does something special happen before or after? Like do you run a certain app or do something that makes it dissapear? Run it from the terminal, and when it crashes, give us the output please.
 
nikoPSK

---

### Post by Vadi on 2008-01-09
After it dissappears, press alt+f2, type in "avant-window-navigator", and it'll appear again.

No need to reboot :)

---

### Post by nikoPSK on 2008-01-09
> **Vadi said:**
> After it dissappears, press alt+f2, type in "avant-window-navigator", and it'll appear again.

No need to reboot :)

Thank you vadi, adding so to the guide (though it's pretty apparent, isn't it? :p)

---

### Post by narx on 2008-01-11
was wondering,

if i have installed awn through apt, and if i checkout awn from bzr and installed it, will it cause any problems?

i wrecked awn before, and this time i m gonna ask before doing anything risky..

---

### Post by confused_user on 2008-01-11
> **nikoPSK said:**
> Thanks alot!
 

 
I would say reinstall... :(
 

 
No problem Holleywood. I am glad you enjoyed. PS try again on kiba... It's very fun (but pointless :p)

I deleted everything, uninstalled everything, followed the guide again, and now it works :guitar:

Weird, i've set this up on a couple of machines now and this was the only one that gave me ****.

---

### Post by lolzlolz on 2008-01-11
ok  the way you tell us to uninstall doesn't work for me, i have tried multiple times to no avail :(
any idea why because i can always go back and open awn 
what should i do?

---

### Post by nikoPSK on 2008-01-11
> **narx said:**
> was wondering,

if i have installed awn through apt, and if i checkout awn from bzr and installed it, will it cause any problems?

i wrecked awn before, and this time i m gonna ask before doing anything risky..

Shouldn't harm your system :D

> **confused_user said:**
> I deleted everything, uninstalled everything, followed the guide again, and now it works :guitar:

Weird, i've set this up on a couple of machines now and this was the only one that gave me ****.

I find that the reinstall always works (though I've never had awn not work...:confused:)

> **lolzlolz said:**
> ok  the way you tell us to uninstall doesn't work for me, i have tried multiple times to no avail :(
any idea why because i can always go back and open awn 
what should i do?

I tell you to remove the awn-curves folder and run that comment. If you want you can uninstall all remaining unimportant pieces from synaptic.

---

### Post by lolzlolz on 2008-01-11
ok i'll try again

---

### Post by kobinasucks on 2008-01-11
> **Covered in Dog Hair said:**
> I'm having trouble getting this to work. I'm running 7.10 and I have followed all of your steps. But when I try to start AWN a box flashes in the upper left corner then it disappears.  So I tried to start it in terminal and this is the error it gave

zach@zach-desktop:~$ avant-window-navigator
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_shared_mem_create
zach@zach-desktop:~$ 

I've tried to find out if I'm running compiz and it says I have the files downloaded in the package manager

I'm getting the exact same error message as Zach. Regarding the graphics card driver installed, I have one of those the troublesome ATI Radeon ones which I have restricted to use the internal Ubuntu one (I think that's what I've done. Sorry: NOOB). How exactly am I meant to customize Compiz. I know how to open Advanced Desktop Effects but what exactly am I supposed to adjust in there?

---

### Post by kobinasucks on 2008-01-11
Goodness, I'm an idiot.

Turns out my error is completely different. Ahem... sorry.

Mine goes:

kobinagraham@kobinagraham-laptop:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/switcher.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_shared_mem_create

And then nothing shows up. I'm using Kiba Dock to get by but I'd be so grateful if you could help me get my beloved AWN back with curves or without!

---

### Post by nikoPSK on 2008-01-11
> **kobinasucks said:**
> Goodness, I'm an idiot.
 
Turns out my error is completely different. Ahem... sorry.
 
Mine goes:
 
kobinagraham@kobinagraham-laptop:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/switcher.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_shared_mem_create
 
And then nothing shows up. I'm using Kiba Dock to get by but I'd be so grateful if you could help me get my beloved AWN back with curves or without!
 
could you try a reinstall please?
 
Thanks!

---

### Post by bscasta on 2008-01-11
Ok I'm a newbie so be easy on me. I have done all on first page. now if i try to run avant-window-manager i get 
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
when I try to type in compiz i get:
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by lolzlolz on 2008-01-11
not an error for here, post error in all desktop effects post along with ur graphics card, someone should be able to help you but this thread is just about awn curves

ps. niko i got it working, it works perfect when i retried

---

### Post by Covered in Dog Hair on 2008-01-11
I have an ATI Radion graphics card and under restricted drivers it says that I have the correct drivers installed and enabled. I went to apperance preferences and there was no tab for desktop effects, just theme, backround, fonts, interface, and visual effects. Then I went to synaptic and the compizconfig-settings-manager was installed. So I tried to reinstall the compiz and the Awn curves and I still get the same error message.

---

### Post by XP-FREAK on 2008-01-11
Thank you, this looks really great.
Can't wait to try this out :)

---

### Post by lolzlolz on 2008-01-11
@covered in dog hair
once again this isn't desktop troubleshooting post in all desktop effects not here only post errors installing awn curves here, noone will be able to help you with that here
thanks

---

### Post by nikoPSK on 2008-01-11
> **XP-FREAK said:**
> Thank you, this looks really great.
Can't wait to try this out :)
 
Hope you'll enjoy
 
> **lolzlolz said:**
> not an error for here, post error in all desktop effects post along with ur graphics card, someone should be able to help you but this thread is just about awn curves
 
ps. niko i got it working, it works perfect when i retried
 
It's fine, don't moderate this thread for me please:KS. I can answer some basic compiz related and other questions, don't make users feel unwanted please. It's best to point them to a guide and say maybe that might help, or try starting a thread on it.
 
Glad you got it working
nikoPSK
 
> **bscasta said:**
> Ok I'm a newbie so be easy on me. I have done all on first page. now if i try to run avant-window-manager i get 
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
when I try to type in compiz i get:
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
 
You'll have to enable compiz. I am guessing you're in gutsy, so basically just get drivers then start compiz by going to System, Preferences, Appearance.
 
Then goto the Desktop effects tab. If you want ecen more customization install [compizconfig-settings-manager]("apt:compizconfig-settings-manager") (click)

---

### Post by XP-FREAK on 2008-01-11
> **nikoPSK said:**
> Hope you'll enjoy

Yes, I do :)

[http://myBlackbox.net/awn_curve.jpeg](http://myBlackbox.net/awn_curve.jpeg)

(better added a link than an image, it's a bit too large)

---

### Post by nikoPSK on 2008-01-11
> **XP-FREAK said:**
> Yes, I do :)

[http://myBlackbox.net/awn_curve.jpeg](http://myBlackbox.net/awn_curve.jpeg)

(better added a link than an image, it's a bit too large)

I like it very much. I think you can make thumbnails for images (actually I know you can, but I don't know how to...)

Glad it worked without a hitch,
nikoPSK

---

### Post by war59312 on 2008-01-12
> **reacocard said:**
> most likely my host (tuxfamily) was just down at that time. It appears to be working fine now, so give it another try.Indeed, OK trying again. wow their server is really slow atm, average of 12.6kB/s.

Ok installed just fine, thanks

um but cant move it so it seems :(

---

### Post by nikoPSK on 2008-01-12
> **war59312 said:**
> Indeed, ok trying again. wow their server is really slow atm, average of 12.6kB/s.

Ok um, there are no themes... odd

themes come in my second post. Enjoy.

---

### Post by nikoPSK on 2008-01-12
Like what I mean is they are on page one at the second post. :KS

---

### Post by legolas_w on 2008-01-12
hi
thank you for reading my post
I am trying to complete the first post instruction but 
```

bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves

```
can not get completed and it stops on 1/4 phase.

Can some one please let me know whether the instruction has changed or something else is wrong?

Thanks.

---

### Post by nikoPSK on 2008-01-12
> **legolas_w said:**
> hi
thank you for reading my post
I am trying to complete the first post instruction but 
```

bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves

```can not get completed and it stops on 1/4 phase.

Can some one please let me know whether the instruction has changed or something else is wrong?

Thanks.

just wait. It doesn't hang. Have patience. :)

nikoPSK

---

### Post by giok13 on 2008-01-12
wen i try to do the second part i get this

 bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves
bzr: ERROR: Target directory "awn-curves" already exists.



so i skipped tht part and went on but it didnt work. and i tried to search for awn curves but could not find it. 

edti well now i somehow got it to work but now i get this

```
The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr155-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages

```

---

### Post by nikoPSK on 2008-01-12
when it says target directory already exists, delete the "awn-curves" folder from your home folder. I can't stress this enough, don't skip commands, every one is useful for the installation of awn curves. 

:)
nikoPSK

---

### Post by legolas_w on 2008-01-12
> **nikoPSK said:**
> just wait. It doesn't hang. Have patience. :)

nikoPSK

Thank you for comment,
problem is that it when i try to open that url in the browser it says:


Not Found

The requested URL /00/00/14/75 was not found on this server.


is it usual?

thanks.

---

### Post by nikoPSK on 2008-01-12
> **legolas_w said:**
> Thank you for comment,
problem is that it when i try to open that url in the browser it says:


Not Found

The requested URL /00/00/14/75 was not found on this server.


is it usual?

thanks.

The server is down I guess. You might want to brew some coffee in the meantime. :)

---

### Post by giok13 on 2008-01-12
well i solved the other problem but now i get this

~/awn-curves$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr

---

### Post by nikoPSK on 2008-01-12
> **giok13 said:**
> well i solved the other problem but now i get this

~/awn-curves$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr

did you add the avant window navigator repositories like in my guide?

nikoPSK

---

### Post by giok13 on 2008-01-12
i just needed to update the synaptic manager manually. but thx anyways. good tut too :)

and i got a question do u know how to do the awn in this video, to make it like tht. [http://www.youtube.com/watch?v=ZD7QraljRfM](http://www.youtube.com/watch?v=ZD7QraljRfM)

or if u know anything on how to make any of the things tht r show in the video would help me out alot. for example. the 3-d back ground, the transperant cube and anything else thts shown in the video. 
thx again

---

### Post by nikoPSK on 2008-01-12
> **giok13 said:**
> i just needed to update the synaptic manager manually. but thx anyways. good tut too :)

and i got a question do u know how to do the awn in this video, to make it like tht. [http://www.youtube.com/watch?v=ZD7QraljRfM](http://www.youtube.com/watch?v=ZD7QraljRfM)

or if u know anything on how to make any of the things tht r show in the video would help me out alot. for example. the 3-d back ground, the transperant cube and anything else thts shown in the video. 
thx again

[gtk-recordmydesktop]("apt:gtk-recordmydesktop") is nice (click) I use it. :)

~/nikoPSK

---

### Post by lolzlolz on 2008-01-13
the dock in that video is called kiba-dock it isn't possible to do that with awn

---

### Post by nikoPSK on 2008-01-13
Oh, the rest is compiz... :)

---

### Post by legolas_w on 2008-01-13
Is the server still  down ?
I am getting the same error, is there any other  way to perform 
```

> bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves

```


Thanks.

---

### Post by SweetInsanity on 2008-01-13
Hello all, I've just installed everything except the themes 'cos the server is down.
Now, awn works great but the synaptic gives me an error of broken dependences (avant-window-navigator-bzr, awn-core-applets-bzr and python-libawn-bzr). I tried to reinstall the broken dependences but it gives me some kind of error. 
Writing "avant-window-navigator" in the terminal gives me this error: 
> (awn-applet-activation:20846): Gtk-WARNING **: Theme directory scalable/places/22 of theme black-white_2-Neon has no size field


** (avant-window-navigator:20842): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:20842): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

writing "awn-manager" doesn't return any error.

So, i followed every step of the guide. What's wrong with this?

Oh, I have an nvidia go geforce 7300 and i'm on a laptop.

Btw, sorry for the english.

---

### Post by legolas_w on 2008-01-13
How I can configure it to start automatically when i start the linux?
I have ubuntu 7.10.
Thanks.

---

### Post by kankon on 2008-01-13
thank you very mush

i'm done with AWN and install

---

### Post by nikoPSK on 2008-01-13
> **legolas_w said:**
> Is the server still  down ?
I am getting the same error, is there any other  way to perform 
```

> bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves

```
Thanks.

I guess the server is still down. I don't really know whats up. I could grab the folder when I get home and upload it :confused:

> **SweetInsanity said:**
> Hello all, I've just installed everything except the themes 'cos the server is down.
Now, awn works great but the synaptic gives me an error of broken dependences (avant-window-navigator-bzr, awn-core-applets-bzr and python-libawn-bzr). I tried to reinstall the broken dependences but it gives me some kind of error. 
Writing "avant-window-navigator" in the terminal gives me this error: 

writing "awn-manager" doesn't return any error.

So, i followed every step of the guide. What's wrong with this?

Oh, I have an nvidia go geforce 7300 and i'm on a laptop.

Btw, sorry for the english.

Your english is fine :). Well, I would say, follow my instructions on removing and try again.

> **legolas_w said:**
> How I can configure it to start automatically when i start the linux?
I have ubuntu 7.10.
Thanks.

goto System->Preferences->Sessions and add the following command once you click new:

avant-window-navigator

Not to sound rude, but, it's on the main page of my guide:)

> **kankon said:**
> thank you very mush

i'm done with AWN and install

Glad you like.

---

### Post by giok13 on 2008-01-13
> **lolzlolz said:**
> the dock in that video is called kiba-dock it isn't possible to do that with awn

kk thx ill check intto tht cause the awn docks been givin me some problems cause im running on a restrickted driver :(

---

### Post by nikoPSK on 2008-01-13
> **giok13 said:**
> kk thx ill check intto tht cause the awn docks been givin me some problems cause im running on a restrickted driver :(

that doesn't affect anything. Restricted means basically in linux terms, basically means proprietary. It's fine. And kiba won't be much different than awn, as kiba is a bit of a memory hog.

---

### Post by giok13 on 2008-01-13
> **nikoPSK said:**
> that doesn't affect anything. Restricted means basically in linux terms, basically means proprietary. It's fine. And kiba won't be much different than awn, as kiba is a bit of a memory hog.

wat i ment by problems is tht the awn hides behind my windows and wont come up. so i have to minimize my windows in order to find it. i like it alot but its getting frasturating cause sometimes it works sometimes it doesnt

---

### Post by nikoPSK on 2008-01-13
> **giok13 said:**
> wat i ment by problems is tht the awn hides behind my windows and wont come up. so i have to minimize my windows in order to find it. i like it alot but its getting frasturating cause sometimes it works sometimes it doesnt

In the awn manager, under bar behavior, make sure the first two aren't checked. Also, could you please talk a little more english? No offense, but I don't really understand your slang so much. If what you mean is it hides behind the gnome panel at the bottom, just remove the panel or put it somewhere else. You can put applets on the top panel too. :)

---

### Post by legolas_w on 2008-01-13
Hi
Thank you very much.
I have install it and it works very good :D
I hope they get it into distribution in 8.04, this way updating will be easier :).
I even installed one theme, can you let me know where i can find more theme?
the official web site has 8-9 theme which are not so much.



Thanks again, keep this nice application up and going.

---

### Post by nikoPSK on 2008-01-13
> **legolas_w said:**
> Hi
Thank you very much.
I have install it and it works very good :D
I hope they get it into distribution in 8.04, this way updating will be easier :).
I even installed one theme, can you let me know where i can find more theme?
the official web site has 8-9 theme which are not so much.



Thanks again, keep this nice application up and going.

you installed one theme. the themes I have are here:
[http://ubuntuforums.org/showpost.php?p=3524312&postcount=2](http://ubuntuforums.org/showpost.php?p=3524312&postcount=2)

You can create your own, there aren't many curves themes out there. :)

nikoPSK

---

### Post by narx on 2008-01-13
nikoPSK,
thanks man, will give it a try..

---

### Post by giok13 on 2008-01-13
i like kiba dock better cause the physics thing on it

---

### Post by Sephoroth on 2008-01-13
> **giok13 said:**
> i like kiba dock better cause the physics thing on it

I myself use Kiba-Dock most of the time (AWN is forced on the bottom edge only and I prefer using window miniatures) but Akamaru hasn't been working properly for quite some time.

---

### Post by SweetInsanity on 2008-01-13
> **nikoPSK said:**
> I guess the server is still down. I don't really know whats up. I could grab the folder when I get home and upload it :confused:



Your english is fine :). Well, I would say, follow my instructions on removing and try again.

Ok, i removed everything and reinstalled. Everything cool, but now i don't have the "awn manager" so I can't go in the option, and the server is still down. So, it's because of the server that i don't have the awn manager? Did I miss something in the installation?

Edit: sorry, just needed to restart awn. Ok, now it seem to works.
Btw why the server is still down? <.<
Well, thx anyway ^_^

---

### Post by nikoPSK on 2008-01-13
> **narx said:**
> nikoPSK,
thanks man, will give it a try..

No problem.

> **giok13 said:**
> i like kiba dock better cause the physics thing on it

> **Sephoroth said:**
> I myself use Kiba-Dock most of the time (AWN is forced on the bottom edge only and I prefer using window miniatures) but Akamaru hasn't been working properly for quite some time.

Yes, well this is an awn thread. :)

> **SweetInsanity said:**
> Ok, i removed everything and reinstalled. Everything cool, but now i don't have the "awn manager" so I can't go in the option, and the server is still down. So, it's because of the server that i don't have the awn manager? Did I miss something in the installation?

Edit: sorry, just needed to restart awn. Ok, now it seem to works.
Btw why the server is still down? <.<
Well, thx anyway ^_^

Does awn manager open with this? 

```
awn-manager
```

---

### Post by narx on 2008-01-13
Just installed it.
This is fantastic..

So far not having any problems with the server.

---

### Post by nikoPSK on 2008-01-13
> **narx said:**
> Just installed it.
This is fantastic..

So far not having any problems with the server.

I am glad you enjoy it. Server is back up, every thing's fine! :D

nikoPSK

---

### Post by -grubby on 2008-01-14
Er as far as I understand AWN needs a compositor to start. So I installed xcompmgr (for use with Flubox, of course) and I start it with the -c and -f arguments (look on the man page for details). But the problem is that is starts but it takes up about a third of the screen with a giant black spot. Also, it acts as a window (it doesn't have a title bar or anything but if I press alt and click on it I can move it around as a window). So is it a xcompmgr problem or an AWN problem or what?

---

### Post by nikoPSK on 2008-01-14
> **nathangrubb said:**
> Er as far as I understand AWN needs a compositor to start. So I installed xcompmgr (for use with Flubox, of course) and I start it with the -c and -f arguments (look on the man page for details). But the problem is that is starts but it takes up about a third of the screen with a giant black spot. Also, it acts as a window (it doesn't have a title bar or anything but if I press alt and click on it I can move it around as a window). So is it a xcompmgr problem or an AWN problem or what?

xcompmanager is a composter, so yes it should work. By blob does it go like around 5 centimeters high? It is most likely dead then... a reinstall I suppose? 

nikoPSK

---

### Post by -grubby on 2008-01-14
> **nikoPSK said:**
> xcompmanager is a composter, so yes it should work. By blob does it go like around 5 centimeters high? It is most likely dead then... a reinstall I suppose? 

nikoPSK

yah around 5 cm high. I was previously having problems with compiz (it was all glitchy but fixed that up). I don't think I need to do something as drastic as reinstalling

---

### Post by nikoPSK on 2008-01-14
> **nathangrubb said:**
> yah around 5 cm high. I was previously having problems with compiz (it was all glitchy but fixed that up). I don't think I need to do something as drastic as reinstalling

I think a re-installation is due for massive blobs, for the record, can i have screenshot?

nikoPSK

---

### Post by -grubby on 2008-01-14
> **nikoPSK said:**
> I think a re-installation is due for massive blobs, for the record, can i have screenshot?

nikoPSK

Sure. [Here's]("http://img33.picoodle.com/img/img33/4/1/13/f_awnsm_13cd4ed.png") the link

---

### Post by nikoPSK on 2008-01-14
WOW, okay... reinstall please.

Best,
nikoPSK

---

### Post by -grubby on 2008-01-14
> **nikoPSK said:**
> WOW, okay... reinstall please.

Best,
nikoPSK

Na I don't need AWN that bad. FBpanel works

---

### Post by nikoPSK on 2008-01-14
> **nathangrubb said:**
> Na I don't need AWN that bad. FBpanel works

But, I would like you to get it working... :lolflag: could you jsut try a reinstall for me?

nikoPSK

---

### Post by -grubby on 2008-01-14
er well now I uninstalled it but I forgot to use the --purge option and now I can't find where it's preferences are so I can delete them?

---

### Post by nikoPSK on 2008-01-14
> **nathangrubb said:**
> er well now I uninstalled it but I forgot to use the --purge option and now I can't find where it's preferences are so I can delete them?

I think you can leave preferences for now. :) Reinstall and you should be okie dokie. :p

Best,
nikoPSK

---

### Post by -grubby on 2008-01-14
> **nikoPSK said:**
> I think you can leave preferences for now. :) Reinstall and you should be okie dokie. :p

Best,
nikoPSK

well I don't have to reinstall to get rid of preferences. Anyway, I found where the preferences are stored

---

### Post by nikoPSK on 2008-01-14
> **nathangrubb said:**
> well I don't have to reinstall to get rid of preferences. Anyway, I found where the preferences are stored

okay, but you uninstalled, now you can reinstall to get it working. :)

---

### Post by kankon on 2008-01-14
very very cool thanks agin

[CENTER][IMG]http://www.kankon.us/upload/Screenshotkankon.png[/IMG][/CENTER]

---

### Post by nikoPSK on 2008-01-14
No problem, I see you chose human curves. :)
 
nikoPSK

---

### Post by gr8dane on 2008-01-14
sudo apt-get install bzr m4 gnome-common

Here is what I get when I type this into terminal.

Package bzr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bzr has no installation candidate


What did I do wrong?

---

### Post by nikoPSK on 2008-01-14
> **gr8dane said:**
> sudo apt-get install bzr m4 gnome-common

Here is what I get when I type this into terminal.

Package bzr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bzr has no installation candidate


What did I do wrong?

you are missing repositories... :|

---

### Post by shafin on 2008-01-15
Thanks to your instruction, I've got it working :)

---

### Post by nikoPSK on 2008-01-15
Glad you enjoyed. :)

---

### Post by shafin on 2008-01-15
I liked the glass theme for 3d AWN,so tried to make something similar for the Awn-curve also:
[[img]http://img2.freeimagehosting.net/uploads/794f70cad3.png[/img]](http://www.freeimagehosting.net/)

[Link for Theme File]("http://mahdee.jameel.googlepages.com/Glass.tgz")

---

### Post by nikoPSK on 2008-01-15
> **shafin said:**
> I liked the glass theme for 3d AWN,so tried to make something similar for the Awn-curve also:
[[IMG]http://img2.freeimagehosting.net/uploads/794f70cad3.png[/IMG]]("http://www.freeimagehosting.net/")

[Link for Theme File]("http://mahdee.jameel.googlepages.com/Glass.tgz")

ooh, can I have it? I'll put it up for download. :)

nikoPSK

---

### Post by shafin on 2008-01-15
Sure,the link is there.

---

### Post by chips24 on 2008-01-15
im creating one!

---

### Post by nikoPSK on 2008-01-15
> **shafin said:**
> Sure,the link is there.

I cannot provide a screenshot because the theme is not loading.  :(

---

### Post by shafin on 2008-01-15
Weired,it works fine for me.

BTW,I think you can create one yourself. I just changed the colors in the Glass engine tab in AWN manager for the Milk theme and made them more transparent and whitish,and used more transparent borders in the Bar appearance tab.

The font used is Bradley Hand ITC Bold -16.

---

### Post by nikoPSK on 2008-01-15
> **shafin said:**
> Weired,it works fine for me.

BTW,I think you can create one yourself. I just changed the colors in the Glass engine tab in AWN manager for the Milk theme and made them more transparent and whitish,and used more transparent borders in the Bar appearance tab.

The font used is Bradley Hand ITC Bold -16.

nvm, got it, looks nice. Posting the screeny. :)

---

### Post by Supertonic on 2008-01-20
Hello I have recently tried to install the awn curves, and I am running into a strange road block.

I run the command:
```
 sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev 
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves 
```

and then I get this readout:
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
autotools-dev is already the newest version.
autotools-dev set to manual installed.
libxdamage-dev is already the newest version.
libxcomposite-dev is already the newest version.
libgnome2-common is already the newest version.
libgnome2-dev is already the newest version.
libgnome-desktop-dev is already the newest version.
libgtk2.0-dev is already the newest version.
libgtk2.0-dev set to manual installed.
libwnck-dev is already the newest version.
libgconf2-dev is already the newest version.
libgconf2-dev set to manual installed.
libglib2.0-dev is already the newest version.
libdbus-glib-1-dev is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
python-dev is already the newest version.
python-dev set to manual installed.
python-gtk2-dev is already the newest version.
python-cairo-dev is already the newest version.
python-gconf is already the newest version.
python-gnome2-dev is already the newest version.
The following extra packages will be installed:
  gconf indent libgconf-dev libgconf11 libglib1.2 libglib1.2-dev
  libgnome-vfs-common libgnome-vfs0 libgtk1.2 libgtk1.2-common liboaf-dev
  liboaf0 liborbit-dev liborbit0 libwrap0-dev libxml1 oaf
Suggested packages:
  nfs-common gnome-vfs-extfs
Recommended packages:
  orbit
The following NEW packages will be installed:
  gconf indent libgconf-dev libgconf11 libglib1.2 libglib1.2-dev
  libgnome-vfs-common libgnome-vfs-dev libgnome-vfs0 libgtk1.2
  libgtk1.2-common liboaf-dev liboaf0 liborbit-dev liborbit0 libwrap0-dev
  libxml1 oaf
0 upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 3675kB of archives.
After unpacking 13.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

```   

I have no idea why it is aborting after I say yes.  If anyone has any ideas, please let me know.  I would love to get this up and running as I already have compiz-fusion running beautifully.  
         Thanks!

---

### Post by Vadi on 2008-01-20
Tried lowercase y? That's what I always use.

---

### Post by nikoPSK on 2008-01-21
> **Vadi said:**
> Tried lowercase y? That's what I always use.

that's good. Although I think he did. My guide does say to refrain copying all the lines at once on that one section. :)

---

### Post by SomeGuyDude on 2008-01-23
Hey, I've noticed a little bug in AWN-curves. I'm not sure if you wrote the program or if this is just a guide for it, but the rightmost icon, whenever the bar-resizes (such as when a window opens or closes) is "jutted up" about a half inch or so, and then goes down only when I mouseover it.

It's a small thing, but since it screws up the shape of the titular "curve", it drives me nuts.

---

### Post by Vadi on 2008-01-23
I get the same when I move cube edges back and forth, the icon alignment goes way out.

Unfortunately the AWN curves author has been too busy for several months now..

---

### Post by nikoPSK on 2008-01-23
> **SomeGuyDude said:**
> Hey, I've noticed a little bug in AWN-curves. I'm not sure if you wrote the program or if this is just a guide for it, but the rightmost icon, whenever the bar-resizes (such as when a window opens or closes) is "jutted up" about a half inch or so, and then goes down only when I mouseover it.
 
It's a small thing, but since it screws up the shape of the titular "curve", it drives me nuts.
 
I do know this, not a dev yet, but working on learning awn a bit more. :)
 
> **Vadi said:**
> I get the same when I move cube edges back and forth, the icon alignment goes way out.
 
Unfortunately the AWN curves author has been too busy for several months now..
 
Meek is tied up with life... :p

---

### Post by Kinfule on 2008-01-24
Thanks for your post it was very easy to install AWN with it and, it looks great.

---

### Post by nikoPSK on 2008-01-24
> **Kinfule said:**
> Thanks for your post it was very easy to install AWN with it and, it looks great.

I am glad you enjoyed.

---

### Post by Kinfule on 2008-01-24
Well I got a little problem, and a question :P

1) I use Kubuntu Gutsy and I can only open AWN by a console (clicking the kmenu or alt+f2 won't work) any idea?

A) Any idea on how to load it on boot? :P

Thanks again

---

### Post by nikoPSK on 2008-01-24
I don't know KDE that well... for load on boot, is there a sessions like thing in kubuntu?

---

### Post by PeterJS on 2008-01-24
Niko! It's broken! Save me buddy. Here are the logs from the build:

[http://oregonstate.edu/~sandinp/Ubuntu/AWN-Curve/autogen.log](http://oregonstate.edu/~sandinp/Ubuntu/AWN-Curve/autogen.log)
[http://oregonstate.edu/~sandinp/Ubuntu/AWN-Curve/make.log](http://oregonstate.edu/~sandinp/Ubuntu/AWN-Curve/make.log)
[http://oregonstate.edu/~sandinp/Ubuntu/AWN-Curve/checkinstall.log](http://oregonstate.edu/~sandinp/Ubuntu/AWN-Curve/checkinstall.log)

---

### Post by nikoPSK on 2008-01-25
> **PeterJS said:**
> Niko! It's broken! Save me buddy. Here are the logs from the build:

[http://oregonstate.edu/~sandinp/Ubuntu/AWN-Curve/autogen.log]("http://oregonstate.edu/%7Esandinp/Ubuntu/AWN-Curve/autogen.log")
[http://oregonstate.edu/~sandinp/Ubuntu/AWN-Curve/make.log]("http://oregonstate.edu/%7Esandinp/Ubuntu/AWN-Curve/make.log")
[http://oregonstate.edu/~sandinp/Ubuntu/AWN-Curve/checkinstall.log]("http://oregonstate.edu/%7Esandinp/Ubuntu/AWN-Curve/checkinstall.log")

well, mainly I see: 
```
could not create temporary file whilst writing archive: No more archived files
```

well, did you lock a directory or something?

---

### Post by PeterJS on 2008-01-25
> **nikoPSK said:**
> well, mainly I see: 
```
could not create temporary file whilst writing archive: No more archived files
```

well, did you lock a directory or something?
Personal and intentionally, no, might it be something that's done as part of the checkinstall process, couldn't tell you I've never studied it's inner workings. Check install is running as root, it should be able to do whatever it needs to do to build me my deb.

---

### Post by nikoPSK on 2008-01-25
hrm, no deb building required. :) you should be able to follow the instructions par say.

---

### Post by PeterJS on 2008-01-25
> **nikoPSK said:**
> hrm, no deb building required. :) you should be able to follow the instructions par say.

I like to keep my system neat and tidy so I always use checkinstall instead of make install. But I'll give plain old make install a go.

Ok, that's not cool. Make install works, but for some reason it refuses to build a deb package. It's installed, I'm just not happy about it.

---

### Post by nikoPSK on 2008-01-25
> **PeterJS said:**
> I like to keep my system neat and tidy so I always use checkinstall instead of make install. But I'll give plain old make install a go.

Ok, that's not cool. Make install works, but for some reason it refuses to build a deb package. It's installed, I'm just not happy about it.

lol, when I tried making a deb for awn curves back around a month ago it never worked.... So I see how you got frustrated too.

---

### Post by Ebuntor on 2008-01-25
Hi,

The thread is way too long to read entirely so sorry if this has been asked before.

I installed awn-curves, I can select it under " Bar Appearance" . However when I select it the bar looks just like the "3D look" . 

If I can select the "Curves Look" doesn't that mean it should be installed?
What did I do wrong?

---

### Post by nikoPSK on 2008-01-25
> **Ebuntor said:**
> Hi,
 
The thread is way too long to read entirely so sorry if this has been asked before.
 
I installed awn-curves, I can select it under " Bar Appearance" . However when I select it the bar looks just like the "3D look" . 
 
If I can select the "Curves Look" doesn't that mean it should be installed?
What did I do wrong?
 
no, no it's fine; basically just refresh the var, or if not, close awn, select the theme, apply it and start awn again. :)

---

### Post by Ebuntor on 2008-01-25
> **nikoPSK said:**
> no, no it's fine; basically just refresh the var, or if not, close awn, select the theme, apply it and start awn again. :)

That worked, looks great, thanks. :)

---

### Post by Ebuntor on 2008-01-25
Just one other question: Is it possible to move the icons a bit lower on the bar, like the icon offset option? If I maximize my windows the icons are so high they cover the window too much. I can provide a screenshot if I'm being too vague.

---

### Post by nikoPSK on 2008-01-25
> **Ebuntor said:**
> That worked, looks great, thanks. :)
 
Just one other question: Is it possible to move the icons a bit lower on the bar, like the icon offset option? If I maximize my windows the icons are so high they cover the window too much. I can provide a screenshot if I'm being too vague. 
 
well, glad you enjoy, icon offset makes them lower or higher. :)

---

### Post by Ebuntor on 2008-01-25
> **nikoPSK said:**
> well, glad you enjoy, icon offset makes them lower or higher. :)

Yeah I know, that is why I was asking if there's a option similar to the " icon offset"  for the curves look? For "flat bar" and "3d look" there the icon offset option, for "curves look" there isn't.

---

### Post by nikoPSK on 2008-01-25
> **Ebuntor said:**
> Yeah I know, that is why I was asking if there's a option similar to the " icon offset" for the curves look? For "flat bar" and "3d look" there the icon offset option, for "curves look" there isn't.
 
should be... I'll check when I get home. :)

---

### Post by Ebuntor on 2008-01-25
> **nikoPSK said:**
> should be... I'll check when I get home. :)

Ok, thank you. :)

---

### Post by nikoPSK on 2008-01-25
> **Ebuntor said:**
> Ok, thank you. :)
 
there is a thank you option. :) it's jsut I am on windows right now, so once I get home and have finished all housework (piano etc) I'll get to you asap

---

### Post by erwall on 2008-01-25
I get the following when I run:

```
./autogen.sh
```

```
checking for PYGTK... ./configure: line 20753: 30508 Segmentation fault      (core dumped) ( $PKG_CONFIG --exists --print-errors "pygtk-2.0 >= 2.8.0" ) 2>&5
./configure: line 20771: 30513 Segmentation fault      (core dumped) ( $PKG_CONFIG --exists --print-errors "pygtk-2.0 >= 2.8.0" ) 2>&5
configure: error: Package requirements (pygtk-2.0 >= 2.8.0) were not met:

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

When I run

```
dpkg -l | grep python-gtk2
```

I get

```
ii  python-gtk2                                2.12.0-0ubuntu2                           Python bindings for the GTK+ widget set
ii  python-gtk2-dbg                            2.12.0-0ubuntu2                           Python bindings for the GTK+ widget set (deb
ii  python-gtk2-dev                            2.12.0-0ubuntu2                           GTK+ bindings: devel files
```

Any ideas?

---

### Post by Kinfule on 2008-01-25
No else has the problem of being able to open awn curve only by a console?

---

### Post by nikoPSK on 2008-01-25
> **Kinfule said:**
> No else has the problem of being able to open awn curve only by a console?

Sorry, what? output? :)

> **erwall said:**
> I get the following when I run:

```
./autogen.sh
``````
checking for PYGTK... ./configure: line 20753: 30508 Segmentation fault      (core dumped) ( $PKG_CONFIG --exists --print-errors "pygtk-2.0 >= 2.8.0" ) 2>&5
./configure: line 20771: 30513 Segmentation fault      (core dumped) ( $PKG_CONFIG --exists --print-errors "pygtk-2.0 >= 2.8.0" ) 2>&5
configure: error: Package requirements (pygtk-2.0 >= 2.8.0) were not met:

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```When I run

```
dpkg -l | grep python-gtk2
```I get

```
ii  python-gtk2                                2.12.0-0ubuntu2                           Python bindings for the GTK+ widget set
ii  python-gtk2-dbg                            2.12.0-0ubuntu2                           Python bindings for the GTK+ widget set (deb
ii  python-gtk2-dev                            2.12.0-0ubuntu2                           GTK+ bindings: devel files
```Any ideas?

hrm? 

> **nikoPSK said:**
> there is a thank you option. :) it's jsut I am on windows right now, so once I get home and have finished all housework (piano etc) I'll get to you asap

it should be icon height. works for me

---

### Post by TolTime on 2008-01-25
I'm having a problem, when i get to the point where i have to add this

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

it won't let me save the source list, I'm assuming that I'm not in root?
I'm a noob to Ubuntu and Linux in general.  any help would be great

---

### Post by Ebuntor on 2008-01-25
> **TolTime said:**
> I'm having a problem, when i get to the point where i have to add this

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

it won't let me save the source list, I'm assuming that I'm not in root?
I'm a noob to Ubuntu and Linux in general.  any help would be great

Yeah, you have to be in root to do that. Make sure you add  **gksudo** to the command.
```
gksudo "gedit /etc/apt/sources.list" 
``` And then add those two deb lines.

You could also simply use sudo, that will ask for your password in the terminal, gksudo will make a nice popup window ask for your password, but basically those two commands are the same (more or less). 
Hope that helps. :)

> **nikoPSK said:**
> there is a thank you option. :) it's jsut I am on windows right now, so once I get home and have finished all housework (piano etc) I'll get to you asap

Of course, take your time, real life should always come first. It's just a small issue, no big deal. :)

---

### Post by nikoPSK on 2008-01-25
> **Ebuntor said:**
> Yeah, you have to be in root to do that. Make sure you add  **gksudo** to the command.
```
gksudo "gedit /etc/apt/sources.list" 
``` And then add those two deb lines.
Hope that helps. :)



Of course, take your time, real life should always come first. It's just a small issue, no big deal. :)

well, I find adjusting the height under 3d then switching to curves does it. :)

---

### Post by Ebuntor on 2008-01-25
> **nikoPSK said:**
> well, I find adjusting the height under 3d then switching to curves does it. :)

The height? The height only changes the icons' size doesn't it?  Only changing the offset modifies their distance form the bottom of the screen.

When I change the icon height to 39, for example, the icons will simply change to that size in all the looks, including the curved look. :)

---

### Post by nikoPSK on 2008-01-25
> **Ebuntor said:**
> The height? The height only changes the icons' size doesn't it?  Only changing the offset modifies their distance form the bottom of the screen.

When I change the icon height to 39, for example, the icons will simply change to that size in all the looks, including the curved look. :)

that's exactly what you want, no? It just makes the bar and icons larger or smaller. :)

---

### Post by Ebuntor on 2008-01-25
> **nikoPSK said:**
> that's exactly what you want, no? It just makes the bar and icons larger or smaller. :)

No, not quite. :) I made two screenshots to explain. As you can seen on the screenshot where I use the curved look the icons overlap the maximized window. When using the 3D look the icons remain under the window doesn't matter which size they are.

So I was wondering if there was a way to make the icons remain under the window border. I assumed this could be done via the offset option but the curves look doesn't have that.

EDIT: Wohoo, 100 beans! :lolflag:

---

### Post by nikoPSK on 2008-01-25
> **Ebuntor said:**
> No, not quite. :) I made two screenshots to explain. As you can seen on the screenshot where I use the curved look the icons overlap the maximized window. When using the 3D look the icons remain under the window doesn't matter which size they are.

So I was wondering if there was a way to make the icons remain under the window border. I assumed this could be done via the offset option but the curves look doesn't have that.

EDIT: Wohoo, 100 beans! :lolflag:

not really... :'(

---

### Post by Ebuntor on 2008-01-25
> **nikoPSK said:**
> not really... :'(

Ah, well too bad. I'll have to live with overlapping icons, no big deal. ;)

---

### Post by nikoPSK on 2008-01-26
> **Ebuntor said:**
> Ah, well too bad. I'll have to live with overlapping icons, no big deal. ;)

well, fix should be out with curves next ver.

nikoPSK

---

### Post by Abu_Dayya on 2008-01-27
Hi
I made a post about awn curves here
[http://ubuntuforums.org/showthread.php?t=672048](http://ubuntuforums.org/showthread.php?t=672048)
 but no one answered. Does anyone knows whats the problem?

---

### Post by dustman on 2008-01-27
the avant window navigator does not start. The output of ```
avant-window-navigator
```

```
dustman@dustman-laptop:~/awn-curves$ avant-window-navigator
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
**Segmentation fault (core dumped)**
dustman@dustman-laptop:~/awn-curves$ /home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

```
"awn-manager" works, i mean it appears when i launch it from a terminal, does not give any error.

Cheers!

Radu

[EDIT] Fixed this by following the instructions from here: [https://answers.launchpad.net/awn/+question/16840](https://answers.launchpad.net/awn/+question/16840) . Even if i issued all those delete/remove commands from the beginning of the HOW-TO, i still had some remains of the old version. So i removed all of them, then reinstalled, and now i have a nice looking curved dock :D (found the launchpad answer in this thread: [http://ubuntuforums.org/showthread.php?t=648949](http://ubuntuforums.org/showthread.php?t=648949))

---

### Post by nikoPSK on 2008-01-27
> **dustman said:**
> the avant window navigator does not start. The output of ```
avant-window-navigator
``````
dustman@dustman-laptop:~/awn-curves$ avant-window-navigator
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Screen is composited.
APPLET : /usr/lib/awn/applets/showdesktop.desktop
**Segmentation fault (core dumped)**
dustman@dustman-laptop:~/awn-curves$ /home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/dustman/.themes/Green Glass2/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

```"awn-manager" works, i mean it appears when i launch it from a terminal, does not give any error.

Cheers!

Radu

[EDIT] Fixed this by following the instructions from here: [https://answers.launchpad.net/awn/+question/16840](https://answers.launchpad.net/awn/+question/16840) . Even if i issued all those delete/remove commands from the beginning of the HOW-TO, i still had some remains of the old version. So i removed all of them, then reinstalled, and now i have a nice looking curved dock :D (found the launchpad answer in this thread: [http://ubuntuforums.org/showthread.php?t=648949](http://ubuntuforums.org/showthread.php?t=648949))

glad you got it fixed. :)

---

### Post by SoulSmasher on 2008-01-28
worked just great, thankfully without any issues, thanks :)

---

### Post by nikoPSK on 2008-01-28
> **SoulSmasher said:**
> worked just great, thankfully without any issues, thanks :)
no problem. :)

---

### Post by ptviperz on 2008-01-29
Anyone know why I'm getting this when attempting to install avm?

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr155-1) but it is not going to be installed
E: Broken packages

---

### Post by nikoPSK on 2008-01-29
> **ptviperz said:**
> Anyone know why I'm getting this when attempting to install avm?

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr155-1) but it is not going to be installed
E: Broken packages

There are broken pacakges... :shock: would you min trying again?

---

### Post by SoulSmasher on 2008-01-29
> **ptviperz said:**
> Anyone know why I'm getting this when attempting to install avm?

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr155-1) but it is not going to be installed
E: Broken packages

before format, i had a similar issue.. that is from version differences. the package version differs from synaptic's default ones, so the package's extension packages. you either have to downgrade the package (search in forum) or get the download the .debs with dependencies and force installing without dependency check (also given here). after force dependency option synaptic issued about broken packages, but after successful compiling i deleted them, and bingo..

those options solved my issue a week ago, hope gives you idea how to solve...

---

### Post by nikoPSK on 2008-01-29
> **SoulSmasher said:**
> before format, i had a similar issue.. that is from version differences. the package version differs from synaptic's default ones, so the package's extension packages. you either have to downgrade the package (search in forum) or get the download the .debs with dependencies and force installing without dependency check (also given here). after force dependency option synaptic issued about broken packages, but after successful compiling i deleted them, and bingo..

those options solved my issue a week ago, hope gives you idea how to solve...

there is a weird dependency problem...

---

### Post by reacocard on 2008-01-29
> **ptviperz said:**
> Anyone know why I'm getting this when attempting to install avm?

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr155-1) but it is not going to be installed
E: Broken packages

You have to have ubuntu-updates enabled.

---

### Post by ptviperz on 2008-01-29
> **reacocard said:**
> You have to have ubuntu-updates enabled.

Awesome, that was the issue, thanks!

---

### Post by nikoPSK on 2008-01-29
I was not so sure myself, thanks R!> **ptviperz said:**
> Awesome, that was the issue, thanks!

---

### Post by XPS600 on 2008-01-29
I am running Kubuntu 7.10, and here's where I get stuck on this How-To:
I've seen this problem posted once prior in this thread, with no solution, so here goes again...

When I run:
```
./autogen.sh && make
```

results in:
```

/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
/usr/share/aclocal/libfame.m4:6: warning: underquoted definition of AM_PATH_LIBFAME
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
aclocal:configure.in:93: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.in:93: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.

```

And if I try sudo make install, I get
```
make: *** No rule to make target `install'.  Stop.

```

Any ideas?

---

### Post by nikoPSK on 2008-01-29
> **XPS600 said:**
> I am running Kubuntu 7.10, and here's where I get stuck on this How-To:
I've seen this problem posted once prior in this thread, with no solution, so here goes again...

When I run:
```
./autogen.sh && make
```results in:
```

/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
/usr/share/aclocal/libfame.m4:6: warning: underquoted definition of AM_PATH_LIBFAME
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
aclocal:configure.in:93: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.in:93: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.

```And if I try sudo make install, I get
```
make: *** No rule to make target `install'.  Stop.

```Any ideas?

it doesn't like KDE...

---

### Post by ptviperz on 2008-01-30
> **ptviperz said:**
> Awesome, that was the issue, thanks!

Next issue, I downloaded all the themes, loaded them into the awn themes. It told me that the theme was successfully added but I don't see them in the list.

I'm sure this is something simple that my n00bness is missing, any ideas?

---

### Post by nikoPSK on 2008-01-30
> **ptviperz said:**
> Next issue, I downloaded all the themes, loaded them into the awn themes. It told me that the theme was successfully added but I don't see them in the list.

I'm sure this is something simple that my n00bness is missing, any ideas?

so, add them again, goto themes, if they are not there, close awn-manager, and reopen. :)

---

### Post by SoulSmasher on 2008-01-30
> **ptviperz said:**
> Next issue, I downloaded all the themes, loaded them into the awn themes. It told me that the theme was successfully added but I don't see them in the list.

I'm sure this is something simple that my n00bness is missing, any ideas?

select the radio button next to theme's name, choose then apply. that radio button was my issue while choosing :)

---

### Post by nikoPSK on 2008-01-30
> **SoulSmasher said:**
> select the radio button next to theme's name, choose then apply. that radio button was my issue while choosing :)

I think he's talking about the theme saying it was *added*, but not showing up. :)

---

### Post by appleimac on 2008-01-30
Hi there I am getting this error please help me :D


```
matt@laptop:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build avant-panel-menu.  Download the appropriate package for
  from your distribution or get the source tarball at
    ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz

checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

```


I have been to the synaptic manager and installed autoconf 

Any help would great

---

### Post by nikoPSK on 2008-01-30
> **appleimac said:**
> Hi there I am getting this error please help me :D


```
matt@laptop:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build avant-panel-menu.  Download the appropriate package for
  from your distribution or get the source tarball at
    ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz

checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

```I have been to the synaptic manager and installed autoconf 

Any help would great

it does have an error saying install something, try this and restart:

```
 sudo apt-get install glib-gettext
```

---

### Post by appleimac on 2008-01-30
```
matt@laptop:~/awn-curves$ sudo apt-get install glib-gettext
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glib-gettext

```

---

### Post by nikoPSK on 2008-01-30
> **appleimac said:**
> ```
matt@laptop:~/awn-curves$ sudo apt-get install glib-gettext
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glib-gettext

```

maybe gettext ? :(

---

### Post by appleimac on 2008-01-30
```
matt@laptop:~/awn-curves$ sudo apt-get install gettext
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gettext is already the newest version.
gettext set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by appleimac on 2008-01-30
Hi mate I have finally got passed that problem but now have this error


```
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```

How do I sort this please

---

### Post by nikoPSK on 2008-01-30
> **appleimac said:**
> Hi mate I have finally got passed that problem but now have this error


```
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```How do I sort this please

what command do you run for that?

> **appleimac said:**
> ```
matt@laptop:~/awn-curves$ sudo apt-get install gettext
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gettext is already the newest version.
gettext set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

hrm... :shock:

---

### Post by appleimac on 2008-01-30
I ran this 

```
./autogen.sh && make

```

And got this 

```
matt@laptop:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
Running autoconf2.50...
Running autoheader2.50...
Running automake-1.9...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a Python interpreter with version >= 2.3.5... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```

---

### Post by nikoPSK on 2008-01-30
> **appleimac said:**
> I ran this 

```
./autogen.sh && make

```And got this 

```
matt@laptop:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
Running autoconf2.50...
Running autoheader2.50...
Running automake-1.9...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a Python interpreter with version >= 2.3.5... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```

well, I'm not that good with python, but it couldn't compile it... :[

---

### Post by appleimac on 2008-01-30
Any suggestions on what I could do please

---

### Post by nikoPSK on 2008-01-30
> **appleimac said:**
> Any suggestions on what I could do please

you could try starting over from scratch. :) That generally works.

---

### Post by ptviperz on 2008-01-30
> **nikoPSK said:**
> I think he's talking about the theme saying it was *added*, but not showing up. :)

It's strange, I've got this running on my desktop and laptop. It's working perfectly on my desktop but the themes don't show up on the laptop :confused:

Oh well, I still love the way this looks and the guide is daggone good. Thanks for the directions and the help.

-Brent

---

### Post by appleimac on 2008-01-30
Hi mate 

I have got passed all the python problems but when I try to launch 

with 

```
avant-window-navigator
```

I get this error

```
matt@laptop:~$ avant-window-navigator
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.
(init) Semaphor-ID : 65536


```

I cant seem to be able to change the visual effects option when I right click the desktop and select change background and select visual effects tab.

Any ideas?

---

### Post by nikoPSK on 2008-01-30
> **ptviperz said:**
> It's strange, I've got this running on my desktop and laptop. It's working perfectly on my desktop but the themes don't show up on the laptop :confused:

Oh well, I still love the way this looks and the guide is daggone good. Thanks for the directions and the help.

-Brent

that's odd, the guide has evolved over time. :)
> **appleimac said:**
> Hi mate 

I have got passed all the python problems but when I try to launch 

with 

```
avant-window-navigator
```I get this error

```
matt@laptop:~/awn-curves$ avant-window-navigator
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

```Any ideas?

please make sure you're running compiz, it comes default with gutsy. Just get drivers for your videocard, goto System->Preferences->Appearance, then the desktop effects tab and choose an option, for even more customization install compizconfig settings manager

---

### Post by appleimac on 2008-01-30
Hi there im new to this how do I install

compizconfig settings manager

How do I get drivers for my videocard


How do I run compiz?


Many Thanks

---

### Post by nikoPSK on 2008-01-30
> **appleimac said:**
> Hi there im new to this how do I install

compizconfig settings manager

How do I get drivers for my videocard


How do I run compiz?


Many Thanks

click this: [compiz-config-settings-manager]("apt:compiz-config-settings-manager") that installs it (not really needed), to get compiz running, you need you need either ati or nvidia card drivers (depending on what you have), then run ```
compiz --replace
``` to launch it once you choose your preferences.

nikoPSK

---

### Post by appleimac on 2008-01-30
Right I have finally got the bar at the bottom to work.

Please seen screenshot for the bits that do not work properly.

I have a strange white line next to the terminal icon

Also 

How do I get rid of the original bar at the bottom of the screen..


Many Thanks


Matt

---

### Post by nikoPSK on 2008-01-30
> **appleimac said:**
> Right I have finally got the bar at the bottom to work.

Please seen screenshot for the bits that do not work properly.

I have a strange white line next to the terminal icon

Also 

How do I get rid of the original bar at the bottom of the screen..


Many Thanks


Matt

very nice desktop, the bar looks not as it should (curves), but the white line is an applet not loading properly, remove it and put it back, if it persists, the applet is broken. I might suggest one thing for your mac themed style:

[http://ubuntuforums.org/showthread.php?t=241868](http://ubuntuforums.org/showthread.php?t=241868)

to delete the panel, right click, delete this panel. :)

---

### Post by appleimac on 2008-01-30
How come I dont have the curve?


Cheers

---

### Post by nikoPSK on 2008-01-30
> **appleimac said:**
> How come I dont have the curve?


Cheers

I don't know, there was another case of this... but if you like it... hey, maybe we have something. :p

---

### Post by ryuuk86 on 2008-01-31
i have this error

```

creating avant-window-navigator
make[3]: Opuszczenie katalogu `/home/daro/awn-curves/src'
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/src'
Making all in awn-applet-activation
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/awn-applet-activation'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/awn-applet-activation'
Making all in data
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/data'
Making all in active
make[3]: Wej&#347;cie do katalogu `/home/daro/awn-curves/data/active'
make[3]: Nie ma nic do zrobienia w `all'.
make[3]: Opuszczenie katalogu `/home/daro/awn-curves/data/active'
make[3]: Wej&#347;cie do katalogu `/home/daro/awn-curves/data'
make[3]: Nie ma nic do zrobienia w `all-am'.
make[3]: Opuszczenie katalogu `/home/daro/awn-curves/data'
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/data'
Making all in applets
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/applets'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/applets'
Making all in po
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/po'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/po'
Making all in pyawn
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/pyawn'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/pyawn'
Making all in awn-manager
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/awn-manager'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/awn-manager'
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves'
make[2]: Opuszczenie katalogu `/home/daro/awn-curves'
make[1]: Opuszczenie katalogu `/home/daro/awn-curves'

```

---

### Post by nikoPSK on 2008-01-31
> **ryuuk86 said:**
> i have this error
 
```

creating avant-window-navigator
make[3]: Opuszczenie katalogu `/home/daro/awn-curves/src'
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/src'
Making all in awn-applet-activation
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/awn-applet-activation'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/awn-applet-activation'
Making all in data
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/data'
Making all in active
make[3]: Wej&#347;cie do katalogu `/home/daro/awn-curves/data/active'
make[3]: Nie ma nic do zrobienia w `all'.
make[3]: Opuszczenie katalogu `/home/daro/awn-curves/data/active'
make[3]: Wej&#347;cie do katalogu `/home/daro/awn-curves/data'
make[3]: Nie ma nic do zrobienia w `all-am'.
make[3]: Opuszczenie katalogu `/home/daro/awn-curves/data'
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/data'
Making all in applets
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/applets'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/applets'
Making all in po
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/po'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/po'
Making all in pyawn
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/pyawn'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/pyawn'
Making all in awn-manager
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves/awn-manager'
make[2]: Nie ma nic do zrobienia w `all'.
make[2]: Opuszczenie katalogu `/home/daro/awn-curves/awn-manager'
make[2]: Wej&#347;cie do katalogu `/home/daro/awn-curves'
make[2]: Opuszczenie katalogu `/home/daro/awn-curves'
make[1]: Opuszczenie katalogu `/home/daro/awn-curves'

```
 
this is when running the make command?  I cannot read the other language... sorry, please translate. :)

---

### Post by winter_mute on 2008-02-01
When I try to run the code, I just get the output of:

pan@hex:/data/Code/awn-curves$ avant-window-navigator
/home/pan/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
Screen is composited.
Segmentation fault (core dumped)

Which is about the least helpful thing ever in fixing this.  And awn-manager works perfectly fine.  Any help here?

---

### Post by nikoPSK on 2008-02-01
> **winter_mute said:**
> When I try to run the code, I just get the output of:

pan@hex:/data/Code/awn-curves$ avant-window-navigator
/home/pan/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
Screen is composited.
Segmentation fault (core dumped)

Which is about the least helpful thing ever in fixing this.  And awn-manager works perfectly fine.  Any help here?

please try a reinstall. :)

---

### Post by Silthrim on 2008-02-04
EDIT: nevermind... I just ran the "./autogen.sh" and "make" as two seperate commands.

---

### Post by nikoPSK on 2008-02-04
> **Silthrim said:**
> EDIT: nevermind... I just ran the "./autogen.sh" and "make" as two seperate commands.
 
yesm it notes that in my guide. :)

---

### Post by royrules22 on 2008-02-04
I'm getting this error:

```
avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)

```

---

### Post by nikoPSK on 2008-02-04
please reinstall you're getting seg faults. :(

---

### Post by el-nico on 2008-02-05
READ THIS, nikoPSK! 
a public pm

I've been a linux-user for some years now. I've tried them all. Really, I have. 
And I've been constantly working on apperances, desktop, ikons, sounds and so many, many more things.
I like my system personal.
 
Been trying to get the dock in place for some time...
Never made it.

Last night I found *your* "how-to..." on this website... and WAM-BAM-thankYOUma'm.... it is all in place, everything is working perfectly, it is beautiful, and by the results of my own tests; it is very, very, very stable ;)

I am so happy!!!

Your "how-to...." is by far the easiest, most understandable and best I've ever read and done!!

Thank you so very much!!!!!

(.....and now begins the hunt for docking ikons ;))


HEY!! I've got a bean!!

---

### Post by el-nico on 2008-02-05
.....and I've got a question for you;

How do I with ease and safe move the awn-curves folder from my home folder to the file-system? In my home folder I have my no-system folders (pictures/documents/video and so on...)

Now I have TWO beans!!

---

### Post by royrules22 on 2008-02-05
> **nikoPSK said:**
> please reinstall you're getting seg faults. :(

I did. I followed the removal instruction on the main page, restarted, redid the whole thing step by step, restarted and still get the same seg fault.

Also I notice people keep the avn-curves and remove the bottom panel but that totally stops me from using the other desktops (as I've set compiz-fusion to use 4 desktops). Is there a way I can either move the desktop chooser to the top panel or get it to show in avn?

First I guess the seg fault problem :confused:

---

### Post by royrules22 on 2008-02-05
[QUOTE=veluxe]I had the very same issue with the segmentation fault. To fix this condition, from within synaptic, I marked the following packages for re-installation: awn-core-applets-bzr, libawn-bzr, and python-libawn-bzr. After these reapplied to my system, awn-curves works like a champ.[/QUOTE]

Now I can run avn, but I'm not sure if this the curves version. It looks like this for me now (ignore the bottom panel, I'm keeping it 'till I figure out the answer to my question in the previous post

---

### Post by xdarkgokux on 2008-02-05
amazing guide... everything works..thx a lot!

---

### Post by Gourgi on 2008-02-05
> **royrules22 said:**
> Now I can run avn, but I'm not sure if this the curves version. It looks like this for me now (ignore the bottom panel, I'm keeping it 'till I figure out the answer to my question in the previous post

no this is the 3-d look
if curves were installed correctly you can enable them doing this : 

> **Alt+F2**
> awn-manager 
that opens awn's manager
then go : 
> General (General appearance)-->Bar Appearance (tab) --> **_Look_**(Tab) [COLOR="Red"][SIZE="1"]here change from[/SIZE][/COLOR] [COLOR="Blue"]3d look [/COLOR][COLOR="Red"][SIZE="1"]to[/SIZE] [/COLOR][COLOR="Blue"]**awn-curves**[/COLOR]
that's all , cheers :popcorn:

---

### Post by reacocard on 2008-02-05
> **el-nico said:**
> .....and I've got a question for you;

How do I with ease and safe move the awn-curves folder from my home folder to the file-system? In my home folder I have my no-system folders (pictures/documents/video and so on...)

Now I have TWO beans!!

just move it using the file manager, it doesn't have to be in a specific spot for curves to work after it's installed. (or even during installation for that matter, but to do that requires editing the command sequence a little.)

---

### Post by nikoPSK on 2008-02-05
> **el-nico said:**
> READ THIS, nikoPSK! 
a public pm

I've been a linux-user for some years now. I've tried them all. Really, I have. 
And I've been constantly working on apperances, desktop, ikons, sounds and so many, many more things.
I like my system personal.
 
Been trying to get the dock in place for some time...
Never made it.

Last night I found *your* "how-to..." on this website... and WAM-BAM-thankYOUma'm.... it is all in place, everything is working perfectly, it is beautiful, and by the results of my own tests; it is very, very, very stable ;)

I am so happy!!!

Your "how-to...." is by far the easiest, most understandable and best I've ever read and done!!

Thank you so very much!!!!!

(.....and now begins the hunt for docking ikons ;))


HEY!! I've got a bean!!

No problemo, guide has been fun working on and I enjoy that I can help people. No real problems ever except the occasional seg fault... :( Glad I could help you! 

> **el-nico said:**
> .....and I've got a question for you;

How do I with ease and safe move the awn-curves folder from my home folder to the file-system? In my home folder I have my no-system folders (pictures/documents/video and so on...)

Now I have TWO beans!!

It is best to leave the folder in home as is. I am not sure if changing the name (adding a period in front to make it hidden) would affect awn. :}

> **royrules22 said:**
> I did. I followed the removal instruction on the main page, restarted, redid the whole thing step by step, restarted and still get the same seg fault.

Also I notice people keep the avn-curves and remove the bottom panel but that totally stops me from using the other desktops (as I've set compiz-fusion to use 4 desktops). Is there a way I can either move the desktop chooser to the top panel or get it to show in avn?

First I guess the seg fault problem :confused:

Other desktops, use bling switcher or desktop switcher applet. Or just control+Alt+Left or right arrow

> **royrules22 said:**
> Now I can run avn, but I'm not sure if this the curves version. It looks like this for me now (ignore the bottom panel, I'm keeping it 'till I figure out the answer to my question in the previous post

It's in 3d view, apply curved look in awn manager, hit refresh. If it doesn't go close awn and restart it. :)

> **xdarkgokux said:**
> amazing guide... everything works..thx a lot!

No problem! :guitar:

---

### Post by jpzamora on 2008-02-05
This is not working for me...when I installed it, there was a message saying that "phyton headers" and a "co" package where missing. The dock continues in 3D mode and I cannot turn to curved shape.

Do I have to reinstall it??

Thanks

---

### Post by nikoPSK on 2008-02-06
> **jpzamora said:**
> This is not working for me...when I installed it, there was a message saying that "phyton headers" and a "co" package where missing. The dock continues in 3D mode and I cannot turn to curved shape.

Do I have to reinstall it??

Thanks

could you give the exact error message? Co as in compiz?

---

### Post by el-nico on 2008-02-06
[QUOTE=nikoPSK;4277331]No problemo, guide has been fun working on and I enjoy that I can help people. No real problems ever except the occasional seg fault... :( Glad I could help you! 



It is best to leave the folder in home as is. I am not sure if changing the name (adding a period in front to make it hidden) would affect awn. :}


I added a period. The folder is not to be seen and everything works. Rebootet, went back and forth.... It seems to be working. Everything is working!
Man, another good reason for having a cold, danish beer tonight ;)

---

### Post by nikoPSK on 2008-02-06
> **el-nico said:**
> [quote=nikoPSK;4277331]No problemo, guide has been fun working on and I enjoy that I can help people. No real problems ever except the occasional seg fault... :( Glad I could help you! 



It is best to leave the folder in home as is. I am not sure if changing the name (adding a period in front to make it hidden) would affect awn. :}


I added a period. The folder is not to be seen and everything works. Rebootet, went back and forth.... It seems to be working. Everything is working!
Man, another good reason for having a cold, danish beer tonight ;)

Ah, fun, I'll add to my guide that the folder can be hidden! (beers are always good ;-) )

---

### Post by ispy on 2008-02-06
It won't run.

I've got Gutsy, 32 Bit, and I did everything as you wish...

but when I try to run in the terminal, I get this error...

```
Screen is composited.
Segmentation fault (core dumped)

```

what does this mean?

---

### Post by nikoPSK on 2008-02-06
> **ispy said:**
> It won't run.

I've got Gutsy, 32 Bit, and I did everything as you wish...

but when I try to run in the terminal, I get this error...

```
Screen is composited.
Segmentation fault (core dumped)

```what does this mean?

it means you reinstall awn... :lol: .

---

### Post by ispy on 2008-02-06
elaborate?

I'm kinda a noob. I can do basic terminal stuff, but really have no clue what a lot of the lingo means...

---

### Post by nikoPSK on 2008-02-06
> **ispy said:**
> elaborate?

I'm kinda a noob. I can do basic terminal stuff, but really have no clue what a lot of the lingo means...
do this:
```
 sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
```

and restart the guide. :)

---

### Post by el-nico on 2008-02-08
> **nikoPSK said:**
> [quote=el-nico;4281161]

Ah, fun, I'll add to my guide that the folder can be hidden! (beers are always good ;-) )

Weeeeell now.... to say it works 100% would be a lie. After five or six reboots the folder came back. But I put another period in front, and away it went....

AND I'M GOIN' TO KEEP ON DOIN' THAT!!!!

Have a nice weekend!

---

### Post by DioSonoIo on 2008-02-08
Thanks for the guide!! Very well done!

Unfortunately my pc is too old for such elaborate things so I have to remove all of this!

Your removal guide is enough to clean up the system? Or do I also have to uninstall the single packages I got following your guide?

Thanx for any answer!:)

---

### Post by nikoPSK on 2008-02-08
> **el-nico said:**
> [quote=nikoPSK;4282587]

Weeeeell now.... to say it works 100% would be a lie. After five or six reboots the folder came back. But I put another period in front, and away it went....

AND I'M GOIN' TO KEEP ON DOIN' THAT!!!!

Have a nice weekend!

It half works then ;)

> **DioSonoIo said:**
> Thanks for the guide!! Very well done!

Unfortunately my pc is too old for such elaborate things so I have to remove all of this!

Your removal guide is enough to clean up the system? Or do I also have to uninstall the single packages I got following your guide?

Thanx for any answer!:)

Thats enough to remove it. :)

---

### Post by el-nico on 2008-02-08
> **nikoPSK said:**
> [quote=el-nico;4292263]

It half works then ;)


Half is half, but better than anything, and gooood enough for me. 
I'm still so VERY pleased with everything. Got some really cool icons now, and if I have to put a period in front of a folder every five or six times I turn my on my lap-top....well, so be it!!!

It's friday; dark norwegian beer time ;)

---

### Post by nikoPSK on 2008-02-08
> **el-nico said:**
> [quote=nikoPSK;4293241]
 
Half is half, but better than anything, and gooood enough for me. 
I'm still so VERY pleased with everything. Got some really cool icons now, and if I have to put a period in front of a folder every five or six times I turn my on my lap-top....well, so be it!!!
 
It's friday; dark norwegian beer time ;)
 
hehe, ;) Try playing around creating your own themes!

---

### Post by wolterh on 2008-02-08
Hi. You told me to give you the output of 
```

avant-window-navigator
awn-manager

```

The awn-manager is ok
But, the window navigator gives this:

You-may-prefer-this output:
```

** (avant-window-navigator:18949): WARNING **: Failed to make connection to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

Complete output:
```

/apps/avant-window-navigator/force_monitor unset, setting now
/apps/avant-window-navigator/monitor_width unset, setting now
/apps/avant-window-navigator/monitor_height unset, setting now
/apps/avant-window-navigator/panel_mode unset, setting now
/apps/avant-window-navigator/auto_hide unset, setting now
/apps/avant-window-navigator/auto_hide_delay unset, setting now
/apps/avant-window-navigator/keep_below unset, setting now
/apps/avant-window-navigator/bar/bar_height unset, setting now
/apps/avant-window-navigator/bar/bar_pos unset, setting now
/apps/avant-window-navigator/bar/bar_angle unset, setting now
/apps/avant-window-navigator/bar/icon_offset unset, setting now
/apps/avant-window-navigator/bar/rounded_corners unset, setting now
/apps/avant-window-navigator/bar/corner_radius unset, setting now
/apps/avant-window-navigator/bar/render_pattern unset, setting now
/apps/avant-window-navigator/bar/pattern_uri unset, setting now
/apps/avant-window-navigator/bar/pattern_alpha unset, setting now
/apps/avant-window-navigator/bar/glass_step_1 unset, setting now
/apps/avant-window-navigator/bar/glass_step_2 unset, setting now
/apps/avant-window-navigator/bar/glass_histep_1 unset, setting now
/apps/avant-window-navigator/bar/glass_histep_2 unset, setting now
/apps/avant-window-navigator/bar/border_color unset, setting now
/apps/avant-window-navigator/bar/hilight_color unset, setting now
/apps/avant-window-navigator/bar/show_separator unset, setting now
/apps/avant-window-navigator/bar/sep_color unset, setting now
/apps/avant-window-navigator/window_manager/show_all_windows unset, setting now
/apps/avant-window-navigator/window_manager/launchers unset, setting now
/apps/avant-window-navigator/app/active_png unset, setting now
/apps/avant-window-navigator/app/use_png unset, setting now
/apps/avant-window-navigator/app/arrow_color unset, setting now
/apps/avant-window-navigator/app/arrow_offset unset, setting now
/apps/avant-window-navigator/app/tasks_have_arrows unset, setting now
/apps/avant-window-navigator/app/name_change_notify unset, setting now
/apps/avant-window-navigator/app/alpha_effect unset, setting now
/apps/avant-window-navigator/app/icon_effect unset, setting now
/apps/avant-window-navigator/title/text_color unset, setting now
/apps/avant-window-navigator/title/shadow_color unset, setting now
/apps/avant-window-navigator/title/background unset, setting now
/apps/avant-window-navigator/title/font_face unset, setting now

** (avant-window-navigator:18949): WARNING **: Failed to make connection to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (avant-window-navigator:18949): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (avant-window-navigator:18949): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:18949): WARNING **: There was an error requesting the name: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
*** glibc detected *** avant-window-navigator: double free or corruption (out): 0x081e2458 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb720dd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7211800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7459961]
/usr/lib/libglib-2.0.so.0(g_error_free+0x29)[0xb7443469]
avant-window-navigator[0x804f6de]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb71ba050]
avant-window-navigator[0x804ea01]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:06 1407502    /usr/local/bin/avant-window-navigator
08067000-08068000 rw-p 0001e000 08:06 1407502    /usr/local/bin/avant-window-navigator
08068000-08206000 rw-p 08068000 00:00 0          [heap]
b6900000-b6921000 rw-p b6900000 00:00 0 
b6921000-b6a00000 ---p b6921000 00:00 0 
b6ac4000-b6ace000 r-xp 00000000 08:06 1026211    /lib/libgcc_s.so.1
b6ace000-b6acf000 rw-p 0000a000 08:06 1026211    /lib/libgcc_s.so.1
b6ae1000-b6b6c000 r--p 00000000 08:06 1436177    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6b6c000-b6b6e000 r-xp 00000000 08:06 1370660    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6b6e000-b6b6f000 rw-p 00001000 08:06 1370660    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6b6f000-b6b72000 r--s 00000000 08:06 721009     /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86.cache-2
b6b72000-b6b74000 r--s 00000000 08:06 721008     /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b6b74000-b6b7a000 r--s 00000000 08:06 721007     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6b7a000-b6b7d000 r--s 00000000 08:06 721005     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6b7d000-b6b80000 r--s 00000000 08:06 721004     /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b6b80000-b6b81000 r--s 00000000 08:06 721002     /var/cache/fontconfig/1b70ff56935fd37e75520e134628df26-x86.cache-2
b6b81000-b6b82000 r--s 00000000 08:06 721001     /var/cache/fontconfig/6edd069ccec3ba28096b368c434fa861-x86.cache-2
b6b82000-b6b86000 r--s 00000000 08:06 721000     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6b86000-b6b87000 r--s 00000000 08:06 720999     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6b87000-b6ba2000 r--s 00000000 08:06 720998     /var/cache/fontconfig/4ca92cf76c0cf3dfa7f011127eff595d-x86.cache-2
b6ba2000-b6bbe000 r--s 00000000 08:06 720997     /var/cache/fontconfig/6abf76b0b4cc7192703d8431ac929b75-x86.cache-2
b6bbe000-b6bdc000 r--s 00000000 08:06 720996     /var/cache/fontconfig/f408d08d2fce062ab660f628db78bf96-x86.cache-2
b6bdc000-b6bdd000 r--s 00000000 08:06 720995     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6bdd000-b6be0000 r--s 00000000 08:06 720994     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6be0000-b6be1000 r--s 00000000 08:06 720885     /var/cache/fontconfig/7ee55724f82591cb35c3d9771e9e69ed-x86.cache-2
b6be1000-b6be4000 r--s 00000000 08:06 720884     /var/cache/fontconfig/f680583fed5bdc90d95a16af47e16528-x86.cache-2
b6be4000-b6be5000 r--s 00000000 08:06 720883     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b6be5000-b6be6000 r--s 00000000 08:06 720882     /var/cache/fontconfig/a8d35ba226d862df35f7c320f882e11a-x86.cache-2
b6be6000-b6be7000 r--s 00000000 08:06 720881     /var/cache/fontconfig/5a86461592e14be7c82e45729474f230-x86.cache-2
b6be7000-b6bed000 r--s 00000000 08:06 720880     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6bed000-b6bef000 r--s 00000000 08:06 720879     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6bef000-b6bf7000 r--s 00000000 08:06 720878     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6bf7000-b6bfd000 r--s 00000000 08:06 720877     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6bfd000-b6bfe000 r--s 00000000 08:06 720874     /var/cache/fontconfig/9451a55048e8dbe8633e64d34165fdf2-x86.cache-2
b6bfe000-b6bff000 r--s 00000000 08:06 720873     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6bff000-b6c01000 r--s 00000000 08:06 720872     /var/cache/fontconfig/393bAborted (core dumped)

```

---

### Post by nikoPSK on 2008-02-08
> **woli said:**
> <snip>
 
Okay, that's odd.. Are you firewalled or something? Try reinstalling awn.

---

### Post by Scarecrow__79 on 2008-02-09
Hey all,

I'm new to the Ubuntu scene. I am having a great time getting to know it.

I had some issue with attempting this modification - obviously a user error. Initially after i got to the install part (i didn't understand the part about being in the folder either..?)  but before i started with that code (after uninstalling) my pc died and kept crashing after i restarted. I tried doing the steps again from the beginning but the pc was very unstable.

I did some more poking around online and came accross this post and script:

[http://flarsen.com/blog/installing-awn-curves-on-ubuntu-710-gutsy-gibbon/]("http://flarsen.com/blog/installing-awn-curves-on-ubuntu-710-gutsy-gibbon/")

when i first ran it i got errors. when i checked the errors i saw a message saying my theme (blubuntu) was not supported. I switched over to one of the standard themes and ran the script again and with-in 7mins...hey presto! i had curved awn and i didn't have to do a thing....:)

i know that probably takes the fun out of it all, but i like things simple and easy   ; p

---

### Post by Gourgi on 2008-02-09
> **Scarecrow__79 said:**
> Hey all,

I'm new to the Ubuntu scene. I am having a great time getting to know it.

I had some issue with attempting this modification - obviously a user error. Initially after i got to the install part (i didn't understand the part about being in the folder either..?)  but before i started with that code (after uninstalling) my pc died and kept crashing after i restarted. I tried doing the steps again from the beginning but the pc was very unstable.

I did some more poking around online and came accross this post and script:

[http://flarsen.com/blog/installing-awn-curves-on-ubuntu-710-gutsy-gibbon/]("http://flarsen.com/blog/installing-awn-curves-on-ubuntu-710-gutsy-gibbon/")

when i first ran it i got errors. when i checked the errors i saw a message saying my theme (blubuntu) was not supported. I switched over to one of the standard themes and ran the script again and with-in 7mins...hey presto! i had curved awn and i didn't have to do a thing....:)

i know that probably takes the fun out of it all, but i like things simple and easy   ; p
the script's command are the same as those in first post
nice script btw :)

i still can't install awn-curves , still getting same segment fault  :(
**can anyone tell me if awn-curves work with launchpad's bzr version of avant ?? **

---

### Post by Samip on 2008-02-09
AWN isnt working for me. I typed this into terminal:
avant-window-navigator
and i got this as the output:
/home/samip/.themes/Clearlooks_blackblue/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
Screen is composited.
Segmentation fault (core dumped)

I can get into the settings though

---

### Post by nikoPSK on 2008-02-09
> **Gourgi said:**
> the script's command are the same as those in first post
nice script btw :)

i still can't install awn-curves , still getting same segment fault  :(
**can anyone tell me if awn-curves work with launchpad's bzr version of avant ?? **

It should work with launchpads... Anyways, you tried a reinstall for that seg fault? It's odd, I never gotten one. Around 30% of users do.
> **Samip said:**
> AWN isnt working for me. I typed this into terminal:
avant-window-navigator
and i got this as the output:
/home/samip/.themes/Clearlooks_blackblue/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
Screen is composited.
Segmentation fault (core dumped)

I can get into the settings though

Please try a reinstall.

---

### Post by el-nico on 2008-02-09
> **nikoPSK said:**
> [quote=el-nico;4294477]
 
hehe, ;) Try playing around creating your own themes!

Ooooo I'm on it, niko. Made two last night. Very primitive, very crued. 
But it's a beginning. Both worked like a charm on the dock. Swirling around 3D-style. 
Having a brainstorm tonight, with The Beatles and Tom Waits and Nick Cave and Leonard Cohen; pencil on paper, sketching, drawing, throwing away....throwing a lot away...

I'm making it happen! I am a part of it all :)

Will post screens in a while (...not tonight)

---

### Post by nikoPSK on 2008-02-09
> **el-nico said:**
> [quote=nikoPSK;4294751]

Ooooo I'm on it, niko. Made two last night. Very primitive, very crued. 
But it's a beginning. Both worked like a charm on the dock. Swirling around 3D-style. 
Having a brainstorm tonight, with The Beatles and Tom Waits and Nick Cave and Leonard Cohen; pencil on paper, sketching, drawing, throwing away....throwing a lot away...

I'm making it happen! I am a part of it all :)

Will post screens in a while (...not tonight)

Will do! I could add them to the second post with all the themes. :)

---

### Post by Gourgi on 2008-02-09
> **nikoPSK said:**
> It should work with launchpads... Anyways, you tried a reinstall for that seg fault? It's odd, I never gotten one. Around 30% of users do.


Please try a reinstall.

whohoo it works , after much pain though ! :popcorn:

i used bzr for awn0.2 and **not trunk** and (after some make install & ldconfig) it worked !!
now i don't touch it :) hehe

curves look good , still i hate the way the icons from curves override other windows :( (although i told awn not to do that ! )
see attached picture ..

---

### Post by nikoPSK on 2008-02-09
> **Gourgi said:**
> whohoo it works , after much pain though ! :popcorn:

i used bzr for awn0.2 and **not trunk** and (after some make install & ldconfig) it worked !!
now i don't touch it :) hehe

curves look good , still i hate the way the icons from curves override other windows :( (although i told awn not to do that ! )
see attached picture ..

have to restart your pc after telling it that. :)

---

### Post by Gourgi on 2008-02-09
> **nikoPSK said:**
> have to restart your pc after telling it that. :)

i did it, no change :(
maybe it has something to to with my current version of avant (0.2.0) and it iss fixed in avant 0.2.1 , i don't know

---

### Post by the_nomad on 2008-02-10
seems that [http://bazaar.launchpad.net/~awn-curves-team/awn/RCS/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/RCS/awn-curves) aint working anymore :( any ideas where can i get it? thanx

---

### Post by nikoPSK on 2008-02-10
> **Gourgi said:**
> i did it, no change :(
maybe it has something to to with my current version of avant (0.2.0) and it iss fixed in avant 0.2.1 , i don't know

Most likely.

> **the_nomad said:**
> seems that [http://bazaar.launchpad.net/~awn-curves-team/awn/RCS/awn-curves]("http://bazaar.launchpad.net/%7Eawn-curves-team/awn/RCS/awn-curves") aint working anymore :( any ideas where can i get it? thanx

I have no idea, I have asked meek, waiting for response.

---

### Post by wolterh on 2008-02-10
OK. I found out. I had another installation of awn. Problem solved by deleting one of the installations and running awn.

---

### Post by nikoPSK on 2008-02-10
> **woli said:**
> OK. I found out. I had another installation of awn. Problem solved by deleting one of the installations and running awn.

there we go. :)

---

### Post by Vadi on 2008-02-11
Btw, to add new repositories, you can go to System - Administration - software sources and click on the third-party software tab.

That's a lot more safer, better, faster, and newbie-friendly and messing with sources.list (which you do -not- want to mess up).

---

### Post by nikoPSK on 2008-02-11
> **Vadi said:**
> Btw, to add new repositories, you can go to System - Administration - software sources and click on the third-party software tab.
 
That's a lot more safer, better, faster, and newbie-friendly and messing with sources.list (which you do -not- want to mess up).
 
I do know that, I guess I can change that in my guide when I get home. :)

---

### Post by RottenBananas on 2008-02-11
Hey great guide!
I got it to work i think but theres a problem...it looks lobsided...the icons on the right side of the bar are extra low and are cut off the screen. If i click on them they come back to normal...and then when i hover over them they mess up again. Heres a screenshot

And it also randomly crashes...awn itself does and also takes out compiz with it. It freezes for about 10 secs..awn disappears and im back in metacity. 

Any suggestions?

Thanks
-Bananas

<-----EDIT----->
lmao like 10 secs after posting this i fixed it...wasted post sorry...i had to change the bar size and reset it and it looks good...as for the random crashing it hasnt happened since(but its only been a day) so ill post again if it does crash.

Thanks!

---

### Post by nikoPSK on 2008-02-11
> **RottenBananas said:**
> Hey great guide!
I got it to work i think but theres a problem...it looks lobsided...the icons on the right side of the bar are extra low and are cut off the screen. If i click on them they come back to normal...and then when i hover over them they mess up again. Heres a screenshot

And it also randomly crashes...awn itself does and also takes out compiz with it. It freezes for about 10 secs..awn disappears and im back in metacity. 

Any suggestions?

Thanks
-Bananas

<-----EDIT----->
lmao like 10 secs after posting this i fixed it...wasted post sorry...i had to change the bar size and reset it and it looks good...as for the random crashing it hasnt happened since(but its only been a day) so ill post again if it does crash.

Thanks!

oh, edited so soon. :lolflag:

---

### Post by Vadi on 2008-02-11
Just move your mouse over the icons and they'll align properly.

It happens often after you switch cube sides

---

### Post by RottenBananas on 2008-02-11
Hey,
sure enough it crashed again...i was just browsing in firefox and awn disappears and compiz is gone. Is there a logfile or something i can post to address the problem easily?

Has this happened to anyone else?

---

### Post by nikoPSK on 2008-02-11
> **RottenBananas said:**
> Hey,
sure enough it crashed again...i was just browsing in firefox and awn disappears and compiz is gone. Is there a logfile or something i can post to address the problem easily?

Has this happened to anyone else?

happens often sadly... What does it say when you run ```
avant-window-navigator
``` in terminal when it crashes?

---

### Post by RottenBananas on 2008-02-12
I gotta wait for it to crash? lol ive been waiting 4 hours and nothing...i bet you it wont crash now that we're watching it!

---

### Post by nine7six on 2008-02-12
I installed the un-curved version and it worked fine, I followed your steps for removal and then installed this version. When I type avant-window-navigator it gives me:

```
Screen is composited.
Segmentation fault (core dumped)
```

Any ideas?

---

### Post by nikoPSK on 2008-02-12
> **nine7six said:**
> I installed the un-curved version and it worked fine, I followed your steps for removal and then installed this version. When I type avant-window-navigator it gives me:

```
Screen is composited.
Segmentation fault (core dumped)
```Any ideas?

It's the common awn curves seg fault, please try a reinstall.

---

### Post by nine7six on 2008-02-12
> **nikoPSK said:**
> It's the common awn curves seg fault, please try a reinstall.

will do, I'll update once I'm finished. Thanks.

---

### Post by nikoPSK on 2008-02-12
> **nine7six said:**
> will do, I'll update once I'm finished. Thanks.

--> [IMG]http://ubuntuforums.org/images/uf/buttons/post_thanks.gif[/IMG] 

:D

---

### Post by mab1376 on 2008-02-13
when i try and start it up i get this message

```
mark@mark-laptop:~$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)
mark@mark-laptop:~$ 

```

---

### Post by RottenBananas on 2008-02-13
Is there a way to not have the dock at the bottom? I wanna put it on the right side. If awn cant do this can kiba or cairo or any other dock?

---

### Post by nikoPSK on 2008-02-13
> **mab1376 said:**
> when i try and start it up i get this message

```
mark@mark-laptop:~$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)
mark@mark-laptop:~$ 

```
please reinstall awn.
> **RottenBananas said:**
> Is there a way to not have the dock at the bottom? I wanna put it on the right side. If awn cant do this can kiba or cairo or any other dock?
for next version of awn, yes.

---

### Post by raafaell on 2008-02-13
mine got stuck on " Fetch phase 1/4" what should i do?

---

### Post by raafaell on 2008-02-13
> **raafaell said:**
> mine got stuck on " Fetch phase 1/4" what should i do?

no, i think it's doing the job, be back again to say that everything went fine. Cheers.

---

### Post by raafaell on 2008-02-13
it's stuck now, on "99% [Connecting to packages.freecontrib.org (34.52.53.34)]"
I think the link is broken, some help please.

---

### Post by RottenBananas on 2008-02-13
> **nikoPSK said:**
> please reinstall awn.

for next version of awn, yes.

Sweeet...any idea when this versions coming out?

---

### Post by nikoPSK on 2008-02-13
> **raafaell said:**
> mine got stuck on " Fetch phase 1/4" what should i do?

Patience young grasshopper

> **raafaell said:**
> no, i think it's doing the job, be back again to say that everything went fine. Cheers.

okay

> **raafaell said:**
> it's stuck now, on "99% [Connecting to packages.freecontrib.org (34.52.53.34)]"
I think the link is broken, some help please.

Just be patient

> **RottenBananas said:**
> Sweeet...any idea when this versions coming out?
Reacocard would know... I think it's like 4 months...

---

### Post by Vadi on 2008-02-14
I do think your instructions are broken. On a clean installation, awn-curves fail to show up in the themes. I'll reinstall, but you should test your instructions too (just grab virtualbox and install ubuntu in it).

---

### Post by Vadi on 2008-02-14
Still not working... it just isn't appearing in the themes section. And this really sucks, because AWN is the only dock I use that has the capability *not* to look like a knock-off OS X dock.

---

### Post by Kivech on 2008-02-14
Ok, first off, awesome guide!

I have it working, but I have some oddities going on though.

Let me start with the installation. I did an install on a clean installation of Ubuntu 7.10. AWN itself ran fine from scratch, the curved add-on had some small problems however.

At the second last step I had this as a result:

marc@marc-desktop:~/awn-curves$ sudo apt-get update
~
*snip*
~
W: Duplicate sources.list entry [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages (/var/lib/apt/lists/download.tuxfamily.org_syzygy42_dists_gutsy_avant-window-navigator_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

marc@marc-desktop:~/awn-curves$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
avant-window-navigator-bzr is already the newest version.
awn-core-applets-bzr is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
marc@marc-desktop:~/awn-curves$ 

I ran apt-get update a second time, but got the same error as displayed here.

At the second message I figured that all was ok and this was just a confirmation that I already had some needed elements installed. I just want to check if the previous error could have made the script maybe build some dependency errors as a result.

As a result, the command avant-window-navigator doesn't do anything anymore. Instead I have to manually start the application from /[my home dir]/awn-curves/src/avant-window-navigator.

Not too much of a big deal. I just have to change the paths in the icon properties and the session list, but it would be nice if it were to work the way it is supposed to. Any ideas how I can get it so that I can run avant-window-navigator without having to go to this specific directory?

Forgive me, been out of the Linux scene for over 10 years, so consider me a complete newb here.

Then, the AWN curve itself:

The default set of applets that one can add don't follow the line of the curve but the added shortcuts do.

Let me put it this way: if I add just applets that come with AWN, they will all sit at the bottom of my screen (in some cases the bottom sinks off my screen, and I have no clue why), but manually added shortcuts to programs nicely follow the curve.
Is there a way I can change this? It seems that the icon offset in some situations doesn't work well. The same goes for opened windows btw, those also follow the curve properly.

I even tried it in 3D mode, and here also the default offset of the icons makes them sink a few pixels below the bottom edge of my screen. Easy to adjust, yes, but not a nice finish.

When I try to switch back to the original AWN mode (flat panel) it closes down and doesn't come back up unless I pick either 3D or curved mode. Is there a way to fix this also? It's pretty handy to be able to go back to the original mode for sake of comparison. Now there's no way for me to see if the offset in the original mode has the same oddities as well.

Thanks in advance for your help.

Kivech

---

### Post by nikoPSK on 2008-02-14
> **Vadi said:**
> I do think your instructions are broken. On a clean installation, awn-curves fail to show up in the themes. I'll reinstall, but you should test your instructions too (just grab virtualbox and install ubuntu in it).
Hrm... I don't know whats wrong...  Very odd...
> **Vadi said:**
> Still not working... it just isn't appearing in the themes section. And this really sucks, because AWN is the only dock I use that has the capability *not* to look like a knock-off OS X dock.
:cry:
> **Kivech said:**
> Ok, first off, awesome guide!

I have it working, but I have some oddities going on though.

Let me start with the installation. I did an install on a clean installation of Ubuntu 7.10. AWN itself ran fine from scratch, the curved add-on had some small problems however.

At the second last step I had this as a result:

marc@marc-desktop:~/awn-curves$ sudo apt-get update
~
*snip*
~
W: Duplicate sources.list entry [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages (/var/lib/apt/lists/download.tuxfamily.org_syzygy42_dists_gutsy_avant-window-navigator_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

marc@marc-desktop:~/awn-curves$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
avant-window-navigator-bzr is already the newest version.
awn-core-applets-bzr is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
marc@marc-desktop:~/awn-curves$ 

I ran apt-get update a second time, but got the same error as displayed here.

At the second message I figured that all was ok and this was just a confirmation that I already had some needed elements installed. I just want to check if the previous error could have made the script maybe build some dependency errors as a result.

As a result, the command avant-window-navigator doesn't do anything anymore. Instead I have to manually start the application from /[my home dir]/awn-curves/src/avant-window-navigator.

Not too much of a big deal. I just have to change the paths in the icon properties and the session list, but it would be nice if it were to work the way it is supposed to. Any ideas how I can get it so that I can run avant-window-navigator without having to go to this specific directory?

Forgive me, been out of the Linux scene for over 10 years, so consider me a complete newb here.

Then, the AWN curve itself:

The default set of applets that one can add don't follow the line of the curve but the added shortcuts do.

Let me put it this way: if I add just applets that come with AWN, they will all sit at the bottom of my screen (in some cases the bottom sinks off my screen, and I have no clue why), but manually added shortcuts to programs nicely follow the curve.
Is there a way I can change this? It seems that the icon offset in some situations doesn't work well. The same goes for opened windows btw, those also follow the curve properly.

I even tried it in 3D mode, and here also the default offset of the icons makes them sink a few pixels below the bottom edge of my screen. Easy to adjust, yes, but not a nice finish.

When I try to switch back to the original AWN mode (flat panel) it closes down and doesn't come back up unless I pick either 3D or curved mode. Is there a way to fix this also? It's pretty handy to be able to go back to the original mode for sake of comparison. Now there's no way for me to see if the offset in the original mode has the same oddities as well.

Thanks in advance for your help.

Kivech

Did you remove the previous installation of awn? It says it's already installed, be sure to run those instructions at the top! :)

---

### Post by Kivech on 2008-02-14
Right, let me go for a reinstall :p

---

### Post by nikoPSK on 2008-02-14
> **Kivech said:**
> Right, let me go for a reinstall :p
Enjoy awn after. :)

---

### Post by Kivech on 2008-02-14
> **nikoPSK said:**
> Enjoy awn after. :)

Finished it a bit ago, and it's working like a charm! Thanks a lot mate, really appreciate the guide.

Kivech

---

### Post by nikoPSK on 2008-02-14
> **Kivech said:**
> Finished it a bit ago, and it's working like a charm! Thanks a lot mate, really appreciate the guide.

Kivech

No problem. :)

---

### Post by BuntuFreak on 2008-02-15
wonderful guide. I used it on one laptop and worked great, on another laptop i get error in the last step

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets.bzr

Any suggestions

---

### Post by reacocard on 2008-02-15
> **BuntuFreak said:**
> wonderful guide. I used it on one laptop and worked great, on another laptop i get error in the last step

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets.bzr

Any suggestions

you misstyped the command, it's -bzr not .bzr.

---

### Post by Comhra on 2008-02-15
Been using it for a couple of weeks now, very staple and beautiful not to mention functional.

---

### Post by eoika on 2008-02-16
hi everybody

the error I get is

```

laura@eoika:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build avant-panel-menu.  Download the appropriate package for
  from your distribution or get the source tarball at
    ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz

checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?


```

what should I do?

thanks!

---

### Post by nikoPSK on 2008-02-16
> **Comhra said:**
> Been using it for a couple of weeks now, very staple and beautiful not to mention functional.

Glad you enjoy. :)

> **eoika said:**
> hi everybody

the error I get is

```

laura@eoika:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build avant-panel-menu.  Download the appropriate package for
  from your distribution or get the source tarball at
    ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz

checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
  glib-gettext.m4 not found
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?


```what should I do?

thanks!
I've had this before... actually I know the problem is gettext... hrm, try getting the tarball.

---

### Post by eoika on 2008-02-16
sorry but I do not know what a tarball is and what I have to do with it..
thanks

---

### Post by eoika on 2008-02-16
ok I understood now,sorry, I have the package, now do I have to...install it?

---

### Post by maka on 2008-02-16
these instructions worked perfectly except I had to throw sudo in front of all of them.  thanks for the guide!

i have two questions:
-how do i know what version of awn i am using?
-how do i know when updates are available?

thanks again for the guide!:KS

---

### Post by maxehhh on 2008-02-16
well i get this problem:

> root@bl1zzard:/home/bl1zzard/awn-curves# apt-get install libawn-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libawn-bzr: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages


Tried Fix Broken Packages in Synaptic but still the same error, tried installing libpango but i don't get any error 

> root@bl1zzard:/home/bl1zzard/awn-curves# apt-get install libpango1.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpango1.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 

After this i try the same command as above [b]sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
[/b] but the same error =(.

---

### Post by reacocard on 2008-02-16
> **maxehhh said:**
> Tried Fix Broken Packages in Synaptic but still the same error, tried installing libpango but i don't get any error 

you have to have ubuntu-updates enabled.

---

### Post by maxehhh on 2008-02-16
> **reacocard said:**
> you have to have ubuntu-updates enabled.

**** me, i bet that's the same reason why i couldn't install wine, because i disabled the updates, thanks and i will post or edit this post when the update is done.

---

### Post by Rylin on 2008-02-16
I did everything right but this is what i get. How do i get the curve?

[[IMG]http://img137.imageshack.us/img137/5475/dockgw0.th.jpg[/IMG]](http://img137.imageshack.us/my.php?image=dockgw0.jpg)

---

### Post by nikoPSK on 2008-02-16
> **Rylin said:**
> I did everything right but this is what i get. How do i get the curve?

[[IMG]http://img137.imageshack.us/img137/5475/dockgw0.th.jpg[/IMG]]("http://img137.imageshack.us/my.php?image=dockgw0.jpg")

apply the curved theme.

> **maka said:**
> these instructions worked perfectly except I had to throw sudo in front of all of them.  thanks for the guide!

i have two questions:
-how do i know what version of awn i am using?
-how do i know when updates are available?

thanks again for the guide!:KS

they will appear in update manager. It says the updated version # there too

> **eoika said:**
> ok I understood now,sorry, I have the package, now do I have to...install it?

Yes

---

### Post by Rylin on 2008-02-16
This is what its set to in the preferences, yet I'm still not getting the curve. :confused:

[[IMG]http://img218.imageshack.us/img218/5053/curvenj3.th.jpg[/IMG]](http://img218.imageshack.us/my.php?image=curvenj3.jpg)

---

### Post by ddaddy2420 on 2008-02-17
AWN not showing up, i get this in terminal when i type avant-window-navigator

avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_gconf_new

---

### Post by Dark Star on 2008-02-17
I removed Avant and now when I try to install it it did not download the file .. 
```

shashwat@shashwat-desktop:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
autotools-dev is already the newest version.
autotools-dev set to manual installed.
libxdamage-dev is already the newest version.
libxdamage-dev set to manual installed.
libxcomposite-dev is already the newest version.
libxcomposite-dev set to manual installed.
libgnome2-common is already the newest version.
libgnome2-dev is already the newest version.
libgnome2-dev set to manual installed.
libgtk2.0-dev is already the newest version.
libgtk2.0-dev set to manual installed.
libgconf2-dev is already the newest version.
libgconf2-dev set to manual installed.
libglib2.0-dev is already the newest version.
libglib2.0-dev set to manual installed.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
python-gconf is already the newest version.
The following extra packages will be installed:
  gconf indent libgconf-dev libgconf11 libglib1.2 libglib1.2-dev
  libgnome-vfs-common libgnome-vfs0 libgtk1.2 libgtk1.2-common liboaf-dev
  liboaf0 liborbit-dev liborbit0 libstartup-notification0-dev libwrap0-dev
  libxml1 libxres-dev oaf python-gobject-dev python-pyorbit-dev python2.5-dev
  x11proto-resource-dev
Suggested packages:
  nfs-common gnome-vfs-extfs
Recommended packages:
  orbit python-gnome2-extras-dev
The following NEW packages will be installed:
  gconf indent libdbus-glib-1-dev libgconf-dev libgconf11 libglib1.2
  libglib1.2-dev libgnome-desktop-dev libgnome-vfs-common libgnome-vfs-dev
  libgnome-vfs0 libgtk1.2 libgtk1.2-common liboaf-dev liboaf0 liborbit-dev
  liborbit0 libstartup-notification0-dev libwnck-dev libwrap0-dev libxml1
  libxres-dev oaf python-cairo-dev python-dev python-gnome2-dev
  python-gobject-dev python-gtk2-dev python-pyorbit-dev python2.5-dev
  x11proto-resource-dev
0 upgraded, 31 newly installed, 0 to remove and 0 not upgraded.
[B]Need to get 6470kB of archives.
After unpacking 23.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.[/B]

```

Why it is aborting the d/l ? What to do now ?

---

### Post by Kivech on 2008-02-17
nikoPSK,

Again, thanks for this guide, it works like a charm. However, I do have a request to make. 

At some point something odd happened and I lost one of the applets. I have no idea how it happened but I didn't find a way to restore it so I figured to go ahead with a reinstall.

Since your instructions assume all components have to be installed, in my reinstall process I ran into a lot of things that clearly were already on my system. Now for the newbies among us (like me) could you include a brief reinstall guide that excludes all the packages that should still be on your system after removal of AWN?

Then a second question: I have noticed two applets with minor bugs: the trash icon and the Quit/Logout icon. The first has a tendency to sink below it's position over time, and the second has a part on the left of the icon that at times is put in the different position than the rest of it resulting in a look as if part was cut off and placed in another position. Both are resolved by hovering your mouse over the icons, which basically resets them.

Where do I file bug reports on these? I really love AWN and would love to help out to make it look even better.

Oh, are there other themes for AWN curves available for download somewhere?

Kivech

---

### Post by nikoPSK on 2008-02-17
> **Rylin said:**
> This is what its set to in the preferences, yet I'm still not getting the curve. :confused:

[[IMG]http://img218.imageshack.us/img218/5053/curvenj3.th.jpg[/IMG]]("http://img218.imageshack.us/my.php?image=curvenj3.jpg")

Refresh awn and restart it if neeeded.
> **ddaddy2420 said:**
> AWN not showing up, i get this in terminal when i type avant-window-navigator

avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_gconf_new

Try a reinstall.

> **Dark Star said:**
> I removed Avant and now when I try to install it it did not download the file .. 
```

shashwat@shashwat-desktop:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
autotools-dev is already the newest version.
autotools-dev set to manual installed.
libxdamage-dev is already the newest version.
libxdamage-dev set to manual installed.
libxcomposite-dev is already the newest version.
libxcomposite-dev set to manual installed.
libgnome2-common is already the newest version.
libgnome2-dev is already the newest version.
libgnome2-dev set to manual installed.
libgtk2.0-dev is already the newest version.
libgtk2.0-dev set to manual installed.
libgconf2-dev is already the newest version.
libgconf2-dev set to manual installed.
libglib2.0-dev is already the newest version.
libglib2.0-dev set to manual installed.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
python-gconf is already the newest version.
The following extra packages will be installed:
  gconf indent libgconf-dev libgconf11 libglib1.2 libglib1.2-dev
  libgnome-vfs-common libgnome-vfs0 libgtk1.2 libgtk1.2-common liboaf-dev
  liboaf0 liborbit-dev liborbit0 libstartup-notification0-dev libwrap0-dev
  libxml1 libxres-dev oaf python-gobject-dev python-pyorbit-dev python2.5-dev
  x11proto-resource-dev
Suggested packages:
  nfs-common gnome-vfs-extfs
Recommended packages:
  orbit python-gnome2-extras-dev
The following NEW packages will be installed:
  gconf indent libdbus-glib-1-dev libgconf-dev libgconf11 libglib1.2
  libglib1.2-dev libgnome-desktop-dev libgnome-vfs-common libgnome-vfs-dev
  libgnome-vfs0 libgtk1.2 libgtk1.2-common liboaf-dev liboaf0 liborbit-dev
  liborbit0 libstartup-notification0-dev libwnck-dev libwrap0-dev libxml1
  libxres-dev oaf python-cairo-dev python-dev python-gnome2-dev
  python-gobject-dev python-gtk2-dev python-pyorbit-dev python2.5-dev
  x11proto-resource-dev
0 upgraded, 31 newly installed, 0 to remove and 0 not upgraded.
[B]Need to get 6470kB of archives.
After unpacking 23.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.[/B]

```Why it is aborting the d/l ? What to do now ?

Does it do that every time? I know that if you copy all the code on that one place you shouldn't it will abort.
> **Kivech said:**
> nikoPSK,

Again, thanks for this guide, it works like a charm. However, I do have a request to make. 

At some point something odd happened and I lost one of the applets. I have no idea how it happened but I didn't find a way to restore it so I figured to go ahead with a reinstall.

Since your instructions assume all components have to be installed, in my reinstall process I ran into a lot of things that clearly were already on my system. Now for the newbies among us (like me) could you include a brief reinstall guide that excludes all the packages that should still be on your system after removal of AWN?

Then a second question: I have noticed two applets with minor bugs: the trash icon and the Quit/Logout icon. The first has a tendency to sink below it's position over time, and the second has a part on the left of the icon that at times is put in the different position than the rest of it resulting in a look as if part was cut off and placed in another position. Both are resolved by hovering your mouse over the icons, which basically resets them.

Where do I file bug reports on these? I really love AWN and would love to help out to make it look even better.

Oh, are there other themes for AWN curves available for download somewhere?

Kivech

Trash icon is up to the developer, reinstall guide, all you really need to do is run the command and delete the awn-curves folder from home.

---

### Post by Dark Star on 2008-02-17
```
shashwat@shashwat-desktop:~$ cd awn-curves
bash: cd: awn-curves: No such file or directory
shashwat@shashwat-desktop:~$ ./autogen.sh && make
bash: ./autogen.sh: No such file or directory
shashwat@shashwat-desktop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
shashwat@shashwat-desktop:~$ 

``` Done everything but where is this directory ?

---

### Post by Kivech on 2008-02-17
> **nikoPSK said:**
> Trash icon is up to the developer, reinstall guide, all you really need to do is run the command and delete the awn-curves folder from home.

Ok, I got those two. Maybe I'm not making myself clear enough:

1) After I remove AWN according to your instructions, I install AWN again, according to your instructions. A whole list of stuff will give me messages that it's either already installed, already has the newest version, etc.
Now, if I (or anyone else for that matter) who is new to Linux sees that, they might panic and think things are going wrong. So for clarity sake I'd say: make a short tutorial for reinstallation of AWN.

Example: To reinstall AWN first remove it all according to instructions (ones you already posted). Then install AWN again according to these XXX instructions (no need to repeat YYY instructions since those packages are already installed on your system).

Something along those lines, since now your guide only covers a full install of all packages needed for AWN but only a PARTIAL removal of those packages (dependencies). In fact, the removal instructions are only for AWN itself, not for the other packages. So in reality that is not completely consistent in case someone new to Linux would have to reinstall AWN.
Anyway, you get my point. All you would have to do is take out all parts that you haven't got listed to remove in an uninstall (this includes the two lines appended to the sources.list file). Which would leave you with 3 instead of 2 guides:
(1) Install of AWN and dependencies
(2) Removal of AWN (but only the AWN packages, dependencies and edited sources.list remains untouched)
(3) Install of just AWN (considering the dependencies were already installed a previous time and not removed).

2) Then regarding the bug: Who developed each applet and where do I find them? Will be hard to submit bug reports if I have no clue who made them. I was hoping you would know where I could find the people behind the applet so I know *where* to file any bug reports.

Thanks again mate, keep up the great work.

Kivech

---

### Post by mech7 on 2008-02-17
Waaaa i get this error?

chris@chris-laptop:~$ avant-window-navigator
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_gconf_new
chris@chris-laptop:~$ 


What gives ?:confused:

---

### Post by ddaddy2420 on 2008-02-17
I am getting the same error as the poster above.  I reinstalled awn curves and it still will not show up.  I don't get any errors during installation and everything seems to go along according to your guide here.

---

### Post by Mad_Gouki on 2008-02-17
I am also getting this error.  It looks like it is a missing library or something like that (I really don't know to be honest)
here is a thread I found on the AWN forums about the same thing (a google search for awn_conf_new gives tons of results of the same error)
[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=933&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=933&page=1&isLive=true)
```
This error has nothing to do with gconf keys.




avant-window-navigator can't find a libawn that contains the function awn_gconf_new. If you installed awn in a non-standard prefix, you need to add the lib directory to LD_LIBRARY_PATH.




Example:
I install awn in the prefix "~/programs/awn" via `./configure --prefix=$HOME/programs/awn ...[more configure flags] && make all install`. So, when I run avant-window-navigator, I use this on the command line:




LD_LIBRARY_PATH=$HOME/programs/awn/lib ~/programs/awn/bin/avant-window-navigator
```
I think it means that the library is there, it just can't find it in there.
I'm not sure what he means by "use this on the command line", but it would be something like
LD_LIBRARY_PATH=$HOME/awn-curves/libawn ~/awn-curves/libawn
I'm not sure what the 2 parts mean to the command, so I'm not really sure what to set them to.

edit: reinstalled it and it works now, thank you for making it :D

---

### Post by ImAnOgre on 2008-02-17
nikoPSK'

Just wanted to say thanks.  Your original post worked flawlessly and I have a curved dock bar now.
[img]http://www.forumup.com/images/smiles/slider_thankyou.gif[/img]

---

### Post by entrapmen on 2008-02-18
Thanks for the Guide.

I've installed AVN without any errors. It seems okay, but i cant add applets, launchers and neither themes to dock.

When i try to add Applet, launcher or theme it turns nothing (i tried this by opening avn and avn-manager on console there was no error message.)

Any ideas?

---

### Post by Dark Star on 2008-02-18
Got it working.. Thanks a ton bro. Nice guide :)

---

### Post by nikoPSK on 2008-02-21
> **Kivech said:**
> Ok, I got those two. Maybe I'm not making myself clear enough:

1) After I remove AWN according to your instructions, I install AWN again, according to your instructions. A whole list of stuff will give me messages that it's either already installed, already has the newest version, etc.
Now, if I (or anyone else for that matter) who is new to Linux sees that, they might panic and think things are going wrong. So for clarity sake I'd say: make a short tutorial for reinstallation of AWN.

Example: To reinstall AWN first remove it all according to instructions (ones you already posted). Then install AWN again according to these XXX instructions (no need to repeat YYY instructions since those packages are already installed on your system).

Something along those lines, since now your guide only covers a full install of all packages needed for AWN but only a PARTIAL removal of those packages (dependencies). In fact, the removal instructions are only for AWN itself, not for the other packages. So in reality that is not completely consistent in case someone new to Linux would have to reinstall AWN.
Anyway, you get my point. All you would have to do is take out all parts that you haven't got listed to remove in an uninstall (this includes the two lines appended to the sources.list file). Which would leave you with 3 instead of 2 guides:
(1) Install of AWN and dependencies
(2) Removal of AWN (but only the AWN packages, dependencies and edited sources.list remains untouched)
(3) Install of just AWN (considering the dependencies were already installed a previous time and not removed).

2) Then regarding the bug: Who developed each applet and where do I find them? Will be hard to submit bug reports if I have no clue who made them. I was hoping you would know where I could find the people behind the applet so I know *where* to file any bug reports.

Thanks again mate, keep up the great work.

Kivech
I have been very busy lately, when I have time. :)
> **mech7 said:**
> Waaaa i get this error?

chris@chris-laptop:~$ avant-window-navigator
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_gconf_new
chris@chris-laptop:~$ 


What gives ?:confused:

try a reinstall please

> **Mad_Gouki said:**
> I am also getting this error.  It looks like it is a missing library or something like that (I really don't know to be honest)
here is a thread I found on the AWN forums about the same thing (a google search for awn_conf_new gives tons of results of the same error)
[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=933&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=933&page=1&isLive=true)
```
This error has nothing to do with gconf keys.




avant-window-navigator can't find a libawn that contains the function awn_gconf_new. If you installed awn in a non-standard prefix, you need to add the lib directory to LD_LIBRARY_PATH.




Example:
I install awn in the prefix "~/programs/awn" via `./configure --prefix=$HOME/programs/awn ...[more configure flags] && make all install`. So, when I run avant-window-navigator, I use this on the command line:




LD_LIBRARY_PATH=$HOME/programs/awn/lib ~/programs/awn/bin/avant-window-navigator
```I think it means that the library is there, it just can't find it in there.
I'm not sure what he means by "use this on the command line", but it would be something like
LD_LIBRARY_PATH=$HOME/awn-curves/libawn ~/awn-curves/libawn
I'm not sure what the 2 parts mean to the command, so I'm not really sure what to set them to.

edit: reinstalled it and it works now, thank you for making it :D

Good for you. :)

> **ImAnOgre said:**
> nikoPSK'

Just wanted to say thanks.  Your original post worked flawlessly and I have a curved dock bar now.
[IMG]http://www.forumup.com/images/smiles/slider_thankyou.gif[/IMG]
No problem, you can click the little medal at the bottom of the guide post. :)
> **entrapmen said:**
> Thanks for the Guide.

I've installed AVN without any errors. It seems okay, but i cant add applets, launchers and neither themes to dock.

When i try to add Applet, launcher or theme it turns nothing (i tried this by opening avn and avn-manager on console there was no error message.)

Any ideas?

I don't really know, generally a reinstall fixes such anomalies. 

> **Dark Star said:**
> Got it working.. Thanks a ton bro. Nice guide :)

No problem.

---

### Post by DreamClown on 2008-02-21
Hi all,
I had successfully installed AWN via another thread on the forums. However, the applets did not work. So, I found this thread and thought I would un-install and try this. I don't think I'm getting a clean un-install though even though I used the code at the beginning of this thread. This is the output after I give the final command in the installation process:


jason@jason-laptop:~/awn-curves$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libawn-bzr python-libawn-bzr
Recommended packages:
  avant-window-navigator
The following NEW packages will be installed:
  avant-window-navigator-bzr awn-core-applets-bzr libawn-bzr python-libawn-bzr
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2976kB of archives.
After unpacking 11.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 103199 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Unpacking avant-window-navigator-bzr (from .../avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/avant-window-navigator/defs/awn.defs', which is also in package python-awn
Unpacking python-libawn-bzr (from .../python-libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr158-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.5/site-packages/awn/awn.so', which is also in package python-awn
Selecting previously deselected package awn-core-applets-bzr.
Unpacking awn-core-applets-bzr (from .../awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb
 /var/cache/apt/archives/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb
 /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr158-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas about how to overcome this? Thanks in advance for your help!

Peace,
~DC~

---

### Post by reacocard on 2008-02-21
> **DreamClown said:**
> Hi all,
I had successfully installed AWN via another thread on the forums. However, the applets did not work. So, I found this thread and thought I would un-install and try this. I don't think I'm getting a clean un-install though even though I used the code at the beginning of this thread. This is the output after I give the final command in the installation process:


<snip>

Any ideas about how to overcome this? Thanks in advance for your help!

Peace,
~DC~

you need to completely remove the previous awn install first, specifically, the packages libawn0 and python-awn.

---

### Post by DreamClown on 2008-02-21
> **reacocard said:**
> you need to completely remove the previous awn install first, specifically, the packages libawn0 and python-awn.

Yep, I used Synaptic to remove those two packages and then re-installed. Works great now! Thanks!

Peace,
~DC~

---

### Post by Mad_Gouki on 2008-02-22
I had awn-curves working perfectly, the only problem was occasional crashes after the pc went to screen savers.
I can't use my applets now, they all show up as a white bar,  I installed an update from the update manager from the repositories that did it, it was awn-applets or something like that (that wasn't its exact name),  Does anyone know how to remove this, or where it would have installed to?  I think removing this and reinstalling awn-curves might fix the problem.  It seems like it is a conflict between the awn-curves applets and the regular awn applets from the update.

edit:
the package is called awn-core-applets-bzr
uninstalling the version 3 and reverting back to version 2 seems to have fixed the problem (without having to reinstall awn-curves)
I'm not really sure why (as I'm a newbie), but it seems to me that the new version of the awn-core-applets-bzr file makes the applets incompatible with awn-curves
an older version that works(for me at least) is available at the ubuntu archive: [http://archive.ubuntu.ir/ubuntu/pool/main/a/awn-core-applets-bzr/](http://archive.ubuntu.ir/ubuntu/pool/main/a/awn-core-applets-bzr/)
If someone else could try the new awn-core-applets-bzr and let me know if they also experience the problem, it might be helpful to the developer of awn-curves, and it would also make me feel a little less crazy ;)
if you are having issues with the applets, possibly due to the command: sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
grabbing the version from the archive may fix the problem, so just do: sudo apt-get install avant-window-navigator-bzr
and grab the awn-core-applets-bzr deb from the link provided.
or if you already ran that command and are having applet problems, just go into synaptics and remove the package and then add the old 1 from the archive.

---

### Post by mech7 on 2008-02-22
Did anybody else had problems with AWN.. it stopped working after the update of yesterday ?

---

### Post by harold4 on 2008-02-22
All is well here.

---

### Post by alsamman on 2008-02-23
well im not sure if someone already asked this (im not in the mood to look through 85 pages), but sometimes when I boot awn, all the icons will be covered by a white bar, icons not visible. I know that closing it and reopening it will fix it but i am just wondering why this occurs in the first place and if there is a way that can make it so that it doesnt happen to begin with

---

### Post by KoolPenguin on 2008-02-26
> **mab1376 said:**
> when i try and start it up i get this message

```
mark@mark-laptop:~$ avant-window-navigator
Screen is composited.
Segmentation fault (core dumped)
mark@mark-laptop:~$ 

```

This is for anyone who has this error.

I tried to re-install AWN w/curves and it kept saying the packages were broken, etc. I did manage to get it working and not sure if this will work for others but this is what I did.

- remove/un-install AWN and all related packages with Synaptic Manager
- remove/comment out the repos you added to the sources.list from the instructions at the beginning of this thread
- add "deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main" to your sources.list (without the quotes)
- run sudo apt-get update in terminal
- install the following packages from Synaptic Manager

avant-window-navigator-bzr
awn-core-applets-bzr
awn-manager-bzr
libawn-bzr
python-libawn-bzr

I'm not an expert but I now have the AWN w/curves and lots of applets to add.  Give it a try and let us know if it works for you.

Also, I'm not trying to take over this thread, the instructions do work for a lot of others and for the few it does not, these instructions may.  Maybe the OP can compare these bzr packages to theirs to find out the problem.  I wonder if it is an ATI graphics problem?

---

### Post by reacocard on 2008-02-26
> **KoolPenguin said:**
> This is for anyone who has this error.

I tried to re-install AWN w/curves and it kept saying the packages were broken, etc. I did manage to get it working and not sure if this will work for others but this is what I did.

- remove/un-install AWN and all related packages with Synaptic Manager
- remove/comment out the repos you added to the sources.list from the instructions at the beginning of this thread
- add "deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main" to your sources.list (without the quotes)
- run sudo apt-get update in terminal
- install the following packages from Synaptic Manager

avant-window-navigator-bzr
awn-core-applets-bzr
awn-manager-bzr
libawn-bzr
python-libawn-bzr

I'm not an expert but I now have the AWN w/curves and lots of applets to add.  Give it a try and let us know if it works for you.

Also, I'm not trying to take over this thread, the instructions do work for a lot of others and for the few it does not, these instructions may.  Maybe the OP can compare these bzr packages to theirs to find out the problem.  I wonder if it is an ATI graphics problem?

This is NOT a good way to do this. The -bzr packages used in that repo you link to have curves partially merged into them already. Installing another version of curves over the top of that is a BAD IDEA.  The -bzr packages the author of this thread is using are from before this merge and are therefore safe to install curves over. 

Note that AWN 0.4 will have curves included by default, so if you can wait a little while I would advise getting normal AWN with [this guide]("http://ubuntuforums.org/showthread.php?p=4409134"), and then you will get curves when they become officially available.

---

### Post by kapst0k on 2008-02-27
Super thanks

---

### Post by shadmy on 2008-02-28
:lolflag: thanks so much for this 

i was searching for that ..:lolflag:... 


u are a Star  :KS

---

### Post by nikoPSK on 2008-02-29
> **harold4 said:**
> All is well here. Good. :)

> **shadmy said:**
> :lolflag: thanks so much for this 

i was searching for that ..:lolflag:... 


u are a Star  :KS :KS Glad I am. :p

> **kapst0k said:**
> Super thanks

> **alsamman said:**
> well im not sure if someone already asked this (im not in the mood to look through 85 pages), but sometimes when I boot awn, all the icons will be covered by a white bar, icons not visible. I know that closing it and reopening it will fix it but i am just wondering why this occurs in the first place and if there is a way that can make it so that it doesnt happen to begin with
Covered? Normally it's just vertical white line, and that's an applet failing to load.


Sorry, I am on a trip, and it's hard to find time for ubuntuforums lately.

---

### Post by rhyguy on 2008-02-29
after typing wget 
```
http://download.tuxfamily.org/syzygy...158-1_i386.deb http://download.tuxfamily.org/syzygy...296-1_i386.deb http://download.tuxfamily.org/syzygy...158-1_i386.deb http://download.tuxfamily.org/syzygy...158-1_i386.deb http://download.tuxfamily.org/syzygy...158-1_i386.deb 
sudo dpkg -i *.deb
```
i get
```
 => `syzygy...158-1_i386.deb'
Resolving download.tuxfamily.org... 
88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:46:23 ERROR 404: Not Found.

--15:46:23--  http://download.tuxfamily.org/syzygy...296-1_i386.deb
           => `syzygy...296-1_i386.deb'
Reusing existing connection to download.tuxfamily.org:80.
HTTP request sent, awaiting response... 404 Not Found
15:46:23 ERROR 404: Not Found.

--15:46:23--  http://download.tuxfamily.org/syzygy...158-1_i386.deb
           => `syzygy...158-1_i386.deb'
Reusing existing connection to download.tuxfamily.org:80.
HTTP request sent, awaiting response... 404 Not Found
15:46:24 ERROR 404: Not Found.

--15:46:24--  http://download.tuxfamily.org/syzygy...158-1_i386.deb
           => `syzygy...158-1_i386.deb'
Reusing existing connection to download.tuxfamily.org:80.
HTTP request sent, awaiting response... 404 Not Found
15:46:24 ERROR 404: Not Found.

--15:46:24--  http://download.tuxfamily.org/syzygy...158-1_i386.deb
           => `syzygy...158-1_i386.deb'
Reusing existing connection to download.tuxfamily.org:80.
HTTP request sent, awaiting response... 404 Not Found
15:46:24 ERROR 404: Not Found.


FINISHED --15:46:24--
Downloaded: 0 bytes in 0 files
rhyguy@Desktop:~/awn-curves$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

```

---

### Post by nikoPSK on 2008-03-01
> **rhyguy said:**
> <snip>
Sadly, I do not know much of this, as recocard implemented it. I am sure he could help you though. :)

---

### Post by reacocard on 2008-03-01
> **nikoPSK said:**
> Sadly, I do not know much of this, as recocard implemented it. I am sure he could help you though. :)

the urls got truncated, here are the correct versions:

32bit:
```
wget http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr-dev_0.2.0-bzr158-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr_0.2.0-bzr158-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/python-libawn-bzr_0.2.0-bzr158-1_i386.deb 
sudo dpkg -i *.deb
```

64bit:
```
wget http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/avant-window-navigator-bzr_0.2.0-bzr166-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/awn-core-applets-bzr_0.2.0-bzr300-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/libawn-bzr-dev_0.2.0-bzr166-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/libawn-bzr_0.2.0-bzr166-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/python-libawn-bzr_0.2.0-bzr166-1_amd64.deb 
sudo dpkg -i *.deb
```



@Niko: you also need to drop the part about the gpg key and apt-get, they're not needed and in fact will fail with this method.

---

### Post by rhyguy on 2008-03-01
now i get
```
rhyguy@desktop:~/awn-curves$ sudo dpkg -i *.deb
Selecting previously deselected package avant-window-navigator-bzr.
(Reading database ... 96641 files and directories currently installed.)
Unpacking avant-window-navigator-bzr (from avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb) ...
Selecting previously deselected package awn-core-applets-bzr.
Unpacking awn-core-applets-bzr (from awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb) ...
Selecting previously deselected package libawn-bzr.
Unpacking libawn-bzr (from libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
Selecting previously deselected package libawn-bzr-dev.
Unpacking libawn-bzr-dev (from libawn-bzr-dev_0.2.0-bzr158-1_i386.deb) ...
Selecting previously deselected package python-libawn-bzr.
Unpacking python-libawn-bzr (from python-libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: dependency problems prevent configuration of avant-window-navigator-bzr:
 avant-window-navigator-bzr depends on libpango1.0-0 (>= 1.18.3); however:
  Version of libpango1.0-0 on system is 1.18.2-0ubuntu1.
dpkg: error processing avant-window-navigator-bzr (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of awn-core-applets-bzr:
 awn-core-applets-bzr depends on libpango1.0-0 (>= 1.18.3); however:
  Version of libpango1.0-0 on system is 1.18.2-0ubuntu1.
dpkg: error processing awn-core-applets-bzr (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libawn-bzr:
 libawn-bzr depends on libpango1.0-0 (>= 1.18.3); however:
  Version of libpango1.0-0 on system is 1.18.2-0ubuntu1.
dpkg: error processing libawn-bzr (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libawn-bzr-dev:
 libawn-bzr-dev depends on libawn-bzr (= 0.2.0-bzr158-1); however:
  Package libawn-bzr is not configured yet.
dpkg: error processing libawn-bzr-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-libawn-bzr:
 python-libawn-bzr depends on libawn-bzr (= 0.2.0-bzr158-1); however:
  Package libawn-bzr is not configured yet.
dpkg: error processing python-libawn-bzr (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 avant-window-navigator-bzr
 awn-core-applets-bzr
 libawn-bzr
 libawn-bzr-dev
 python-libawn-bzr


```

---

### Post by reacocard on 2008-03-01
> **rhyguy said:**
> now i get
```
rhyguy@desktop:~/awn-curves$ sudo dpkg -i *.deb
Selecting previously deselected package avant-window-navigator-bzr.
(Reading database ... 96641 files and directories currently installed.)
Unpacking avant-window-navigator-bzr (from avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb) ...
Selecting previously deselected package awn-core-applets-bzr.
Unpacking awn-core-applets-bzr (from awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb) ...
Selecting previously deselected package libawn-bzr.
Unpacking libawn-bzr (from libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
Selecting previously deselected package libawn-bzr-dev.
Unpacking libawn-bzr-dev (from libawn-bzr-dev_0.2.0-bzr158-1_i386.deb) ...
Selecting previously deselected package python-libawn-bzr.
Unpacking python-libawn-bzr (from python-libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: dependency problems prevent configuration of avant-window-navigator-bzr:
 avant-window-navigator-bzr depends on libpango1.0-0 (>= 1.18.3); however:
  Version of libpango1.0-0 on system is 1.18.2-0ubuntu1.
dpkg: error processing avant-window-navigator-bzr (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of awn-core-applets-bzr:
 awn-core-applets-bzr depends on libpango1.0-0 (>= 1.18.3); however:
  Version of libpango1.0-0 on system is 1.18.2-0ubuntu1.
dpkg: error processing awn-core-applets-bzr (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libawn-bzr:
 libawn-bzr depends on libpango1.0-0 (>= 1.18.3); however:
  Version of libpango1.0-0 on system is 1.18.2-0ubuntu1.
dpkg: error processing libawn-bzr (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libawn-bzr-dev:
 libawn-bzr-dev depends on libawn-bzr (= 0.2.0-bzr158-1); however:
  Package libawn-bzr is not configured yet.
dpkg: error processing libawn-bzr-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-libawn-bzr:
 python-libawn-bzr depends on libawn-bzr (= 0.2.0-bzr158-1); however:
  Package libawn-bzr is not configured yet.
dpkg: error processing python-libawn-bzr (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 avant-window-navigator-bzr
 awn-core-applets-bzr
 libawn-bzr
 libawn-bzr-dev
 python-libawn-bzr


```

ah, forgot about dependencies. take 3:


32bit:
```
wget http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr-dev_0.2.0-bzr158-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr_0.2.0-bzr158-1_i386.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/python-libawn-bzr_0.2.0-bzr158-1_i386.deb 
sudo gdebi *.deb
```

64bit:
```
wget http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/avant-window-navigator-bzr_0.2.0-bzr166-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/awn-core-applets-bzr_0.2.0-bzr300-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/libawn-bzr-dev_0.2.0-bzr166-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/libawn-bzr_0.2.0-bzr166-1_amd64.deb http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/amd64/python-libawn-bzr_0.2.0-bzr166-1_amd64.deb 
sudo gdebi *.deb
```

---

### Post by MorningView425 on 2008-03-02
hi, i've been following this same problem and when i plugged in the latest text i get

"This package is uninstallable
Dependency is not satisfiable:  libawn-bzr"

any ideas?  thx

---

### Post by billybag on 2008-03-03
i am having trouble getting the auto-hide function to work. i have tried reinstalling, complete removal and then reinstalling, nothing...

i managed to kind of get it to work. i completely removed it and then, due to a weird bug that causes the black theme to not work, it works with glass some times

---

### Post by nikoPSK on 2008-03-04
> **MorningView425 said:**
> hi, i've been following this same problem and when i plugged in the latest text i get

"This package is uninstallable
Dependency is not satisfiable:  libawn-bzr"

any ideas?  thx

Hrm... Sorry, I don't really know with the updates and all...

> **billybag said:**
> i am having trouble getting the auto-hide function to work. i have tried reinstalling, complete removal and then reinstalling, nothing...

i managed to kind of get it to work. i completely removed it and then, due to a weird bug that causes the black theme to not work, it works with glass some times
Err, I knew it would stick out a bit from the top... 

Reacocard... So these portions?

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
```

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
``` :)

---

### Post by joshrobinson on 2008-03-05
> **MorningView425 said:**
> hi, i've been following this same problem and when i plugged in the latest text i get

"This package is uninstallable
Dependency is not satisfiable:  libawn-bzr"

any ideas?  thx

well either this is an old howto, or its missing a few steps:

run these commands one at a time
```

echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'  |  sudo tee -a /etc/apt/sources.list

echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'  |  sudo tee -a /etc/apt/sources.list

```

then run

```

sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

```

last do the following command in your awn folder, as the howto tells you
```

sudo gdebi *.deb

```

thats what i did to clear up the same error you had

---

### Post by reacocard on 2008-03-05
> **nikoPSK said:**
> Hrm... Sorry, I don't really know with the updates and all...


Err, I knew it would stick out a bit from the top... 

Reacocard... So these portions?

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
```

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
``` :)

correct

> **joshrobinson said:**
> well either this is an old howto, or its missing a few steps:

run these commands one at a time
```

echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'  |  sudo tee -a /etc/apt/sources.list

echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main'  |  sudo tee -a /etc/apt/sources.list

```

then run

```

sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

```

last do the following command in your awn folder, as the howto tells you
```

sudo gdebi *.deb

```

thats what i did to clear up the same error you had

NO. THERE IS NO REPOSITORY OR PPA INVOLVED ANYMORE. Curves will be merged into trunk soon and will then be in that PPA you use. Until then, use the archived debs I've provided in lieu of a repo.

---

### Post by white_eagle-mk on 2008-03-06
Dude I can't run awn, I followed your instructions EXACTLY as shown, but when I do <code> sudo gdebi *.deb </code>  in the awn-curves folder I get <code> Dependency is not satisfiable: libawn-bzr </code> . I installed libawn-bzr using sudo apt-get install libawn-bzr, and when I do again sudo gdebi *.deb I get the same error :(:(:(:(

Thanks.

***Nevermind I fixed it, by looking upwards the page ;)

---

### Post by nikoPSK on 2008-03-06
Updated my guide.

---

### Post by NOLU on 2008-03-06
I never get an AWN curve folder when I enter the command so can't go from there (I think). I have already got AWN working but would like to get the curve,

A bit of a noob at this so sorry if this has been done 1000 times.

---

### Post by sweetfishremix on 2008-03-06
vu@vu-laptop:~/awn-curves$ sudo gdebi *.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
Dependency is not satisfiable: libawn-bzr


HELPPPPP!! ALMOST DONE WITH INSTALATION T_T

---

### Post by Sphearion on 2008-03-07
> vu@vu-laptop:~/awn-curves$ sudo gdebi *.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
Dependency is not satisfiable: libawn-bzr


HELPPPPP!! ALMOST DONE WITH INSTALATION T_T

Ok, the simple way of doing this is to run sudo gdebi libawn-bzr*.deb

then after those install run the sudo gdebi *.deb again. and all should work fine ;)

---

### Post by CWaugh on 2008-03-08
> **Sphearion said:**
> Ok, the simple way of doing this is to run sudo gdebi libawn-bzr*.deb

then after those install run the sudo gdebi *.deb again. and all should work fine ;)

Thank You!!  I was having that exact problem.

---

### Post by quadm on 2008-03-11
For some reason i've been getting this message. an hour of googling and troubleshooting didnt do anything.
any help would be appreciated. 

```
./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.23
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE
Running autoconf...
Running autoheader...
Running automake-1.9...
Processing ./awn-curves/configure.in
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `..'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite
andrew@andrew-laptop:~/awn-curves$ ./autogen.sh --prefix=/usr/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.23
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.in
Running libtoolize...
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE
Running autoconf...
Running autoheader...
Running automake-1.9...
Processing ./awn-curves/configure.in
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `..'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...

```

Thanks.

---

### Post by sayantandas on 2008-03-13
hi all
i'm getting the following error after using the command  *sudo gdebi libawn-bzr*.deb*



library for Avant Window Navigator applets
 Library for Avant Window Navigator applets.
Do you want to install the software package? [y/N]:y
Selecting previously deselected package libawn-bzr.
(Reading database ... 136861 files and directories currently installed.)
Unpacking libawn-bzr (from libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: error processing libawn-bzr_0.2.0-bzr158-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 libawn-bzr_0.2.0-bzr158-1_i386.deb

---

### Post by reacocard on 2008-03-13
> **sayantandas said:**
> hi all
i'm getting the following error after using the command  *sudo gdebi libawn-bzr*.deb*



library for Avant Window Navigator applets
 Library for Avant Window Navigator applets.
Do you want to install the software package? [y/N]:y
Selecting previously deselected package libawn-bzr.
(Reading database ... 136861 files and directories currently installed.)
Unpacking libawn-bzr (from libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: error processing libawn-bzr_0.2.0-bzr158-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 libawn-bzr_0.2.0-bzr158-1_i386.deb

completely remove any old awn installations first.

---

### Post by sayantandas on 2008-03-13
> **reacocard said:**
> completely remove any old awn installations first.

thanks for the reply.. but i deleted installtions completely 2 times b4...
should i remove the awm- curves folder and do a fresh download as well?

---

### Post by muximus on 2008-03-13
i think u can get the same curved look if u go to gconf editor>apps>avant...>bar>bar angle 
and change the value to -1, no need to install nething new

---

### Post by reacocard on 2008-03-13
> **muximus said:**
> i think u can get the same curved look if u go to gconf editor>apps>avant...>bar>bar angle 
and change the value to -1, no need to install nething new

if you're running the latest from my PPA or trunk then yes, that will indeed give you curves.

---

### Post by sayantandas on 2008-03-13
> **muximus said:**
> i think u can get the same curved look if u go to gconf editor>apps>avant...>bar>bar angle 
and change the value to -1, no need to install nething new

thanks but what about the addons and applets?
can i not install them?

---

### Post by sayantandas on 2008-03-13
after much googling around in this forum i found this thread

[http://ubuntuforums.org/showthread.php?t=385981&highlight=kiba](http://ubuntuforums.org/showthread.php?t=385981&highlight=kiba)

and after following the instructions correctly there i was able to install awn correctly 

thanks to all of you who tried to help me.

PS: i still think kiba-dock has a better animation , just that it doesn't load a startup i had to switch to awn.

---

### Post by OzzyFrank on 2008-03-15
I installed via your instructions fine (except the end bit  **sudo gdebi *.deb** told me [COLOR="DarkRed"]**gdebi error, file not found: *.deb**[/COLOR]) and the 3D Curves ended up as an option in AWN Manager (except I never got the curves, just a thinner 3D look bar), but after a reboot there is no AWN. I try to start it with the icon and nothing, not even as a running process. Trying via the terminal returns:

[COLOR="#8b0000"]**avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_gconf_new**[/COLOR]

AWN Manager loads though, but is no help (I tried a few things, and going back to some previous settings). Still no AWN. I am running Gutsy 64-bit if that helps.

---

### Post by OzzyFrank on 2008-03-15
OK, I figured I'd look through these many pages to see if someone had the some problem, and many did, with removal and reinstallation via the instructions being the default answer. I soon saw what others were saying, that it was going nowhere coz all the libraries well already installed etc.

So I tried something that rarely ever fixes anything, being a **Reinstallation via Synaptic**. Sure enough, it worked, and interestingly it told me it needed to download 1 package, being avant-window-navigator-bzr, which - to my knowledge - I had already gotten the lastest of (as in, in the last couple of hours while doing all this).

But there you go - it's fixed, and must say it looks mighty grand! But I can't see the trash can even though it opens if I click the right end of the dock, hehe. (And yes, tried deactivating it, the activating it again, still the same).

Hope this morsel of info helps others. Cheers

PS: **Spoke too soon**... while looking in AWN Manager, I realised it was set to **3D look**, and when I pulled the menu down, just that and **Flat bar** are in the list! Dunno what that means, but I'm not gonna touch it!

---

### Post by OzzyFrank on 2008-03-15
> **muximus said:**
> i think u can get the same curved look if u go to gconf editor>apps>avant...>bar>bar angle 
and change the value to -1, no need to install nething new

Hmmm... I notice that... um, does that mean we went through all this to change a single setting in gconf-editor?

But it's not April 1st yet!!!

---

### Post by WFGeppetto on 2008-03-15
Ok, I've looked through several pages, and I don't see anyone else with this problem.  I have some weird ones with AWN.

I had the 64bit Ubuntu installed, and I used AWN the first time around without problems, but I couldn't get the curves to work.  After backing my system up, and freshly installing, I tried again.  Curves worked this time, but the applets did not (ie: white lines).

I had numerous problems with internet applications, and plugins, so I eventually decided to use the 32bit Ubuntu for the added support.  Now, I have the 32bit running (my pc is AMD64), and everything is going great, except AWN.

I used the same method I did the first time, in hopes of getting the applets working:

I followed the how-to for AWN, before I followed the AWN curves how-to.  I followed the instructions on this page to the T (I believe), including the rm commands. 

This is what happened at the specific code line that created a problem:

> wfgeppetto@GPTO:~/awn-curves$ sudo gdebi *.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
Wrong architecture 'i386'wfgeppetto@GPTO:~/awn-curves$

I'm confused.  Is it an issue with the 32bit version?  I did not encounter this problem before, on the 64bit distro (GG 7.10, then and now).  Any help?

---

### Post by OzzyFrank on 2008-03-15
OK, I'm not having as much luck as I first thought, but have more info to work with. First, the dock would only unhide itself if I moved the cursor to either end of it (not from above as is usual). Now, after a reboot it once again doesn't appear, and again trying from the terminal returns:

**avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_gconf_new**

Now, in the installation instructions, the 2nd last command beforehand went to "download" stuff and didn't complain at all, but did tell me 0 bytes of 0 bytes were downloaded (yes, I had stopped all other web activity in case). This happened 3 times, but when I tried just before it seemed like it got what it was after:

[B]FINISHED --10:55:43--
Downloaded: 3,167,686 bytes in 5 files[/B]

This time when I ran the last command, [COLOR="DarkRed"]**sudo gdebi *.deb**[/COLOR], I got:

ozzman@ubuntu666:~/awn-curves$ sudo gdebi *.deb
[sudo] password for ozzman:
[B]Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
A later version is already installed[/B]

I tried the .deb files in the ~/awn-curves folder, and they also complained that a later version had been installed. Once again, I tried reinstalling avant-window-navigator-bzr via Synaptic, and got this:

**avant-window-navigator-bzr (version 0.3.1.bzr198.1~gutsy) will be re-installed**

... though it doesn't download anything. Or fix anything. Tried with all the related packages selected, and AWN starts... and I can unhide by moving from the top again... and the Manager has "Curves look" back in the dropdown menu... but NOW **no applets show at all, except for a thin black line** (a pixel or so across)** for each going up for about 2 inches**! Before, the trash was invisible but accessible... now the 2 applets (trash and show desktop) can no longer be accessed... just those lines going up (tried disabling and reenabling them of course, to no avail)! And I'll probably lose all this with a reboot, hehehe!!

Anyway, any suggestions would be welcome. Cheers

---

### Post by WFGeppetto on 2008-03-17
Alrighty, I figured it out.  Ubuntu knows I have an AMD64 machine, and it doesn't want to install i386 stuff on it.  

I replaced this command
```
sudo gdebi *.deb
```

with this
```
sudo dpkg -i --force-architecture *.deb
```

It worked like a charm.  I did lose a couple of applets, but I bet I can find them, and copy them into the appropriate folder, or something.

---

### Post by BLTicklemonster on 2008-03-18
Bah, here's what I get, after rm-ing twice and starting over, and sudo aptitude installing the package it says it has a problem with:

bill@bill-laptop:~/awn-curves$ sudo gdebi *.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
Dependency is not satisfiable: libawn-bzr

---

### Post by BLTicklemonster on 2008-03-19
Bah, I installed the awn deb, and turned on curves. I want extra applets, so I installed them, and this is what I see:

[[IMG]http://img246.imageshack.us/img246/5770/awnproblemsxq3.th.jpg[/IMG]](http://img246.imageshack.us/my.php?image=awnproblemsxq3.jpg)

in case you're wondering, those lines on the right are my new applets. Any idea what's wrong?

---

### Post by WFGeppetto on 2008-03-19
I almost want to tell you, but I think I would give you bad advice, or call it the wrong name, or something stupid.  Sorry, I will tell you this, but it probably won't help:

1. Supposedly, there is supposed to be some way to turn the applets off in the system tray, and then they are supposed to be accessable from awn.  I read about it on the awn support page, but I don't remember the link, google will.  This didn't work for me, though.

2.  When you run AWN in the terminal, it will tell you that the applets you are looking for aren't there, but I don't know how to tell you why.  You know some stuff, I've seen you around, maybe what I tell you will tell you where to look.  That problem only occured to me after installing AWNcurves.  In the awn curves folder, there is an applet folder.  Maybe (I don't know) you need to make copies for both folders.

3.  The only time I have had a successful installation of AWNcurves, with functional applets was the last time.  I did the following:  removed all traces of all awn anything (the tutorials tell you how), then install awn, first, and make sure it functions, then follow AWN curves, including the remove commands.  I also know that some people have actually had success in copying broken applets into the right folder, but again, I am not competent enough to guide you with code.

I hope that stuff helps.  You may not remember, but you helped me once, I think it was with wireless.  At the time, I didn't know how to thank, so, here is your belated thanks!  +1.

The usual guy that watches this thread will come along eventually.  He'll be able to help for sure, but I hope I gave you something to work with.

---

### Post by BLTicklemonster on 2008-03-19
Thanks Geppetto, it was late, and I was tired, and that would never have dawned on me.

---

### Post by WFGeppetto on 2008-03-19
Yay! I helped!  That feels good.  

You know, I think I'm starting to understand a lot more about what Open Source is about.  I hope I can be a useful resource soon.

---

### Post by BLTicklemonster on 2008-03-19
Well, you gave me something to go on, and I found the applets in /usr/lib/awn or something, copied them to the /bill/awn or something folder, but now when I try to use applets, the whole awn thing crimps up into a small little half moon with no icons at all!

But it's a start. If I can at least effect it, I know I'm doing something.

---

### Post by WFGeppetto on 2008-03-19
Aww, well, I've got two that aren't wanting to work.  Everything, but my squiggly wobbly orange thing, and my trash applet work.  I'll work on figuring it out as well, and post my results.

Sorry I couldn't help more, maybe I will yet.  Unfortunately, people in the know haven't visited this thread much recently.

You may get a better response in the Avant-Window-Navigator (Functional Eye Candy) thread.  Reocard (I think is his name) maintains that thread rather well, and I think he is actually one of the developers for AWN.  Either way, he knows some stuff.

Something else, maybe bar heighth, can affect it?  Oh, you mean horizontally squishes, like you turned everything but the launcher off, huh?  Yeah, I don't know, but I have found more results searching google with this input:

> site://http:ubuntuforums.org awn applet white line

---

### Post by reacocard on 2008-03-19
> **WFGeppetto said:**
> Aww, well, I've got two that aren't wanting to work.  Everything, but my squiggly wobbly orange thing, and my trash applet work.  I'll work on figuring it out as well, and post my results.

Sorry I couldn't help more, maybe I will yet.  Unfortunately, people in the know haven't visited this thread much recently.

You may get a better response in the Avant-Window-Navigator (Functional Eye Candy) thread.  Reocard (I think is his name) maintains that thread rather well, and I think he is actually one of the developers for AWN.  Either way, he knows some stuff.

Something else, maybe bar heighth, can affect it?  Oh, you mean horizontally squishes, like you turned everything but the launcher off, huh?  Yeah, I don't know, but I have found more results searching google with this input:

it's reacocard, and here's the thread: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

also, I'm not an AWN developer, but I have been packaging it practically since its first release so I know an awful lot about the project.

---

### Post by BLTicklemonster on 2008-03-19
A. how can I rid any instance of avant-window-navigator and/or awn curves (two different things?) from my system to get a clean start? Just rm them as is mentioned?

B. Gee, isn't there like a .deb file for this that has the applets and everything already in it? I downloaded one that should have had the applets, but didn't. What's up with that?

---

### Post by Yes on 2008-03-20
I'm trying to do this on a Gusty machine, but I keep getting the error "dependencies not met: libawn-bzr" when I try installing the .deb.  I have libawn-bzr and libawn-bzr-dev installed, does anyone know what the problem might be?

---

### Post by WFGeppetto on 2008-03-20
Yes, I am almost positive I can help you.

From what I understand (ie: disclaimer, I don't know alot, but I have this working)  You missed a line in the AWN repository list, and/or a line installing that file.  Go to System-Administration-Synaptics Packages Manager.  Search for libawn-bzr.  If it is not there, then you did not enable one of the repositories, if it is, then install it.

Most importantly, you definitely missed a code, or line from the original instructions.  I don't know a whole lot about this, but I have installed it about 8 times, because I'm bad about messing with my stuff.  I have gotten it to work almost perfectly the last 3 times.  If the instructions are followed to a T, seriously, then it works for me.

What works more often, although I don't know why:

If you installed AWNcurves, then (for me, maybe I goofed) the rm commands leave the /awn-curves folder behind.  I delete it, just in case, and follow all the -rm commands given in the instructions (**IMP** Do not trust all -rm commands, they remove, and are dangerous, but I know that these are fine).  Then, I installed Avant-window-navigator, as listed by Reacocard above, and checked to see if it worked well.  Then I came to this thread, and followed the instructions line by line, with -rm commands, and all.  This doesn't actually make sense, but it worked more consistantly for me, when it comes to applets working.

I can't tell you how to fix applets properly, as I have two I haven't tried to fix yet.  Tomorrow I wil.

Only reference my post, do not depend on it over, or above someone with more beans, or especially Reacocard.

---

### Post by RebelwithoutaClue on 2008-03-20
I followed all of the above but when it came to the last I get...

avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_gconf_new

What did I do wrong?:confused:

---

### Post by BLTicklemonster on 2008-03-20
I'm very interested in getting this to work so that when I boot, my computer looks noticeably different from others. I want people to go "wtf, eh?", and ask questions. But I'm afraid that I'll have to resort back to gdesklets, because awn is still not quite there yet. When it is, it's going to kick some butt! Though it's dependence on compiz/etc, in my opinion, is a serious dead weight anchor sucking it into a vortex ... no wait, I mean it's a drag to have to run something that resource intensive just to have awn looking all cool.

---

### Post by Yes on 2008-03-20
Thanks WFGeppetto, but I definitly have libawn-bzr installed.  And I've had AWN installed before and AWN-curves comnpiled fine so I don't think it's a problem with any dependencies.

I'll try redoing the whole guide now, I guess.

e:  Nope, didn't work :(

---

### Post by moonbeam on 2008-03-21
> **BLTicklemonster said:**
> I'm very interested in getting this to work so that when I boot, my computer looks noticeably different from others. I want people to go "wtf, eh?", and ask questions. But I'm afraid that I'll have to resort back to gdesklets, because awn is still not quite there yet. When it is, it's going to kick some butt! Though it's dependence on compiz/etc, in my opinion, is a serious dead weight anchor sucking it into a vortex ... no wait, I mean it's a drag to have to run something that resource intensive just to have awn looking all cool.

No need for compiz (you just need a compositor):  [http://wiki.awn-project.org/Installation](http://wiki.awn-project.org/Installation)

Though the composite requirement is slated to change:  [https://launchpad.net/awn/+milestone/0.4](https://launchpad.net/awn/+milestone/0.4)

There are many lightweight compositors that work very well with awn. Including xfwm4 and the most recent metacity release.  At the moment I'm using xfwm4 due to some compiz borkage and it, as always, works flawlessly.

---

### Post by BLTicklemonster on 2008-03-21
So can it be made to work in IceWM or Fluxbox?

---

### Post by moonbeam on 2008-03-21
> **BLTicklemonster said:**
> So can it be made to work in IceWM or Fluxbox?

Probably.  You need need to use either xcompmgr or cairo-compmgr ( [http://cairo-compmgr.tuxfamily.org/](http://cairo-compmgr.tuxfamily.org/) )  

xcompmgr seems to be more or less unmaintained but it will work fairly well though there may be a few applets that show regressions (3 or 4 I think).

cairo-compmgr has been very unstable for me when I have tested it.... YMMV.

Beyond that you might want to check out:  [http://wiki.awn-project.org/FAQ#AWN_grabs_the_focus_on_a_large_piece_of_the_screen_in_Openbox._How_do_I_fix_this.3F](http://wiki.awn-project.org/FAQ#AWN_grabs_the_focus_on_a_large_piece_of_the_screen_in_Openbox._How_do_I_fix_this.3F)

---

### Post by reacocard on 2008-03-21
> **BLTicklemonster said:**
> So can it be made to work in IceWM or Fluxbox?

yes, with a separate composite manager like xcompmgr. However, AWN 0.4 is slated to remove the need for a compositor so you may simply want to wait for that.

---

### Post by jw5801 on 2008-03-21
> **moonbeam said:**
> No need for compiz (you just need a compositor):  [http://wiki.awn-project.org/Installation](http://wiki.awn-project.org/Installation)

Though the composite requirement is slated to change:  [https://launchpad.net/awn/+milestone/0.4](https://launchpad.net/awn/+milestone/0.4)

There are many lightweight compositors that work very well with awn. Including xfwm4 and the most recent metacity release.  At the moment I'm using xfwm4 due to some compiz borkage and it, as always, works flawlessly.

How did you get it to work properly with the native xfwm4 compositor? There's a bug which I've spent a bunch of time trying to get around that causes AWM to continually steal focus from all other windows because xfwm4 doesn't recognise a flag that AWN tries to set. There's a patch for xfwm4, and it's fixed in the more recent releases of xfce4, but my attempt to install a newer xfwm4 from source wasn't particularly successful.

---

### Post by moonbeam on 2008-03-21
> **jw5801 said:**
> How did you get it to work properly with the native xfwm4 compositor? There's a bug which I've spent a bunch of time trying to get around that causes AWM to continually steal focus from all other windows because xfwm4 doesn't recognise a flag that AWN tries to set. There's a patch for xfwm4, and it's fixed in the more recent releases of xfce4, but my attempt to install a newer xfwm4 from source wasn't particularly successful.

I use Gentoo so my solution probably wouldn't be relevant :-)

For Ubuntu I believe your best bet is:  [https://launchpad.net/~xubuntu-team/+archive](https://launchpad.net/~xubuntu-team/+archive)

---

### Post by BLTicklemonster on 2008-03-22
You know, for now, I'd be happy if I could get it to show the apps applet (you know, all the stuff like internet, games, etc) instead of white lines.

---

### Post by jw5801 on 2008-03-22
> **moonbeam said:**
> I use Gentoo so my solution probably wouldn't be relevant :-)

For Ubuntu I believe your best bet is:  [https://launchpad.net/~xubuntu-team/+archive](https://launchpad.net/~xubuntu-team/+archive)

Excellent! Thanks a bunch. I tried using the Hardy repos to update xfwm4 but they had the same version as Gutsy.

Cheers!

---

### Post by moonbeam on 2008-03-22
> **BLTicklemonster said:**
> You know, for now, I'd be happy if I could get it to show the apps applet (you know, all the stuff like internet, games, etc) instead of white lines.

How are you installing awn?  I'm guessing you've been following the curves installation guide?


I'd suggest looking the following over:

[http://wiki.awn-project.org/FAQ#Why_does_my_bar_have_one_or_more_thin.2C_vertical.2C_white_lines_that_extend_beyond_the_dock.3F](http://wiki.awn-project.org/FAQ#Why_does_my_bar_have_one_or_more_thin.2C_vertical.2C_white_lines_that_extend_beyond_the_dock.3F)

If all applets are showing issues my guess would be that you have a situation where more than one version of awn is installed.  

If it's only the python applets that are acting up then it's probably an issue with PYTHONPATH.

If it is just some of the python applets acting up then it's a random selection of missing dependencies.

The last two really shouldn't be happening if you're installing from a repo (I think, I'm really not a Ubuntu expert).  So my guess is it's the first one (more than one version of awn installed).

Try following the wiki link to diagnose what the problem is from the terminal output.  It'll just be easier to look at that then guessing :-)

---

### Post by billybag on 2008-03-22
How can i create an executable updater script so i dont have to keep opening up terminal and putting in ```
cd ~/awn-curves
bzr update
./autogen.sh && make && sudo make install
``` when i want to update AWN curves?

---

### Post by billybag on 2008-03-27
how do i set awn to use my theme's icons instead of constantly having to right click and select change icon every time i start an app?

---

### Post by kamla_desi on 2008-03-28
home:~/awn-curves$sudo gdebi *.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
Dependency is not satisfiable: libawn-bzr
home:~/awn-curves$avant-window-navigator
avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory
home:~/awn-curves$

hi i tried to follow ur instructions, (preety throught i might say :) )
But i got stuck here

home:~/awn-curves$sudo gdebi *.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
Dependency is not satisfiable: libawn-bzr
home:~/awn-curves$avant-window-navigator
avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory
home:~/awn-curves$

Please help

---

### Post by billybag on 2008-03-29
looks like you are having some dependency issues. 
try ```
wget http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb
``` to download the deb
i am actually fairly certain i have ran into this problem before in the past and i think this is how i fixed it but i am not sure. but i am sure you are missing 'libawn.so.0'

also, did you have AWN installed previously? you may want to remove it if you did. also try this link   [http://ubuntuforums.org/showthread.php?t=385981&highlight=kiba](http://ubuntuforums.org/showthread.php?t=385981&highlight=kiba)

---

### Post by TheMemphisExperience on 2008-03-30
Mine will not start up. It has it's own launcher, though. 

This is what happens when I put avant-window-navigator and awn-manager in the terminal.



> katsu@OmegaPieSysUbuntu:~/awn-curves$ avant-window-manager
bash: avant-window-manager: command not found
katsu@OmegaPieSysUbuntu:~/awn-curves$ avant-window-navigator
avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory
katsu@OmegaPieSysUbuntu:~/awn-curves$ awn-manager
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:188: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 168, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 188, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue



I restarted the whole computer to attempt to satisfy hat it asked. Then I removed it and reinstalled. It still will not open.

---

### Post by HotCocoa on 2008-04-07
Nice guide!  I'm featuring it on my Linux blog at [http://susebuntu.wordpress.com](http://susebuntu.wordpress.com)!

---

### Post by OzzyFrank on 2008-04-07
> **HotCocoa said:**
> Nice guide!  I'm featuring it on my Linux blog at [http://susebuntu.wordpress.com](http://susebuntu.wordpress.com)!

um... I perhaps wouldn't rush into that one! As you may notice if you read through some of the comments, it is far from perfect. Many have all sorts of problems installing it, and those that do get it happening can suffer loss of features and/or stability. For example, many of us lose the applets, or rather they appear as very thin vertical lines, which cannot be clicked (so they need to be removed). In addition, on my system the whole dock just disappears every hour or so... and that can be while I'm not even using the PC, ie opening new things... it just vanishes.

And I can tell you the general advice given to uninstall it all, then reinstall it... then uninstall and reinstall it... and uninstall and reinstall it... doesn't seem to do much but waste time. Unfortunately.

---

### Post by billybag on 2008-04-08
curves has been combined into trunk... all you need to do now is download the trunk version of awn and then change some settings in gconf... like the curvyness and such. the settings to edit can be found on the official awn curves forum [http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=853&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=853&page=1&isLive=true)

so in short, these directions are no longer neccessary as you can get curves already and dont really need to download it seperately

---

### Post by Locutus_of_Borg on 2008-04-08
I'm trying to get this working in Gentoo but am hung up on the dependencies

```
sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev 
```

are not available in Portage, is there some reasonable way I can download these either from Gentoo, or while in ubuntu but only save the source codes in separate files within a folder?

nevermind, solved it

```
emerge avant-window-navigator
bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
cd awn-curves
./autogen.sh && make
make install
```

---

### Post by ride1226 on 2008-04-21
this is what i get...

```
milby@milby-desktop:~$ avant-window-navigator
avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory
milby@milby-desktop:~$ awn-manager
/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py:188: DeprecationWarning: raising a string exception is deprecated
  raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"
\Traceback (most recent call last):
  File "/usr/local/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/local/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 168, in __init__
    self.setup_color(TITLE_TEXT_COLOR, self.wTree.get_widget("textcolor"))
  File "/usr/local/share/avant-window-navigator/awn-manager/awnPreferences.py", line 188, in setup_color
    raise "\nKey: "+key+" isn't set.\nRestarting AWN usually solves this issue\n"

Key: /apps/avant-window-navigator/title/text_color isn't set.
Restarting AWN usually solves this issue


```

not sure where i screwed up at. works great on my laptop been using it for months...got a new pc and now messed somethin up on this install.

---

### Post by rundee_f on 2008-04-21
hi niko wuzzup!? :)

being a long time...

ummm... i recommend this thread as a sticky... :D

---

### Post by ColdFusionEESG on 2008-04-22
Hey All,

First thing....Hey Niko...I see yer from Victoria, BC....small world...me too.  That said I swear I met a Niko on the local Cybersuds list.....you the same Niko? ;-)

....and on to my question....

It appears that AWN curves is a different beast than AWN.  I can get my regular AWN to look like the screenshots in the first post in this thread by opening gconf-editor and altering the bar angle to -1.

So how is what I'm doing different from AWN curves?

BTW...my approach has a slight issue with the Cairo Menu and Show Desktop applets don't follow the curve...they just stay where they were on the 3D bar.

Anyways...TIA for any info

Cheers

---

### Post by reacocard on 2008-04-22
> **ColdFusionEESG said:**
> Hey All,

First thing....Hey Niko...I see yer from Victoria, BC....small world...me too.  That said I swear I met a Niko on the local Cybersuds list.....you the same Niko? ;-)

....and on to my question....

It appears that AWN curves is a different beast than AWN.  I can get my regular AWN to look like the screenshots in the first post in this thread by opening gconf-editor and altering the bar angle to -1.

So how is what I'm doing different from AWN curves?

BTW...my approach has a slight issue with the Cairo Menu and Show Desktop applets don't follow the curve...they just stay where they were on the 3D bar.

Anyways...TIA for any info

Cheers

curves was merged into main AWN recently, your trick is now the 'official' method of getting curves. Because of this merge, the -curves branch mentioned in this thread's guide is no longer updated, and should not be used.

---

### Post by ColdFusionEESG on 2008-04-22
> **reacocard said:**
> curves was merged into main AWN recently, your trick is now the 'official' method of getting curves. Because of this merge, the -curves branch mentioned in this thread's guide is no longer updated, and should not be used.

Ahhh...thanks reacocard....saved me a heck of a thread read ;-)

Cheers

---

### Post by SoulSmasher on 2008-04-25
> **reacocard said:**
> curves was merged into main AWN recently, your trick is now the 'official' method of getting curves. Because of this merge, the -curves branch mentioned in this thread's guide is no longer updated, and should not be used.

so if this guide won't work on, how can we install on hardy as clean install ?
thanks :)

guide does not work on hardy

it says 
```
E: Couldn't find package libgnome-vfs-dev
```
if i install libgnomevfs2-dev from synaptic and keep on going it cannot make the configuration to be rady for install..

here's my full terminal

```
soul@soul:~$ sudo rm -f /usr/local/bin/awn*
[sudo] password for soul: 
soul@soul:~$ sudo rm -f /usr/local/bin/awn*
soul@soul:~$ sudo rm -f /usr/local/bin/avant*
soul@soul:~$ sudo rm -rf /usr/local/lib/awn
soul@soul:~$ sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
soul@soul:~$ sudo rm -f /usr/local/share/applications/avant*
soul@soul:~$ sudo rm -f /usr/local/share/applications/awn*
soul@soul:~$ sudo rm -rf /usr/local/share/avant-window-navigator
soul@soul:~$ sudo rm -f /usr/local/lib/libawn*
soul@soul:~$ sudo rm -rf /usr/local/include/libawn
soul@soul:~$ sudo rm -f /usr/local/lib/libawn*
soul@soul:~$ sudo rm -f /usr/local/lib/pkgconfig/awn.pc
soul@soul:~$ sudo rm -rf /usr/local/share/awn-core-applets
soul@soul:~$ sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
soul@soul:~$ sudo apt-get install bzr m4 gnome-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  autoconf automake1.9 autotools-dev intltool libc6-dev libtool linux-libc-dev
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc
  automake1.9-doc bzr-gtk bzr-svn python-pycurl glibc-doc manpages-dev gcj
  gfortran fortran95-compiler libtool-doc
Recommended packages:
  automaken bzrtools python-paramiko libltdl3-dev
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev bzr gnome-common intltool libc6-dev
  libtool linux-libc-dev m4
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB of archives.
After this operation, 37.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ftp-stud.fht-esslingen.de hardy/main m4 1.4.10-1 [207kB]
Get:2 http://ftp-stud.fht-esslingen.de hardy/main autoconf 2.61-4 [448kB]
Get:3 http://ftp-stud.fht-esslingen.de hardy/main autotools-dev 20070725.1 [61.9kB]
Get:4 http://ftp-stud.fht-esslingen.de hardy/main automake1.9 1.9.6+nogfdl-3ubuntu1 [388kB]
Get:5 http://ftp-stud.fht-esslingen.de hardy/main bzr 1.3.1-1 [4478kB]         
Get:6 http://ftp-stud.fht-esslingen.de hardy/main linux-libc-dev 2.6.24-16.30 [694kB]
Get:7 http://ftp-stud.fht-esslingen.de hardy/main libc6-dev 2.7-10ubuntu3 [3344kB]
Get:8 http://ftp-stud.fht-esslingen.de hardy/main libtool 1.5.26-1ubuntu1 [340kB]
Get:9 http://ftp-stud.fht-esslingen.de hardy/main intltool 0.37.1-1ubuntu1 [85.8kB]
Get:10 http://ftp-stud.fht-esslingen.de hardy/main gnome-common 2.20.0-1 [15.4kB]
Fetched 10.1MB in 2min0s (83.6kB/s)                                            
Selecting previously deselected package m4.
(Reading database ... 133047 files and directories currently installed.)
Unpacking m4 (from .../archives/m4_1.4.10-1_i386.deb) ...
Selecting previously deselected package autoconf.
Unpacking autoconf (from .../autoconf_2.61-4_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20070725.1_all.deb) ...
Selecting previously deselected package automake1.9.
Unpacking automake1.9 (from .../automake1.9_1.9.6+nogfdl-3ubuntu1_all.deb) ...
Selecting previously deselected package bzr.
Unpacking bzr (from .../archives/bzr_1.3.1-1_i386.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-16.30_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_i386.deb) ...
Selecting previously deselected package libtool.
Unpacking libtool (from .../libtool_1.5.26-1ubuntu1_i386.deb) ...
Selecting previously deselected package intltool.
Unpacking intltool (from .../intltool_0.37.1-1ubuntu1_all.deb) ...
Selecting previously deselected package gnome-common.
Unpacking gnome-common (from .../gnome-common_2.20.0-1_all.deb) ...
Setting up m4 (1.4.10-1) ...

Setting up autoconf (2.61-4) ...

Setting up autotools-dev (20070725.1) ...
Setting up automake1.9 (1.9.6+nogfdl-3ubuntu1) ...

Setting up bzr (1.3.1-1) ...

Setting up linux-libc-dev (2.6.24-16.30) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtool (1.5.26-1ubuntu1) ...
Setting up intltool (0.37.1-1ubuntu1) ...
Setting up gnome-common (2.20.0-1) ...
soul@soul:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autotools-dev is already the newest version.
autotools-dev set to manually installed.
libgnome2-common is already the newest version.
E: Couldn't find package libgnome-vfs-dev
soul@soul:~$ bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
soul@soul:~$ bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
bzr: ERROR: File exists: u'/home/soul/awn-curves/.bzr': [Errno 17] File exists: '/home/soul/awn-curves/.bzr'
soul@soul:~$ cd awn-curves
soul@soul:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.26
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.16.3
checking for intltool >= 0.30...
  testing intltoolize... found 0.37.1
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
Running autoconf...
Running autoheader...
Running automake-1.9...
configure.in: installing `./install-sh'
configure.in: installing `./missing'
awn-applet-activation/Makefile.am: installing `./depcomp'
pyawn/Makefile.am: installing `./compile'
pyawn/Makefile.am:10: installing `./py-compile'
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for a Python interpreter with version >= 2.3.5... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers
soul@soul:~/awn-curves$ sudo make install
make: *** No rule to make target `install'.  Stop.

```

---

### Post by reacocard on 2008-04-25
> **SoulSmasher said:**
> so if this guide won't work on, how can we install on hardy as clean install ?
thanks :)

guide does not work on hardy

it says 
```
E: Couldn't find package libgnome-vfs-dev
```
if i install libgnomevfs2-dev from synaptic and keep on going it cannot make the configuration to be rady for install..

here's my full terminal

```
soul@soul:~$ sudo rm -f /usr/local/bin/awn*
[sudo] password for soul: 
soul@soul:~$ sudo rm -f /usr/local/bin/awn*
soul@soul:~$ sudo rm -f /usr/local/bin/avant*
soul@soul:~$ sudo rm -rf /usr/local/lib/awn
soul@soul:~$ sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
soul@soul:~$ sudo rm -f /usr/local/share/applications/avant*
soul@soul:~$ sudo rm -f /usr/local/share/applications/awn*
soul@soul:~$ sudo rm -rf /usr/local/share/avant-window-navigator
soul@soul:~$ sudo rm -f /usr/local/lib/libawn*
soul@soul:~$ sudo rm -rf /usr/local/include/libawn
soul@soul:~$ sudo rm -f /usr/local/lib/libawn*
soul@soul:~$ sudo rm -f /usr/local/lib/pkgconfig/awn.pc
soul@soul:~$ sudo rm -rf /usr/local/share/awn-core-applets
soul@soul:~$ sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
soul@soul:~$ sudo apt-get install bzr m4 gnome-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  autoconf automake1.9 autotools-dev intltool libc6-dev libtool linux-libc-dev
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc
  automake1.9-doc bzr-gtk bzr-svn python-pycurl glibc-doc manpages-dev gcj
  gfortran fortran95-compiler libtool-doc
Recommended packages:
  automaken bzrtools python-paramiko libltdl3-dev
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev bzr gnome-common intltool libc6-dev
  libtool linux-libc-dev m4
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.1MB of archives.
After this operation, 37.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ftp-stud.fht-esslingen.de hardy/main m4 1.4.10-1 [207kB]
Get:2 http://ftp-stud.fht-esslingen.de hardy/main autoconf 2.61-4 [448kB]
Get:3 http://ftp-stud.fht-esslingen.de hardy/main autotools-dev 20070725.1 [61.9kB]
Get:4 http://ftp-stud.fht-esslingen.de hardy/main automake1.9 1.9.6+nogfdl-3ubuntu1 [388kB]
Get:5 http://ftp-stud.fht-esslingen.de hardy/main bzr 1.3.1-1 [4478kB]         
Get:6 http://ftp-stud.fht-esslingen.de hardy/main linux-libc-dev 2.6.24-16.30 [694kB]
Get:7 http://ftp-stud.fht-esslingen.de hardy/main libc6-dev 2.7-10ubuntu3 [3344kB]
Get:8 http://ftp-stud.fht-esslingen.de hardy/main libtool 1.5.26-1ubuntu1 [340kB]
Get:9 http://ftp-stud.fht-esslingen.de hardy/main intltool 0.37.1-1ubuntu1 [85.8kB]
Get:10 http://ftp-stud.fht-esslingen.de hardy/main gnome-common 2.20.0-1 [15.4kB]
Fetched 10.1MB in 2min0s (83.6kB/s)                                            
Selecting previously deselected package m4.
(Reading database ... 133047 files and directories currently installed.)
Unpacking m4 (from .../archives/m4_1.4.10-1_i386.deb) ...
Selecting previously deselected package autoconf.
Unpacking autoconf (from .../autoconf_2.61-4_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20070725.1_all.deb) ...
Selecting previously deselected package automake1.9.
Unpacking automake1.9 (from .../automake1.9_1.9.6+nogfdl-3ubuntu1_all.deb) ...
Selecting previously deselected package bzr.
Unpacking bzr (from .../archives/bzr_1.3.1-1_i386.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-16.30_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_i386.deb) ...
Selecting previously deselected package libtool.
Unpacking libtool (from .../libtool_1.5.26-1ubuntu1_i386.deb) ...
Selecting previously deselected package intltool.
Unpacking intltool (from .../intltool_0.37.1-1ubuntu1_all.deb) ...
Selecting previously deselected package gnome-common.
Unpacking gnome-common (from .../gnome-common_2.20.0-1_all.deb) ...
Setting up m4 (1.4.10-1) ...

Setting up autoconf (2.61-4) ...

Setting up autotools-dev (20070725.1) ...
Setting up automake1.9 (1.9.6+nogfdl-3ubuntu1) ...

Setting up bzr (1.3.1-1) ...

Setting up linux-libc-dev (2.6.24-16.30) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtool (1.5.26-1ubuntu1) ...
Setting up intltool (0.37.1-1ubuntu1) ...
Setting up gnome-common (2.20.0-1) ...
soul@soul:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autotools-dev is already the newest version.
autotools-dev set to manually installed.
libgnome2-common is already the newest version.
E: Couldn't find package libgnome-vfs-dev
soul@soul:~$ bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
soul@soul:~$ bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
bzr: ERROR: File exists: u'/home/soul/awn-curves/.bzr': [Errno 17] File exists: '/home/soul/awn-curves/.bzr'
soul@soul:~$ cd awn-curves
soul@soul:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.26
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.16.3
checking for intltool >= 0.30...
  testing intltoolize... found 0.37.1
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
Running autoconf...
Running autoheader...
Running automake-1.9...
configure.in: installing `./install-sh'
configure.in: installing `./missing'
awn-applet-activation/Makefile.am: installing `./depcomp'
pyawn/Makefile.am: installing `./compile'
pyawn/Makefile.am:10: installing `./py-compile'
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for a Python interpreter with version >= 2.3.5... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers
soul@soul:~/awn-curves$ sudo make install
make: *** No rule to make target `install'.  Stop.

```

use this guide instead, with the bar_angle trick: [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

### Post by Grifter81 on 2008-04-29
I've done everything so far but I have this problem when I try to run awn.

avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory

It appears that when I try to install the package libawn-bzr it can't be found. Does anyone know a work around for this?

---

### Post by VizioNy on 2008-04-30
Hi, I am very new to ubuntu. I thought I would make it regular o/s for my girlfriend. And wanted to add some eye candy throughout the process.

I used the instructions listed on the first page, I got all the way to the last step but this is what I get when I tried the last cmd.


xxxx&xxx:~/awn-curves$ sudo gdebi *.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
Dependency is not satisfiable: libawn-bzr

Any suggestions? I cannot get AWN to launch either.

---

### Post by OzzyFrank on 2008-04-30
Try installing **libawn-bzr** first and see if that fixes it. Wouldn't be surprised if it doesn't... I have to say this is one BIG mess, and I'm one of the ones who got it to run (though it crashes randomly and frequently). Can't wait till this is something you can install easily through Synaptic!

---

### Post by Exsecrabilus on 2008-05-23
I would be happy if this was updated for Ubuntu 8.04 LTS "Hardy Heron."

---

### Post by reacocard on 2008-05-23
> **Exsecrabilus said:**
> I would be happy if this was updated for Ubuntu 8.04 LTS "Hardy Heron."

this is no longer the official way of installing curves. for the most current method, see the FAQ question about curves in this guide: [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

### Post by Exsecrabilus on 2008-05-23
> **reacocard said:**
> this is no longer the official way of installing curves. for the most current method, see the FAQ question about curves in this guide: [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)
Win.

---

### Post by melenor on 2008-05-27
Is there a repository for AWN-Curves also what is the most current, correct way to install curves?

---

### Post by jw5801 on 2008-05-27
> **melenor said:**
> Is there a repository for AWN-Curves also what is the most current, correct way to install curves?

It's now part of the awm trunk, so it should be included in a generic awm install, which you can get from the hardy repositories.

---

### Post by reacocard on 2008-05-27
> **melenor said:**
> Is there a repository for AWN-Curves also what is the most current, correct way to install curves?

see this post: [http://ubuntuforums.org/showpost.php?p=5028899&postcount=930](http://ubuntuforums.org/showpost.php?p=5028899&postcount=930)

---

### Post by war59312 on 2008-06-05
Indeed the updates show up but makes the user feel you cant trust them?

---

### Post by Exsecrabilus on 2008-06-05
> **war59312 said:**
> Indeed the updates show up but makes the user feel you cant trust them?
We got no choice, this isn't in the official repos, and since it's not stable enough, it won't be.
And since it isn't, the system detects it as "insecure." We'll just have to assume the newbies get it.

---

### Post by war59312 on 2008-06-08
Yeah, so there is no way 3rd parties could at least sign their own releases?

---

### Post by Frak on 2008-06-08
> **Exsecrabilus said:**
> We got no choice, this isn't in the official repos, and since it's not stable enough, it won't be.
And since it isn't, the system detects it as "insecure." We'll just have to assume the newbies get it.
If it has the right gpg signature, and the user says its ok, its auto-trusted.

---

### Post by reacocard on 2008-06-08
> **war59312 said:**
> Yeah, so there is no way 3rd parties could at least sign their own releases?

Only if we were to host the repo ourselves, which means we miss out on the wonderful build farm the PPA system has.

---

### Post by AlexBellisBrown on 2008-06-27
Following the instructions EXACTLY as were posted in the first post, i got this baby working first time!!! WOOOOOO! Thank you so much! :D

---

