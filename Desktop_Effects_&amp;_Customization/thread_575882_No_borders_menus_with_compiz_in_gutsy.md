---
title: "No borders/ menus with compiz in gutsy"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by mtgrocks04 on 2007-10-14
I have tried everything I could find, I have put the line in xorg.config, I have tried running compiz --replace -c emerald &. I cannot get borders working with compiz, I also cannot get beryl-manager to install. Is there some other way to get this issue corrected?

---

### Post by mtgrocks04 on 2007-10-14
I also noticed it said it could not start the plugin emerald, i have emerald installed

---

### Post by mtgrocks04 on 2007-10-14
Bump

---

### Post by patang on 2007-10-15
using gtk-window-decorator instead of emerald worked for me.

regards
Sid

---

### Post by Forlong on 2007-10-15
> **mtgrocks04 said:**
> I cannot get borders working with compiz
What type of graphics card?
> **mtgrocks04 said:**
> I also cannot get beryl-manager to install
Beryl is not in Gutsy's repos. The project is discontinued.

---

### Post by mtgrocks04 on 2007-10-15
Intel i810, I know beryl is discontinued, but I read that some people were using it to select compiz. How would I use gtk?

---

### Post by Forlong on 2007-10-15
If you want to use gtk-window-decorator, you have to start it manually (via [Alt]+[F2])
Or you just remove emerald.
> **mtgrocks04 said:**
> I also noticed it said it could not start the plugin emerald, i have emerald installed
Could you please post that output?

---

### Post by mtgrocks04 on 2007-10-15
This is the output, all my effects work for minimize and maximize and create, I just do not get borders. I tried to run gtk-window-decorator, but when i tried to run it in alt-f2 it didnt work and when i tried to run it in konsole it says i need to install compiz-gnome, but will that work since im running kubuntu?

greg@greg-laptop:~$ Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'rotate'
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'cubecaps'

---

### Post by Forlong on 2007-10-15
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by mtgrocks04 on 2007-10-15
```
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager
ii  compiz-dev                                 1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - deve
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1            Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2            Collection of plugins from OpenCompositing f
ii  compiz-kde                                 1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - KDE
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1            Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1              Decorator for compiz-fusion
ii  libcompizconfig-backend-kconfig            0.0+git20070912-0ubuntu1              KConfig Settings library for plugins - OpenC
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3            Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1              Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1            Compiz configuration system bindings

```

---

### Post by chunchengch on 2007-10-15
According to my experience, Emerald 0.3 does not work fine with Beryl, you have to switch to Compiz Fusion, otherwise the border-missing problem will always bother you.

---

### Post by mtgrocks04 on 2007-10-15
I'm not using beryl, I am running gutsy and compiz fusion which is standard with gutsy.

---

### Post by Tachyon1000 on 2007-10-15
Go into Preferences>Advanced Desktop Effect Settings and turn on the window decorator plugin.  If that does not work, turn it off and on again.  Alernatively, go into Appearance>Visual Effects>Custom>Preferences and do the same thing.  I tried using Emerald as well and it has not worked for me. I got the borderless windows.  Only thing that solved it was to turn the Compiz window decorator on.

---

### Post by Tachyon1000 on 2007-10-16
Yeah, emerald is funny.  I had to turn off desktop effects then turn them back on to get borders back and probably activate the window decorator.  For the themes I have seen in emerald, it doesn't seem to be worth the hassle.

---

### Post by teasum on 2007-10-16
I'm having the same issue; however, I can't resolve it because I do not have "Advanced Desktop Effect Settings" in my System > Preferences menu.  Is there a way to enable the aforementioned window manager plugin via the command line?  Also, any idea how to get this option in my menu?  I looked in the main menu preferences in case this option was simply grayed out, but it's not there at all. 

Thanks!

---

### Post by mtgrocks04 on 2007-10-16
I have looked in the advanced desktop settings manager. I can see the option, however it will not let me activate it, in fact I cannot activate any of the options, any thoughts on how to fix this?

---

### Post by talent03 on 2007-10-16
The way I got the borders back was to remove emerald from the package manager and type compiz in the terminal. That got me the original borders back.

---

### Post by JBAlaska on 2007-10-16
Try removing ccsm in synaptic and restarting x, then you should see "Advanced Desktop Effect Settings".

