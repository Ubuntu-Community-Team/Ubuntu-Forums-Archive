---
title: "Counter-Strike 1.6 Opens in tiny window."
date: 2007-07-24
forum: Gaming &amp; Leisure
---

### Post by SpyderS05 on 2007-07-24
Well, I installed Steam with Wine and then downloaded Counter-Strile 1.6.  I had done this before and it worked fine, but when I changed my video settings in CS it messed it up and if I loaded it then it would just go black and I'd have to restart.  So I unisntalled it and now when I run CS it appears in a tiny window.  Not really a window, just a small portion of the screen.  Here is a Screen shot, I have to monitors so that's why its big.

---

### Post by eiskalt on 2007-07-24
open console, type winecfg, click graphics tab, is emulate virtual desktop checked?

---

### Post by SpyderS05 on 2007-07-25
No, it is not.

Also, when I view my Video settings in CS there is no value's in Resolution.

---

### Post by eiskalt on 2007-07-25
is it running under software or opengl?

---

### Post by SpyderS05 on 2007-07-25
OpenGL

---

### Post by eiskalt on 2007-07-25
did you compile from source?  is this the only program you have under wine?  what version of wine are you using?

---

### Post by SpyderS05 on 2007-07-25
Ummm, not sure what you mean when you say compile from source.  It is Wine-0.9.37 and I also have Ventrillo installed with wine and it works fine.

---

### Post by eiskalt on 2007-07-25
Time for you to learn, young padiwan.  

Go here

