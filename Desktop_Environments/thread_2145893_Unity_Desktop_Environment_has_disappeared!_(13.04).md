---
title: "Unity Desktop Environment has disappeared! (13.04)"
date: 2013-05-16
forum: Desktop Environments
---

### Post by matt7195 on 2013-05-16
Greetings!

I've been messing around with different desktop environments recently, and I seem to have messed up.

I installed the latest Cinnamon when I upgraded to 13.04, because I have my parents running it, and I like to be able to sync up with them whenever they have problems.  But Cinnamon has had terrible problems since the upgrade.  It crashes on startup over 50% of the time, going into GNOME fallback mode. (Is this just me?)

So I decided to try out GNOME 3.8 the way that OMGUbuntu described it ([http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome](http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome)).  Unfortunately, things have turned bad. I'm guessing it might be due to the fact that I had Cinnamon installed.  I'm reading they might be incompatible ([https://mailman.archlinux.org/pipermail/arch-dev-public/2013-April/024792.html](https://mailman.archlinux.org/pipermail/arch-dev-public/2013-April/024792.html)).

Anyway, after installing 3.8, all Desktop Environments (Unity and GNOME) disappeared from the login option menu.  The only ones left were Cinnamon and Cinnamon (Sortware Rendering).  

Uninstalled 3.8, but still the same issue.  Re-installed Unity, no change.  Now the only time I can get into anything but Cinnamon is when it crashes.  GNOME Fallback is still there at least.

I'd really like to get Unity back.  It's not great having such and unstable UI be my only option.  I'm hoping this is just a listing issue, since GNOME is still there.  And Unity is still listed as installed in Synaptic.

If anybody has gone through anything similar or has any suggestions, they'd be much appreciated.

Thanks!

---

### Post by grahammechanical on 2013-05-17
Why did you uninstall Unity? We can have more than one desktop interface installed at the same time. We can switch between the alternatives at log in and Ubuntu will run the last used desktop interface. So, why?

Gnome 3.8 was not put into 13.04 for a reason. And it is still to be brought into the development version of 13.10. The latest is not always the greatest. It is often the least tested.

You may be in a situation where a fresh install is the easiest and simplest method of fixing this. I have several installs of Ubuntu. I experiment with them and when things break, I just re-install and start again. I have a broken 13.04 install that I was trying to get Unity 8 working on it and MIR and the phone core apps. I am not going to mess around trying to fix what is wrong. I will just re-install and start again with my experiment.

Regards.

---

### Post by Frogs Hair on 2013-05-17
My two attempts with Gnome 3.8 were less than spectacular. With the first I was able to remove all the packages and keep  the installation working. The second time on the 13.04 final release even with the ppa purge many packages were not down graded to 3.6. While the OS worked it was compromised and it was not worth fixing manually. The best solution was to reinstall and stick with 3.6 for daily use. From what I have seen on the forums not with just Gnome 3.8 I will steer clear of the Gnome ppa's. kudos to those that have 3.8 running well.

---

### Post by matt7195 on 2013-05-17
Thanks for your input, Frogs Hair.  I'm also wondering if I might get to the point that a full reinstall makes the most sense, but I thought I'd throw this out to the forum first, just in case there's a simple solution I'm missing.

@Grahammechanical: I'm sorry I might not have been clear enough:

I never uninstalled Unity.  The main story of my problem is that Unity disappeared from my Desktop Environment choices on the login page.  This was immediately after I installed GNOME 3.8.  So I'm guessing it has to do with that.

What I meant with "re-installing Unity" was that I went into Synaptic, saw that Unity was still installed, and hit "Mark for Reinstallation" anyway, on the off chance that might fix everything.

Now I'm thinking maybe if I uninstall Cinnamon, the other options might show back up... Or there might be no Desktop Environment choices and I'm completely locked out... 

So thanks again for any recommendations!

By the way, I'm running an Asus S500C.

---

### Post by Frogs Hair on 2013-05-17
If you have terminal access in Unity Ctrl + Alt +T try the following . [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

Check you version of the file manager under Files > About and if it is not 3.6.3 you have 3.8 packages installed on your system.

---

### Post by matt7195 on 2013-05-17
Thanks for the reset suggestion, Frogs Hair, but my problem is that I can't even reach Unity.  I'm trapped in a broken Cinnamon that crashes into GNOME Fallback half the time I boot.  Logging out and trying to switch to a different Desktop Environment only brings up the Cinnamon options.  Am I missing an alternative way to get back to Unity?

---

### Post by matt7195 on 2013-05-17
Well, just a quick update that I figured it out:

I checked out how somebody with Kubuntu or Lubuntu would install Unity and tried that.  In case anybody has a similar issue one day, this worked perfectly in the terminal:

sudo apt-get install ubuntu-desktop

Thanks for everybody's suggestions in the meantime!

---

