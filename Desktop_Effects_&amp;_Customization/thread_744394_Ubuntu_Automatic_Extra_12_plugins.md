---
title: "Ubuntu Automatic Extra 12 plugins"
date: 2008-04-03
forum: Desktop Effects &amp; Customization
---

### Post by 22flames on 2008-04-03
Hello here is a script i wrote to installe all of the extra non included compiz plugins in gusty gibbon. If Enough people request i will spend alot of time and find the commands to make a script of the same type for ubuntu hardy haron as a dont have this yet i might need people to test please pm me if you want to help.



Before you do this

1.Go to Applications menu

2.Go to add remove programs

3.Search ccsm

4.Download and install ccsm



Instructions

1. Download this script

Sendspace

 [http://www.sendspace.com/file/crok4y](http://www.sendspace.com/file/crok4y)

Megaupload

[http://www.megaupload.com/?d=7G1UE72M](http://www.megaupload.com/?d=7G1UE72M)

or Rapidshare

[http://rapidshare.com/files/10474255..._gusty.sh.html](http://rapidshare.com/files/10474255..._gusty.sh.html)


1.5. You might have to right click go to permissions and tick the allow executing file as program box

2. Double click run in terminal

3. say y to all

4.When asks for password enter yours

5.enjoy new plugins in ccsm

Edit- This is for gusty in not sure if it will work in hardy

instructions from jryprt

---

### Post by alexsabree on 2008-04-03
What about hardy heron, will this work with it?

---

### Post by 16777216 on 2008-04-04
> **alexsabree said:**
> What about hardy heron, will this work with it?


I'm about to find out. So pull up a piece of floor and sit beside it.   :popcorn:

Then again maybe not. I get a 404.

---

### Post by 22flames on 2008-04-04
hmm it works gusty and im not getting a 404

---

### Post by 22flames on 2008-04-04
Here i will upload to rapidshare and megaupload so you can download

Megaupload

[http://www.megaupload.com/?d=7G1UE72M](http://www.megaupload.com/?d=7G1UE72M)

or Rapidshare

[http://rapidshare.com/files/104742555/compiz_13_plugins_gusty.sh.html](http://rapidshare.com/files/104742555/compiz_13_plugins_gusty.sh.html)


have fun

---

### Post by 16777216 on 2008-04-04
Had a thunder storm and tornado roll through here, well near here so the intertubes was wonky.

About to try again.

Sorry, not a thing works I get errors on every compile.

---

### Post by 22flames on 2008-04-04
thats why its for gusty not hardy but thanks for the info

---

### Post by 22flames on 2008-04-04
if i get help i might make a hardy one

---

### Post by 22flames on 2008-04-04
does noone need this

---

### Post by 16777216 on 2008-04-04
Yeah sure! 
But I think compiz on hardy has 3d fireflies tile and screensaver. (but I have tried an install script like this one with gutsy and when I upgraded to hardy I left my /home partition untouched so I may have remnants. )

It has 3d but that is it.

---

### Post by dboot on 2008-04-04
What 12 extra plugins are you referring to? After installing compiz manager, there already seems to be tons of features/options.

---

### Post by 22flames on 2008-04-04
So this script wont work on hardy but it has the 3d windows built in because its the new compiz so i need to find the new plugins that work with the upgraded plugins in compiz im still not sure why nobody has used this script for gusty though.... were not all on hardy yet

---

### Post by 16777216 on 2008-04-04
Oh,.. There's a *lot* more than that.  
[http://www.compiz-fusion.org/](http://www.compiz-fusion.org/)

---

### Post by 16777216 on 2008-04-04
> **22flames said:**
> So this script wont work on hardy but it has the 3d windows built in because its the new compiz so i need to find the new plugins that work with the upgraded plugins in compiz im still not sure why nobody has used this script for gusty though.... were not all on hardy yet


Well if we keep jabbering on like this maybe someone will look. :lolflag:

---

### Post by 22flames on 2008-04-04
3d windows snow on desktop screensaver 3d cube or windows most of the videos you see on youtube use these so try the instructions youll see the differance

Here are two of theme

[http://youtube.com/watch?v=Rmz9a9pJR_s](http://youtube.com/watch?v=Rmz9a9pJR_s)

---

### Post by 22flames on 2008-04-04
yah hopefully they will i mean :lolflag:

---

### Post by 16777216 on 2008-04-04
Sorry it was too long to PM to you.

```
paul@Alpha:~/Desktop$ ./'1 plugin test(2).sh'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-bcop is already the newest version.
compiz-dev is already the newest version.
build-essential is already the newest version.
libxcomposite-dev is already the newest version.
libpng12-dev is already the newest version.
libsm-dev is already the newest version.
libxrandr-dev is already the newest version.
libxdamage-dev is already the newest version.
libxinerama-dev is already the newest version.
libstartup-notification0-dev is already the newest version.
libgconf2-dev is already the newest version.
librsvg2-dev is already the newest version.
libdbus-1-dev is already the newest version.
libdbus-glib-1-dev is already the newest version.
libgnome-desktop-dev is already the newest version.
x11proto-scrnsaver-dev is already the newest version.
libxss-dev is already the newest version.
libxslt1-dev is already the newest version.
libtool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
--15:07:16--  http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f
           => `/tmp/screensaver.tar.gz'
Resolving gitweb.opencompositing.org... 195.114.19.35
Connecting to gitweb.opencompositing.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]

    [  <=>                                ] 14,550        35.63K/s             

15:07:16 (35.54 KB/s) - `/tmp/screensaver.tar.gz' saved [14550]

compiling : matrix.cpp -> build/matrix.loIn file included from matrix.h:6,
                 from matrix.cpp:1:
vector.h: In member function ‘Vector Vector::toScreenSpace(CompScreen*) const’:
vector.h:37: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h:38: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h: In member function ‘Vector Vector::toCoordsSpace(CompScreen*) const’:
vector.h:46: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h:47: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
In file included from matrix.cpp:1:
matrix.h: At global scope:
matrix.h:15: error: expected ‘,’ or ‘...’ before ‘*’ token
matrix.h:15: error: ISO C++ forbids declaration of ‘CompTransform’ with no type
matrix.h: In constructor ‘Matrix::Matrix(int)’:
matrix.h:15: error: ‘mat’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::rotate(float, float, float, float)’:
matrix.h:30: error: ‘CompTransform’ was not declared in this scope
matrix.h:30: error: expected primary-expression before ‘)’ token
matrix.h:30: error: ‘matrixRotate’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::scale(float, float, float)’:
matrix.h:38: error: ‘CompTransform’ was not declared in this scope
matrix.h:38: error: expected primary-expression before ‘)’ token
matrix.h:38: error: ‘matrixScale’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::translate(float, float, float)’:
matrix.h:46: error: ‘CompTransform’ was not declared in this scope
matrix.h:46: error: expected primary-expression before ‘)’ token
matrix.h:46: error: ‘matrixTranslate’ was not declared in this scope
make: *** [build/matrix.lo] Error 1
compiling : matrix.cpp -> build/matrix.loIn file included from matrix.h:6,
                 from matrix.cpp:1:
vector.h: In member function ‘Vector Vector::toScreenSpace(CompScreen*) const’:
vector.h:37: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h:38: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h: In member function ‘Vector Vector::toCoordsSpace(CompScreen*) const’:
vector.h:46: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
vector.h:47: error: invalid use of incomplete type ‘struct _CompScreen’
/usr/include/compiz/compiz.h:47: error: forward declaration of ‘struct _CompScreen’
In file included from matrix.cpp:1:
matrix.h: At global scope:
matrix.h:15: error: expected ‘,’ or ‘...’ before ‘*’ token
matrix.h:15: error: ISO C++ forbids declaration of ‘CompTransform’ with no type
matrix.h: In constructor ‘Matrix::Matrix(int)’:
matrix.h:15: error: ‘mat’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::rotate(float, float, float, float)’:
matrix.h:30: error: ‘CompTransform’ was not declared in this scope
matrix.h:30: error: expected primary-expression before ‘)’ token
matrix.h:30: error: ‘matrixRotate’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::scale(float, float, float)’:
matrix.h:38: error: ‘CompTransform’ was not declared in this scope
matrix.h:38: error: expected primary-expression before ‘)’ token
matrix.h:38: error: ‘matrixScale’ was not declared in this scope
matrix.h: In member function ‘Matrix& Matrix::translate(float, float, float)’:
matrix.h:46: error: ‘CompTransform’ was not declared in this scope
matrix.h:46: error: expected primary-expression before ‘)’ token
matrix.h:46: error: ‘matrixTranslate’ was not declared in this scope
make: *** [build/matrix.lo] Error 1
paul@Alpha:~/Desktop$
```

---

### Post by 22flames on 2008-04-05
bump

---

### Post by santiagoward2000 on 2008-04-05
I like the idea. I haven't tested it because I'd already compiled the plugins myself in Gutsy, but I'd like to see one for Hardy (if you could do it, of course!) :)

---

### Post by 16777216 on 2008-04-05
It seems to be a pain in the buttocks so far. :):(

---

### Post by dboot on 2008-04-06
Your script worked for me perfectly in Gutsy. Thanks!

---

### Post by 22flames on 2008-04-07
your very welcome i hope more people like you will look into this and comment ok :KS

---

### Post by 22flames on 2008-04-13
.....

---

### Post by 22flames on 2008-04-16
bump .....:popcorn:

---

### Post by Lantesh on 2008-04-16
Hey I wanted to let you know this worked absolutely fantastic for me.  I had been wanting to add some additional plugins, but all the instructions I'd run across before left too much room for error.  It always seemed that people were having issues, and with my compilation skills being pretty bad I had decided to play it safe and let well enough alone.  Then I saw this thread.  Your script is so simple to use...how is it said in those Geico commercials, even a caveman could do it.  All I can say is THANK YOU VERY VERY VERY Much!!!  Oh and for the record I installed this in LInux Mint 4.0, which is based on Gutsy, so I'd imagine this script will work on any of the Gutsy variants.

Edit: Just thought I'd post back here the one error I've noticed.  In the "Cube Atlantis" plugin I can't change any of the settings, or I should say I can change them, but the changes don't take effect.  The plugin works in that I do get an aquarium inside my cube, but I can't change the number of fish.  It will only show the default setup.  Anyway it's not a big deal.  I just thought that was odd.

---

### Post by noctis_vulpes on 2008-04-17
Still on Feisty with Beryl, so I'm afraid I can't test this out yet... Will be upgrading to Hardy when it comes out, and I will VERY much like to see Hardy version of this script. Thanks for your time and effort, 22flames. ^^

---

### Post by 22flames on 2008-04-18
Thank you all for your comments i relly enjoy reading them and i will be trying with the hardy script im still working on it ill post it when im done but i dont have hardy yet so when it comes out i will work on it

---

### Post by NEUR0M4NCER on 2008-04-24
Hi - awesome script, thanks so much for making it. Works well on Gutsy AMD64 for me. Can't get the screensaver plugin to work though - settings say it should initiate after 1 minute, but nothing. I disabled the gnome screensaver, as I thought that might be messing things up, but no luck.

Any ideas?

---

### Post by NEUR0M4NCER on 2008-05-03
Finally managed the upgrade to Hardy - would love if there was any progress with a Hardy version of your script?

Regards

---

### Post by 22flames on 2008-05-08
Im Actully  working on that right now thank you for all the comments and i had some problems with the screensaver at first to but there is some setting in compiz or gnome i cant remember witch that enables it so just fiddle around with it and you can expect to see a new script within the next few weeks lol buy

22flames
junior linux ninja

---

### Post by NEUR0M4NCER on 2008-05-12
Awesome - I look forward to it.

Thanks again for all of your hard work!


Regards

---

### Post by LeShin on 2008-05-13
This would be brilliant if you can get the script working in Hardy! Been trying to find away to add the cubeaddon and reflection (for the cylinder desktop) and title plugins into my current compiz but no joy (I did manage to get the snow plugin working). Some guy over at the compiz-fusion forum said that plugin just doesn't work in Hardy, hopefully he's wrong. A big THANK YOU in advance :)

---

### Post by olskar on 2008-06-14
Would also love this in Hardy! Any progress?

---

### Post by NEUR0M4NCER on 2008-06-14
There is exactly this for Hardy, by the O.P., in [Installation Scripts for Everything](http://ubuntuforums.org/showthread.php?t=800950). An excellent thread, and the Compiz script worked perfectly on my Hardy AMD64 setup - hello sphere.

Regards

---

