---
title: "Getting newest Compiz-Fusion and plugins in Gutsy?"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by quadomatic on 2007-10-19
After I upgraded to Gutsy, I had to uninstall all my original compiz-fusion packages, and then reinstalled everything from the ubuntu repositories, rather than trevino's repository.

[http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/)

I noticed I was missing some plugins aftewards, like Cube Atlantis and 3D windows. I tried re-enabling trevino's repository and installing the unofficial and unsupported plugin packages, but this caused compiz fusion to crash when I enabled to 3D windows plugin.

How would I go about getting the latest, greatest version of Compiz Fusion with all the newest plugins? I'm trying to be careful, so as to not break my Ubuntu system.

---

### Post by bitmaster on 2007-10-23
So far I haven't seen anyone run the Atlantis or 3D Windows correctly in Gutsy. Installing the unsupported packages does indeed break Compiz and will not run. People have also been trying to compile the plugins in Gutsy from source, but since the build dependencies for Gutsy are different, the compiz-core will fail to compile.

We can only wait, I hope things will be updated soon!

--Albert

---

### Post by Grishka on 2007-10-23
> **bitmaster said:**
> So far I haven't seen anyone run the Atlantis or 3D Windows correctly in Gutsy. Installing the unsupported packages does indeed break Compiz and will not run. People have also been trying to compile the plugins in Gutsy from source, but since the build dependencies for Gutsy are different, the compiz-core will fail to compile.

We can only wait, I hope things will be updated soon!

--Albert

actually, it is possible to compile compiz-fusion from git. 3d windows and atlantis work just like they should. one could try using CF updater-installer script. it's been superseded by Git4CF Automator, but I've had more luck with using the old script.

---

### Post by craigyjack on 2007-10-23
You can get the newest compiz fusion for gutsy by uninstalling all the compiz stuff from ubuntu's repositories (search for compiz in synaptic and remove them) and then compiling compiz fusion from source. this website is a great easy to follow tutorial for compiling the source code [http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html)

it works for me fine. the only problem i have now is emerald window decorator, i do not know where to get the new emerald, because emerald in ubuntu's repos is dependent on old compiz.

yeah, i had the newest compiz in feisty, then when i upgraded to gusty, i was backtracked back to crappy old 0.5.2 compiz fusion which doesnt run nearly as well as 0.6.0.

soon maybe someone will make a gutsy repo for the newest compiz releases, like trevino did in feisty. for know though, if you want the latest, you'll have to compile it yourself.

o, and if anyone knows where i can get the soruce code for the newest emerald i would appreciate that, cause i cannot find it anyway!

-craig

---

### Post by paul92 on 2007-10-24
Hello,

I can't speak english, I'm french...
I would like to have plugins atlantis, 3D windows and wallpaper but they aren't on gutsy repository, I try trevino's repository of FEISTY to my ubuntu GUTSY but compiz-fusion doesn't run... how can I do? compile?

**In french**

Bonjour,

Je voudrais installer les plugins unsupported de compiz-fusion sur gutsy (atlantis, 3D windows, wallpaper, ...) mais je ne les ai pas trouvés dans les dépots officiels de gutsy.  J'ai essayé les dépots trevino de feisty mais sans résultat...  quelqu'un pourrait il m'expliquer comment compiler ou autre ??
J'aimerais beaucoup les avoir...


AMD 64 3400+, 1024 ram, ATI radeon 9600 PRO, ubuntu 7.10 Gutsy Gibbon, 32bits, compiz-fusion, aiglx, free drivers.

---

### Post by cybersaicho on 2007-10-24
> **paul92 said:**
> Hello,

I can't speak english, I'm french...
I would like to have plugins atlantis, 3D windows and wallpaper but they aren't on gutsy repository, I try trevino's repository of FEISTY to my ubuntu GUTSY but compiz-fusion doesn't run... how can I do? compile?

**In french**

Bonjour,

