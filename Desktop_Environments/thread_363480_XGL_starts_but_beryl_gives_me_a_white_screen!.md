---
title: "XGL starts but beryl gives me a white screen!"
date: 2007-02-17
forum: Desktop Environments
---

### Post by Copperteeth on 2007-02-17
I recently replaces a failed harddrive and i reloaded ubuntu and updated everything. I installed XGL and beryl using this guide [HERE]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html") and most everything worked. Unfortunately though after xgl starts up beryl starts up and gives me a white screen, i know its running because i can rotate the cube but i cannot see my desktop, i was able to get a screen capture before i switched back into GNOME. [Screenshot here]("http://img.photobucket.com/albums/v239/copperteeth/Screenshot-4.png")

---

### Post by roongpatoong on 2007-02-20
I am experiencing the same issue. Only thing is - I followed the same install guide as you and everything was fine, then today I was prompted to install some updates and I think right after that I started to get the white screen issue.

Searching the net has shown LOTS of people getting this behaviour at different times over the past couple of months but I still haven't managed to find any particular fix!

It's a shame coz I was really digging Beryl and was getting used to its usability advantages - not to mention all that candy ;)

Let us know if anyone knows of a fix ...

---

### Post by thnogueira on 2007-02-20
from
[COLOR="Blue"][ http://forum.beryl-project.org/viewtopic.php?f=36&t=3756]("http://forum.beryl-project.org/viewtopic.php?f=36&t=3756")[/COLOR]

I solved your problem running:

```
$ beryl-manager --no-force-window-manager

```

and then:

```
$ beryl-xgl --use-copy
```

BTW. Have you ever tried the [COLOR="Blue"][search]("http://www.ubuntuforums.org/search.php") [/COLOR]tools? IT WORKS!!!

Try [COLOR="Blue"][this,]("http://www.ubuntuforums.org/search.php?searchid=14946639")[/COLOR] for example.

---

### Post by lemoniceblock on 2007-02-22
What thnogueria posted does work but I had a nightmare using that when my computer crashed 3 times consecutively  @________@
I found this:
```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &
```
Type that into your terminal when you're on your XGL session.
It's not perfect but so far it hasn't crashed for me yet =P but I can only use it when the XGL session luckily doesn't show up as a white screen; does anyone know if it's possible to write a script or something so that the LD_PRELOAD... is entered once we log into XGL?
Thanks in advance ~^^~

---

### Post by tripleZero on 2007-02-22
i used to have that problem on edgy but i fixed it by uninstalling beryl and xgl, then install AIGLX and beryl.  after that it worked great

---

### Post by lemoniceblock on 2007-02-23
Yep, I was using AIGLX too and it worked perfectly but I couldn't get the right resolution for my screen until I switched to the proprietary driver which doesn't support AIGLX...

---

### Post by jay019 on 2007-02-23
> **thnogueira said:**
> from
[COLOR="Blue"][ http://forum.beryl-project.org/viewtopic.php?f=36&t=3756]("http://forum.beryl-project.org/viewtopic.php?f=36&t=3756")[/COLOR]

I solved your problem running:

```
$ beryl-manager --no-force-window-manager

```

and then:

```
$ beryl-xgl --use-copy
```

BTW. Have you ever tried the [COLOR="Blue"][search]("http://www.ubuntuforums.org/search.php") [/COLOR]tools? IT WORKS!!!

Try [COLOR="Blue"][this,]("http://www.ubuntuforums.org/search.php?searchid=14946639")[/COLOR] for example.

I used search, found this post and am now enjoying beryl. WOW!!!!!!!! Thanks thnogueira, I have something for the vista fanboys to really get excited about. Like shimering windows, desktop cube and all the stuff Im going to find out about it in the next few hours of playing around. Peace!!!

---

### Post by nachotronics on 2007-02-23
Here's a solution I got from _[**Forlong's** post in the beryl forums]("http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=330")_[SIZE="3"]** it consists in downgrading to the last working version from Treviños svn repository. **[/SIZE]

1. Uninstall Beryl completely
```
sudo apt-get remove 'beryl*'
```

2. Remove the SVN-repository (or any other Beryl-repo) so it won't update, till the next tested working version comes out
```
sudo gedit /etc/apt/sources.list
```
Then comment every beryl related line by adding # at the beggining, in my case they looked like this:
```
# deb http://ubuntu.beryl-project.org edgy main
# deb-src http://ubuntu.beryl-project.org edgy main
# deb http://www.beerorkid.com/compiz edgy main-edgy
# deb http://media.blutkind.org/xgl edgy main (latest: beryl 0.1.1)
# deb http://beryl.xglusers.de/ edgy main (latest: beryl 0.1.4; no aquamarine)
# deb http://download.tuxfamily.org/3v1deb edgy beryl-svn ( bleeding edge beryl development, use with care )
```

3. Look for these packages in /var/cache/apt/archives/

beryl_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-core_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-manager_0.2.0+svn20070213-r4019+3v1ubuntu0_i386.deb
beryl-plugins_0.2.0+svn20070218-r4130+3v1ubuntu0_i386.deb
beryl-plugins-data_0.2.0+svn20070218-r4130+3v1ubuntu0_all.deb
beryl-settings_0.2.0+svn20070218-r4140+3v1ubuntu0_i386.deb
beryl-settings-bindings_0.2.0+svn20070201-r3550+3v1ubuntu0_i386.deb
emerald_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb
libberyldecoration0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libberylsettings0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libemeraldengine0_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb

also optional: emerald-themes_0.2.0+svn20070126-r3229+3v1ubuntu0_all.deb

Or download them from _[**Treviños** svn repository]("http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/")_ or just [_**get the entire set at once from rapidshare -> beryl-svn.tar.gz**_]("http://rapidshare.com/files/17958701/beryl-svn.tar.gz.html")

4. Copy them to another folder e.g. beryl-svn on your desktop

5. Open a terminal and go to that directory
```
cd ~/Desktop/beryl-svn
```

6. Install all packages of that folder:
```
sudo dpkg -i *.deb
```

7. Start beryl by running
```
beryl-manager
```

8. Enjoy\\:D/

---

### Post by ramasdf123 on 2007-02-25
LOL, rather than running this in the terminal add both of the commands to session manager for startup and it works

:lolflag: then run the manager to get everything else working

---

### Post by CaptSaltyJack on 2007-02-25
FYI, this is one thing I find annoying.. a hundred different articles/blogs on how to install Beryl, and so many of them differ from one another.

This guide here should get you a completely clean and working install of Beryl on Ubuntu.  I followed the instructions and it worked 100% the first time, zero problems.

[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

Actually, I was getting the black windows bug, so I had to set Beryl to "force AIGLX", it's an nvidia driver bug apparently.  Other than that, no problems.

---

### Post by 4KvRMU7Nnv on 2007-02-26
I noticed this as well with Xgl.  I am currently using Aiglx becuase i cannot tolerate having anything less than the most amazing eye candy so i have to use beryl.  I would use Xgl but it causes the white screen.  if you Have ATi or something and need Xgl, i suggest just using plain old compiz as it doesn't crash like this right now.

---

