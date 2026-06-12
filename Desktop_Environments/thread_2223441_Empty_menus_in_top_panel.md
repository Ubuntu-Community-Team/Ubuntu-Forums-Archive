---
title: "Empty menus in top panel"
date: 2014-05-11
forum: Desktop Environments
---

### Post by t_ras on 2014-05-11
Lenovo G500/ Ubuntu 14.04

After installing some UI tweek application:
Theme Configuration
Tweak Tool
Unity Tweak Tool
Ubuntu Tweek

It seems that one the applications (or their combination) caused the menus in the top panel launcher to be empty. I'm not sure this is the problem though.
Now all the application menus are empty. The main menu only offers my user+guest, no shutdown/suspend....
Some menus (like wireless) are full, but these are the exceptions.

Any Idea how to solve it?

---

### Post by grumblebum2 on 2014-05-11
Is this still the case after a reboot?

---

### Post by t_ras on 2014-05-11
Unfortunately yes.

---

### Post by grumblebum2 on 2014-05-11
Bit confused what you mean by "top panel launcher".
Screenshot?
You using unity?

---

### Post by t_ras on 2014-05-11
Im using Unity
Here is an example:
I open the file manager, go to the file/edit/whatever menu in the top panel - the menu is empty. If there are supposed to be there 4 divisions of option, I got the divisions, but nothing to click on, it is all empty. 
I would have added a screen shot, but it doesn't capture the opened menu.

---

### Post by Elfy on 2014-05-11
similar to this

[https://launchpadlibrarian.net/130772914/bug.png](https://launchpadlibrarian.net/130772914/bug.png)

---

### Post by grumblebum2 on 2014-05-11
Right click on the desktop > Change Desktop Background
Goto the behaviour tab and hit the **restore behaviour**  button.
Could also try setting show menu's in the windows titlebar and see what happens.

---

### Post by t_ras on 2014-05-11
The problem is exactly as Elfy pointed. I tried the restore behavior and background but it didnt help. The menus are empty even when shown in title bar.

---

### Post by grumblebum2 on 2014-05-11
I'll wait see if  Elfy knows of bug and/or solution.

---

### Post by Elfy on 2014-05-11
Elfy doesn't use ubuntu/unity. All he did was look for a bug - found an old one with a screenshot to illustrate the issue for the OP.

---

### Post by grumblebum2 on 2014-05-11
grumblebum2 acknowledges Elfy's response. ;)

---

### Post by deadflowr on 2014-05-11
> **t_ras said:**
> 
I would have added a screen shot, but it doesn't capture the opened menu.

Open a terminal and run
```
gnome-screenshot -d 5
```

then quickly click on a menu before the 5 seconds is up.
It'll capture a screenie with menus.

Beside that, have you tried changing themes?
Or, what exactly does theme configuration mean?

---

### Post by grumblebum2 on 2014-05-11
I would use unity tweak tool and restore the gtk theme back to default and anything else you may have changed.
Also if you used **gtk-theme-config**, open it up and hit the revert button.

I would also set compiz/unity back to defaults with the terminal command...
```
dconf reset -f /org/compiz/
```
...then logout back in.

---

### Post by t_ras on 2014-05-11
Compiz reset and resetting everything in unity tweak did not help.
Any other ides?  
I fear I will have to reinstall :(

---

### Post by grumblebum2 on 2014-05-11
No other ideas except maybe try re-installing indicator-appmenu.
```
sudo apt-get install --reinstall indicator-appmenu
```

---

### Post by t_ras on 2014-05-11
Not helping :(

Thanks though...

---

### Post by grumblebum2 on 2014-05-11
If you create a new user account and login to that account, does it happen there.

---

### Post by t_ras on 2014-05-11
Also with a new user.

---

### Post by grumblebum2 on 2014-05-11
Beyond me then.
I have installed and use unity-tweak-tool, gnome-tweak-tool, ubuntu-tweak and gtk-theme-config without problem.

---

### Post by t_ras on 2014-05-11
Thanks! The weirder part is that it doesn't happen to ALL applications.

---

### Post by grumblebum2 on 2014-05-11
Sounds like some package needed for gtk2 or gtk3.
ie there are packages **unity-gtk2-module** and **unity-gtk3-module**.
Just wild guesses here.

Have a poke around in synaptic looking at your installation history under the File menu.

Have you added 3rd party ppas?

---

### Post by t_ras on 2014-05-11
I  added 3rd party ppas. What is the efect?

---

### Post by grumblebum2 on 2014-05-11
> **t_ras said:**
> I  added 3rd party ppas. What is the efect?
Depends on the ppa.
Some ppas can contain additional packages that can upgrade your ubuntu version of a package and cause problems.

eg I just installed **gis-weather** from the noobslab/apps ppa.
The ppa includes upgrades (denoted by yellow star in synaptic) to **libaudclient2** among others  which will be included upon next update and upgrade.
This can cause problems with the default ubuntu repo packages using a different version.
So after installing gis-weather I disable the noobslab/apps ppa.

I always check in synaptic when adding ppas to see what other packages are in a ppa.

---

### Post by t_ras on 2014-05-11
I dont seem to have libaudclient2 installed ( though I remember I got errors about it being missing when I tried to installed from PPA). 
I removed the PPA repositories and have nothing marked with a yellow star, though maybe I already installed some unwanted thing from PPA through upgrades.
How can I knwo if theres eneything I need to downgrade?

---

### Post by grumblebum2 on 2014-05-11
> **t_ras said:**
> I dont seem to have libaudclient2 installed ( though I remember I got errors about it being missing when I tried to installed from PPA). 
I removed the PPA repositories and have nothing marked with a yellow star, though maybe I already installed some unwanted thing from PPA through upgrades.
How can I knwo if theres eneything I need to downgrade?
libaudclient2 was just an example.

Have a look in synaptic. Click on origin then the added ppa. Only  currently enabled ppas show.
If you disabled a ppa, in synaptic, goto **menu > settings > repositories > other software**
and re-enable.
Close the "software and updates" window and hit the reload button in synaptic.

This may not even be your problem...just a suggestion.

---

### Post by deadflowr on 2014-05-11
> **t_ras said:**
> Thanks! The weirder part is that it doesn't happen to ALL applications.

That might be helpful.
Can you list some that it doesn't happen to?

Maybe we can see a pattern, or something.

---

### Post by t_ras on 2014-05-12
It happens to file manager and system menus, but chrom menus are fine.

---

### Post by t_ras on 2014-05-12
It seems I have many packages from the PPA repositories, most of them seem to be related to gnome (though also Unity tweak is from PPA).

---

### Post by t_ras on 2014-05-12
Might reinstalling unity help?

---

### Post by grumblebum2 on 2014-05-12
If it was me I would backup and do a fresh install and put it down to a learning experience and
take more care and diligence when using 3rd party ppas.

---

### Post by t_ras on 2014-05-12
Yep, it seems I had to learn my lesson regarding PPAs...

---

### Post by grumblebum2 on 2014-05-12
Yeah... I mean for the sake of a headache you can be up and running again within half an hour.

---

