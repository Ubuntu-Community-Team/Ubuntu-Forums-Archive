---
title: "X with snow"
date: 2007-11-13
forum: Desktop Effects &amp; Customization
---

### Post by sDoky on 2007-11-13
Hi guys, I'm starting to prepare for upcoming Christmas by adding snow effect to my desktop. Well that's the easy part - I mean thinking. The thing is a little bit more complicated than I thought it would be. Here's my problem: I use compiz (not fusion) but that ought to be OK since there's a package on [http://compiz.org/plugins](http://compiz.org/plugins) with the determined snow plugin ([this]("http://www.anykeysoftware.co.uk/compiz/plugins/snow.tar.gz")). I unpacked it, and when I executed command
```
make
sudo make install
```
it just gave me some kind of an error:
```
sdoky@sdoky-desktop:~/snow$ make
[: 1: ==: unexpected operator
-e compiling : snow.c -> build/libsnow.losnow.c:89: warning: implicit declaration of function 'N_'
snow.c:89: error: initializer element is not constant
snow.c:89: error: (near initialization for 'snowDirections[0]')
snow.c:90: error: initializer element is not constant
snow.c:90: error: (near initialization for 'snowDirections[1]')
snow.c:91: error: initializer element is not constant
snow.c:91: error: (near initialization for 'snowDirections[2]')
snow.c:93: error: initializer element is not constant
snow.c:93: error: (near initialization for 'snowDirections[3]')
snow.c: In function 'beginRendering':
snow.c:314: warning: passing argument 2 of 'prepareXCoords' makes pointer from integer without a cast
snow.c: In function 'snowPaintScreen':
snow.c:419: warning: passing argument 2 of 's->paintScreen' from incompatible pointer type
snow.c:419: warning: passing argument 3 of 's->paintScreen' makes integer from pointer without a cast
snow.c:419: error: too many arguments to function 's->paintScreen'
snow.c:419: error: void value not ignored as it ought to be
snow.c:419: warning: statement with no effect
snow.c:420: warning: assignment from incompatible pointer type
snow.c: In function 'snowPaintWindow':
snow.c:438: warning: passing argument 3 of 'w->screen->paintWindow' from incompatible pointer type
snow.c:438: warning: passing argument 4 of 'w->screen->paintWindow' makes pointer from integer without a cast
snow.c:438: error: too few arguments to function 'w->screen->paintWindow'
snow.c:438: warning: assignment makes integer from pointer without a cast
snow.c:439: warning: assignment from incompatible pointer type
snow.c: In function 'snowInitScreen':
snow.c:592: warning: assignment from incompatible pointer type
snow.c:596: warning: assignment from incompatible pointer type
snow.c: In function 'snowDisplayInitOptions':
snow.c:769: error: 'CompOption' has no member named 'shortDesc'
snow.c:769: warning: statement with no effect
snow.c:770: error: 'CompOption' has no member named 'longDesc'
snow.c:770: warning: statement with no effect
snow.c:779: error: 'CompOption' has no member named 'shortDesc'
snow.c:779: warning: statement with no effect
snow.c:780: error: 'CompOption' has no member named 'longDesc'
snow.c:780: warning: statement with no effect
snow.c:789: error: 'CompOption' has no member named 'shortDesc'
snow.c:789: warning: statement with no effect
snow.c:790: error: 'CompOption' has no member named 'longDesc'
snow.c:790: warning: statement with no effect
snow.c:799: error: 'CompOption' has no member named 'shortDesc'
snow.c:799: warning: statement with no effect
snow.c:800: error: 'CompOption' has no member named 'longDesc'
snow.c:802: warning: statement with no effect
snow.c:810: error: 'CompOption' has no member named 'shortDesc'
snow.c:810: warning: statement with no effect
snow.c:811: error: 'CompOption' has no member named 'longDesc'
snow.c:813: warning: statement with no effect
snow.c:822: error: 'CompOption' has no member named 'shortDesc'
snow.c:822: warning: statement with no effect
snow.c:823: error: 'CompOption' has no member named 'longDesc'
snow.c:825: warning: statement with no effect
snow.c:834: error: 'CompOption' has no member named 'shortDesc'
snow.c:834: warning: statement with no effect
snow.c:835: error: 'CompOption' has no member named 'longDesc'
snow.c:835: warning: statement with no effect
snow.c:844: error: 'CompOptionRestriction' has no member named 's'
snow.c:844: error: request for member 'string' in something not a structure or union
snow.c:844: warning: statement with no effect
snow.c:845: error: 'CompOptionRestriction' has no member named 's'
snow.c:845: error: request for member 'nString' in something not a structure or union
snow.c:845: warning: statement with no effect
snow.c:849: error: 'CompOption' has no member named 'shortDesc'
snow.c:849: warning: statement with no effect
snow.c:850: error: 'CompOption' has no member named 'longDesc'
snow.c:850: warning: statement with no effect
snow.c:864: error: 'CompOption' has no member named 'shortDesc'
snow.c:864: warning: statement with no effect
snow.c:865: error: 'CompOption' has no member named 'longDesc'
snow.c:865: warning: statement with no effect
snow.c:871: error: 'CompOption' has no member named 'shortDesc'
snow.c:871: warning: statement with no effect
snow.c:872: error: 'CompOption' has no member named 'longDesc'
snow.c:872: warning: statement with no effect
snow.c:878: error: 'CompOption' has no member named 'shortDesc'
snow.c:878: warning: statement with no effect
snow.c:879: error: 'CompOption' has no member named 'longDesc'
snow.c:879: warning: statement with no effect
snow.c:882: error: 'CompOptionRestriction' has no member named 's'
snow.c:882: error: request for member 'string' in something not a structure or union
snow.c:882: warning: statement with no effect
snow.c:883: error: 'CompOptionRestriction' has no member named 's'
snow.c:883: error: request for member 'nString' in something not a structure or union
snow.c:883: warning: statement with no effect
snow.c:887: error: 'CompOption' has no member named 'shortDesc'
snow.c:887: warning: statement with no effect
snow.c:888: error: 'CompOption' has no member named 'longDesc'
snow.c:888: warning: statement with no effect
snow.c:894: error: 'CompOption' has no member named 'shortDesc'
snow.c:894: warning: statement with no effect
snow.c:895: error: 'CompOption' has no member named 'longDesc'
snow.c:897: warning: statement with no effect
snow.c: At top level:
snow.c:984: error: initializer element is not constant
snow.c:984: error: (near initialization for 'snowVTable.getVersion')
snow.c:985: error: initializer element is not constant
snow.c:985: error: (near initialization for 'snowVTable.getMetadata')
snow.c:986: warning: initialization from incompatible pointer type
snow.c:987: warning: initialization from incompatible pointer type
snow.c:988: warning: initialization from incompatible pointer type
snow.c:989: warning: initialization from incompatible pointer type
snow.c:990: warning: initialization from incompatible pointer type
snow.c:991: warning: initialization from incompatible pointer type
snow.c:992: warning: initialization from incompatible pointer type
snow.c:995: warning: initialization from incompatible pointer type
snow.c:996: warning: initialization from incompatible pointer type
snow.c:998: warning: excess elements in struct initializer
snow.c:998: warning: (near initialization for 'snowVTable')
snow.c:999: warning: excess elements in struct initializer
snow.c:999: warning: (near initialization for 'snowVTable')
snow.c:1000: warning: excess elements in struct initializer
snow.c:1000: warning: (near initialization for 'snowVTable')
snow.c:1001: warning: excess elements in struct initializer
snow.c:1001: warning: (near initialization for 'snowVTable')
snow.c:1003: warning: excess elements in struct initializer
snow.c:1003: warning: (near initialization for 'snowVTable')
make: *** [build/libsnow.lo] Error 1

```
and this is pretty much I'm trying to achieve in my Gutsy Gibbon: [http://www.youtube.com/watch?v=le9kYqIAtjY](http://www.youtube.com/watch?v=le9kYqIAtjY)

Is there any help you can give me (well not just me)... ???

Thank you very much for your help.

---

### Post by Sephoroth on 2007-11-13
I managed to get snow working a while back by getting a version off of the GIT (a pre-Compiz 0.62 release).  Also, Gutsy comes preinstalled with Compiz Fusion...

---

### Post by Espreon on 2007-11-13
Download the attached script into your home folder

The script is found in my second reply.

and type in the terminal:

```

sh snowscript.sh

```

I am assuming you have CCSM installed (the advance CF configuration tool) if you don't do the following:

1. Goto: System>Administration>Software Sources s

2. Check (if unchecked) Community-maintained Open Source software

3. Close the window and hit Reload

4. Enter this in the terminal:

```

sudo apt-get install compizconfig-settings-manager

```

Then goto System>Preferences>Advance Desktop Settings


Then enable Snow

Enjoy!

BTW the Snow plugin can also load any tiny resolution .png

---

### Post by GokuSoul on 2007-11-13
Hi I am new at this I downloaded the snow tar file what do I do next?:lolflag:

---

### Post by Ankara23 on 2007-11-14
There is an error in your script. The tar file that is downloaded is called '3d.tar.gz' not
'snow.tar.gz'

The line that reads:
```
tar -xvvzf 'snow.tar.gz'
```

should read:
```
tar -xvvzf '3d.tar.gz'
```

Once that is changed the script loads up the snow plugin perfectly. 
Thank you very much.

---

### Post by Espreon on 2007-11-14
Whoops, were all human and we all make mistakes, so I corrected my shell script and reuploaded it and it is attached to this reply.

And to Ankara:

Your welcome very much.

To sDoky: You should really use Compiz Fusion rather than the original, its getting more attention and stuff (so more developers are developing stuff for it), plus CF works better than Beryl and Compiz worked for me. 

There are lots of plugins for CF, like Atlantis (which puts a simple, yet delightful aquarium in the cube), Cover Flow window switching, Flip 3D (CF does it alot better than Vista does it) and lets not forget CCSM (which is better than the original Compiz configuration tool), but that does not mean that those plugins (except CCSM cause its not a plugin, its an application) can't be ported to Compiz (they probably can)

---

### Post by sDoky on 2007-11-14
> **Espreon said:**
> Whoops, were all human and we all make mistakes, so I corrected my shell script and reuploaded it and it is attached to this reply.

And to Ankara:

Your welcome very much.

To sDoky: You should really use Compiz Fusion rather than the original, its getting more attention and stuff (so more developers are developing stuff for it), plus CF works better than Beryl and Compiz worked for me. 

There are lots of plugins for CF, like Atlantis (which puts a simple, yet delightful aquarium in the cube), Cover Flow window switching, Flip 3D (CF does it alot better than Vista does it) and lets not forget CCSM (which is better than the original Compiz configuration tool), but that does not mean that those plugins (except CCSM cause its not a plugin, its an application) can't be ported to Compiz (they probably can)
Well thanks a lot, however I couldn't get that working. I have run your script, and it bursted the same error right at me. Couldn't that be problem with missing of any development package? Or what yould that be? And how can I get to know what type of compiz do I have? I mean Compiz/Compiz fusion. I know that I'm definetely not using Beryl or Emerald. I'm using ordinary system window decorator, just with additional colours and so on. Although I know I am using Compiz config settings manager (that's the CCSM, as I suppose)

---

### Post by dnns123 on 2007-11-14
Thanks a lot, works like a charm and I feel like it should be included in compiz's features.

@the person above me, just get the script and put it in your Home folder. I'm not sure about this, but , download the snow.tar.gz from the first post and do the same in step one. Just follow the rest of the instructions. If that doesnt work, extract the snow.tar.gz in the Home folder and try again.

Sorry, I'm still new to this and still messy

---

### Post by Rhubarb on 2007-11-14
If you want snow (and reindeer and christmas trees) on your desktop, you can install xsnow from the repositories.
```
sudo aptitude install xsnow
```
Then just run it from the terminal (or press Alt + F2), and type in "xsnow".

xsnow does not require compiz fusion to work, and it will work fine in compiz as well.

For those that want a watery desktop, but don't have compiz, they can install "xdesktopwaves" from the repositories.
You can also have penguins running around your desktop, install "xpenguins" from the repositories.

---

### Post by sDoky on 2007-11-14
> **dnns123 said:**
> Thanks a lot, works like a charm and I feel like it should be included in compiz's features.

@the person above me, just get the script and put it in your Home folder. I'm not sure about this, but , download the snow.tar.gz from the first post and do the same in step one. Just follow the rest of the instructions. If that doesnt work, extract the snow.tar.gz in the Home folder and try again.

Sorry, I'm still new to this and still messy

Well I thought of that too, it didn't work out... both things you said

---

### Post by Espreon on 2007-11-14
> **Rhubarb said:**
> If you want snow (and reindeer and christmas trees) on your desktop, you can install xsnow from the repositories.
```
sudo aptitude install xsnow
```
Then just run it from the terminal (or press Alt + F2), and type in "xsnow".

xsnow does not require compiz fusion to work, and it will work fine in compiz as well.

For those that want a watery desktop, but don't have compiz, they can install "xdesktopwaves" from the repositories.
You can also have penguins running around your desktop, install "xpenguins" from the repositories.

Thanks for metioning the xdesktopswaves thing, but xsnow makes CF runs really slow when you are using the cube.

---

### Post by GokuSoul on 2007-11-14
Hi i installed it but i can't change the texture it always stay to squares no matter how many images i put please help

---

### Post by Espreon on 2007-11-14
You need to enable the PNG image loader plugin, (it should be enabled by default). It can be enabled like other plugins in CCSM.

---

### Post by Ankara23 on 2007-11-15
Before I forget, this plugin works very nicely out of the box, HOWEVER it looks really cool if you include a "texture file"  

Open:
advanced desktop settings>>extras>>>snow>>>textures (tab)

Set the path to this little snowflake file that I have attached, (obviously save it to *your* harddrive first) :)
I think you will like the results...

---

### Post by dysolve on 2007-11-15
when i try and run the file it asks me to insert the gutsy release cadidate cd, which i do now have, i tried using the cd i installed gutsy from but it does not like that one.. why will it now download the file i need from repo's?

btw how do you stop xsnow if run from alt+f2?

---

### Post by Rhubarb on 2007-11-16
> **dysolve said:**
> when i try and run the file it asks me to insert the gutsy release cadidate cd, which i do now have, i tried using the cd i installed gutsy from but it does not like that one.. why will it now download the file i need from repo's?

btw how do you stop xsnow if run from alt+f2?

Go to System --> Administration --> Software Sources
Uncheck the box there that says "Cdrom with Ubuntu 710 'Gutsy Gibbon'"
Press close, then press reload.
You should be able to install anything from the repos without being hassled to insert your Ubuntu CD.

To stop xsnow running, press Alt + F2 again, and type in:
```
killall xsnow
```

---

