---
title: "Problems with multiple desktops installed"
date: 2011-12-08
forum: Desktop Environments
---

### Post by abrand9 on 2011-12-08
I am pretty new to linux and ubuntu but have really enjoyed it so far. I started out with a vanilla ubuntu install with the unity desktop (currently on 11.10). I actually liked it quite a bit but wanted to try out some other desktops to see the options they offered. So I installed the kde plasma desktop (kububtu) and the gnome 3 shell through the software center. They all seem to work well. Problem is when i return to the unity desktop a lot of the settings have changed or shortcuts no longer work. I did not make any settings changes in the other desktop environments. Basically my compiz settings were no longer working, so i uninstalled it. I still have issues with fonts, application switcher, workspace (only lets me have one) and keyboard shortcuts. 

So my questions are: 
Is there a problem with installing multiple desktops? Is this even a good idea to have multiple installed?

Is there a way to reset unity to its defaults without having to uninstall the other desktops? 

Thanks

---

### Post by Jay Car on 2011-12-08
Hi! Welcome to Ubuntu Forums!

You can try [this]("http://www.liberiangeek.net/2011/10/reset-ubuntu-unity-desktop-after-messing-it-up/"):
open terminal by pressing the keys below:
```
Ctrl - Alt - T
```

When terminal opens, run the command below to reset Unity:
```
unity --reset

```

To go further, run the command below:
```
unity --reset-icons
```

I don't think it's necessarily a problem installing more than one desktop, but sometimes - when you are first learning your way around - it's good to keep things simple. 

On the other hand, trying lots of new stuff can be a fun learning adventure (depending on one's definition of fun)  :)

JCC

---

### Post by abrand9 on 2011-12-08
Thanks Jay for the response, i tried the reset and I guess unity got uninstalled somehow. So apt-get unity and bam I am back in action. Everything is back to normal, whew what a relief.

Now only one minor thing left, when I boot my computer i get the kubuntu splash screen instead of standard ubuntu splash screen, any ideas how to get that back?

Thanks

---

### Post by stinkeye on 2011-12-09
> **abrand9 said:**
> 

Now only one minor thing left, when I boot my computer i get the kubuntu splash screen instead of standard ubuntu splash screen, any ideas how to get that back?

Thanks
```
sudo update-alternatives --config default.plymouth
```


Choose...
```
/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
```


Then run...
```
sudo update-initramfs -u
```

---

### Post by amhainen on 2011-12-09
Would installing XFCE, Gnome-classic, and possibly even LXDE on top of Unity, KDE, and Gnome3 add anymore complexity? I'm kind of excited for 12.04, so long as I never have to use Unity which is why I'd like to have many alternatives at disposal.

Abrand9, did you have any problems with different login managers from various sessions? I've heard reports of multiple loading bars in some instances. Any other issues you've noticed when switching sessions?

---

### Post by stinkeye on 2011-12-09
> **amhainen said:**
> Would installing XFCE, Gnome-classic, and possibly even LXDE on top of Unity, KDE, and Gnome3 add anymore complexity? I'm kind of excited for 12.04, so long as I never have to use Unity which is why I'd like to have many alternatives at disposal.

Abrand9, did you have any problems with different login managers from various sessions? I've heard reports of multiple loading bars in some instances. Any other issues you've noticed when switching sessions?
Haven't noticed any issues except Unity's AppMenu showing in gnome shell sometimes,
which can be easily fixed
Have gnome-shell Unity and xfce installed.
Can switch between gnome-shell and Unity using **gnome-shell --replace**
or **compiz --replace**

> **abrand9 said:**
> Is there a way to reset unity to its defaults without having to uninstall the other desktops?
This command will reset unity to defaults.
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

Give it time to run and if it doesn't reload properly run...
```
compiz --replace
```

---

### Post by abrand9 on 2011-12-09
> **amhainen said:**
> Abrand9, did you have any problems with different login managers from various sessions? I've heard reports of multiple loading bars in some instances. Any other issues you've noticed when switching sessions?

I have not had any problems yet, but I have only had all the DE's installed for a couple days and have not done much tweaking yet. Switching between DE's has been easy and painless, just log off and log back in. There may be an another method as stinkeye was getting at previously. Ubuntu's standard login manager just took control so i really didn't see much change except for all the different login options of course. Just a note, when i installed the gnome shell, gnome classic was included with the gnome 3 package for me. 


Thanks stinkeye for all your help.

---

