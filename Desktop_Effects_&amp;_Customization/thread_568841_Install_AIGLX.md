---
title: "Install AIGLX"
date: 2007-10-06
forum: Desktop Effects &amp; Customization
---

### Post by ASPCartman on 2007-10-06
Ho all. So i have removed my ATI card from system and reinstalled gutsy. Now i have Nvidia 6150 (yeah i know sucks, but its nvidia). I wanna install compiz fusion + aiglx.

So how can i do it? (I know how to install compiz fusion. I mean istall aiglx)
Im asking cos i cant find any guide. I saw guides of installing XGL (instaling fglrx then editing session etc) But nothin for AIGLX. Help me guys!

PS
What is better? AIGLX or XGL?

---

### Post by Faud on 2007-10-06
You shouldnt need it

---

### Post by Forlong on 2007-10-06
You don't need to install AIGLX as it's implemented by default in Ubuntu's X-Server since Edgy.

And with a Nvidia card you don't need neither Xgl nor AIGLX.

---

### Post by ASPCartman on 2007-10-06
How is it? No xgl or aiglx? How compiz will work ?

I had tried to install compiz fusion without aiglx or xgl and all windows had no up line menu ( close, max min) and i cant move em or jump between em. That means that emerald or usual one (how is it called) didnt started. So i didnt find any better way then reinstalling system. And waiting hours of downloading updates :(

So anyway u wanna say me that all that i need after installing gutsy is updating, turning on nvidia-xgl-new in restricted drivers and using CF script to install compis fusion? And thats all?

Then what the hell is this 3d acceleration (XGL and AIGLX)?! And why i cant use compizF/beryl using my x1800 gto2 without it but can using old 6150 nvidia?

---

### Post by Forlong on 2007-10-06
> **ASPCartman said:**
> How is it? No xgl or aiglx? How compiz will work ?
The Nvidia drivers have built-in support for that.
> **ASPCartman said:**
> I had tried to install compiz fusion without aiglx or xgl and all windows had no up line menu ( close, max min) and i cant move em or jump between em.
If you couldn't even move or switch between the windows, that means Compiz wasn't running at all.
> **ASPCartman said:**
> So anyway u wanna say me that all that i need after installing gutsy is updating, turning on nvidia-xgl-new in restricted drivers and using CF script to install compis fusion? And thats all?
Everything except for the CF script. Gutsy has Compiz Fusion installed by default.
> **ASPCartman said:**
> And why i cant use compizF/beryl using my x1800 gto2 without it but can using old 6150 nvidia?
ATI doesn't support Linux very well (this will hopefully change in a few weeks), that's why you need to install Xgl to compensate this.
If you want to know more about Xgl - see here: [http://www.freedesktop.org/wiki/Software/Xgl](http://www.freedesktop.org/wiki/Software/Xgl)

---

### Post by ASPCartman on 2007-10-06
Thx, 

I used CF script to install Compiz Fusion and when i use terminal to start it i got

```
aspcartman@ASP:~$ sudo fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 22, in <module>
  File "usr/lib/python2.5/site-packages/FusionIcon/util.py", line 23, in <module>
ImportError: libcompizconfig.so.0: cannot open shared object file: No such file or directory

```

What to do?

PS
I added line to xorg.conf to start AIGLX.
What is better? Using it or not?

---

### Post by Forlong on 2007-10-06
> **ASPCartman said:**
> What to do?
You'll have to ask this in the thread for the script. I recommend using the packages that come with Gutsy only.
> **ASPCartman said:**
> I added line to xorg.conf to start AIGLX.
What is better? Using it or not?
Although I don't think it will make any difference, I'd remove it.

---

### Post by ASPCartman on 2007-10-06
Hm when i set extra in appearence menu of gutsy - i got same story as last time.No upper menu of window and i cant move em or choose betweeen em :(

Use package that comes with gutsy? And where can i update em for example? When i type "Fusion" in synaptic (Standart repos) i got only plugins (main n extra) and some old things that has nothing with compiz fusion.

---

### Post by ASPCartman on 2007-10-06
Ok i installed compiz-gnome package and fusion-icon starded. All fine but... i got 1fps. 

Here is log:

```
aspcartman@ASP:~$ sudo fusion-icon
[sudo] password for aspcartman:
 * Detected Session: gnome
 * Searching for installed applications...
libccs: dlopen: /usr/local/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Backend     : ini
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
 * Using the GTK Interface
 * Decorator "" is invalid.
 * Setting decorator to GTK Window Decorator ("gtk-window-decorator --replace")
 * Starting Compiz
 ... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp
Backend     : ini
Integration : true
Profile     : default
Adding plugin fadedesktop (fadedesktop)
Adding plugin place (place)
Adding plugin regex (regex)
Adding plugin thumbnail (thumbnail)
Adding plugin extrawm (extrawm)
Adding plugin minimize (minimize)
Adding plugin ezoom (ezoom)
Adding plugin png (png)
Adding plugin video (video)
Adding plugin atlantis (atlantis)
Adding plugin switcher (switcher)
Adding plugin splash (splash)
Adding plugin snow (snow)
Adding plugin shift (shift)
Adding plugin firepaint (firepaint)
Adding plugin ring (ring)
Adding plugin resize (resize)
Adding plugin put (put)
Adding plugin mswitch (mswitch)
Adding plugin expo (expo)
Adding plugin cubereflex (cubereflex)
Adding plugin wall (wall)
Adding plugin blur (blur)
Adding plugin fs (fs)
Adding plugin zoom (zoom)
Adding plugin snap (snap)
Adding plugin crashhandler (crashhandler)
Adding plugin opacify (opacify)
Adding plugin scaleaddon (scaleaddon)
Adding plugin wobbly (wobbly)
Adding plugin widget (widget)
Adding plugin cubecaps (cubecaps)
Adding plugin cube (cube)
Adding plugin plane (plane)
Adding plugin winrules (winrules)
Adding plugin scalefilter (scalefilter)
Adding plugin addhelper (addhelper)
Adding plugin fakeargb (fakeargb)
Adding plugin water (water)
Adding plugin scale (scale)
Adding plugin inotify (inotify)
Adding plugin tile (tile)
Adding plugin bench (bench)
Adding plugin clone (clone)
Adding core settings (General Options)
Adding plugin group (group)
Adding plugin mblur (mblur)
Adding plugin imgjpeg (imgjpeg)
Adding plugin reflex (reflex)
Adding plugin fade (fade)
Adding plugin neg (neg)
Adding plugin rotate (rotate)
Adding plugin annotate (annotate)
Adding plugin screenshot (screenshot)
Adding plugin vpswitch (vpswitch)
Adding plugin decoration (decoration)
Adding plugin showdesktop (showdesktop)
Adding plugin glib (glib)
Adding plugin trailfocus (trailfocus)
Adding plugin workarounds (workarounds)
Adding plugin 3d (3d)
Adding plugin dbus (dbus)
Adding plugin animation (animation)
Adding plugin gears (gears)
Adding plugin colorfilter (colorfilter)
Adding plugin text (text)
Adding plugin svg (svg)
Adding plugin resizeinfo (resizeinfo)
Adding plugin move (move)
Initializing core options...done
compiz (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
compiz (dbus) - Error: InitObject failed
compiz (core) - Error: Couldn't activate plugin 'dbus'
Initializing place options...done
Initializing move options...done
Initializing resize options...done
Initializing decoration options...done
Initializing wobbly options...done
Initializing cube options...done
Initializing fade options...done
Initializing minimize options...done
Initializing rotate options...done
Initializing scale options...done
Initializing switcher options...done
Initializing workarounds options...done
Initializing zoom options...done
Setting Update "command"
```

---

### Post by Forlong on 2007-10-06
OK, first of all: _never_ run a regular application with sudo.

Then: if you want to use Compiz Fusion from the Gutsy repositories, you need to remove the files you installed with the script. Run the script again and see if there's an option for that.

---

### Post by ASPCartman on 2007-10-06
Ok question about installing is closed (i rebooted and all is fine (fine for this piece of **** - 6150) ~15-20 fps) 

But now new question:
How to make it run at start with admin privileges (sudo) without asking for password (cos if i just type in terminal  fusion icon then i got a pemission denied error) ?

And still question about AIGLX: 
What is AIGLX and should i use it (and why?)

---

### Post by Faud on 2007-10-06
> And still question about AIGLX: 
What is AIGLX and should i use it (and why?)

This question has allready been answered for you by Forlong.

> You don't need to install AIGLX as it's implemented by default in Ubuntu's X-Server since Edgy

> But now new question:
How to make it run at start with admin privileges (sudo) without asking for password (cos if i just type in terminal fusion icon then i got a pemission denied error) ?

You want to add it to your current session.  System->Preferences-> Sessions
Compiz should not need sudo to run

---

### Post by ASPCartman on 2007-10-06
hm. Some times (in most cases) when i run fusion-icon (no matter with or without sudo) i got verrrrry low fps. I have to restart x to solve it. 

And if i wont start fusion icon with sudo then i wont be able to change any settings in config ( it doesnt have permition to do it).

Im thinking about returning to my ati card (cos even using the simple cube makces me laging) but there i have a problem too.  Xserver doesnt start at all after installing fglrx (

So as far by now im busy making my ps3 work (im typing right now from ps3) so ill continiue this tomorow. Thx everyone. 

PS
Last question - can semone post a link to a simple guide where i can find the installing of new fglrx driver that support AIGLX? (alpha/beta one)

---

### Post by Forlong on 2007-10-06
> **ASPCartman said:**
> And if i wont start fusion icon with sudo then i wont be able to change any settings in config ( it doesnt have permition to do it).
That's because you run it already being root. Now you don't have permission for your own configs.
Here's how you set it right again:
```
sudo chown $USER:$USER $HOME -R
```
```
chmod -R u+rwX $HOME
```
> **ASPCartman said:**
> Last question - can semone post a link to a simple guide where i can find the installing of new fglrx driver that support AIGLX? (alpha/beta one)
It's not released yet.

---

