---
title: "Separate desktop backrounds?"
date: 2004-12-03
forum: Desktop Environments
---

### Post by Loonux on 2004-12-03
Im sure when I installed a previous version of mandrake a long long time ago i could set different backgrounds for each of the four desktops. I know that uses KDE whereas Ubuntu uses GNome, but is there any way to change the background for each desktop? that was a nice feature that i haven't worked out how to do yet.

Many thanks in advance

---

### Post by p!=f on 2004-12-03
I'm afraid there's no such a feature in Gnome (correct me if wrong) by default but you can use [http://wallpapoz.sourceforge.net/](http://wallpapoz.sourceforge.net/) to have different wallpapers on each desktop.
I created the package just in case you don't want to compile it. Compiled for **Hoary** but may work on **Warty**. You have to
```

gzip -d wallpapoz_0.1-1_i386.deb.gz

```
it first. Hope it helps.

---

### Post by Tomy on 2005-01-19
[QUOTE=p!=f]...I created the package just in case you don't want to compile it....
  [/QUOTE]
  
  :D Thank you! Thank you!:D
  
 I compiled this last summer when I was testing UserLinux. In fact, it was the first (and almost only) program I have ever compiled. I was kinda proud of myself that I got it to work.
  
  But the truth is, **I am a user, **and forever indebted to those of you who create this wonderful software.
  
  I do know how to **apt-get **and **dpkg** and I appreciate you making it easy for me.
  
  Tomy
  
  ps Is gnome going to add this feature? Lots of people who have tried KDE really like different backgrounds on each workspace.

---

### Post by merinda on 2005-01-20
Hi,

I am Akbar, the developer of wallpapoz program. Nice to know that somebody use this program....

I will improve this program by starting developing it in this March. Right now, I am too busy with my commercial works.

In the next version of wallpapoz, it will support wallpapers slide show on each workspace...... 

Just post problem installing this program. I'll try to help you.

Just wait it!!!!

---

### Post by lizardking on 2005-01-20
[QUOTE=p!=f]I'm afraid there's no such a feature in Gnome (correct me if wrong) by default but you can use [http://wallpapoz.sourceforge.net/](http://wallpapoz.sourceforge.net/) to have different wallpapers on each desktop.
I created the package just in case you don't want to compile it. Compiled for **Hoary** but may work on **Warty**. You have to
```

gzip -d wallpapoz_0.1-1_i386.deb.gz

```
it first. Hope it helps.[/QUOTE]
how can install it with **apt**?
if i install it with **dpkg -i** it reports this:
```
lizardking@iac:~ $ sudo dpkg -i Desktop/wallpapoz_0.1-1_i386.deb
Password:
(Lettura del database ... 78186 file e directory attualmente installati.)
Preparativi per il rimpiazzo di wallpapoz 0.1-1 (usando .../wallpapoz_0.1-1_i386.deb) ...
Spacchetto il rimpiazzo di wallpapoz ...
dpkg: problemi con le dipendenze impediscono la configurazione di wallpapoz:
 wallpapoz dipende da libglib2.0-0 (>= 2.5.5); comunque:
  La versione di libglib2.0-0 nel sistema è 2.4.7-0ubuntu2.
 wallpapoz dipende da libgtk2.0-0 (>= 2.5.5); comunque:
  La versione di libgtk2.0-0 nel sistema è 2.4.10-1ubuntu1.
 wallpapoz dipende da libxml++2.6; comunque:
  Il pacchetto libxml++2.6 non è installato.
 wallpapoz dipende da libxml2 (>= 2.6.15); comunque:
  La versione di libxml2 nel sistema è 2.6.11-3ubuntu1.1.
dpkg: errore processando wallpapoz (--install):
 problemi con le dipendenze - lasciato non configurato
Sono occorsi degli errori processando:
 wallpapoz
lizardking@iac:~ $
```

---

### Post by Tomy on 2005-01-23
Try this:
                          ```
 ~$ sudo apt-get install libglademm-2.4-1
  ~$ sudo apt-get install libglibmm-2.4-1
  ~$ sudo apt-get install libgtkmm-2.4-1
  ~$ sudo apt-get install libsigc++-2.0-0
``` 
 You can put them all on one apt-get line but the line is too long to display cleanly here in the forum. I am sure there is a simpler way to do this, but I'm not a guru.
    
                         and then install the wallpapoz deb 
                          ```
~$  sudo dpkg -i wallpapoz_0.1-1_i386.deb
```
                       To run it from a terminal just type:
                        ```
~$ wallpapoz
``` 
 I got it installed and was able to set different wallpapers but at this point restarting the daemon doesn't work. Worked for me under UserLinux--I'll post back if I figure it out.
                       
                       Good luck
                       Tomy
                     
                     okay, I got it to work. My problem was that I had my desktop background set to **No Wallpaper**. After I set it to a wallpaper everything works fine.

---

### Post by Tomy on 2005-01-23
[QUOTE=merinda]Hi,
  
  I am Akbar, the developer of wallpapoz program. Nice to know that somebody use this program....
  [/QUOTE]
  Hi Akbar,
  
  Thanks for creating wallpapoz :D! 
  
 My first experience with GNU/Linux was with Lindows/Linspire and they use KDE. I really like Ubuntu and I am getting more familiar with Gnome but I missed my KDE desktop wallpapers. Now I have them working with Gnome.
  
  Great little program.
  Tomy

---

### Post by Mgcross on 2005-03-24
[QUOTE=merinda]Hi,

I am Akbar, the developer of wallpapoz program. Nice to know that somebody use this program....

I will improve this program by starting developing it in this March. Right now, I am too busy with my commercial works.

In the next version of wallpapoz, it will support wallpapers slide show on each workspace...... 

Just post problem installing this program. I'll try to help you.

Just wait it!!!![/QUOTE]

Nice to see you in the forum. I am running hoary64, and I downloaded the source you provide...configure make and make install went fine, but when I run "wallpapoz" it segfaults....

Where should I begin looking for solutions? I am just a silly user..... :oops:

---

### Post by lao_V on 2005-03-24
KDE implements this feature quite nicely without having to install additional software along with slide shows for your backgrounds! Its great!

---

### Post by Mgcross on 2005-03-26
Yes, I know...I was a hard-core K fan before ubuntu....as U uses G by default, I decided to give it a try...I can't go back to kde now...love Gnome too much...

---

### Post by helmoltz on 2005-03-26
I installed wallpapoz and all lib necessary files. All ok in the installation phase, but when I launch "wallapoz" by terminal either as normal user, as root I obtain this error message:

[COLOR=Red][B]root@Mitac-6120N:/home/gibbs/Program # wallpapoz
wallpapoz: error while loading shared libraries: libxml++-2.6.so.1: cannot open shared object file: No such file or directory
root@Mitac-6120N:/home/gibbs/Program # wallpapoz
wallpapoz: error while loading shared libraries: libxml++-2.6.so.1: cannot open shared object file: No such file or directory[/B][/COLOR]

 :roll: 
Why? Can you help me?

---

### Post by doclivingston on 2005-03-27
You'll need to install 'libxml++2.6' (i.e. `apt-get install libxml++2.6`).

---

### Post by helmoltz on 2005-03-27
Thanks,
but I have installed llibxml++-2.6 with Synaptic and I obtained that output: wallpapoz didn't work. I think that it can't run because a new version of libxml++-2.6 contain/install libxml++-2.6.so.2, so wallpapoz that needs libxml++-2.6.so.1, obviously can't start.
I hope that my reply is clear, sorry for my English (I'm Italian!)

---

### Post by merinda on 2005-04-08
There is new development version of wallpapoz and installation tips in the official site:
[http://wallpapoz.sf.net](http://wallpapoz.sf.net)

I hope it can help some people to install this software. Well, I still don't have enough time. But I think in May, I can work the new version. The new version will come with more than one wallpaper for one workspace. 

Be patient! I have to study for exam.

---

### Post by merinda on 2005-04-08
[QUOTE=helmoltz]I installed wallpapoz and all lib necessary files. All ok in the installation phase, but when I launch "wallapoz" by terminal either as normal user, as root I obtain this error message:

[COLOR=Red][B]root@Mitac-6120N:/home/gibbs/Program # wallpapoz
wallpapoz: error while loading shared libraries: libxml++-2.6.so.1: cannot open shared object file: No such file or directory
root@Mitac-6120N:/home/gibbs/Program # wallpapoz
wallpapoz: error while loading shared libraries: libxml++-2.6.so.1: cannot open shared object file: No such file or directory[/B][/COLOR]

 :roll: 
Why? Can you help me?[/QUOTE]


Try to compile the development version source....
[http://www.akbarhome.com/download/files/wallpapoz-20050408.tar.bz2](http://www.akbarhome.com/download/files/wallpapoz-20050408.tar.bz2)

Or use the static binary instead:
[http://wallpapoz.sf.net](http://wallpapoz.sf.net)

---

### Post by helmoltz on 2005-04-30
:???: 
Thanks I tried last version of wallpapoz: wallpapoz-static-binary-20050412.tar.bz2.
After decompression and launch of program I obtainde this result in terminal.

> gibbs@Mitac-6120N:~ $ /home/gibbs/Program/WALLPAPOZ/wallpapoz/bin/wallpapoz

(process:9205): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(wallpapoz:9205): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: undefined symbol: g_return_if_fail_warning

(wallpapoz:9205): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: undefined symbol: g_return_if_fail_warning

(wallpapoz:9205): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: undefined symbol: g_return_if_fail_warning

(wallpapoz:9205): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so: undefined symbol: g_return_if_fail_warning
Fontconfig error: "conf.d", line 1: no element found

** (wallpapoz:9205): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: undefined symbol: g_return_if_fail_warning
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (wallpapoz:9205): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: undefined symbol: g_return_if_fail_warning
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (wallpapoz:9205): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: undefined symbol: g_return_if_fail_warning
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (wallpapoz:9205): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: undefined symbol: g_return_if_fail_warning
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (wallpapoz:9205): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: undefined symbol: g_return_if_fail_warning
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (wallpapoz:9205): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: undefined symbol: g_return_if_fail_warning
Failed to load Pango module for id: 'BasicScriptEngineFc'
(wallpapoz:9205): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (wallpapoz:9205): CRITICAL **: file pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
Aborted

I'm using Ubuntu Breezy, can I do something now to correct?

---

### Post by xalen on 2005-05-03
I got a very similar error to the previous message but I'm using Hoary.  First I tried installing from the binary but the make failed.  Then I tried the deb file which seemed to install but got the above error when I ran wallpapoz.  I'm using the 686 kernel, is that a problem or is there something I should clean up from the binary install?

---

### Post by greenwom on 2005-05-13
I've run into the same problem this the so.2 deal......

Hope someone can provide a newbee like me a clue :-)

---

### Post by Rainbow Demon on 2005-05-22
If you have a trouble, first install wallpapoz from .deb-package (can be found on previsous page), then copy libxml++-2.6.so.2 from /usr/lib to libxml++-2.6.so.1 (dirrectory is the same). Now you can run "wallpapoz".
Later you may have a trouble using it.. Try to cange walls using "sudo wallpapoz" and then restart daemon using "wallpapoz" (without sudo) command.
If you want wallpapoz to be loaded on every startup you should add to Computer--Desktop Prefences--Sessions--last tab "daemon_wallpapoz" command.
Sorry for my bad english, i live in Russia

---

### Post by greenwom on 2005-05-22
your english is fine, you probably spell better than I do :)

This is one of those apps that would be really cool if it just worked out of the box.  I 'm not going to mess with this until it's stable and working proprerly.  Messing with the desktop enviornment can be like shooting yourself in the foot (if it's your only working computer.)  

I'll wait on multiple backgounds and transperent windows.  I'd rather not toy with my working ubuntu box.

---

### Post by Rainbow Demon on 2005-05-22
thanks =)

I turned off wallpapoz now, coz i have only 128Mb RAM and PIII 800 Mhz. Speed and productivity is more valuable for me.

---

### Post by Lunde on 2005-07-03
[QUOTE=merinda]Hi,

I am Akbar, the developer of wallpapoz program. Nice to know that somebody use this program....

I will improve this program by starting developing it in this March. Right now, I am too busy with my commercial works.

In the next version of wallpapoz, it will support wallpapers slide show on each workspace...... 

Just post problem installing this program. I'll try to help you.

Just wait it!!!![/QUOTE]
 Thanks Akbar! You did some nice work there

---

### Post by merinda on 2005-07-22
New version of wallpapoz is out. It supports multiple wallpapers per workspace.
[http://wallpapoz.sf.net](http://wallpapoz.sf.net)

Dependencies is rather complex. Install them in order:
libxml++-2.10
libsigc++-2.0
glibmm-2.4
gtkmm-2.4
libglademm-2.4

This is my guess. You can install libsigc++, glibmm, gtkmm, libglademm with your synaptic ( install development files too not just runtime ) but not libxml++ because libxml++ is not common library so I don't think Ubuntu will package for you. Compile it your self. Get it here:
[http://libxmlplusplus.sourceforge.net/](http://libxmlplusplus.sourceforge.net/)

About static file??? I made static file using statifier ( [http://statifier.sf.net](http://statifier.sf.net) ). The author of the statifier promise me the new version will be better. But I haven't try it. I am learning autopackage so it will help some people installing this software.

Tell me if you have problem installing this software. I'll help my best.

Regards,

Akbar

---

### Post by cutOff on 2005-07-22
Does it works on hoary? I'm pretty interested.

---

### Post by manicka on 2005-07-22
[QUOTE=merinda]New version of wallpapoz is out. It supports multiple wallpapers per workspace.
[http://wallpapoz.sf.net](http://wallpapoz.sf.net)

Dependencies is rather complex. Install them in order:
libxml++-2.10
libsigc++-2.0
glibmm-2.4
gtkmm-2.4
libglademm-2.4[/QUOTE]
Nice program :D 
Makes desktop switching a little bit to slow for my liking but works well.

If anyone is interested a copy of the deb file I made for libxml++-2.10 with checkinstall for hoary is available [here](http://members.iinet.net.au/~gracey88/libxml++-2.10.0-1_i386.deb)  
Usual caveats apply

---

### Post by cutOff on 2005-07-23
[QUOTE=cutOff]Does it works on hoary? I'm pretty interested.[/QUOTE]
Still waiting for a reply though.

---

### Post by Lunde on 2005-07-23
[QUOTE=cutOff]Still waiting for a reply though.[/QUOTE]
 It's anwered in the above post
[QUOTE=manicka]
If anyone is interested a copy of the deb file I made for libxml++-2.10 with checkinstall for hoary is available [here](http://members.iinet.net.au/~gracey88/libxml++-2.10.0-1_i386.deb)  
Usual caveats apply[/QUOTE]

---

### Post by cutOff on 2005-07-23
I've already seen but doesn't help me much.

Anyway thanks for reply.

---

### Post by Lunde on 2005-07-23
[QUOTE=cutOff]I've already seen but doesn't help me much.

Anyway thanks for reply.[/QUOTE]
 Then I'm sorry, I did'nt understand your question.
Manicka made a .deb file for installation under Hoary, and I thought you asked if it's possible to run this under Hoary.

---

### Post by manicka on 2005-07-23
Yes, it works under hoary, but as stated above it's a little slow for  my liking.

Follow the instructions to install at the website and make sure all dependencies are installed. libxml++-2.10 isn't available through backports so you have to compile it yourself. A link to the deb I compiled is in the previous post if you find it useful.

---

### Post by cutOff on 2005-07-23
[QUOTE=manicka]Yes, it works under hoary, but as stated above it's a little slow for  my liking.

Follow the instructions to install at the website and make sure all dependencies are installed. libxml++-2.10 isn't available through backports so you have to compile it yourself. A link to the deb I compiled is in the previous post if you find it useful.[/QUOTE]
Thanks manicka, i'll give it a try.

---

### Post by Tomy on 2005-09-22
Edited: September 23,2005
If you can help please respond to this newer thread [wallpapoz]("http://ubuntuforums.org/showthread.php?t=56369&highlight=wallpapoz") where two of us appear to have the same problem.

I did not realize when I posted this that I was in an old warty forum.

[QUOTE=merinda]New version of wallpapoz is out. It supports multiple wallpapers per workspace.
[http://wallpapoz.sf.net]("http://wallpapoz.sf.net")

Dependencies is rather complex. Install them in order:
libxml++-2.10
libsigc++-2.0
glibmm-2.4
gtkmm-2.4
libglademm-2.4
... Regards,

Akbar[/QUOTE]
Here is what I did but it does not work. I am running Ubuntu Hoary 5.04.

Downloaded two files:
$ wget -c [http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2]("http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2")
$ wget -c [http://members.iinet.net.au/~gracey88/libxml++-2.10.0-1_i386.deb]("http://members.iinet.net.au/%7Egracey88/libxml++-2.10.0-1_i386.deb")

Then I installed libxml++-2.10 from  manicka's deb.
# dpkg -i libxml++-2.10.0-1_i386.deb

I then installed the dependencies: (note: these are not the exact libs from Akbar's instructions)
# apt-get install libsigc++-2.0-dev
# apt-get install libglibmm-2.4-dev
# apt-get install libgtkmm-2.4-dev
# apt-get install libglademm-2.4-dev

and then 
# tar -jxvf wallpapoz-0.2.tar.bz2
# cd wallpapoz-0.2
# make
# sh install.sh /usr

Everything seemed to work okay. But when I click on Applications>Accessories>Wallpapoz nothing happens.

When I run it from the command line I get this error message:
~ $ wallpapoz
wallpapoz: error while loading shared libraries: libxml++-2.6.so.2: cannot open shared object file: No such file or directory

I may have had the original version of wallpapoz on this machine at one point. I think libxml++-2.6.so.2 was needed for that.

Any suggestions. I am running hoary.

Thanks
Tomy

edited to add files I used.

---

### Post by angrykeyboarder on 2005-10-26
[quote=p!=f]I'm afraid there's no such a feature in Gnome (correct me if wrong) by default but you can use [http://wallpapoz.sourceforge.net/]("http://wallpapoz.sourceforge.net/") to have different wallpapers on each desktop.
I created the package just in case you don't want to compile it. Compiled for **Hoary** but may work on **Warty**. You have to
```

gzip -d wallpapoz_0.1-1_i386.deb.gz

``` it first. Hope it helps.[/quote]

I'd love to know you you were able to compile this.  I just downloaded it from Sourceforge and I'm getting errors in response to my "./configure" entry and I can't figure out how to get around them.

---

### Post by Tomy on 2005-10-26
[quote=angrykeyboarder]I'd love to know you you were able to compile this. I just downloaded it from Sourceforge and I'm getting errors in response to my "./configure" entry and I can't figure out how to get around them.[/quote] 
I wrote a HOWTO for installing wallpapoz.

[http://ubuntuforums.org/showthread.php?t=69507&highlight=wallpapoz]("http://ubuntuforums.org/showthread.php?t=69507&highlight=wallpapoz")

You can just run the script and it should install on Hoary. I added an old library to the dependencies and that got rid of my errors.

Tomy

---

### Post by angrykeyboarder on 2005-10-26
[quote=Tomy]I wrote a HOWTO for installing wallpapoz.

[http://ubuntuforums.org/showthread.php?t=69507&highlight=wallpapoz]("http://ubuntuforums.org/showthread.php?t=69507&highlight=wallpapoz")

You can just run the script and it should install on Hoary. I added an old library to the dependencies and that got rid of my errors.

Tomy[/quote]

That's not what I was looking for, but thanks anyway.

---

### Post by trinaryouroboros on 2005-11-08
[QUOTE=merinda]New version of wallpapoz is out. It supports multiple wallpapers per workspace.
[http://wallpapoz.sf.net](http://wallpapoz.sf.net)

Dependencies is rather complex. Install them in order:
libxml++-2.10
libsigc++-2.0
glibmm-2.4
gtkmm-2.4
libglademm-2.4

This is my guess. You can install libsigc++, glibmm, gtkmm, libglademm with your synaptic ( install development files too not just runtime ) but not libxml++ because libxml++ is not common library so I don't think Ubuntu will package for you. Compile it your self. Get it here:
[http://libxmlplusplus.sourceforge.net/](http://libxmlplusplus.sourceforge.net/)

About static file??? I made static file using statifier ( [http://statifier.sf.net](http://statifier.sf.net) ). The author of the statifier promise me the new version will be better. But I haven't try it. I am learning autopackage so it will help some people installing this software.

Tell me if you have problem installing this software. I'll help my best.

Regards,

Akbar[/QUOTE]

I'm just a semi n00b, but your program was incredible in Hoary Hedgehog. I went on here and immediately setup my own simple how-to to get Hoary + wallpapoz working wonderfully.

Now I'm getting a different problem, but this is since I upgraded to Dapper Drake Ubuntu. It's giving a "Segmentation fault" when I try to run the daemon for wallpapoz. Guess it's time to get cracking with self-education again.

---

### Post by Bob Morane on 2005-11-13
[Try this]("http://www.ubuntuforums.org/showthread.php?p=372864#post372864")

---

### Post by 0okami on 2005-11-24
[QUOTE=Bob Morane][Try this]("http://www.ubuntuforums.org/showthread.php?p=372864#post372864")[/QUOTE]

tried it... not working in breezy (5.10) for me... i get errors. 
Now its left incomplete. For now, i just want to get rid of any references to the program... 

Are there any left overs that need to be removed if the install failed? if so where do i go to remove them? 

Anyone get this working on breezy 5.10?

---

### Post by merinda on 2005-12-06
Hi,

Initially I developed Wallpapoz using C++, libxml++ ( C++ version of libxml ) and gtkmm ( C++ version of gtkmm ). Later this choice gave many users problems. Most of them had difficulties installing gtkmm library if not libxml++. 

However the big problem is the program ( the daemon ) crashes when running in Ubuntu Breezy Badger but the program runs fine in Fedora Core 4. The gui however runs fine in both distro. So I tracked it down.... then found that the problem was located in threading part. After reading and thinking it many times, I couldn't find the solution. I have no idea why the program get crashed when the program creates the threads. 

So I decided to convert the daemon source to python. It works fine. But it's weird if the gui source is in C++ but the daemon is in python. Then I convert the gui source to python source using pygtk.

Ok, go to the official site to download the wallpapoz in python version.
[http://wallpapoz.sf.net](http://wallpapoz.sf.net)

Someday maybe I will fix the bug in C++ version of Wallpapoz but I'm not sure.

Regards,

Akbar

---

### Post by Sionide on 2005-12-16
Just installed Wallpapoz 0.3 after finding this thread. It works well, maybe a one second delay in changing wallpaper when you switch desktops - I'll see how it goes, might get rid of it, might not..

---

### Post by vvlaw on 2005-12-19
is that not support the xfce4?

---

### Post by sanane on 2006-11-17
```

root@ubuntu:/home/prodigy/downloads# sudo apt-get install libglademm-2.4-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libglademm-2.4-1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libglademm-2.4-1c2a
E: Package libglademm-2.4-1 has no installation candidate
root@ubuntu:/home/prodigy/downloads# wallpapoz
wallpapoz: error while loading shared libraries: libglademm-2.4.so.1: cannot open shared object file: No such file or directory
root@ubuntu:/home/prodigy/downloads# apt-get install libxml++2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxml++2.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxml++2.6c2a
E: Package libxml++2.6 has no installation candidate
root@ubuntu:/home/prodigy/downloads# sudo dpkg -i wallpapoz_0.1-1_i386.deb
Selecting previously deselected package wallpapoz.
(Reading database ... 109126 files and directories currently installed.)
Unpacking wallpapoz (from wallpapoz_0.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of wallpapoz:
 wallpapoz depends on libglademm-2.4-1; however:
  Package libglademm-2.4-1 is not installed.
 wallpapoz depends on libglibmm-2.4-1; however:
  Package libglibmm-2.4-1 is not installed.
 wallpapoz depends on libgtkmm-2.4-1; however:
  Package libgtkmm-2.4-1 is not installed.
 wallpapoz depends on libsigc++-2.0-0 (>= 2.0.2); however:
  Package libsigc++-2.0-0 is not installed.
 wallpapoz depends on libxml++2.6; however:
  Package libxml++2.6 is not installed.
dpkg: error processing wallpapoz (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wallpapoz
root@ubuntu:/home/prodigy/downloads# wallpapoz
wallpapoz: error while loading shared libraries: libglademm-2.4.so.1: cannot open shared object file: No such file or directory
root@ubuntu:/home/prodigy/downloads# 

```


why is installing tricky that much....

can someone just help me plz....

i installed all packages with synaptic and then

```
sudo apt-get install libglademm-2.4-1
```

but i got the error which is at the bottom.... :(

---

### Post by bboywh1teout on 2008-02-19
i tried to open wallpapoz with GDebi package installer and it gives ma an error,
Wrong architecture 'i386'

---

### Post by 0okami on 2008-02-20
> **bboywh1teout said:**
> i tried to open wallpapoz with GDebi package installer and it gives ma an error,
Wrong architecture 'i386'

hmm. I've seen that only when i grab the wrong build... for example, when trying to install a 64bit app on a 32bit...

---