When you start "Advanced Desktop Effect Settings" , go to the "windows decorations" plugin and type emerald in the command box (needs to have emerald installed) "sudo apt-get emerald"

---

### Post by teasum on 2007-10-16
I still have this problem.

2 updates:
1)  I also cannot find "Appearance>Visual Effects>Custom>Preferences".  Under the 'Visual Effects' tab of the 'Appearances' window, there is no custom of preferences option.  Perhaps I do not have these menu options because I upgraded rather than doing a clean installation?  I don't know.
2) I do not have emerald installed, according to synaptic, and yet I have the same problem as the OP, namely no window borders when running any level of 'visual effects'.

Any suggestions?

---

### Post by teasum on 2007-10-16
> **JBAlaska said:**
> Try removing ccsm in synaptic and restarting x, then you should see "Advanced Desktop Effect Settings".

When you start "Advanced Desktop Effect Settings" , go to the "windows decorations" plugin and type emerald in the command box (needs to have emerald installed) "sudo apt-get emerald"

Thanks for the tips.  However, I see no package named 'ccsm' in synaptic.  I'm confused...

---

### Post by mtgrocks04 on 2007-10-16
I have the advanced desktop settings in my kmenu. I just simply cannot select any optiions in it.

---

### Post by mtgrocks04 on 2007-10-16
UPDATE:
   problem fixed. I reinstalled emerald, and then in the advanced desktop manager I had to select the preferences tab and then activate the plugins through there. now it works perfectly. Thanks for all the help.

---

### Post by Forlong on 2007-10-17
> **teasum said:**
> I see no package named 'ccsm' in synaptic.  I'm confused...
The package is called **compizconfig-settings-manager** :)

---

### Post by ulli.winter on 2007-10-18
> **JBAlaska said:**
> Try removing ccsm in synaptic and restarting x, then you should see "Advanced Desktop Effect Settings".

When you start "Advanced Desktop Effect Settings" , go to the "windows decorations" plugin and type emerald in the command box (needs to have emerald installed) "sudo apt-get emerald"

i had the same problem as described: gutsy+effects=no border
i've added compizconfig-settings-manager via synaptic to modify window decoration plugin as described above - now it works!

---

### Post by cypresstwist on 2007-10-19
having the same problem. removed all compiz-related packages, reinstalled them, enabled/disabled window decoration in cssm, still no borders. :(cypress@malacka:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1               OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1               OpenGL window and compositing manager
rc  compiz-extra                               0.3.6.1-0ubuntu2                           extra third party plugins for compiz
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1                 Collection of extra plugins from OpenCompositing for C
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2                 Collection of plugins from OpenCompositing for Compiz
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1               OpenGL window and compositing manager - GNOME window d
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                          OpenGL window and compositing manager - Gtk window dec
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1               OpenGL window and compositing manager - plugins
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1                 Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1                   Decorator for compiz-fusion
ii  gnome-compiz-manager                       0.10.3-0ubuntu2                            Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1                 Settings library for plugins - OpenCompositing Project
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3                 Settings library for plugins - OpenCompositing Project
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1                   Decoration engines for compiz-fusion
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                            Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1                 Compiz configuration system bindings

---

### Post by meimato on 2007-10-19
Had the same problem and resolved enablig emerand in ccsm; but it's not possible to use gtk-window-decorator instead of emerald, as it was in Feisty?

P.S. I can I enable the trasparence when moving windows?

---

### Post by Forlong on 2007-10-19
> **meimato said:**
> but it's not possible to use gtk-window-decorator instead of emerald, as it was in Feisty?
If you want to use GWD you have to either remove Emerald or start it manually via [Alt]+[F2]:
```
gtk-window-decorator --replace
```
(adding it to the startup programs should work too)
> **meimato said:**
> P.S. I can I enable the trasparence when moving windows?
See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) under *Transparency &#8594; Transparent windows on the move*


@cypresstwist: you shouldn't use gnome-compiz-manager and ccsm at the same time.

---

### Post by ravenus on 2007-10-19
Thanks for that helpful blog, Forlong :D

---

### Post by dwasifar on 2007-10-19
I have tried everything in this thread and I still can't get borders working with visual effects.  I only get borders when the visual effects are set to None in Appearance>Visual Effects tab.  Also, when the window borders are gone, the contents of any terminal window I have open are invisible.

