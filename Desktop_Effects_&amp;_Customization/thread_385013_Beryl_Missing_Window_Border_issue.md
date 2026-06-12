---
title: "Beryl Missing Window Border issue"
date: 2007-03-15
forum: Desktop Effects &amp; Customization
---

### Post by dheerajsp on 2007-03-15
hey there...

im running Kubuntu 6.10 on an Nvidia GeForce FX 5200 GPU. i previously used Beryl on Ubuntu and it worked just fine other than the usual crashing..

i installed beryl on Kubuntu today, after installing the NVIDIA drivers downloaded from the Nvidia site. when i load beryl-manager, the borders are missing. i had the same issue on Ubuntu, but changing 'nv' to 'nvidia' in xorg.conf solved the problem then. this time, it didnt work.

so anyone knows of the solution? should i post my xorg.conf contents too?

---

### Post by louis_nichols on 2007-03-15
Is beryl working otherwise? I mean, do you get other effects, other than window borders? Like transparencies, desktop cube and the like. Otherwise, it might be that not only window borders are missing, but that beryl doesn't work at all. In this case, it might be a matter of video driver. You should check that the driver in xorg.conf is indeed set to nvidia.

If you get all the effects but the window border, this can mean several things. Firstly, the window border for kde should be [aquamarine]("http://wiki.beryl-project.org/wiki/Aquamarine") and not emerald. Secondly, thre might be other issues. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=367850") for possible issues and solutions.

---

### Post by dheerajsp on 2007-03-15
yes i AM gettin all the other effects....like cube, rain drop.... i noticed that the "nvidia" is apeparing in 2 consecutive sections, so i made sure both are "nvidia" and not nv.

---

### Post by dheerajsp on 2007-03-15
btw, i also noticed that the 'Reload Window Decorator' and 'Select Window Decorator' options are greyed out in the  beryl right-click menu.

---

### Post by FruitieX on 2007-03-15
Have you got emerald installed? (The window decorator in beryl) I guess you do have it installed... Add the ubuntu-beryl repos and try aptitude search emerald and see what you can install with the name emerald.

---

### Post by louis_nichols on 2007-03-15
> **FruitieX said:**
> Have you got emerald installed? (The window decorator in beryl) I guess you do have it installed... Add the ubuntu-beryl repos and try aptitude search emerald and see what you can install with the name emerald.

AFAIK, emerald doesn't work at all with kde. What he needs to install is aquamarine, as I said.

---

### Post by dheerajsp on 2007-03-15
> **louis_nichols said:**
> AFAIK, emerald doesn't work at all with kde. What he needs to install is aquamarine, as I said.
how do i install aquamarine?

EDIT: i found 3 packages when i searched for Aquamarine in Adept Manager. so im installing those...lets see.

---

### Post by dheerajsp on 2007-03-15
ok...problem solved. i did this:'sudo nvidia-xconfig --add-argb-glx-visuals' and restarted X server and everything works now.

thanx for the help guys...but is there an Aquamarine theme manager?

---

### Post by FruitieX on 2007-03-15
@louis_nihols: Sorry, I didn't first notice that he's using Kubuntu. (Didn't read the thread too well... Srry won't do that in the future, you always learn something from your mistakes :P)

@dheerajsp: Aquamarine should be installed just like I explained howto install emerald, so just what you are doing now. If nothing else, try Xfce4 with emerald :P just like I do on my pc, it's faster and less of a resource hog than KDE or Gnome. (Aptitude install xfce4). (Or why not then, try gnome: aptitude install gnome...) Hope you'll get it to work! I also think that beryl works a lot faster for me when I use Xfce4 instead of gnome (I would use KDE but it depends on Juk that depends on some other app that has a too new version in the Ubuntu Feisty Fawn repos, that is how I (luckily!) ended up with Xfce4 that I nowdays after some tweaking think is great!)...

FruitieX.

---

### Post by FruitieX on 2007-03-15
Darn! You were too fast... :D :D

Edit: Instead of tripleposting:

Don't know about the Aquamarine Theme manager but I know for sure that there is the Emerald Theme manager ;). But if you want to use KDE, you'll have to find an other solution.

FruitieX.

---

### Post by dheerajsp on 2007-03-15
hehe....works fine now...hope other who have the same problem get it resolved!!!

---

### Post by dheerajsp on 2007-03-15
> **FruitieX said:**
> Darn! You were too fast... :D :D

Edit: Instead of tripleposting:

Don't know about the Aquamarine Theme manager but I know for sure that there is the Emerald Theme manager ;). But if you want to use KDE, you'll have to find an other solution.

FruitieX.
Emerald theme's are applying properly now.  before they wudnt apply....well i cudnt see it cos the borders werent even loading. but now they're OK. so ill stick with Emerald now.

---

### Post by louis_nichols on 2007-03-15
I haven't used aquamarine, but from what I read, I understand that the themes correspond to the ones kwin uses. So you just go to KDE Control center to change window borders and aquamarine automatically uses those. In theory, at least... :)

---

### Post by dheerajsp on 2007-03-15
> **louis_nichols said:**
> I haven't used aquamarine, but from what I read, I understand that the themes correspond to the ones kwin uses. So you just go to KDE Control center to change window borders and aquamarine automatically uses those. In theory, at least... :)
um yeah, that's what i thought too. but emerald's working fine now...

