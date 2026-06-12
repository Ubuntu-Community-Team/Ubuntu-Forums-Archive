---
title: "Something similar to Ubuntu Software Center for KDE?"
date: 2010-07-17
forum: Desktop Environments
---

### Post by murderslastcrow on 2010-07-17
Before I start, I've already installed the Ubuntu Software Center, which didn't work (it won't start). However, I think it's just some dependencies not being met or something, and I don't want to have to install tons of Gnome stuff just to get something like the software center.

I understand the technical benefits of using PackageKit, and I'm really glad to use it, except that it doesn't easily separate graphical applications from libraries, and there are no screenshots/thorough descriptions available so far as I can see.

This basically makes it hard for a newbie to find their way around and realize the great selection of software available for Linux. Having a software-center-like application is great for opening someone's eyes to that.

Even something similar to the ol' Add/Remove dialogue would be satisfactory. So long as it has some kind of description- I really don't care if it doesn't let you install libraries, only graphical utilities/programs. That would actually be preferable in some cases.

Of course, it would be nice if KPackagekit started integrating some of those features, but we can only hope. I can't really find anything Qt-based along these lines just yet. T^T Why does everyone in FOSS hate round menus and radial gradients?? I'll never understand.

---

### Post by ajgreeny on 2010-07-17
What about **synaptic**, a sort of advanced software-center. It's what I always use in gnome ubuntu, (in fact I've yet to use software-center), and I know it will run in kubuntu, though I have no idea how much of the gnome desktop it will need in order to run.

---

### Post by murderslastcrow on 2010-07-17
KPackageKit is kind of an advanced Synaptic, actually. Well, there are some things in Synaptic like pics, but Synaptic has always been too listy and not applicationy enough. The Ubuntu Software Center categorizes stuff based on what kind of application it is, which roots out all the libraries, and it brings up applications before libraries.

That's more of what I'm looking for. But thanks for the info! Maybe I should just code my own in Python, lmao.

---

### Post by StephanG on 2010-08-09
I've just discovered Muon and so far I'm loving it!

Its an advanced package manager like Synaptic built on Qt for Kubuntu.

Just add "ppa:echidnaman/qapt" to your repositories and then its simply a matter of: ```
 sudo apt-get install muon 
```

Its not quite software center, but IMHO its several leagues above KPackageKit.

P.S. Its still a beta, so it isn't quite bugfree yet.  But its getting close.

---

### Post by ankspo71 on 2010-08-09
> **StephanG said:**
> I've just discovered Muon and so far I'm loving it!

Its an advanced package manager like Synaptic built on Qt for Kubuntu.

Just add "ppa:echidnaman/qapt" to your repositories and then its simply a matter of: ```
 sudo apt-get install muon 
```

Its not quite software center, but IMHO its several leagues above KPackageKit.

P.S. Its still a beta, so it isn't quite bugfree yet.  But its getting close.

Yeah, I was just reading about Muon here the other day: [http://jontheechidna.wordpress.com/2010/07/05/introducing-qapt-and-the-muon-package-manager/](http://jontheechidna.wordpress.com/2010/07/05/introducing-qapt-and-the-muon-package-manager/) and I think it looks like it is going to be nice to use. I haven't tried it yet though (because I couldn't remember the name of the application until I read your post lol).

---

