---
title: "Ubuntu thinks it's Mint"
date: 2009-05-04
forum: General Help
---

### Post by Zoowey on 2009-05-04
Aright, well I've got myself a rather odd question.

I like to use Mint menu in my Ubuntu 9.04 installation, so far I have been using the packages from Linux Mint 6 Felicia, which requires you just install "mintsystem" and "mintmenu". 

I have used mintmenu without any problems what so ever, but just recently I wanted to try out the new version of the mintmenu which is from Linux Mint 7 Gloria (Alpha) and it required me to install an extra package since it was a dependency called "mint-info-main" and ever since I have installed that package my Ubuntu 9.04 installation thinks it's actually Linux Mint 7 Gloria. 

In grub, in the list it specifies the kernel name as Linux Mint 7 Gloria and in my system monitor it does the same. I have uninstalled "mint-info-main" by marking it for "complete removal" in synaptic so it would get rid of any config files but that didn't seem to have any effect.

Now it's not that I don't like Linux Mint but the fact is, this isn't Linux Mint and it's actually messing up some of Ubuntu's native programs and some of my 3rd party programs say that they aren't compatible with the Alpha version of Mint.

This is the Linux Mint repository where I get my packages.
[http://packages.linuxmint.com/](http://packages.linuxmint.com/)

So my question is, how do I fix this and get it to say it's Ubuntu 9.04 again?

[[IMG]http://img65.imageshack.us/img65/6240/screenshotsystemmonitor.th.png[/IMG]](http://img65.imageshack.us/img65/6240/screenshotsystemmonitor.png)

---

### Post by Zoowey on 2009-05-05
Ok, I've fixed the problem with help from another forum.

What I did was simply modify my lsb-release file to:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

And now it seems to be back to normal again.

---

### Post by clemyeats on 2009-05-06
It's not enough. You also need to set the global restoration option to False in /etc/linuxmint/mintSystem.conf

This is going to be changed in the near future so that you won't have to do that. The new adjustment system makes a lot of sense for Mint users but it creates the problem you mentioned for people using Mint tools in other distros. 

We're definitely fixing that as soon as we've got the release out. 

Clem.

---

