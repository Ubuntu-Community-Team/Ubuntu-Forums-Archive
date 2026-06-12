---
title: "Compiz Fusion Mini-How-to."
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by Fireblend on 2007-06-22
Hello! I decided to do something for society today and make a little how-to on what and how to install the new Compiz Fusion. These are the steps **[COLOR="Red"]I[/COLOR]** used to get it working. As you know, ymmv so be careful when following the following steps. Also, as mentioned on the sticky, this isn't for ubuntu newbies, although anyone who can follow directions can do it, really. Also, I'd advice to follow this only if you already have either beryl or compiz installed and using, so you know your graphic card is supported and you don't get the WSOD :p

Anyway, here it is:


[COLOR="Red"]**WHAT IS IT?**[/COLOR]

Well, I think the best way to explain what it is is by watching a video at youtube. Here's a few links:

[**Video 1**]("http://www.youtube.com/watch?v=D-2ZUAZoGOQ") / [**Video 2**]("http://www.youtube.com/watch?v=E4Fbk52Mk1w") / [**Video 3**]("http://www.youtube.com/watch?v=EytuaK04llw")

On the other hand, if you feel like a theoric definition, I guess we can use Wikipedia, which states:
> 
"Compiz Fusion is an extension of the Compiz compositing window manager for the X Window System. It was created from the remerging of Beryl into Compiz. It aims to port almost all of the features of Beryl to Compiz plugins, and continue to improve Compiz's core functionality.

There has yet to be an official release of Compiz Fusion, but preliminary packages are available."

So it basically means that unless you want to be stuck with your current beryl or compiz effects (and I'm not saying that's a bad option), you're gonna have to switch to Fusion sooner or later. Now, it's among Gutsy's goals to have this included, so if you are a patient human being you can wait. On the other hand, if you feel like upgrading now, follow these pretty simple instructions to get the current version.

Now, the current version is pretty stable (about as much as Beryl from my experience so far), so you don't have to worry about it being to unstable or anything but like any alpha/beta of anything, I can't guarantee you're gonna have the same results as me, so I'm not responsable for whatever might happen to your computer. Anyway, follow the instructions already:
[COLOR="Red"]
[B]
HOW TO INSTALL:[/B][/COLOR]

I'm gonna assume we're installing on a fresh install, so most of you (specially if you already have experience installing eyecandy) might already have some steps covered, like getting Trevino's repository, for example. But to help those who might not have it installed, I'm gonna cover all the steps.

**STEP 1:**

First, we'll be adding [Trevino's repositories]("http://3v1n0.tuxfamily.org/"), which is where we're getting our Fusion copy from. You can also find a lot of other eyecandy software from them, like Avant Window Nav. and Affinity. Anyway, first we go to System->Administration->Software sources and select the "Third-party sources" tab. You're gonna get a listbox and a button that says "add" below it. Click there and paste the following:

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Now do exactly the same and add this:

```
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Make sure that the added lines have appeared in the listbox. Done? Now close that window and open up the terminal. Once we're on the terminal, type the following to get the GPG Key for the repositories we just added (You can probably skip this step, but it's best to do this).

```
sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
```

Once entered, just wait. If for some reason it seems to be done but the "user@computer:$ " thing doesn't appear, close the terminal and open a new one or just start hitting random keys, for some reason, that happens to me so I thought I'd add that to avoid you waiting centuries for nothing to happen. Anyway, once that's done:

```
sudo apt-get update
```

You should notice the two lines we added in the update list. If they're there, so far so good.

**STEP 2:**

Now we'll install what we need so we can start playing with our new beautiful effects. I should note that most of the following comes from [http://forums.opencompositing.org/viewtopic.php?f=14&t=131](http://forums.opencompositing.org/viewtopic.php?f=14&t=131), so you might as well go there and continue.

Anyway, just type these on a terminal:
```

sudo apt-get remove compiz-core desktop-effects

sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde

sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!

sudo apt-get install compiz-fusion-*

```
If everything got removed / installed correctly, just press alt+f2 and type 
```

compiz --replace

```
If all went well, congratulations, you now have Compiz Fusion! You can configure it at the System->Preferences menu.


[COLOR="Red"]**TROUBLESHOOTING:**[/COLOR]

Alright, now to make this guide kinda useful, I'll add a couple of fixes that might help, feel free to add more in the comments or something.

***1. Windows are not moving as smoothly as they used to in Beryl / Compiz.***

This happened to me and it took me a while to fix. However, it shouldn't be too difficult. The current move plugin for some reason acts like that, so until they fix it we'll install a replacement plugin which is actually the old move plugin :p

[COLOR="Red"][UPDATE][/COLOR] Before doing the following, you have to install the following packages from the repos if you don't have them already:

[B]libxslt1.1 
libxslt1-dev 
compiz-dev
[/B]

1. Go here: [http://forum.compiz.org/viewtopic.php?t=1064](http://forum.compiz.org/viewtopic.php?t=1064)
2. Get the douge plugin
3. Untar it anywhere, preferably home so you don't have to navigate too mcuh on terminal.
4. Navigate to the new douge directory and type
```
make; make install
```
5. Restart Fusion
6. Go to the configurator and deselect move plugin, select douge.

That should do it, but if you see no change, restart the GUI (ctrl+alt+backspace) to make sure before making sure it's not working.

(Credit goes to Delfick from opencompositing forums for this one)
[B][I]
2. No window borders![/I][/B]

Well actually, I think there are a million possibilities for why this happens, but everytime it happens to me I can fix it with this command. Run it with alt+f2:

```
emerald --replace &
```


Well, that's all for now, hope it works out as well for you as it did for me, best of luck! :p

---

### Post by smartboyathome on 2007-06-22
You should start from metacity to avoid the no window border error. Also, I would suggest using compiz --replace, as if you are using your metacity theme in compiz, that will restore it, and not cause you to have to use Emerald.

---

### Post by Motoxrdude on 2007-06-22
Works with xgl.

---

### Post by KrazyPenguin on 2007-06-22
> wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

I believe this command needs to sudo in front of it so it looks like this:
sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

Doing the sudo apt-get udate gave me key errors:
But since I was already logged in the terminal as root I did the wget "part" again and it didn't stall, like the first time.  Then the update went perfect.

;-)

---

### Post by Vorian on 2007-06-22
you can also add the key by entering this in the terminal

> KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -

---

### Post by zero244 on 2007-06-22
Is this new version compiz fusion for fiesty only or can you install it on Edgy. If you can install it on edgy do you us the same repository.

---

### Post by superyounan1 on 2007-06-22
AWESOME! its working in my XGL session, whereas the old Compiz did not!

I noticed my wobbly windows were sluggish, so i tried compiling the bouge plugin, but got an error:

```
make; make install
[: 1: ==: unexpected operator
-e compiling : bouge.c -> build/libbouge.loPackage compiz was not found in the pkg-config search path.
Perhaps you should add the directory containing `compiz.pc'
to the PKG_CONFIG_PATH environment variable
No package 'compiz' found
bouge.c:32:20: error: compiz.h: No such file or directory
bouge.c:47: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveMetadata'
bouge.c:76: error: expected specifier-qualifier-list before 'HandleEventProc'
bouge.c:93: error: expected specifier-qualifier-list before 'PaintWindowProc'
bouge.c:120: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitiate'
bouge.c:222: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveTerminate'
bouge.c:264: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveGetYConstrainRegion'
bouge.c:353: error: expected ')' before '*' token
bouge.c:535: error: expected ')' before '*' token
bouge.c:676: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'movePaintWindow'
bouge.c:711: error: expected declaration specifiers or '...' before 'Display'
bouge.c: In function 'moveDisplayInitOptions':
bouge.c:713: error: 'CompOption' undeclared (first use in this function)
bouge.c:713: error: (Each undeclared identifier is reported only once
bouge.c:713: error: for each function it appears in.)
bouge.c:713: error: 'o' undeclared (first use in this function)
bouge.c:715: error: 'MoveDisplay' has no member named 'opt'
bouge.c:717: error: 'CompOptionTypeAction' undeclared (first use in this function)
bouge.c:718: error: 'moveInitiate' undeclared (first use in this function)
bouge.c:719: error: 'moveTerminate' undeclared (first use in this function)
bouge.c:720: error: 'FALSE' undeclared (first use in this function)
bouge.c:722: error: 'CompBindingTypeButton' undeclared (first use in this function)
bouge.c:723: error: 'CompActionStateInitButton' undeclared (first use in this function)
bouge.c:724: error: 'CompAltMask' undeclared (first use in this function)
bouge.c:725: error: 'Button1' undeclared (first use in this function)
bouge.c:726: error: 'CompBindingTypeKey' undeclared (first use in this function)
bouge.c:727: error: 'CompActionStateInitKey' undeclared (first use in this function)
bouge.c:730: warning: implicit declaration of function 'XKeysymToKeycode'
bouge.c:730: error: 'display' undeclared (first use in this function)
bouge.c:730: warning: implicit declaration of function 'XStringToKeysym'
bouge.c:732: error: 'MoveDisplay' has no member named 'opt'
bouge.c:734: error: 'CompOptionTypeInt' undeclared (first use in this function)
bouge.c:739: error: 'MoveDisplay' has no member named 'opt'
bouge.c:741: error: 'CompOptionTypeBool' undeclared (first use in this function)
bouge.c:744: error: 'MoveDisplay' has no member named 'opt'
bouge.c: At top level:
bouge.c:750: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
bouge.c:762: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveSetDisplayOption'
bouge.c:798: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitDisplay'
bouge.c:835: error: expected ')' before '*' token
bouge.c:848: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitScreen'
bouge.c:873: error: expected ')' before '*' token
bouge.c:891: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInit'
bouge.c:901: error: expected ')' before '*' token
bouge.c:908: error: expected ')' before '*' token
bouge.c:913: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
bouge.c:919: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveVTable'
bouge.c:941: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/libbouge.lo] Error 1
[: 1: ==: unexpected operator
-e compiling : bouge.c -> build/libbouge.loPackage compiz was not found in the pkg-config search path.
Perhaps you should add the directory containing `compiz.pc'
to the PKG_CONFIG_PATH environment variable
No package 'compiz' found
bouge.c:32:20: error: compiz.h: No such file or directory
bouge.c:47: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveMetadata'
bouge.c:76: error: expected specifier-qualifier-list before 'HandleEventProc'
bouge.c:93: error: expected specifier-qualifier-list before 'PaintWindowProc'
bouge.c:120: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitiate'
bouge.c:222: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveTerminate'
bouge.c:264: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveGetYConstrainRegion'
bouge.c:353: error: expected ')' before '*' token
bouge.c:535: error: expected ')' before '*' token
bouge.c:676: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'movePaintWindow'
bouge.c:711: error: expected declaration specifiers or '...' before 'Display'
bouge.c: In function 'moveDisplayInitOptions':
bouge.c:713: error: 'CompOption' undeclared (first use in this function)
bouge.c:713: error: (Each undeclared identifier is reported only once
bouge.c:713: error: for each function it appears in.)
bouge.c:713: error: 'o' undeclared (first use in this function)
bouge.c:715: error: 'MoveDisplay' has no member named 'opt'
bouge.c:717: error: 'CompOptionTypeAction' undeclared (first use in this function)
bouge.c:718: error: 'moveInitiate' undeclared (first use in this function)
bouge.c:719: error: 'moveTerminate' undeclared (first use in this function)
bouge.c:720: error: 'FALSE' undeclared (first use in this function)
bouge.c:722: error: 'CompBindingTypeButton' undeclared (first use in this function)
bouge.c:723: error: 'CompActionStateInitButton' undeclared (first use in this function)
bouge.c:724: error: 'CompAltMask' undeclared (first use in this function)
bouge.c:725: error: 'Button1' undeclared (first use in this function)
bouge.c:726: error: 'CompBindingTypeKey' undeclared (first use in this function)
bouge.c:727: error: 'CompActionStateInitKey' undeclared (first use in this function)
bouge.c:730: warning: implicit declaration of function 'XKeysymToKeycode'
bouge.c:730: error: 'display' undeclared (first use in this function)
bouge.c:730: warning: implicit declaration of function 'XStringToKeysym'
bouge.c:732: error: 'MoveDisplay' has no member named 'opt'
bouge.c:734: error: 'CompOptionTypeInt' undeclared (first use in this function)
bouge.c:739: error: 'MoveDisplay' has no member named 'opt'
bouge.c:741: error: 'CompOptionTypeBool' undeclared (first use in this function)
bouge.c:744: error: 'MoveDisplay' has no member named 'opt'
bouge.c: At top level:
bouge.c:750: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
bouge.c:762: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveSetDisplayOption'
bouge.c:798: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitDisplay'
bouge.c:835: error: expected ')' before '*' token
bouge.c:848: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitScreen'
bouge.c:873: error: expected ')' before '*' token
bouge.c:891: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInit'
bouge.c:901: error: expected ')' before '*' token
bouge.c:908: error: expected ')' before '*' token
bouge.c:913: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
bouge.c:919: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveVTable'
bouge.c:941: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/libbouge.lo] Error 1

```

---

### Post by Nezing on 2007-06-22
Also had a look at Compiz-Fusion here:

[http://news.softpedia.com/news/Beryl-Is-Dead-Long-Live-Compiz-Fusion-57881.shtml](http://news.softpedia.com/news/Beryl-Is-Dead-Long-Live-Compiz-Fusion-57881.shtml)

Some people say that "eye candy" should not sell the product alone,but on this evidence,it is a straight five.Woo hoo.
Sorry,I got carried away there. :)

It will also be pre-installed with Ubuntu 7.10 (Gutsy Gibbon) .

---

### Post by Stephen Howard on 2007-06-22
I just wish I didn't keep reading 'compositing' and 'composting'.

---

### Post by Stephen Howard on 2007-06-22
> sudo apt-get remove compiz-core desktop-effects

It says that its going to remove: compiz compiz-core compiz-extra compiz-gtk compiz-plugins desktop-effects  **ubuntu-desktop**

Should I be worried that its going to remove ubuntu-desktop?

---

### Post by mrdeeds2324 on 2007-06-22
Totally works! thank you very much!

---

### Post by janbockaert on 2007-06-22
> **Stephen Howard said:**
> It says that its going to remove: compiz compiz-core compiz-extra compiz-gtk compiz-plugins desktop-effects  **ubuntu-desktop**

Should I be worried that its going to remove ubuntu-desktop?

no, ubuntu-desktop is a meta package, removing one package from this meta-package, forces ubuntu-desktop to be removed (i 'm guessing desktop-effects is part of ubuntu-desktop). But every other package installed with ubuntu-desktop will still be installed.

---

### Post by Fireblend on 2007-06-22
> **superyounan1 said:**
> AWESOME! its working in my XGL session, whereas the old Compiz did not!

I noticed my wobbly windows were sluggish, so i tried compiling the bouge plugin, but got an error:

```
make; make install
[: 1: ==: unexpected operator
-e compiling : bouge.c -> build/libbouge.loPackage compiz was not found in the pkg-config search path.
Perhaps you should add the directory containing `compiz.pc'
to the PKG_CONFIG_PATH environment variable
No package 'compiz' found
bouge.c:32:20: error: compiz.h: No such file or directory
bouge.c:47: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveMetadata'
bouge.c:76: error: expected specifier-qualifier-list before 'HandleEventProc'
bouge.c:93: error: expected specifier-qualifier-list before 'PaintWindowProc'
bouge.c:120: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitiate'
bouge.c:222: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveTerminate'
bouge.c:264: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveGetYConstrainRegion'
bouge.c:353: error: expected ')' before '*' token
bouge.c:535: error: expected ')' before '*' token
bouge.c:676: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'movePaintWindow'
bouge.c:711: error: expected declaration specifiers or '...' before 'Display'
bouge.c: In function 'moveDisplayInitOptions':
bouge.c:713: error: 'CompOption' undeclared (first use in this function)
bouge.c:713: error: (Each undeclared identifier is reported only once
bouge.c:713: error: for each function it appears in.)
bouge.c:713: error: 'o' undeclared (first use in this function)
bouge.c:715: error: 'MoveDisplay' has no member named 'opt'
bouge.c:717: error: 'CompOptionTypeAction' undeclared (first use in this function)
bouge.c:718: error: 'moveInitiate' undeclared (first use in this function)
bouge.c:719: error: 'moveTerminate' undeclared (first use in this function)
bouge.c:720: error: 'FALSE' undeclared (first use in this function)
bouge.c:722: error: 'CompBindingTypeButton' undeclared (first use in this function)
bouge.c:723: error: 'CompActionStateInitButton' undeclared (first use in this function)
bouge.c:724: error: 'CompAltMask' undeclared (first use in this function)
bouge.c:725: error: 'Button1' undeclared (first use in this function)
bouge.c:726: error: 'CompBindingTypeKey' undeclared (first use in this function)
bouge.c:727: error: 'CompActionStateInitKey' undeclared (first use in this function)
bouge.c:730: warning: implicit declaration of function 'XKeysymToKeycode'
bouge.c:730: error: 'display' undeclared (first use in this function)
bouge.c:730: warning: implicit declaration of function 'XStringToKeysym'
bouge.c:732: error: 'MoveDisplay' has no member named 'opt'
bouge.c:734: error: 'CompOptionTypeInt' undeclared (first use in this function)
bouge.c:739: error: 'MoveDisplay' has no member named 'opt'
bouge.c:741: error: 'CompOptionTypeBool' undeclared (first use in this function)
bouge.c:744: error: 'MoveDisplay' has no member named 'opt'
bouge.c: At top level:
bouge.c:750: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
bouge.c:762: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveSetDisplayOption'
bouge.c:798: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitDisplay'
bouge.c:835: error: expected ')' before '*' token
bouge.c:848: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitScreen'
bouge.c:873: error: expected ')' before '*' token
bouge.c:891: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInit'
bouge.c:901: error: expected ')' before '*' token
bouge.c:908: error: expected ')' before '*' token
bouge.c:913: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
bouge.c:919: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveVTable'
bouge.c:941: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/libbouge.lo] Error 1
[: 1: ==: unexpected operator
-e compiling : bouge.c -> build/libbouge.loPackage compiz was not found in the pkg-config search path.
Perhaps you should add the directory containing `compiz.pc'
to the PKG_CONFIG_PATH environment variable
No package 'compiz' found
bouge.c:32:20: error: compiz.h: No such file or directory
bouge.c:47: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveMetadata'
bouge.c:76: error: expected specifier-qualifier-list before 'HandleEventProc'
bouge.c:93: error: expected specifier-qualifier-list before 'PaintWindowProc'
bouge.c:120: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitiate'
bouge.c:222: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveTerminate'
bouge.c:264: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveGetYConstrainRegion'
bouge.c:353: error: expected ')' before '*' token
bouge.c:535: error: expected ')' before '*' token
bouge.c:676: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'movePaintWindow'
bouge.c:711: error: expected declaration specifiers or '...' before 'Display'
bouge.c: In function 'moveDisplayInitOptions':
bouge.c:713: error: 'CompOption' undeclared (first use in this function)
bouge.c:713: error: (Each undeclared identifier is reported only once
bouge.c:713: error: for each function it appears in.)
bouge.c:713: error: 'o' undeclared (first use in this function)
bouge.c:715: error: 'MoveDisplay' has no member named 'opt'
bouge.c:717: error: 'CompOptionTypeAction' undeclared (first use in this function)
bouge.c:718: error: 'moveInitiate' undeclared (first use in this function)
bouge.c:719: error: 'moveTerminate' undeclared (first use in this function)
bouge.c:720: error: 'FALSE' undeclared (first use in this function)
bouge.c:722: error: 'CompBindingTypeButton' undeclared (first use in this function)
bouge.c:723: error: 'CompActionStateInitButton' undeclared (first use in this function)
bouge.c:724: error: 'CompAltMask' undeclared (first use in this function)
bouge.c:725: error: 'Button1' undeclared (first use in this function)
bouge.c:726: error: 'CompBindingTypeKey' undeclared (first use in this function)
bouge.c:727: error: 'CompActionStateInitKey' undeclared (first use in this function)
bouge.c:730: warning: implicit declaration of function 'XKeysymToKeycode'
bouge.c:730: error: 'display' undeclared (first use in this function)
bouge.c:730: warning: implicit declaration of function 'XStringToKeysym'
bouge.c:732: error: 'MoveDisplay' has no member named 'opt'
bouge.c:734: error: 'CompOptionTypeInt' undeclared (first use in this function)
bouge.c:739: error: 'MoveDisplay' has no member named 'opt'
bouge.c:741: error: 'CompOptionTypeBool' undeclared (first use in this function)
bouge.c:744: error: 'MoveDisplay' has no member named 'opt'
bouge.c: At top level:
bouge.c:750: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
bouge.c:762: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveSetDisplayOption'
bouge.c:798: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitDisplay'
bouge.c:835: error: expected ')' before '*' token
bouge.c:848: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitScreen'
bouge.c:873: error: expected ')' before '*' token
bouge.c:891: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInit'
bouge.c:901: error: expected ')' before '*' token
bouge.c:908: error: expected ')' before '*' token
bouge.c:913: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
bouge.c:919: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveVTable'
bouge.c:941: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/libbouge.lo] Error 1

```

Damn I'm sorry, I'm gonna update the main post now. WHat's missing is that you gotta have the following packages installed (you can get em from the repos).

[B]libxslt1.1 
libxslt1-dev 
compiz-dev
[/B]
Sorry! I'll even PM you to make sure you get the message :p

---

### Post by Vorian on 2007-06-22
> **Stephen Howard said:**
> 
Should I be worried that its going to remove ubuntu-desktop?

No

---

### Post by superyounan1 on 2007-06-22
> Damn I'm sorry, I'm gonna update the main post now. WHat's missing is that you gotta have the following packages installed (you can get em from the repos).

[B]libxslt1.1 
libxslt1-dev 
compiz-dev
[/B]
Sorry! I'll even PM you to make sure you get the message :p

Thanks! gonna try that.

Its running well, feels very stable. There are some basic things that I cant figure out yet, like how to change my window decorations. I'm gonna keep clicking around, its got to be in the nice new compiz-config manager somwhere.

Thanks again

---

### Post by Stephen Howard on 2007-06-22
> **janbockaert said:**
> no, ubuntu-desktop is a meta package, removing one package from this meta-package, forces ubuntu-desktop to be removed (i 'm guessing desktop-effects is part of ubuntu-desktop). But every other package installed with ubuntu-desktop will still be installed.

Thanks, I guessed as much, but wasn't sure.  I wish they'd mark meta packages so that its clear.

---

### Post by defishguy on 2007-06-22
I just successfully installed it on Feisty and after using it for the last fifteen minutes I have to admit that I'm very impressed.  Excellent work!

---

### Post by Fireblend on 2007-06-22
> **defishguy said:**
> I just successfully installed it on Feisty and after using it for the last fifteen minutes I have to admit that I'm very impressed.  Excellent work!

Thanks! It's great to know the guide's actually being of use :D Enjoy your new Fusion effects!

---

### Post by Vorian on 2007-06-22
Nice work Fireblend :)

---

### Post by nsegative on 2007-06-22
Hey could someone help me out a bit?
I have a laptop with a geforce 7400. I installed this package and everything went smoothly. However when I turned it on the borders would dissappear (I'm using the default theme human) and the emerald command I used did nothing but give me an error. So I looked around and found this:
[https://answers.launchpad.net/ubuntu/+question/5317](https://answers.launchpad.net/ubuntu/+question/5317)
It told me to do this
> 
Section "Device"
        Identifier "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver "nvidia"
        BusID "PCI:1:0:0"
EndSection

Add the following lines to it:

    Option "AddARGBVisuals" "True"
    Option "AddARGBGLXVisuals" "True"
    Option "NoLogo" "True"

So it now reads:

Section "Device"
        Identifier "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver "nvidia"
        BusID "PCI:1:0:0"
        Option "AddARGBVisuals" "True"
        Option "AddARGBGLXVisuals" "True"
        Option "NoLogo" "True"
EndSection
However this did not help and I still had borders. So I opened it again, and changed the depth to 24 and rebooted. Now compiz --replace fails to do anything. Any ideas how to fix the borders and run in 32 bit mode?

---

### Post by Vorian on 2007-06-22
did you use

alt+F2 and enter* **compiz --replace** *in the command line?

---

### Post by nsegative on 2007-06-22
> **Vorian said:**
> did you use

alt+F2 and enter* **compiz --replace** *in the command line?
Yep, it works in 16 depth but when I go to xorg.conf and change depth to 24 it doesnt load anymore (also I'm ok with 16 as long as my border comes back). If its something wrong with the theme can u suggest a dark theme that will work with it? Thanks (also terminal is just a white blank when I enable it in 16 bit with compiz-fusion on).

---

### Post by gslo on 2007-06-22
Installed on fresh xubuntu (no beryl, just nvidia drivers) and it seems to be running fine. Exept how can I start the compizconfig-settings-manager to enable 3d effects, cube, etc. There is no menu entry in xubuntu for this I cant figure uot the command to start it. Synaptic confirms that its installed.

Thanks

---

### Post by smartboyathome on 2007-06-22
to start the settings manager, type ccsm in a terminal

---

### Post by gslo on 2007-06-22
Thank you smart! I never thought to abbreviate.

---

### Post by Useff on 2007-06-22
This works great! Thanks a lot! I'm using a Radeon 9800 Pro with XGL.

A couple minor gripes:

1) The "super" key doesn't work. I made sure it was mapped to the win key in the keyboard preferences in GNOME.

**Edit: Fixed! I ran gnome-settings-daemon and now everything works. This also does the trick if your icon, control, or window border theme options aren't taking effect**

2) The only way I can change a theme in Emerald is if I change it in the theme manager, then run emerald --replace.

Can anyone help me out?

---

### Post by moevmie on 2007-06-22
Hey, I'm getting this message

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
  compiz: Depends: compiz-decorator
E: Broken packages

```

so it's not really working for me, anybody has any suggestions????

thanks..
m

EDIT: I GOT IT WORKING, I GUESS THE REPOSITORIES CHANGED...

---

### Post by nsegative on 2007-06-22
I'm still having no luck with the missing borders, anyone?

---

### Post by smartboyathome on 2007-06-22
I would suggest using 16 bit since it works.

---

### Post by saldie on 2007-06-22
Thanks for the how-to.
Everytime I restart my computer I have to start it manually.
How do I make it auto-start?

---

### Post by smartboyathome on 2007-06-22
System > Preferences > Session, then make a new entry using the command "compiz --replace" and enjoy!

---

### Post by Vorian on 2007-06-22
> **smartboyathome said:**
> System > Preferences > Session, then make a new entry using the command "compiz --replace" and enjoy!You may not want to do that as this is in development right now and can cause some head aches if it breaks.

---

### Post by saldie on 2007-06-22
Thanks for the reply, but what do I enter in the "command" part.

---

### Post by Vorian on 2007-06-22
alt+F2

---

### Post by smartboyathome on 2007-06-22
compiz --replace is what you enter in the command part.

---

### Post by saldie on 2007-06-22
that was easy enough, thanks again.

---

### Post by DraeLee on 2007-06-23
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
  compiz: Depends: compiz-decorator
E: Broken packages



I am having the same problem as the other gentleman.  I have been searching high and low and cannot find a solution.  I am using x86_64 feisty fawn.  I got beryl to work properly but I cannot get the compiz to work any help would be appreciated I have been stuck on this for hours

thx in advance

---

### Post by steveneddy on 2007-06-23
Compiz Fusion is COOL!

Nice effects. I like the reflections and the Tab Group plugin. 

Now THIS is how a modern desktop is supposed to be!

Very nice.

Hate the name - love the effects.

Thank you devs. Thank you David. Thank you all that are involved in this great project.

-SE

---

### Post by Joe_CoT on 2007-06-23
> **DraeLee said:**
> Reading package lists... Done
I am having the same problem as the other gentleman.  I have been searching high and low and cannot find a solution.  I am using x86_64 feisty fawn.  I got beryl to work properly but I cannot get the compiz to work any help would be appreciated I have been stuck on this for hours
thx in advance