When I start compiz manually I get this:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0111 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```

And here is dpkg -l | grep compiz

```
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1 OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1 OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1   Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2   Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1 OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1 OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1   Compiz configuration settings manager
ii  gnome-compiz-manager                       0.10.3-0ubuntu2              Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1   Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3   Settings library for plugins - OpenCompositi
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2              Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1   Compiz configuration system bindings

```

---

### Post by dwasifar on 2007-10-19
> **dwasifar said:**
> I have tried everything in this thread and I still can't get borders working with visual effects.  I only get borders when the visual effects are set to None in Appearance>Visual Effects tab.  Also, when the window borders are gone, the contents of any terminal window I have open are invisible.

When I start compiz manually I get this:

```
Checking for Xgl: not present.
.... 
```


AHA.  Should have caught that before I posted.  Installing xserver-xgl from Synaptic solved the problem.

---

### Post by Dyegov on 2007-10-19
I have done all that has been said in here, and still don't get window borders. Please help!!!

---

### Post by Forlong on 2007-10-19
> **Dyegov said:**
> I have done all that has been said in here, and still don't get window borders. Please help!!!
Honestly, what do you expect from us?
We know nothing about your hardware, drivers etc.
Your profile even says you're on Windows...

We'er not clairvoyant, you know.

---

### Post by Dyegov on 2007-10-19
Well, I'm sorry, but you could have said it better . . . 

Anyway, I'm not a tech guy; I only know I have an nVidia card which actually has it's drivers (restricted) and all of that. The windows borders worked fine until I installed Advanced Desktop Effects Settings, to activate the cube and other nice effects . . . It worked fine until I reboot. Now all the effects work alright (including the cube) but I have no window borders . . . :confused:

---

### Post by F1r3 on 2007-10-19
I have an nvidia graphics card as well and had a lot of the same problems posted in this thread. 
No borders and my terminal windows came up white.
I looked around for a while and found this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Restarted X and everything worked for me.

---

### Post by Dyegov on 2007-10-19
> **F1r3 said:**
> I have an nvidia graphics card as well and had a lot of the same problems posted in this thread. 
No borders and my terminal windows came up white.
I looked around for a while and found this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Restarted X and everything worked for me.

Well, that actually worked!! Now I see the borders, but my theme was changed to a reddish thingy. I tried to change the theme back to human through Appearance, but it doesn't work . . .

---

### Post by praxis22 on 2007-10-19
Sounds like the default Emerald/Beryl theme. Go into the Emerald Theme Manager, (big green diamond in System -> Preferences) and change it there.

---

### Post by Dyegov on 2007-10-19
I have tried that but there's no no other choice :(

---

### Post by rmx.dave on 2007-10-20
Still experiencing this problem as well. Compiz will start and I'll get all of the effects, but I have no borders or title bar. They are there, I can click above the window and drag it around...its just invisible. I have emerald installed and have the window decorations turned on in CCSM. Also, I try gtk-window-decorator, but I get this error:

```
gtk-window-decorator: error while loading shared libraries: libwnck-1.so.18: cannot open shared object file: No such file or directory

```

Any thoughts? I'm using integrated i915 graphics on the i810 driver. 

Thanks!

---

### Post by azdragon on 2007-10-20
I was having the same problem, the white box in the terminal, and no borders.  My problem was just like some of the others on here.   I did the nvidia command and it fixed all my problems with borders and such.

Thanks.

---

### Post by praxis22 on 2007-10-20
> **rmx.dave said:**
> 
```
gtk-window-decorator: error while loading shared libraries: libwnck-1.so.18: cannot open shared object file: No such file or directory

