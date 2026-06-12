---
title: "Installing KDE Plasma 5.6 on 16.04"
date: 2016-03-23
forum: Desktop Environments
---

### Post by geovino on 2016-03-23
I tried to install KDE 5.6 on Kubuntu 16.04 beta and used these instructions to add the PPA. 
[http://www.omgubuntu.co.uk/2016/03/kde-plasma-5-6-released](http://www.omgubuntu.co.uk/2016/03/kde-plasma-5-6-released)

It doesn't work. How do you install KDE 5.6 in Kubuntu 16.04?

---

### Post by QDR06VV9 on 2016-03-23
Don't kill the messenger..but It dose not look like it will make it to Xenial.
[https://www.reddit.com/r/Kubuntu/comments/3zv5bc/sounds_like_1604_will_ship_with_plasma_55_not_56/](https://www.reddit.com/r/Kubuntu/comments/3zv5bc/sounds_like_1604_will_ship_with_plasma_55_not_56/)
[https://planetkde.org/](https://planetkde.org/)

**EDIT:** A friend just sent me this link, **have a careful look**.
[http://neon.kde.org/download](http://neon.kde.org/download)

So for 16.04 you should be able to 
Install KDE neon
You will need to open a terminal to enter the following instructions.


Add the KDE neon package archive
[B]export NEON_ARCHIVE=unstable # or set to 'stable' for Git development stable branches
[/B]
```
export NEON_ARCHIVE=unstable # or set to 'stable' for Git development stable brancheswget -qO - 'http://archive.neon.kde.org/public.key' | sudo apt-key add -
sudo apt-add-repository http://archive.neon.kde.org/${NEON_ARCHIVE}

```
```
sudo apt update
```
Install KDE neon
```
sudo apt install neon-desktop
sudo apt full-upgrade
```

---

### Post by buzzingrobot on 2016-03-24
Yesterdays' FAQ on the Neon developer preview says there are no Xenial packages. Also, it "doesn&#8217;t have builds of applications yet..." and that it is not "necessarily" stable, but "built from Git stable branches, not released software."  [http://jriddell.org/2016/03/23/kde-neon-developer-edition-installable-image-faq/](http://jriddell.org/2016/03/23/kde-neon-developer-edition-installable-image-faq/)

There are no Xenial packages of any kind in the backports PPA OMGUbuntu cited. An obvious error on its part.

---

### Post by QDR06VV9 on 2016-03-24
Thanks buzzingrobot for a better link with the needed Info if he wants to venture forth..
I will add
> It&#8217;s the developer edition, if you don&#8217;t know how to install it then it&#8217;s probably not for you.
So be prepared to roll-up your shirt sleeves if you are going to dig-in and give it go..
Kind Regards

---

