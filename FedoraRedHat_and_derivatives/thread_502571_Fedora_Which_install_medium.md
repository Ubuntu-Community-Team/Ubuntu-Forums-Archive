---
title: "Fedora: Which install medium?"
date: 2007-07-16
forum: Fedora/RedHat and derivatives
---

### Post by ThinkBuntu on 2007-07-16
How will my desktop experience be affected by my choice of the LiveCD or the DVD to install Fedora 7? I'm going to use the default GNOME desktop. Is the only difference a matter of which packages are available for install? Or will I be missing certain things in my install by just using the CD?

I also noticed that the LiveCD is labled as 686, while the DVD is 386. Does this have anything to do with how the distro's optimized/compiled?

---

### Post by Adam_GUI on 2007-07-16
According to my Fedora Core 5 book, it shouldn't matter whither it's i386 or i686, as it won't install on an i386 machine.

If you have an older machine, go with the i386 install DVD. (Because it'll install on i486 and up.)  If you're sure you have an i686 machine--go ahead with the live cd.  You can always use YUM or PUP to update/add packages.
And FreshMEAT to find *.rpms.
And packages that break themselves.
And Dependency Hell.

:wink:

All kidding aside though, enjoy Fedora Core 7.  My class had to use 5 while 7 was being beta-tested.  And having to hunt-down RPMs was never fun--and the results were always undesirable. I hope that's fixed a bit by now.
That, or I really missed out on something essential.

---

### Post by igknighted on 2007-07-17
The liveCD is just like Ubuntu's, it dumps everything onto the HD.  You get just the DE on the disk and the package selection included (I am 90% sure OpenOffice is not included on the gnome disk... but IIRC you are an abiword guy anyway).  Otherwise it makes no difference.  If you really want to customize the package selection then go with the DVD, otherwise the liveCD should do fine.

PS: While the liveCD does not boot up with the pretty splash screen, it is installed and works on first boot.

> According to my Fedora Core 5 book, it shouldn't matter whither it's i386 or i686, as it won't install on an i386 machine.

If you have an older machine, go with the i386 install DVD. (Because it'll install on i486 and up.) If you're sure you have an i686 machine--go ahead with the live cd. You can always use YUM or PUP to update/add packages.
And FreshMEAT to find *.rpms.
And packages that break themselves.
And Dependency Hell.



All kidding aside though, enjoy Fedora Core 7. My class had to use 5 while 7 was being beta-tested. And having to hunt-down RPMs was never fun--and the results were always undesirable. I hope that's fixed a bit by now.
That, or I really missed out on something essential.

You missed something essential.  Fedora is really no different than Ubuntu (we add medibuntu to get codec and enable universe/multiverse, in Fedora you add the Livna repo and you are good to go).  You can get more complicated with the repo's... but you would only want to do that to tweak your system in some specific way, and you should research whether the repos you want to use together conflict.

---

### Post by ThinkBuntu on 2007-07-17
So far I'm enjoying my system with Fedora. Looks great, functions smoothly. Desktop effects are great compared to the choppy performance I get in Ubuntu, and having SELinux installed and configured is certainly assuring. If I can get this running well, I'm hoping to use it for a while. Seems to have the robustness and quality of openSuSE with less bloat in general.

The LiveCD uses SquashFS, and seems to get the job done well. What's interesting is that I loaded the disc to RAM (1.5GB RAM in my ThinkPad) and GIMP still didn't start instantly...It seems to me that GIMP can only start so fast, and that I've actually achieved its top start speeds in Zenwalk, Arch, and maybe Debian.

---

### Post by ThinkBuntu on 2007-07-17
There are many ways distros can earn "brownie points" from me. One is to include GVim by default, and another is to have GNOME office instead of OpenOffice included. Fedora earns an extra point for packaging Audacious with a default "Bluecurve" theme, which is just awesome. So far, although there have been some tiny bumps, a great experience!

---

### Post by MethodOne on 2007-07-17
There is just one minor flaw in the live CDs:  they don't come with wget.  I can easily fix that by running yum install wget.

---

### Post by ThinkBuntu on 2007-07-18
> **MethodOne said:**
> There is just one minor flaw in the live CDs:  they don't come with wget.  I can easily fix that by running yum install wget.
I noticed that, and was a bit surprised.

---

### Post by igknighted on 2007-07-18
One thing I love is they distribute the ability to create a custom live iso, then provide a website for people to share "Fedora Respins".  I think that is an awesome idea, I hope it catches on.  If I figure out how to get my sound working on Fedora 7 then I'll definitely respin it so others can use it too (damn those hda-intel sound cards...)

---

### Post by ThinkBuntu on 2007-07-18
> **igknighted said:**
> One thing I love is they distribute the ability to create a custom live iso, then provide a website for people to share "Fedora Respins".  I think that is an awesome idea, I hope it catches on.  If I figure out how to get my sound working on Fedora 7 then I'll definitely respin it so others can use it too (damn those hda-intel sound cards...)
I'm pretty certain that PCLinuxOS has a similar feature that allows you to essentially take a Live-CD (or installable CD) snapshot of your current system. I've never used it, but I think it just generates an ISO with a single command. I'd also guess that this feature is in Mandriva, but you never know.

---

### Post by ThinkBuntu on 2007-07-18
Quick question: What convinced or drove you to switch from Fedora to openSuSE? Both are very enticing, and have jumped out in the lead for my long-term distro.

---

### Post by igknighted on 2007-07-18
> **ThinkBuntu said:**
> I'm pretty certain that PCLinuxOS has a similar feature that allows you to essentially take a Live-CD (or installable CD) snapshot of your current system. I've never used it, but I think it just generates an ISO with a single command. I'd also guess that this feature is in Mandriva, but you never know.

Yeah, I think Ubuntu even has this (i forget what it is called), but Fedora has advertised it to users which I think is important.  If users realize how easy it is to create custom spins and distribute them then I think it would do wonders for promoting linux, because for almost no work we can create custom versions suited for a particular user.

---

### Post by igknighted on 2007-07-18
> **ThinkBuntu said:**
> Quick question: What convinced or drove you to switch from Fedora to openSuSE? Both are very enticing, and have jumped out in the lead for my long-term distro.

The ease of setting up dual monitors, my extra annoying sound was not supported in Fedora 7 (I gave my Creative card away that was universally supported and now I am using the HDA from the mobo... better sound card, less supported).  I got really annoyed though by the awkward package management in Suse so I am searching again.  I am currently on CentOS to get back to the Fedora feel, but it lacks desktop packages so I might go back to Fedora 6 (sound works in these... go figure) until Fedora 8 comes out.  Go figure.

PS, if you get a chance I left another question on CSS forums.

EDIT: Plus I am more of a KDE guy than a Gnome guy, and I find Fedora's KDE to be kinda weird.  I actually am using Gnome on my new CentOS install, but will add KDE apps in places (Amarok and K3B).

---

### Post by ThinkBuntu on 2007-07-18
I prefer GTK apps and the KDE environment which puts me in a tough position. I'm slowly migrating towards Xfce, but it's damn hard to configure, and Zenwalk's the only great version I've seen that really is true to my vision of Xfce. SAM is awesome, but it feels subtly like KDE in Xfce clothes.

Some things with Fedora are bothering me: One is that I can't browse packages when disconnected from the internet (using Add/Remove). F-Spot can't be installed due to a mono-related dependency, which leaves me with few "natural" outs for that app. Boot time is deceptively slow: By switching between screens, it seems fast, but in reality clocks in at the typical openSUSE 50-60 seconds. On the other hand, operation is very smooth, and the GNOME is very well-customized. Tough call so far.

Also, this is random, but you should check out Vector. I was positively floored by how desktop-ready this distro is, compared to the minimal fanfare it receives. Installation is a little tough, but anyone can do it.

---

### Post by igknighted on 2007-07-20
Since this thread has kind of drifted, I thought I would update and say that CentOS did not win out for the desktop.  I'm gonna give pardus a run for a bit.  CentOS just isn't focused on the home desktop (not a criticism, its an awesome distro for the enterprise desktop or server... in fact I run two CentOS servers and love them).  I am really impressed by pardus, the biggest issue I have had is that the login screen is written in Turkish (and its easy to change that theme).

---

### Post by ThinkBuntu on 2007-07-20
Pardus is a great distro, although I'm looking for something lighter. I also had a great experience with Vector, but it felt a little rusty. That being said, apart from oversized fonts in GTK apps, I was able to get done everything I needed to before ever connecting to the internet, including all codecs and wireless. Not to mention that the KDE is the smoothest I've used to date. Right now, the god-awful Sabayon Business Edition (which I'm reviewing for a blog, not mine) is on my system and I can't wait to get it off. The only strong points, besides its Gentoo roots (which some love), are font rendering and the inclusion of all proprietary software (drivers, codecs, etc).

Next I'm going with pure Slackware, which I'm hoping works out well. If not, I'll be giving Vector a good look as well as Zenwalk. If none of these work out, I can see myself sticking with Debian or PCLinuxOS. To date, except for Ubuntu which I ran for about two months in my first Linux experience (on a MacBook no less), I have yet to use a distro for 30 days straight, although I've probably used Mint and Zenwalk for a little over a month in different spurts.

I figure if a distro is good and solid enough to stay on my laptop for over 30 days (the standard software trial period) I'll gladly donate to the project and stick with it. Right now, I'm still in trial stage.

---

### Post by igknighted on 2007-07-24
> **MethodOne said:**
> There is just one minor flaw in the live CDs:  they don't come with wget.  I can easily fix that by running yum install wget.

Haha, this one just got me.  I reinstalled Fedora because they have a 2.6.22 kernel out now (fixes the sound issues I had) and remembered this thread when I tried to wget something.  The other thing that Fedora annoys me by not including is gconf-editor.  Fedora's gnome needs some tweaking (nautilus especially) before I can use it, so gconf-editor is always the first thing I need.  Overall though, I would rather them leave a few things out that are easy to install via yum then add all sorts of crap that I don't need.

---