```

Any thoughts? 
Open synaptic and search for **libwnck** this will return about 5 entries or so, I have the following installed:

libwnck22
libwnck-common
libwnck-dev

If you're not going to be compiling stuff, then you can ignore libwnck-dev

Then try again. The problem is the binary is failing as it cannot find a shared library, for more details on what that means see this link:

[http://en.wikipedia.org/wiki/Library_(computer_science](http://en.wikipedia.org/wiki/Library_(computer_science))

---

### Post by praxis22 on 2007-10-20
> **Dyegov said:**
> I have tried that but there's no no other choice :(

Click on the green diamond, then click on the **repositories** tab there should be two buttons one for GPL'ed themes, and one for non GPL'ed themes, click one or both, and this will download lots of new GUI themes for you to experiment with.

---

### Post by freed0m on 2007-10-20
This can help too, try to remove 

rm -rf ~/.config/compiz

then try to activate Compiz from System -> Preferences ->  Appearance -> Visual Effects -> Extras

Cheers

---

### Post by rmx.dave on 2007-10-20
> **praxis22 said:**
> Open synaptic and search for **libwnck** this will return about 5 entries or so, I have the following installed:

libwnck22
libwnck-common
libwnck-dev

If you're not going to be compiling stuff, then you can ignore libwnck-dev

Then try again. The problem is the binary is failing as it cannot find a shared library, for more details on what that means see this link:

[http://en.wikipedia.org/wiki/Library_(computer_science](http://en.wikipedia.org/wiki/Library_(computer_science))

Yeah, I should have mentioned that I already searched for those libraries and they were there...which makes this even more strange.

I also tried deleting the /.config/compiz folder as suggested above, with no luck.

---

### Post by madhatter84gn on 2007-10-20
You may try checking the compiz settings in the compiz manager. I had a problem similar to this and still have to some extent. For some reason Windows decorations keeps getting turned off. Once I enable the decorations checkbox then all is well and I get the borders and menus. The problem I am still having is after a reboot even if I choose close and save the settings, compiz always defaults back to no windows decorations and then I have to go into the manager and change enable it again.

---

### Post by jhbruin on 2007-10-20
I had a similar problem this morning. First my manual nvidia drivers update was causing x to load in failsafe mode. I uninstalled the drivers and reinstalled them using ENVY ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) which fixed my problem.

Then I tried to re-enable my compiz/emerald sessions using compiz --replace and emerald --replace. This didn't work. I just ended up with no borders and buttons. So I disabled it again in Sessions.

Finally, I went to System -> Preferences -> Appearance -> Visual Effects Tab  and ticked the "Extra" bubble. This also immediately gave me the no borders. I saved the settings and restarted X (Alt+Ctrl+Backspace). Magically my window decorations (emerald) worked, as did all the rest of compiz.

:KS Hooray for Gusty Gibbon!

---

### Post by rmx.dave on 2007-10-20
Yeah Window Decorations are definitely enabled in CCSM. Sigh...

I have a hunch though. When it tells me that it cant find that libwnck.so or whatever file, could it be because its trying to look into an older location from my last compiz install? I removed compiz completely before I upgraded, but perhaps i missed something and its looking for old dependencies?

---

### Post by BoredOutOfMyMind on 2007-10-20
> **rmx.dave said:**
> Yeah Window Decorations are definitely enabled in CCSM. Sigh...

I have a hunch though. When it tells me that it cant find that libwnck.so or whatever file, could it be because its trying to look into an older location from my last compiz install? I removed compiz completely before I upgraded, but perhaps i missed something and its looking for old dependencies?

It is broken in my clean install also. 

So much for "out of the box compiz"

This and sound are NEVER going to solve bug #1
:mad:

---

### Post by rmx.dave on 2007-10-20
> **BoredOutOfMyMind said:**
> It is broken in my clean install also. 

So much for "out of the box compiz"

This and sound are NEVER going to solve bug #1
:mad:

I hereby request the project be named Compiz CONFUSION. :)

---

### Post by markballermann on 2007-10-20
Compiz works better after I did this, though not perfect:

```
sudo ln -s /usr/lib/libwnck-1.so.22.2.3 /usr/lib/libwnck-1.so.18
```

Awn wouldn't work before this, and now it has started working too.

---

### Post by rmx.dave on 2007-10-20
> **markballermann said:**
> Compiz works better after I did this, though not perfect:

```
sudo ln -s /usr/lib/libwnck-1.so.22.2.3 /usr/lib/libwnck-1.so.18
```

Awn wouldn't work before this, and now it has started working too.

Well, that solved the error with gtk-window-decorator looking for the libwnck file. Now when I try running gtk-window-decorator i get this error:

```
Could not acquire decoration manager selection on screen 0 display ":0.0"

