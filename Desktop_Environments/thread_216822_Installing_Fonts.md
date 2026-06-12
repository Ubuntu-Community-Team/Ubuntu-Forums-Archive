---
title: "Installing Fonts"
date: 2006-07-16
forum: Desktop Environments
---

### Post by khaledaboualfa on 2006-07-16
I know this is a tried and tested question. I have read through the How to off the wiki:

[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)

But for some reason when I try and drag and drop fonts into either the fonts: folder or the usr/share/fonts/ folder it doesn't allow it and I get the following message:

You do not have permissions to write to this folder.

How do I solve this? Do I need to install fonts from the command line? If so is there any thread or post someone could direct me to? Thanks in advance.

---

### Post by Jagot on 2006-07-16
The only directory you have permission to write to normally is your /home folder.  You just need to start Naultilus as root.  Hit alt-f2 the type:

```
gksudo nautilus
```

Now you will be able to move files into your /usr/share/fonts directory.

---

### Post by coffeecat on 2006-07-16
I've had a quick look at that howto. Seems a tad over-complicated. So as not to repeat myself, have a look at the posts by bruce89 and myself in [this thread.](http://www.ubuntuforums.org/showthread.php?t=215955)

---

### Post by Perfect Storm on 2006-07-16
Is it fonts you need to use with OO, gimp etc for one user? Then just make a folder in your home called **.fonts** then drop the fonts in there.

---

### Post by khaledaboualfa on 2006-07-16
Wow, that was fast. Actually no I'm just trying to get some fonts in so that I can also use them in firefox. Some websites (unfortunately mine included) looks really different to what I'm used to on a windows box and it shouldn't at all. The only thing that I've noticed to be the case is the fonts. Lucidia isn't there. 

Also I'm just asking as I'm a designer who's recently made the switch over to Linux and I'm trying to sort my house out so to speak. So I need like a good font manager/viewer as well amongst other things.

Thanks for the help everyone. I'll report back if I've got any problems.

---

