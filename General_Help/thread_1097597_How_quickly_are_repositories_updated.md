---
title: "How quickly are repositories updated?"
date: 2009-03-16
forum: General Help
---

### Post by shadow_code on 2009-03-16
Hi,

for example:

Gedit 2.26.0 was released today. How long will it take for me to receive the update in Ubuntu?

Thanks

---

### Post by geirha on 2009-03-16
Ubuntu does not update the version of packages. During the development of an Ubuntu release, the newest versions of packages are added continously, until the package freeze date (which is about a month after the development cycle started iirc). After the package freeze, whatever version is in the repository, is the final one for that release. A new minor version will come along if there's a bugfix, but the major version numbers stay the same.

So, 2.26.x might be the version of gedit in the release after Jaunty Jackalope ...

---

### Post by shadow_code on 2009-03-16
ok thanks

Is their a way of getting the latest version of software through the package system? So that bug fixes are still automatically downloaded.

---

### Post by skymera on 2009-03-16
Check [www.getdeb.net](www.getdeb.net)

---

### Post by snowpine on 2009-03-16
The answer to the original question is, every 6 months (with each new release) unless it is a bug fix or security update.

---

### Post by shadow_code on 2009-03-16
but I want it now :(

I'll have to figure out how to install it from source sometime... dependencies have scared me off for now :P

---

### Post by geirha on 2009-03-16
It is likely that gedit 2.26.0 has the same dependencies as gedit from the repositories, and to install the dependencies for the gedit in the repos, you run the command
```
sudo apt-get build-dep gedit
```

---

### Post by shadow_code on 2009-03-16
cool thanks :D

I'm almost there, but I got the following error:

```
checking for PYGTK... no
configure: WARNING: Requested 'pygobject-2.0 >= 2.15.4' but version of PyGObject is 2.15.3
configure: WARNING: Disabling python support

```

---

### Post by SamNSane on 2009-03-16
> **shadow_code said:**
> but I want it now :(

I'll have to figure out how to install it from source sometime... dependencies have scared me off for now :P

From what I can see, there are several ways in which you might obtain a version update for a given package in Ubuntu without a lot of fussing around:

1. from the main repositories -- This isn't really supposed to happen, I guess, insofar as full application software packages are concerned. But I do occasionally see version upgrades for packages when they consist primarily of bug fixes / security fixes instead of the addition of features. Or my old brain may be confusing offerings from the backport repository with stuff from the standard repository.

2. from the backport repositories -- The Ubuntu community provides for the ability to get later versions of many packages through this "unofficial" repository. (I guess unofficial means that it's not directly supported by Canonical.) These versions are not as thoroughly tested or vetted for use with your Ubuntu version as packages in the standard repository, but they are items from subsequent Ubuntu versions which should work pretty well for your current version. You can petition the maintainers of these repositories to include specific packages you'd like to see, but you have to provide reasons (functional / security / whatever). If you do a good enough job of documenting your reasons, they may include the software you want.

3. from repositories maintained by the developers of the package you want to upgrade -- Most developers don't do this, but a few do. (The gedit devs do not, AFAIK.) If the devs maintain a repo that's designed to service your distribution / version you're golden. I would characterize this as being slightly more risky than #2 above, since the Ubuntu community may or may not have had any involvement in development / integration of the package. But this is generally a safe source for upgraded software packages. Be sure to import their key into Synaptic, as well as the repository location.

4. from repositories maintained by members of the Ubuntu community at the launchpad ppa locations -- There are folks who have particular interests in certain packages who adapt, compile, and maintain repositories to provide those packages to folks running various Ubuntu versions. You add the repository location and key for your particular Ubuntu version into Synaptic, and from now on that PPA repository is one of the repos Synaptic and the Update Manager check when looking for packages to install or update. The package manager will automatically compare the different versions of the software you want and choose the latest one to offer to you.

5. by downloading a .deb file from the package maintainers' site or from a third party site (like GetDeb) -- If you get a .deb file that was either
a) made for your particular version of Ubuntu, or
b) made for "all" Debian-based distributions
you should be reasonably safe in installing it -- asuming that any third party source you might use is known to be trustworthy. However, installing software by this method will result in you no longer receiving automated security updates and bug fixes for the software. If you want a subsequent update to the software, you should go back to the location where you got your current version to see if a new one is posted.

The above methods are generally listed in order of decreasing desirability (with #s 3 and 4 maybe being roughly equivalent -- the software devs knowing more about their own software and the launchpad guys knowing more about integrating that software into Ubuntu), from the standpoint of the likely reliability of the installation process and the resulting software installation.

Compiling software from source has a lot of drawbacks. The most important one, IMO, being is that a kernel upgrade (or even something less central to the system) may break your compiled software, depending on just what kind of software it is. Having to uninstall compiled software and drivers before upgrading kernel versions, then recompiling and reinstalling seems like a whole lot of work (for not much return) to me these days.

YMMV. These days I'd rather work **with** the computer than work **on** the computer.

---

### Post by shadow_code on 2009-03-16
Thanks for the info,

I couldn't find a solution for gedit, but I've managed to install it from source now anyway :smile:

---

### Post by SamNSane on 2009-03-16
> **shadow_code said:**
> Thanks for the info,

I couldn't find a solution for gedit, but I've managed to install it from source now anyway :smile:

I kind of figured you'd go that way. Good for you.

There are some GUI glitches in 2.22.3 that have been pestering me for a while. Now that you've brought this up I'm going to go look at their change log to see if those have been fixed. If so, I may be joining you.

---