```

I'll do some googling on this message for now.

---

### Post by rmx.dave on 2007-10-20
I haven't come up with anything and I'm getting a little tired of hunting. Someone has to have the answer. Help me? I have candy :)

---

### Post by BoredOutOfMyMind on 2007-10-20
Did anyone get the Emerald-Themes working?

I googled and found a deb to download and installed it but it does not work..

Even the default Emerald would be better than Clearlooks.....

I have cube and wobbly windows so I will work with it. 

On to the Database!

:guitar:

---

### Post by CFBauer on 2007-10-21
> **dwasifar said:**
> AHA.  Should have caught that before I posted.  Installing xserver-xgl from Synaptic solved the problem.
This worked for me with my window border issue, which seemed similar to yours.  Thanks.

---

### Post by JackyBoy on 2007-10-21
I'm not sure how much you all can do for me, but I'm having quite a few problems with compiz.  

I've installed ccsm and beryl, and I'm still having problems with my window borders not showing up.  In the ccsm I have Window Decoration enabled, but every time I restart the x it gets turned off.  To get my window borders to show up, every time I boot I have to go into the ccsm and re-enable Window Decoration, then go to the terminal and enter "compiz".  After that the window borders work fine.  Is there any way I can fix this so I don't have to repeat the above process every time I restart?

I also can't get any of the window open/close/minimize/maximize animations to work even though I have Animations turned on in the ccsm.  Is this a bug issue or is there something else wrong with my configuration?

I'm pretty new to Linux so any help is greatly appreciated :D

---

### Post by rmx.dave on 2007-10-21
> **JackyBoy said:**
> I'm not sure how much you all can do for me, but I'm having quite a few problems with compiz.  

I've installed ccsm and beryl, and I'm still having problems with my window borders not showing up.  In the ccsm I have Window Decoration enabled, but every time I restart the x it gets turned off.  To get my window borders to show up, every time I boot I have to go into the ccsm and re-enable Window Decoration, then go to the terminal and enter "compiz".  After that the window borders work fine.  Is there any way I can fix this so I don't have to repeat the above process every time I restart?

I also can't get any of the window open/close/minimize/maximize animations to work even though I have Animations turned on in the ccsm.  Is this a bug issue or is there something else wrong with my configuration?

I'm pretty new to Linux so any help is greatly appreciated :D

Hmm, I can't get mine to come on at all. 

I'm starting to get used to the old-school no effects interface...

---

### Post by Jose Catre-Vandis on 2007-10-21
> **JBAlaska said:**
> Try removing ccsm in synaptic and restarting x, then you should see "Advanced Desktop Effect Settings".

When you start "Advanced Desktop Effect Settings" , go to the "windows decorations" plugin and type emerald in the command box (needs to have emerald installed) "sudo apt-get emerald"

Yeah, this worked for me :)

---

### Post by rmx.dave on 2007-10-22
I still haven't gotten anything. But I see that Compiz 0.6 is released. Maybe I'll kill all compiz that's installed and try compiling? Any objections?

---

### Post by markballermann on 2007-10-22
Hi Dave, I gave up on the upgrade route, I have my machine working after a fresh install:
[http://ubuntuforums.org/showthread.php?p=3601164#post3601164](http://ubuntuforums.org/showthread.php?p=3601164#post3601164)

Hats off to you if you have the time/energy to track down this problem, but maybe going with a fresh install is something to consider.

---

### Post by rmx.dave on 2007-10-22
Well, you can put your hat back on. I think I'm just going to do a fresh install. Not just because of Compiz (I can live without that), but because of the little quirks I've accumulated over the years that I just don't feel like ironing out. Oh Lord, now time to back up 40gb of docs

---

### Post by nogg3r5 on 2007-10-22
> **F1r3 said:**
> I have an nvidia graphics card as well and had a lot of the same problems posted in this thread. 
No borders and my terminal windows came up white.
I looked around for a while and found this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Restarted X and everything worked for me.

Worked for me. What does the command actually do?????

---

### Post by daynah on 2007-10-22
> **dwasifar said:**
> AHA.  Should have caught that before I posted.  Installing xserver-xgl from Synaptic solved the problem.

After trying all of the other methods and messing mup my X a few times, this was my solution! To any others trying to find it, I hope ya'll check this first. Just quickly trying to install it will tell you if it was the problem or not. :)

Thanks everyone.

---

### Post by carlos1992 on 2007-10-24
just download the ADES and see the tab option thats it

---

### Post by leona on 2007-10-28
> **JBAlaska said:**
> Try removing ccsm in synaptic and restarting x, then you should see "Advanced Desktop Effect Settings".

**When you start "Advanced Desktop Effect Settings" , go to the "windows decorations" plugin and type emerald in the command box (needs to have emerald installed) "sudo apt-get emerald"**

I did something slightly different but it made it work, I went to add/remove and under 'other' there is the advance desktop effects' app (silly place to put it, should be under system imho), enabled that, then I was able to get this menu item under System>referenaces , then followed the 2nd part of the instructions above, restarted and now have my borders, back, 
**Thank you very much.**

edit to add, sorry no this didn't solve my problem, it just turned the effects off which gave me my borders back, drat, looks like I can only have one or the other, border or effects.

---

### Post by MegaJim on 2007-10-28
> **F1r3 said:**
> I have an nvidia graphics card as well and had a lot of the same problems posted in this thread. 
No borders and my terminal windows came up white.
I looked around for a while and found this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Restarted X and everything worked for me.

Just posting to say thankyou this fixed my nvidia compiz config on feisty.  Much appreciated.

---

### Post by leona on 2007-10-30
> **F1r3 said:**
> I have an nvidia graphics card as well and had a lot of the same problems posted in this thread. 
No borders and my terminal windows came up white.
I looked around for a while and found this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Restarted X and everything worked for me.

Fixed my probs too.

---

### Post by Alienist on 2007-10-31
Also check to see if your video driver is actually running, especially if it's a restricted driver. Do this by going to System-->Administration-->Restricted Drivers Manager. This worked for me. For some reason it was disabled after I reconfigured Xorg.

---

### Post by garydale on 2008-03-12
> **Tachyon1000 said:**
> Go into Preferences>Advanced Desktop Effect Settings and turn on the window decorator plugin.  If that does not work, turn it off and on again.  Alernatively, go into Appearance>Visual Effects>Custom>Preferences and do the same thing.  I tried using Emerald as well and it has not worked for me. I got the borderless windows.  Only thing that solved it was to turn the Compiz window decorator on.

I'm running Gutsy Gibbon and got the same problem each time I tried an install. I did this twice and it's something in the updates after the initial install. Having read of the same problem occurring with ATI cards, it's not the restricted NVidia driver.

The menu choices are a little different in Gutsy. I don't have an Advanced Desktop Effect Settings and the Appearance | Preferences | Visual Effects  (again, not the same as reported above) needed to be set to None. Turning them back on removes the borders again.

---

### Post by gi2k15 on 2008-05-01
Worked like a charm here. Thanks!

---

### Post by Derviansoul on 2008-05-06
Hello everyone

i've just had this problem after removing compiz and installing back again on gutsy.
after trying everything on google and on this topic i found compiz troubleshooting webpage.

for the lazy ones here it is the commands that worked for me i had a windows decorator running though:
> 
here may be a problem with the way Compiz is being started. Enter this command into a console window to find out how and whether Compiz is running:

```
ps ax | grep compiz
```

If you don't see a command starting with "compiz" or "compiz.real" in the output, then Compiz is failing to start altogether. Please refer to the Common Mistakes section above to see whether anything describes your situation. Also check the Setup article to see whether your X server was properly configured.

If you do see a "compiz" or "compiz.real" command in the output, check whether "ccp" is part of the command line. The ccp plugin is required for Compiz to interact with settings made in ccsm. If it's missing from your Compiz command line, you should edit your startup process to include ccp in Compiz's command line, as in this example:

```
compiz --replace ccp
```

If this setting works until u restart or until you log in back again, then:

```
sudo gedit /usr/bin/compiz
```

then on the line 66 where it says:

```
COMPIZ_OPTIONS="--ignore-desktop-hints --replace" 
```

please edit it and change to be something like this:

```
COMPIZ_OPTIONS="--ignore-desktop-hints --replace ccp" 
```

and restart compiz manually to check if it works

```
 compiz
```

for everyone else that might have this problem still, the [link]("http://wiki.compiz-fusion.org/Troubleshooting#head-86425eda7d8a5726e38eac05d62bbdf8d6067004")

I'm not an expert,but this was the fix that i could get after a few search and looking into the compiz configuration file.

btw i have an ati graphic card and no emerald installed!
Hope this helps.
regards

---

