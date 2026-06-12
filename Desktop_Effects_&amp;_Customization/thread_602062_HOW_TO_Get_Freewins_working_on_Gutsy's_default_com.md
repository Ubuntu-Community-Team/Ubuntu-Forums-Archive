---
title: "HOW TO: Get Freewins working on Gutsy's default compiz"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by scottDkoDer on 2007-11-03
Well, finally, for those that are using Gutsy and would like to have the additional eyecandy plug-in 'Freewins' working with Gutsy's default compiz-fusion, I'm presenting this guide.  This tutorial assumes that:

1) You have a fresh install of Gutsy.
2) You already have Gutsy's default compiz working.
3) You are running as user and not root.

NOTE: compiz-fusion is installed by default in Ubuntu Gutsy and will work as long as you have a video card with appropriate drivers and proper configuration.  This is beyond the scope of this tutorial, but there are a plethora of guides to configure your graphics card on Gutsy.  Also, many thanks to SmSpillaz of forum.opencompositing.org for patching this plug-in.

```
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O /tmp/freewins.zip http://smspillaz.googlepages.com/freewins-0.3-0.6.zip
mkdir -p  ~/compiz/ && cd ~/compiz
unzip /tmp/freewins.zip
cd ~/compiz/freewins-0.3-0.6
make clean
make
make install
```

Then restart ccsm and compiz.

If there are any problems, please check the prerequisites first, then ensure you have followed all instructions and typed all commands correctly.  Each should return without errors. If all is in order and there are still issues, then post any problems or suggested changes here.

Enjoy,

Scott

---

### Post by gafner on 2007-11-07
for a clean install you could create a deb packet and install it like this:

> dh_make -c gpl -e [email]your@mail.addr[/email]ess -m --createorig
sudo dpkg-buildpackage
cd ..
sudo dpkg -i freewins-0.3_0.6-1_amd64.deb

---

### Post by giri1985 on 2007-11-07
There were no porblems with installation. But there are no buttons assigned for freewins in ccsm and it is not accepting any new values. So i am not able use the plugin. Please help.

---

### Post by lnogueir on 2007-11-07
> **giri1985 said:**
> There were no porblems with installation. But there are no buttons assigned for freewins in ccsm and it is not accepting any new values. So i am not able use the plugin. Please help.

+1

---

### Post by jimerickso on 2007-11-07
> **lnogueir said:**
> +1
with all due rspect what exactly do you mean?

---

### Post by Jose Catre-Vandis on 2007-11-08
Be nice to know what freewins is and what effects it provides e.g. screenshot :)

---

### Post by SomeGuyDude on 2007-11-08
> **Jose Catre-Vandis said:**
> Be nice to know what freewins is and what effects it provides e.g. screenshot :)