Most probably they didn't package the 64 bit version correctly. Happens a lot. :( i'm in the same boat

---

### Post by gslo on 2007-06-23
Thank to all , working beautifully!

---

### Post by DraeLee on 2007-06-23
well if thats the case that really sucks then well I got beryl working
i really wanted to try out compiz fusion though

---

### Post by SendDerek on 2007-06-23
Just wanted to drop by and say thanks for taking the initiative to dive in and provide this how-to on these forums!

I tried it, but alas... it did not work for me.  I couldn't get any of the effects to work and my window borders weren't showing up.  Oh well... it won't be too much longer before Gutsy has all of the kinks worked out!  I can wait until then.

You were right though... if it doesn't work for you, it's a headache to get back to where you were before! lol.

---

### Post by vexorian on 2007-06-23
I had issues , but I just made a reboot and the effeCts worked! before the reboot Compiz--replaCe did nothing.

---

### Post by soro2005 on 2007-06-23
My friggin goodness! And I thought Beryl was great! Thanks a lot for the HowTo. I've been spending the last hour and a half spinning my cube with my eyes wide open and marveling at how my processor load graph doesn't even think about doing anything else than just flatlining! Incredible!

---

### Post by DShepherd on 2007-06-23
> 
I'm still having no luck with the missing borders, anyone?

I had to install the emerald packages from the Trevino's repository.. and that seemed to work worked

sudo apt-get install libemeraldengine0 emearld

> My friggin goodness! And I thought Beryl was great! Thanks a lot for the HowTo. I've been spending the last hour and a half spinning my cube with my eyes wide open and marveling at how my processor load graph doesn't even think about doing anything else than just flatlining! Incredible!

I still miss some things from beryl like the miniview plugin.. but i guess that will all come in time

---

### Post by nsegative on 2007-06-23
> **DShepherd said:**
> I had to install the emerald packages from the Trevino's repository.. and that seemed to work worked

sudo apt-get install libemeraldengine0 emearld



I still miss some things from beryl like the miniview plugin.. but i guess that will all come in time
This is what I get:
> sudo apt-get install libemeraldengine0 emearld
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libemeraldengine0 is already the newest version.
libemeraldengine0 set to manual installed.
E: Couldn't find package emearld
Could you list your steps after you installed compiz fusion including the needed emerald files? Thanks!

c

---

### Post by flankker on 2007-06-23
**nsegative**: u made a typo, its not "emearld" it is "emerald" :)

---

### Post by nsegative on 2007-06-23
> **flankker said:**
> **nsegative**: u made a typo, its not "emearld" it is "emerald" :)
Still the same results. If I do emerald --replace in terminal I get : wnck-warning **: unhandled action type (nil)
Oh and one more question, I set compiz --replace to boot in session and my desktop would fail to load ( i had to manually remove it in recovery console).

---

### Post by chrisrx on 2007-06-23
I can't find my most used feature from beryl which was rotating the cube with the scroll wheel when the pointer was near the edge of the screen.  Is it not included in compiz?

---

### Post by kystorms on 2007-06-23
how do we get to where we can change the themes?

I saw on another post this is what we need to have in our preferences -gcompizthemer
which i dont see, I have a green beryl crystal and the compizconfig settings manager, 

any help or tutorials?

thanks
Ha, never mind ... it is the green crystal to use LOL
does the themse set up the same as they do in beryl?

thanks

---

### Post by DraeLee on 2007-06-23
well since I got fed up with x86_64 not being supported on a lot of things I reinstalled using i386 version.  DId the install instructions here and it installed flawlessly :D  yessir.  And I must say it does look really really good.  When support for 64bit becomes a little bit more stable Ill use it instead.  I just get tired of forcing 64bit on 32bit apps.  I am fooling with this now thanks again for the guide simple and straight to the point.



What green crystal I dont see that??

---

### Post by kystorms on 2007-06-23
system>preferences>green crystal

is it in the wrong place or not supposed to be there/?
I would not be surprised, i always manage to screw something up!

:-)
also, in beryl you can make the skydome just by pointing to a graphic in a file, is the same true for this cube set up as well?

---

### Post by DraeLee on 2007-06-23
> **kystorms said:**
> system>preferences>green crystal

is it in the wrong place or not supposed to be there/?
I would not be surprised, i always manage to screw something up!

:-)
also, in beryl you can make the skydome just by pointing to a graphic in a file, is the same true for this cube set up as well?

Well i see the compiz settings manager but its not a green diamond for me.  as far as the skydome the only way I know to do it is ctrl+alt and move the mouse.

Also does anyone know what the super key is I have no clue on that one??

---

### Post by nsegative on 2007-06-23
One error I noticed: in gconf-editor the shadow_radius when you type in compiz --replace always turns to 9 and integer (where ti should be float). However if I type compiz --replace gconf I have borders but a lot of the effects are now missing and wont activate.

---

### Post by robio376 on 2007-06-23
Got everything working! But I don't have a theme manager except for the default one. How do I install the emerald theme manger. This is a clean install of Ubuntu with all updates. and just followed your instructions.

---

### Post by Fireblend on 2007-06-23
The green crystal is Emerald Settings Manager, which =/= Compiz Settings
THe super key is the "WIndows" key near the ctrl/alt keys.

Edit:

To Install emerald theme manager,

```
sudo apt-get install emerald emerald-themes
```

should work.

---

### Post by DraeLee on 2007-06-23
well dont I feel slooooow.  thank you for the reply now I can try something ;-)



Ok got a question though.  I installed the emerald theme manager and I clicked a theme that I like but it did not change anything.  Now in beryl I know you could just click the one you like and it would change it.  Is there a different path to this on fusion.??

---

### Post by flankker on 2007-06-23
(ignore, i fixed it)

---

### Post by yinglcs2 on 2007-06-23
If I already have beryl installed on my Ubuntu 7.0.4, what do I need to do to install compiz fusion?

---

### Post by llamakc on 2007-06-23
> **yinglcs2 said:**
> If I already have beryl installed on my Ubuntu 7.0.4, what do I need to do to install compiz fusion?

Follow the instructions on page 1 of this thread. Worked perfectly for me.

---

### Post by DraeLee on 2007-06-23
does anyone know how to get the themes to work properly??

---

### Post by maplekandalf on 2007-06-23
Hi,
I am currently a beryl user, but my knowledge of linux is limited. How would I remove beryl before starting this guide? (I have the svn)

---

### Post by DraeLee on 2007-06-23
i believe its sudo apt-get remove beryl 

i think

---

### Post by trinaryouroboros on 2007-06-23
I was hoping to compile my own how-to but you beat me to the punch. Not only have I utterly failed to get Compiz Fusion set up, but, I can't even install compiz itself!

I am running Beryl presently, happily, yet, I wanted to see the new Compiz Fusion.

When I follow instructions and get to sudo apt-get install compiz, I get the following:

```
ouroboros@w0-rm-h0-l3-ff:~$ sudo apt-get install compiz
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
  compiz: Depends: compiz-decorator but it is not installable
E: Broken packages
ouroboros@w0-rm-h0-l3-ff:~$ 
```

Been cracking at this for a couple days now with no luck.

I'm using 64-bit Feisty Fawn, any ideas?

I tried getting compiz-decorator-gtk and extracted the RPM...no dice!

I also tried getting the compiz deb file straight from tr3vin0s thing, no good, same odd "uninstallable" compiz-decorator.

