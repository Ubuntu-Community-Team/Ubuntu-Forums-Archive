---
title: "Desktop Environments"
date: 2008-05-27
forum: Desktop Environments
---

### Post by freeflyer57 on 2008-05-27
So I have tried KDE, GNOME, Lookxp, and fluxbox. What other environments are there besides those and IceVM?

---

### Post by jpyanowski on 2008-05-27
What are you looking for?

---

### Post by freeflyer57 on 2008-05-27
any kind of environment. It doesn't have to be light or anything. I just want to know what people think of other environments.

---

### Post by ladr0n on 2008-05-27
If you want something completely different, try ratpoison
If you want something quite pretty (but not necessarily stable), try enlightenment aka e17
There's also xfce, which is vaguely similar to gnome, but a bit lighter.

---

### Post by freeflyer57 on 2008-05-27
I was checking out enlightenment and came across this.

[http://www.elvenspirit.com/screenshots/Screenshot_423613_original.jpg]("http://www.elvenspirit.com/screenshots/Screenshot_423613_original.jpg")

---

### Post by LeoSolaris on 2008-05-27
I rather like FVWM-Crystal. It's in the repo, so it's an easy install.

I am not really partial to most of the WM's yet, but I have not exhausted my search either. Just use Synaptic to look up window manager. IIt will give to a slew of them, as well as a lot of other things so you will have a little sifting to do.

Fluxbox is pretty interesting so far as well.

Just my two cents

---

### Post by freeflyer57 on 2008-05-27
So as I was installing e17, and I messed up. Well I happened to notice that half of my computer is in German, while the other half is in English. Normally, it's in German. So now it's Applications -> Spiele (games). Naja. don't know if it happened during or what, but it's really weird and hard to get around.

---

### Post by Tux Aubrey on 2008-05-27
> If you want something quite pretty (but not necessarily stable), try enlightenment aka e17

The version available in the Ubuntu repos is a bit old.

To get the latest builds, use [Rui Pais guide]("http://ubuntuforums.org/showthread.php?t=546746"):

I find the latest version to be very stable - especially without the more bleeding edge e-apps that Rui leaves out.

---

### Post by freeflyer57 on 2008-05-27
> To get the latest builds, use Rui Pais guide:


I tried this, and I got a dependency error. So I moved on. At first I was doing it by hand, but I stopped and tried that method.

---

### Post by RedSquirrel on 2008-05-27
Openbox is nice. :)

---

### Post by shrimphead on 2008-05-28
on a related note, has anyone managed to get ede compiled under hardy?

---

### Post by urukrama on 2008-05-28
> **RedSquirrel said:**
> Openbox is nice. :)

Indeed!

If you want to try Openbox, follow the link in my signature. You'll find all the information you'll need to get you started with Openbox.

---

### Post by atomkarinca on 2008-05-28
If you want a decent E17 experience under Ubuntu I suggest [openGEU]("http://opengeu.intilinux.com/Home.html"). You can install it as a meta package after adding the repository.

Other than that [LXDE]("http://lxde.sourceforge.net/") is worth trying I think. But to me Fluxbox rules.

---

### Post by rishabh on 2008-05-28
If you're willing to deviate from the path of traditional DEs, take a look at Sun's idea of a Java-based 3D desktop environment:

[https://lg3d.dev.java.net/](https://lg3d.dev.java.net/)

And of course, screenshots ;)

