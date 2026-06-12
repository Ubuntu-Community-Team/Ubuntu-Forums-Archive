---
title: "Install Gnome DM with Xubuntu Question"
date: 2011-10-24
forum: Desktop Environments
---

### Post by mikodo on 2011-10-24
Hello,

I was using Xubuntu and Ubuntu 10.04, switching between the two, in logins. I broke Xfce, when trying different configs and removed Xubuntu. I now, only use Ubuntu 10.04. I am going to stay with that, untill after 12.04 comes out, when I want to use Xubuntu exclusively. Unfortunately, I have at least one application, that for linux, works only in Gnome. So, what would be the best way to do that? All I can think of is, fresh installing both Xubuntu and Ubuntu 12.04 and using Xubuntu like I did before. I wonder though, if there a way to run Gnome with Xubuntu, that allows for a more purer and responsive Xfce experience, than doing it this way?

I guess, I am asking for alternatives to think about.

I have a newer computer, with 4gigs of ram, a quad-core processor and enough disk space to run both; So, that is not a concern. 

Thank you.

---

### Post by crdlb on 2011-10-24
What is the app that only works in GNOME?

In any case, I don't understand what you're concerned about. You can install gnome on xubuntu and xfce on ubuntu with no ill effects, unless you count having extra applications in the menus. It's not like both desktops will run simultaneously.

---

### Post by gsmanners on 2011-10-24
What's important in Xfce is not so much the desktop as it is the apps. If we knew what apps you needed, then it would be a lot easier to help. :D

Lately, it seems like Gnome isn't really trying to integrate well with anything other than Gnome itself. It's kind of irritating, but it's nothing that you can't work around. Breakage happens, and that's why I make backups and reinstall every now and then.

And yeah, fresh install is a very good idea, especially with all the Unity/Gnome Shell development going on. Those projects are stirring up quite a lot of activity in many other Gnome projects.

---

### Post by 3Miro on 2011-10-24
I am unaware of any app that runs under Gnome and not under Xfce (I use Xfce on several machines). There are some Gnome tools that can conflict with Xfce (like Nautilus, but it can be hacked).

Are you using Devilspire? This is a Metacity only thing I doubt it will ever be available for Gnome 3 (which means it will not be available for 12.04 anyway).

---

### Post by mikodo on 2011-10-24
> **crdlb said:**
> What is the app that only works in GNOME?

In any case, I don't understand what you're concerned about. You can install gnome on xubuntu and xfce on ubuntu with no ill effects, unless you count having extra applications in the menus. It's not like both desktops will run simultaneously.
It is a bible front-end application for the Crosswire/Sword project called Xiphos.

---

### Post by gsmanners on 2011-10-24
Xiphos and many of its modules are in the repos, so you just install them the normal way. I don't see anything out of the ordinary in it, either.

---

### Post by 3Miro on 2011-10-24
> **mikodo said:**
> It is a bible front-end application for the Crosswire/Sword project called Xiphos.

It doesn't look like anything special, why wouldn't it run under XFCE?

---

### Post by mikodo on 2011-10-24
Well I read this from a while ago: [http://sourceforge.net/tracker/?func=detail&aid=3005789&group_id=5528&atid=355528](http://sourceforge.net/tracker/?func=detail&aid=3005789&group_id=5528&atid=355528)

From what I understand, I need to bring in lots of gnome dependencies to run this in Xfce.

Could I still do that, without installing a full-fledged Gnome3/Unity desktop?

---

### Post by 3Miro on 2011-10-24
> **mikodo said:**
> Well I read this from a while ago: [http://sourceforge.net/tracker/?func=detail&aid=3005789&group_id=5528&atid=355528](http://sourceforge.net/tracker/?func=detail&aid=3005789&group_id=5528&atid=355528)

From what I understand, I need to bring in lots of gnome dependencies to run this in Xfce.

Could I still do that, without installing a full-fledged Gnome3/Unity desktop?

There is a difference between installing dependencies, installing the whole DE and requiring the DE. Many applications use Gnome libraries, but those run just fine under XFCE. You will see slightly higher memory usage (since you have to load those libraries) and you will need to install the dependencies (automatically from the Software Center), but you don't need to have the entire DE and you certainly don't need to run it. 

You can install Xubuntu and then add Xiphos from the Software Center and then it should just run.

---

### Post by mikodo on 2011-10-24
> **3Miro said:**
> There is a difference between installing dependencies, installing the whole DE and requiring the DE. Many applications use Gnome libraries, but those run just fine under XFCE. You will see slightly higher memory usage (since you have to load those libraries) and you will need to install the dependencies (automatically from the Software Center), but you don't need to have the entire DE and you certainly don't need to run it. 

You can install Xubuntu and then add Xiphos from the Software Center and then it should just run.
Thankyou! I didn't know that until now. This is great, as I can install Xubuntu alone, to use.

:)

---

### Post by gsmanners on 2011-10-24
Yeah, in fact Xubuntu is already Xfce + lots of Gnome stuff. What you want probably wouldn't add that much.

---