:(

I've scoured the web, and am kinda surprised no one has got this error message before...maybe I'm just a damn fool here or something.

Edit: Beryl has to be removed first? Is that what's causing the compiz-decorator glitch??

---

### Post by Hawk__0 on 2007-06-23
I dont understand.. lol.. i did it all, is it supposed to run w/o beryl showing on my "system tray"?
I was running beryl, i exited after switching to metacity when i followed this tutorial.  i opened up beryl and it worked'n all.  none of the settings i configured in the compiz thinger worked though.  how do i open "compiz fusion" or is opening beryl supposed to be what i do? i downloaded some updates and stuff too..

---

### Post by Fireblend on 2007-06-23
> **Hawk__0 said:**
> I dont understand.. lol.. i did it all, is it supposed to run w/o beryl showing on my "system tray"?
I was running beryl, i exited after switching to metacity when i followed this tutorial.  i opened up beryl and it worked'n all.  none of the settings i configured in the compiz thinger worked though.  how do i open "compiz fusion" or is opening beryl supposed to be what i do? i downloaded some updates and stuff too..

No, beryl is something else, independent from fusion. there's no icon on the notifications bar for fusion. Close that and run compiz --replace with alt+f2, then it should work. To access to Fusion's settings, run ccsm on alt+f2 or Compiz Setting Manager under System->Preferences :p

---

### Post by v8YKxgHe on 2007-06-23
Hum, I can't get this to work. I currently run Beryl on AIGLX with an nVidia - however, after following your guide and doing compiz --replace the window manager flashes on an off, then back to metacity. 

If I do it in the terminal, I get this:

```
alex@alex-ubuntu:~$ compiz --replace
Adding plugin move (move)
Adding plugin wobbly (wobbly)
Adding plugin snow (snow)
Adding plugin inotify (inotify)
Adding plugin opacify (opacify)
Adding plugin regex (regex)
Adding plugin water (water)
Adding plugin fakeargb (fakeargb)
Adding plugin annotate (annotate)
Adding plugin scale (scale)
Adding plugin showdesktop (showdesktop)
Adding plugin tile (tile)
Adding plugin place (place)
Adding plugin neg (neg)
Adding plugin text (text)
Adding plugin switcher (switcher)
Adding plugin animation (animation)
Adding plugin winrules (winrules)
Adding plugin plane (plane)
Adding plugin cubereflex (cubereflex)
Adding plugin clone (clone)
Adding plugin bench (bench)
Adding plugin thumbnail (thumbnail)
Adding plugin ring (ring)
Adding plugin video (video)
Adding plugin trailfocus (trailfocus)
Adding plugin imgjpeg (imgjpeg)
Adding plugin mblur (mblur)
Adding plugin snap (snap)
Adding plugin svg (svg)
Adding plugin resizeinfo (resizeinfo)
Adding plugin resize (resize)
Adding plugin group (group)
Adding plugin crashhandler (crashhandler)
Adding plugin screenshot (screenshot)
Adding plugin scaleaddon (scaleaddon)
Adding plugin vpswitch (vpswitch)
Adding plugin fade (fade)
Adding plugin put (put)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin png (png)
Adding plugin decoration (decoration)
Adding core settings (General Options)
Adding plugin blur (blur)
Adding plugin dbus (dbus)
Adding plugin extrawm (extrawm)
Adding plugin splash (splash)
Adding plugin cube (cube)
Adding plugin rotate (rotate)
Adding plugin wall (wall)
Adding plugin fs (fs)
Adding plugin minimize (minimize)
Adding plugin glib (glib)
Adding plugin reflex (reflex)
Adding plugin zoom (zoom)
Adding plugin addhelper (addhelper)
Adding plugin expo (expo)
Backend     : gconf
Integration : true
Profile     : default
Initializing core options...done
Initializing move options...done
Initializing place options...done
Initializing resize options...done
/usr/bin/compiz: line 681: 12466 Segmentation fault      (core dumped) $@
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

---

### Post by v8YKxgHe on 2007-06-23
nevermind! Fixed! Beryl was conflicting with it, after removing beryl ( sudo apt-get remove --purge beryl emerald emerald-themes ) it all works!

---

### Post by dorath on 2007-06-23
I was also having problems with the window borders dissapearing.  What worked for me was to ctrl+alt+backspace, then alt+F2: compiz --replace

After that, it's worked like a charm!  Fun stuff :D

Kudos to the people behind this super-spiffy project!

---

### Post by Hawk__0 on 2007-06-23
I enabled skydome, animated it and put on an image.  the image is replaced by the default gradiant, and i removed the end caps... which are still there...?


also inside cube doesnt zoom like it used to :(

---

### Post by DraeLee on 2007-06-23
im fooling with the skydomes now and it only has the default Im not sure what I am doing wrong here any help???

---

### Post by bazooze28 on 2007-06-23
can someone please help me? im a noob at ubuntu

im going to try to install compiz fusion tonight because im not on my computer right now.  but i am having trouble with the 4 desktops/wokspaces in the bottom right hand corner of the screen.  When i first installed ubuntu, the workspaces worked fine.  then i installed beryl, had fun with it, and later removed it.  now the first workspace works fine.  but when i click in the second, third, or fourth workspace, i just see a blank scree.  all i see is my wallpaper, no toolbars on the top and bottom of the screen, and no mouse.  the only way i get back to the first desktop is using control-alt-left.  

Then if i go to the special effects option and put "disable cube" it works and i can go to all the workspaces.  however, i can not have different programs in each of the workspace.   Say, for example, i have firefox open in the first workspace, and i click on the 2nd, 3rd, or 4th, it is also in those workspace too. i just want it open in 1 workspace.

can someone tell me how go back to the default settings for the workspaces that came with ubuntu.  this way, when i try to install  compiz fusion tonight, it will have a better chance of working.

thanks in advance

---

### Post by cumanzor on 2007-06-23
Hi, I installed following this instructions and from the compcomm site. (Treviño's post)

Anyways, it doesn't work for me, segmentation fault :(

> manuel@desktop:~$ compiz --replace

(emerald:8652): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)' failed

(emerald:8652): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8652): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8652): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8652): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8652): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8652): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8652): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8652): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8652): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8652): Wnck-WARNING **: Unhandled action type (nil)
Adding plugin scale (scale)
Adding plugin extrawm (extrawm)
Adding plugin clone (clone)
Adding plugin scaleaddon (scaleaddon)
Adding plugin plane (plane)
Adding plugin thumbnail (thumbnail)
Adding plugin dbus (dbus)
Adding plugin mblur (mblur)
Adding plugin trailfocus (trailfocus)
Adding plugin video (video)
Adding plugin snap (snap)
Adding plugin bench (bench)
Adding plugin text (text)
Adding plugin neg (neg)
Adding plugin tile (tile)
Adding plugin firepaint (firepaint)
Adding plugin imgjpeg (imgjpeg)
Adding plugin crashhandler (crashhandler)
Adding plugin rotate (rotate)
Adding plugin wobbly (wobbly)
Adding plugin png (png)
Adding plugin splash (splash)
Adding plugin fakeargb (fakeargb)
Adding plugin resizeinfo (resizeinfo)
Adding plugin annotate (annotate)
Adding plugin snow (snow)
Adding plugin switcher (switcher)
Adding plugin addhelper (addhelper)
Adding plugin water (water)
Adding plugin fadedesktop (fadedesktop)
Adding plugin cube (cube)
Adding plugin move (move)
Adding plugin glib (glib)
Adding plugin regex (regex)
Adding plugin svg (svg)
Adding plugin reflex (reflex)
Adding plugin cubereflex (cubereflex)
Adding plugin fs (fs)
Adding plugin blur (blur)
Adding plugin group (group)
Adding plugin inotify (inotify)
Adding plugin minimize (minimize)
Adding plugin wall (wall)
Adding plugin showdesktop (showdesktop)
Adding plugin decoration (decoration)
Adding plugin resize (resize)
Adding plugin screenshot (screenshot)
Adding plugin expo (expo)
Adding plugin winrules (winrules)
Adding core settings (General Options)
Adding plugin put (put)
Adding plugin opacify (opacify)
Adding plugin place (place)
Adding plugin fade (fade)
Adding plugin zoom (zoom)
Adding plugin ring (ring)
Adding plugin animation (animation)
Adding plugin vpswitch (vpswitch)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing imgjpeg options...done
Initializing move options...done
Initializing svg options...done
Initializing minimize options...done
/usr/bin/compiz: line 681:  8852 Segmentation fault      (core dumped) $@
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


---

### Post by Voodooengine on 2007-06-23
I'm getting this error. :)

ravi@ravi:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

I followed your original post, and everything ran fine. I guess it just won't start.. I'm running a ATI x1600 so thats most likely why.

---

### Post by llamakc on 2007-06-23
Hey, what's the key-combo to get the Desktop Wall to work?

---

### Post by pedalwrench on 2007-06-23
> **llamakc said:**
> Hey, what's the key-combo to get the Desktop Wall to work?

usually ctrl+alt+ a arrow key 

by the way works good, intel I910 :p

edit:  i am lovin' the expo thing!!

By the way anyone know how to make the cube switch on the mouse scroll wheel?

---

### Post by Hawk__0 on 2007-06-23
"super key" for me thats the windows key. thats odd. lol.

ummm anybody else notice some of beryls effects are missing? maybe im retarded, but i cant find the pop up 3d windows, i cant zoom out from inside cube, and if i delete the end cap images from the settings, they still show up (i liek no end caps... transparent).

also, while rotating, its a lot different than beryl, i liked the way old beryl rotated.

---

### Post by Danman3459 on 2007-06-23
I got it to work by adding 

```
Option "AddARGBGLXVisuals" "True"
```

To the Section "Screen" part of Xorg.conf

Works great ...

P.S.  I got this from [http://ubuntuforums.org/archive/index.php/t-386025.html](http://ubuntuforums.org/archive/index.php/t-386025.html)

---

### Post by klato on 2007-06-23
Cool, got it working over here.  Thanks!

---

### Post by smartboyathome on 2007-06-23
There is a new version of Compiz Fusion in the repo that supports transparency. Just set the color of your caps and everything to completely transparent. Then it will appear to have no caps.

---

### Post by pt123 on 2007-06-23
Can this be installled while having Beryl installed (i.e I am not planning to run them together but switch). It is just that I have heard some of the features in Beryl have not been ported over like:
When using the scroll of the mouse on the desktop the cube doesn't rotate.
Also the snow efect ( I am a sucker for it)

---

### Post by Fireblend on 2007-06-23
> **pt123 said:**
> Can this be installled while having Beryl installed (i.e I am not planning to run them together but switch). It is just that I have heard some of the features in Beryl have not been ported over like:
When using the scroll of the mouse on the desktop the cube doesn't rotate.
Also the snow efect ( I am a sucker for it)

Yes, you can have them both without one interfering with the other.
Oh and there is a snow effect in Fusion :p

---

### Post by smartboyathome on 2007-06-23
you need to change these in the control panel. to get it, type (in a terminal) "ccsm" (without quotes)

---

### Post by sparq-l on 2007-06-23
I am also a n00b, but I seem to be getting held up very early in this process.  I'm unable to download the repositories.  

I'm getting a 404 on both of them.  

Anyone else having this issue, or have an suggestions on how to fix it?

---

### Post by DarkN00b on 2007-06-23
Everything worked fine here. My i855 graphics chipset isn't even breaking a sweat. :D Eat that, Vista.

The only issue I have is that I cannot set the bottom cap pic. I have my skydome and top cap working just fine, but that bottom cap just won't appear.

I **really** like the cube reflection and I know I would like the group window plugin if I could figure out how to get it to work. Also where's that dodge effect at? I likes it. :D

---

### Post by pt123 on 2007-06-23
> **Fireblend said:**
> Yes, you can have them both without one interfering with the other.
Oh and there is a snow effect in Fusion :p

Cool thanks so should I disable Beryl & Beryl-Manager from the Preferences->Sessions->Start up programs

before trying to install this?

---

### Post by Fireblend on 2007-06-23
> **pt123 said:**
> Cool thanks so should I disable Beryl & Beryl-Manager from the Preferences->Sessions->Start up programs

before trying to install this?

Well, I wouldn't change anything until I'm sure fusion works. Remove those and add the fusion commands if it works out.

---

### Post by Darganot on 2007-06-23
Personally, I was missing window boarders after following your walkthrough (I'm running the Linux Mint Cassandra, which had beryl pre-installed... I had the same problem with that I was hoping fusion would fix it).  Well, it didn't, and after trying several different things in this thread, here is what personally worked for me (with a GeForce 4):

> 
sudo apt-get remove --purge beryl emerald emerald-themes

edit xorg.conf (gnome)
> sudo gedit /etc/X11/xorg.conf
add this under section "screen":
> Option "AddARGBGLXVisuals" "True"

Also make sure to add an entry under sessions for "compiz --replace".  Now restart your system:

> sudo reboot

Once I had all these ducks in order I finally had my window boarders back plus neato effects.  I know what I'll be doing today...  

:popcorn:  Thanks  :D

---

### Post by Hawk__0 on 2007-06-23
I set it, but they still show white AND transparent depending on the angle.

anybody find (if in existence) the feature for 3d pop out windows?
i had it on beryl but i cant seem to find it in fusion

---

### Post by aldenhg on 2007-06-23
The link to the douge plugin is down due to a database error. Anyone have a mirror or a tarball they can thoss up for those of us who are a little late to the party?

---

### Post by milot on 2007-06-23
I have a problem when I run compiz --replace:

```

milot@QuickWhite:~$ compiz --replace
Adding plugin put (put)
Adding plugin png (png)
Adding plugin fs (fs)
Adding plugin wall (wall)
Adding plugin inotify (inotify)
Adding plugin vpswitch (vpswitch)
Adding plugin tile (tile)
Adding plugin opacify (opacify)
Adding plugin trailfocus (trailfocus)
Adding plugin bench (bench)
Adding plugin winrules (winrules)
Adding plugin zoom (zoom)
Adding plugin rotate (rotate)
Adding core settings (General Options)
Adding plugin fakeargb (fakeargb)
Adding plugin blur (blur)
Adding plugin water (water)
Adding plugin snap (snap)
Adding plugin neg (neg)
Adding plugin resize (resize)
Adding plugin fadedesktop (fadedesktop)
Adding plugin wobbly (wobbly)
Adding plugin dbus (dbus)
Adding plugin cubereflex (cubereflex)
Adding plugin splash (splash)
Adding plugin plane (plane)
Adding plugin scale (scale)
Adding plugin video (video)
Adding plugin showdesktop (showdesktop)
Adding plugin expo (expo)
Adding plugin annotate (annotate)
Adding plugin switcher (switcher)
Adding plugin fade (fade)
Adding plugin firepaint (firepaint)
Adding plugin glib (glib)
Adding plugin decoration (decoration)
Adding plugin minimize (minimize)
Adding plugin imgjpeg (imgjpeg)
Adding plugin text (text)
Adding plugin screenshot (screenshot)
Adding plugin addhelper (addhelper)
Adding plugin thumbnail (thumbnail)
Adding plugin crashhandler (crashhandler)
Adding plugin clone (clone)
Adding plugin move (move)
Adding plugin animation (animation)
Adding plugin group (group)
Adding plugin scaleaddon (scaleaddon)
Adding plugin reflex (reflex)
Adding plugin cube (cube)
Adding plugin svg (svg)
Adding plugin regex (regex)
Adding plugin place (place)
Adding plugin snow (snow)
Adding plugin mblur (mblur)
Adding plugin resizeinfo (resizeinfo)
Adding plugin extrawm (extrawm)
Adding plugin ring (ring)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing zoom options...done
Initializing resize options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

I removed beryl successfully but I cannot setup compiz.

---

### Post by Fireblend on 2007-06-23
> **milot said:**
> I have a problem when I run compiz --replace:

```

milot@QuickWhite:~$ compiz --replace
Adding plugin put (put)
Adding plugin png (png)
Adding plugin fs (fs)
Adding plugin wall (wall)
Adding plugin inotify (inotify)
Adding plugin vpswitch (vpswitch)
Adding plugin tile (tile)
Adding plugin opacify (opacify)
Adding plugin trailfocus (trailfocus)
Adding plugin bench (bench)
Adding plugin winrules (winrules)
Adding plugin zoom (zoom)
Adding plugin rotate (rotate)
Adding core settings (General Options)
Adding plugin fakeargb (fakeargb)
Adding plugin blur (blur)
Adding plugin water (water)
Adding plugin snap (snap)
Adding plugin neg (neg)
Adding plugin resize (resize)
Adding plugin fadedesktop (fadedesktop)
Adding plugin wobbly (wobbly)
Adding plugin dbus (dbus)
Adding plugin cubereflex (cubereflex)
Adding plugin splash (splash)
Adding plugin plane (plane)
Adding plugin scale (scale)
Adding plugin video (video)
Adding plugin showdesktop (showdesktop)
Adding plugin expo (expo)
Adding plugin annotate (annotate)
Adding plugin switcher (switcher)
Adding plugin fade (fade)
Adding plugin firepaint (firepaint)
Adding plugin glib (glib)
Adding plugin decoration (decoration)
Adding plugin minimize (minimize)
Adding plugin imgjpeg (imgjpeg)
Adding plugin text (text)
Adding plugin screenshot (screenshot)
Adding plugin addhelper (addhelper)
Adding plugin thumbnail (thumbnail)
Adding plugin crashhandler (crashhandler)
Adding plugin clone (clone)
Adding plugin move (move)
Adding plugin animation (animation)
Adding plugin group (group)
Adding plugin scaleaddon (scaleaddon)
Adding plugin reflex (reflex)
Adding plugin cube (cube)
Adding plugin svg (svg)
Adding plugin regex (regex)
Adding plugin place (place)
Adding plugin snow (snow)
Adding plugin mblur (mblur)
Adding plugin resizeinfo (resizeinfo)
Adding plugin extrawm (extrawm)
Adding plugin ring (ring)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing zoom options...done
Initializing resize options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

I removed beryl successfully but I cannot setup compiz.

Try adding ```
compiz --replace 
``` and  ```
emerald --replace & 
``` to the session startup commands and restart the gui with ctrl+alt+backspace.

---

### Post by devonj on 2007-06-23
Does anyone know why when compiz is install it pushes the screen over. When I run compiz the screen resizes and shifts everything to the left.

Computer: Thinkpad T40
Graphics Card: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02)

The white space on the side of the attached pic is the problem that am having

---

### Post by cumanzor on 2007-06-23
Compiz forums are down. Can anyone give me a link to the douge plug in?

---

### Post by Schnare on 2007-06-23
will compiz work on a radeon 9600 pro?

---

### Post by Vorian on 2007-06-23
> **Schnare said:**
> will compiz work on a radeon 9600 pro?Can you run Beryl or Compiz (desktop effects) now?

If so, yes :)

---

### Post by Schnare on 2007-06-23
The desktop effects that come with feisty work fine but i keep getting "Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system" when I try to do the compiz - replace thing

---

### Post by DrTsus on 2007-06-23
I'm very new to linux, so I'm probably doing soemthing dumb, but I've followed the directions, but I get this.... sorry it's long

```
brandon@brandons-computer:~$ sudo apt-get remove compiz-core desktop-effects sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde sudop apt-get install compizconfig-settings-manager # compizconfig-backends-* ?! sudo apt-get install compiz-fusion-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apt-get
brandon@brandons-computer:~$ sudo apt-get remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be REMOVED:
  compiz compiz-core compiz-gtk compiz-plugins desktop-effects
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 165kB of archives.
After unpacking 2372kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
brandon@brandons-computer:~$ 


```

---

### Post by DAaaMan64 on 2007-06-23
Another 64bit user with errors, would like some help! :)
```

daaaman64@govinda:~$ sudo apt-get install compiz compiz-kde
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator but it is not installable
E: Broken packages


```

---

### Post by smartboyathome on 2007-06-23
64 bit doesn't work yet... :-\

---

### Post by hellfried on 2007-06-23
i already have beryl installed in feisty. can i just follow the steps outlined if i want to upgrade to fusion?

---

### Post by Fireblend on 2007-06-23
> **hellfried said:**
> i already have beryl installed in feisty. can i just follow the steps outlined if i want to upgrade to fusion?

Yes.

---

### Post by Treviño on 2007-06-23
Many thanks for posting this guide with my packages ;)

I was thinking to include doodge in my repo too, or maybe manage it in move itself... I'll let you know!

I can't follow all the threads about this, so for latest news check always the opencompositing and compiz forum threads

---

### Post by Hawk__0 on 2007-06-23
> **DrTsus said:**
> I'm very new to linux, so I'm probably doing soemthing dumb, but I've followed the directions, but I get this.... sorry it's long

```
brandon@brandons-computer:~$ sudo apt-get remove compiz-core desktop-effects sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde sudop apt-get install compizconfig-settings-manager # compizconfig-backends-* ?! sudo apt-get install compiz-fusion-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apt-get
brandon@brandons-computer:~$ sudo apt-get remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be REMOVED:
  compiz compiz-core compiz-gtk compiz-plugins desktop-effects
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 165kB of archives.
After unpacking 2372kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
brandon@brandons-computer:~$ 


```


seems odd.  I've just always done lower case "y".  try that.


anybody know how to change the window manager back to gnome? im tryna play some games in cedega and i cant really cuz i get lots of weird problems haah.  in beryl i could jsut right click it and change it

---

### Post by hatchetjuggla on 2007-06-23
metacity --replace should do it

---

### Post by Hawk__0 on 2007-06-23
thanks :D it worked

---

### Post by Fireblend on 2007-06-23
> **Treviño said:**
> Many thanks for posting this guide with my packages ;)

I was thinking to include doodge in my repo too, or maybe manage it in move itself... I'll let you know!

I can't follow all the threads about this, so for latest news check always the opencompositing and compiz forum threads

Thanks! And also thanks to you for making Ubuntu users' life oh so much simpler! :D Who doesn't love your repo after all?
 
Including the douge plugin would be really good, I know of at least a couple of people that have encountered the same issue as I have and it's always great to have options that don't involve making and installing packages, after all this shouldn't be restricted to advanced users; who likes waiting ages for easy installing methods to fix things that can be fixed as easily as that? Although your repo does make things much simpler. Keep up the brilliant work!

---

### Post by michaelzap on 2007-06-23
Anyone else have problems getting cube cap images to show up? Better yet, anyone figure out how to fix it?

I just got a number of compiz and beryl updates via the update manager. they included some fusion plugins and whatnot. Wondering what this means...

Compiz and Emerald together are using less than 20MB of RAM on my system, and all this eye candy doesn't seem to slow down anything at all as far as I've noticed.

---

### Post by hellfried on 2007-06-23
> **Fireblend said:**
> Yes.

great stuff! i already have it up and running thanks to u! i have always had problems with changing the theme using emerald theme manager. after selecting the desired one, it does not take. in fusion is there another way of doing it?

---

### Post by Fireblend on 2007-06-23
> **hellfried said:**
> great stuff! i already have it up and running thanks to u! i have always had problems with changing the theme using emerald theme manager. after selecting the desired one, it does not take. in fusion is there another way of doing it?

Glad to know I was of help! You should try entering ```
emerald --replace &
``` to make the emerald theme reload (use alt+f2).

---

### Post by pt123 on 2007-06-23
Cool it is working fine but the snow plugin is just producing squares falling down.

Also beryl had a beryl manager which would let me switch back to metacity, for like watching videos or criticals tasks i.e. don't want the computer crash. 

Does compiz-fusion have something similar, like an icon in the notification area?

---

### Post by Fireblend on 2007-06-23
> **pt123 said:**
> Cool it is working fine but the snow plugin is just producing squares falling down.

Also beryl had a beryl manager which would let me switch back to metacity, for like watching videos or criticals tasks i.e. don't want the computer crash. 

Does compiz-fusion have something similar, like an icon in the notification area?

The different snow effect is because Beryl had a default picture for snow and is this one you have to set it up... And there's no notification area icon, but you can create a launcher with the command metacity --replace that basically does the same thing as selecting metacity in the Beryl icon :D

---

### Post by hellfried on 2007-06-23
> **Fireblend said:**
> Glad to know I was of help! You should try entering ```
emerald --replace &
``` to make the emerald theme reload (use alt+f2).

ok doing that actually changes the default theme but its a crap shoot. sometime nothing happens and on occasion the new theme takes but all the buttons disappear.

---

### Post by Hawk__0 on 2007-06-23
in 1 video i see the guy flip his windows around in 3d, where is that option?

---

### Post by redmonster13 on 2007-06-23
Ok, I got ubuntu installed on a dual boot setup and got compiz fusion installed. Keep in mind this is my first time at linux period. Now my problem is I can only see a small portion of the screen in the top left corner with compiz running. Everything is fine with metacity running though.

I can navigate to a small degree in compiz but it is maddening.

I also cant seem to change my display to 1280x1024 (yes that is how this problem started) I have tried undoing everything I did while trying to change my res.

any thoughts? (besides, this guy is a moron)

---

### Post by DarkN00b on 2007-06-23
Well, I figured out (finally) that dodge is an animation that can be applied to windows being focussed. I can be so slow sometimes. [img]http://img480.imageshack.us/img480/1662/doh4jw.gif[/img]

Now could someone point me to a page that explains the grouping/tabbing plugin? LOL

---

### Post by pt123 on 2007-06-23
[http://wiki.beryl-project.org/wiki/Window_Grouper](http://wiki.beryl-project.org/wiki/Window_Grouper)

Redmonster post a screenshot, amazed that you install Linux after seeing this.

---

### Post by redmonster13 on 2007-06-23
I will have to do a full reinstall, I tried to update the video driver and killed unbuntu. I will reinstall it in the morning and put compiz back on. This is just to cool to passup :)

If I end up in the same situation I will post some screenshots.

I think this time I will leave the damn video drivers alone and just deal with 1024x780 (or whatever it defaults to)

I wanted to mess with linux for a while now just never got around to it.

---

### Post by DarkN00b on 2007-06-24
> **pt123 said:**
> [http://wiki.beryl-project.org/wiki/Window_Grouper](http://wiki.beryl-project.org/wiki/Window_Grouper)

Redmonster post a screenshot, amazed that you install Linux after seeing this.

Yeehaw! Thank _you_. I got it working now. For those who want to know:

1. Click the first window you want to group and press Super+s.
2. Click on the second window you want to group and press Super+s.
3. Continue doing this until you have selected all the windows you want to group.
4. Press Super+g to group the windows. Now you can move/minimize/maximize the windows together.

Now it gets cool. For that nifty rotating window thing, you need to select your windows (with Super+s) and then **tab** them together by pressing Super+t. After you have done that, just hover your mouse cursor over the window titlebar and you'll see some thumbnails. Click them to rotate the window to the one you want.

---

### Post by ivesjd on 2007-06-24
I can't get compiz fusion to run on start-up correctly. When I reboot with "compiz --replace" in the session/start-up thing, none of my other default startup programs start, and nothing seems to work right. I installed Gnome Compiz Manager so I can switch back to Meta city, but nothing is started the right way. And if at anypoint I restart X, it just crashes and reboots. I don't want to have to boot into meta city everytime and then switch to fusion, but if thats what I have to do.... 
I was running beryl before this, I removed all of beryl (including emerald) because I was having problems with fusion(which it fixed). Then I rebooted and am stuck in this rut. Any help from anyone would be great.

---

### Post by pt123 on 2007-06-24
> **redmonster13 said:**
> I will have to do a full reinstall, I tried to update the video driver and killed unbuntu. I will reinstall it in the morning and put compiz back on. This is just to cool to passup :)
.

Noooooo :)

Your installation is not screwed it's just your xorg.conf (video configuration file) file is, when you probably tried to upgrade your video drivers. 

What video card do you have?

---

### Post by pt123 on 2007-06-24
> **ivesjd said:**
> I removed all of beryl (including emerald) because I was having problems with fusion(which it fixed). Then I rebooted and am stuck in this rut. Any help from anyone would be great.

Did you reinstall emerald because Compiz fusion needs it.

---

### Post by ivesjd on 2007-06-24
No, but it was working fine, but now Ubuntu won't boot at all. But Im gonna jump at it again tomorrow. Hopefully I can get it working without having to reinstall fiesty. I'll try installing emerald from the recovery boot. See if that helps.

---

### Post by BobCFC on 2007-06-24
> **DrTsus said:**
> I'm very new to linux, so I'm probably doing soemthing dumb, but I've followed the directions, but I get this.... sorry it's long

```
brandon@brandons-computer:~$ sudo apt-get remove compiz-core desktop-effects sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde sudop apt-get install compizconfig-settings-manager # compizconfig-backends-* ?! sudo apt-get install compiz-fusion-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apt-get
brandon@brandons-computer:~$ sudo apt-get remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be REMOVED:
  compiz compiz-core compiz-gtk compiz-plugins desktop-effects
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 165kB of archives.
After unpacking 2372kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
brandon@brandons-computer:~$ 


```


you are trying to do 4 commands at once on that big long line...  break it up in to separate pieces and do one after the other pressing enter each time:

sudo apt-get remove compiz-core desktop-effects 
sudo apt-get install compiz compiz-gnome 
sudo apt-get install compizconfig-settings-manager 
sudo apt-get install compiz-fusion-*

---

### Post by pt123 on 2007-06-24
> **ivesjd said:**
> No, but it was working fine, but now Ubuntu won't boot at all. But Im gonna jump at it again tomorrow. Hopefully I can get it working without having to reinstall fiesty. I'll try installing emerald from the recovery boot. See if that helps.

What do you mean by not boot up at which specific point does it stop.

---

### Post by ajmorris on 2007-06-24
the ones in the gutsy repos don't work properly:(.... and if i use the feisty ones from tuxfamily it doesn't work at all :( will, have to wait till the ones in gutsy are fixed.

---

### Post by trinaryouroboros on 2007-06-24
> **DAaaMan64 said:**
> Another 64bit user with errors, would like some help! :)
```

daaaman64@govinda:~$ sudo apt-get install compiz compiz-kde
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator but it is not installable
E: Broken packages


```

Are you freaking kidding me? C'mon, someone has a clue on this problem!

I uninstalled beryl and everything, this is day four now of troubleshooting compiz-decorator, what gives?

---

### Post by webosb on 2007-06-24
user@pc1:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
user@pc1:~$ 


can someone help?

---

### Post by Hawk__0 on 2007-06-24
> **ivesjd said:**
> I can't get compiz fusion to run on start-up correctly. When I reboot with "compiz --replace" in the session/start-up thing, none of my other default startup programs start, and nothing seems to work right. I installed Gnome Compiz Manager so I can switch back to Meta city, but nothing is started the right way. And if at anypoint I restart X, it just crashes and reboots. I don't want to have to boot into meta city everytime and then switch to fusion, but if thats what I have to do.... 
I was running beryl before this, I removed all of beryl (including emerald) because I was having problems with fusion(which it fixed). Then I rebooted and am stuck in this rut. Any help from anyone would be great.

Im not sure how you added your automatic launch on boot stuff, but ensure the stuff that is NOT booting is check marked in:  system->preferences->session

I didnt uninstall beryl, I just unchecked it from there so it wouldnt start, then i added 2 lines to load emerald and compiz fusion.:

add 1 line called Emerald (or what you prefer it to be called), and put this in the command part of the box:
```
emerald --replace &
```
then click ok and make a new one for compiz fusion:
```
compiz --replace
```

after that.. it should all work correctly, you may have to restart your computer, or input both of those commands by hitting alt+F2 (that will just load for the current session, not all.)

I went from beryl to this with no problems, i just pretty much switched my window manager to metacity, clocsed beryl, and then did that stuff up there.

good luck

---

### Post by tbob18 on 2007-06-24
Thanks, almost everything seems to be working perfectly.
The window boarders seemed to just randomly start working, they did not work when I first installed it, and they did not even show up under beryl.

Another problem that mysteriously disappeared is when I would try to go full screen with video the player would just crash (using totem, mplayer, smplayer or VLC).
I also had this problem in Beryl, but it seems to be working fine now.

One problem I am having is when I drag windows around it makes them semi-transparent using up too much CPU (~20%) compared to the 2-3% beryl uses.
Anyone have a link to the douge plugin? That forum seems to be down.

The last problem is when I open a lot of windows, some of them start turning black..
I also had this problem in Beryl, not sure what the cause is.

Has anyone got this working right on Dual screens yet? If I enable my second output, it either goes very, very slow, or just crashes.
This worked pretty good on beryl but ran a little slow.

Some specs (if that will help anything):
Athlon XP 3200+
Abit NF7-S 2.0
MSI Geforce 6600gt
2048x1536 @ 75hz
Ubuntu 7.04 (latest updates and all that)

The rest should not matter.

Thanks.

Edit: Oh yeah, does Compiz Fusion have 3D effects where the windows popped out of the cube? I liked that effect.

Edit: Another thing, when using the Zoom desktop I can't click or use anything, in beryl you could. Maybe this will get addressed later.

---

### Post by mustali on 2007-06-24
Thanks for the simple HOWTO. Everything worked perfectly after a reboot.

I'm blown away by the effects and the lean resource management.

Now I am gonna go back for a moment and enjoy the gentle snow fall on my desktop... :)

---

### Post by buttons on 2007-06-24
Still missing the link to the bouge plugin (hate those jerky wobbly windows!)

Anyone post up a copy?

EDIT: Nevermind.  Current bouge plugin is [here]("http://hibbert.univ-lille3.fr/~cbellegarde/Compiz/bouge.tar.gz").

---

### Post by ivesjd on 2007-06-24
As of right now I dont get a desktop. It boots to the login screen, and then I can login. But once it starts loading the screen goes black with only my cursor.

---

### Post by CheeseEatingBulldog on 2007-06-24
I used google to get the cache of that page, the links to the plugins are:

[http://hibbert.univ-lille3.fr/~cbellegarde/Compiz/bouge.tar.gz]("http://hibbert.univ-lille3.fr/~cbellegarde/Compiz/bouge.tar.gz")
[http://hibbert.univ-lille3.fr/~cbellegarde/Compiz/resize.tar.gz]("http://hibbert.univ-lille3.fr/~cbellegarde/Compiz/resize.tar.gz")

---

### Post by DrTsus on 2007-06-24
How do I start emerald at startup. When I type emerald --replace & in the terminal I get errors, so I don't want to get errors on startup if I put it in sessions like that. It does work in the Alt + F2 thing.

---

### Post by ivesjd on 2007-06-24
Okay, I can boot and and get a normal login screen, then the ubuntu loading thing comes up, and  it goes to a black screen with my cursor. Then restart X and it loads, but I get an error saying "I've detected a panel already running and will now exit" so I dont get my top and bottom panels. (With the clock etc.) Im at a loss of what to do.

---

### Post by DraeLee on 2007-06-24
Hmmm got a question.  oddly enough emerald --replace & has my tool bars showing up which means i can choose different emerald themes which is great right?,,,,,.,

If I close the terminal then my bars disappear.  Now I tested this by first checking my /etc/X11/xorg.conf to make sure that the changes I needed to do were there to begin with for disappearing bars and they were.  So then I entered in the command again (emerald --replace &) to reload it and it showed up.  as long as i minimize that terminal and keep it open my emerald themes show up.  Has anyone else had this dilema??

---

### Post by Jason.TJ.Johnson on 2007-06-24
> **DShepherd said:**
> I had to install the emerald packages from the Trevino's repository.. and that seemed to work worked

sudo apt-get install libemeraldengine0 emearld



I still miss some things from beryl like the miniview plugin.. but i guess that will all come in time

The window manager trick worked perfectly for me. Now i have borders on my windows.

One correction for anyone copying and pasting.
Emerald is spelled wrong ( a typo I'm sure )

So the command you want to post is:
```

sudo apt-get install libemeraldengine0 emerald

```

---

### Post by DarkN00b on 2007-06-24
> **DraeLee said:**
> Hmmm got a question.  oddly enough emerald --replace & has my tool bars showing up which means i can choose different emerald themes which is great right?,,,,,.,

If I close the terminal then my bars disappear.  Now I tested this by first checking my /etc/X11/xorg.conf to make sure that the changes I needed to do were there to begin with for disappearing bars and they were.  So then I entered in the command again (emerald --replace &) to reload it and it showed up.  as long as i minimize that terminal and keep it open my emerald themes show up.  Has anyone else had this dilema??

That's because whatever you start in a terminal window is automatically terminated when you close that terminal. Use Alt+F2, enter emerald --replace & then hit enter. Your bars will remain.

---

### Post by Jason.TJ.Johnson on 2007-06-24
> **DraeLee said:**
> Hmmm got a question.  oddly enough emerald --replace & has my tool bars showing up which means i can choose different emerald themes which is great right?,,,,,.,

If I close the terminal then my bars disappear.  Now I tested this by first checking my /etc/X11/xorg.conf to make sure that the changes I needed to do were there to begin with for disappearing bars and they were.  So then I entered in the command again (emerald --replace &) to reload it and it showed up.  as long as i minimize that terminal and keep it open my emerald themes show up.  Has anyone else had this dilema??

Hold on wait?
Are you typing the command into the terminal? If so, I believe closing the terminal causing the application to close..

You should just try typing it (emerald --replace &) into the run prompt.

You can pull up the run prompt by pressing ALT+F2.

---

### Post by Jason.TJ.Johnson on 2007-06-24
> **DarkN00b said:**
> That's because whatever you start in a terminal window is automatically terminated when you close that terminal. Use Alt+F2, enter emerald --replace & then hit enter. Your bars will remain.

Damn beaten!
:)

---

### Post by spmsrh on 2007-06-24
I had a bit of a struggle trying to fix transparency in fullscreen from default 89 to 100, finally managed to do that by adding the rule 

state=fullscreen 
100

---

### Post by DraeLee on 2007-06-24
lol ok thank you that did work i forgot about the alt+f2


oops forgot :D  how do u ungroup the windows, I mean like revert back to normal (just wanted to know).

---

### Post by ivesjd on 2007-06-24
Okay, so I sorta got it working. But I have to restart X every boot since it comes up to a black screen with just the cursor. But its getting more consisteint :P

---

### Post by andrewsomething on 2007-06-24
If any one is getting this error when trying Compiz-Fusion 

```
    /usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319
```


And Emerald wouldn't run with Compiz-Fusion (ie no window decorations). I might have the solution.

 I solved the problem on my end, and now do not receive this error. Emerald and Compiz are playing nicely together.

If you are having the same problem, check what version of Emerald you are running. If were getting Emerald and Beryl from the Beryl Project repo, the version of Emerald you have will not work with Compiz-Fusion from Trevino's repo. You should use the version of Emerald in his repo. That fixed all my problems.

The easiest way to switch is probably to just delete the beryl repo from your source list altogether. That doesn't mean that you need to get rid of Beryl. Just upgrade both Emerald and Beryl using Trevino's repo. I can now switch back and forth from Beryl and Compiz-Fusion with ease, and Emerald gives me no more problems.

Hopefully that works for others getting that same error. I haven't heard this fix from else yet, but it works for me.

---

### Post by ivesjd on 2007-06-24
Is anyone else unable to put in new keyboard short cuts? Im trying to enable the ring switcher plugin and it is not letting me switch the keys to (Alt+Tab) and (Alt+Shift+Tab). I disabled these keys from all the other shortcuts I could find.

---

### Post by gkiller on 2007-06-24
> **redmonster13 said:**
> I will have to do a full reinstall, I tried to update the video driver and killed unbuntu. I will reinstall it in the morning and put compiz back on. This is just to cool to passup :)

If I end up in the same situation I will post some screenshots.

I think this time I will leave the damn video drivers alone and just deal with 1024x780 (or whatever it defaults to)

I wanted to mess with linux for a while now just never got around to it.
If you have an Nvidia card, you have to enable the proprietary driver from System > Administration > Restricted Driver Manager. If your xorg.conf got messed up, you can just press Alt-F2 and type "nvidia-settings". There you can setup a basic working xorg.conf again, without having to reinstall anything.

> **trinaryouroboros said:**
> Are you freaking kidding me? C'mon, someone has a clue on this problem!

I uninstalled beryl and everything, this is day four now of troubleshooting compiz-decorator, what gives?There is no working 64bit version of compiz/fuision in Treviños repository (yet?). I believe that is the cause of your problem.

---

### Post by gkiller on 2007-06-24
> **ivesjd said:**
> Is anyone else unable to put in new keyboard short cuts? Im trying to enable the ring switcher plugin and it is not letting me switch the keys to (Alt+Tab) and (Alt+Shift+Tab). I disabled these keys from all the other shortcuts I could find.
Just double-click on the action name and then type the hotkeys manually, eg "<Alt><Shift>Tab". The other special keys are <Control> and <Super>.

---

### Post by nonameguy on 2007-06-24
Removed my post, solved my own problem.  Great tutorial, easy to work with and WOW compiz fusion is a lot more optimized than beryl.  Great stuff!

---

### Post by DarkN00b on 2007-06-24
> **DraeLee said:**
> lol ok thank you that did work i forgot about the alt+f2


oops forgot :D  how do u ungroup the windows, I mean like revert back to normal (just wanted to know).

Select the group of windows you want to ungroup and press Super+u.

---

### Post by DraeLee on 2007-06-24
ty very much sir

---

### Post by ivesjd on 2007-06-24
> **gkiller said:**
> Just double-click on the action name and then type the hotkeys manually, eg "<Alt><Shift>Tab". The other special keys are <Control> and <Super>.

No, It works differntly, you have to do the keyboard shortcut you want. I can do Alt+` but I cant do alt tab like I want. Which is a standerd for window switching.

My other problems is now figured out at least. I can't boot with ```
compiz --replace -c emerald &
``` or ```
compiz --replace
emerald --replace 
``` 
But I can boot into metacity and then run the commands and get compiz to work. Any Ideas?

---

### Post by gkiller on 2007-06-24
> **ivesjd said:**
> No, It works differntly, you have to do the keyboard shortcut you want. I can do Alt+` but I cant do alt tab like I want. Which is a standerd for window switching.You can do it both ways, just try it. Double-click on the *name* of the action, not on any of the other columns.

I remember having the same problem for some plugins but not for all... apparently a bug.

---

### Post by nonameguy on 2007-06-24
I'm noticing everything is fast except for scroll bars.. is this a known issue, any fix?

---

### Post by ticopelp on 2007-06-24
It took quite a bit of tweaking, but I got this working. It looks amazing. I was convinced I would be sticking to Beryl for some time, but now I'm not so sure.

Thanks!

---

### Post by llamakc on 2007-06-24
I just figured out grouping. it is really sweet.

Super+S on the windows you want to select for grouping, Super+G to group them, then try Super+left/right keys. Sweet.

---

### Post by bigken on 2007-06-24
Worked for me did have the window boarder issue 

I run sudo apttitude install emerald 

this seemed to fix it 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=36350&stc=1&d=1182713322[/IMG]

---

### Post by Hawk__0 on 2007-06-24
> **ivesjd said:**
> No, It works differntly, you have to do the keyboard shortcut you want. I can do Alt+` but I cant do alt tab like I want. Which is a standerd for window switching.

My other problems is now figured out at least. I can't boot with ```
compiz --replace -c emerald &
``` or ```
compiz --replace
emerald --replace 
``` 
But I can boot into metacity and then run the commands and get compiz to work. Any Ideas?

What ive done is go to system->preferences->session
then you can add both lines of code there.  i made mine separate, including the following:
```
compiz --replace
```
```
emerald --replace &
```

---

### Post by digital_exhaust on 2007-06-24
Sorry, I'm sure that this has been asked and answered a dozen times at the least... but I've got a Radeon RV100 QY [Radeon 7000/VE] agp card, and I can run Beryl just fine.... so I should be able to run Fusion, correct?

---

### Post by Hawk__0 on 2007-06-24
im not sure if you can with a radeon card, my friend had lots of trouble with his ati card.

---

### Post by llamakc on 2007-06-24
I'm running Compiz-Fusion with zero problems on an ATI card. I'm NOT using fglrx, and using the 'radeon' driver and AIGLX.

---

### Post by ivesjd on 2007-06-24
> **gkiller said:**
> You can do it both ways, just try it. Double-click on the *name* of the action, not on any of the other columns.

I remember having the same problem for some plugins but not for all... apparently a bug.

Ya, that worked, I never though to click on the name itself. 

As for trying to get it to boot as different entrys in the startup, I've tried that as well. I've also tried adding it to rc.local (startup script) and all have failed. So Im just gonna leave it for now. It boots okay into metacity. Although I can see it switch the screen on and off a few times, and then I can just switch it. Not the best, but it works. Ive got pretty much everything working how I want. Other then not being able to replace the bottom cap. But all in all, I like it better then Beryl. Thanks everyone for helping me out. And thanks for the great how-to. :)

---

### Post by DrTsus on 2007-06-24
It seems very buggy. My mouse is bouncing all over the place. Menus will unexpectantly open. I'll be moving my mouse on the desktop and the highlight rectangle will form. The mouse will just move across screen. While I'm typing it will unselect the window. I've head each of those errors just while typing this. Help!

---

### Post by redmonster13 on 2007-06-24
I was having problems, this being the first time I have installed linux, but after a few reinstalls and graphics driver problems I have Compiz Fusion running. Funny thing, I took it step by step and followed the instructions and everything works perfectly.

Thanks for the tutorial.

---

### Post by ivesjd on 2007-06-24
> **DrTsus said:**
> It seems very buggy. My mouse is bouncing all over the place. Menus will unexpectantly open. I'll be moving my mouse on the desktop and the highlight rectangle will form. The mouse will just move across screen. While I'm typing it will unselect the window. I've head each of those errors just while typing this. Help!
Are you running Ubuntu on a laptop? It sounds like your wrists are hitting the trackpad while typing. Try this thread. [http://ubuntuforums.org/showthread.php?t=483217](http://ubuntuforums.org/showthread.php?t=483217)

---

### Post by digital_exhaust on 2007-06-24
Wow... got it running and..well, yeah..wow. 

I really like this, very cool, very smooth and stable (so far;)).. so much more than Beryl... 

Thanks a lot for the tutorial, worked perfect.. on my second try, after I borked my install because I wasn't paying enough attention... but the second time around it all went very well.. Thanks again!!!

---

### Post by hydroPWNic on 2007-06-24
The tutorial mostly worked for me, nice job!  

    I just have one question, and believe me I ask for help only as a last resort :(

I'm trying to get that bouge plugin installed because moving my windows is indeed laggy.  I follow the usual procedure for installing a 'tar.gz', i change directories, i DONT './configure' because theres no configuration file, but when go to 'MAKE' the file i get this as an output:

```
jared@DOWNSTAIRS:~/bouge$ make; make install
[: 1: ==: unexpected operator
make: Nothing to be done for `all'.
[: 1: ==: unexpected operator
install   : /home/jared/.compiz/plugins/libbouge.so.so-e

```

no idea what to do, i googled for literally 2.5 hours.  Im hoping one of yous can help me. :)

and by the way i've installed those three packages mentioned earlier: 

libxslt1.1
libxslt1-dev
compiz-dev

---

### Post by DrTsus on 2007-06-24
I realized what it was. I had a wireless mouse that broke on my desk upside down so whenever the desk moved it probably fidgetted. And since it was upside down it kept clicking. I took out the batteries and everything runs FANTASTICALLY. Works much better then Beryl. No actual freezes, a few hiccups, but it works in no time.

---

### Post by ivesjd on 2007-06-24
Two questions.
1. Downloaded the bouge plugin, but have no idea what to do after I untar it. 
2. What does the & sign do in emerald --replace &?

---

### Post by brandon moore on 2007-06-24
Anyone else having problems getting compiz-fusion-* to install? I keep getting this:

> E: Couldn't find package compiz-fusion-*

---

### Post by llamakc on 2007-06-24
> **brandon moore said:**
> Anyone else having problems getting compiz-fusion-* to install? I keep getting this:

No, show your /etc/apt/sources.list

---

### Post by brandon moore on 2007-06-24
here's what i have...

no errors come up with a sudo apt-get update, either...


> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

---

### Post by bazooze28 on 2007-06-24
Has anyone got the skydome working.  I tried about many pictures and downloaded some from gnome-look.org and none of them worked.  if some got them working, please let me know how

---

### Post by FluffyBunny on 2007-06-24
> **bazooze28 said:**
> Has anyone got the skydome working.  I tried about many pictures and downloaded some from gnome-look.org and none of them worked.  if some got them working, please let me know how

I just updated my compiz fusion a few minutes ago and I didn't have any trouble getting the skydome to work. I just used the same skydome that I used with beryl and it worked great, and unlike beryl it doesn't seem to care about the size of the image.

---

### Post by Fireblend on 2007-06-24
> **bazooze28 said:**
> Has anyone got the skydome working.  I tried about many pictures and downloaded some from gnome-look.org and none of them worked.  if some got them working, please let me know how

The images have to be powers of two, for example 1024x1024, 2048x2048...

---

### Post by tribaal on 2007-06-25
> **chrisrx said:**
> I can't find my most used feature from beryl which was rotating the cube with the scroll wheel when the pointer was near the edge of the screen.  Is it not included in compiz?

Can't find it either... I miss this feature a lot. Did anybody find how to make it work the way it used to in Beryl? This is really a show blocker for me (although I love the new looks :) ).
Also, I can't seem to be able to reassign which screen edge does what (I like to have "exposé" as the bottom screen edge action).

Help?

Thanks :)