[http://www.sun.com/software/looking_glass/details.xml](http://www.sun.com/software/looking_glass/details.xml)

It's not exactly USEFUL as of now, but it might be later on...

---

### Post by atomkarinca on 2008-05-28
> **rishabh said:**
> If you're willing to deviate from the path of traditional DEs, take a look at Sun's idea of a Java-based 3D desktop environment:

[https://lg3d.dev.java.net/](https://lg3d.dev.java.net/)

And of course, screenshots ;)

[http://www.sun.com/software/looking_glass/details.xml](http://www.sun.com/software/looking_glass/details.xml)

It's not exactly USEFUL as of now, but it might be later on...

I had tried that a few weeks ago and the packages were broken. Have they fixed that?

---

### Post by rishabh on 2008-05-28
> **atomkarinca said:**
> I had tried that a few weeks ago and the packages were broken. Have they fixed that?

Did you try the MegaBundle, the .deb packages or their repositories? 
I'm downloading from the repos right now. I can check it after it installs and let you know in about an hour. :popcorn:

---

### Post by atomkarinca on 2008-05-28
> **rishabh said:**
> Did you try the MegaBundle, the .deb packages or their repositories? 
I'm downloading from the repos right now. I can check it after it installs and let you know in about an hour. :popcorn:

I had tried their repositories. It gave out an error while installing (I can't remember right now) and I'm pretty sure it was a broken package error.

---

### Post by rishabh on 2008-05-28
> **atomkarinca said:**
> I had tried their repositories. It gave out an error while installing (I can't remember right now) and I'm pretty sure it was a broken package error.

The problem is a broken "postinstall" script. It tries to run "/bin/arch", which is nonexistent from Gutsy onwards.

It has been discussed in great detail HERE:
[http://ubuntuforums.org/showthread.php?p=3706336](http://ubuntuforums.org/showthread.php?p=3706336)

UPDATE: I fixed it. (with the help of the above link)

Create a file in "/bin" called "arch" and add the text "uname -m" to it. Make the file executable. It should work.

---

### Post by atomkarinca on 2008-05-28
> **rishabh said:**
> The problem is a broken "postinstall" script. It tries to run "/bin/arch", which is nonexistent from Gutsy onwards.

It has been discussed in great detail HERE:
[http://ubuntuforums.org/showthread.php?p=3706336](http://ubuntuforums.org/showthread.php?p=3706336)

UPDATE: I fixed it. (with the help of the above link)

Create a file in "/bin" called "arch" and add the text "uname -m" to it. Make the file executable. It should work.

Thanks, I was able to get that work. It seems nice but it's very slow. Or it could be that Fluxbox has spoiled me :)

---

### Post by Seventh Reign on 2008-05-28
I'm partial to the standard Gnome, but have been checking out Enlightenment and Openbox lately.  

This is what I love most about *nix.    There are endless options for how you want your system to look and perform.  How many choices do you get with Windows? 3?  Pre-XP, XP, and Vista?  ... and the differences there are cosmetic.

---

### Post by Aesir09 on 2008-05-28
gnome is just the best hands down.

its so nice and simple.

i am currently removing kde 3.5.9 and kde 4 core. very anooying and cluttering.

but kde 3 is alot better than kde 4.


```
 use moar gnome!111
```

---

### Post by urukrama on 2008-05-28
> **Seventh Reign said:**
> How many choices do you get with Windows? 3?  Pre-XP, XP, and Vista?  ... and the differences there are cosmetic.

There are a number of shells you can install. I rather like Litestep. BBlean/BB4win is popular as well. They just aren't as well known as the various DE/WMs in Linux.

---

### Post by TheIdiotThatIsMe on 2008-06-01
> **atomkarinca said:**
> 
Other than that [LXDE]("http://lxde.sourceforge.net/") is worth trying I think. But to me Fluxbox rules.

I second LXDE, and they recently [added repos]("http://ubuntuforums.org/showthread.php?t=805334") so you can just add them and install, and get updates without much fuss. Pretty fast compared to Gnome, but have troubles with wireless under it (just need to find a good WiFi program, WiFi Radar doesn't work too well). PCManFM is a god send (although it's technically a seperate project, just included into LXDE). 

Also you can install EDE, either through their install script on their site or there are .debs around on the internet but they're not the most  (say only 7.10, but will install with no problem on 8.04). It's doesn't seem as polished though.

---

### Post by eriqjaffe on 2008-06-01
> **TheIdiotThatIsMe said:**
> just need to find a good WiFi program, WiFi Radar doesn't work too wellI would heartily recommend wicd - I use it on my antique laptop and it works quite well.  It's not in the repos, but they have a .deb package up [here]("https://sourceforge.net/project/showfiles.php?group_id=194573").

---

