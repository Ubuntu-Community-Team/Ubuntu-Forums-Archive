---
title: "xscreensaver"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by twodogs on 2007-04-21
hi,

i am new to ubuntu and beryl and i really love it.  ubuntu is working really good and Feisty is the best ever.  has anyone been using the xscreensaver glmatrix trick.  i call it a trick because i cant get it to work yet.  i open console and type in 'xscreensaver-demo' and select glmatrix screensaver.  then in terminal 'xscreensaver-command -activate'  the screen goes black and starts matrix code but I don't want the black.  i want to see my desktop thru the code.  on the 'screensaver preferences' box, advanced tab, i have 'image manipulation' and 'fading and colormaps' boxes unchecked.  still no go!  any help would be appreciated!!

if you don't understand, go here --> [http://www.youtube.com/watch?v=kYgV2GlsufI](http://www.youtube.com/watch?v=kYgV2GlsufI) and watch the 'My Ubuntu Beryl Matrix 3D Desktop.'  it rocks!

TwoDogS out!

---

### Post by TadH on 2007-11-08
dude ive been trying to get that to work for weeks and no luck still

---

### Post by nickelby on 2007-11-09
For the background with the moving Matrix, you can use a program called "xwinwrap". It works something like Dreamscene for Windows but better since you can use the modules in XScreensaver, video files, etc. as your background :-)

---

### Post by Jaren15949 on 2007-12-07
This has to do with your graphics drivers. Everytime I reinstall ubuntu, I need to get NVIDIA _fully_ running before I can view any openGL screensavers. Otherwise, they just show blank screens.

---

### Post by glymph on 2007-12-22
I was able to achieve something similar using devilspie, to force glmatrix to run on the background, screenshot here: [http://rowla.dyndns.org/gallery/v/screenshots/glmatrix_desktop.png.html]("http://rowla.dyndns.org/gallery/v/screenshots/glmatrix_desktop.png.html")

Dom :)

---

### Post by curtis1552 on 2008-02-02
once you get the screensaver to work type this in the command line to run the screensaver.

xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/xmatrix -window-id WID -small -delay 50000 -density 60 -crack

Your path to the screeen  saver might be different. Also I am using the xmatrix not the GLmatrix, (the crack is the intro segment of the screensaver)
This runs it in the background as oposed to transparent in the foreground.
However, you loose access to your desktoip icons.

---

### Post by glymph on 2008-03-20
A similar effect can be achieved with the GLMatrix screensaver; I set the -no-rotate option so it doesn't give me vertigo ;-)

xwinwrap -g -ni -argb -fs -s -st -sp -b -nf --   /usr/lib/xscreensaver/glmatrix -no-rotate  -window-id WID

---

### Post by Kogitsune on 2008-03-20
> **nickelby said:**
> For the background with the moving Matrix, you can use a program called "xwinwrap". It works something like Dreamscene for Windows but better since you can use the modules in XScreensaver, video files, etc. as your background :-)

I looked up xwinwrap, and would really appreciate instructions as to how to go about installing it. The download setup on the main xwinwrap website is very alien to me, so if someone could post some simple instructions or something to type into the terminal that would allow me to install xwinwrap, that'd be really cool.

My purpose for installing this is to use an animated .gif file as a desktop background. If that isn't possible with this program, please say so. I've been told before that an animated .gif can't be used as a Desktop background, and this program was mentioned there too.

If it can play video files and screensavers, it should be able to play a .gif file, right?
If not, when will .gif backgrounds be implemented? 

(Sorry for reposting questions you guys have probably seen way too many times before)

---

