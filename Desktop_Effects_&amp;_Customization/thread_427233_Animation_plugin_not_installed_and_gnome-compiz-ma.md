---
title: "Animation plugin not installed and gnome-compiz-manager not working on feisty"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by equinox_child on 2007-04-29
Hi,
I'm using ubuntu-feisty with desktop effects enabled and I just installed the compiz-extras plugin set and tweaked a lot of the settings, which worked fine except for a few things:

1)  The animation plugin isn't installed for some reason. When I run gnome-compiz-preferences, it warns me about that. Also, when I use gconf-editor, animations isn't in the plugin folder under compiz. I have reinstalled the compiz-extras package twice. Still no luck. 

2) I've installed gnome-compiz-manager but I can't seem to run it from the terminal when I type it in. I can run the gnome-compiz-preferences but it doesn't have all the settings. 

3) Does anyone know where I can get some tutorial or guide on setting up the wallpaper plugin so that I can get different wallpapers on each face of the cube? I know where the wallpaper plugin options are in the gconf-editor but I have no clue on how to set them up. Im worried that if I change the wrong setting I'll mess up the entire compiz system :P

4) Similar to the above, does anyone know how to make the cube transparent on the top so that I can see the thru it when I rotate?

Any help with these would be really appreciated.
Thanks in advance :)

---

### Post by frup on 2007-04-29
Have you tried system > preferences > GL Desktop?

---

### Post by mikibg on 2007-04-29
> **frup said:**
> Have you tried system > preferences > GL Desktop?

and he can find there,,,,,,what?animation? no da man
animantion iz not in extra plug ,,,and if you want to have it U must install compiz 0.5

---

### Post by equinox_child on 2007-04-29
@frup: yup, i've tried that...the manager loads but has very limited options (useful, but limited). I can't find the animations configuration in there...

If I have to upgrade to compiz, i'll wait for the stable release. Thanks for the help on that, that strikes out the first one of my questions...i didn't actually expect replies so fast, im loving the ubuntu community :)

oh, and on the note of upgrading, i went to the compiz website and it says version 0.4 is the stable release now. However, when i open up synaptic and ask it to check for upgrades, it assumes the latest version (which came with feisty) is 0.3.x ... any ideas why that is so?

---

### Post by Zyppora on 2007-05-11
This is EXACTLY my problem! Except that for me, there's a 5th point: the Water plugin doesn't seem to work at all. I can set the shortcuts for both the raindrops and the pointer effect, but neither seem to have any effect (iow. the pointer and the desktop are still 'boring').

I've run into many issues trying to get Compiz to work (XGL non-functional, XGL slow as hell, Compiz gives error, system freeze (or slow enough to look like it), no cube, no rotating cube, etc. etc.), and now this. I've been skimming the net trying to figure out all of the answers, but it seems that this is pretty much the end of the line for me and asking here was the last thing I wanted to do, but the first thing that came up in me.

Is upgrading to 0.5 really the only way to get these to work? Coz I really don't feel like doing that just yet.

---

### Post by rootkowski on 2007-05-15
Hello everyone!

I'm having similar problems to yours. I'm trying to set different wallpapers for different desktops of the cube - no idea how to do that. And then the thing with water effect's not working either.

Anyway, you've been talking about different versions of compiz:

"i went to the compiz website and it says version 0.4 is the stable release now. However, when i open up synaptic and ask it to check for upgrades, it assumes the latest version (which came with feisty) is 0.3.x ... any ideas why that is so?"

i think I have an idea. This is what compiz.org says: 

"Compiz 0.4 is the stable version and is the successor of 0.2.2."

and

"Compiz 0.5 is the developmental version and is the successor of 0.3.6."

The version that came with feisty is 0.3.6. So that means the only version you can upgrade to is 0.5 which is still unstable. It's a real pity I didn't read that before I tried to install 0.4 on top of 0.3.6. I made the whole compiz system unstable and I decided to reinstall feisty. Well, now I know. And I will rather wait for 0.5 stable.

If I find any solution for any of the issues I'll post them here.

Good luck!

---

### Post by mikibg on 2007-05-15
if U have install beryl do not upgrade compiz ....First U must remove beryl .
I have problem after upgrade compiz 0.3.6 to 0.5  to install plug like animation and other
Some1 can post here how to install plug in compiz 0.5 ....
I do not find why they do not put all plug in extra compiz plug ...this is work in fiesty????

---

### Post by equinox_child on 2007-05-16
I got the water and snow plugins working. You have to go to the gconf-editor, go under apps, compiz, general, and there shud be one of the folders in there with an option for plugins that are loaded (im not at home at the moment so i can't say exactly where, but it'll be the top line on one of the folders). And if you attempt to edit the key, it will have a list of plugins in a very specific order (a plugin that requires another plugin is below it). Check what the water plugin is called exactly. and add that string to the bottom of the list. Then go to the water plugin settings and set your key-shortcuts for initializing. I'll try put a more descriptive process when I get home, but for those who are familiar with gconf-editor, you can try this.