Je voudrais installer les plugins unsupported de compiz-fusion sur gutsy (atlantis, 3D windows, wallpaper, ...) mais je ne les ai pas trouvés dans les dépots officiels de gutsy.  J'ai essayé les dépots trevino de feisty mais sans résultat...  quelqu'un pourrait il m'expliquer comment compiler ou autre ??
J'aimerais beaucoup les avoir...


AMD 64 3400+, 1024 ram, ATI radeon 9600 PRO, ubuntu 7.10 Gutsy Gibbon, 32bits, compiz-fusion, aiglx, free drivers.

bon jour :)

there are warnings in the internet that say that trevinos repositories are for feisty and NOT for gusty and  if you install them they will not work and probably crash your compiz fusion. but there are indeed people that manage to run these plugins compiled and all i can say is that i already had 3d windows plugin working smooth in a gusty installation :) check these out 

[http://releases.compiz-fusion.org/0.6.0/](http://releases.compiz-fusion.org/0.6.0/)

if you really want those plug ins but be careful compiling them :guitar:

im new to linux and dont know if this helps but its all i know :):):)

---

### Post by unebaguettesvp on 2007-10-24
i think this is the most recent source code for emerald:

[http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php)

0.2.1 is the latest? haven't tried compiling the newest compiz-fusion. thanks for the link. i'm going to try it when i get back home.

---

### Post by Pablo Pablovski on 2007-10-24
There's an installer script for 3D windows on Gutsy in the thread below (post #15). It worked for me...

