---
title: "newbie question: synaptic package manager"
date: 2008-10-19
forum: Desktop Environments
---

### Post by zachbb on 2008-10-19
Hi

I'm new so please be nice!

I noticed that Open Office 3 is out. So to insall this, I tried both "Add/Remove Programs" and the "Synaptic Package Mangaer", but all of them still only offer version 2.4 of Open Office.

Why is this and in how much time will it allow Open Office 3?

Thanks

---

### Post by redbrain on 2008-10-19
Yeah this can be confusing to new users on how package managers work, but you'll soon learn to love them to pieces! :)

Synaptic/ad-remove
use: apt-get (the cmd line tool for installing programs automaticly)

This rely's on a 'sources' file which has links to repositorys or packages. These repositorys haven't been updated to include and update for open-office but with the new version of ubuntu 11 days away, you'll find your update manager will give you the choice to do distro upgrade and this will update these repository links for the newer packages and should include the new open-office. 

You could however if you wanted package open-office 3 or compile + run it your self but this is a little more complicated :). But it could be a valuable learning experience. 

If you really want it now someone is bound to know a link to a .deb of it or somthing.

---

### Post by zachbb on 2008-10-19
Thank you so much for helping me understand this.

Are the repositories only updated on each OS release? or can they be updated independetly?

I will definetely try to compile it myself!

Thanks!

---

### Post by cl0ckwork on 2008-10-19
the repositories are updated however often you tell them to, but the packages might not be up to date with current software releases.

this is usually because the current software is not fully stable and the software in the repositories are trusted to work better.

compiling may get a little confusing but a little terminal work and you should be on your way, easiest thing to do is to add a seperate repository for that software of get a .deb file for it

---

