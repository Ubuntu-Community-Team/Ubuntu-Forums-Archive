---
title: "LXDE Gaming? E17 Gaming?"
date: 2010-08-11
forum: Gaming &amp; Leisure
---

### Post by Nick_Jinn on 2010-08-11
How is gaming on LXDE, Lubuntu or Mint version? Does wine function alright?

I am also thinking about installing E17 to my flash drive of LDXE Mint. Are there any issues to worry about when installing them?


Is there a good way to add the repositories of other linux distros, like E-live or OZOS?



I am experimenting with creating a light weight distro with good 2D graphics and an easy to use interface and am wondering how well Wine supports 3D graphics in these light weight distros.

---

### Post by snowpine on 2010-08-11
Games are applications. LXDE, E17, Gnome, etc. are "desktop environments."

You can run any application in any desktop environment. A game that runs well in Gnome should run equally well in LXDE, and so on.

The only difference of course is that, on older hardware that struggles to run Gnome, switching to a lighter desktop environment will give you a performance boost across the board.

ps I do not recommend adding repositories from other distros. :(

---

### Post by Simian Man on 2010-08-11
The desktop environment you use makes no difference whatsoever on the applications you use on top of it, including wine.  Why would it?

---

### Post by Nick_Jinn on 2010-08-11
> **snowpine said:**
> Games are applications. LXDE, E17, Gnome, etc. are "desktop environments."

lol. Yeah, I knew that.

> **snowpine said:**
> You can run any application in any desktop environment. A game that runs  well in Gnome should run equally well in LXDE, and so on.



Are you sure that some applications are not desktop environment specific? I am no expert, but I think you might be mistaken in some instances.

I heard for example that WINE will install files, but people dont see wine in their menu....a minor annoyance, but what other problems might somebody run into in one environment vs another? Actually, its more than just the environment, its also that its an entirely different distro based on a different DE.

> **snowpine said:**
> Games are applications. LXDE, E17, Gnome, etc.  are "desktop environments."

You can run any application in any desktop environment. A game that runs  well in Gnome should run equally well in LXDE, and so on.

The only difference of course is that, on older hardware that struggles  to run Gnome, switching to a lighter desktop environment will give you a  performance boost across the board.

ps I do not recommend adding repositories from other distros. :(

Why not? Sometimes the work. In Mint anyway we can choose not to install specific update. It breaks it down nicer for us. I wont install updates from those repositories, at least not ones that affect my system.


But I would like to add the Elive repositories, which is debian based so should have a high degree of compatibility, and use some of their files to enhance an E17 desktop environment option added to Mint LXDE.



I wouldnt add Red Hat or Suse....I want to stay within the Debian family, but I would like to add some repositories. Does anyone here use Elive?

---

### Post by Nick_Jinn on 2010-08-11
> **Simian Man said:**
> The desktop environment you use makes no difference whatsoever on the applications you use on top of it, including wine.  Why would it?



So Compiz should work perfect in LXDE and the Enlightenment desktop effect manager should work flawlessly in Gnome?

Actually, compiz might work with LXDE, but I still thought that some apps were specific to certain distros.

---

### Post by snowpine on 2010-08-11
> **Nick_Jinn said:**
> So Compiz should work perfect in LXDE and the Enlightenment desktop effect manager should work flawlessly in Gnome?

Actually, compiz might work with LXDE, but I still thought that some apps were specific to certain distros.

Compiz and Enlightenment are not applications; they are windows managers. I think you are just being argumentative (not that there is anything wrong with a healthy debate). ;)

I have used Elive in the past. It is a nice distro based on Debian Stable. Debian is not 100% binary compatible with Ubuntu, so proceed at your own risk.

---

### Post by Nick_Jinn on 2010-08-11
So any single program that isnt a desktop manager should be able to work in any desktop environment as long as the kernel and stuff beneith the hood is the same? There are no exceptions?   I sort of thought that desktop managers were apps in their own rights, but I keep seeing apps that say they are for Gnome or for KDE....is that totally arbitrary? Dont you need to download part of the files for that desktop environment to use that app?   I mean, I click on Compiz bottons that say "Keep KDE compatibility" or "Keep Gnome Compatibility"? I guess thats the manager doing that, but I always thought that some apps require dependencies that are found in the DE packages.    I guess I am wrong?

---

### Post by sakuramboo on 2010-08-11
LXDE + Compiz

[http://www.youtube.com/watch?v=BeuDBJ6IY5M](http://www.youtube.com/watch?v=BeuDBJ6IY5M)

As long as you have the proper libraries installed, you can run any application. The package might not install the proper icons in the menu and such, but what's stopping you from making them yourself?

---

### Post by Simian Man on 2010-08-11
> **Nick_Jinn said:**
> So Compiz should work perfect in LXDE and the Enlightenment desktop effect manager should work flawlessly in Gnome?

Actually, compiz might work with LXDE, but I still thought that some apps were specific to certain distros.

Well compiz is a window manager, not an application.  You can replace the window manager LXDE uses (Openbox) with compiz.  I can't imagine why you'd want that though.  Enlightenment is not much more than a window manager IIRC so replacing it with Compiz would be even more pointless.  If this is a "light gaming" distro, where does compiz come into the picture?

And applications are practically never specific to certain distros or desktops.  The only examples I can think of are things like gnome-appearance-properties being specific to Gnome or Yast being specific to Suse.  Never games or anything.

---

### Post by snowpine on 2010-08-11
You're thinking about it too hard. :) Just install LXDE and Wine and see for yourself if it works. I'm surprised you haven't already, since you say you are creating your own lightweight distro...

---

### Post by Nick_Jinn on 2010-08-11
> **snowpine said:**
> You're thinking about it too hard. :) Just install LXDE and Wine and see for yourself if it works. I'm surprised you haven't already, since you say you are creating your own lightweight distro...

  OK, thanks. Glad to hear that it seems to work :)   But I did hear that there were at least bugs in LXDE with Wine, mostly regarding the programs not showing up in the application window....like the Wine app is there, but the apps from your C drive dont show up....Hopefully that problem has been resolved.

---

