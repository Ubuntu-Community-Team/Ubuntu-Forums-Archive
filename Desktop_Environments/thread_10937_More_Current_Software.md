---
title: "More Current Software?"
date: 2005-01-12
forum: Desktop Environments
---

### Post by JackDog on 2005-01-12
I just started using ubuntu on one of my systems to see what it is like for a desktop computer. I have been using gentoo for the last three years and am fairly happy with it. Ubuntu offers a less painless upgrade infrastructure and gives a simple interface for keeping the machine up to date. I am not questioning the reasons for producing a stable distro, what I question is what should a distribution encompass?

My question is why does ubuntu not load more current software? For instance a recent thread asked why firefox 1.0 was not marked as stable... Well why wouldnt it be? Does ubuntu feel that they need to offer support for seemingly third party software? Should mswindows offer support for firefox? I can understand DE and WM versions, that makes sense since they tend to be customized, but a web browser, email client, IM client? This type of software has already been tested by the respective projects QA system. If those systems are not up to par, it would make sense to hold versions back. But firefox? It is probably the most tested OO project, ever... millions of users.... A distribution needs to focus on its core, let the users decide which software they want to use, categorize it as stable or unstable, tested or untested, but give them easy access. This single attribute made gentoo a very powerful and popular distribution.

It seems completely unnecessary to put products back through QA when they already passed a more stringent set of tests by their authors. For ubuntu to survive I really believe there needs to be an easier way to use the latest software. Ubuntu needs to focus on the "distribution" (kernel, Xorg, glibc, gcc, synaptic)  not the individual applications. (firefox, gaim, evolution,  openoffice). Why dont you just provide access from your site to the user forums for the products themselves? No offense but it takes a very large user base (like gentoo) to provide support for all the products it entails. Ubuntu just isnt there yet, even if they were, I would rather get answers from the products site because they tend to be more responsive and accurate.There is no reason to double our efforts. In the corporate world if we have a problem with a product, we ask the makers, not the packagers. That saves us a lot of time.  

I would just like to see if there is a valid counter argument. I am in a corporate environment that uses SUSE and its a real pain in the butt to maintain. But our developers all have the latest third party software versions. Everyone uses firefox 1.0, tbird 1.0, and kde 3.3.2 or gnome 2.8.3. In lots of cases they have to. The only thing holding us back from using Ubuntu is the lack of current software. I realize we can create our own repo and package our own software, or point to another repo, but its hard to sell a distro that needs to be polished on our end. 

Seems to me like ubuntu should keep just about every aspect of the production cycle the same, except expose a repository that provides more current software by default for desktop installs. In my opinion, that would make ubuntu unstoppable in the desktop market. No one else provides such a cutting edge suite. In the server market, admins can simply not use the more current repos and the install can disable them.

---

### Post by jdong on 2005-01-12
I value Ubuntu's consistency. However, I certainly agree that many users do have justified demand for newer software.

When running sensitive programs, like Matlab (3rd party native binary-only), or MCC18 (Windows-only app run through WINE), having differing versions of certain packages yields wildly different results.

For example, with 20040615 of WINE, I must symlink a lot of MCC18's binaries to a non-EXE extension, while I don't for 20040716, while I do for 200412xx. Having tech support deal with these consistencies will drive anyone crazy.

Plus, system vulnerabilities are harder to track and fix when everything is friggin' changing versions. Gentoo bugfixes are commonly accompanied with broken patches, usually taking at least 2 more revisions before a proper fix is made. Fedora's errata has some absolutely EMBARRASSING, yet concerning, mistakes due to its high pace.

==========================


On the other side of the argument, I believe that desktop applications do need to be more up-to-date. Many of us here believe so. Since Ubuntu's team obviously won't provide them, I've decided to take things into my own hands. I started the Ubuntu Backports project: [http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47), to offer high-quality, maintained and stability-focused backports of various non-system-critical packages. So far, I've packaged over 250 backports (and received a whopping 3 dollars!) for Warty Warthog, and the activity simply never ceases.

I hope that the Ubuntu team will see from my project that you CAN have stability and the latest packages at the same time, and therefore will offer OFFICIAL updates in the near future.

-- Ubuntu Backports.

---

### Post by JackDog on 2005-01-12
Thank you for the reply. Your backports system could work very well for us. I will definitely check into that. I would just like to find a ports/bedian based distro that takes more of a windows approach to updating. Focus on the "system" not the apps. Of course what is a system? Does that include the DE? Would be nice if it didnt. It would also be nice if Ubuntu would slot most apps. So I could run the stable gnome and the unstable 2.9.3 gnome and blow away either whenever I wanted to. gentoo does this with KDE and it works great. KDE libs are stored in the path rather than absolute locations. So if you compile k3b you can compile it against 3.1, 3.2 and 3.3 if you want. 

One note with gentoo though, although the distro as a whole will never be as stable as other distros, they do have a staging mech built in via masking and environment. But someone has to be the canary in the coal mine. If you run stable (x86) 98% of the time things will just work but you never know for sure... I am just getting tired of compiling things all the time. But to get customized software there really is no other way...

---

### Post by castrojo on 2005-01-12
Look into "debootstrap" if you want to run hoary inside of warty to play with unstable versions of stuff.

> For ubuntu to survive I really believe there needs to be an easier way to use the latest software. 

Really, a 6 month release cycle is plenty fast.

---

### Post by JackDog on 2005-01-13
[i]
Really, a 6 month release cycle is plenty fast.
[/i]

I think my point is that the "cycle" isnt the problem for most software packages. Ubuntu doesnt need to support all of the applications it can install. Firefox1.0 has already been tested and released by its makers but average ubuntu users wont see it until hoary is out.  6 months is an eternity to firefox development, it changes very fast. As do KDE and gnome, especially wrt bugs.. Ubuntu, (In my opinion) should find a way to get users these updated programs more easily. Universe is great for "unsupported" software. It would be nice if that functionality was relayed a little better to new users after an install.  jdong's backports are really nice, but again, its too bad this repo isnt included as an available repository to the user right after an install. 

Anyways, this is an exciting distro. Hopefully it will continue to grow. There just arent enough viable debian based linux distros out for the desktop. I just wanted to get a idea of how the users, admins and devs felt about an idea. A great distro in my mind would be one that after an install, the software would be a little more current =)

---

### Post by JackDog on 2005-01-13
[i]
Really, a 6 month release cycle is plenty fast.
[/i]

I think my point is that the "cycle" isnt the problem for most software packages. Ubuntu doesnt need to support all of the applications it can install. Firefox1.0 has already been tested and released by its makers but average ubuntu users wont see it until hoary is out.  6 months is an eternity to firefox development, it changes very fast. As do KDE and gnome, especially wrt bugs.. Ubuntu, (In my opinion) should find a way to get users these updated programs more easily. Universe is great for "unsupported" software. It would be nice if that functionality was relayed a little better to new users after an install.  jdong's backports are really nice, but again, its too bad this repo isnt included as an available repository to the user right after an install. 

Anyways, this is an exciting distro. Hopefully it will continue to grow. There just arent enough viable debian based linux distros out for the desktop. I just wanted to get a idea of how the users, admins or devs felt about an idea. A great distro in my mind would be one that after an install, the software would be a little more current. In the last 24 months the linux desktop has grown tremendously. If it keeps accelerating, even a 6 month cycle for system specific packages will be too slow.

---

