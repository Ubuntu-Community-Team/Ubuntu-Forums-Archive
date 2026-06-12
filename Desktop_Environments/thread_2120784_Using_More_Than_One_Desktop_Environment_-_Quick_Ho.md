---
title: "Using More Than One Desktop Environment - Quick How To?"
date: 2013-02-27
forum: Desktop Environments
---

### Post by benluca1 on 2013-02-27
Hello forums!

I'm using a fresh install of **Xubuntu**, thinking of installing the **Cinnamon** desktop, which I've used recently (and briefly) in Mint 14 Nadia and liked. 

The (small) problem is, that I DO like** XFCE** and concerned that I may be losing it altogether if I convert to Cinnamon. 

From what I've garnered by reading various info pages, is that (in Linux), you do not actually lose a desktop environment when you install another, but are able to choose which environment you wish to use at each login?

Is this true, and if so, is it automatic? Or is there somethiing I need to do, in order to have this choice? Thanks for the help and info. 

Respectfully,

Ben

---

### Post by unheeding on 2013-02-27
Installing Cinnamon won't get rid of xfce.  In the log in screen, under "Session" (usually) there will be options.  The default is likely "Xubuntu" or the xfce desktop environment.  Click on "Cinnamon" and log in, it will bring you to the Cinnamon desktop environment.  It'll probably ask you if you want it to become the default, which is self-explanatory.

---

### Post by benluca1 on 2013-02-27
> **unheeding said:**
> Installing Cinnamon won't get rid of xfce.  In the log in screen, under "Session" (usually) there will be options.  The default is likely "Xubuntu" or the xfce desktop environment.  Click on "Cinnamon" and log in, it will bring you to the Cinnamon desktop environment.  It'll probably ask you if you want it to become the default, which is self-explanatory.

That is what I was hoping. I'm going to give this a try, it will be great to have options available at login, each time. Thanks for your reply.

---

### Post by benluca1 on 2013-02-27
It worked. As a very new Linux user, this is a minor accomplishment. I have installed a few various desktop environments (to inlclude Cinnamon of course) and am having a lot of fun exploring each.

If there are any other new users who wish to try this, here is how I did it,

1. sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
2. sudo apt-get update
3. sudo apt-get install cinnamon

There are probably other ways to go about this, but this one worked for me. 

Respectfully,

Ben

---

