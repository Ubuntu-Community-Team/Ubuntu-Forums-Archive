---
title: "Ancient laptop - should I use Netbook Remix"
date: 2009-05-01
forum: General Help
---

### Post by lemmyc on 2009-05-01
Hi,
I'm looking to use an old (10 yr old?) Sony Vaio laptop to run as a music player in my kitchen.
Screen res is only 800x600 - CPU is an old celeron.

I'm wondering if Netbook Remix is a good way to go for fast boot times and making the most of the limited screen space. Or would I get better results with the old celeron processor using Xubuntu or Kubuntu (can't remember which of these is more lightweight)?

Another factor - I want to run Spotify, which I believe will require Wine.

Also, if installing UNR, I think I will need to burn a CD, as I'm sure booting from flash drive won't be supported. Does a UNR .iso exist anywhere?

Thanks for any advice. (Please don't tell me to throw it in the bin - I'm aware of that option!)

---

### Post by Brandon Williams on 2009-05-01
I would go with Xubuntu. It's lighter weight than either Gnome (UNR is basically Gnome) or KDE. In fact, if it were me, I probably wouldn't even run XFCE, but instead would go for something _very_ light weight, like fluxbox or FVWM.

---

### Post by 3rdalbum on 2009-05-01
Netbook Remix is still "full-fat" Ubuntu with a custom interface, so no - you'd be better served by Xubuntu, assuming you've got that machine chock-full of RAM.

---

### Post by cmnorton on 2009-05-01
In a word, No (don't do it). I had a four year old Acer and that installed 6.10, and its predecessors well until 8.04, which just would not install. Laptops are tricky. Suggest finding an ultra-small Linux distro.

---

### Post by jespdj on 2009-05-01
Ubuntu Netbook Remix is more or less the same as the regular Ubuntu with some extra packages. I don't think it's much lighter than regular Ubuntu. It does have some nice optimizations that make it run better on screens with lower resolutions. See, for example: [Ubuntu Netbook Remix 9.04 hands-on](http://www.tuxradar.com/content/ubuntu-netbook-remix-904-hands).

Xubuntu is the lighter-weight version of Ubuntu.

How much memory does that old laptop have? Does it have more than the minimum amount necessary for Ubuntu? See [Ubuntu System Requirements](https://help.ubuntu.com/community/Installation/SystemRequirements).

If it has not enough memory, then there are a number of other Linux distributions that are especially made for older and slower systems that you might want to look at.

---

### Post by chriskin on 2009-05-01
> **lemmyc said:**
> Hi,
I'm looking to use an old (10 yr old?) Sony Vaio laptop to run as a music player in my kitchen.
Screen res is only 800x600 - CPU is an old celeron.

I'm wondering if Netbook Remix is a good way to go for fast boot times and making the most of the limited screen space. Or would I get better results with the old celeron processor using Xubuntu or Kubuntu (can't remember which of these is more lightweight)?

Another factor - I want to run Spotify, which I believe will require Wine.

Also, if installing UNR, I think I will need to burn a CD, as I'm sure booting from flash drive won't be supported. Does a UNR .iso exist anywhere?

Thanks for any advice. (Please don't tell me to throw it in the bin - I'm aware of that option!)


even though i am tempted to say that i will not do much work outside the bin , it would be rather interesting to try xubuntu and tell us how it performs. it will be a major accomplishment for the devs if you can run modern apps on this laptop :) 
or an lxde-based distro, even thought i'm not sure if xfce or lxde is lighter


**[COLOR=Black]edit :[/COLOR] **i dived into the internets and got what i thought , lxde is lighter than xfce, while keeping the desktop as nice as possible

---

### Post by lemmyc on 2009-05-01
Thanks, looks like xubuntu is winning the vote...

---

### Post by lemmyc on 2009-05-01
> **jespdj said:**
> Ubuntu Netbook Remix is more or less the same as the regular Ubuntu with some extra packages. I don't think it's much lighter than regular Ubuntu. It does have some nice optimizations that make it run better on screens with lower resolutions. See, for example: [Ubuntu Netbook Remix 9.04 hands-on](http://www.tuxradar.com/content/ubuntu-netbook-remix-904-hands).

Xubuntu is the lighter-weight version of Ubuntu.

How much memory does that old laptop have? Does it have more than the minimum amount necessary for Ubuntu? See [Ubuntu System Requirements](https://help.ubuntu.com/community/Installation/SystemRequirements).

If it has not enough memory, then there are a number of other Linux distributions that are especially made for older and slower systems that you might want to look at.

Just looked at the hardware specs - Celeron at 463Mhz and 64MB of RAM. Which explains why the hard drive is constantly thrashing with the Win XP OS which was recently installed on it... 
So it squeezes into the bare minimum requirements.

---

### Post by lemmyc on 2009-05-01
> **chriskin said:**
> 
**[COLOR=Black]edit :[/COLOR] **i dived into the internets and got what i thought , lxde is lighter than xfce, while keeping the desktop as nice as possible

Thanks, will take a look.

---

### Post by thegreenblob on 2009-05-01
You might also want to check out [Crunchbang]("http://crunchbanglinux.org/"), it's based off of Ubuntu but runs openbox which is lighter than gnome/kde/xfce. Though may not be as user friendly. (Like when you install something you have to make the menu entry your self), but if you don't like that idea Xubuntu would be my next choice.

---

### Post by roger_1960 on 2009-05-01
Hi

If Xubuntu is a bit slow (64Mb is not much) perhaps try Puppylinux 4.2.  It boots from a live disk and runs in RAM so you can try it first.  Its normally very easy to install and very fast.  I use it for recovering old laptops but would be happy to run it full time on an old machine.

---

### Post by snowpine on 2009-05-01
> **lemmyc said:**
> Just looked at the hardware specs - Celeron at 463Mhz and 64MB of RAM. Which explains why the hard drive is constantly thrashing with the Win XP OS which was recently installed on it... 
So it squeezes into the bare minimum requirements.

You need more ram if possible (I recommend 256mb minimum), then maybe you could try Puppy or SliTaz. The only distro I have used that runs well with 64mb of ram is DSL (Damn Small Linux). Your computer is much too underpowered for anything based on Ubuntu (including Netbook Remix, Xubuntu, Crunchbang, etc.)

---

### Post by lemmyc on 2009-05-01
Thanks for the helpful advice all. You have saved me much wasted time.

---

### Post by nucleuskore on 2009-05-01
Xubuntu 8.04

---

### Post by lavinog on 2009-05-01
I have heard that Xubuntu has become just as bloated as Ubuntu.

You can still run Ubuntu on really old machines. You have to do alot of tweaking, remove components that you don't need.
Since this is going to be a specialized system, you should remove things like bluetooth, openoffice. If you don't plan to do any printing remove cups.

If you want to get really specialized, install the server edition, then install only what you need.

Edit: I just found out that I can remove the bulk of evolution from Ubuntu now.

---

### Post by nucleuskore on 2009-05-01
That's why I said 8.04 :)

---

