---
title: "how to work with compiz"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by Willye on 2007-11-22
i have installed compiz i did it:
apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
apt-get install compizconfig-settings-manager
but i don't know how to configure it, and how to put special effects in my desktop when i opened windows or close .... etc

---

### Post by subs on 2007-11-22
first type this out in the terminal
> sudo aptitude install compizconfig-settings-manager

now goto System > Preferences > Advanced Desktop Effects Settings

here you can setup whichever effect u want to

---

### Post by spiderbatdad on 2007-11-22
It has a bit of a learning curve to be sure. There are alt+f2 or command line options for changing the windows manager and theme manager. BTW did you install emerald from synaptic? You need that. Anyway, I found a compiz-fusion icon through google, and installed it. It let me put an icon on the taskbar to enable a GUI for switching windows manager from metacity to compiz, and changing the theme to emerald. BTW the icon was invisible (haha) but i could tell it was there as it created a blank space on the taskbar.  Right clicking opened the options.

---

### Post by Willye on 2007-11-22
ok, i can see in preferences->advanced desktop effects settings
but, i have tried to change several parametres, but when i close or open a new window or change my workplace doesn't appear neither effects, what i must to do

---

### Post by Willye on 2007-11-22
i want to know how to rotate my desktops and how to use these special effects

---

### Post by overdrank on 2007-11-22
> **Willye said:**
> i want to know how to rotate my desktops and how to use these special effects

Hi have you enabled compiz? Try alt, F2 then enter ```
compiz --replace
```

---

### Post by Willye on 2007-11-22
ok i ran compiz --replace, and now ?

---

### Post by spiderbatdad on 2007-11-22
in the settings manager make sure you have selected "cube" and "rotate cube" I dont think they are on by default. If you are still not rendering i just tried a good how to here:[http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+fresh+install+gutsy](http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+fresh+install+gutsy)

post #7. It worked for me after a resart, but i do have an ati graphics card. It slows my desktop response down and I dont much care for it. Beryl was so much better. Also I would be wary of this posters recommendations for removing software further down in the posts. I read never to rm -rf anything.

---

### Post by Willye on 2007-11-22
i don't have grpahics card, is compulsory to have anyone?

---

### Post by borgir on 2007-11-22
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)
here is a good help

---

### Post by overdrank on 2007-11-22
> **Willye said:**
> i don't have grpahics card, is compulsory to have anyone?

HI you do have graphics it just maybe onboard. Please post the output of this command in the terminal ```
lspci
```

---

### Post by spiderbatdad on 2007-11-22
you definitely have a graphics card. Usually cube rotation is initiated by the middle mouse button or left&right mouse simultaneously, but you have to select cube and rotate cube as options in the compiz settings manager

---

### Post by Willye on 2007-11-22
i have a little problem, 'cause now i can't check any box, it's how be disable, why ?

---

### Post by Willye on 2007-11-22
i can't check any box, i don't know what happend, it's how be disabled, why ?

---

### Post by overdrank on 2007-11-22
> **Willye said:**
> i can't check any box, i don't know what happend, it's how be disabled, why ?

Try and go to system, preference, appearance. Then visual effects and see if it is applied.

---

### Post by JBAlaska on 2007-11-22
You might have some unresolved problems with compiz, open a terminal and type ```
compiz --replace
``` that will allow you to see any error messages.

and post the output of ```
lspic
``` as overdrank mentioned.

---

### Post by subs on 2007-11-23
> **Willye said:**
> i don't have grpahics card, is compulsory to have anyone?

ya to run compiz you will need to have a supported graphics card....

---