[http://www.youtube.com/watch?v=16Qz_Ov3FuU](http://www.youtube.com/watch?v=16Qz_Ov3FuU)

Very cool looking, but I'd imagine it has little practical use unless there's a quick shortcut to make it snap back to normal orientation. Otherwise I'd keep finding myself with windows at wonky angles and trying to "fix" them.

Plus I can't think of a reason I'd want to rotate a window sideways. Still, pretty darn neat.

---

### Post by grnqrtr on 2007-11-08
@giri1985 & lnogueir

>  Originally Posted by giri1985  View Post
There were no porblems with installation. But there are no buttons assigned for freewins in ccsm and it is not accepting any new values. So i am not able use the plugin. Please help.

I think you guys probably had the same problem I had.  I followed the instructions at the top but it would give me one error, something about not being able to copy the freewins.xml file over.  So I created a folder called "metadata" in the ~/.compiz directory and then re-followed the instructions and it was able to copy the freewins.xml file into the new directory I created.  Then I was able to set the controls for freewins in cssm.  For some reason it didn't make the metadata folder itself and therefore wasn't able to copy a file into that directory that didn't exist.

Hopefully that will work for you too.

---

### Post by lnogueir on 2007-11-08
> **grnqrtr said:**
> @giri1985 & lnogueir



I think you guys probably had the same problem I had.  I followed the instructions at the top but it would give me one error, something about not being able to copy the freewins.xml file over.  So I created a folder called "metadata" in the ~/.compiz directory and then re-followed the instructions and it was able to copy the freewins.xml file into the new directory I created.  Then I was able to set the controls for freewins in cssm.  For some reason it didn't make the metadata folder itself and therefore wasn't able to copy a file into that directory that didn't exist.

Hopefully that will work for you too.

I have the metadata folder. I re-followed the instructions again and didn't work! I will keep looking for a solution!

Thanks for the help!

---

### Post by Jose Catre-Vandis on 2007-11-11
> **SomeGuyDude said:**
> [http://www.youtube.com/watch?v=16Qz_Ov3FuU](http://www.youtube.com/watch?v=16Qz_Ov3FuU)

Very cool looking, but I'd imagine it has little practical use unless there's a quick shortcut to make it snap back to normal orientation. Otherwise I'd keep finding myself with windows at wonky angles and trying to "fix" them.

Plus I can't think of a reason I'd want to rotate a window sideways. Still, pretty darn neat.

Thanks, agreed cool looking with little practical use. Best part on Youtube was the guy in the comments section asking if it was for XP or Vista :)

Can get windows to spin round but have not option to rotate them in and out of the screen at an angle. what do i need to do this (as in the youtube video)?

[EDIT] Don't worry, it started working after reboot :)

---

### Post by santiagoward2000 on 2007-11-21
Thank you for this how to! I just installed it and it works great!

---

### Post by santiagoward2000 on 2007-11-21
Hey! I found a problem in mine :(
Now, if I have the freewins plugin enabled, when I try to turn my computer off, after I press the "Quit" button, the screen dims as usual, but the window with the options to turn off, restart, log out, etc doesn't show up.
Does anyone know how to fix this?

---

### Post by OmegaBLK on 2007-11-21
> **Jose Catre-Vandis said:**
> 
Can get windows to spin round but have not option to rotate them in and out of the screen at an angle. what do i need to do this (as in the youtube video)?

[EDIT] Don't worry, it started working after reboot :)

Having a similar problem.  Tried rebooting.  I cannot completely control if I want move a window on Z or X axis.  Sometimes I can move around in 2D and sometimes I can move the window in 3D or at angle.  Is there a way to control whether to move a winodw in 2D or 3D when I want to do it?

EDIT:  Never mind.  For some strange reason I can not configure the key binding for "Axis help toggle" action in CCSM>Freewins.  I checked the freewins.xml file and that particular option is set to Control+Shift+a.  I am able to rotate 2D and 3D now.  Very weird...

---

### Post by ameba on 2007-11-21
So

---

### Post by OmegaBLK on 2007-11-22
^Did you enable Freewins from the Uncategorized section in CCSM (Compiz Config Settings Manager)?

---

### Post by Jose Catre-Vandis on 2007-11-26
Why do some windows rotate in and out and others don't - e.g. Firefox?

---

### Post by Six_Digits on 2007-11-28
> **grnqrtr said:**
> @giri1985 & lnogueir



I think you guys probably had the same problem I had.  I followed the instructions at the top but it would give me one error, something about not being able to copy the freewins.xml file over.  So I created a folder called "metadata" in the ~/.compiz directory and then re-followed the instructions and it was able to copy the freewins.xml file into the new directory I created.  Then I was able to set the controls for freewins in cssm.  For some reason it didn't make the metadata folder itself and therefore wasn't able to copy a file into that directory that didn't exist.

Hopefully that will work for you too.

I already have that folder and .xml file...


EDIT: Got it working after another CTRL+ALT+backspace.

---

### Post by lpuente on 2007-11-30
> **scottDkoDer said:**
> Well, finally, for those that are using Gutsy and would like to have the additional eyecandy plug-in 'Freewins' working with Gutsy's default compiz-fusion, I'm presenting this guide.  This tutorial assumes that:

1) You have a fresh install of Gutsy.
2) You already have Gutsy's default compiz working.
3) You are running as user and not root.

