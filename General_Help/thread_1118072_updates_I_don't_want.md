---
title: "updates I don't want"
date: 2009-04-06
forum: General Help
---

### Post by Extreedoc on 2009-04-06
Ubuntu is currently urging me to download a Time Zone Data update for Morocco, Tunisia etc. I can see no need to download this for my computer here in England but of course, if I don't download it it will keep offering it. What should I do?

---

### Post by kanikilu on 2009-04-06
Well, you can lock a package to the currently installed version by opening Synaptic, search for "tzdata", click on it, and then go to Package > Lock Version.

However, this means you won't get updates for this package in the future, even if there are changes that apply to you...

My suggestion would be to just install it, but, you always have the option to lock it.

---

### Post by anjilslaire on 2009-04-06
The TZData is already installed on the system, and the Update Manager is simply prompting to apply the latest version. THere's no harm in installing it, and it likely won't even take up any additional space, or if so, just a few kb's. 

It's included on all installations, so nothing out of teh ordinary is happening. I got teh update today on all of my systems here in the US as well.

---

### Post by Extreedoc on 2009-04-06
Thanks fellas, I'll download it then. Cous cous anyone?

---

### Post by sofasurfer on 2009-04-06
But I think the original poster was saying that he doesn't want to install useless stuff whos only purpose (on his particular computer) is to take up space. There are many packages like this that I also would like to avoid. Sure we can just live with it but in the interest of economy and like-to-think-of-things-to-complain-aboutedness, why couldn't there be an option next to non-life-n-death packages to lock them out?

---

### Post by wrose51106 on 2009-04-06
If you don't want / need the original package just uninstall it.

The updates themselves take up a trivial amount of space. I do not know the application but if I write a program called Rose and it is at V 1.0, I then send an update out to change the way the colors look I update to V 1.1. I then find a security flaw that allows daisys to invade my garden so I update again to V 1.2. Hope I didnt confuse anyone besides myself.

-Bill

---

### Post by kanikilu on 2009-04-06
> But I think the original poster was saying that he doesn't want to install useless stuff whos only purpose (on his particular computer) is to take up space. There are many packages like this that I also would like to avoid. Sure we can just live with it but in the interest of economy and like-to-think-of-things-to-complain-aboutedness, why couldn't there be an option next to non-life-n-death packages to lock them out?

In this case, while the *changes* to the tzdata package may be "useless" to a lot of people, the package itself is not. There's not really a way to opt out of updates like this without locking the current version or uninstalling the entire package.

---

### Post by kanikilu on 2009-04-06
> **wrose51106 said:**
> If you don't want / need the original package just uninstall it.

The updates themselves take up a trivial amount of space. I do not know the application but if I write a program called Rose and it is at V 1.0, I then send an update out to change the way the colors look I update to V 1.1. I then find a security flaw that allows daisys to invade my garden so I update again to V 1.2. Hope I didnt confuse anyone besides myself.

-Bill

I think you make a good point (if I'm understanding you correctly). Sure, you can lock a package to a specific version because you've deemed the recent changes not necessary to your installation, however, now you run the risk of missing future updates which may not be so trivial (such as security updates), and now it's up to you to keep track of all that and decide when to upgrade instead of letting a package manager do it. 

Furthermore, short of patching in diffs yourself and "rolling your own", once you update to the latest package that plugs a security hole, you are going to get all the updates in between that you elected to skip in the first place...

So, there's really no point unless you know for a fact that a current package is never going to be updated again with anything you deem necessary (which I'd say is impossible to know), or you are willing to run without any such updates (which I'd say is not good practice)...

---

### Post by wrose51106 on 2009-04-06
Exactly :p

---

### Post by bodhi.zazen on 2009-04-06
> **sofasurfer said:**
> But I think the original poster was saying that he doesn't want to install useless stuff whos only purpose (on his particular computer) is to take up space. There are many packages like this that I also would like to avoid. Sure we can just live with it but in the interest of economy and like-to-think-of-things-to-complain-aboutedness, why couldn't there be an option next to non-life-n-death packages to lock them out?

You have two options :

1. Do a minimal install and add only what you need. It is easier to build up then break down.

2. Change your updates to security only. This is what I do on a server. Other then security or some new feature or bug fix, there is no need to update a package.

---

### Post by Extreedoc on 2009-04-08
> **sofasurfer said:**
> But I think the original poster was saying that he doesn't want to install useless stuff whos only purpose (on his particular computer) is to take up space. There are many packages like this that I also would like to avoid. Sure we can just live with it but in the interest of economy and like-to-think-of-things-to-complain-aboutedness, why couldn't there be an option next to non-life-n-death packages to lock them out?

Thanks Sofasurfer, you understand my concern exactly and I would like to second your plea for a "lock-out" option with non essential and geographically specific packages of this kind.
John.

---

