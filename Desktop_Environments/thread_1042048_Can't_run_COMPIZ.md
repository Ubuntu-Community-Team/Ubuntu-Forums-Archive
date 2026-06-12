---
title: "Can't run COMPIZ"
date: 2009-01-17
forum: Desktop Environments
---

### Post by coss_cat on 2009-01-17
Hello everyone,

I tried to install COMPIZ and get the beautiful effects on my desktop, but I have a very nasty error that keeps appearing all the time: 

"There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly."

I used compiz-check, and the result is this:

"Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8600M GT (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]"

Running nvidia-setting showed no problems or what so ever about xgl or 3D rendering.
When running Compiz by itself I get also this "Checking for Xgl: not present. "

Can anyone please help?

Thank you,

---

### Post by ajcham on 2009-01-17
> When running Compiz by itself I get also this "Checking for Xgl: not present. "
You can safely ignore this - it's not relevant as you have an Nvidia card, so do not require XGL.

As for…
> "There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly."

How did you install Compiz?  From what I've read see this only occurs when you choose another method, rather than installing the version in the repos. In any case, it would seem that compiz should run anyway — it is only the Scale plugin that is affected. Potential fixes are altering the Scale plugin's parameters in Compiz Settings Manager or installing additional Compiz libraries (I'm not sure which) from the repos.

If you did use an alternative installation method, I would recommend removing it first and installing the Ubuntu supported one.  You may find this is all you need to do, but if not then have a look at the other fixes.

---

### Post by coss_cat on 2009-01-17
Thank you ajcham.
The comment was very useful. However, installation was done using the native repos for Ubuntu, in add/remove utility that comes with the OS. I found that installing SCCSM (Simple Compiz Config Settings Manager), did the job well, witch means that now I have full functionality of the Compiz environment tool.

For those who had the same problem as I did, I recommend first uninstalling the compiz package and after that install SCCSM. After this under the Main Menu/ System/ Preferences/ Appearance at the visual effects tab, you'll find Custom (along with None, Normal, Extra that were before installation). Press the Preferences tab and this is it.

An other way to do it is under Main Menu/ System/ Preferences/ Advanced Desktop Effects Settings. There you go.

Thank you,

---