NOTE: compiz-fusion is installed by default in Ubuntu Gutsy and will work as long as you have a video card with appropriate drivers and proper configuration.  This is beyond the scope of this tutorial, but there are a plethora of guides to configure your graphics card on Gutsy.  Also, many thanks to SmSpillaz of forum.opencompositing.org for patching this plug-in.

```
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O /tmp/freewins.zip http://smspillaz.googlepages.com/freewins-0.3-0.6.zip
mkdir -p  ~/compiz/ && cd ~/compiz
unzip /tmp/freewins.zip
cd ~/compiz/freewins-0.3-0.6
make clean
make
make install
```

Then restart ccsm and compiz.

If there are any problems, please check the prerequisites first, then ensure you have followed all instructions and typed all commands correctly.  Each should return without errors. If all is in order and there are still issues, then post any problems or suggested changes here.

Enjoy,

Scott
Thank you for this good info. I'm sorry, but I do get the following error:

cp freewins.xml /home/i/.compiz/plugins/../metadata/
cp: target `/home/i/.compiz/plugins/../metadata/' is not a directory: No such file or directory
make: *** [install] Error 1
rm freewins.lo

What do I have to do to fix this?  Thank you.

---

### Post by fuchur on 2007-12-01
as i think above might be helped by this as well: 

followed this howto, but for obscure reasons, the xml file this method produced was wrong.


i had to manually enter <button></button> and <key></key> 
in the three lines starting with
<default>
so that the file finally looks like 



```
<?xml version="1.0" encoding="UTF-8"?>
<compiz>
    <plugin name="freewins">
	<short>Freewins</short>
	<long>Freely rotate windows</long>
	<display>
	    <option type="action" name="initiate">
			<short>Initiate rotation</short>
			<long>Start Rotation</long>
			
<default><button>&lt;Control&gt;&lt;Shift&gt;Button1</button></default>
	    		<allowed button="true"/>
	    </option>
	    <option type="action" name="reset">
			<short>Reset</short>
			<long>Reset Rotation</long>
<default><button>&lt;Control&gt;&lt;Shift&gt;Button2</button></default>
			<allowed button="true"/>
	    </option>
	    <option type="action" name="toggle">
			<short>Axis help toggle</short>
			<long>Axis selection helper </long>
			
<default><key>&lt;Control&gt;&lt;Shift&gt;a</key></default>
			<allowed key="true"/>
	    </option>
	</display>
    </plugin>
</compiz>

```






btw regarding 

> **lpuente said:**
> Thank you for this good info. I'm sorry, but I do get the following error:

cp freewins.xml /home/i/.compiz/plugins/../metadata/
cp: target `/home/i/.compiz/plugins/../metadata/' is not a directory: No such file or directory
make: *** [install] Error 1
rm freewins.lo

What do I have to do to fix this?  Thank you.

i also have this issue. but 

mkdir /home/i/.compiz/plugins/../metadata/

solves this, provided your username is in fact i :-)

---

### Post by doctorgreg on 2007-12-03
Hey Fuchur.  I changed the xml file to what you have above and it still does not work.  I don't know what to do?

---

### Post by thetictacaddict on 2007-12-04
Sweet!  Thanks for the guide.  fuchur, your xml file helped me out.

---

### Post by nevr2low on 2007-12-05
this might sound strange but how do you edit the xml file because i have the opt under my CCSM but i cant change anything im running 7.1 and i dont understand how to do it thanks

---

### Post by fuchur on 2007-12-07
@ drgreg
I am sorry, I don't know what else you could try.  But there is also a thread at:

