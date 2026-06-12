---
title: "Want to install KDE 4.5 on Ubuntu"
date: 2010-09-04
forum: Desktop Environments
---

### Post by dkc.com on 2010-09-04
Hi Friends,

I am an ex-windows Vista victim who have been happily using Ubuntu 10.04 LTS since its release. Completely happy with the switch with minor hic-ups here and there. Although haven't completely uninstalled Vista and boot in there once a week basis to do some mobile syncing.

At that time I feel that the Gnome desktop, however sturdy it is, misses the eye candies of Vista so want to try KDE 4.5. I have a real bad experience with KDE's one of the 4.X releases with its bugs so I want to take precautions at this time.

Is the following way good enough to install KDE desktop:

sudo apt-get install kubuntu-desktop

Is it possible me to switch between the desktops at the login time so that I can use both of them alternatively?

Thanks in advance.

---

### Post by 3Miro on 2010-09-04
You can install kubuntu-desktop and in the case of Ubuntu 10.04 it will come with KDE 4.4. Then upon boot you can select between KDE and Gnome.

---

### Post by Nythain on 2010-09-04
First, make sure you add the kubuntu backports ppa, easiest way to do that is to open a terminal and type
```

sudo add-apt-repository ppa:kubuntu-ppa/backports

```after that, a simple
```

sudo apt-get update && sudo apt-get install kubuntu-desktop

```should do the trick of getting you a Kubuntu 4.5.x desktop install

And yes, its possible to switch between the two of them... when installing the kubuntu desktop it will ask if you want to keep using GDM or switch to KDM, either one you pick should have entries for both the Gnome and KDE desktop logins

if anyone knows a better more reliable or easier way, feel free to chime in

---

### Post by wkhasintha on 2010-09-04
Open Synaptic Package Manager(System->Administration) and search for &#8220;kde desktop&#8221;.Now you should decide whether you want to use kde as a primary desktop or secondary or just for changing taste.In first case you can choose full kde fr0m Synaptic Package Manager but in the second case minimal kde or base kde is fine.

---

### Post by d3v1150m471c on 2010-09-05
no doubt kde has excellent "eye-candy" but i find gnome to have much better visuals than vista. You may just want to consider doing some modifications. Also, i'd sooner download kubuntu than install kubuntu-desktop through apt because it can be buggy.

here's my gnome desktop. transparent custom panels, system monitor, pager, some quick launchers, the infamous compiz cube, vista aero style windows, customized gnomenu button, custom background. this isn't even all you can do with gnome my friend and for the resources it doesn't use, you can't beat it.

---

### Post by dkc.com on 2010-09-05
> **d3v1150m471c said:**
> no doubt kde has excellent "eye-candy" but i find gnome to have much better visuals than vista. You may just want to consider doing some modifications. Also, i'd sooner download kubuntu than install kubuntu-desktop through apt because it can be buggy.

here's my gnome desktop. transparent custom panels, system monitor, pager, some quick launchers, the infamous compiz cube, vista aero style windows, customized gnomenu button, custom background. this isn't even all you can do with gnome my friend and for the resources it doesn't use, you can't beat it.

Saw all your images and they look quite impressive and convincing. Which programs have you used for that?

---

### Post by perspectoff on 2010-09-05
I have both Kubuntu (with KDE4) and Ubuntu (Gnome) on my laptop (as well as Windows 7). 

I pretty much only use Kubuntu, though, and have done so for about 3 years, now.

It's all personal preference, though. I just happen to like many KDE apps better, although I do use a fair number of Gnome apps.

I can't get any of my kids or employees (primarily used to Windows) to use Ubuntu, though. They will only use Kubuntu, since it is similar enough to the M$ Windows style.

Check out [http://kubuntuguide.org](http://kubuntuguide.org)

and [http://ubuntuguide.org](http://ubuntuguide.org)

Yes, I think

 sudo apt-get install kubuntu-desktop

is sufficient, as well as

 sudo apt-get install kubuntu-restricted-extras

PS Those effects are easy in both KDE and Gnome. (They are available in Windows Vista and 7, as well.) However flashy they seem, they aren't really that useful on a day-to-day basis. I leave them turned off.

Check out some demos on You Tube if you really want to see the flash of either Ubuntu or Kubuntu:

[http://www.youtube.com/watch?v=LdIEeJ9PnGc](http://www.youtube.com/watch?v=LdIEeJ9PnGc) (Kubuntu)
[http://www.youtube.com/watch?v=WturcjzIjXg](http://www.youtube.com/watch?v=WturcjzIjXg) (Ubuntu)

Also:

[http://www.youtube.com/watch?v=GhucfBFoTFs](http://www.youtube.com/watch?v=GhucfBFoTFs) (Kubuntu)
[http://www.youtube.com/watch?v=VvfRpmqKRbs](http://www.youtube.com/watch?v=VvfRpmqKRbs) (Ubuntu)

---

### Post by Nythain on 2010-09-05
> **dkc.com said:**
> 
At that time I feel that the Gnome desktop, however sturdy it is, misses the eye candies of Vista so want to try KDE 4.5.

Really, is everyone else missing the 4.5 part of that sentence? just installing kubuntu-desktop from the lucid repos will not get you 4.5 which is well worth the upgrade. 4.5 brings into play countless bug fixes, better stability, new and exciting features like an honest attempt at tiling and a better system tray.

The only way i know of that you are gonna get 4.5 in lucid is to make sure you add the kubuntu backports ppa, or wait till Maverick gets its official release

---

### Post by marl30 on 2010-09-05
KDE Definitely have a more stable feel to it since since 4.5.1 came out. I installed the KDE desktop on Ubuntu and upgraded to 4.5.0 a few weeks ago. I was dissatisfied with the instability issues, so I cleaned it off. Now I installed it once more after 4.5.1 has been released, and I must saying, I'm loving it. Kinda made me regret I took off Mint 9 KDE. I still love Gnome, so the dual desktop will suit me well. :D

---

### Post by d3v1150m471c on 2010-09-05
> **dkc.com said:**
> Saw all your images and they look quite impressive and convincing. Which programs have you used for that?


the panels and background i made in gimp. to use photoshop brushes just place them in ~/.gimp/brushes and load gimp. make the panel the height of what you'll set your panel to and the width being your resolution. the menu button is something else i made on gimp and uses Gnomenu. to set compiz up and the cube first:

```

sudo apt-get install compiz-settings-manager

```

there's many tutorials for it online. the terminal is just a transparent profile. right click your terminal and you'll see the options for it. and last but not least 
```

sudo apt-get install emerald

```

setting up emerald can be a pain. if you open up the file called ~/.profile and somewhere at the bottom on a line by itself add this code:
```

emerald --replace &

```

it'll start right up for you when you log back in (that's if you have issues with it. other than that the monitor to my right is the system-moniter. right click your panel to add it. the pager top right, same deal. good luck

---

