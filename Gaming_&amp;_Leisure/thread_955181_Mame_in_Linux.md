---
title: "Mame in Linux"
date: 2008-10-21
forum: Gaming &amp; Leisure
---

### Post by jukingeo on 2008-10-21
Hello,

I used to run a program called Multiple Arcade Machine Emulator (MAME) in Windows.  Is there a Linux version floating around???

---

### Post by DoktorSeven on 2008-10-22
[SDLmame](http://rbelmont.mameworld.info/?page_id=163)

Should be in Multiverse repos in latest versions of Ubuntu.  It has a simple "type in the game name" interface by default but you can get a frontend -- I use kxmame (the SVN version that works with SDLmame) and made a package [here](http://sdcofer.googlepages.com/) (works in 8.04 at the very least).

Be sure to edit /etc/sdlmame/mame.ini (you'll have to use sudo/gksudo/kdesu) with at least the path to your ROMs.

---

### Post by bpalone on 2008-10-22
Here is a link to some useful information:

[http://www.danielandrade.net/2008/01/08/running-mame-games-on-ubuntu/](http://www.danielandrade.net/2008/01/08/running-mame-games-on-ubuntu/)

---

### Post by powerqun on 2008-10-22
Q: What's the best time for a dental appointment? A: Tooth-thirty.        ............................................................................................................................................buy [world of warcraft gold](http://www.mmoinn.com/)| cheap [wow power leveling](http://www.mmoinn.com/mmoinn_pl/)| site: [http://www.mmoinn.com](http://www.mmoinn.com)|buy [wow gold](http://woweu.mmoinn.com/index.do?PageModule=OrderForm_new)|cheap [wow gold](http://www.mmoinn.com)

---

### Post by jukingeo on 2008-10-22
> **DoktorSeven said:**
> [SDLmame](http://rbelmont.mameworld.info/?page_id=163)

Should be in Multiverse repos in latest versions of Ubuntu.  It has a simple "type in the game name" interface by default but you can get a frontend -- I use kxmame (the SVN version that works with SDLmame) and made a package [here](http://sdcofer.googlepages.com/) (works in 8.04 at the very least).

Be sure to edit /etc/sdlmame/mame.ini (you'll have to use sudo/gksudo/kdesu) with at least the path to your ROMs.


I will say that overall I am looking for a version that has a front end that you would see on an arcade game.  Kind of like the systems they have on the "Build Your Own Arcade Controls" website.

However, for the sake of playing games and simplicity in set up, I decided to give your package a shot and installed it.  BUT there is a problem.  I can't find it.  I looked under Games, under Accessories, under Graphics.  Where did it go?


> Here is a link to some useful information:

[http://www.danielandrade.net/2008/01...mes-on-ubuntu/](http://www.danielandrade.net/2008/01...mes-on-ubuntu/)

I downloaded Xmame tonight and I just browsed through the documentation.  WOW!  There is much to go through there.  It looks like a lot of work to set it up.




EDIT:

Hello guys

This is more of what I am after in a front end:

[http://www.anti-particle.com/wahcade.shtml](http://www.anti-particle.com/wahcade.shtml)

Supposedly this is based off of the MameWah for Windows.  I used MameWah before.  BUT I don't know something like this would get set up in Linux.  Has anyone used this front end?

Geo

Geo

---

### Post by Rotarychainsaw on 2008-10-22
[http://sourceforge.net/projects/gva/](http://sourceforge.net/projects/gva/)

I use that as my front end to sdl mame. Gets the job done, and the developer answers requests haha.

---

### Post by features on 2008-10-22
What about KXMame?  It's in the repositories.  It's what I use for MAME, and I find it not too bad.

---

### Post by DoktorSeven on 2008-10-23
> **jukingeo said:**
> However, for the sake of playing games and simplicity in set up, I decided to give your package a shot and installed it.  BUT there is a problem.  I can't find it.  I looked under Games, under Accessories, under Graphics.  Where did it go?

I don't think it makes a shortcut.  Just make your own calling the executable "kxmame".

---

### Post by jukingeo on 2008-10-23
> **features said:**
> What about KXMame?  It's in the repositories.  It's what I use for MAME, and I find it not too bad.

Oh, wait.  I just got to thinking.  Isn't KXMame for KDE? I have Gnome.

> **DoktorSeven said:**
> I don't think it makes a shortcut.  Just make your own calling the executable "kxmame".

Ok, I ended up confusing myself.  I thought what I downloaded and installed was SDLMame.  More then likely Kxmame is for KDE.  As I said above I have Gnome. I guess that is the reason why I am not finding anything.  More then likely the install didn't take.

I did download both SDLMame AND Xmame...but Xmame seems like it has a really complicated procedure in order to get it working.  So I installed the SDLMame via your package.  But it may look like I have to find it and uninstall if if it was meant for KDE.

Background check:  I only been on Linux for about 5 months now.  Usually everything I installed was either from a .deb file, .rar file or from the repositories.  Everything has a an icon to click on to start the program...so this is kind of unusual for me.  Does it have to be started up in the Terminal?

Thanx,

Geo

---

### Post by jukingeo on 2008-10-23
> **Rotarychainsaw said:**
> [http://sourceforge.net/projects/gva/](http://sourceforge.net/projects/gva/)

I use that as my front end to sdl mame. Gets the job done, and the developer answers requests haha.


Yeah, I think this is the front end I need as it says it is for Gnome.

Doktor Seven, how do I uninstall that package now.  I don't think it was the right one.  I believe I have to use what RotaryCS recommends as that is meant for Gnome.  I just need to know how to set it up with SDLMame.

So what about WahCade?  Anyone use that?  It certainly looks more like an arcade machine front end than anything else I seen thusfar.

Thanx y'all!

---

### Post by disturbedite on 2008-10-24
> **jukingeo said:**
> Oh, wait.  I just got to thinking.  Isn't KXMame for KDE? I have Gnome.

yes it is but use kxmame. kxmame has many improvements over gxmame.

---

### Post by Rotarychainsaw on 2008-10-24
SDLMame has a file in /etc. edit it as root and put the path to your roms folder. You can tweak other stuff in there, but I think the defaults work. GVA reads everything from the sdlmame config.

---

### Post by jukingeo on 2008-10-25
Hello,

I can't find the Kxmame (or SDLMame) anywhere.  I looked in etc folder and didn't find anything. So I don't know where it went. Perhaps it didn't install after all.

Next problem:

Since I can't find the kxmame install, I proceeded to the separate installation of SDLMame and gnome-video-arcade front end.

While this is an unacceptable front end for an arcade game I decided to give it a shot to see how mame performs in the Linux environment.

I downloaded both progams and set them up in my "games" directory.  After unpacking SDLMame, I did notice that is shares familiar folders to it's Windows counterpart.  I didn't see any kind of installation for SDLMame, so I guess I am good to go there?

Next I moved to the gnome-video-arcade front end and it looked like there was an install procedure there.  There was a readme file there that I read.  So I started to follow that.  Low and behold there is a problem:

Here is my terminal output:

geo@home:~/Games$ cd gnome-video-arcade-0.6.4
geo@home:~/Games/gnome-video-arcade-0.6.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.12) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

geo@home:~/Games/gnome-video-arcade-0.6.4$ 

What the heck is glib-2.0??  Apparently the front end will not load without it.  I searched in both Add/remove programs and the Synaptic repository and that file is no where to be found.

Please advise on how to proceed.

Thank You,

Geo

---

### Post by jukingeo on 2008-11-14
Hello All, 

I have successfully installed both SDLMame (Ubuntu Synaptic Repository version) and I am going to use this with the WahCade front end (download/Install from website).

I would appreciate any advice on how to set these two programs up together.

Thank You,

Geo

---

### Post by binbash on 2008-11-14
> **jukingeo said:**
> Hello,

I can't find the Kxmame (or SDLMame) anywhere.  I looked in etc folder and didn't find anything. So I don't know where it went. Perhaps it didn't install after all.

Next problem:

Since I can't find the kxmame install, I proceeded to the separate installation of SDLMame and gnome-video-arcade front end.

While this is an unacceptable front end for an arcade game I decided to give it a shot to see how mame performs in the Linux environment.

I downloaded both progams and set them up in my "games" directory.  After unpacking SDLMame, I did notice that is shares familiar folders to it's Windows counterpart.  I didn't see any kind of installation for SDLMame, so I guess I am good to go there?

Next I moved to the gnome-video-arcade front end and it looked like there was an install procedure there.  There was a readme file there that I read.  So I started to follow that.  Low and behold there is a problem:

Here is my terminal output:

geo@home:~/Games$ cd gnome-video-arcade-0.6.4
geo@home:~/Games/gnome-video-arcade-0.6.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.12) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

geo@home:~/Games/gnome-video-arcade-0.6.4$ 

What the heck is glib-2.0??  Apparently the front end will not load without it.  I searched in both Add/remove programs and the Synaptic repository and that file is no where to be found.

Please advise on how to proceed.

Thank You,

Geo

sudo apt-get install libglib2.0-dev

---

### Post by jukingeo on 2008-11-15
> **binbash said:**
> sudo apt-get install libglib2.0-dev

I am no longer going the original route.  I would like to get WahCade to work with SDLMame now.  I like this front end.  It is the sister program to Mamewah of which I used under Windows.  The website is a bit unclear about setting everything up.  As of now WahCade DOES launch, but it still as to be set up.

---