[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

that deals a lot with freewins as well. maybe you can  find some help there 

@ nevr2low: to edit the xml file you just have to open 

/home/xxxx/.compiz/metadata/freewins.xml 
where xxx is your username
with your favorite text editor (like gedit) , and then restart at least ccsm (but i think also compiz)

---

### Post by hotroddude on 2007-12-18
i keep getting an error trying to download it, it worked once but i cant use it and it doesnt stay checked when i close it, so i dont think it installed correctly so i tried again and im getting this,

```
steven@steven-desktop:~/compiz/freewins-0.3-0.6$ make install
libtool --mode=install install libfreewins.la \
        /home/steven/.compiz/plugins/libfreewins.la
install .libs/libfreewins.so.0.0.0 /home/steven/.compiz/plugins/libfreewins.so.0.0.0
install: cannot remove `/home/steven/.compiz/plugins/libfreewins.so.0.0.0': Permission denied
make: *** [install] Error 1
```

---

### Post by ronmarley1 on 2007-12-21
> **Jose Catre-Vandis said:**
> Why do some windows rotate in and out and others don't - e.g. Firefox?

I would like to know this as well.

EDIT:  Figured it out...  Use the "Axis help toggle" to tell you where to click to rotate 2D or 3D.

---

### Post by anubis3000bc on 2007-12-23
anubis@ubuntu:~/compiz/freewins-0.3-0.6$ make
libtool --mode=compile gcc `pkg-config --cflags compiz` -Wall -shared -c -o freewins.lo freewins.c
mkdir .libs
 gcc -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -Wall -shared -c freewins.c  -fPIC -DPIC -o .libs/freewins.o
freewins.c:59: error: expected specifier-qualifier-list before 'HandleEventProc'
freewins.c:73: error: expected specifier-qualifier-list before 'PaintOutputProc'
freewins.c:100: error: expected specifier-qualifier-list before 'Bool'
freewins.c:115: error: expected declaration specifiers or '...' before 'XEvent'
freewins.c: In function 'FWHandleEvent':
freewins.c:119: error: dereferencing pointer to incomplete type
freewins.c:121: error: 'ev' undeclared (first use in this function)
freewins.c:121: error: (Each undeclared identifier is reported only once
freewins.c:121: error: for each function it appears in.)
freewins.c:124: error: 'MotionNotify' undeclared (first use in this function)
freewins.c:126: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:127: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:127: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:127: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:128: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:128: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:130: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:131: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:133: error: 'FWWindow' has no member named 'zaxis'
freewins.c:135: error: 'FWWindow' has no member named 'grabLeft'
freewins.c:140: error: 'FWWindow' has no member named 'grabTop'
freewins.c:153: error: 'FWWindow' has no member named 'grabLeft'
freewins.c:153: error: 'FALSE' undeclared (first use in this function)
freewins.c:153: error: 'TRUE' undeclared (first use in this function)
freewins.c:154: error: 'FWWindow' has no member named 'grabTop'
freewins.c:163: warning: implicit declaration of function 'damageScreen'
freewins.c:163: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:168: error: 'FWWindow' has no member named 'rotated'
freewins.c:169: error: 'FWScreen' has no member named 'rotatedWindows'
freewins.c:170: error: 'FWWindow' has no member named 'rotated'
freewins.c:173: error: 'FWWindow' has no member named 'rotated'
freewins.c:174: error: 'FWScreen' has no member named 'rotatedWindows'
freewins.c:175: error: 'FWWindow' has no member named 'rotated'
freewins.c:184: error: 'ButtonPress' undeclared (first use in this function)
freewins.c:191: error: 'ButtonRelease' undeclared (first use in this function)
freewins.c:192: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:193: error: dereferencing pointer to incomplete type
freewins.c:193: error: dereferencing pointer to incomplete type
freewins.c:194: error: dereferencing pointer to incomplete type
freewins.c:194: error: dereferencing pointer to incomplete type
freewins.c:196: error: 'FWScreen' has no member named 'grabIndex'
freewins.c:197: warning: implicit declaration of function 'removeScreenGrab'
freewins.c:197: error: 'FWScreen' has no member named 'grabIndex'
freewins.c:198: error: 'FWScreen' has no member named 'grabIndex'
freewins.c:202: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:202: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:202: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:203: error: 'FWWindow' has no member named 'grabbed'
freewins.c:204: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:209: error: 'FocusOut' undeclared (first use in this function)
freewins.c:212: error: 'FocusIn' undeclared (first use in this function)
freewins.c:213: error: 'NotifyGrab' undeclared (first use in this function)
freewins.c:214: error: 'FWDisplay' has no member named 'focusWindow'
freewins.c:214: warning: implicit declaration of function 'findWindowAtDisplay'
freewins.c:221: warning: implicit declaration of function 'UNWRAP'
freewins.c:221: error: 'handleEvent' undeclared (first use in this function)
freewins.c:222: error: dereferencing pointer to incomplete type
freewins.c:223: warning: implicit declaration of function 'WRAP'
freewins.c: At top level:
freewins.c:228: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'FWPaintWindow'
freewins.c:274: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'FWPaintOutput'
freewins.c:340: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'FWDamageWindowRect'
freewins.c: In function 'FWWindowResizeNotify':
freewins.c:362: error: dereferencing pointer to incomplete type
freewins.c:362: error: dereferencing pointer to incomplete type
freewins.c:362: error: dereferencing pointer to incomplete type
freewins.c:363: error: dereferencing pointer to incomplete type
freewins.c:363: error: dereferencing pointer to incomplete type
freewins.c:368: error: dereferencing pointer to incomplete type
freewins.c:368: error: 'windowResizeNotify' undeclared (first use in this function)
freewins.c:369: error: dereferencing pointer to incomplete type
freewins.c:370: error: dereferencing pointer to incomplete type
freewins.c: At top level:
freewins.c:375: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'initiateFWRotate'
freewins.c:426: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'resetFWRotation'
freewins.c:454: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'toggleFWAxis'
freewins.c: In function 'freewinsGetDisplayOptions':
freewins.c:469: error: dereferencing pointer to incomplete type
freewins.c:472: error: 'FWDisplay' has no member named 'opt'
freewins.c:473: warning: control reaches end of non-void function
freewins.c: At top level:
freewins.c:475: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsSetDisplayOption'
freewins.c:507:33: warning: "/*" within comment
freewins.c:517: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsOptionInfo'
freewins.c:528: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsInitWindow'
freewins.c: In function 'freewinsFiniWindow':
freewins.c:560: error: dereferencing pointer to incomplete type
freewins.c:560: error: dereferencing pointer to incomplete type
freewins.c:560: error: dereferencing pointer to incomplete type
freewins.c:561: error: dereferencing pointer to incomplete type
freewins.c:563: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:564: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c: At top level:
freewins.c:572: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsInitScreen'
freewins.c: In function 'freewinsFiniScreen':
freewins.c:602: error: dereferencing pointer to incomplete type
freewins.c:602: error: dereferencing pointer to incomplete type
freewins.c:604: warning: implicit declaration of function 'freeWindowPrivateIndex'
freewins.c:606: error: 'paintWindow' undeclared (first use in this function)
freewins.c:607: error: 'paintOutput' undeclared (first use in this function)
freewins.c:609: error: 'damageWindowRect' undeclared (first use in this function)
freewins.c:611: error: 'windowResizeNotify' undeclared (first use in this function)
freewins.c: At top level:
freewins.c:617: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsInitDisplay'
freewins.c: In function 'freewinsFiniDisplay':
freewins.c:649: error: dereferencing pointer to incomplete type
freewins.c:651: warning: implicit declaration of function 'freeScreenPrivateIndex'
freewins.c:653: error: 'handleEvent' undeclared (first use in this function)
freewins.c: At top level:
freewins.c:686: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsInit'
freewins.c: In function 'freewinsFini':
freewins.c:704: warning: implicit declaration of function 'freeDisplayPrivateIndex'
freewins.c: In function 'freewinsGetVersion':
freewins.c:713: error: 'ABIVERSION' undeclared (first use in this function)
freewins.c:714: warning: control reaches end of non-void function
freewins.c: At top level:
freewins.c:718: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsVTable'
freewins.c:736: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [freewins.lo] Error 1
anubis@ubuntu:~/compiz/freewins-0.3-0.6$ make install
libtool --mode=compile gcc `pkg-config --cflags compiz` -Wall -shared -c -o freewins.lo freewins.c
 gcc -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -Wall -shared -c freewins.c  -fPIC -DPIC -o .libs/freewins.o
freewins.c:59: error: expected specifier-qualifier-list before 'HandleEventProc'
freewins.c:73: error: expected specifier-qualifier-list before 'PaintOutputProc'
freewins.c:100: error: expected specifier-qualifier-list before 'Bool'
freewins.c:115: error: expected declaration specifiers or '...' before 'XEvent'
freewins.c: In function 'FWHandleEvent':
freewins.c:119: error: dereferencing pointer to incomplete type
freewins.c:121: error: 'ev' undeclared (first use in this function)
freewins.c:121: error: (Each undeclared identifier is reported only once
freewins.c:121: error: for each function it appears in.)
freewins.c:124: error: 'MotionNotify' undeclared (first use in this function)
freewins.c:126: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:127: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:127: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:127: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:128: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:128: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:130: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:131: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:133: error: 'FWWindow' has no member named 'zaxis'
freewins.c:135: error: 'FWWindow' has no member named 'grabLeft'
freewins.c:140: error: 'FWWindow' has no member named 'grabTop'
freewins.c:153: error: 'FWWindow' has no member named 'grabLeft'
freewins.c:153: error: 'FALSE' undeclared (first use in this function)
freewins.c:153: error: 'TRUE' undeclared (first use in this function)
freewins.c:154: error: 'FWWindow' has no member named 'grabTop'
freewins.c:163: warning: implicit declaration of function 'damageScreen'
freewins.c:163: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:168: error: 'FWWindow' has no member named 'rotated'
freewins.c:169: error: 'FWScreen' has no member named 'rotatedWindows'
freewins.c:170: error: 'FWWindow' has no member named 'rotated'
freewins.c:173: error: 'FWWindow' has no member named 'rotated'
freewins.c:174: error: 'FWScreen' has no member named 'rotatedWindows'
freewins.c:175: error: 'FWWindow' has no member named 'rotated'
freewins.c:184: error: 'ButtonPress' undeclared (first use in this function)
freewins.c:191: error: 'ButtonRelease' undeclared (first use in this function)
freewins.c:192: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:193: error: dereferencing pointer to incomplete type
freewins.c:193: error: dereferencing pointer to incomplete type
freewins.c:194: error: dereferencing pointer to incomplete type
freewins.c:194: error: dereferencing pointer to incomplete type
freewins.c:196: error: 'FWScreen' has no member named 'grabIndex'
freewins.c:197: warning: implicit declaration of function 'removeScreenGrab'
freewins.c:197: error: 'FWScreen' has no member named 'grabIndex'
freewins.c:198: error: 'FWScreen' has no member named 'grabIndex'
freewins.c:202: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:202: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:202: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:203: error: 'FWWindow' has no member named 'grabbed'
freewins.c:204: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:209: error: 'FocusOut' undeclared (first use in this function)
freewins.c:212: error: 'FocusIn' undeclared (first use in this function)
freewins.c:213: error: 'NotifyGrab' undeclared (first use in this function)
freewins.c:214: error: 'FWDisplay' has no member named 'focusWindow'
freewins.c:214: warning: implicit declaration of function 'findWindowAtDisplay'
freewins.c:221: warning: implicit declaration of function 'UNWRAP'
freewins.c:221: error: 'handleEvent' undeclared (first use in this function)
freewins.c:222: error: dereferencing pointer to incomplete type
freewins.c:223: warning: implicit declaration of function 'WRAP'
freewins.c: At top level:
freewins.c:228: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'FWPaintWindow'
freewins.c:274: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'FWPaintOutput'
freewins.c:340: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'FWDamageWindowRect'
freewins.c: In function 'FWWindowResizeNotify':
freewins.c:362: error: dereferencing pointer to incomplete type
freewins.c:362: error: dereferencing pointer to incomplete type
freewins.c:362: error: dereferencing pointer to incomplete type
freewins.c:363: error: dereferencing pointer to incomplete type
freewins.c:363: error: dereferencing pointer to incomplete type
freewins.c:368: error: dereferencing pointer to incomplete type
freewins.c:368: error: 'windowResizeNotify' undeclared (first use in this function)
freewins.c:369: error: dereferencing pointer to incomplete type
freewins.c:370: error: dereferencing pointer to incomplete type
freewins.c: At top level:
freewins.c:375: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'initiateFWRotate'
freewins.c:426: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'resetFWRotation'
freewins.c:454: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'toggleFWAxis'
freewins.c: In function 'freewinsGetDisplayOptions':
freewins.c:469: error: dereferencing pointer to incomplete type
freewins.c:472: error: 'FWDisplay' has no member named 'opt'
freewins.c:473: warning: control reaches end of non-void function
freewins.c: At top level:
freewins.c:475: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsSetDisplayOption'
freewins.c:507:33: warning: "/*" within comment
freewins.c:517: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsOptionInfo'
freewins.c:528: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsInitWindow'
freewins.c: In function 'freewinsFiniWindow':
freewins.c:560: error: dereferencing pointer to incomplete type
freewins.c:560: error: dereferencing pointer to incomplete type
freewins.c:560: error: dereferencing pointer to incomplete type
freewins.c:561: error: dereferencing pointer to incomplete type
freewins.c:563: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c:564: error: 'FWDisplay' has no member named 'grabWindow'
freewins.c: At top level:
freewins.c:572: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsInitScreen'
freewins.c: In function 'freewinsFiniScreen':
freewins.c:602: error: dereferencing pointer to incomplete type
freewins.c:602: error: dereferencing pointer to incomplete type
freewins.c:604: warning: implicit declaration of function 'freeWindowPrivateIndex'
freewins.c:606: error: 'paintWindow' undeclared (first use in this function)
freewins.c:607: error: 'paintOutput' undeclared (first use in this function)
freewins.c:609: error: 'damageWindowRect' undeclared (first use in this function)
freewins.c:611: error: 'windowResizeNotify' undeclared (first use in this function)
freewins.c: At top level:
freewins.c:617: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsInitDisplay'
freewins.c: In function 'freewinsFiniDisplay':
freewins.c:649: error: dereferencing pointer to incomplete type
freewins.c:651: warning: implicit declaration of function 'freeScreenPrivateIndex'
freewins.c:653: error: 'handleEvent' undeclared (first use in this function)
freewins.c: At top level:
freewins.c:686: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsInit'
freewins.c: In function 'freewinsFini':
freewins.c:704: warning: implicit declaration of function 'freeDisplayPrivateIndex'
freewins.c: In function 'freewinsGetVersion':
freewins.c:713: error: 'ABIVERSION' undeclared (first use in this function)
freewins.c:714: warning: control reaches end of non-void function
freewins.c: At top level:
freewins.c:718: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'freewinsVTable'
freewins.c:736: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [freewins.lo] Error 1
anubis@ubuntu:~/compiz/freewins-0.3-0.6$

---

### Post by anubis3000bc on 2007-12-23
Now can anybody help me fix freewins?

---

### Post by kokomonjo on 2007-12-25
> **fuchur said:**
> as i think above might be helped by this as well: 

followed this howto, but for obscure reasons, the xml file this method produced was wrong.


i had to manually enter <button></button> and <key></key> 
in the three lines starting with
<default>
so that the file finally looks like 



```
<?xml version="1.0" encoding="UTF-8"?>
<compiz>
    <plugin name="freewins">
	<short>Freewins</short>
	<long>Freely rotate windows</long>
	<display>
	    <option type="action" name="initiate">
			<short>Initiate rotation</short>
			<long>Start Rotation</long>
			
<default><button>&lt;Control&gt;&lt;Shift&gt;Button1</button></default>
	    		<allowed button="true"/>
	    </option>
	    <option type="action" name="reset">
			<short>Reset</short>
			<long>Reset Rotation</long>
<default><button>&lt;Control&gt;&lt;Shift&gt;Button2</button></default>
			<allowed button="true"/>
	    </option>
	    <option type="action" name="toggle">
			<short>Axis help toggle</short>
			<long>Axis selection helper </long>
			
<default><key>&lt;Control&gt;&lt;Shift&gt;a</key></default>
			<allowed key="true"/>
	    </option>
	</display>
    </plugin>
</compiz>

```






btw regarding 



i also have this issue. but 

mkdir /home/i/.compiz/plugins/../metadata/

solves this, provided your username is in fact i :-)

I also have this problem how and when do i use "mkdir /home/i/.compiz/plugins/../metadata/" as far as a few plugins for compiz goes. i get an error as soon as i get to the "make" and "make install" commans.  also could anyone explain how to use xml for this freewin problem? i have freewin installed but cannot enter in a key combo to intiate it. I am a total beginner sooo all of this is new to me right now

---

### Post by bharkins on 2008-02-13
> **scottDkoDer said:**
> Well, finally, for those that are using Gutsy and would like to have the additional eyecandy plug-in 'Freewins' working with Gutsy's default compiz-fusion, I'm presenting this guide.  This tutorial assumes that:

1) You have a fresh install of Gutsy.
2) You already have Gutsy's default compiz working.
3) You are running as user and not root.

NOTE: compiz-fusion is installed by default in Ubuntu Gutsy and will work as long as you have a video card with appropriate drivers and proper configuration.  This is beyond the scope of this tutorial, but there are a plethora of guides to configure your graphics card on Gutsy.  Also, many thanks to SmSpillaz of forum.opencompositing.org for patching this plug-in.

```
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
wget -O /tmp/freewins.zip http://smspillaz.googlepages.com/freewins-0.3-0.6.zip
mkdir -p  ~/compiz/ && cd ~/compiz
unzip /tmp/freewins.zip
cd ~/compiz/freewins-0.3-0.6
make clean
make
make install
```

Then restart ccsm and compiz.

If there are any problems, please check the prerequisites first, then ensure you have followed all instructions and typed all commands correctly.  Each should return without errors. If all is in order and there are still issues, then post any problems or suggested changes here.

Enjoy,

Scott

I installed freewins per instructions above. When I open freewins in ccsm, I only get "none" in the actions of rotate windows, etc. How do I get the action started?

---

### Post by chavanak on 2008-02-13
The effect is very cooolllll!!! Its working fine for me but yes i find other plugins more usefull..
I mainly use these plugins to make my gf jeleous ;)

---

### Post by bharkins on 2008-02-18
I opened the .xml file in gedit. I have the same key combinations as others have shown:
Initiate=Crtl+Shft+1, Reset=Ctrl+Shft+2, Action toggle=Ctrl+Shft+a
Tried to enter these into the "None" boxes, but they won't take them. I can't get these to work at all in Freewins.

---

### Post by chavanak on 2008-02-18
Freewins has some issues on gutsy!!! The notification area stops responding when you have freewins enabled. So if someone faces this problem, try disabling freewins

---

### Post by bharkins on 2008-02-18
> **chavanak said:**
> Freewins has some issues on gutsy!!! The notification area stops responding when you have freewins enabled. So if someone faces this problem, try disabling freewins

Agreed - I turned Freewins off for the moment to see if the developer can improve the reliability. Is the plugin working for Hardy?

---

### Post by lbarnes on 2008-02-19
i can't get it to work, i finally got it to appear in ccsm under uncategorized
but it is unchecked and i cannot check it or enable it, furthermore
all of my other plugins are frozen as well - i can't disable desktop cube for example
any ideas?

edit*
ok, i didn't realize i unchecked something in the plugin part of ccsm
i can enable freewins in ccsm but it is completely blank

---

### Post by chavanak on 2008-02-19
[http://ubuntuforums.org/showthread.php?t=659282](http://ubuntuforums.org/showthread.php?t=659282)

Check this post, its given how exactly to install free windows manager or freewins

---

