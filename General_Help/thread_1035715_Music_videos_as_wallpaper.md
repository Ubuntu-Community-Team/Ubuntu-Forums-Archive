---
title: "Music videos as wallpaper"
date: 2009-01-10
forum: General Help
---

### Post by Kinrui on 2009-01-10
Does anyone think its possible to play music videos as a wallpaper from your desktop? Extra credits if the videos are streamed from youtube.

---

### Post by Sjums07 on 2009-01-12
i have made some reseach on it.. and if you can get a html as wallpaper, then yes :p

```
<html>
<head>
<title>Wallpaper</title>
</head>
<body bgcolor="#030303">
<center><br/><br/><br/>
<object width="425" height="344"><param name="movie" value="http://www.youtube.com/v/7v3KCAJwJK8&hl=en&fs=1"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/7v3KCAJwJK8&hl=en&fs=1" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="425" height="344"></embed></object>
</center>
</body>
</html>
```

that will show a vid with nothing else but the vid ;D hope it helps :D

---

### Post by Wartender on 2009-01-12
or you can use xwinwrap, which is a nifty appliaction that will display videos or screensavers on your desktop. to install it, you'll need these packages
```
sudo apt-get install xorg-dev build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs
```
after installing those, type this in
```
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
```
then
```
cd xwinwrap]
```
and finally, 
```
make
```
then you can make a symbolic link in your bin folder by doing this:
```
sudo ln -s /usr/src/xwinwrap/xwinwrap /usr/bin/
```
to use it for videos, type this in
```
nice -n 15 xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -nosound /path/of/file.avi -loop 0
```
remember to switch the /path/of/file.avi with the actual path of the video you want to show.
the options that are used for xwinwrap are:
xwinwrap [-g] [-ni] [-argb] [-fs] [-s] [-st] [-sp] [-a] [-b] [-nf]
[-fl] [-o OPACITY] &#8212; COMMAND ARG1&#8230;
-ni = no input
-fs = fullscreen
-s sticky 
-st skip taskbar 
-sp skip pager 
-a above 
-b below 
-nf noFocus
-o opacity sretty self-explanatory, you need a value between 0 and 1
also, if you want to display a screensaver, her is an example:
```
nice -n 15 xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -root -window-id WID
```
you can switch glmatrix with any other screensaver in that folder.
hope this helps! as for the streaming from youtube i don't know...
p.s. i got this info from [here]("http://freetimesblog.wordpress.com/2008/06/14/desktop-animato-con-xwinwrap/"). but it's in italian so i translated.

---

### Post by sendblink23 on 2009-01-12
Pues mano, yo para entretenerme un ratito.... decidi hacer el test a eso... =P

I tried testing on that...  it does place the video (I used a screensaver), and what happened it does start playing... but many complications...  its seems like a huge fight between the *background video* VS the current desktop...

as of my testing on my Ubuntu 8.10  ...  it was messing up the whole desktop.. making it on Usable *The Video was simply being Over the whole screen, but moving the mouse showed a bit what was actually on the desktop... really fuzzy*  

.. yeah I was in panic...    no worries

so I simply turned off my Computer *Manually (holding the Off button of the computer) and it actually restarted normally Ubuntu, without the video playing

At least it was fun, that it almost worked for me.

I'd have to say, someone else should test it.. to see if the video conflict with Desktop error happens the same as me, on Ubuntu 8.10.


se cuidan .. chevere el FIND de eso broo

---

### Post by Wartender on 2009-01-12
oh yeah i remember that hapeened to me the first time i tried using it on 8.10... i don't remember what i did to fix it though, or even if i did anything and it just worked once... btw if that happens you don't have to turn off the computer, try to see if you can close the terminal you opened the program in, and if that doesn't work and you can't do anything else use ctrl+alt+backspace, that'll restart x (it'll take you to the login screen)

---

### Post by sendblink23 on 2009-01-12
> **Wartender said:**
> oh yeah i remember that hapeened to me the first time i tried using it on 8.10... i don't remember what i did to fix it though, or even if i did anything and it just worked once... btw if that happens you don't have to turn off the computer, try to see if you can close the terminal you opened the program in, and if that doesn't work and you can't do anything else use ctrl+alt+backspace, that'll restart x (it'll take you to the login screen)

Yeah I know that obviously, no matter what.. pressing the *holding the turn off Button* is more effective  ;) since it won't save any current settings after shutting down inside running any OS.

But anyways I just tried through VirtualBox on Ubuntu 8.04 distro, and it worked perfectly ...  well I'll surf around to see the solution on 8.10, since yes you have just confirmed that you had managed to fix it.

---

### Post by sendblink23 on 2009-01-12
Dude.. LINUX is not an iPhone nore iTouch ...  :P  (you just copied the same html code of how it was done video wallpaper without the release of vWallpaper on 2.0 FW & above, what Saurik created, after his creation in Winterboard)  but yup it should work...  since I've seen it done on windows doing it that same way, on XP (I first saw it on a Virus... then I manipulated to work as a normal wallpaper, that was years ago.

Now how can we implement this on Linux, since when it was on Windows XP, that i can remember it was quite as simple as just placing an HTML inside the Windows Folder, I just can't remembered how it was named that html file.


blahh ...  I know this way.. will be much better than doing a package install, it would be simply making an HTML and save it, and run a command to activate it...  then open Sessions  and save that command, So that it will always turn on automatically on every restart of Ubuntu.




> **Sjums07 said:**
> i have made some reseach on it.. and if you can get a html as wallpaper, then yes :p

```
<html>
<head>
<title>Wallpaper</title>
</head>
<body bgcolor="#030303">
<center><br/><br/><br/>
<object width="425" height="344"><param name="movie" value="http://www.youtube.com/v/7v3KCAJwJK8&hl=en&fs=1"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/7v3KCAJwJK8&hl=en&fs=1" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="425" height="344"></embed></object>
</center>
</body>
</html>
```

that will show a vid with nothing else but the vid ;D hope it helps :D

---

