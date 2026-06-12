---
title: "Downgrade back to KDE 3"
date: 2010-06-17
forum: Desktop Environments
---

### Post by C.Marlow on 2010-06-17
Hi Everyone,

I have currently the LATEST version of Kubuntu 10.04 and I just DO NOT LIKE kde 4.... There are things I liked better in 3 than I did 4. I hate the desktop containers I hate when you turn them off and put your icons on the desktop they pop back to where they were before I just found it to have more JUNKWARE than I wanted . I just want simple KDE 3 back.

I had KUBUNTU 8.10 and thinking I was getting KDE 3 it gave me KDE 4.0.0 ( the one where the taskbar was black ) 

Is there a way to find to get I guess 8.04 to get KDE 3.5 back?

Thanks,
Christopher

---

### Post by ankspo71 on 2010-06-18
Hi,
I'm not sure about downgrading KDE, but I think there is a PPA available... but I couldn't locate it. 

However, if you want to do a reinstall of Lucid with KDE 3.5 (Kubuntu Trinity 10.04), here is a link for live cds.
[https://wiki.kubuntu.org/Kubuntu/Kde3/Lucid](https://wiki.kubuntu.org/Kubuntu/Kde3/Lucid)
(All three mirrors have Lucid)

Hope this helps.

PS. Here is a link to Kubuntu 8.04 [http://releases.ubuntu.com/kubuntu/8.04/](http://releases.ubuntu.com/kubuntu/8.04/)

---

### Post by ankspo71 on 2010-06-18
I found the PPA's for KDE 3.5 ;)

**Step 1. Install the PPA**

KDE 3.5
[https://launchpad.net/~kde3-maintainers/+archive/ppa](https://launchpad.net/~kde3-maintainers/+archive/ppa)
to add the repository:
```
sudo add-apt-repository ppa:kde3-maintainers/ppa
```

[COLOR="Red"]Optional: (Probably very experimental!)[/COLOR]
KDE 3.5 Nightly Builds
[https://launchpad.net/~kde3-maintainers/+archive/trinity-svn-nightly](https://launchpad.net/~kde3-maintainers/+archive/trinity-svn-nightly)
to add the repository:
```
sudo add-apt-repository ppa:kde3-maintainers/trinity-svn-nightly
```

**Step 2: Install KDE 3.5**
```
sudo apt-get update
sudo apt-get install kubuntu-desktop-kde3
```

Note: this might want to remove some kde packages that are not compatible with KDE 4x.

Hope this helps

---

