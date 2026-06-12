---
title: "Questions and problems with kubuntu"
date: 2005-04-27
forum: Desktop Environments
---

### Post by Heretic09 on 2005-04-27
Are the sources located here:

[http://www.ubuntulinux.org/wiki/AptGetOrg](http://www.ubuntulinux.org/wiki/AptGetOrg)

usable in kubuntu?

Also kde seems to crash a whole lot more on kubuntu then my previous distro (suse 9.1)

I used apt-get with suse and it was very dependable but with kubuntu I keep getting missing repositories when trying to install apps like mplayer or when trying to update kdelibs-data I get error in transaction. Is there a smart upgrade function that can be enabled when using synaptic?

Oh and one more thing, when kdesu is used in starting programs sometimes my root password won't work (gives me incorrect password) but when I put in my standard user password it works. If I log off and on root password will work again. 

So far almost every review rates kubuntu as stable, fast and almost crash proof so far that hasn't been the case for me. Are there things i'm doing wrong? Or any solutions to rectify the problems listed above?

---

### Post by XDevHald on 2005-04-27
For the first question, that would be a no probably. If it's Ubuntu, then it's probably not Kubuntu filing for your Distro.

Also, it's hoary ;) so that does say a lot.

Second question, it should prompt you automatically when you first start using Synaptic, I'm not real sure how to actually get this set up by hand, but I am sure some of the guys/gals here do. :)

Third Question, you'll need to set a root password, there is a password, but it's set up by default from the system on installation, you'll need to Goto **Users** **and Groups **in your **Systems **panel in your KDE Start Menu button. Then open it, then select root, erase the default password and set a new one :)

And the last question, just keep your system up to date and you'll be ok ;)

---

### Post by jodef on 2005-04-27
First of all welcome to the forums.
Second if you are new to kubuntu don't try to do too many things at the same time.
Check out the [UbuntuGuide](http://ubuntuguide.org) although written primarily for ubuntu a lot of the info pertains just as well to kubuntu.

The sources are the same for both distros.One is kde based the other gnome based.

KDE crashes a lot is pretty general could you be more specific is it a particular application, what are you doing when it crashes? The more info you give the better KDE 3.4 is new and there are still bugs being worked out.

Kubuntu uses kynaptic not synaptic it's a little less intuitive so set up the sources as indicated in the ubuntuguide and you could install synaptic which has the smart upgrade option that you are familiar with.

Ubuntu and by extension Kubuntu use sudo as opposed to a root user.The user you created during installation will be the sudo user.

---

### Post by Heretic09 on 2005-04-27
Tried changing the root password. Then logged back in as a regular user and tried using synaptic, when the prompt for the password came up I entered the new one but again it said it was incorrect. tried my regular user password and it worked fine. Kinda odd and not really secure.

---

### Post by jodef on 2005-04-27
> Kinda odd and not really secure. 
You may not be familiar with the sudo method of doing things but it is just different no more no less you can learn why this model was chosen [here](http://www.ubuntulinux.org/wiki/RootSudo).

In the final analysis use what feels good to you.

---

### Post by Heretic09 on 2005-04-27
[QUOTE=jodef]You may not be familiar with the sudo method of doing things but it is just different no more no less you can learn why this model was chosen [here](http://www.ubuntulinux.org/wiki/RootSudo).

In the final analysis use what feels good to you.[/QUOTE]

What i meant was using kdesu and ubuntu accepting my standard user password and not the root.

For activating translucency and shadows I entered the mandatory options in the xorg.conf:

Option          "backingstore"          "true"
Option          "RenderAccel"           "true"

Section "Extensions"
        Option "Composite" "Enable"
        Option "RENDER" "true"
        Option "DAMAGE" "true"
EndSection

But when enable it in control center it says its active but I don't see the shadows or the traparancy, tried messing with the sliders but no changes.

---

