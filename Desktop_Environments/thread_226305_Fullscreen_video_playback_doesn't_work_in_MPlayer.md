---
title: "Fullscreen video playback doesn't work in MPlayer"
date: 2006-07-31
forum: Desktop Environments
---

### Post by blueturtl on 2006-07-31
There's something funny about MPlayer under Dapper.

I've compiled and installed MPlayer the same way since Hoary and now I've run into this: no video can be played in fullscreen mode. Instead of being properly adjusted to fullscreen size the video will simply play in a small window in the middle of the screen. All my monitor space is wasted on black edges. Does anyone know what causes this and how to fix it?

This also happened at a friend's place when I was setting up Ubuntu for them, so I know this is not machine spesific or a driver issue.

Also, how do I remove the "Play with MPlayer" submenu items from the right-click menus under Gnome after uninstallation?

---

### Post by Dr. Nick on 2006-07-31
its the video output codec that mplayer is using, open up mplayer and right click on the video window and hit "prefrences" then click the video tab and set it to xv instead of x11 and then restart mplayer and see if that helps.

---

### Post by blueturtl on 2006-07-31
I can't find the option of xv!

Apparently some things have been rearranged in Dapper, since for example i could not find the package x-window-system-dev. I went looking for xv in Synaptic and came up with the xlibs-dev package which requires a whole bunch of other packages to be installed. I'm going to recompile and see if I can get this thing to work.

Meanwhile, how do I remove those extra "Open with MPlayer" submenu options, as they keep regenerating everytime I reinstall MPlayer?!

---

### Post by blueturtl on 2006-07-31
I fixed it! It was apparently the xlibs-dev packages since now I have the option of xv under video and everything works as it once did.

Everything would have gone smooth had I known that the x-window-system-dev package has been devided into multiple smaller packages!

---

### Post by Dr. Nick on 2006-07-31
Glad you got it, I havent used a custom compiled version before, I knew the xv option was their under the ubuntu compiled packages but didnt even think about it having to have the -dev files installed to build xv into a source compiled ver,

Unfortunaltey I do not know how to remove the "play in mplayer" button

---

### Post by blueturtl on 2006-08-03
I would use a ready package, but for some reason MPlayer is never in my repos. Not in Universe at least. Actually, compiling MPlayer has taught me some things about Linux and isn't necessarily even that hard. Most of problems have to do with the required packages being installed. Plus I look like a real guru to all people with all that messy output on the display while it's compiling. :grin: 

I'm going to check if the Open-with submenu entry is double for other users as well, that will help me find wether it's a local issue (aka in my home folder) or something bigger.

I'm still a bit lost with the compiling bit, because to be honest I have not been able to find a good generic manual about it. The most problematic part is make install, since I don't know what happens then. Where do the files go? How do I uninstall or undo changes? It's all vague. In DOS I liked having hands-on control over everything. If I installed an app into C:\APP I knew I could just remove the folder and the system would be like nothing ever happened. I understand the file system hierarchy in Linux was designed to be more efficient (aka libs go here, binaries there etc), but it all seems like a big mess when you don't know what is happening and don't have controll over it.

In the course of this problem I have reinstalled MPlayer multiple times, and I know that since the files always go to the same place, there should not really be any problem, but the "Open-with" submenu is bothering me under Gnome since I do not know how it is affected and how it can be fixed. Also what have I broken that I cannot see? :-k

---

### Post by endfx on 2006-08-03
You remember the ./configure script you ran before you ran make?
Well that has a lot of options that you can pass in such as where to install the files (i.e. when you run make install). I would read the "readme" file or "install" file you got with mplayer.

So make just compiles the programs, assuming you have all the dependencies.

Make install simply copies the executables and config files to where they need to go (which is specified in the configure script you ran) This is why you need to be root (or sudo) when your run "make install"

I'm probably repeating a lot of stuff that you already know.

Now your menu problem:
Browse to a file (in File Browser) that you would open with mplayer (such as an avi file). Right Click, select properties.
Select the "Open With" tab. Now remove the the extra "mplayers" from that list (highlight and select remove). You should be able to remove all but one mplayer's in that list.

And if you are curious, you can also set the default application from here. Just select the radio button beside the app that you want (probably mplayer). Now you can just double click on the movie file instead of right clicking and "open with" mplayer

Hope this helps.

---

### Post by endfx on 2006-08-03
And I forgot one thing about the compiling bit:

The problem with compiling/installing from source is that uninstalling can be a real pain in the ***. If the application that you installed was well written, then you should be able to run a:
make uninstall 
from the same directory you ran "make install".

Otherwise there isn't really a good way to uninstall program you installed from source. 

That is why I chose ubunutu -- because of the great package management system -- you can install without worrying about dependencies and uninstalls are just as easy.

---

### Post by Dr. Nick on 2006-08-03
Actually if you install "checkinstall" and get into the habit of using

sudo checkinstall 

as oppsed to 

sudo make install 

then removal is alot easier, checkinstall will build a .deb file after compiling and then you can install it, installing the .deb will allow removal through synaptic or regular .dpkg methods which will help keep your system cleaner using self compiled programs.

I think mplayer compiled from source is nicer if you build it against gtk2, I knew at one time it was still built against gtk1 so it doesnt look as nice as some other applications.

---

### Post by blueturtl on 2006-08-03
> ...you can also set the default application from here. Just select the radio button beside the app that you want (probably mplayer). Now you can just double click on the movie file instead of right clicking and "open with" mplayer


This is pure gold! Thank you endfx and Dr. Nick for shedding light on so many things at once! I'm not home, so I can't test these things immediately, but I will try your tips first thing tomorrow. Gotta love the forums. :p

---