[http://forum.compiz-fusion.org/showthread.php?t=4860]("http://forum.compiz-fusion.org/showthread.php?t=4860")

---

### Post by unebaguettesvp on 2007-10-24
wait. nevermind. emerald is 0.3 in the ubuntu repository. so, there must be a newer version (> 0.2.1) somewhere out there.

---

### Post by unebaguettesvp on 2007-10-24
[http://cgit.compiz-fusion.org/fusion/decorators/emerald/commit/?h=0.6.0]("http://cgit.compiz-fusion.org/fusion/decorators/emerald/commit/?h=0.6.0")

---

### Post by bas1 on 2007-10-24
I too would like to have compiz fusion 6.0, but I don't want to ruin my current Gutsy installation. I guess my question is this:

        Has anyone tested the latest version of emerald (0.6.0, according to the link above) with the newest version of compiz fusion (also 0.6.0) and found both to be stable?


Thanks! :D

---

### Post by bas1 on 2007-10-24
> **bas1 said:**
> I too would like to have compiz fusion 6.0, but I don't want to ruin my current Gutsy installation. I guess my question is this:

        Has anyone tested the latest version of emerald (0.6.0, according to the link above) with the newest version of compiz fusion (also 0.6.0) and found both to be stable?


Thanks! :D

Well, I installed compiz fusion 0.6.0 from source, but when trying to start it via 'compiz --replace gconf'
I get this:


```
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
```

What's wrong?

---

### Post by unebaguettesvp on 2007-10-25
that worked! once you download that package do:

cd ../
tar jxvf emerald-0.6.0.tar.bz2
cd emerald-0.6.0/
./autogen.sh
make
sudo make install

then go back to Synaptic and install libemeraldengine0 and libdecoration0. compiz-fusion 0.6!!!!!

---

### Post by unebaguettesvp on 2007-10-25
did you remove all packages containing to compiz from synaptic? was this a fresh install of gutsy? or an upgrade?

---

### Post by bas1 on 2007-10-25
> **unebaguettesvp said:**
> did you remove all packages containing to compiz from synaptic? was this a fresh install of gutsy? or an upgrade?

It *was* a fresh install, but I think that I compiled it wrong. Anyways, I re-installed gutsy (nothing big for me, I usually re-install my OSes on a monthly basis) and re-compiled compiz fusion 0.6.0 from source. I also installed emerald 0.6.0 from source and also installed the packages libemeraldengine0 and libdecoration0 from synaptic. I am 100% positive that I compiled everything correctly, but I still get the same error as above when trying to launch compiz via compiz --replace. I can however use the new version of ccsm, and it makes me want 0.6.0 even more :) . 

Any idea on how to solve this problem?

P.S. I did indeed un-install every package pretaining to compiz before I started compiling.

---

### Post by davidforehand on 2007-10-29
I tried compiling following this link also.
[http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html)

After uninstalling all compiz traces in synaptic and deleting everything pertaining to compiz in my home directory I started compiling. Everything appeared to have compiled and installed correctly with no errors and I also installed emerald from git. However when I do the "compiz --replace gconf" I lose my window decoration and no compiz plugins work not even the cube. ccsm does open but nothing works.

Just for reference Ive tried this on my desktop with both fresh installs of ubuntu and kubuntu and tried it on my laptop with kubuntu.

I also did a "locate compiz" in the root directory before compiling and it found some entries but I was unable to delete them and I figured everyone who has been able to get it to work probably didnt have to delete these files.

---

### Post by davidforehand on 2007-10-29
Here is what happens when I type the following in the terminal.

david@david-desktop:~$ compiz --replace -c emerald &
[1] 9198
david@david-desktop:~$ compiz (core) - Warn: Unknown option '-c'

compiz (core) - Error: Couldn't load plugin 'emerald'

---

### Post by davidforehand on 2007-10-29
I fixed it for my problem, maybe it will help you out.

i put this code in the terminal

    ```
compiz --replace ccp &
```

after that i put the next one in the terminal

     ```
emerald --replace &
```

Im sure you can combine the two but I new and not sure how.

---

### Post by davidforehand on 2007-10-29
The next question is where is the atlantis and the 3D window plugins? The snow plugin is there but not the others. Were they removed from the plugins-unsupported list?

---

### Post by Hexxagon on 2007-10-29
> **davidforehand said:**
> The next question is where is the atlantis and the 3D window plugins? The snow plugin is there but not the others. Were they removed from the plugins-unsupported list?

Uh, where exactly is the snow plugin??

---

### Post by bas1 on 2007-10-29
> **davidforehand said:**
> I fixed it for my problem, maybe it will help you out.

i put this code in the terminal

    ```
compiz --replace ccp &
```

after that i put the next one in the terminal

     ```
emerald --replace &
```

Im sure you can combine the two but I new and not sure how.

These steps did not solve my problem. Still no compiz fusion 0.6.0, and no emerald :( .
I am getting the same error as before.

---

### Post by unebaguettesvp on 2007-10-29
@bas1

have you tried this?

[http://ubuntuforums.org/showthread.php?t=587819]("http://ubuntuforums.org/showthread.php?t=587819")

---

### Post by bas1 on 2007-10-29
> **unebaguettesvp said:**
> @bas1

have you tried this?

[http://ubuntuforums.org/showthread.php?t=587819]("http://ubuntuforums.org/showthread.php?t=587819")

This does not apply to me, as I have an intel 915 gms chipset with integrated graphics, but thanks anyways.

---

### Post by veratyr on 2007-10-29
Is there a repository with packages for gutsy yet?

---

### Post by Ehtetur on 2007-11-01
Can someone tell me where  they've hid the source code for the atlantis plugin?
I found the source for 3d cube effects in compiz-fusion and was able to compile and install a deb.
I'd like to do the same for atlantis

---

### Post by giri1985 on 2007-11-05
Try this:

[http://forum.compiz-fusion.org/showthread.php?p=35533](http://forum.compiz-fusion.org/showthread.php?p=35533)

---

### Post by bas1 on 2007-11-05
Wow, that really works. Please note though that this is done with the default version of compiz fusion that comes with Gutsy, and does not update the core of compiz. It does however add on some of the most notable new plugins.

---

### Post by mjpoetic on 2007-11-09
> **davidforehand said:**
> I fixed it for my problem, maybe it will help you out.

i put this code in the terminal

    ```
compiz --replace ccp &
```

after that i put the next one in the terminal

     ```
emerald --replace &
```

Im sure you can combine the two but I new and not sure how.
just put an "&&" in between the commands on one line

---