- trib'

---

### Post by Dark Star on 2007-06-25
I saw shortcuts of Fusion.. there is written SUper.. btw which is Super key :S

---

### Post by Vorian on 2007-06-25
> **Dark Star said:**
> I saw shortcuts of Fusion.. there is written SUper.. btw which is Super key :S
Your windows key

---

### Post by mahasmb on 2007-06-25
I get stuck here @[COLOR="Red"] sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!
[/COLOR]
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="#ff0000"]E: Couldn't find package compizconfig-settings-manager[/COLOR]
```


Here's my whole upgrade process
```
maha@maha-laptop:~$ sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
--09:25:37--  http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,180 (4.1K) [text/plain]

100%[===============================================================================================>] 4,180          5.69K/s             

09:25:38 (5.69 KB/s) - `-' saved [4180/4180]

OK
maha@maha-laptop:~$ sudo apt-get update
Err http://beryl-mirror.lupine.me.uk feisty Release.gpg
  Could not resolve 'beryl-mirror.lupine.me.uk'
Err http://beryl-mirror.lupine.me.uk feisty/all Translation-en_CA                                                                         
  Could not resolve 'beryl-mirror.lupine.me.uk'
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]                                                                       
Ign http://security.ubuntu.com feisty-security/main Translation-en_CA                                                                     
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_CA                                                               
Get:2 http://download.tuxfamily.org feisty Release.gpg [189B]                                                                             
Ign http://download.tuxfamily.org feisty/beryl-svn Translation-en_CA                                                                      
Ign http://download.tuxfamily.org feisty/eyecandy Translation-en_CA                                                                       
Ign http://beryl-mirror.lupine.me.uk feisty Release                                                                                       
Hit http://download.tuxfamily.org feisty Release                                                                                          
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_CA                                                               
Hit http://security.ubuntu.com feisty-security Release                                                                                    
Hit http://security.ubuntu.com feisty-security/main Packages                                                                              
Hit http://security.ubuntu.com feisty-security/restricted Packages                                                    
Hit http://security.ubuntu.com feisty-security/main Sources                                                                               
Hit http://security.ubuntu.com feisty-security/restricted Sources                                                                         
Hit http://security.ubuntu.com feisty-security/multiverse Packages                                                                        
Get:3 http://archive.ubuntu.com feisty Release.gpg [191B]                                                                                 
Ign http://archive.ubuntu.com feisty/universe Translation-en_CA                                                       
Ign http://archive.ubuntu.com feisty/main Translation-en_CA                                              
Ign http://archive.ubuntu.com feisty/restricted Translation-en_CA                                        
Hit http://archive.ubuntu.com feisty Release                                                             
Hit http://archive.ubuntu.com feisty/universe Packages                                                   
Hit http://archive.ubuntu.com feisty/main Packages                                 
Hit http://archive.ubuntu.com feisty/restricted Packages                           
Ign http://beryl-mirror.lupine.me.uk feisty/all Packages                                            
Err http://beryl-mirror.lupine.me.uk feisty/all Packages                                            
  Could not resolve 'beryl-mirror.lupine.me.uk'
Get:4 http://ca.archive.ubuntu.com feisty Release.gpg [191B]                                                                              
Ign http://ca.archive.ubuntu.com feisty/multiverse Translation-en_CA                                                                      
Get:5 http://ca.archive.ubuntu.com feisty-updates Release.gpg [191B]                                                                      
Ign http://ca.archive.ubuntu.com feisty-updates/main Translation-en_CA                                                                    
Ign http://ca.archive.ubuntu.com feisty-updates/restricted Translation-en_CA                                                              
Ign http://ca.archive.ubuntu.com feisty-updates/multiverse Translation-en_CA                                                              
Hit http://ca.archive.ubuntu.com feisty Release                                                                                           
Hit http://ca.archive.ubuntu.com feisty-updates Release                                                                                   
Hit http://ca.archive.ubuntu.com feisty/main Sources                                                                                      
Hit http://ca.archive.ubuntu.com feisty/restricted Sources                                                                                
Hit http://ca.archive.ubuntu.com feisty/multiverse Packages                                                                               
Hit http://ca.archive.ubuntu.com feisty-updates/main Packages                                                                             
Hit http://ca.archive.ubuntu.com feisty-updates/restricted Packages                                                                       
Hit http://ca.archive.ubuntu.com feisty-updates/main Sources                                                                              
Hit http://ca.archive.ubuntu.com feisty-updates/restricted Sources                                                                        
Hit http://ca.archive.ubuntu.com feisty-updates/multiverse Packages                                                                       
Fetched 5B in 8s (1B/s)                                                                                                                   
Failed to fetch http://beryl-mirror.lupine.me.uk/dists/feisty/Release.gpg Could not resolve 'beryl-mirror.lupine.me.uk'
Failed to fetch http://beryl-mirror.lupine.me.uk/dists/feisty/all/i18n/Translation-en_CA.bz2 Could not resolve 'beryl-mirror.lupine.me.uk'
[COLOR="Red"]Failed to fetch http://download.tuxfamily.org/3v1deb/dists/feisty/Release Unable to find expected entry  beryl-svn/binary-i386/Packages in Meta-index file (malformed Release file?)[/COLOR]
Failed to fetch http://beryl-mirror.lupine.me.uk/dists/feisty/all/binary-i386/Packages.gz Could not resolve 'beryl-mirror.lupine.me.uk'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
maha@maha-laptop:~$ sudo apt-get remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnome-compiz-manager0 libdecoration0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  compiz compiz-core compiz-gnome compiz-gtk compiz-plugins desktop-effects gnome-compiz-manager ubuntu-desktop
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 4534kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 123661 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing desktop-effects ...
Removing gnome-compiz-manager ...
Removing compiz ...
Removing compiz-plugins ...
Removing compiz-gnome ...
Removing compiz-gtk ...
Removing compiz-core ...
maha@maha-laptop:~$ sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnome-compiz-manager0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-core compiz-gnome compiz-gtk compiz-plugins
Suggested packages:
  nvidia-glx
The following NEW packages will be installed:
  compiz compiz-core compiz-gnome compiz-gtk compiz-plugins
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/535kB of archives.
After unpacking, 3219kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package compiz-core.
(Reading database ... 123521 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_1%3a0.3.6-1ubuntu13_i386.deb) ...
Selecting previously deselected package compiz-plugins.
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.3.6-1ubuntu13_i386.deb) ...
Selecting previously deselected package compiz-gtk.
Unpacking compiz-gtk (from .../compiz-gtk_1%3a0.3.6-1ubuntu13_i386.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.3.6-1ubuntu13_i386.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_1%3a0.3.6-1ubuntu13_all.deb) ...
Setting up compiz-core (0.3.6-1ubuntu13) ...
Setting up compiz-plugins (0.3.6-1ubuntu13) ...

Setting up compiz-gtk (0.3.6-1ubuntu13) ...

Setting up compiz-gnome (0.3.6-1ubuntu13) ...
Setting up compiz (0.3.6-1ubuntu13) ...
maha@maha-laptop:~$ sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

```

---

### Post by Vorian on 2007-06-25
the package name changed

use this
> sudo apt-get install compizconfig-settings-manager
sudo apt-get install libcompizconfig-backend-gconf

**AND/OR **(If you use Kubuntu)
sudo apt-get install libcompizconfig-backend-kconfig

---

### Post by mahasmb on 2007-06-25
I use Gnome and it's still telling me it can't find any of those packages.

Edit:
I'm no pro at this, but I'm gonna guess the real problem is the following?


**Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/Release](http://download.tuxfamily.org/3v1deb/dists/feisty/Release) Unable to find expected entry  beryl-svn/binary-i386/Packages in Meta-index file (malformed Release file?)**

I marked that in red in the second code box of my initial post in this thread.

---

### Post by souteneur3190 on 2007-06-25
[PHP]/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded[/PHP]"

when i run compiz --replace everything looks fine until the very bottom when the above code shows up.

I dont have nvidia or ATI, do I need to run it in aiglx or w/e?  If so how would i do that?

---

### Post by ivesjd on 2007-06-25
> **mahasmb said:**
> I use Gnome and it's still telling me it can't find any of those packages.

Edit:
I'm no pro at this, but I'm gonna guess the real problem is the following?


**Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/Release](http://download.tuxfamily.org/3v1deb/dists/feisty/Release) Unable to find expected entry  beryl-svn/binary-i386/Packages in Meta-index file (malformed Release file?)**

I marked that in red in the second code box of my initial post in this thread.

You need to add the sources, I'm pretty sure that you didnt. They are in the how-to. 

I still haven't gotten Compiz to boot properly. I get a black screen with my cursor. But when I restart X I get a flash of my background. And then I can usually re-login and it works. Does anyone have any ideas. I've tried everything in this thread (with the execption of addint the "&" to the end of emerald --replace when its in its own start-up entry. What does that & sign do?

---

### Post by HeavyAl on 2007-06-25
Just a quick note to say thanks to the original poster - it worked for me as well as a lot of others apparently. I already had the default base compiz package working right out of the box with feisty but I was surprised to see that just about everything in this 'fusion' version of it works as well. 

It's interesting that the machine I'm running on actually performs so well with all this stuff - I had Vista installed for testing at one point on the machine (IBM T40, 32Mb ATI, 1Gig Ram, 2Ghz) and it refused to allow the glass effects even with numerous registry hacks - I am thoroughly impressed that the compiz/beryl/fusion group has been able to put out such a spiffy tool that can work on what I think is a relatively low end machine without any obvious show stoppers.

Two points of contention that I will add: Having to install emerald to get the borders working properly isn't the most intuitive way of getting this thing going, but it's not a huge problem - though I personally am still confused about why I need to have a separate theme manager rather than the built in gnome themeing stuff. ... the other thing is that video still blacks out when swapping desktops rather than continuously playing as I've seen in some of the videos floating around - though I'm betting this has something to do with the low end nature of my video card and it's not a big deal anyway since I don't play vids that often.

Anyway, nice work all the way around.

---

### Post by m.musashi on 2007-06-25
Thanks for the how to. Seems to be working well - maybe better than beryl but then I guess that was the idea.

Quick question. With beryl I used to have set so that the cube would rotate with the mouse wheel but I don't see that option in the compiz settings manager. Any idea how to get that working?

Thanks.

---

### Post by walkerk on 2007-06-25
Sessions > Preferences > CompizConfig Settings Manager

should be in there..

---

### Post by m.musashi on 2007-06-25
Yeah, that's where I'm looking but not finding it. There are some options under rotate cube but I can't find anything about using the mouse wheel.

---

### Post by gkiller on 2007-06-25
> **m.musashi said:**
> Yeah, that's where I'm looking but not finding it. There are some options under rotate cube but I can't find anything about using the mouse wheel.
It's the plugin "Viewport Mouse Switch". But it isn't complete yet. The screen edge mousewheel function is not implemented yet.

---

### Post by m.musashi on 2007-06-25
> **gkiller said:**
> It's the plugin "Viewport Mouse Switch". But it isn't complete yet. The screen edge mousewheel function is not implemented yet.

Ah, thanks. That clears that up. I guess I'll just wait.

---

### Post by AriciU on 2007-06-25
Doesn't work for me at all. Reinstalled emerald too...

Lame standard window borders + no effect whatsoever.... wobbly windows, cube, rotating cube, etc etc

It's like it hasn't loaded at all.

I've set it to autostart in Sessions and rebooted (compiz --replace and emerald --replace &).

I'm having no problems running Beryl. Dunno wtf can be wrong with this.

I'm getting this message when running "compiz --replace" in the console btw:

> Adding core settings (General Options)
Adding plugin annotate (annotate)
Adding plugin blur (blur)
Adding plugin clone (clone)
Adding plugin cube (cube)
Adding plugin dbus (dbus)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin fs (fs)
Adding plugin glib (glib)
Adding plugin inotify (inotify)
Adding plugin minimize (minimize)
Adding plugin move (move)
Adding plugin place (place)
Adding plugin plane (plane)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin resize (resize)
Adding plugin rotate (rotate)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin video (video)
Adding plugin water (water)
Adding plugin wobbly (wobbly)
Adding plugin zoom (zoom)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin imgjpeg (imgjpeg)
Adding plugin neg (neg)
Adding plugin opacify (opacify)
Adding plugin put (put)
Adding plugin resizeinfo (resizeinfo)
Adding plugin ring (ring)
Adding plugin scaleaddon (scaleaddon)
Adding plugin snap (snap)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin vpswitch (vpswitch)
Adding plugin wall (wall)
Adding plugin winrules (winrules)
Adding plugin addhelper (addhelper)
Adding plugin bench (bench)
Adding plugin crashhandler (crashhandler)
Adding plugin cubereflex (cubereflex)
Adding plugin extrawm (extrawm)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin group (group)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin showdesktop (showdesktop)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin fakeargb (fakeargb)
Adding plugin snow (snow)
Adding plugin tile (tile)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


---

### Post by AriciU on 2007-06-25
Switched back to Beryl and found out that my window borders dissapeared when using Emerald. They used to work before installing fusion and updating emerald with the package from these new repo's. 

Now i have to use the GTK window manager with Beryl. I should've just stayed put ffs :mad:

---

### Post by andrewsomething on 2007-06-25
> **AriciU said:**
> Switched back to Beryl and found out that my window borders dissapeared when using Emerald. They used to work before installing fusion and updating emerald with the package from these new repo's. 

Now i have to use the GTK window manager with Beryl. I should've just stayed put ffs :mad:

What repo are you getting Beryl from? I'm assuming it's from the Beryl Project repo. You might want to try going with the version in Trevino's (the same place that Compiz/Fusion is) if that is where you are getting Emerald...

I was having problems getting Emerald to work with Compiz Fusion. After upgrading to the versions of Beryl and Emerald in Trevino's repo, I can now switch back and forth from Compiz/Fusion to Beryl with ease and Emerald works with both.

---

### Post by AriciU on 2007-06-25
I'm afraid to do that really :) Don't want to mess Beryl up too. Hope someone will manage to work it out... problem comes from "compiz --replace" spitting out "failed to open device" errors.

---

### Post by TmP on 2007-06-26
I had the same decoration problem, but the solution from andrewsomething helped.
Just throw the damned Beryl repository out from:
> sudo gedit /etc/apt/sources.list
then
> 
sudo apt-get update
sudo apt-get remove emerald
sudo apt-get upgrade
sudo apt-get install emerald

*Or sth like that. I'm a noob so I don't stack my commands.*

and there you go!

Although I still have this problem but I can now correct it using the 
> compiz --replace -c emerald &
command.

Also, 
it seems to be much more optimized than Beeryl. I can now run it on "good" instead of "fast".
Maby thats because I've been using the Beryl RC... from SVN

---

### Post by mahasmb on 2007-06-26
> **ivesjd said:**
> You need to add the sources, I'm pretty sure that you didnt. They are in the how-to. 

I still haven't gotten Compiz to boot properly. I get a black screen with my cursor. But when I restart X I get a flash of my background. And then I can usually re-login and it works. Does anyone have any ideas. I've tried everything in this thread (with the execption of addint the "&" to the end of emerald --replace when its in its own start-up entry. What does that & sign do?

Okay, first of all Richard rocks! I really liked reading through LFG especially closer to the beginning of it. Secondly though, I definitely added those those sources. Tried it more than once, but I think an installation from before is messing  me up because the following package keeps on failing.

**_[http://download.tuxfamily.org/3v1deb/dists/feisty/Release](http://download.tuxfamily.org/3v1deb/dists/feisty/Release) Unable to find expected entry  beryl-svn/binary-i386/Packages in Meta-index file (malformed Release file?)_**

I really don't know how to fix this. 

Here's my post from earlier on in this thread:

> **mahasmb said:**
> I get stuck here @[COLOR="Red"] sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!
[/COLOR]
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="#ff0000"]E: Couldn't find package compizconfig-settings-manager[/COLOR]
```


Here's my whole upgrade process
```
maha@maha-laptop:~$ sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
--09:25:37--  http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,180 (4.1K) [text/plain]

100%[===============================================================================================>] 4,180          5.69K/s             

09:25:38 (5.69 KB/s) - `-' saved [4180/4180]

OK
maha@maha-laptop:~$ sudo apt-get update
Err http://beryl-mirror.lupine.me.uk feisty Release.gpg
  Could not resolve 'beryl-mirror.lupine.me.uk'
Err http://beryl-mirror.lupine.me.uk feisty/all Translation-en_CA                                                                         
  Could not resolve 'beryl-mirror.lupine.me.uk'
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]                                                                       
Ign http://security.ubuntu.com feisty-security/main Translation-en_CA                                                                     
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_CA                                                               
Get:2 http://download.tuxfamily.org feisty Release.gpg [189B]                                                                             
Ign http://download.tuxfamily.org feisty/beryl-svn Translation-en_CA                                                                      
Ign http://download.tuxfamily.org feisty/eyecandy Translation-en_CA                                                                       
Ign http://beryl-mirror.lupine.me.uk feisty Release                                                                                       
Hit http://download.tuxfamily.org feisty Release                                                                                          
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_CA                                                               
Hit http://security.ubuntu.com feisty-security Release                                                                                    
Hit http://security.ubuntu.com feisty-security/main Packages                                                                              
Hit http://security.ubuntu.com feisty-security/restricted Packages                                                    
Hit http://security.ubuntu.com feisty-security/main Sources                                                                               
Hit http://security.ubuntu.com feisty-security/restricted Sources                                                                         
Hit http://security.ubuntu.com feisty-security/multiverse Packages                                                                        
Get:3 http://archive.ubuntu.com feisty Release.gpg [191B]                                                                                 
Ign http://archive.ubuntu.com feisty/universe Translation-en_CA                                                       
Ign http://archive.ubuntu.com feisty/main Translation-en_CA                                              
Ign http://archive.ubuntu.com feisty/restricted Translation-en_CA                                        
Hit http://archive.ubuntu.com feisty Release                                                             
Hit http://archive.ubuntu.com feisty/universe Packages                                                   
Hit http://archive.ubuntu.com feisty/main Packages                                 
Hit http://archive.ubuntu.com feisty/restricted Packages                           
Ign http://beryl-mirror.lupine.me.uk feisty/all Packages                                            
Err http://beryl-mirror.lupine.me.uk feisty/all Packages                                            
  Could not resolve 'beryl-mirror.lupine.me.uk'
Get:4 http://ca.archive.ubuntu.com feisty Release.gpg [191B]                                                                              
Ign http://ca.archive.ubuntu.com feisty/multiverse Translation-en_CA                                                                      
Get:5 http://ca.archive.ubuntu.com feisty-updates Release.gpg [191B]                                                                      
Ign http://ca.archive.ubuntu.com feisty-updates/main Translation-en_CA                                                                    
Ign http://ca.archive.ubuntu.com feisty-updates/restricted Translation-en_CA                                                              
Ign http://ca.archive.ubuntu.com feisty-updates/multiverse Translation-en_CA                                                              
Hit http://ca.archive.ubuntu.com feisty Release                                                                                           
Hit http://ca.archive.ubuntu.com feisty-updates Release                                                                                   
Hit http://ca.archive.ubuntu.com feisty/main Sources                                                                                      
Hit http://ca.archive.ubuntu.com feisty/restricted Sources                                                                                
Hit http://ca.archive.ubuntu.com feisty/multiverse Packages                                                                               
Hit http://ca.archive.ubuntu.com feisty-updates/main Packages                                                                             
Hit http://ca.archive.ubuntu.com feisty-updates/restricted Packages                                                                       
Hit http://ca.archive.ubuntu.com feisty-updates/main Sources                                                                              
Hit http://ca.archive.ubuntu.com feisty-updates/restricted Sources                                                                        
Hit http://ca.archive.ubuntu.com feisty-updates/multiverse Packages                                                                       
Fetched 5B in 8s (1B/s)                                                                                                                   
Failed to fetch http://beryl-mirror.lupine.me.uk/dists/feisty/Release.gpg Could not resolve 'beryl-mirror.lupine.me.uk'
Failed to fetch http://beryl-mirror.lupine.me.uk/dists/feisty/all/i18n/Translation-en_CA.bz2 Could not resolve 'beryl-mirror.lupine.me.uk'
[COLOR="Red"]Failed to fetch http://download.tuxfamily.org/3v1deb/dists/feisty/Release Unable to find expected entry  beryl-svn/binary-i386/Packages in Meta-index file (malformed Release file?)[/COLOR]
Failed to fetch http://beryl-mirror.lupine.me.uk/dists/feisty/all/binary-i386/Packages.gz Could not resolve 'beryl-mirror.lupine.me.uk'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
maha@maha-laptop:~$ sudo apt-get remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnome-compiz-manager0 libdecoration0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  compiz compiz-core compiz-gnome compiz-gtk compiz-plugins desktop-effects gnome-compiz-manager ubuntu-desktop
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 4534kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 123661 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing desktop-effects ...
Removing gnome-compiz-manager ...
Removing compiz ...
Removing compiz-plugins ...
Removing compiz-gnome ...
Removing compiz-gtk ...
Removing compiz-core ...
maha@maha-laptop:~$ sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnome-compiz-manager0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-core compiz-gnome compiz-gtk compiz-plugins
Suggested packages:
  nvidia-glx
The following NEW packages will be installed:
  compiz compiz-core compiz-gnome compiz-gtk compiz-plugins
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/535kB of archives.
After unpacking, 3219kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package compiz-core.
(Reading database ... 123521 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_1%3a0.3.6-1ubuntu13_i386.deb) ...
Selecting previously deselected package compiz-plugins.
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.3.6-1ubuntu13_i386.deb) ...
Selecting previously deselected package compiz-gtk.
Unpacking compiz-gtk (from .../compiz-gtk_1%3a0.3.6-1ubuntu13_i386.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.3.6-1ubuntu13_i386.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_1%3a0.3.6-1ubuntu13_all.deb) ...
Setting up compiz-core (0.3.6-1ubuntu13) ...
Setting up compiz-plugins (0.3.6-1ubuntu13) ...

Setting up compiz-gtk (0.3.6-1ubuntu13) ...

Setting up compiz-gnome (0.3.6-1ubuntu13) ...
Setting up compiz (0.3.6-1ubuntu13) ...
maha@maha-laptop:~$ sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

```

Hopefully someone can help? :(

---

### Post by ivesjd on 2007-06-26
The best thing I can tell you is to remove everything. Beryl. Emerald. Compiz fusion. and run through the guide again. on another note, I finally got compiz to boot, I put "compiz --replace -c emerald &" in a boot script, but also had sleep 30 which makes it wait 30 seconds before it runs the command.

---

### Post by mahasmb on 2007-06-26
It took me forever to get Beryl working.. I have an ATI card. I'd much rather stick with what I have until a better solution comes my way.

---

### Post by oliwally on 2007-06-26
Thanks for all this - got Compiz Fusion working with very little hassle. Just a few questions:

Compiz doesn't seem quite as smooth as Beryl (on my computer - centrino duo and 256MB Nvidia). Expecially rotating the cube is a tiny bit fragmented. Compiz Benchmark tells me that the framerate drops to about 15 fps when rotating the cube (at other times it hovers at about 60fps). How do I solve this?

In Beryl I used Emerald for various decorations. What do I use in Compiz to have different themes available to me?

---

### Post by gkiller on 2007-06-26
> **oliwally said:**
> Thanks for all this - got Compiz Fusion working with very little hassle. Just a few questions:

Compiz doesn't seem quite as smooth as Beryl (on my computer - centrino duo and 256MB Nvidia). Expecially rotating the cube is a tiny bit fragmented. Compiz Benchmark tells me that the framerate drops to about 15 fps when rotating the cube (at other times it hovers at about 60fps). How do I solve this?Try going into Compizconfig Settings Manager > General, and deactive both "detect refresh rate", "sync to vblank", and set refresh rate to 200.

---

### Post by Imarri01 on 2007-06-26
i installed compiz fusion and everything is working fine except the cude. I seem to only have 1 desktop so wen i press ctrl-alt-mouse1 nothing happens and when i use expose it only shows just one screen. Any ideas?

---

### Post by andrewsomething on 2007-06-26
> **Imarri01 said:**
> i installed compiz fusion and everything is working fine except the cude. I seem to only have 1 desktop so wen i press ctrl-alt-mouse1 nothing happens and when i use expose it only shows just one screen. Any ideas?

Well, first of all, make sure that you have both "desktop cube" and "rotate cube" enabled. The next place to look is General Options>Desktop Size. Horizontal Virtual Size should be set be set to four. Vertical Virtual Size and Number of Desktops should be set to one (I know that's counter intuitive).

See if that works...

---

### Post by vexorian on 2007-06-26
hi, how do you use emerald themes on compiz-fusion?

---

### Post by borimrr on 2007-06-26
Do I need to create an XGL session adn log into it to run Compiz-Fusion or can I use a regular GNOME session?

---

### Post by chaser209 on 2007-06-26
EDIT: Nevermind.

---

### Post by puppy on 2007-06-26
Hmm, no luck for me:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gtk: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but 1:0.5.1+git20070626~3v1ubuntu0 is to be installed
E: Broken packages

:(

---

### Post by karlhm76 on 2007-06-26
I found that I didn't need compiz-gtk, although one guide I followed said that I needed it. I don't have it installed now and it works fine.

---

### Post by karlhm76 on 2007-06-26
> **Imarri01 said:**
> i installed compiz fusion and everything is working fine except the cude. I seem to only have 1 desktop so wen i press ctrl-alt-mouse1 nothing happens and when i use expose it only shows just one screen. Any ideas?

I had a similar problem and it was caused by the fact I only had one workspace set up. as soon as I increased the number of workspaces to 2 or more I was able to rotate the "cube". Having a desktop triangular prism was excellent, but I have a traditional cube now.

There is an option in the settings manager somewhere - I'm at work and not at my computer now so I don't know exactly where it is.

Incidently, I got compiz to crash back to metacity by clicking on the workspace switcher. It just froze and then dumped me back to metacity.

---

### Post by LlamaKing on 2007-06-26
```
$ compiz --replace

Adding plugin plane (plane)
Adding plugin regex (regex)
Adding plugin clone (clone)
Adding plugin glib (glib)
Adding plugin svg (svg)
Adding plugin resize (resize)
Adding plugin fs (fs)
Adding plugin video (video)
Adding plugin move (move)
Adding core settings (General Options)
Adding plugin zoom (zoom)
Adding plugin rotate (rotate)
Adding plugin cube (cube)
Adding plugin annotate (annotate)
Adding plugin decoration (decoration)
Adding plugin place (place)
Adding plugin screenshot (screenshot)
Adding plugin minimize (minimize)
Adding plugin water (water)
Adding plugin blur (blur)
Adding plugin dbus (dbus)
Adding plugin wobbly (wobbly)
Adding plugin inotify (inotify)
Adding plugin switcher (switcher)
Adding plugin scale (scale)
Adding plugin png (png)
Adding plugin fade (fade)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing svg options...done
Initializing resize options...done
Initializing move options...done
Initializing zoom options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing place options...done
Initializing minimize options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done
Initializing scale options...done
Initializing rotate options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
```

-------------------------------

Emerald doesn't load after this. I've tried everything. All the effects in compiz run great as far as I can tell, but it's a little hard trying to work with no window borders. Anybody have any advice on getting emerald to work?

---

### Post by oliwally on 2007-06-27
> **gkiller said:**
> Try going into Compizconfig Settings Manager > General, and deactive both "detect refresh rate", "sync to vblank", and set refresh rate to 200.

I have done this and it's still not running as smoothly as Beryl did. The 'burn' effect on closing windows also runs a bit slowly.

Since it ran well with Beryl, I'm assuming that the problem is not with the capability of my hardware, but rather some configuration somewhere. Can anyone help? Should I post my xorg.conf?

And I'm still puzzled as to whether or not I should be using Emerald? Will it work? What other decorators are there?

---

### Post by shinjo101788 on 2007-06-27
I am having a somewhat related problem. I installed all the stuff like the instructions said to and i have a number of problems. For one, when i start up ubuntu the window that shows the programs it is loading does not go away. it stays on the desktop on "nautilus" also i also do not have any window bars. When i run the metacity replace command i get a number of errors

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_on_all_workspaces"
Window manager warning: "" found in configuration database is not a valid value for keybinding "maximize_vertically"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_1"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_2"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_up"


then when i run the compiz replace i get these errors

Adding plugin resizeinfo (resizeinfo)
Adding plugin tile (tile)
Adding plugin wall (wall)
Adding plugin cubereflex (cubereflex)
Adding plugin crashhandler (crashhandler)
Adding plugin png (png)
Adding plugin water (water)
Adding plugin splash (splash)
Adding plugin firepaint (firepaint)
Adding plugin rotate (rotate)
Adding plugin addhelper (addhelper)
Adding plugin showdesktop (showdesktop)
Adding plugin regex (regex)
Adding plugin dbus (dbus)
Adding plugin wobbly (wobbly)
Adding plugin inotify (inotify)
Adding plugin group (group)
Adding plugin resize (resize)
Adding plugin cube (cube)
Adding plugin decoration (decoration)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin snow (snow)
Adding plugin clone (clone)
Adding plugin opacify (opacify)
Adding plugin text (text)
Adding plugin svg (svg)
Adding plugin minimize (minimize)
Adding plugin extrawm (extrawm)
Adding plugin snap (snap)
Adding plugin scale (scale)
Adding plugin put (put)
Adding plugin blur (blur)
Adding plugin fs (fs)
Adding plugin place (place)
Adding plugin reflex (reflex)
Adding plugin switcher (switcher)
Adding plugin plane (plane)
Adding plugin fade (fade)
Adding plugin scaleaddon (scaleaddon)
Adding plugin move (move)
Adding plugin ring (ring)
Adding plugin thumbnail (thumbnail)
Adding plugin trailfocus (trailfocus)
Adding plugin glib (glib)
Adding plugin fadedesktop (fadedesktop)
Adding plugin winrules (winrules)
Adding plugin imgjpeg (imgjpeg)
Adding plugin bench (bench)
Adding plugin video (video)
Adding core settings (General Options)
Adding plugin mblur (mblur)
Adding plugin zoom (zoom)
Adding plugin annotate (annotate)
Adding plugin fakeargb (fakeargb)
Adding plugin neg (neg)
Adding plugin screenshot (screenshot)
Backend : ini
Integration : true
Profile : default
Initializing core options...done
Initializing tile options...done
Initializing water options...done
Initializing splash options...done
Initializing firepaint options...done
Initializing showdesktop options...done
Initializing resize options...done
Initializing decoration options...done
Initializing animation options...done
Initializing expo options...done
Initializing svg options...done
Initializing minimize options...done
Initializing blur options...done
Initializing place options...done
Initializing switcher options...done
Initializing move options...done
Initializing ring options...done
Initializing thumbnail options...done
Initializing imgjpeg options...done
Initializing mblur options...done
Initializing zoom options...done
Initializing neg options...done
Initializing wobbly options...done
Initializing reflex options...done
Initializing fade options...done
Initializing group options...done
Initializing scale options...done
/usr/bin/compiz.real (splash) - Warn: Could not load splash background image "/data/splash_background.png" !
/usr/bin/compiz.real (splash) - Warn: Could not load splash logo image "/data/splash_logo.png" !

everything seems to work except when i colose the terminal it gors back to normal. and by normal i mean no borders and the nautilus thingy on my desktop.

could it be that I still have beryl installed?

Im really new to linux so i really appreciate all of your help, thank you.

I also have this error too

~$ /usr/bin/compiz.real (core) - Warn: pixmap 0xe0126b can't be bound to texture

i ran copiz--replace and metacity--replace in the alt-F2 window and everything works, except when i restat my compuet all of it erases. Aslo the "nautilius" thing will not go away.

can anyone help? :)

---

### Post by CarlosinFL on 2007-06-27
Guys - I am having **problems** with this. I am doing a fresh install of Ubuntu and installed "Restricted Drivers" so I am testing the nVidia card and all looks well.

I was able to manually edit the source list and add the 2 suggested entries and then do an apt-get clean and a new apt-get update.

Now when it comes time to start entering in the commands, I have problems.

Please HELP or any suggestions are greatly appreciated!

```
cwilliams@cwilliams:~$ sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]                 
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US               
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://download.tuxfamily.org feisty Release.gpg [189B]
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US  
Ign http://download.tuxfamily.org feisty/eyecandy Translation-en_US  
Hit http://download.tuxfamily.org feisty Release
Hit http://download.tuxfamily.org feisty/eyecandy Packages          
Hit http://download.tuxfamily.org feisty/eyecandy Sources
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]                                                        
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Get:5 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Hit http://security.ubuntu.com feisty-security/main Sources
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security/restricted Sources
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Hit http://security.ubuntu.com feisty-security/universe Packages
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://us.archive.ubuntu.com feisty Release
Hit http://security.ubuntu.com feisty-security/multiverse Packages  
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://security.ubuntu.com feisty-security/multiverse Sources   
Hit http://us.archive.ubuntu.com feisty-backports Release
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Sources
Hit http://us.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Sources
Fetched 5B in 2m4s (0B/s)
Reading package lists... Done
cwilliams@cwilliams:~$ sudo apt-get remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  compiz-plugins: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by mid_night gypsy on 2007-06-27
I remove my post.

---

### Post by CarlosinFL on 2007-06-27
**Bumping to last page for help**

---------------------

Guys - I am having **problems** with this. I am doing a fresh install of Ubuntu and installed "Restricted Drivers" so I am testing the nVidia card and all looks well.

I was able to manually edit the source list and add the 2 suggested entries and then do an apt-get clean and a new apt-get update.

Now when it comes time to start entering in the commands, I have problems.

Please HELP or any suggestions are greatly appreciated!

```
cwilliams@cwilliams:~$ sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]                 
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US               
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://download.tuxfamily.org feisty Release.gpg [189B]
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US  
Ign http://download.tuxfamily.org feisty/eyecandy Translation-en_US  
Hit http://download.tuxfamily.org feisty Release
Hit http://download.tuxfamily.org feisty/eyecandy Packages          
Hit http://download.tuxfamily.org feisty/eyecandy Sources
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]                                                        
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Get:5 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Hit http://security.ubuntu.com feisty-security/main Sources
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security/restricted Sources
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Hit http://security.ubuntu.com feisty-security/universe Packages
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://us.archive.ubuntu.com feisty Release
Hit http://security.ubuntu.com feisty-security/multiverse Packages  
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://security.ubuntu.com feisty-security/multiverse Sources   
Hit http://us.archive.ubuntu.com feisty-backports Release
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Sources
Hit http://us.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Sources
Fetched 5B in 2m4s (0B/s)
Reading package lists... Done
cwilliams@cwilliams:~$ sudo apt-get remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  compiz-plugins: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by LouisvilleLIP on 2007-06-27
> **mahasmb said:**
> It took me forever to get Beryl working.. I have an ATI card. I'd much rather stick with what I have until a better solution comes my way.

How did you finally get it?  I'm having the same problem you had.
(Never mind, I figured it out.)

---

### Post by PRGUY85 on 2007-06-27
Hey there:

I installed Compiz-Fusion and have it working wonderfully on my laptop. Yet, it doesn't start automatically every time I boot up Ubuntu. I have to do the following command every time on my terminal:

compiz --replace -c emerald &

I added the command to my startup list on Preferences---Sessions, yet it doesn't work. I have to do it on terminal each time.

How do I make Compiz-Fusion work everytime I log on?

---

### Post by shinjo101788 on 2007-06-28
I have a question.

I got compiz fusion running beatifully.  Now i have an update window telling me to update compiz.  I am afraid to do it because i have worked so hard on it.  Will updating it ruin anything?? I have some pictures below of the update window.  

and to fix your problem PRGUY85:

(This worked for me, i had your exact same problem)


Open up gconf-editor and go to desktop/gnome/applications/window_manager

Set "current" and "default" to /usr/bin/metacity

Reload gdm / restart and compiz should load fine now.

My pics are attatched.

---

### Post by Vorian on 2007-06-28
> **shinjo101788 said:**
> I have a question.

I got compiz fusion running beatifully.  Now i have an update window telling me to update compiz.  I am afraid to do it because i have worked so hard on it.  Will updating it ruin anything?? I have some pictures below of the update window. 
I have experienced _zero_ problems with the latest upgrade :)

---

### Post by repolho on 2007-06-28
so difficult here.... i just install compiz, works fine.... did the update... segmentation fault, and my cssm always core dumped.... same tips?

---

### Post by shinjo101788 on 2007-06-28
Is there a possibility i can get that error?

---

### Post by Vorian on 2007-06-28
> **shinjo101788 said:**
> Is there a possibility i can get that error?There is always the possibility.  It is bleeding edge software in development, so you should expect breakage.

Sorry :(

---

### Post by shinjo101788 on 2007-06-28
so can i deselect them anyway? when i deselect the check box and i close the window, it still tells me i have updates to install.

---

### Post by Vorian on 2007-06-28
> **shinjo101788 said:**
> so can i deselect them anyway? when i deselect the check box and i close the window, it still tells me i have updates to install.

Sure, you don't have to select the upgrade.  There will most likely be daily builds on CF.  If you want to be cautious, wait to see if people are having problems before you upgrade.

:)

---

### Post by gkiller on 2007-06-28
> **Carlwill said:**
> **Bumping to last page for help**

---------------------

Guys - I am having **problems** with this. I am doing a fresh install of Ubuntu and installed "Restricted Drivers" so I am testing the nVidia card and all looks well.

I was able to manually edit the source list and add the 2 suggested entries and then do an apt-get clean and a new apt-get update.

Now when it comes time to start entering in the commands, I have problems.

Please HELP or any suggestions are greatly appreciated!

Try removing the Trevino repositories from sources.list, then doing apt-get update and then remove compiz-core and desktop-effects. Maybe that will work. I would first try to resolve all the conflicts without having the Trevino repo added because that one only complicates everything. Once all is cleared up and the old compiz-core removed, you can try to add Trevino repo back and get the new compiz/fusion.

On how to resolve remaining conflicts: try "sudo apt-get -f install", or go into Synaptic, I think it has some conflict manager there. Or you could try aptitude, but that is a bit advanced and I don't know enough about it to tell in detail how to solve conflicts with it.

> **Vorian said:**
> Sure, you don't have to select the upgrade.  There will most likely be daily builds on CF.  If you want to be cautious, wait to see if people are having problems before you upgrade.
I think Trevino mentioned that he'll update the packages about twice a week or so.


**Advise to all: **If you are happy with your compiz/fusion as it is now and don't want to risk breakage, just remove the Trevino repository from your sources.list. That way the current version will stay and you won't be bothered with any more update messages about compiz.

---

### Post by sambehera on 2007-06-29
im having problems getting this to work...

```
buzz@buzz-station:~$ sudo apt-get -y install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-kconfig
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
```

where can i find compizconfig-settings-manager??

im running kubuntu feisty amd64

---

### Post by sdelano on 2007-06-29
I have just installed compiz-fusion and the compiz --replace command at first was nnot working for me. I saw that I needed to update a few things (system update notification), did so, and it still doesnt work. I then read that restarting help, so i restarted and tried compiz --replace again. Well... Compiz works...but my window manager does not. 

When I did the system update I have a feeling I updated something having to do with the WM. This is the error I get when loading compiz:

```
Adding plugin zoom (zoom)
Adding plugin tile (tile)
Adding core settings (General Options)
Adding plugin wobbly (wobbly)
Adding plugin expo (expo)
Adding plugin screenshot (screenshot)
Adding plugin cubereflex (cubereflex)
Adding plugin scaleaddon (scaleaddon)
Adding plugin firepaint (firepaint)
Adding plugin glib (glib)
Adding plugin clone (clone)
Adding plugin addhelper (addhelper)
Adding plugin fs (fs)
Adding plugin place (place)
Adding plugin fadedesktop (fadedesktop)
Adding plugin move (move)
Adding plugin thumbnail (thumbnail)
Adding plugin fade (fade)
Adding plugin bench (bench)
Adding plugin cube (cube)
Adding plugin annotate (annotate)
Adding plugin snow (snow)
Adding plugin reflex (reflex)
Adding plugin switcher (switcher)
Adding plugin resizeinfo (resizeinfo)
Adding plugin video (video)
Adding plugin splash (splash)
Adding plugin wall (wall)
Adding plugin text (text)
Adding plugin opacify (opacify)
Adding plugin dbus (dbus)
Adding plugin animation (animation)
Adding plugin vpswitch (vpswitch)
Adding plugin snap (snap)
Adding plugin svg (svg)
Adding plugin group (group)
Adding plugin imgjpeg (imgjpeg)
Adding plugin water (water)
Adding plugin blur (blur)
Adding plugin fakeargb (fakeargb)
Adding plugin ring (ring)
Adding plugin rotate (rotate)
Adding plugin put (put)
Adding plugin minimize (minimize)
Adding plugin crashhandler (crashhandler)
Adding plugin plane (plane)
Adding plugin resize (resize)
Adding plugin decoration (decoration)
Adding plugin mblur (mblur)
Adding plugin inotify (inotify)
Adding plugin winrules (winrules)
Adding plugin trailfocus (trailfocus)
Adding plugin showdesktop (showdesktop)
Adding plugin neg (neg)
Adding plugin png (png)
Adding plugin scale (scale)
Adding plugin regex (regex)
Adding plugin extrawm (extrawm)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing zoom options...done
Initializing place options...done
Initializing move options...done
Initializing thumbnail options...done
Initializing minimize options...done
Initializing resize options...done
[COLOR="Red"]/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319[/COLOR]

Initializing decoration options...done
Initializing mblur options...done
Initializing showdesktop options...done
Initializing wobbly options...done
Initializing reflex options...done
Initializing animation options...done
Initializing blur options...done
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done
Initializing rotate options...done
Initializing scale options...done
Initializing expo options...done
Initializing cubereflex options...done

```

Thanks,
Stephen

---

### Post by chestnut1969 on 2007-06-29
Simply stunning, love it :)

---

### Post by dr_psikick on 2007-06-30
Great toturial! Thanks!
Is it possible to assign diferent desktop backgrounds to the diferent virtual desktops or viewports? If so, how?
Thanks.

---

### Post by locke.dragon on 2007-06-30
could someone post a .sh script that would launch BOTH compiz fusion AND emerald on startup?  i've tried doing it, but i'm still a noob.  :p

---

### Post by ChadMC on 2007-06-30
> **locke.dragon said:**
> could someone post a .sh script that would launch BOTH compiz fusion AND emerald on startup?  i've tried doing it, but i'm still a noob.  :p

I use this command...
```
compiz --replace -c emerald &
```

---

### Post by enrigp on 2007-06-30
Hello to everybody,

I Have  the same problem than LlamaKing,

I have installed compiz and when i launch compiz i lose the windows borders

I have seen in other forums this error but nobody solve the problem, I had working ok with previous version of Ubuntu (Dapper), but with Feisty the borders goes out.

Help Please Please, or say me whe can i find the log of metacity or compiz to try look for any error.

:(

---

### Post by tact on 2007-07-03
> **llamakc said:**
> I just figured out grouping. it is really sweet.

Super+S on the windows you want to select for grouping, Super+G to group them, then try Super+left/right keys. Sweet.

It gets even sweeter....   in the settings for grouping and tabbing turn on the "auto tab windows"....

What it does is this - whenever you open a window it is automatically "tabbed" to its own group of one window.   Every window you open is similarly tabbed to its own group of one window.  

Now the sweetness...   to place two windows into one tabbed group just drag the little icon-window that appears when you hover mouse on the title bar... over to the other window's title bar.  Presto!  they merge into one...  continue adding windows as you like.

To take a window from a group... drag the little icon window to some clear space on your desktop... or even drag it onto a totally different desktop!

---

### Post by trinaryouroboros on 2007-07-03
Is this available for 64-bit yet?

---

### Post by lsalminen on 2007-07-04
Hi, I followed this guide exactly, but when I do Alt-F2 and start compiz, there are no effects.... is there a way to get the effects to start??

---

### Post by Djieff on 2007-07-04
Hi everyone,

I installed compiz fusion following the steps, and everything went well. When the install was complete, I did Alt+F2 and I typed this:

compiz --replace

Unfortunately, I lost all the window decorations. Sometime it is so bad, that every shell I open is a white square, where I can't write. The only option at this point is to log out. Then I found another command, which I tried:

compiz --replace -c emerald &

It gave me the same exact results. I thought that maybe there was a chance that emerald wasn't installed. so I typed this command:

sudo apt-get install emerald emerald-themes

It installed something, and then I re-tried "compiz --replace -c emerald &" it gave me the same results again.

I'm using an Nvidia 7300 LE with a resolution of 1280x1024 with the nvidia restricted drivers.


Do you have any Idea?
thanks,

---

### Post by mafutha1 on 2007-07-04
Compiz fusion rocks! Dream on Bill! It took me awhile to get it working,using this and other threads but windows will never see me again.Great how to. Thanx.

---

### Post by mafutha1 on 2007-07-04
> **Djieff said:**
> Hi everyone,

I installed compiz fusion following the steps, and everything went well. When the install was complete, I did Alt+F2 and I typed this:

compiz --replace

Unfortunately, I lost all the window decorations. Sometime it is so bad, that every shell I open is a white square, where I can't write. The only option at this point is to log out. Then I found another command, which I tried:

compiz --replace -c emerald &

It gave me the same exact results. I thought that maybe there was a chance that emerald wasn't installed. so I typed this command:

sudo apt-get install emerald emerald-themes

It installed something, and then I re-tried "compiz --replace -c emerald &" it gave me the same results again.

I'm using an Nvidia 7300 LE with a resolution of 1280x1024 with the nvidia restricted drivers.


Do you have any Idea?
thanks,
I tried everything and nothing worked till I stumbled onto this, in Compiz Settings Manager,window decoration,command insert, emerald --replace.This worked for me,good luck,keep trying!

---

### Post by SurfHawk on 2007-07-05
Got to the step of compiz --replace and got the following result:

Fatal: Failed test: texture from pixmap support
Checks indicate that it's impossible to start compiz on your system

I successfully had beryl running like a champ before this with the exception of games freezing, but all the desktop effects were great.  And I made sure to remove all "beryl" before starting this process.  Here are my system specs:

VooDoo Envy laptop with Pentium M 1.73 Ghz
2GB RAM
ATI Radeon R300 using restricted drivers
Feisty Fawn

I would appreciate any help that you can give.  Be aware that I am a relative noob to Ubuntu and Linux in general and I am still negotiating the learning cure.

Thank you.

---

### Post by blackdevil on 2007-07-08
well, I followed instructions. Didnt work. Deleted and reinstalled, didnt work. After typing in 'compiz --replace -c emerald &' I get the following:

blackdevil@Daedalus:~$ compiz --replace -c emerald &
[1] 7306
blackdevil@Daedalus:~$ /usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

Some things work like transparency, but nothing else. Windo w decorations also dissapear. Somewhat boggling. Beryl was running quite good.

---

### Post by EnderTheThird on 2007-07-08
> **blackdevil said:**
> well, I followed instructions. Didnt work. Deleted and reinstalled, didnt work. After typing in 'compiz --replace -c emerald &' I get the following:

blackdevil@Daedalus:~$ compiz --replace -c emerald &
[1] 7306
blackdevil@Daedalus:~$ /usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

Some things work like transparency, but nothing else. Windo w decorations also dissapear. Somewhat boggling. Beryl was running quite good.

Basically the same problem here.  I can't seem to find a fix anywhere either.

---

### Post by blackdevil on 2007-07-08
It sounds like the deb needs to be rebuilt, but I cant find an older source or another deb to use in the mean time. Anyone? Anyone?

---

### Post by firmwire on 2007-07-08
> **EnderTheThird said:**
> Basically the same problem here.  I can't seem to find a fix anywhere either.

Ditto

---

### Post by blackdevil on 2007-07-08
Talked to Trevinho, and the problem is that the deb isnt updated in  the script. He is apparently working on it now and the fix should be out soon hopefully.

---

### Post by firmwire on 2007-07-08
BAM!!! I knew it was something like that. Nice work!

---

### Post by blackdevil on 2007-07-08
I just compiled from scratch... but I dont have all the plugins. Apparently some are in one location and the others are in another. Possibly conflicting problems with Trevinho's deb installation, though I thought I deleted it.

---

### Post by Matteran on 2007-07-08
Thanks a lot, works great in Linux Mint. It's a combination of the best of Beryl and Compiz, GREAT!

However, how can I enable Anisotropic filtering or anything like that? Changing the settings in nvidia-settings do nothing.

Also what function is the Top-Right corner activating by default? Where it shows all the windows on any face of the cube? I've been looking for like 15 minutes and can't figure out what it's called.

Thanks.

---

### Post by phssthpok on 2007-07-09
I'm having 2 issues:

(1) "metacity --replace" just locks up my computer and I have to hard reset. Sometimes metacity will spit out this error:

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager error: Unable to open X display 


(2) ccsm brings up the config utility but it's just a blank page.

Thanks for any help.

---

### Post by marx2k on 2007-07-09
I wonder if anyone else is having this issue when compiz starts..

when typing 'compiz --replace &' in the terminal, compiz starts fine and the debug information along with 
```

...
Initializing decoration options...done
Initializing move options...done
Initializing place options...done
Initializing resize options...done
Initializing svg options...done
[COLOR="Red"]/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format[/COLOR]
Initializing video options...done
Initializing wobbly options...done
Initializing animation options...done
Initializing imgjpeg options...done
Initializing ring options...done
Initializing thumbnail options...done
...

```

I am wondering what that warning is about?

Obviously this has to do with the 'Enable Video Playback' plugin 


When I disable/reenable the plugin, in terminal debug I get 
```

Active Plugin List update
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Does anyone know how this can be fixed or even if it is important? Im not sure what it does but I'd like to see compiz running smoothly upon firing so I can get it out of the way and continue evaluation.

---

### Post by marx2k on 2007-07-09
Also, can someone explain the flood of 

```

A handler is already registered for the path starting with path[0] = "org"

```

---

### Post by madrano on 2007-07-10
> **sambehera said:**
> im having problems getting this to work...

```
buzz@buzz-station:~$ sudo apt-get -y install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-kconfig
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
```

where can i find compizconfig-settings-manager??

im running kubuntu feisty amd64


same problem, please help

---

### Post by marx2k on 2007-07-10
And one more question on debug output...

When I start emerald, 

```

(emerald:30197): Wnck-WARNING **: Unhandled action type (nil)

```

Any takers?

---

### Post by trinaryouroboros on 2007-07-10
> **madrano said:**
> same problem, please help

You guys have the deb line in your /etc/apt/sources.list for download.tuxfamily.org/3v1n0 set to eyecandy-amd64?

---

### Post by ericdegen on 2007-07-10
Thanks for the How-to, up and running on my very finicky ATI X1600 Mobile.  

In fact this Compiz Fusion alpha is more solid then the Beryl I was running - Cheers!

---

### Post by ant1060 on 2007-07-12
Hi all :

I followed your HOW TO and am absolutely delighted with Compiz Fusion!  I couldn't believe my eyes when I saw what it can do, so a huge thank you to all you people who put so much time into this for our enjoyment! WAOW :):):)

I hesitated for a long time before installing (I did not have Beryl or Compiz before) - I am not that expert with Linux / computers, but all went well, and I was able to find out everything I needed to know except :

1) I cannot find a list of keystrokes to make the various effects work - everyone else seems to know this instinctively, probably from Beryl.... Can someone point me in the right direction?

2) I would like to switch on 'Mouse Gestures' but cannot figure this out at all... Anyone?

Again, thanks so much, this is sooooooooo great!
Ant (Brussels)

---

### Post by jpidrovo on 2007-07-12
hi I just had a problem with Compiz fusion :
I installed It was running superb 
But the I download and install the unofficial plugins and when I choose that option: desktop paint or something like that. the screen froze ... I restarted the system but the after login the screen is just in blank 
Help me please ... 
How can I uninstall compiz-fusion fom the recovery mode 
what commands shoul I write ... 
please I really need this 
thank you for your time

---

### Post by marx2k on 2007-07-12
Couple more issues Ive discovered. One of them, I think someone here has posted about is that when getting into Gnome, the Gnome loading screen doesnt go away for a while. Eventually it does if I switch to another desktop or possibly move a window over it.  After installing compiz fusion, booting into gnome is a hit or miss thing.

The other thing is Cube Rotation.  Sometimes it refuses to rotate using hotkeys (CTRL+ALT+mouse) until I run ccsm - I could just run ccsm and then close it and it will be fine but for some reason, no cube rotation until that happens.  Also, the cube WILL rotate upon mouse-on-edge-of-screen but not via hotkeys.  Not sure what could cause that and it's difficult to reproduce as it happens randomly but it DOES happen every day

---

### Post by ev5unleash1 on 2007-07-12
When I try to start compiz with this in terminal compiz --replace. It says can not run in VESA or VGA drivers. What should I do.

I think I know mt Graphics rendering had been disabled when I installed Ubuntu Studio 7,04 Fiesty. But I don't know how to reenable them. Even if this is not the problem can you tell me what I type in the terminal to reenable this.

---

### Post by trinaryouroboros on 2007-07-13
> **ev5unleash1 said:**
> When I try to start compiz with this in terminal compiz --replace. It says can not run in VESA or VGA drivers. What should I do.

I think I know mt Graphics rendering had been disabled when I installed Ubuntu Studio 7,04 Fiesty. But I don't know how to reenable them. Even if this is not the problem can you tell me what I type in the terminal to reenable this.

This depends on the type of graphics card you're using.

Use the graphics card section here to install the correct drivers for your card:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)

---

### Post by trinaryouroboros on 2007-07-13
> **jpidrovo said:**
> hi I just had a problem with Compiz fusion :
I installed It was running superb 
But the I download and install the unofficial plugins and when I choose that option: desktop paint or something like that. the screen froze ... I restarted the system but the after login the screen is just in blank 
Help me please ... 
How can I uninstall compiz-fusion fom the recovery mode 
what commands shoul I write ... 
please I really need this 
thank you for your time

If you can get to a shell (like CTRL-ALT-F2 or something) you should be able to run this:

```
sudo killall compiz
```

That will kill compiz, and you might see your normal desktop back on Screen0 by hitting CTRL-ALT-F1

From there you could obviously go through Synaptic Package manager, or whatever you were using previously to remove/reinstall Compiz Fusion.

Otherwise, if it's easier for you just to remove the program:

```
sudo apt-get remove compiz
```

(note: you might have to remove other components as well, that were listed in this how-to)

Then just:

```
sudo reboot now
```

---

### Post by CyberAngel on 2007-07-17
> **blackdevil said:**
> well, I followed instructions. Didnt work. Deleted and reinstalled, didnt work. After typing in 'compiz --replace -c emerald &' I get the following:

blackdevil@Daedalus:~$ compiz --replace -c emerald &
[1] 7306
blackdevil@Daedalus:~$ /usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

Some things work like transparency, but nothing else. Windo w decorations also dissapear. Somewhat boggling. Beryl was running quite good.

Same behavior here.... Only transparency works :(

```
$ compiz --replace -c emerald
Checking for Xgl: not present.
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Converting gconf plugin list: ''
Checking for nVidia: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070709 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

```

Any solution?

I am on amd64...

---

### Post by Deco_21 on 2007-07-17
This is your problem "Checking for Xgl: not present." you dont have xgl session.


You must have a  beryl session working if you want to get Compiz Fusion works. Try first 

beryl-manager --no-force-window-manager 

then 

compiz --replace --c emerald &

in the terminal.

---

### Post by GaryParr on 2007-07-17
First off, this thread has been great and many thanks for the how-to. Just wanted to add my 2 cents worth. I've managed to get compiz fusion working on an nvidia card (sony laptop) with dual display (docking station) inside an XGL session with twinview working correctly (maximized windows are on one display). I started with this how-to and then upgraded to the nvidia-xgl-new driver. I took the twinview setting for xorg.conf generated by nvidia-settings and added the following to the Device section

[INDENT]Option   "XAANoOffscreenPixmaps"   "true"
Option   "AllowGLXWithComposite"   "true"
Option   "TripleBuffer"   "true"
Option   "DisableGLXRootClipping"	"true"[/INDENT]

then added the following to the Screen section

[INDENT]Option         "AddARGBGLXVisuals" "True"[/INDENT]

finally added 

[INDENT]Section   "Extensions"
   Option   "Composite"   "Enable"
EndSection[/INDENT]

And then (this is the KICKER) I modified the xgl startup command to be this:

[INDENT] Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer +xinerama &[/INDENT]

I then run compiz from a menu launcher with

[INDENT]compiz --replace -c emerald[/INDENT]

After this, everything works like a chimp. I undock and restart X and I'm back to one solid screen. I throw 'er back in the docking station, restart X and I'm sitting pretty in a dual display. Compiz works like a dream and the XGL session removes the need for running compiz with the --indirect-rendering flag I had to use in a normal X session.

---

### Post by CyberAngel on 2007-07-18
> **Deco_21 said:**
> This is your problem "Checking for Xgl: not present." you dont have xgl session.


You must have a  beryl session working if you want to get Compiz Fusion works. Try first 

beryl-manager --no-force-window-manager 

then 

compiz --replace --c emerald &

in the terminal.

No this is not the problem....
if you see below that line it has:
```
Checking for nVidia: present.
```

Except that I was using Compiz Fusion before :)

Today it is working again after some upgrades so it was obviously the packages for amd64 broken :)

Anyway thanks for the reply ;)

---

### Post by Depressed Man on 2007-07-19
Edit: Fixed it now. I had to readd "dri" to the modules (for some odd reason it was removed).

---

### Post by xcalibur32 on 2007-07-20
I re-installed feisty. Updated fglrx. Then i installed compiz fusion n later xgl. when I type compiz --replace. I get

Backend     : ini
Integration : true
Profile     : default
Adding plugin scalefilter (scalefilter)
Adding plugin 3d (3d)
Adding plugin svg (svg)
Adding plugin fade (fade)
Adding plugin minimize (minimize)
Adding plugin keybinding (keybinding)
Adding plugin expo (expo)
Adding plugin wobbly (wobbly)
Adding plugin switcher (switcher)
Adding plugin crashhandler (crashhandler)
Adding plugin move (move)
Adding plugin colorfilter (colorfilter)
Adding plugin snow (snow)
Adding plugin reflex (reflex)
Adding plugin atlantis (atlantis)
Adding plugin bench (bench)
Adding plugin workarounds (workarounds)
Adding plugin flash (flash)
Adding plugin cheatsheet (cheatsheet)
Adding plugin firepaint (firepaint)
Adding plugin imgjpeg (imgjpeg)
Adding plugin snap (snap)
Adding plugin scaleaddon (scaleaddon)
Adding plugin addhelper (addhelper)
Adding plugin mousegestures (mousegestures)
Adding plugin put (put)
Adding plugin place (place)
Adding plugin cube (cube)
Adding plugin zoom (zoom)
Adding plugin text (text)
Adding plugin water (water)
Adding plugin kiosk (kiosk)
Adding plugin quickchange (quickchange)
Adding plugin annotate (annotate)
Adding plugin screensaver (screensaver)
Adding plugin video (video)
Adding plugin wall (wall)
Adding plugin tile (tile)
Adding plugin vpswitch (vpswitch)
Adding plugin inotify (inotify)
Adding plugin dbus (dbus)
Adding plugin widget (widget)
Adding plugin fadedesktop (fadedesktop)
Adding plugin png (png)
Adding core settings (General Options)
Adding plugin cubereflex (cubereflex)
Adding plugin opacify (opacify)
Adding plugin decoration (decoration)
Adding plugin splash (splash)
Adding plugin glib (glib)
Adding plugin wallpaper (wallpaper)
Adding plugin screenshot (screenshot)
Adding plugin thumbnail (thumbnail)
Adding plugin animation (animation)
Adding plugin clone (clone)
Adding plugin rotate (rotate)
Adding plugin group (group)
Adding plugin resize (resize)
Adding plugin blur (blur)
Adding plugin scale (scale)
Adding plugin regex (regex)
Adding plugin gotovp (gotovp)
Adding plugin showdesktop (showdesktop)
Adding plugin plane (plane)
Adding plugin resizeinfo (resizeinfo)
Adding plugin fakeargb (fakeargb)
Adding plugin ring (ring)
Adding plugin extrawm (extrawm)
Adding plugin notification (notification)
Adding plugin neg (neg)
Adding plugin winrules (winrules)
Adding plugin fs (fs)
Adding plugin trailfocus (trailfocus)
Adding plugin mblur (mblur)
Initializing core options...done
Initializing 3d options...done
Initializing minimize options...done
Initializing move options...done
Initializing imgjpeg options...done
Initializing place options...done
Initializing zoom options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing decoration options...done
Initializing splash options...done
Initializing resize options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing scale options...done
Initializing switcher options...done
Initializing atlantis options...done



If I type ctrl+x i get back the command prompt and the compiz seizes to work.. 

Is there a fix. ALso I have not installed beryl? Any suggestions?

Thanks

---

### Post by Adler on 2007-07-22
Hi All,

Apparently, there has been a great deal of work done here, but I **still** loose my Windows Decorator when I launch Fusion. 

Basically, when I launch Fusion / Emerald from either Terminal, or ALT + F2 Fusion works, but I loose everything, and Terminal goes to a "White Screen". I have tried all the commands listed here! Several times. Plus, have gone through all the repos possible, plus posts in other Forums.

Why don't we have a basic "Fusion" Window Decorator, rather than fighting with Emerald? 

Here's what happens when I run compiz --replace -c emerald & in Terminal:

jjmacey@jjm-laptop:~$ compiz --replace -c emerald &
[1] 7023
jjmacey@jjm-laptop:~$ Backend     : ini
Integration : true
Profile     : default
Adding plugin extrawm (extrawm)
Adding plugin bench (bench)
Adding plugin tile (tile)
Adding plugin imgjpeg (imgjpeg)
Adding plugin put (put)
Adding plugin atlantis (atlantis)
Adding plugin wall (wall)
Adding plugin snap (snap)
Adding plugin move (move)
Adding plugin trailfocus (trailfocus)
Adding plugin wobbly (wobbly)
Adding plugin opacify (opacify)
Adding plugin fs (fs)
Adding plugin vpswitch (vpswitch)
Adding plugin addhelper (addhelper)
Adding plugin snow (snow)
Adding plugin mblur (mblur)
Adding plugin regex (regex)
Adding plugin fadedesktop (fadedesktop)
Adding core settings (General Options)
Adding plugin cheatsheet (cheatsheet)
Adding plugin splash (splash)
Adding plugin fakeargb (fakeargb)
Adding plugin switcher (switcher)
Adding plugin 3d (3d)
Adding plugin png (png)
Adding plugin wallpaper (wallpaper)
Adding plugin water (water)
Adding plugin decoration (decoration)
Adding plugin gotovp (gotovp)
Adding plugin blur (blur)
Adding plugin cubereflex (cubereflex)
Adding plugin clone (clone)
Adding plugin dbus (dbus)
Adding plugin quickchange (quickchange)
Adding plugin showdesktop (showdesktop)
Adding plugin resizeinfo (resizeinfo)
Adding plugin annotate (annotate)
Adding plugin mousegestures (mousegestures)
Adding plugin fade (fade)
Adding plugin plane (plane)
Adding plugin colorfilter (colorfilter)
Adding plugin screenshot (screenshot)
Adding plugin scalefilter (scalefilter)
Adding plugin workarounds (workarounds)
Adding plugin rotate (rotate)
Adding plugin video (video)
Adding plugin reflex (reflex)
Adding plugin resize (resize)
Adding plugin zoom (zoom)
Adding plugin neg (neg)
Adding plugin flash (flash)
Adding plugin inotify (inotify)
Adding plugin text (text)
Adding plugin crashhandler (crashhandler)
Adding plugin group (group)
Adding plugin cube (cube)
Adding plugin thumbnail (thumbnail)
Adding plugin widget (widget)
Adding plugin winrules (winrules)
Adding plugin glib (glib)
Adding plugin kiosk (kiosk)
Adding plugin ring (ring)
Adding plugin keybinding (keybinding)
Adding plugin scaleaddon (scaleaddon)
Adding plugin expo (expo)
Adding plugin screensaver (screensaver)
Adding plugin notification (notification)
Adding plugin place (place)
Adding plugin scale (scale)
Adding plugin svg (svg)
Adding plugin minimize (minimize)
Adding plugin firepaint (firepaint)
Adding plugin animation (animation)
Initializing core options...done
Initializing imgjpeg options...done
Initializing move options...done
Initializing snow options...done
Initializing mblur options...done
Initializing cheatsheet options...done
Initializing 3d options...done
Initializing water options...done
Initializing decoration options...done
/usr/bin/compiz.real (blur) - Warn: No stencil buffer. Region based blur disabled
Initializing blur options...done
Initializing clone options...done
Initializing quickchange options...done
Initializing showdesktop options...done
Initializing mousegestures options...done
Initializing screenshot options...done
Initializing workarounds options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing resize options...done
Initializing zoom options...done
Initializing flash options...done
Initializing crashhandler options...done
Initializing thumbnail options...done
Initializing winrules options...done
Initializing place options...done
Initializing svg options...done
Initializing firepaint options...done
Initializing animation options...done
Initializing snap options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing widget options...done
Initializing expo options...done
Initializing screensaver options...done
Initializing scale options...done
Initializing switcher options...done
Initializing wallpaper options...done
Initializing rotate options...done
Initializing cubereflex options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

I do have everything working regarding those Desk Top effects -- I ran Beryl very well -- but loosing my Windows Decorator is really a pain in the butt!

Any Help?

Adler

Edit -- I've not seen any updates in the past week or so. Are the repos still up-dating?

---

### Post by trinaryouroboros on 2007-07-23
Alrighty, again, open up Synaptic Package Manager, search for Beryl, and remove beryl and it's decorator libraries/etc. - also remove Emerald (you can just do: sudo apt-get remove emerald )

The following is for 64-bit users Only:

If you are using 64-bit Feisty Fawn, open up your /etc/apt/sources.list and make sure the line for Trevino's "eyecandy" is not set to "eyecandy" but actually "eyecandy-amd64"

Then proceed to do this in terminal:

```
sudo apt-get remove compiz emerald emerald-themes
```

Then start from the beginning of the how to, and make sure you do:

```
sudo apt-get install emerald emerald-themes
```

At the very end, and add the following two applications to your System -> Preferences -> Session -> Startup:

```
Name: Compiz Fusion
Launcher: compiz --replace

Name: Emerald
Launcher: emerald --replace
```

I -just- had to fix my friends 64-bit compiz fusion setup this weekend, and he -also- completely missed the steps above...

:lolflag:

---

### Post by DaveTheAve on 2007-07-23
I'm getting a weird error too (Feisty x64):

> 
david@David-laptop:~$ compiz --replace &
[1] 7092
david@David-laptop:~$ Backend     : kconfig
Integration : true
Profile     : default
Adding plugin resize (resize)
Adding plugin move (move)
Adding plugin scale (scale)
Adding plugin place (place)
Adding plugin svg (svg)
Adding plugin fade (fade)
Adding plugin inotify (inotify)
Adding plugin glib (glib)
Adding plugin wobbly (wobbly)
Adding plugin video (video)
Adding plugin decoration (decoration)
Adding plugin minimize (minimize)
Adding plugin water (water)
Adding plugin annotate (annotate)
Adding plugin zoom (zoom)
Adding plugin dbus (dbus)
Adding plugin cube (cube)
Adding plugin plane (plane)
Adding plugin switcher (switcher)
Adding plugin blur (blur)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin rotate (rotate)
Adding plugin fs (fs)
Adding plugin screenshot (screenshot)
Adding core settings (General Options)
Adding plugin clone (clone)
Adding plugin named inputzoom
Adding plugin named snow
Adding plugin named neg
Adding plugin named group
Adding plugin named bs
Adding plugin named showdesktop
Adding plugin named 3d
Adding plugin named opacify
Adding plugin named widget
Adding plugin named put
Adding plugin named border
Adding plugin named wallpaper
Adding plugin named mousegestures
Adding plugin named state
Adding plugin named trailfocus
Adding plugin named bench
Initializing core options...done
Initializing resize options...done
Initializing move options...done
Initializing place options...done
Initializing svg options...done
david@David-laptop:~$ Initializing decoration options...done
Initializing minimize options...done
Initializing water options...done
Initializing zoom options...done
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (blur) - Warn: No stencil buffer. Region based blur disabled
Initializing blur options...done
fuse: failed to exec fusermount: Permission denied
Initializing fs options...done
/usr/bin/compiz: line 777:  7304 Segmentation fault      (core dumped) $*


---

### Post by Adler on 2007-07-23
trinaryouroboros,

I keep going through this, and thanks for your suggestions!

Still, I've no Emerald Window Decorator, or better put no Window Decorator at all when I boot. Fusion effects work, but still if I launch Terminal I only get a white square.

I have to be so close!

Adler

---

### Post by Likenota on 2007-07-25
umm i cant boot in unbuntu because the compiz-fusion freezes... any ideas guyS? how do i go about booting in terminal and doing the metacity replace or whatever to change it to the beryl theme or defaults..

---

### Post by linuxuser/palmprogrammer on 2007-07-27
*It will also be pre-installed with Ubuntu 7.10 (Gutsy Gibbon) .*

Really? They why bother with all of this?

Ill just wait (till october?)!

---

### Post by vexorian on 2007-07-27
why bother? well some people like cool stuff as fast as possible.

Of course, some other people might prefer something more stable, fusion is not recommended for them (although I have not experienced issues, it is still alpha so I wouldn't recommend it to anyone...)

---

### Post by Adler on 2007-07-27
> why bother? well some people like cool stuff as fast as possible.

vexorian,

I agree. I could not give up until I had compiz-fusion, and my Emerald themes running. 

All, sooo, sooo cool! You gotta love it!

Free the Fish @ [http://www.youtube.com/watch?v=jXXupyTjpDA](http://www.youtube.com/watch?v=jXXupyTjpDA)

Adler

---

### Post by Likenota on 2007-07-29
> **Likenota said:**
> umm i cant boot in unbuntu because the compiz-fusion freezes... any ideas guyS? how do i go about booting in terminal and doing the metacity replace or whatever to change it to the beryl theme or defaults..

okay like i asked before... please help me out and dont just disregard the messages made by me i am not a noob and id like to know how to fix this issue. i cant even boot into ubuntu without fixing it. so im stuck with boring xp.

---

### Post by egon2020 on 2007-07-29
> **Matteran said:**
> 
Also what function is the Top-Right corner activating by default? Where it shows all the windows on any face of the cube? I've been looking for like 15 minutes and can't figure out what it's called.


Did anyone ever find out what this is? It is SO IRRITATING. I would love to disable it.

---

### Post by vexorian on 2007-07-30
I think it is a bug that makes the window picker active even when it is disabled, and it is disabled by default.

---

### Post by weblordpepe on 2007-07-30
It aint a bug, silly bum. There's a gestures plugin as well as the expose` plugin thingie.

---

### Post by vexorian on 2007-08-01
I have disabled all the plugins yet still moving the mouse to the upper right corner will show a window switcher.

---

### Post by Atreus12 on 2007-08-02
I guess I am a little bit behind the times, as I just now installed compiz fusion. I had never had fast enough hardware to run it until I borrowed my sisters laptop.

My question is: compiz seems to be running a little...laggy. When I do the cube, or other such actions, the display...lags. Now, normally I would write this off as 'hardware not fast enough', but when I booted to PCLinuxOS 2007 live cd beryl ran flawlessly, and VERY fast.

So why is my compiz fusion on Ubuntu 7.04 so much slower than the live cd of PSLOS?

There was an option on the first post about "windows not moving as smoothly", is this what I want? Windows seem to be moving around just fine, but the video lags badly when I rotate the cube...etc.

Advice?

-Andrew

Edit: I have no restricted drivers to install.

---

### Post by Adler on 2007-08-02
> I guess I am a little bit behind the times

Atreus12,

No, you are not behind the times. If you ran Beryl well, you are ahead of the times e.g. M$ or Mac!

I do run compiz-fusion (Fusion), but every time I re-boot my notebook I have to hit ALT + F2 then add "emerald --replace" to get my Emerald Themes back. This despite having added "Emerald / emerald --replace" to my start up manager. 

Trying to add "Splash Screen" via the CompizConfig Settings Manager still freezes my PC. I can't complain though because I do see some marginal improvements versus Beryl.  The big issue as far as I can tell is with the Windows Manager e.g. getting themes to work with Fusion

Regarding your Video card, if you have installed the latest driver (ATI or NVIDIA) via whatever app you've chosen -- perhaps ENVY, you should be good to go! But, have only run into issues related to Fusion still not being the complete "out of the box" Beryl replacement that we had hoped for.

Until now, there have been some Distros that offer Beryl *out of the box*. I run Linux Mint Cassandra, but then went to Fusion with a bunch of hacks. As I mentioned all is not yet perfect.

As I understand it the next version of Ubuntu, due in October, will have solved all your issues.

I'm not sure that I've helped you here, but just giving you my set of experiences with Fusion.

Adler

---

### Post by HeavyAl on 2007-08-03
> **Atreus12 said:**
> I guess I am a little bit behind the times, as I just now installed compiz fusion

......

Advice?
.

What hardware are you actually running on? Video card specs? What kind of framerates does glxgears give you? These would be good things to know to start with.

Also, if you have CompizConfig installed you can change the texture filter under the general settings section (general/display settings) to 'fast' which might improve performance. There are a dozen or so other settings under the general section that you might adjust or turn off to get better performance.

---

### Post by Atreus12 on 2007-08-03
How do I check video card specs and cpu clock speed from the cli?

The computer is a Dell Inspiron 600m w/ 512 mb ram and a Pentium 'M' processor. I believe that it is the intel integrated video card, but I'm not sure.

The point is, the computer ran Beryl very fast without any lag on the PCLinuxOS 2007 live cd. It runs compiz-fusion rather slowly on Ubuntu 7.04. I'm wondering if there is a way to correct this. Specifically:

glxgears: 910 fps

Question #2
Video does not work. When try to play a video, it displays for a split second, and then just shows a black screen where the video should be. Sound still plays fine. I have 'video play' mode (or whatever) it's called turned on in compiz, but I tried it with it turned off and it made no difference. ... ideas?

-Andrew

**Edit: Both were fixed, see below**

---

### Post by mgmiller on 2007-08-03
> Question #2
Video does not work. When try to play a video, it displays for a split second, and then just shows a black screen where the video should be. Sound still plays fine. I have 'video play' mode (or whatever it's called turned on in compiz, but I tried it with it turned off and it made no difference. ... ideas?

-Andrew

I had the same problem.  I found I had to change the default video settings for my players.
Each uses a different command.

This should help:
[http://ubuntuforums.org/showthread.php?t=485410&highlight=totem+video+command]("http://ubuntuforums.org/showthread.php?t=485410&highlight=totem+video+command")

---

### Post by Adler on 2007-08-03
Hi All,

Where's the original Author at?

I'm running Fusion fine with all the little issues, but it runs well for me. 

Hey, this thread is only a **third** the length of getting an ATI device going w/ UBUNTU. Not to complain, but things are pretty good w/ Linux.

Adler

---

### Post by Atreus12 on 2007-08-04
> **mgmiller said:**
> I had the same problem.  I found I had to change the default video settings for my players.
Each uses a different command.

This should help:
[http://ubuntuforums.org/showthread.php?t=485410&highlight=totem+video+command]("http://ubuntuforums.org/showthread.php?t=485410&highlight=totem+video+command")

**AWESOME**

It worked. Plus, I turned the 'texture filter' to fast, and now it's running fast!

This inspiron 600m has to be my most successful install yet. Wireless works out of the box, video card works out of the box....with compiz-fusion no less!

-Andrew

---

### Post by Ub1476 on 2007-08-08
nvm

---

### Post by Chymera on 2007-08-13
> sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!

it says it can't find the files

---

### Post by Chymera on 2007-08-13
c'mon ppl im trying to get compiz fusion installed for over 2 hours.... even some hint would be apreciated...

---

### Post by Chymera on 2007-08-13
solved.... you might want to note that some ppl's comps have 64bit architecture

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64

---

### Post by whoosh on 2007-08-13
Sorry, I'm pretty new to this stuff but I'm getting an error when I do 

```
sudo apt-get remove compiz-core desktop-effects
```

It says 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  compiz-plugins: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  ubuntu-desktop: Depends: desktop-effects but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

and when I run sudo apt-get -f install I get

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  beryl-settings-bindings libberylsettings0 libemeraldengine0
  beryl-plugins-data libberyldecoration0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
Need to get 0B/170kB of archives.
After unpacking 1323kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 108036 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone have any idea?

Edit: NVm I figured it out ;D

---

### Post by bruckwine on 2007-08-13
> **weblordpepe said:**
> It aint a bug, silly bum. There's a gestures plugin as well as the expose` plugin thingie.

Correcto - had me buggin at first..same with the top-left..panes plugin....

Hope trevinho updates his repo soon as I'm too scared to try amaranth's way just yet!

---

### Post by sm32589g on 2007-08-13
can u make it rain and snow in compiz fusion? or just snow?

---

### Post by 5h4rk on 2007-08-17
How do I know what version of CF I'm running?

---

### Post by Dark Star on 2007-08-17
Plz post relevant heading :) btw ```
aptitude show compiz
``` in terminal :D

---

### Post by Adler on 2007-08-17
Dark Star,

**Cool!**

I just ran it, and found that I'm @ Version: 1:0.5.1+git20070730~3v1ubuntu0.

*Everything* works, but I'm now curious. Is there a later version out there? I *did* see something that CF had just gone final, but not sure my repositories are picking this up.

Adler

---

### Post by satkata on 2007-08-17
The repository provided by trevino is not up-to-date, because he is having a vacation or something like that. There was a post about that on this forum.

If you can't wait till he is back, you could switch to the new updated repo.

For further information look here:
[http://ubuntuforums.org/showthread.php?t=481314]("http://ubuntuforums.org/showthread.php?t=481314")

---

### Post by Adler on 2007-08-19
satkata,

There was an update today of the repository, and I am now running - 

1:0.5.3~git20070817+3v1ubuntu0.

I've now finally got the Splash screen working. However, I'm noticing some of my usual key stroke commands no longer function, and have to go through CompizConfig Settings Manager to see what  now does what. LOL!

Adler

---

### Post by fakie_flip on 2007-08-19
sdfs

---

### Post by fakie_flip on 2007-08-19
sorry, double post

---

### Post by fakie_flip on 2007-08-19
Could someone explain why this is not working?

```
[COLOR="Red"]chris@ubuntu:~$ tail /etc/apt/sources.list[/COLOR]

deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb [http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu) feisty/
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe

[COLOR="Blue"]# compiz-fusion
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy[/COLOR]
[COLOR="Red"]chris@ubuntu:~$ sudo wget [/COLOR]http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
--20:18:32--  [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... failed: Connection refused.
gpg: no valid OpenPGP data found.
chris@ubuntu:~$ sudo apt-get update[COLOR="Blue"]Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg                           
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)[/COLOR]
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) feisty/ Release.gpg                                  
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) feisty/ Translation-en_US                            
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release.gpg                                
Get:1 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US            
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US              
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Translation-en_US                 
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) feisty/ Release                                      
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Get:6 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]                
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release                                    
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) feisty/ Packages                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                          
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) feisty/ Packages                                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                          
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Fetched 198B in 4s (45B/s)
[COLOR="Blue"]Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/Release.gpg](http://download.tuxfamily.org/3v1deb/dists/feisty/Release.gpg)  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/i18n/Translation-en_US.bz2](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/i18n/Translation-en_US.bz2)  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)[/COLOR]
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
chris@ubuntu:~$
```

---

### Post by GFree678 on 2007-08-19
> **fakie_flip said:**
> Could someone explain why this is not working?
See for yourself: root repository - [http://download.tuxfamily.org](http://download.tuxfamily.org)

Currently dead.

---

### Post by fakie_flip on 2007-08-19
> **GFree678 said:**
> See for yourself: root repository - [http://download.tuxfamily.org](http://download.tuxfamily.org)

Currently dead.

Dead why? Is it discontinued?

---

### Post by GFree678 on 2007-08-19
> **fakie_flip said:**
> Dead why? Is it discontinued?
I figure since the packages in Trevinos' repo are currently having problems on many systems, maybe he's taken the site down to avoid messing up anyone else until the problems are fixed.

---

### Post by Adler on 2007-08-19
> I figure since the packages in Trevinos' repo are currently having problems on many systems, maybe he's taken the site down to avoid messing up anyone else until the problems are fixed.

GFree678,

I think that you are right here. I up-dated my system earlier today, and I've run into some issues, but it hasn't crashed my pc. Although I've not really heard of any one having such issues.

Adler

---

### Post by fakie_flip on 2007-08-20
> **Adler said:**
> GFree678,

I think that you are right here. I up-dated my system earlier today, and I've run into some issues, but it hasn't crashed my pc. Although I've not really heard of any one having such issues.

Adler

What is the recommended way to get compiz fusion then besides compiling?

---

### Post by Adler on 2007-08-20
fakie_flip,

I've seen things like this happen before, and I'm just going to wait until the next up-date.

Adler

---

### Post by munmon on 2007-08-20
Hello,

I did have all those non working plugins. The 3D windows not working and so on. What I did to make it work was, I simply remove everything. All compiz settings (I mean all of them, just like installing it for the first time).

then initiate the 

apt-get autoclean
apt-get clean.

Then simply reinstall. It works for me.

---

### Post by outphase on 2007-08-20
How can I set my custom keyboard shortcuts? The Actions tab seems to be missing now.

---

### Post by Adler on 2007-08-20
> How can I set my custom keyboard shortcuts? The Actions tab seems to be missing now.

outphase,

About 10 minutes ago I was in the Settings Manager looking for the same thing. They are no longer there.

However, I still can get Rain - <Shift><F9>, Snow with <Super><F3>. What I am really missing is getting the Desktop Cube. I used to be able to do that with <CTRL><ALT><Left Mouse Button><Touch Pad>. Now, it no longer functions.

I figure the next up-date will correct what went wrong in the repository. 

Adler

---

### Post by Parms on 2007-08-21
OK, Ive been looking through all the pages on here... I've got emerald and fusion working.. Cube and all. I can seem to set the theme. Is there a guide how to do this?

---

### Post by Adler on 2007-08-21
> I've got emerald and fusion working

Parms,

What are you using for a *Theme* right now?

Is it an Emerald Theme? If so, you just need to launch Emerald, and select a new theme or download a new one. If you are running GNOME, go to gnome-look.org. There's a large choice there.

If you are trying to get both working together you may have to add a few things to get it to boot right.

I myself use Linux Mint, and add things to Sessions.

However, the latest up-date broke a few things like getting CUBE going.

What version are you running?

The posts above will tell you how to do that.

Adler

---

### Post by tkboy85 on 2007-08-21
> **Parms said:**
> OK, Ive been looking through all the pages on here... I've got emerald and fusion working.. Cube and all. I can seem to set the theme. Is there a guide how to do this?

Did you run fusion with emerald?

```
compiz --replace -c emerald
```

I installed compiz fusion, then installed emerald theme manager. Then I ran the above and I got both working (as in, I'm able to change themes etc.)

---

### Post by Adler on 2007-08-21
tkboy85,

You may have forgotten where to run

compiz --replace -c emerald

I've used ALT+F2.

Adler

---

### Post by tkboy85 on 2007-08-21
Yup, I forgot to put that in. I think I need more practice in writing complete instructions. Thanks! :)

---

### Post by Adler on 2007-08-21
tkboy85,

No problem from my side. 

It seems that compiz-Fusion might be a *little* bit broken right now.

I'm sure that a good deal of work is going on right now in the background. I've been through Beryl, and had to compile drivers to get my old Radeon XPress 200M card doing it all. That thread was 100 pages long!.

Those 3D Desktops are sooo... Cool. I've got a bunch of YouTube videos out there.

Sit back relax... Isn't the next UBUNTU to include Fusion?

Better things to come.

Adler

---

### Post by Adler on 2007-08-22
Hi All,

Am I right or wrong that the compiz-Fusion repositories are broken right now?

I've lost a good deal of functions after the latest up-grade e.g. the 3-d Cube keys no longer work.

In fact, the Settings Manager no longer lets me set key stroke commands.

Adler

---

### Post by Inxsible on 2007-08-23
yes, if you are using Trevinos repos, things have been a bit haywire. I tried using amaranths repos ..but they dont have all the plugins and now somebody suggested vorians repos. Trouble is, I am not sure which is stable and has all the plugins :)

tried to install from source, but it installs a bunch of kde crap which i dont want/need

guess i shall just wait, until trevino fixes the bugs.

---

### Post by munmon on 2007-08-23
Trevino's update his package already.

    compiz (0.5.3~git20070817+3v1ubuntu0 => 0.5.5~git20070820+3v1ubuntu0)
   compiz-core (0.5.3~git20070817+3v1ubuntu0 => 0.5.5~git20070820+3v1ubuntu0)

---

### Post by craigyjack on 2007-08-23
I can not find a place to change the binding for rotating the cube with the mouse. by default it is ctrl+alt+button1 on the mouse, but there is no place to change this binding now in compizconfig setting manager. can someone let me know how i can change the mouse binding so i can rotate my cube how i used to before all this updating madness. (i use a side mouse button [button5] or something to rotate cube) it worked fine before all this updating, but now idk how to change it.

also, whenever i turn on Expo plugin, it just turns right off. maybe i need to remove all my config files and reinstall trevino's packages and see if it fixes some stuff.

---

### Post by Adler on 2007-08-23
Hi All,

There have been two up-dates for me today, and *Bindings* is *back!*

[IMG]http://img137.imageshack.us/img137/5752/mintscreenshot22dy5.png[/IMG]

However, they don't seem to yet work.

I'm just hanging back waiting for more up-dates.

Adler

---

### Post by Inxsible on 2007-08-24
They work for me :)

---

### Post by tkboy85 on 2007-08-24
Hmm... the keys-bindings don't seem to be saved after closing CCSM. Maybe a conflict with previous installations? I'll try to purge and reinstall again later...

---

### Post by MarshallClan on 2007-08-24
Thanks Gentlemen!!! Great How-to. Working smoothly!

---

### Post by tkboy85 on 2007-08-24
Ok, I just got back. Did a full purge(including the removal of config files in home directory), then reinstalled the files. But changes to keybindings still don't stick. But thanks anyway for the updates! :)

[I]Edit: Yikes, now I can't even enable animations or another other plugin. Seems like whatever's enabled at default stays enabled, and whatever isn't stays disabled no matter how I select it. :(
Config files in home directory are both 0 bytes...[/I]

---

### Post by Adler on 2007-08-24
> Thanks Gentlemen!!! Great How-to. Working smoothly!

MarshallClan,

*You* have *everything* running?

There was new up-date running today.

I'm still stuck on stupid, as well as, others.

tkboy85,

*Yikes* is the right word. I'm hanging back and seeing what happens. There have been 4 up-dates in the last three days.

I've always found that when it is broken, and a few tricks don't work, it is really broken.

Adler

---

### Post by tkboy85 on 2007-08-25
Hey the new updates by Trevino seem to put everything back in order! I've gotta test it out somemore, but so far things look promising! :D

---

### Post by fettuohi on 2007-08-25
Can anybody get the the 3D and Atlantis plugins to work after the latest update from Trreviño (3v1n0)? I can't get them to start anymore since the repo was updated to using the 0.5.5svn.

Regards

André

---

### Post by BRILLtheTHRILL on 2007-08-25
i really just can't get this to work.
fireblend can you get on aim sometime or PM me?

---

### Post by Adler on 2007-08-25
> Can anybody get the the 3D and Atlantis plugins to work after the latest update from Trreviño (3v1n0)? 

fettuohi,

No luck from my side, but there was *another* up-date today. Obviously there is a lot going on here in the background.

Adler

---

### Post by bagguley on 2007-08-25
Awesome!!

Thanks guys

---

### Post by DoorGunner on 2007-08-25
Yep .... worked very nicely

I origionally had beryl installed and on initial start up i lost my windows decorator. I found that after i removed beryl and especially the ~/.beryl file that was left over and the beryl start scripts I initially installed my decorator came back.

---

### Post by Skorzen on 2007-08-25
I followed the tutorial but I maybe have done **** and now I don't have those close, minimize and maximize bars. Could someone help me to revert this?

EDIT - It's done, thanks.

---

### Post by walkerk on 2007-08-25
> **Adler said:**
> fettuohi,

No luck from my side, but there was *another* up-date today. Obviously there is a lot going on here in the background.

Adler

go into synaptic and remove the unofficial plugins/unsupported plugins.. and the re-install.. this should fix it..

---

### Post by Dark Star on 2007-08-26
```
shashwat@shashwat-desktop:~$ sudo gedit /etc/apt/sources.list
shashwat@shashwat-desktop:~$ sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
--16:26:32--  http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,180 (4.1K) [text/plain]

100%[====================================>] 4,180         15.40K/s             

16:26:33 (15.40 KB/s) - `-' saved [4180/4180]

OK
shashwat@shashwat-desktop:~$ sudo apt-get update
Get:1 http://download.tuxfamily.org feisty Release.gpg [189B]                  
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Get:2 http://download.tuxfamily.org feisty Release.gpg [189B]                  
Ign http://ppa.dogfood.launchpad.net feisty Release.gpg                        
Ign http://ppa.dogfood.launchpad.net feisty/main Translation-en_US             
Get:3 http://hendrik.kaju.pri.ee feisty Release.gpg [189B]                     
Ign http://hendrik.kaju.pri.ee feisty/screenlets Translation-en_US             
Get:4 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Get:5 http://in.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://in.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://ppa.dogfood.launchpad.net feisty/restricted Translation-en_US       
Ign http://ppa.dogfood.launchpad.net feisty/universe Translation-en_US         
Ign http://ppa.dogfood.launchpad.net feisty/multiverse Translation-en_US       
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Ign http://in.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://in.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://in.archive.ubuntu.com feisty/multiverse Translation-en_US           
Get:6 http://in.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://download.tuxfamily.org feisty/eyecandy Translation-en_US            
Ign http://in.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://in.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Hit http://download.tuxfamily.org feisty Release                               
Hit http://hendrik.kaju.pri.ee feisty Release                                  
Hit http://ppa.dogfood.launchpad.net feisty Release                            
Hit http://in.archive.ubuntu.com feisty Release                                
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://download.tuxfamily.org feisty Release                               
Hit http://in.archive.ubuntu.com feisty-updates Release                        
Ign http://ppa.dogfood.launchpad.net feisty/main Packages                      
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://hendrik.kaju.pri.ee feisty/screenlets Packages                      
Hit http://in.archive.ubuntu.com feisty/main Packages                          
Hit http://in.archive.ubuntu.com feisty/restricted Packages                    
Hit http://in.archive.ubuntu.com feisty/main Sources                           
Hit http://download.tuxfamily.org feisty/avant-window-navigator Packages       
Hit http://download.tuxfamily.org feisty/avant-window-navigator Sources        
Ign http://ppa.dogfood.launchpad.net feisty/restricted Packages                
Ign http://ppa.dogfood.launchpad.net feisty/universe Packages                  
Ign http://ppa.dogfood.launchpad.net feisty/multiverse Packages                
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://security.ubuntu.com feisty-security/restricted Sources              
Hit http://in.archive.ubuntu.com feisty/restricted Sources                     
Hit http://in.archive.ubuntu.com feisty/universe Packages                      
Hit http://in.archive.ubuntu.com feisty/universe Sources                       
Hit http://in.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://in.archive.ubuntu.com feisty/multiverse Sources                     
Hit http://in.archive.ubuntu.com feisty-updates/main Packages                  
Hit http://in.archive.ubuntu.com feisty-updates/restricted Packages            
Hit http://in.archive.ubuntu.com feisty-updates/main Sources                   
Ign http://ppa.dogfood.launchpad.net feisty/main Sources                       
Ign http://ppa.dogfood.launchpad.net feisty/restricted Sources                 
Ign http://ppa.dogfood.launchpad.net feisty/universe Sources                   
Ign http://ppa.dogfood.launchpad.net feisty/multiverse Sources                 
Hit http://download.tuxfamily.org feisty/eyecandy Packages                     
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://security.ubuntu.com feisty-security/universe Sources                
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://security.ubuntu.com feisty-security/multiverse Sources              
Hit http://download.tuxfamily.org feisty/eyecandy Sources                      
Hit http://in.archive.ubuntu.com feisty-updates/restricted Sources             
Hit http://ppa.dogfood.launchpad.net feisty/main Packages
Hit http://ppa.dogfood.launchpad.net feisty/restricted Packages
Hit http://ppa.dogfood.launchpad.net feisty/universe Packages
Hit http://ppa.dogfood.launchpad.net feisty/multiverse Packages
Hit http://ppa.dogfood.launchpad.net feisty/main Sources
Hit http://ppa.dogfood.launchpad.net feisty/restricted Sources
Hit http://ppa.dogfood.launchpad.net feisty/universe Sources
Hit http://ppa.dogfood.launchpad.net feisty/multiverse Sources
Fetched 6B in 2s (3B/s)  
Reading package lists... Done
shashwat@shashwat-desktop:~$ sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libemeraldengine0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-core compiz-gnome compiz-plugins
Recommended packages:
  compiz-fusion-plugins-main
The following NEW packages will be installed:
  compiz compiz-core compiz-gnome compiz-plugins
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 955kB of archives.
After unpacking 3908kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
shashwat@shashwat-desktop:~$ 

```




Plz see that the download fail after I press "Y" Plz help me :)

---

### Post by buildid on 2007-08-26
wel installed after that i have no windows borders , no minimise or maximize buttons , to solve this i did :

compiz --replace -c emerald 

as i read that, oke this works wel for me .

Now i see this message : /usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

is this important or not , can i ignore this ?

---

### Post by Dark Star on 2007-08-26
1'st of all I got my error solved :) and your problem . Open Compiz Manager press ALt+ F2 and type ccsm now under Effects Select Windows Decoration :) This will solve the problem ;)

---

### Post by rcatman on 2007-08-26
Awesome!! So, I am running an AMD Athlon 64 with an Nvidia Geforce4 Go 420 on a Compaq Presario R3000..... I had some problems initially getting compiz fusion up and running. The restricted drivers manager told me I had no need for restricted drivers but I went ahead and let Automatix install nvidia drivers for me.

Using the CF installer, I picked gnome and said no to the kde libraries. I chose to install the stable version not the git version.

When I clicked on the Compiz Icon in System->Tools nothing would show up. The same thing happened when I opened up Compiz Settings Manager from System->Preferences (No new window). So I found out that ccsm is the command for compiz's manager. I opened a terminal and typed ccsm to get something appear that said "compizconfig module not found".

I read extensively through about half this post and came to the idea that I should uninstall then reinstall. Also I thought "Why not try the more up-to-date git version?" 

Lo-behold, things work perfect. I have snow :) I didn't have that on my desktop w/Geforce3 Ti 200. I'm very very happy.  Now it's time to make every coffee shop person who takes a glance at my screen jealous and utter the words "What the?".

---

### Post by Adler on 2007-08-26
> go into synaptic and remove the unofficial plugins/unsupported plugins.. and the re-install.. this should fix it..

walkerk,

Thanks for the reply, but that didn't work.

The real issue that I have is that I can't get the 3D Cube. There was *another* up-date today, but that hasn't resolved the issue. 

Hey, I lived not too far away from you in Heusenstamm, Der Nabel der Welt.

Adler

---

### Post by Adler on 2007-08-26
Well,

I think that I might see the solution here, at least I *think*.

[IMG]http://img169.imageshack.us/img169/5325/mintscreenshot23km3.png[/IMG]

My Settings Manager from GIT (Trevino) seems to vary a good deal from what is in the official repos. 

I still can't initiate "Cube". Anybody have a suggestion for *Bindings*? It seems I keep being asked for a *button* to add should I want to edit the present setting, which does not work.

Adler

---

### Post by Dark Star on 2007-08-26
Alder Go to General Options under Desktop Size change Horizontal Virtual Size & no. of Desktops to 4 restart and tell the result ;)

---

### Post by Adler on 2007-08-26
Dark Star,

I did as you suggested, and when I jam my Mouse to the upper left I get this... Oh, that shows Expo...

[IMG]http://img81.imageshack.us/img81/9374/screenshot1kk6.png[/IMG]

Hmm...

Adler

PS -- *The Truth is out there to quote the X-Files*

---

### Post by Adler on 2007-08-26
Dark Star,

I found out that I had to change your suggestion a bit. CF *is* running in the background, but had no idea where to get it going. Thanks for that.

Here's what I did --

[IMG]http://img179.imageshack.us/img179/4381/mintscreenshot25lr3.png[/IMG]

I've got all that goodness back, and will do further work to get my 3D Cube looking good again.

[IMG]http://img403.imageshack.us/img403/4708/screenshot3jb4.png[/IMG]

Thanks for the help!

Adler

---

### Post by Dark Star on 2007-08-26
Pretty cool :D Now you have a 3d cube ;)

---

### Post by Aya Dream on 2007-08-28
This mini howto put me on the right track but I must confess to following the more recent instructions at  [http://forum.compiz-fusion.org/showthread.php?t=3679]("http://forum.compiz-fusion.org/showthread.php?t=3679") dated 27/08/2007. I followed the instructions exactly and (despite what the article says) I ended up with no windows borders and a white on white terminal window.

This was cured by going into System -> Preferences -> CompizConfig Settings Manager and deselecting the 'negative' option under Accessibility.

(Actually, somewhere along the line, I also installed the three additional packages referred to on page 1 of this mini howto).

This Compix-Fusion implementation was done on a relatively new install of Feisty 7.04 Linux 2.6.20-16 generic and very happy with it I am.

---

### Post by Aya Dream on 2007-08-28
Sorry previous post about deselecting 'negative' is utter rubbish. Please ignore.

Still got same problems of no window borders and whit on white terminal after re-boot

Happy, I am not!

---

### Post by MrGreen on 2007-08-28
Not managed to get CF working using either methods script or repo ... seems beryl will not load now as well 

Seen all the videos and screenshots but never thought it would be this difficult to install

---

### Post by bdoe on 2007-08-28
Well, I spent the better part of the day yesterday giving Compiz an honest try.  I first tried the method in [this thread]("http://ubuntuforums.org/showthread.php?t=488385"), using fglrx and XGL (I found XGL to be extremely unstable on my system.  It worked okay after a reboot, but severely corrupts the screen when logging out/logging in.  I suppose I could have fixed that by having X-server reset after every session, but my patience was very thin by this point).  I had considerable dependency issues when I tried installing compiz, and the config-manager could not be found, period.  

I then tried the script on this thread, and got more dependency issues (it turns out there were conflicts with files that had managed to get downloaded with unrelated packages from a different repository).  I finally got it installed, but nothing seemed to work right.  Windows were being drawn without decorations or titlebars, windows were getting stuck to the bottom panel, and when I did manage to get titlebars working, windows were opening up in such a way that their titlebars were underneath the top panel, making it impossible to move the window.  I tried changing settings in the config manager, but nothing was changing.  It was as if my settings weren't taking at all!  Finally, after yet another screen corruption, I dumped the fglrx/XGL setup and went back to the mesa radeon drivers with AIGLX.  This fixed the screen corruption issues, but I was still left with an unresponsive Compiz config manager and disappearing window decorations - and then, all of a sudden, my windows became stuck to the desktop and would not move or resize or anything.  I could minimize and maximize them, but that was it.  

So I uninstalled Compiz using the same script, and tried a third approach, using Amaranth's repository, using the steps in [this thread]("http://ubuntuforums.org/showthread.php?t=533476") - after I removed Trevino's repositories from sources.list.  The install went very smoothly, but - again - I had control panel that was not responding to enabling or disabling of plugins.  Only the general preferences seemed to respond with real-time changes.  And I still had unmovable windows.  I rebooted, the stuck window problem remained, and now Compiz was complaining about not finding any manageable screens!

This was the last straw.  I completely purged all things Compiz, reinstalled Beryl and Emerald, and all is well in the world again.  I guess Feisty just isn't ready for Compiz yet.

---

### Post by MrGreen on 2007-08-28
I have tried both script and repo method nothing .... I guess I will have to wait for Gutsy release

Now Beryl does not work ;-(

I clean a clean out all the eye candy script lol... man some of those screenshots do look cool

---

### Post by dorogavtsev on 2007-08-29
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

:( :( :( :( :( :( :(

---

### Post by Aya Dream on 2007-08-30
Ok, I'm on Feisty 7.04 Linux 2.6.20-16-generic using Compiz-Fusion 5.2 from [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) repository. Everything seems to be working well touch wood! System is an Asus P4V800D-X with Nvidia GeForce 6200 AGP and 3Gb RAM. I've installed Nvidia restricted graphics driver 9755.

A couple of questions:
1) I have a session auto-run at start-up with 'compiz --replace' and it works. I have also installed emerald, libemeraldengine0 (both 03~git20070717-0ubuntu1~ppa1) and emerald-themes (0.2.1-0ubuntu1). Do I need this last package? - it seems like wrong version number! Anyway, can I replace my startup run command of 'compiz --replace' with 'compiz --replace -c emerald &'
to start compiz-fusion with emerald themes? I only have original system themes at the moment.

2) Do I need to install xserver-xgl for emerald to work? I can see from Synaptic that I already have Xserver-xorg installed and some other info follows:

root@rwd-18082007c:/home/robert# glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
etc etc...

root@rwd-18082007c:/home/robert# glxinfo | grep texture_from_pixmap
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer,

**Edit:** Q1 'compiz --replace -c emerald &' didn't work for me. I had to set up 2 startup programs in Sessions: 1) 'compize --replace' and ii) 'emerald --replace'. Q2 No I don't need 'xserver-xgl' for emerald to work.
Thanks for all your help guys. Good job on the Mini-Howto

---

### Post by guernicaaa on 2007-08-30
Finally solved my border issue problem, but there are three things that are bugging me right now:
1.  I grab and hold the titlebar of a window to move it, but when I release the mouse button, it continues to "hold" the window and move it around.  I'm sure there's some sticky option that I'm missing.
2.  I used to be able to rotate the cube by using my middle (scroll wheel) button.  Again, probably another option that I'm just missing.
3.  Firefox shows up on every side of the cube, and it's the same firefox.  But no other programs do that.

Help with any of these would be greatly appreciated.

---

### Post by 5h4rk on 2007-08-30
this is weird, i dont know it happens only to me or not, but for the desktop cube, without background image, when i rotate it, it get very laggy, but when i add an background image, it get a little bit less laggy...

---

### Post by b0rka7a on 2007-08-30
```
boris@ubuntu-7:~/Desktop/Downloads/wine-0.9.44$ sudo apt-get remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be REMOVED:
  compiz compiz-core compiz-gtk compiz-plugins desktop-effects
  gnome-compiz-manager ubuntu-desktop
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 7 to remove and 17 not upgraded.
Need to get 161kB of archives.
After unpacking 3531kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
```

:confused:
If I remove ubuntu-desktop, I think I'm gonna wreck my Ubuntu.

My problem is actually my graphic card: ATI Radeon 9550. I installed the drivers from System ->  Administration -> Restricted Drivers Manager. After I did this I couldn't start Beryl or Compiz. Why ? Please help me ! :( I don't want to buy new NVidia card :(
Sorry for my English. I'm from Bulgaria....

---

### Post by Aya Dream on 2007-08-30
> If I remove ubuntu-desktop, I think I'm gonna wreck my Ubuntu.

Answer as per janbockaert & Vorian on page 2:

no, ubuntu-desktop is a meta package, removing one package from this meta-package, forces ubuntu-desktop to be removed (i 'm guessing desktop-effects is part of ubuntu-desktop). But every other package installed with ubuntu-desktop will still be installed.

Regarding installing CF with ATI card you may want to refer to the following thread:
[http://ubuntuforums.org/showthread.php?t=488385]("http://ubuntuforums.org/showthread.php?t=488385")

---

### Post by Rupertronco on 2007-08-30
> 

:confused:
If I remove ubuntu-desktop, I think I'm gonna wreck my Ubuntu.

My problem is actually my graphic card: ATI Radeon 9550. I installed the drivers from System ->  Administration -> Restricted Drivers Manager. After I did this I couldn't start Beryl or Compiz. Why ? Please help me ! :( I don't want to buy new NVidia card :(
Sorry for my English. I'm from Bulgaria....

Well you can certainly speak English better than I can speak any other language. You can remove the ubuntu-desktop package and then just re-install (sudo aptitude install ubuntu-desktop) after you ditch your compiz.

---

### Post by Adler on 2007-08-30
Guys,

What are you using for repositories?

Trevinos are back. And, I running CF very, very well. And, they are being up-dated.

I've noticed that CF will not be included in the next version of Ubuntu, and also not in the next release of the Linux distro that I presently run -- Linux Mint.

I guess it is too unstable for us. LOL!

Adler

---

### Post by bdoe on 2007-08-31
Heh...  You think maybe Sabayan will pick it up? :p

---

### Post by Adler on 2007-08-31
> Heh... You think maybe Sabayan will pick it up? 

I'm not sure. 

Adler

---

### Post by oni5115 on 2007-08-31
I just wanted to add a small note for those having the invisble window border issue.  If you don't have the Emerald packages installed, you can also try one of the following:
gtk-window-decorator --replace
kde-window-decorator --repace

I didn't like how Emerald used the 'wrap-up' feature on double clicking a title bar, and I could not find the options to change it.  I found the above mentioned on the open compositing forums, and it worked great for me.

---

### Post by tkboy85 on 2007-09-01
> **oni5115 said:**
> 
I didn't like how Emerald used the 'wrap-up' feature on double clicking a title bar, and I could not find the options to change it.  I found the above mentioned on the open compositing forums, and it worked great for me.

There's an option to change it in the Emerald Theme Manager. Go to the Emerald Settings tab, then look for Titlebar Double-Click Action. That is where you can change it from the default shade(wrap up as you call up) to the more common action of maximize/restore, or even to minimize.

---

### Post by The Pinny Parlour on 2007-09-01
.

---

### Post by The Pinny Parlour on 2007-09-01
How do start it?  I have it all installed.

---

### Post by phoochka on 2007-09-01
I just wanted to say nice work and thanks! 

I had a previous install of beryl/compiz which was surprisingly easy to remove. Currently enjoing ALL the pretty effects of compiz fusion on my Asus A6j laptop with the dreaded **ATI** x1600!

---

### Post by The Pinny Parlour on 2007-09-01
I get the following when I update using the update manager:

E: /var/cache/apt/archives/beryl-settings-simple_0.3.0+git20070320~3v1ubuntu2_i386.deb: trying to overwrite `/usr/share/beryl-settings-simple/level2.Profile', which is also in package beryl-defaults


Could anyone help?

Thank you.

---

### Post by The Pinny Parlour on 2007-09-01
Darn.

I followed this how-to and now nothing to do with beryl, compiz or compiz-fusion works.  

Thanks.  :mad::mad::mad::mad::mad::mad:

---

### Post by The Pinny Parlour on 2007-09-01
How do I totally remove all this desktop enhancement stuff so I can try again?

---

### Post by The Pinny Parlour on 2007-09-01
Will try this instead.
[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

---

### Post by Chronos6 on 2007-09-01
I have a kinda strange problem with mplayer and compiz.
The pictures are speaking instead of me:
[http://kep-feltoltes.hu/foto/xgl2.png-6577.html](http://kep-feltoltes.hu/foto/xgl2.png-6577.html)
[http://kep-feltoltes.hu/foto/mplayer.png-6578.html](http://kep-feltoltes.hu/foto/mplayer.png-6578.html)
Thanx

---

### Post by tkboy85 on 2007-09-02
> **Chronos6 said:**
> I have a kinda strange problem with mplayer and compiz.
The pictures are speaking instead of me:
[http://kep-feltoltes.hu/foto/xgl2.png-6577.html](http://kep-feltoltes.hu/foto/xgl2.png-6577.html)
[http://kep-feltoltes.hu/foto/mplayer.png-6578.html](http://kep-feltoltes.hu/foto/mplayer.png-6578.html)
Thanx
If you're running compiz while playing videos, it's a known problem. You have to change the video output under preferences. I used xv and it works fine. If the aspect ratio looks wierd as well, you can try to set the aspect ratio manually by right-clicking on the video screen and selecting from there.

---

### Post by Chronos6 on 2007-09-02
Tried both, the aspect ratio is not changing, and none of the outpust are working. The pictures what i uploaded are from different outputs.

---

### Post by kobinasucks on 2007-09-03
I seem to be the only one who's had a problem with this guide, I'm afraid.

Everything went perfectly until I typed in the last command ('compiz --replace') and received the following nasty:

xset:  unable to open display ""
xdpyinfo:  unable to open display "".
xvinfo:  Unable to open display 
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
xdpyinfo:  unable to open display "".
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

I'm pretty sure Compiz-Fusion should work on my system (a Dell Inspiron 6000) because Beryl did before.

Any help, Fireblend?

---

### Post by jbizzler on 2007-09-05
Bouge is failing miserably.  I got the libraries you say I need, and I needed to get libtool as well. However, your link to Bouge was down, so I found it elsewhere. Maybe that's the problem? Here's my output of 'make'.

```
[: 1: ==: unexpected operator
-e compiling : bouge.c -> build/libbouge.lobouge.c:76: error: expected specifier-qualifier-list before 'HandleEventProc'
bouge.c:93: error: expected specifier-qualifier-list before 'PaintWindowProc'
bouge.c:120: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitiate'
bouge.c:222: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveTerminate'
bouge.c:264: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveGetYConstrainRegion'
bouge.c: In function 'moveHandleMotionEvent':
bouge.c:357: error: dereferencing pointer to incomplete type
bouge.c:357: error: dereferencing pointer to incomplete type
bouge.c:359: error: 'MoveScreen' has no member named 'grabIndex'
bouge.c:364: error: dereferencing pointer to incomplete type
bouge.c:366: error: 'MoveDisplay' has no member named 'w'
bouge.c:368: error: 'MoveDisplay' has no member named 'x'
bouge.c:368: error: 'lastPointerX' undeclared (first use in this function)
bouge.c:368: error: (Each undeclared identifier is reported only once
bouge.c:368: error: for each function it appears in.)
bouge.c:369: error: 'MoveDisplay' has no member named 'y'
bouge.c:369: error: 'lastPointerY' undeclared (first use in this function)
bouge.c:371: error: dereferencing pointer to incomplete type
bouge.c:371: error: 'CompWindowTypeFullscreenMask' undeclared (first use in this function)
bouge.c:377: error: 'XRectangle' undeclared (first use in this function)
bouge.c:377: error: expected ';' before 'workArea'
bouge.c:380: error: 'MoveDisplay' has no member named 'x'
bouge.c:381: error: 'MoveDisplay' has no member named 'y'
bouge.c:383: warning: implicit declaration of function 'getWorkareaForOutput'
bouge.c:384: warning: implicit declaration of function 'outputDeviceForWindow'
bouge.c:385: error: 'workArea' undeclared (first use in this function)
bouge.c:387: error: 'MoveDisplay' has no member named 'opt'
bouge.c:389: error: 'MoveDisplay' has no member named 'region'
bouge.c:390: error: 'MoveDisplay' has no member named 'region'
bouge.c:390: warning: implicit declaration of function 'moveGetYConstrainRegion'
bouge.c:395: error: 'MoveDisplay' has no member named 'region'
bouge.c:400: error: dereferencing pointer to incomplete type
bouge.c:400: error: dereferencing pointer to incomplete type
bouge.c:401: error: dereferencing pointer to incomplete type
bouge.c:401: error: dereferencing pointer to incomplete type
bouge.c:402: error: dereferencing pointer to incomplete type
bouge.c:402: error: dereferencing pointer to incomplete type
bouge.c:402: error: dereferencing pointer to incomplete type
bouge.c:403: error: dereferencing pointer to incomplete type
bouge.c:403: error: dereferencing pointer to incomplete type
bouge.c:405: warning: implicit declaration of function 'XRectInRegion'
bouge.c:405: error: 'MoveDisplay' has no member named 'region'
bouge.c:408: error: 'MoveDisplay' has no member named 'status'
bouge.c:408: error: 'RectangleIn' undeclared (first use in this function)
bouge.c:414: error: 'MoveDisplay' has no member named 'region'
bouge.c:421: error: dereferencing pointer to incomplete type
bouge.c:421: error: dereferencing pointer to incomplete type
bouge.c:426: error: 'MoveDisplay' has no member named 'region'
bouge.c:433: error: dereferencing pointer to incomplete type
bouge.c:433: error: dereferencing pointer to incomplete type
bouge.c:438: error: 'MoveDisplay' has no member named 'status'
bouge.c:443: error: 'MoveDisplay' has no member named 'opt'
bouge.c:445: error: dereferencing pointer to incomplete type
bouge.c:445: error: 'CompWindowStateMaximizedVertMask' undeclared (first use in this function)
bouge.c:447: error: 'MoveScreen' has no member named 'snapOffY'
bouge.c:449: error: dereferencing pointer to incomplete type
bouge.c:451: error: dereferencing pointer to incomplete type
bouge.c:451: error: 'CWX' undeclared (first use in this function)
bouge.c:451: error: 'CWY' undeclared (first use in this function)
bouge.c:453: error: dereferencing pointer to incomplete type
bouge.c:453: error: 'CWWidth' undeclared (first use in this function)
bouge.c:454: error: dereferencing pointer to incomplete type
bouge.c:456: error: dereferencing pointer to incomplete type
bouge.c:457: error: dereferencing pointer to incomplete type
bouge.c:457: error: dereferencing pointer to incomplete type
bouge.c:459: error: 'MoveDisplay' has no member named 'x'
bouge.c:459: error: 'MoveDisplay' has no member named 'y'
bouge.c:461: warning: implicit declaration of function 'maximizeWindow'
bouge.c:463: error: 'MoveScreen' has no member named 'snapOffY'
bouge.c:463: error: 'MoveScreen' has no member named 'snapBackY'
bouge.c:468: error: 'MoveScreen' has no member named 'origState'
bouge.c:470: error: 'MoveScreen' has no member named 'snapBackY'
bouge.c:472: warning: implicit declaration of function 'otherScreenGrabExist'
bouge.c:479: warning: implicit declaration of function 'syncWindowPosition'
bouge.c:481: error: 'MoveScreen' has no member named 'origState'
bouge.c:483: error: dereferencing pointer to incomplete type
bouge.c:484: error: dereferencing pointer to incomplete type
bouge.c:486: warning: implicit declaration of function 'warpPointer'
bouge.c:486: error: 'pointerY' undeclared (first use in this function)
bouge.c:494: error: dereferencing pointer to incomplete type
bouge.c:496: error: dereferencing pointer to incomplete type
bouge.c:498: error: dereferencing pointer to incomplete type
bouge.c:498: error: dereferencing pointer to incomplete type
bouge.c:499: error: dereferencing pointer to incomplete type
bouge.c:501: error: dereferencing pointer to incomplete type
bouge.c:502: error: dereferencing pointer to incomplete type
bouge.c:503: error: dereferencing pointer to incomplete type
bouge.c:504: error: dereferencing pointer to incomplete type
bouge.c:507: error: dereferencing pointer to incomplete type
bouge.c:507: error: 'CompWindowStateMaximizedHorzMask' undeclared (first use in this function)
bouge.c:509: error: dereferencing pointer to incomplete type
bouge.c:509: error: dereferencing pointer to incomplete type
bouge.c:509: error: dereferencing pointer to incomplete type
bouge.c:509: error: dereferencing pointer to incomplete type
bouge.c:512: error: dereferencing pointer to incomplete type
bouge.c:512: error: dereferencing pointer to incomplete type
bouge.c:512: error: dereferencing pointer to incomplete type
bouge.c:515: error: dereferencing pointer to incomplete type
bouge.c:517: error: dereferencing pointer to incomplete type
bouge.c:517: error: dereferencing pointer to incomplete type
bouge.c:518: error: dereferencing pointer to incomplete type
bouge.c:520: error: dereferencing pointer to incomplete type
bouge.c:521: error: dereferencing pointer to incomplete type
bouge.c:522: error: dereferencing pointer to incomplete type
bouge.c:523: error: dereferencing pointer to incomplete type
bouge.c:527: warning: implicit declaration of function 'moveWindow'
bouge.c:527: error: 'MoveDisplay' has no member named 'w'
bouge.c:527: error: 'TRUE' undeclared (first use in this function)
bouge.c:527: error: 'FALSE' undeclared (first use in this function)
bouge.c:529: error: 'MoveDisplay' has no member named 'x'
bouge.c:530: error: 'MoveDisplay' has no member named 'y'
bouge.c: At top level:
bouge.c:536: error: expected declaration specifiers or '...' before 'XEvent'
bouge.c: In function 'moveHandleEvent':
bouge.c:540: error: dereferencing pointer to incomplete type
bouge.c:542: error: 'event' undeclared (first use in this function)
bouge.c:543: error: 'ButtonPress' undeclared (first use in this function)
bouge.c:544: warning: implicit declaration of function 'findScreenAtDisplay'
bouge.c:544: warning: assignment makes pointer from integer without a cast
bouge.c:547: error: dereferencing pointer to incomplete type
bouge.c:547: error: dereferencing pointer to incomplete type
bouge.c:549: error: 'MoveScreen' has no member named 'grabIndex'
bouge.c:551: warning: implicit declaration of function 'moveTerminate'
bouge.c:552: error: 'MoveDisplay' has no member named 'opt'
bouge.c:557: error: 'KeyPress' undeclared (first use in this function)
bouge.c:558: error: 'KeyRelease' undeclared (first use in this function)
bouge.c:559: warning: assignment makes pointer from integer without a cast
bouge.c:562: error: dereferencing pointer to incomplete type
bouge.c:562: error: dereferencing pointer to incomplete type
bouge.c:564: error: 'MoveScreen' has no member named 'grabIndex'
bouge.c:570: error: 'MoveDisplay' has no member named 'key'
bouge.c:572: warning: implicit declaration of function 'XWarpPointer'
bouge.c:572: error: dereferencing pointer to incomplete type
bouge.c:572: error: 'None' undeclared (first use in this function)
bouge.c:581: error: 'MotionNotify' undeclared (first use in this function)
bouge.c:582: warning: assignment makes pointer from integer without a cast
bouge.c:584: error: 'pointerX' undeclared (first use in this function)
bouge.c:584: error: 'pointerY' undeclared (first use in this function)
bouge.c:586: error: 'EnterNotify' undeclared (first use in this function)
bouge.c:587: error: 'LeaveNotify' undeclared (first use in this function)
bouge.c:588: warning: assignment makes pointer from integer without a cast
bouge.c:592: error: 'ClientMessage' undeclared (first use in this function)
bouge.c:593: error: dereferencing pointer to incomplete type
bouge.c:597: error: 'WmMoveResizeMove' undeclared (first use in this function)
bouge.c:598: error: 'WmMoveResizeMoveKeyboard' undeclared (first use in this function)
bouge.c:600: warning: implicit declaration of function 'findWindowAtDisplay'
bouge.c:600: warning: assignment makes pointer from integer without a cast
bouge.c:603: error: array type has incomplete element type
bouge.c:605: error: 'CompAction' undeclared (first use in this function)
bouge.c:605: error: 'action' undeclared (first use in this function)
bouge.c:606: error: 'MoveDisplay' has no member named 'opt'
bouge.c:614: warning: implicit declaration of function 'moveInitiate'
bouge.c:615: error: 'CompActionStateInitKey' undeclared (first use in this function)
bouge.c:621: error: 'Window' undeclared (first use in this function)
bouge.c:621: error: expected ';' before 'root'
bouge.c:624: warning: implicit declaration of function 'XQueryPointer'
bouge.c:624: error: dereferencing pointer to incomplete type
bouge.c:624: error: dereferencing pointer to incomplete type
bouge.c:625: error: 'root' undeclared (first use in this function)
bouge.c:625: error: 'child' undeclared (first use in this function)
bouge.c:629: error: 'Button1Mask' undeclared (first use in this function)
bouge.c:645: error: 'CompActionStateInitButton' undeclared (first use in this function)
bouge.c:648: error: dereferencing pointer to incomplete type
bouge.c:603: warning: unused variable 'o'
bouge.c:655: error: 'DestroyNotify' undeclared (first use in this function)
bouge.c:656: error: 'MoveDisplay' has no member named 'w'
bouge.c:656: error: 'MoveDisplay' has no member named 'w'
bouge.c:658: error: 'MoveDisplay' has no member named 'opt'
bouge.c:661: error: 'UnmapNotify' undeclared (first use in this function)
bouge.c:662: error: 'MoveDisplay' has no member named 'w'
bouge.c:662: error: 'MoveDisplay' has no member named 'w'
bouge.c:664: error: 'MoveDisplay' has no member named 'opt'
bouge.c:670: warning: implicit declaration of function 'UNWRAP'
bouge.c:670: error: 'handleEvent' undeclared (first use in this function)
bouge.c:671: error: dereferencing pointer to incomplete type
bouge.c:672: warning: implicit declaration of function 'WRAP'
bouge.c: At top level:
bouge.c:676: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'movePaintWindow'
bouge.c:711: error: expected declaration specifiers or '...' before 'Display'
bouge.c: In function 'moveDisplayInitOptions':
bouge.c:715: error: 'MoveDisplay' has no member named 'opt'
bouge.c:716: error: dereferencing pointer to incomplete type
bouge.c:717: error: dereferencing pointer to incomplete type
bouge.c:718: error: dereferencing pointer to incomplete type
bouge.c:718: error: 'moveInitiate' undeclared (first use in this function)
bouge.c:719: error: dereferencing pointer to incomplete type
bouge.c:719: error: 'moveTerminate' undeclared (first use in this function)
bouge.c:720: error: dereferencing pointer to incomplete type
bouge.c:720: error: 'FALSE' undeclared (first use in this function)
bouge.c:721: error: dereferencing pointer to incomplete type
bouge.c:722: error: dereferencing pointer to incomplete type
bouge.c:722: error: 'CompBindingTypeButton' undeclared (first use in this function)
bouge.c:723: error: dereferencing pointer to incomplete type
bouge.c:723: error: 'CompActionStateInitButton' undeclared (first use in this function)
bouge.c:724: error: dereferencing pointer to incomplete type
bouge.c:724: error: 'CompAltMask' undeclared (first use in this function)
bouge.c:725: error: dereferencing pointer to incomplete type
bouge.c:725: error: 'Button1' undeclared (first use in this function)
bouge.c:726: error: dereferencing pointer to incomplete type
bouge.c:726: error: 'CompBindingTypeKey' undeclared (first use in this function)
bouge.c:727: error: dereferencing pointer to incomplete type
bouge.c:727: error: 'CompActionStateInitKey' undeclared (first use in this function)
bouge.c:728: error: dereferencing pointer to incomplete type
bouge.c:729: error: dereferencing pointer to incomplete type
bouge.c:730: warning: implicit declaration of function 'XKeysymToKeycode'
bouge.c:730: error: 'display' undeclared (first use in this function)
bouge.c:730: warning: implicit declaration of function 'XStringToKeysym'
bouge.c:732: error: 'MoveDisplay' has no member named 'opt'
bouge.c:733: error: dereferencing pointer to incomplete type
bouge.c:734: error: dereferencing pointer to incomplete type
bouge.c:735: error: dereferencing pointer to incomplete type
bouge.c:736: error: dereferencing pointer to incomplete type
bouge.c:737: error: dereferencing pointer to incomplete type
bouge.c:739: error: 'MoveDisplay' has no member named 'opt'
bouge.c:740: error: dereferencing pointer to incomplete type
bouge.c:741: error: dereferencing pointer to incomplete type
bouge.c:742: error: dereferencing pointer to incomplete type
bouge.c:744: error: 'MoveDisplay' has no member named 'opt'
bouge.c:745: error: dereferencing pointer to incomplete type
bouge.c:746: error: dereferencing pointer to incomplete type
bouge.c:747: error: dereferencing pointer to incomplete type
bouge.c: In function 'moveGetDisplayOptions':
bouge.c:755: error: dereferencing pointer to incomplete type
bouge.c:757: error: 'MoveDisplay' has no member named 'opt'
bouge.c:757: error: invalid application of 'sizeof' to incomplete type 'CompOption' 
bouge.c:758: error: 'MoveDisplay' has no member named 'opt'
bouge.c:759: warning: control reaches end of non-void function
bouge.c: At top level:
bouge.c:762: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveSetDisplayOption'
bouge.c:798: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitDisplay'
bouge.c: In function 'moveFiniDisplay':
bouge.c:838: error: dereferencing pointer to incomplete type
bouge.c:840: warning: implicit declaration of function 'freeScreenPrivateIndex'
bouge.c:842: error: 'handleEvent' undeclared (first use in this function)
bouge.c: At top level:
bouge.c:848: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInitScreen'
bouge.c: In function 'moveFiniScreen':
bouge.c:876: error: dereferencing pointer to incomplete type
bouge.c:876: error: dereferencing pointer to incomplete type
bouge.c:877: error: dereferencing pointer to incomplete type
bouge.c:879: warning: implicit declaration of function 'removeScreenAction'
bouge.c:880: error: 'MoveDisplay' has no member named 'opt'
bouge.c:882: error: 'paintWindow' undeclared (first use in this function)
bouge.c:884: error: 'MoveScreen' has no member named 'moveCursor'
bouge.c:885: warning: implicit declaration of function 'XFreeCursor'
bouge.c:885: error: dereferencing pointer to incomplete type
bouge.c:885: error: 'MoveScreen' has no member named 'moveCursor'
bouge.c: At top level:
bouge.c:891: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveInit'
bouge.c: In function 'moveFini':
bouge.c:904: warning: implicit declaration of function 'freeDisplayPrivateIndex'
bouge.c: In function 'moveGetVersion':
bouge.c:911: error: 'ABIVERSION' undeclared (first use in this function)
bouge.c:912: warning: control reaches end of non-void function
bouge.c: At top level:
bouge.c:919: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'moveVTable'
bouge.c:941: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/libbouge.lo] Error 1
```

---

### Post by Draconix on 2007-09-07
I'm using Ubuntu fiesty fawn 7.04 64 bit and I followed the instructions step by step and I looked in the preferences menu and lo and behold...no compiz and I'm missing my borders....I tried "emerald and compiz --replace &" commands...nothing.  What am I doing wrong? Thanks in advance.

---

### Post by AronVanAmmers on 2007-09-09
Thanks for an excellent mini-howto. Compiz-fusion is working flawlessly on my Ati 9200SE / AMD Athlon 2600+. I'm using the open source radeon driver and AIGLX.

I've been using Beryl fulltime for the last couple of months. The performance of Compiz-fusion is better in a number of important areas. For my system it makes the difference between "cool effects, but a bit slow" and "looks great, works snappy".

---

### Post by Adler on 2007-09-09
AronVanAmmers,

I have to agree.

I've done the same thing. Followed a How-To for Beryl, and another for CF.

I think that this thread has gotten too long. As far as I know Ubuntu will not include any 3D Desktop Manger in the next release. 

Perhaps the author can re-write the How-To. Just a question.

As far as I know the Beryl svn files are still active, and my CF files keep up-dating.

I think that a clarification here would help everyone.

Adler

---

### Post by flapane on 2007-09-09
Any chanche to mantain the superkaramba applets in more than 1 desktop as beryl did ?
It still seems a little less smooth than beryl (git 4sep07), isn't it?
Any trayicon for kde?

---

### Post by Adler on 2007-09-09
flapane,

I'm coming from the GNOME side of things, and all my Gdesklets show on my *cube* sides.

SuperKaramba, which is used with the KDE Desktop, seemed to have always been a problem for me. Even from disto-upgrade to another Linux Distro.

Sorry. 

*But*, I hit last.fm. Great music there!

Adler

---

### Post by flapane on 2007-09-09
Originally it was a beryl problem (0.1.2 version), too, let's hope they'll fix soon, as I need my applets in every desktop.
Last.fm is great, isn't it? Add me as a friend, if u want ;)

---

### Post by Adler on 2007-09-09
flapane,

I'm *sure* that you need to add the Beryl SVN repositories to keep / install the latest Beryl. 

As I said before, getting compiz-Fusion has been a *little* confusing. But, I've done it.

There does need to be a new How-To done here.

I'd love to know how I can record / save to disk the video "God is an Astronaut" from last.fm.

I've bookmarked the Site.

Adler

---

### Post by flapane on 2007-09-09
I deleted beryl yesterday, I was referring to the problem in 0.1.2, which was solved in the next version, now I've done it, too, with compiz-fusion. 
[[IMG]http://img206.imageshack.us/img206/5894/dddsy5.th.jpg[/IMG]](http://img206.imageshack.us/img206/5894/dddsy5.jpg)

I think you can't record flash videos from lastfm.

---

### Post by Adler on 2007-09-09
flapane,

Thanks for that.

> I think you can't record flash videos from lastfm.

There was a  great video there.

We will see what the next generation Ubuntu brings.

Adler

---

### Post by RAV TUX on 2007-09-09
> **Fireblend said:**
> Hello! I decided to do something for society today and make a little how-to on what and how to install the new Compiz Fusion. These are the steps **[COLOR=Red]I[/COLOR]** used to get it working. As you know, ymmv so be careful when following the following steps. Also, as mentioned on the sticky, this isn't for ubuntu newbies, although anyone who can follow directions can do it, really. Also, I'd advice to follow this only if you already have either beryl or compiz installed and using, so you know your graphic card is supported and you don't get the WSOD :p

Anyway, here it is:


[COLOR=Red]**WHAT IS IT?**[/COLOR]

Well, I think the best way to explain what it is is by watching a video at youtube. Here's a few links:

[**Video 1**]("http://www.youtube.com/watch?v=D-2ZUAZoGOQ") / [**Video 2**]("http://www.youtube.com/watch?v=E4Fbk52Mk1w") / [**Video 3**]("http://www.youtube.com/watch?v=EytuaK04llw")

On the other hand, if you feel like a theoric definition, I guess we can use Wikipedia, which states:


So it basically means that unless you want to be stuck with your current beryl or compiz effects (and I'm not saying that's a bad option), you're gonna have to switch to Fusion sooner or later. Now, it's among Gutsy's goals to have this included, so if you are a patient human being you can wait. On the other hand, if you feel like upgrading now, follow these pretty simple instructions to get the current version.

Now, the current version is pretty stable (about as much as Beryl from my experience so far), so you don't have to worry about it being to unstable or anything but like any alpha/beta of anything, I can't guarantee you're gonna have the same results as me, so I'm not responsable for whatever might happen to your computer. Anyway, follow the instructions already:
[COLOR=Red]
[B]
HOW TO INSTALL:[/B][/COLOR]

I'm gonna assume we're installing on a fresh install, so most of you (specially if you already have experience installing eyecandy) might already have some steps covered, like getting Trevino's repository, for example. But to help those who might not have it installed, I'm gonna cover all the steps.

**STEP 1:**

First, we'll be adding [Trevino's repositories]("http://3v1n0.tuxfamily.org/"), which is where we're getting our Fusion copy from. You can also find a lot of other eyecandy software from them, like Avant Window Nav. and Affinity. Anyway, first we go to System->Administration->Software sources and select the "Third-party sources" tab. You're gonna get a listbox and a button that says "add" below it. Click there and paste the following:

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```Now do exactly the same and add this:

```
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```Make sure that the added lines have appeared in the listbox. Done? Now close that window and open up the terminal. Once we're on the terminal, type the following to get the GPG Key for the repositories we just added (You can probably skip this step, but it's best to do this).

```
sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
```Once entered, just wait. If for some reason it seems to be done but the "user@computer:$ " thing doesn't appear, close the terminal and open a new one or just start hitting random keys, for some reason, that happens to me so I thought I'd add that to avoid you waiting centuries for nothing to happen. Anyway, once that's done:

```
sudo apt-get update
```You should notice the two lines we added in the update list. If they're there, so far so good.

**STEP 2:**

Now we'll install what we need so we can start playing with our new beautiful effects. I should note that most of the following comes from [http://forums.opencompositing.org/viewtopic.php?f=14&t=131](http://forums.opencompositing.org/viewtopic.php?f=14&t=131), so you might as well go there and continue.

Anyway, just type these on a terminal:
```

sudo apt-get remove compiz-core desktop-effects

sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde

sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!

sudo apt-get install compiz-fusion-*

```If everything got removed / installed correctly, just press alt+f2 and type 
```

compiz --replace

```If all went well, congratulations, you now have Compiz Fusion! You can configure it at the System->Preferences menu.


[COLOR=Red]**TROUBLESHOOTING:**[/COLOR]

Alright, now to make this guide kinda useful, I'll add a couple of fixes that might help, feel free to add more in the comments or something.

***1. Windows are not moving as smoothly as they used to in Beryl / Compiz.***

This happened to me and it took me a while to fix. However, it shouldn't be too difficult. The current move plugin for some reason acts like that, so until they fix it we'll install a replacement plugin which is actually the old move plugin :p

[COLOR=Red][UPDATE][/COLOR] Before doing the following, you have to install the following packages from the repos if you don't have them already:

[B]libxslt1.1 
libxslt1-dev 
compiz-dev
[/B]

1. Go here: [http://forum.compiz.org/viewtopic.php?t=1064](http://forum.compiz.org/viewtopic.php?t=1064)
2. Get the douge plugin
3. Untar it anywhere, preferably home so you don't have to navigate too mcuh on terminal.
4. Navigate to the new douge directory and type
```
make; make install
```5. Restart Fusion
6. Go to the configurator and deselect move plugin, select douge.

That should do it, but if you see no change, restart the GUI (ctrl+alt+backspace) to make sure before making sure it's not working.

(Credit goes to Delfick from opencompositing forums for this one)
[B][I]
2. No window borders![/I][/B]

Well actually, I think there are a million possibilities for why this happens, but everytime it happens to me I can fix it with this command. Run it with alt+f2:

```
emerald --replace &
```
Well, that's all for now, hope it works out as well for you as it did for me, best of luck! :p

upon adding the first deb I get this:

```
W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
```




to get the GPG Key this happened:
```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
Password:Password:


gpg: no valid OpenPGP data found.
```

Is this guide out of date?

---

### Post by Adler on 2007-09-09
RAV TUX,

It does seem that Trevinos repositories go down from time to time. 

Also, he has posted here, at least once, to let us know what is happening. 

I shifted to Fusion, and the updates keep coming. And I'm back to normal.

I'd post a *How-To*, but can't be sure a lot of those things needed are still there i.e. GPG Key, Repositories, etc.

Adler

---

### Post by Vorian on 2007-09-09
It's not necessary to have the gpg key, it just is less annoying to have it.

---

### Post by Adler on 2007-09-09
Vorian,

Duh?

How can you get access after adding the repos? I always run "sudo aptitude update" in terminal. Consider me *old school*. Then, without the GPG key I got Errors, when I do that "sudo aptitude   update-dist". 

Let us know what you have in mind. I've got all those GPG keys, so I'm puzzled by your response.

Meanwhile, running CF very, very well.

I'd like to add a *How-To* here. 

Adler

---

### Post by Vorian on 2007-09-09
you apt-get install them.

All a gpg key does is let your system know the repository is a verified source.  It does not "lock" the packages.

---

### Post by AlexTepes on 2007-09-09
I'm going to commit suicide, cause I think I installed, beryl, compiz, compiz-fusion, followed 100 guides, and all I get is Beryl working and it switches on then I get no window holders/tooltips and then reverts back to gnome =(

---

### Post by nikoPSK on 2007-09-12
AAAAAAAAAAAAAAAAA I'm very new to ubuntu (just put 7.04 on my pc... today...) but I really want compiz fusion... I have tried you guide and I fail still to install it. Installing in linux is wierd... I keep getting failed to write cache I have no idea what to do... I have alo read the softpedia guide and still no luck... help plz? And also when terminal asks for my pass when I type no asterixs or anything shows up!	](*,)

---

### Post by readitsideways on 2007-09-12
Ahhh, and compiz-fusion is messed up again after an upgrade. I should know better than to let a CF update go through. Now, no 3D windows or screensaver and in ccsm all the images are missing. 

I'm using Vorian's repo since trevino's fiasco a few weeks ago. 

Duncan

---

### Post by Lithium17 on 2007-09-12
After following the guide, my desktop is now laggy and everything has gotten messed up.  To boot I don't even have the program, according to my program list.  I can't even access the settings for compiz. 

If nothing can be done can someone at least tell me how to uninstall?

---

### Post by Schnoidz on 2007-09-12
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
This guide worked well for me on 2 computers running Feisty.

---

### Post by paneas13 on 2007-09-16
I 've got NO borders. I type in the Terminal emerald --replace & and terminal kills itself. What should I try ?

---

### Post by kepahe on 2007-09-16
Ok,

How do i make it work now??
cos no only cant open desktop effects, but everything insede compiz its got a close sign next to it.

---

### Post by kepahe on 2007-09-16
Ok,

How do i make it work now??
cos no only cant open desktop effects, but everything insede compiz its got a close sign next to it.

---

### Post by Adler on 2007-09-16
Hi All,

The latest up-date also did break my CF set-up.

I found a solution by going into CCSM -  Preferences - Reset to Defaults. That got me some functionality back -- like the cube -- but it wiped out my pre-sets, and I had to start all over again.

Also, a few things are still missing. I guess I'll just wait for the next up-date. 

There's a thread here @ the Compiz Community Forums --  [http://forum.compiz-fusion.org/showthread.php?t=4115](http://forum.compiz-fusion.org/showthread.php?t=4115) concerning the latest up-date.

I hope that this helps.

Adler

---

### Post by gilligan on 2007-09-26
Hi,

I'm new to this forum. I installed Compiz Fusion and I still can't make it work! Mean how can I activate all those effects?

Thanks a lot
Gilligan

---

### Post by Adler on 2007-09-26
> Mean how can I activate all those effects?

gilligan,

You need to launch CompizConfig Settings Manager (CCSM). You should find it in your menus.

Adler

---

### Post by Dvorakis on 2007-09-26
Ok heres the deal...I just installed this,and it works fine besides the window boarders,and when I try to do emerald --replace nothing happens....Even though emerald is installed (I'd like to use an emerald theme,so I want this either way)

Any help?

---

### Post by Adler on 2007-09-26
Dvorakis,

Try adding this to Sessions: Click New, Name: Emerald, Command: emerald --replace.

Then re-boot. Emerald should launch.

Adler

---

### Post by Dvorakis on 2007-09-26
OK so apparently emerald is running fine...but it says the process is sleeping.

Anyway,when I start compiz I still don't have any window decorations and None of the effects seem to work.

---

### Post by bluedragon436 on 2007-11-02
Luckly for me my first install attempt with Compiz Fusion was a success...  It runs fine and I am having no issues with it at this time...the only other thing I want to add is I would like to find the Atlantis plugin that will work with Gutsy!!!  but I can handle what I have for now...

---

