---
title: "Installed Gnome 3.8 Desktop Environment, Unity wallpapers no longer working!?!?"
date: 2013-04-22
forum: Desktop Environments
---

### Post by MattBergholm on 2013-04-22
I installed Gnome 3.8 from the following instructions:
[http://www.ubuntukiller.com/2013/03/...ome-38-in.html](http://www.ubuntukiller.com/2013/03/...ome-38-in.html)

I used it for a bit and didn't love Gnome so I logged back into Unity. Now when I enable "Show Desktop Icons" I get a white screen with no background image. When I disable it I get a back screen with no background image.

I have uninstalled and reinstalled LightDM. Deleted the config files and forced it to recreate them.
I uninstalled (purge and reinstall) the nVidia-313-updates
I have booted into XFCE and Unity and both have the same issue

I just want my Unity back!!! What the heck do I do now?


Thanks,
Matt

---

### Post by MattBergholm on 2013-04-22
Sorry, meant to mention I am running 13.04. From what I have seen though, 12.10 is affected by the same issue as well.

---

### Post by Frogs Hair on 2013-04-22
Check the Ubuntu +1 sub forum , I have seen posts on  similar problems . I think you need the 3.8 tweak tool and extensions as well if it/they did not upgrade. I removed the 3.8 PPA and re-installed 3.6 with help of the PPA Purge and synaptic but it took a couple of  hours . It is noted in most instructions I have seen that this is a use at your own risk installation procedure. I would try to make it work rather than removing three PPAs because it was no fun. When there is a single PPA I may try again.

---

### Post by Branimir on 2013-04-22
I have installed,also, gnome 3.7-8 from staging PPA in Ubuntu 12.10 and always got problems. Empathy dos not work, too.
Didn't notice wallpaper problem, though, as without working messenger I immediately purged PPA.

---

### Post by EgoGratis on 2013-04-22
Yes i think this is known bug.

> I have uninstalled and reinstalled LightDM. Deleted the config files and forced it to recreate them.
I uninstalled (purge and reinstall) the nVidia-313-updates
I have booted into XFCE and Unity and both have the same issue

I just want my Unity back!!! What the heck do I do now?

Probably you will have to remove GNOME 3.8 PPA for now with the help of ppa-purge command for all the PPAs you added and then i think you will have working background in Unity again.

sudo ppa-purge ppa:gnome3-team/gnome3
sudo ppa-purge ppa:ricotz/testing
sudo ppa-purge ppa:ricotz/staging

---

### Post by MattBergholm on 2013-04-22
Thanks guys,
I was able to purge and remove them all. I had to re-enable the repository, purge, then reboot. I have a desktop background now but I have some other weird things going on all of a sudden.

Unity panel color isn't auto-adjusting to the desktop image, i can't disable the Unity panel on my second monitor, I have sticky edges stuck on.

I shouldn't have messed with it! It was so stable... haha I am slowly working through it. Thanks for the advice guys.

---

### Post by EgoGratis on 2013-04-22
> I shouldn't have messed with it! It was so stable...

Where would be the fun in that!

---

### Post by yustradhistira on 2013-04-25
the problem with me , in ubuntu 13.04.
so , i use gnome until now.i can back to unity.
how to reinstall unity ?

---

### Post by gnugen on 2013-04-25
To reinstall Unity, I think this command should work but first you have to uninstall the original Unity desktop environment
```

sudo apt-get install ubuntu-desktop
```

I do not know how to uninstall the unity desktop environment properly, so you might want to check somewhere else.

This is in reply to yustradhistira.

---

### Post by rrich1974 on 2013-04-25
messing up with DE is not quite a good idea.

---

### Post by aratina_race on 2013-04-26
I had the same problem, i.e. white backround after installing Gnome 3.8.
I fixed it by opening up the Gnome Tweak Tool and under the desktop heading, switch "Have file manager handle the desktop" to off

---

