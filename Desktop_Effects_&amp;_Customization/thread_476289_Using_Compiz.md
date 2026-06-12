---
title: "Using Compiz"
date: 2007-06-17
forum: Desktop Effects &amp; Customization
---

### Post by RelativelyQuantum on 2007-06-17
Just a quick, fairly straight-forward question: How do you use Compiz? For some reason Beryl just isn't showing up on my "Add/Remove Programs" application, so I decided to download Compiz through Synaptic.

Any thoughts? Comments would be appreciated.

---

### Post by Ozeuss on 2007-06-17
since you needed to download compiz, i guess you aren't using feisty.
first you need to have composite enabled- the howto depends on your card and your xorg version. for instance, in feisty and intel cards, compositing works OOTB. after that you can run compiz.
my recommendation is to install gnome-compiz-manager, and play with it.

---

### Post by RelativelyQuantum on 2007-06-17
Thanks; I'll try that. I suppose I can find that in Synaptic?

---

### Post by RelativelyQuantum on 2007-06-17
Why couldn't I install Beryl in Edgy? I've heard of people installing it in Dapper, et al...

---

### Post by RelativelyQuantum on 2007-06-17
And I've already installed the Gnome manager.

---

### Post by Ozeuss on 2007-06-18
I haven't tried to install beryl in edgy, only on feisty (used compiz on edgy). if it's not in universe, you might need to add a repository for it. best that you look for the plentiful howto's for beryl in this forum.

---

### Post by FuturePilot on 2007-06-18
If you're using Edgy you're going to need to find a repo for it since it isn't in the Edgy repos. You basically have 2 choices. You could find a third party repo for Edgy, or you could upgrade to Feisty which has Compiz in the Feisty repos and it also has it installed by default as well.

---

### Post by RelativelyQuantum on 2007-06-18
> **FuturePilot said:**
> You could find a third party repo for Edgy, or you could upgrade to Feisty which has Compiz in the Feisty repos and it also has it installed by default as well.

How or where would I find a third party repo? I downloaded the .tar.bz file of the latest Beryl distro from the Beryl site; would that fall into this category? Upgrading to Feisty again isn't a particularly appealing option, in that last time it completely nuked my hard drive, taking two other operating systems with it :(.

---

### Post by RelativelyQuantum on 2007-06-18
I accessed this file:
```

gksu gedit /etc/apt/sources.list
```

and added the Beryl repository to it:
```

deb http://ubuntu.beryl-project.org/ edgy main
```

Is there anything I did wrong?

In any case, what's up with the page the url links to? Is that supposed to be there, or was someone pulling my leg?

---

### Post by Ozeuss on 2007-06-19
I didn't quite understand your last post. why would you need to follow the repository link?
after you changed and saved sources.list, run 'sudo apt-get update', or open synaptic and then install or search for the beryl packages.

---

### Post by RelativelyQuantum on 2007-06-19
I followed the tutorial on the Beryl wiki, and had it installed and running within ten minutes. However, when I tried to change the settings in the Beryl manager, my effects stopped working altogether. What could have caused this?

About following the link, I would just expect a resource url to contain something other than a shrine to an anime character. I thought that a bit strange...

---

