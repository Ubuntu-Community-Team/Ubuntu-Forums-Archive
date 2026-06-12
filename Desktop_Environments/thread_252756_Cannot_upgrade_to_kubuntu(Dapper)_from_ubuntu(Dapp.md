---
title: "Cannot upgrade to kubuntu(Dapper) from ubuntu(Dapper) using apt-get"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Najand on 2006-09-07
I wanna change the desktop environment to Kubuntu from Ubuntu but whenever I do:

```
$ sudo apt-get install kubuntu-desktop
```

I get the following error... Is there anything wrong with my apt database?

```
najand@najand-ubuntu:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: amarok but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
E: Broken packages

```


Anyone has any idea why? TIA

---

### Post by BLTicklemonster on 2006-09-12
What does it say when you try to install it from synaptic?

---

### Post by Najand on 2006-09-12
Hmm, No... I don't usually use Synaptic...
When using apt-get or aptitude. Maybe I have a wrong
source list.

---

### Post by TransitMan on 2006-09-12
Add this to your sources list - 
deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main

---

### Post by BLTicklemonster on 2006-09-12
WOW. I just installed kde and am in it now. Talk about ... heck eye candy out the wazoo. This makes XP look amatuerish. And I played unrealtournament online, and it didn't cause any performance decrease. Only thing not working is vmware, which I think I can make work. I think I'll hang out in kde (is kde = kubuntu?) for a while to see what it's like.

---

### Post by neoeden on 2006-09-12
kubuntu is ubuntu except it uses kde instead of gnome. So yeah.

---

### Post by -deadcats on 2006-09-12
If you like KDE eye-candy, may I suggest PCLinuxOS?

It's like Kubuntu on steriods--a 686-optimized (Mandriva fork?) KDE that uses apt-get and Synaptic as package managers. 

I've played a ton with the latest release over the past couple weeks. It's got a couple glitches, but so do all distros. Nothing showstopper or without a workaround. Very fast. Fastest Kool Desktop Environment I've ran in ANY off-the-shelf Distro (which precludes Gentoo, of course). :)

I started with KDE, but am hooked on GNOME at the moment (Ubuntu). But if I were ever to go back to KDE then PCLinuxOS is probably what I'd be using. I'm just tired of eye-candy at the moment. I like my nice, minimalistic Ubuntu GNOME desktop at present. :)

regards,
-dc

---

### Post by BLTicklemonster on 2006-09-13
Well, I'm actually anti-eye candy, but this is so quick and smooth. There are no "trails" when I move windows around on the desktop, either, like I see in gnome, even though I have the latest nvidia drivers installed. And being a windows migrator, it has some similarities, and those similarities (the k in the bottom you click and all that stuff pops up) have everything you have listed. Plus it comes with some really neat stuff installed. Really impressive.

---