On another, more pertinent note, I still can't get animation to work.

---

### Post by rootkowski on 2007-05-16
In configuration editor you go: apps/compiz/general/allscreens/options and then you choose the top key called active_plugins. In mine there are following plugins enabled: gconf, png, svg, decoration, wobbly, fade, minimize, zoom, inputzoom, cube, switcher, move, resize, place, scale, dbus, annotate, screenshot, clone, showdesktop, rotate, water. So I got the water effect working. :-)

Now I don't actually understand what animation you are after. At least I don't have any animation plugin, but if i go to GL Desktop, on the Workspaces tab there are options for Skydome and Animate. You can choose a picture there to set as a background for the cube. Is this the animation you can't get working?

---

### Post by equinox_child on 2007-05-17
The animation i'm talking about is a plugin that comes in extras which basically allows you to choose from a bunch of animations for windows opening,closing and minimize/maximizing...that is, u can set it so that when ur windows close, instead of fading out, they can for example, sort of dissapear like a mirage...its hard to explain...watch the video here to see what i mean
[http://www.youtube.com/watch?v=jy4TxLzReP8](http://www.youtube.com/watch?v=jy4TxLzReP8)
...that sort of thing...i've seen it in compiz videos...also seen it on the compiz website under plugins
[http://compiz.org/Plugins](http://compiz.org/Plugins)

I'll try to get it working today...i just haven't had time to think about or mess around with it this week...
I'm alos going to try to use a larger skydome image, a panoramic one this time and see if that works. That one shouldn't pose too much of a challenge but let's see how i go.
I got water and snow to work...snow is real pretty when ur not using the computer...But i switch both off when i'm doing serious work because they are way too distracting and i get distracted very easily :P

---

### Post by rootkowski on 2007-05-17
I got it working. :-D

Kind of anyway. I installed gnome-compiz-manager and gnome-compiz-manager-extra and i have no idea if that helped at all. Then i installed something like libtool using synaptic (trying to install the plugins i got an error message about the libtool thingy). Then in the terminal I cd'ed into the folder with (extracted) animation plugin and just ran "make install". I did the same about snow. Then i added the two entries (animation and snow) to the active_plugins key in Configuration Editor apps/compiz/general/allscreens/options.

Animation works very nice. The only thing I don't know is how to configure them - both animation and snow. They aren't in the GL Desktop. Maybe there's something in the Configuration Editor, I haven't checked yet.

PS. in case it did matter to install the gnome-compiz-manager packages you can find them there: [http://compiz.org/Gnome_Compiz_Manager]("http://compiz.org/Gnome_Compiz_Manager")

---

### Post by equinox_child on 2007-05-17
My make install still has errors after I install libtool :(
Do i need to place the folder somewhere specific before i make install...its currently on my desktop..
Here's a small amount of them...they go on for ages..

```
animation.c:5162: error: expected ')' before '*' token
animation.c:5220: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animPaintWindow'
animation.c:5272: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animGetWindowIconGeometry'
animation.c:5306: error: expected ')' before '*' token
animation.c:5844: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animDamageWindowRect'
animation.c:6165: error: expected ')' before '*' token
animation.c:6188: error: expected ')' before '*' token
animation.c:6219: error: expected ')' before '*' token
animation.c:6232: error: expected ')' before '*' token
animation.c:6245: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animPaintScreen'
animation.c:6263: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animInitDisplay'
animation.c:6288: error: expected ')' before '*' token
animation.c:6299: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animInitScreen'
animation.c:6346: error: expected ')' before '*' token
animation.c:6377: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animInitWindow'
animation.c:6420: error: expected ')' before '*' token
animation.c:6442: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animInit'
animation.c:6451: error: expected ')' before '*' token
animation.c:6457: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animDeps'
animation.c:6462: error: expected ')' before '*' token
animation.c:6468: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animVTable'
animation.c:6491: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/libanimation.lo] Error 1
```

Any ideas?

---

### Post by rootkowski on 2007-05-17
Maybe you should download the plugin again. Maybe the one you extracted is corrupt. I don't know really. Doesn't it give you any errors about missing libraries or libraries that don't meet the requirements (that they are too old or sth)?

I hade my plugins on the desktop too. so that at least shouldn't be a problem. Have you checked the gnome-compiz-manager and gnome-compiz-manager-extra? 

You can also try this: [http://forum.compiz.org/viewtopic.php?t=726](http://forum.compiz.org/viewtopic.php?t=726) or just generally look through compiz forum.

How did you get the snow plugin to work? Can you configure it? How?

---

### Post by rootkowski on 2007-05-17
I think I have messed something up with my compiz because now it doesn't start with the system :-(

---

### Post by equinox_child on 2007-05-17
i'll try redownloading...lets see how that goes...
btw, snow comes with extras(it did for me)...so i just added snow to the active_plugins key mentioned earlier in this post. And then i went to the snow options and set my initializing keys.
On a side note, don't you love it how most things in linux don't need a restart after you install? at most you restart the Xserver but even that's in extreme cases. Thank god i left windows.

---

### Post by rootkowski on 2007-05-17
Ok!
So I have the snow going now. It's cool!
And it is cool not having to restart the machine every time you install something. I agree.

But at the moment I'm trying to find out what it is i've done that compiz doesn't start with the system anymore. I reinstalled some packages and that didn't help. I wrote a new script for it - didn't help. I am almost going mad.

---

### Post by mikibg on 2007-05-17
ok problem with animation plug that U can not install shemas for this 
U can copy libanination.so to /usr/lib/compiz and gconf-editor app-compiz-general-allscreens-options right kick on active-plugs edit add and wrote animation 
and disable minize but u can not install shemas I try to copy animation shemas to compiz.shemas and do not work

---

### Post by rootkowski on 2007-05-18
I searched my computer for libanimation.so and there's nothing like that. Still the plugin works. Only that I can't change settings for it using GL Desktop.

---

### Post by mikibg on 2007-05-18
libanimation.so is in animation plug ....you can download plug and copy than
but why U do that ....install beryl 0.3.0

---

### Post by ReapeX on 2007-05-23
anyone has a link to a purge compiz and install beryl guide?

---

### Post by charles nicholls on 2007-05-24
If you are running feisty then compiz is installled by default, at least it is on this machine, I didnt uninstalll it but You probably could through synaptic, Beryl have a .deb at [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX)
which takes you through it step by step, hope this help

---

### Post by ReapeX on 2007-05-26
Awesome I downloaded beryl and I am keeping compiz for now (until I get use to Beryl completely).

---

### Post by nuir on 2007-06-16
I had the same problem for quite some time, but I managed to find a solution, hope it works for others:

1. Install the *compiz-dev* package, it's needed to compile compiz plug-ins. I installed it using Synaptic.
You can also install the *gnome-compiz-manager* package from here too.

2. Install the *libtool* libraries, I installed them from Synaptic as well, these are also needed to compile compiz plug-ins.

3. Download the *animation.tar.gz* file from the compiz web page if you don't already have it.

4. Untar the file to some directory.

5. Open a terminal and go to the directory where you unzipped the animation plug-in file. To build and install the plug-in the compiz wiki suggests to write the next commands:

```
./configure --prefix=/usr
make
sudo make install
```

the ./configure line didn't work for me, but it didn't matter, the plug-in was built and installed after all.

6. As someone already said, this only made the plug-in work, but no schema was installed so you can't configure any options. But if you look at the unzipped folder, there should be an animation.schema file right there. You can install this manually, using the terminal from the same directory as before, write the next code:

```
gconftool-2 --install-schema-file=animation.schema
```

Now, you should have the configuration options in the configuration editor:
/-->apps-->compiz-->plugins-->animation-->screen0-->options

Just remember to write the plug-in name in /-->apps-->compiz-->general-->allscreens-->options-->active_plugins (add "animation" to the active_plugins key to the right)

---

### Post by Wutzl on 2007-06-21
Nuir, you are the man! Thanks so much for your instructions - worked perfectly for me (although I got some error messages when compiling the animation plugin).

I switched from Beryl (too unstable) to compiz and was really missing the animations - you made my day!

---

### Post by dansued on 2007-06-21
after adding compiz-dev and libtool, I'm still getting these sort of errors,

```
animation.c:4199: error: 'Model' has no member named 'topHeight'
animation.c:4199: error: invalid operands to binary +
animation.c:4199: error: incompatible types in initialization
animation.c: At top level:
animation.c:4261: error: expected ')' before '*' token
animation.c:4312: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'animEnsureModel'
animation.c:4355: error: expected ')' before '*' token
animation.c:4414: error: expected ')' before '*' token

```

---

### Post by nuir on 2007-06-22
I think compiz needs some better documentation. Most of these problems seem to be related to missing dependencies. :-?
For those who still have some trouble, you can check the next links to see if you can find some info on to what libraries you may be missing:
This has a small how-to for installing compiz in ubuntu:

[http://compiz.org/Ubuntu_Installation_Guide]("http://compiz.org/Ubuntu_Installation_Guide")

It suggests adding a compiz repository to synaptic, maybe the packages from their repository work better... but I haven't tried.
In the next link, there's a list of all the dependencies required to compile compiz on a machine with Ubuntu Fiesty:

[http://forum.compiz.org/viewtopic.php?t=827]("http://forum.compiz.org/viewtopic.php?t=827")

Someone suggested earlier that maybe installing the *gnome-compiz-manager* and the *compiz-extra* packages might be needed as well.
Finally, try to look for info in the compiz site and forums. Good luck!

Note: I also forgot to tell that I too got some errors when compiling the animation plug-in, however despite these errors the plug-in was installed and it worked fine (except for the schema).

---

