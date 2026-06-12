---
title: "Trying to upgrade to Gutsy"
date: 2009-01-19
forum: General Help
---

### Post by fr023nske7ch on 2009-01-19
I have 7.04 installed at the moment and I'm trying to upgrade. However I'm getting this error:

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]

It seems that I get this error when I use the update manager or the add/remove application. It also tells me that there alot of the software isn't compatible because my computer architecture is i386. Any help? Thanks!

I just installed Ubuntu from a 7.04 cd. I'm a beginner, try to explain what you are doing so I can try to get the hang of this thing.

---

### Post by Gondee on 2009-01-19
Mabye you should just burn a copy of 8.10, and install that. And the i386 part should be fine for now.

---

### Post by fr023nske7ch on 2009-01-19
> **Gondee said:**
> Mabye you should just burn a copy of 8.10, and install that. And the i386 part should be fine for now.

I could do that, but I'm wondering if there is any other way. What is this i386 biz about and why is it fine for now?

---

### Post by mssever on 2009-01-19
> **Gondee said:**
> Mabye you should just burn a copy of 8.10, and install that. And the i386 part should be fine for now.
Um, the OP is trying to upgrade, not do a clean install. You can't upgrade directly from Gutsy to Intrepid.
> **fr023nske7ch said:**
> I have 7.04 installed at the moment and I'm trying to upgrade. However I'm getting this error:

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]

It seems that I get this error when I use the update manager or the add/remove application. It also tells me that there alot of the software isn't compatible because my computer architecture is i386. Any help? Thanks!

I just installed Ubuntu from a 7.04 cd. I'm a beginner, try to explain what you are doing so I can try to get the hang of this thing.
Feisty has, I believe, been deleted from the update servers since it's well past end-of-life. Try opening /etc/apt/sources.list and changing all occurrences of "feisty" to "gutsy". That might work. However, upgrading from such an old version will probably be problematic, and it might be fastest to do a clean install of intrepid or hardy.

---

### Post by mssever on 2009-01-19
> **fr023nske7ch said:**
> What is this i386 biz about and why is it fine for now?
I'm confused that you're getting warning messages about that. Could you post the exact text? i386 refers to an Intel 386-compatible chipset. Most people today run i686 (which is backwards-compatible with i386) with a 32-bit OS. If you were running 64-bit, you'd see something different (ia64, I think). At any rate, I run 32-bit and have never encountered software that won't run on it.

---

### Post by fr023nske7ch on 2009-01-19
> **mssever said:**
> Um, the OP is trying to upgrade, not do a clean install. You can't upgrade directly from Gutsy to Intrepid.

Feisty has, I believe, been deleted from the update servers since it's well past end-of-life. Try opening /etc/apt/sources.list and changing all occurrences of "feisty" to "gutsy". That might work. However, upgrading from such an old version will probably be problematic, and it might be fastest to do a clean install of intrepid or hardy.

Ok cool. I was thinking that I was gonna do that anyways. However, will the i386 problem still exist?

---

### Post by theWrkncacnter on 2009-01-19
If you're just starting from scratch, you'll save a lot of downloading time installing afresh :)

Right now, could you do "uname -a" to tell us whether you are running a 64 bit OS or a 32 bit OS at the moment. If you install from scratch, which I think you should, you will have no problems with confused architecture. But updating usually doesn't run into that kind of problem. Exactly what error message did you get?

---

### Post by fr023nske7ch on 2009-01-19
> **mssever said:**
> I'm confused that you're getting warning messages about that. Could you post the exact text? i386 refers to an Intel 386-compatible chipset. Most people today run i686 (which is backwards-compatible with i386) with a 32-bit OS. If you were running 64-bit, you'd see something different (ia64, I think). At any rate, I run 32-bit and have never encountered software that won't run on it.

Right, so in the add/remove application, alot of the applications will tell me this in the description box (7zip):

This application is provided by the Ubuntu community.
7zip cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

Its true that I am running a pretty old computer, 5 or 6 years old, a Dell Inspiron 600m. Does Ubuntu not support this?

---

### Post by mssever on 2009-01-19
> **fr023nske7ch said:**
> Right, so in the add/remove application, alot of the applications will tell me this in the description box (7zip):

This application is provided by the Ubuntu community.
7zip cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

Its true that I am running a pretty old computer, 5 or 6 years old, a Dell Inspiron 600m. Does Ubuntu not support this?
That's an odd error message. I'm running 32-bit and I can install 7zip. And my server dates to 2002 and runs Ubuntu fine, albeit slowly since I don't have enough RAM. If you go the reinstall route, hopefully that message will go away. Be sure you install the 32-bit version, as the 64-bit version won't work on your hardware (you probably knew that already :)).

Oh, one other thing: I'm not too familiar with the ins and outs of Add/Remove, since I never use it. Do you get that same message from Synaptic or when trying to install via the command line? To install 7zip from the command line: ```
sudo aptitude install p7zip-full
```

---

### Post by jrusso2 on 2009-01-19
Really do a clean install of either 8.04 or 8.10 since Gutsy will be next to go unsupported.

I would not worry about that error message, I would think this issue has something to do with the feisty repository being gone.

---

### Post by niteshifter on 2009-01-19
Hi,

As you say you're just starting let's (and I seldom say this) do a do-over, aka a fresh install. You problem is fixable, but with a lot of effort.

8.04.1 (Hardy) has 2 years, 3 months left until the repositories are removed. This is what's known as a LTS (Long Term Support) release.
8.10 (Ibex) has 1 year, 3 months left. It is not a LTS release.
Another thing to consider is generally moving from one LTS to the next is pretty much painless.

The choice is yours.

---