---

### Post by SonicSteve on 2007-03-15
I had the exact same issue with beryl\emerald. I have found it too quirky to use. I would love to get it working but... I don't know where to start with it. 
For me I could get it loaded and it will work well for a bit, 5mins to 1hr. Then the boarders will disappear like yours did. I haven't been able to forceably kill beryl/emerald either. So I end up rebooting. 

I have an Nvidia Gforce 5200 with the Nvidia drivers loaded. Other 3d games work well so I assume that it's loaded right. I'm using Ubuntu and Gnome

I'll be interested to see if you experience the same thing I did.

---

### Post by medley on 2007-03-15
> **louis_nichols said:**
> AFAIK, emerald doesn't work at all with kde. What he needs to install is aquamarine, as I said.

No, this is incorrect. Emerald does, in fact, work with KDE. I know from first hand experience. I am using that combination on a system today. I don't have Aquamarine installed on that system.

---

### Post by myusrnm on 2007-03-16
> 
If you find that you have no borders after you have set up Beryl with AIGLX using the latest nvidia driver you should append the following to your /etc/X11/xorg.conf in the “Device” section:
[quote]
Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"

For some reason many guides do not mention this problem.
[/quote] 

via [http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/](http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/)

try that if the first thing does not work!

---

### Post by dheerajsp on 2007-03-16
ok, how do i add beryl-manager to my Kubuntu startup?

---

### Post by SonicSteve on 2007-03-16
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "Tru

> **myusrnm said:**
> via [http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/](http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/)

try that if the first thing does not work!

Thanks, I'll give it a try, infact I'm trying it right now. I already the option "triple buffer" but not the others. I also noticed a beryl and emerald update came in on the backports. between the updates and the xorg.conf config lets see.

One thing I noticed in the terminal is this though;
Take note of the bold underlined "GLX_EXT_texture_from_pixmap".
I don't know if this is normal or not but it failed.

steve@UbuntuServer:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
**_Checking for GLX_EXT_texture_from_pixmap        : failed_**

No GLX_EXT_texture_from_pixmap
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options


I should also say that I take a noticable performance hit while beryl is running. Things end up a bit choppy. I really like beryl though, can't wait for stablility.

---

### Post by joyolee on 2007-03-17
hi, i have the same problem as yours`~

and i  did  what you said "sudo nvidia-xconfig --add-argb-glx-visuals"and then restarted X server 

but it still doesn't work~

btw, i use gnome~

---

### Post by pwrinxs on 2007-03-17
I had the same problem until I followed these steps from another thread. Try this:

In terminal:

sudo gedit /etc/X11/xorg.conf

Scroll down to "Screen" section, and insert the following line:

Option "AddARGBGLXVisuals"

Save, close, and restart your X session.

This worked for me!

---

### Post by Yellowbelly on 2007-03-20
I had this problem and his original line fixed it for me. I just installed beryl, started the manager and I couldn't move the windows because the border wasn't there. Switch to metacity, put that code in, restart computer (or I guess X) and voila. Maybe I didn't install it right but it's working perfectly now.

---

### Post by Cygnus on 2007-06-09
> **joyolee said:**
> hi, i have the same problem as yours`~

and i  did  what you said "sudo nvidia-xconfig --add-argb-glx-visuals"and then restarted X server 

but it still doesn't work~

btw, i use gnome~

It worked for me on kubuntu.

---

### Post by royg on 2007-07-15
Hello there forum users/non-users,

I'd like to add to all the comments of the others, that is, this gave me an headache for about 2 days and I have been pulling my hair for few hous without the window borders and adding RGBGLX visuals and so many other xorg.conf tweaks didn't get it up and running, While it works for most in some cases this is what I had to do.
here's what finally did the trick.

1. FIRST Add RGBGLX visuals and Allow GLX with composit ..etc as the default as described by the others in this forum reply (if it get it working your done..if not keep reading) 
(The following was originally suggested by TAMAS SULYOK on "[NO Window borders with NVIDIA and AIGLX]("http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/#comment-3397")" last access jul 15 2007 so all hail the maestro :) )
2. Start beryl settings manager
3. select window management
4. select "set attributes by various criteria"
5. in window borders  tab add all the possible borders (don't use grab)
6. from the top of the options (in beryl settings) "general options, window management, desktop, visual effects, accessibility..etc" select Visual effects
7, now check window decorations
8. go back to "general options" (in beryl settings) select the advance tab
9. if you are using Wine or Crossover select the "enable workaround for certain wne and legacy windows"

this should get this your borders working in extreme cases of beryl window border issue.

If it still doesn't work, then I feel your frustration @_@ I am so sorry, for card info

I am running nvidia Gforce 7300 with version 100.14.11 (nvidia legacy driver) I had the same problem with the native driver and the restricted drivers.

Also please note, before you install NVIDIA legacy driver supplied by NVIDIA please make sure you uninstall your restricted NVIDIA driver otherwise your gdm may fail to start with an API mismatch error. Please read the other forums on how to uninstall restricted driver from command line (that is if you already stuck there) otherwise simply use synaptics manager and uninstall the restricted drivers.

Hope this help at least some...my 2 cents worth ;) now beryl is snowing and raining on my desktop ;)

---

