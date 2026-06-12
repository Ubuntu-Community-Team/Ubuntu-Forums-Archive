---
title: "Synaptic and various questions"
date: 2006-09-24
forum: Desktop Environments
---

### Post by PCSpectra.com on 2006-09-24
Again, I'm loving the Ubuntu experience, but...

I have spent the better part of 2-3 days reading about package managers, and have a good idea as to how Debian packages are like RPM. I also understand t hat Ubuntu by default has the Application installer/remover like Windows which is basically a layer ontop of Synaptic, which itself is a layer on apt-get.

For Now I just prefer working with Synaptic as GUI prevents me from typing long winded URL's, etc...

I think I understand how apt-get differes from RPM in the sense apt-get packages are stored online (or other repos) and the mirrors for your locale are stored in /etc/whatever that file is called.list :P

Prevents you from entering URL's and instead just specify package names which are then downloaded remotely.

Anyways the GUI also prevent me from having to find the repos, etc....

So...I've been tinkering with Synaptic and I have browsed all installed packages...some seem to be almost duplicated... :| 

One which bugs me the most however is the accessibility packages.

I also stumbled onto this one: Standalone shell setup for initramfs

When I mark for removal or complete removal, I get a wanring telling me alot of other dependancies are going to also be uninstalled...

gnome-session, gnome-power-manager, etc...

Obviously I want to keep those and just get rid of things I know I won't need...

Here is another example: I just tried to remove **anacron** and one of it's dependancies is **ubuntu-desktop**

Obviously, I really don't want to remove that...

So am I stuck with all these dependancies? Can I not remove them but keep others I want like ubuntu-desktop

p.s-I am trying to compile gedit from source and I've managed to figure out most problems, but now have reached a point where it says the GTK+, GLIB libraries are outdated, but I used Synaptic to download the latest (i think) so do I have to somehow manually update those files???

Cheers :)

---

### Post by Sarisar on 2006-09-25
OK first up I'm not an expert!

However my understanding is that each package lists dependencies, so if UbuntuDesktop says it needs anachron (even if it doesn't) then synaptic and apt-get etc will try to remove UbuntuDesktop when you try to remove anachron.

I don't think there is a way around it, but most of them should be fairly accurate in dependencies (although I have found ones that don't seem to make sense to me)

---

