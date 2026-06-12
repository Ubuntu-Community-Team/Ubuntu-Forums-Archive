---
title: "Is Ubuntu Studio a separate DE?"
date: 2008-09-09
forum: Desktop Environments
---

### Post by lewisskinner on 2008-09-09
Hi there.  I fairly new to Ubuntu and linux (I got Feisty just before Gutsy came out) and have mostly been playing around - mass installing KDE, Xfce mythbuntu etc.  Recently, I came across Ubuntu Studio, which is actually useful to me since I fancy myself as a bit of an amateur producer (emphasis on amateur!)

However, I can't seem to get it installed as a separate DE (you know, when you're at login and you click "select session) and choose KDE, KDE4, mythbuntu, GNOME etc)

Am I being daft, or is there something I'm missing?  It'd be very useful if I could do this, as my girlfriend just wants Ubuntu for surfing and playing music, and doesn't want the clutter of the Studio Desktop and all it's programs.

Oh by the way, I installed using ```
sudo apt-get ubuntustudio-desktop
``` in the terminal.

---

### Post by Anzan on 2008-09-09
I could be wrong as it's been a while since I tried it (and I now use Fluxbox) but your GNOME session is now Ubuntu Studio. It's not an actual DE but a version.

---

### Post by lewisskinner on 2008-09-09
well that doesn't seem to be the case at the moment.  My girlfriend and I both seem to have the basic GNOME DE.

---

### Post by lewisskinner on 2008-09-09
Anyone else got any ideas?  Studio definitely hasn't replace my GNOME DE.

---

### Post by lewisskinner on 2008-09-10
can anyone please help me?  Did I use the right command to install it, and why can I not log into Ubuntu Studio or even find the installed packages/applications that come with US?

---

### Post by leg on 2008-09-10
I am pretty sure it is not a seperate item you can boot to. I have parts of ubuntu-studio installed but I do not have the desktop installed and my desktop looks just the same as it did before I installed any studio elements. If you search through synaptic for ubuntu-studio you will find a few different meta packages such as graphics sound etc. You can install whichever ones of these you want. The first thing I would do if I were you would be to uninstall anything studio related and start again just picking the items you want and not selecting the desktop item.

If I read your post correctly you say you are an amatuer producer. If that refers to sound then you will need to install a different kernel to accommodate real time processing for sound. If you are referring to graphics or video then just select the option you want. That is what I did as I have no desire to install all the different sound programs and the new kernel required for it.

Good luck

---

### Post by snowpine on 2008-09-10
Hi there, you can install the Ubuntu Studio audio applications and the real time kernel with the following:

```
apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt
```

The applications should appear in your applications menu. There's no need for any special login session or anything. 

There are a few other packages (search for ubuntustudio in synaptic) if you want the video or graphic applications.

It doesn't matter what session you use; you can use the Studio apps from Gnome, KDE, Fluxbox, whatever. There are also some Gnome themes available if you want the look and feel--can't remember off the top of my head if it's ubuntustudio-desktop or ubuntustudio-artwork or whatever. You would choose these themes using the regular method. If you had installed Ubuntu Studio from scratch, it would be a pre-themed Gnome desktop. Personally I find the theme kind of ugly so I just run the apps. :)

Hope that helps!

ps Your girlfriend will see all of the apps in her applications menu as well; there's no way around this as far as I know.

---

### Post by lewisskinner on 2008-09-10
You're right, in so far as I do mostly sound.  I'm hoping to make some tracks and also make music videos for them, so I need both really (hence installing the whole Studio desktop seemed like the better option).  What new kernel do I need for sound and how do I get it?

Essentially what I wanted was a system where my girlfriend, or visitors to the house, can boot into a GDM and not have their menus cluttered by sound and movie manipulation programmes, meanwhile, a quick change session, and the studio set-up is waiting for me.  As an aside, I installed a lot of the audio packages and also the menu, but it hasn't appeared, so I don't know where to access them from.

Would I be better off downloading Ubuntu Studio as an ISO, installing it first and then adding the KDM or Xfce as the "default" desktop for other users?

---

### Post by snowpine on 2008-09-10
> **lewisskinner said:**
> You're right, in so far as I do mostly sound.  I'm hoping to make some tracks and also make music videos for them, so I need both really (hence installing the whole Studio desktop seemed like the better option).  What new kernel do I need for sound and how do I get it?

Essentially what I wanted was a system where my girlfriend, or visitors to the house, can boot into a GDM and not have their menus cluttered by sound and movie manipulation programmes, meanwhile, a quick change session, and the studio set-up is waiting for me.  As an aside, I installed a lot of the audio packages and also the menu, but it hasn't appeared, so I don't know where to access them from.

Would I be better off downloading Ubuntu Studio as an ISO, installing it first and then adding the KDM or Xfce as the "default" desktop for other users?

Hi Lewis, I'm afraid (and I could be wrong, maybe there is something I'm overlooking) the best solution for you would be to install Ubuntu Studio onto a separate partition. It doesn't matter if your GF boots into KDE or Xfce; the applications will be there. 

I think part of your confusion is that, unlike, say ubuntu-desktop, ubuntustudio-desktop does NOT install all of the applications. You need to install ubuntustudio-audio, ubuntustudio-video, etc. separately.

The real-time kernel (which is optimized for low-latency audio) is 'linux-rt' like I mentioned in my previous post.

Ubuntu Studio is simply the sum of:
1. Ubuntu
2. Lots of cool applications
3. The real time kernel (linux-rt)
4. The Ubuntu Studio theme and artwork

Hope that helps you out!

ps this link might help you get a handle on what's in each of the metapackages: [http://packages.ubuntu.com/hardy/ubuntustudio-desktop](http://packages.ubuntu.com/hardy/ubuntustudio-desktop)

---

### Post by skullmunky on 2008-09-11
KDE (Kubuntu) and Gnome (regular ubuntu) and XFCE (Xubuntu) are different complete desktop session managers.  Ubuntu Studio is a collection of applications and the realtime kernel.   The apps you can use from any desktop - KDE, Gnome, XFCE, whatever.  The session chooser at login only lets you choose which window manager you want.

I think there are some other easy ways to get the result you want.

One way is just to edit the application menu, and put all the audio related apps into an "Audio Editing" submenu, so they're out of the way.  They're probably not all grouped together nicely at the moment, hence what you describe as "cluttering" the menu.

Or, another thing you could do is make one or two other user accounts; one for GF, one for guests, etc.  You can just remove items from their application menus, so they're tidier.

---

### Post by ad_267 on 2008-09-11
Ubuntu Studio uses GNOME. ubuntustudio-desktop just installs new wallpapers, GDM, gtk and metacity themes. You can apply them from System - Preferences - Appearance.

---

### Post by lewisskinner on 2008-09-12
Thanks for all the help guys!  Looks like there's no way around my problem save for a dual-boot Ubuntu/Ubuntu-studio, so I'll have to leave it be (or buy a new PC!)

By the way, does the low-latency kernel have any ill effects on other applications?  Seems odd that it'd not be shipped with regular Ubuntu if not.

Also, why when I boot up do I get options of linux regular and linux-rt?  Do these actually exist, or has my kernel been effectively upgraded and replaced by the low-latency version?

---

### Post by ad_267 on 2008-09-13
I think the low latency kernel isn't as good at running many different cpu intensive tasks at once.

You now have both the realtime (rt) kernel and the regular one so you can boot into whichever one you want. You can remove the regular one using Synaptic if you want.

---