[http://winehq.org/](http://winehq.org/)

in the upper right corner is the current version of wine.  Download that and extract it.

In that file is a text file labeled readme. open it

wine actually has a way to make compilling easier, in the read me you should see a line that says ./tools/wineinstall or somethihng like that.  Open a console/terminal window, cd to the wine directory that you just extracted.  Then type ./tools/wineinstall press enter, it will prompt you for everything if might want.  At the end, if you get any errors or it says it cant find something, then try searching synaptic package manager for that file, or post here.  This will create a wine install that is tailored to your specific system, so things like drivers and creen size will be correct.  I gotta jet to work. l8r

---

### Post by frodon on 2007-07-25
First disable beryl when playing or get the knowledge of configuring it correctly to work with wine, by default beryl badly interact with wine so if you haven't configured beryl to work correctly with wine windows then solve this first.

---

### Post by SpyderS05 on 2007-07-25
Ok, well I downloaded the latest version of wine but I can't install that until I remove the older version and I can't find how to do that.

---

### Post by ashmew2 on 2007-07-25
open up a terminal and type :

sudo apt-get remove wine

that shud do the trick , if that doesnt work , u could try going into the synaptic package manager and removing wine from there.
Hope this helps !

---

### Post by SpyderS05 on 2007-07-25
Yep, that did it.  Thanks.  Now I try and install the new wine and I get this:

WINE Installer v0.75

Running configure...

configure: creating cache config.cache
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.

---

### Post by SpyderS05 on 2007-07-25
I tried doing:

sudo apt-get install libc6-dev g++ gcc    and
sudo apt-get install gcc

but it said I already had the newest version for both.

---

### Post by SpyderS05 on 2007-07-25
Hurray, it's installing now.  I had to install libc6-dev-i386 and libc6-i386

However I noticed it said I didn't have something installed and it won't have OpenGL or Direct X support.  That sounds like it's gonna pose a problem.

---

### Post by eiskalt on 2007-07-25
i'm not at home atm, so i cant do this myself, try searching snyaptic for that  "gcc -m32", Your on a 64bit system, so I beleive you need a 32bit build environment.  I could be wrong, but give it a try.

Also check this how to out, I have a 32bit system so i've never done this.  Also, I have beryl and wine seems to play nice with it; no intervention.

[http://wiki.winehq.org/WineOn64bit#head-7a277214ee284c1915cd6c431f6369cfcde97e3c](http://wiki.winehq.org/WineOn64bit#head-7a277214ee284c1915cd6c431f6369cfcde97e3c)

---

### Post by SpyderS05 on 2007-07-25
Ok, now I have Wine installed and I put in the tahoma.ttf font in the font folder but I have no text anywhere when Steam opens up.

---

### Post by eiskalt on 2007-07-25
yea that usually means the font isnt  installed,  I took my font folder from my old windows pc.  Its one of the only things I keep on hand.  When you compilled wine initially, did you get any messages like, truetype fonts not installed, or something to that effect?

---

### Post by SpyderS05 on 2007-07-25
No, I didn't see anything like that.  I'm gonna try and copy my enitre font folder from my windows partition.

---

### Post by SpyderS05 on 2007-07-25
Ok, I was looking around google and found a lot of people with this problem and it seems to happen with this newest version of wine.  But, I unisntalled wine and everything and reinstalled it again from source.  Once it was done I was gonna add the Fonts to the folder, but my wine directory wasn't there.  So to check to see if it was installed right I did wine Steam.exe and it worked, and then the Wine folder showed up.  So, I stopped the Steam install, put the fonts in and did it again but still no f***ing fonts in Steam.  Also when it is installing, the console is open this messsage keeps coming up:

fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time

---

### Post by eiskalt on 2007-07-25
the font issue is common through all versions of wine, not just the current one.  THe problem your having is usually that you didnt have something installed when it compiled.  What you can do is just recompile, dont worry about uninstalling,

```

More stuff above here.
config.status: creating tools/winedump/Makefile
config.status: creating tools/winegcc/Makefile
config.status: creating tools/wmc/Makefile
config.status: creating tools/wrc/Makefile
config.status: creating include/config.h
config.status: executing include/stamp-h commands
config.status: executing dlls/gdi32/enhmfdrv commands
config.status: executing dlls/gdi32/mfdrv commands
config.status: executing dlls/kernel32/nls commands
config.status: executing dlls/user32/resources commands
config.status: executing dlls/wineps.drv/data commands
config.status: executing include/wine commands

Configure finished.  Do 'make depend && make' to compile Wine.


We need to install wine as root user, do you want us to build wine,
'su root' and install Wine?  Enter 'no' to continue without installing
(yes/no) 

```

When you compile, look for this screen.  If there are any problems or things that arent installed it should say so right above "configure finished. Do 'make depend"...

---

### Post by SpyderS05 on 2007-07-25
There is nothing there, it looks the same as yours

---

### Post by eiskalt on 2007-07-25
ok, try this, open synaptic package manager, and search for xrender

when i did that, i came up with libxrender1, and libxrender-dev installed.  Its been awhile since i compiled wine.

---

### Post by SpyderS05 on 2007-07-25
Ya, I saw the same ones.  They had been installed already, so I re-installed them and also installed libxrender1-dbg

---

### Post by eiskalt on 2007-07-25
try recompiling,  you are using ./tools/wineinstall right?

---

### Post by SpyderS05 on 2007-07-25
What I was doing was ./configure and then I did "make" and after that I did "make install".  If I do ./tools/wineinstall now it says it's already configured and then says
"We need to install wine as root user, do you want us to build wine,
'su root' and install Wine?  Enter 'no' to continue without installing
(yes/no) "

---

### Post by eiskalt on 2007-07-25
oh, ok, what you gotta do is delete the wine directory, not the .wine, but the one you initially used to compile wine.  Then uncompress the wine.rar again, go back in, then use ./tools/wineinstall   it'll get all the dependencies and makes things easier.

---

### Post by SpyderS05 on 2007-07-25
Ok, I did all that and now and everything looks Ok, there is nothing above Configure Finished now what do I do when it says:

We need to install wine as root user, do you want us to build wine,
'su root' and install Wine?  Enter 'no' to continue without installing
(yes/no)

---

### Post by eiskalt on 2007-07-25
ok, just type yes, then l8r it'll ask for the root password, just type it in and press enter, then it should install and hopefully all will be fine.

---

### Post by SpyderS05 on 2007-07-25
WOW! Still the same thing, I think I'm going to kill someone!

Still get the "fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time"

---

### Post by eiskalt on 2007-07-25
I did a search for x11 under synaptic, heres what I ccame up with.

[IMG]http://i3.photobucket.com/albums/y88/bLudDagger/wang.jpg[/IMG]

---

### Post by SpyderS05 on 2007-07-26
Ok, there were a couple things I did not have that you did.  So I installed everything as what you have and now I am uninstalling wine again, deleteing the folder and doing the ./tools/wineinstall again.  Hopefully this will do the trick.

---

### Post by SpyderS05 on 2007-07-26
Why does the world hate me!? No luck.  Still the same Xrender BS

So, I ran ./configure > check.txt  so I could check everything and under the X11 thins everything is good but it says it didn't find Xrandr.h and Xf86vmode.h and Xcursor.h

---

### Post by SpyderS05 on 2007-07-26
Well, I abandonded doing the wineinstall and all that and just added the winehq repository to my system, then did sudo apt-get install wine and now it's working.  Well, at least I have text.  We'll see what happens when I set up CS

---

### Post by SpyderS05 on 2007-07-26
Still tiny window, so I've gotten nowhere. lol

---

### Post by eiskalt on 2007-07-27
lol, ok, sorry to put you through that then.  Atleast you have a well configured version of wine.  When you open counterstrike, is the box for run in window checked?  Under where you change the resolution?

---

