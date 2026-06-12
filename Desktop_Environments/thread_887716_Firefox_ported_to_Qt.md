---
title: "Firefox ported to Qt"
date: 2008-08-12
forum: Desktop Environments
---

### Post by krazyd on 2008-08-12
Just a heads up for all those sick of the sub-par firefox love that us KDE-ers have been getting thus far: [http://dot.kde.org/1218543988/](http://dot.kde.org/1218543988/)

Can't wait! Looks like it'll be ready for Intrepid!
:popcorn:

---

### Post by pluviosity on 2008-08-12
Dude, about time KDE gets some Firefox love, especially since Windows and Mac got better visual integration.  And the article says it only took 5 days to port it?!  Makes me wonder why it wasn't done sooner.

I'm really looking forward to this :popcorn:

---

### Post by ggaaron on 2008-08-12
I'm just curious. Why do you need to use Qt with KDE and GTK with GNOME and using GTK with KDE is so bad? They are just different widget toolkits... I'm using KDE with firefox and other GTK applications, based on what they can do, not what technologies were used to write them, but I see many people with different approach, so I'd like to ask what is the difference in using Gtk or Qt applications?

---

### Post by pluviosity on 2008-08-13
> **ggaaron said:**
> I'm just curious. Why do you need to use Qt with KDE and GTK with GNOME and using GTK with KDE is so bad? They are just different widget toolkits... I'm using KDE with firefox and other GTK applications, based on what they can do, not what technologies were used to write them, but I see many people with different approach, so I'd like to ask what is the difference in using Gtk or Qt applications?

Using Firefox that integrates with Gnome better than with KDE is highly annoying.  There are a couple of things that come to mind.  

-If I wanted to make a picture in Firefox my desktop background in KDE, it's not going to work.  

-The Open and Save dialogs are the Gnome ones, not KDE's, which annoys me because I personally feel that KDE's is more useful, but that is my opinion (I actually use Firefox's default dialog, but that's another story).  

-Firefox uses GTK theming, and while you *can* try and force GTK apps to use KDE looks, I find that, at least with the themes I use in KDE, it is often very buggy and not worth it.  The scrollbar, fonts, widgets, and icons are different, and while I can change some of them with Firefox themes, it still feels foreign to my desktop, not to mention that default FF looks HIDEOUS on KDE.

-Integration with other apps can be annoying.  Often times, it will open documents in the default Gnome apps (I have Gnome installed for a few reasons but am almost always in KDE).  While you can change most of the default apps, some workarounds are not easy (I still can't get FF to send RSS feeds to Akregator).  

Most of the irritation is cosmetic, I'll admit that.  But when everything else on my desktop that I regularly use has a standard look and FF doesn't fit in, it just doesn't feel right.  Qt integration would improve this by leaps and bounds.  I can't say for sure whether or not the Qt integration would necessarily improve on the rest of my points because I'm no expert, but it certainly won't hurt.

---

### Post by p_quarles on 2008-08-14
> **pluviosity said:**
> Using Firefox that integrates with Gnome better than with KDE is highly annoying.  There are a couple of things that come to mind.
Firefox doesn't really integrate with anything -- not Windows, Aqua, Gtk or QT. It uses its own XUL portable toolkit, which is one of the main complaints brought by fans of others browsers. 

It's also worth noting that another major browser (Opera) already uses Qt, but doesn't integrate with KDE at all, because it's compiled with a static Qt library. Your KDE appearance and dialogue settings won't be inherited by Opera at all. 

The only browsers that truly integrate into their environment are Explorer, Epiphany and Konqueror (EDIT: and the Mac version of Safari, of course). With the rest, you're getting a toolkit that is largely specific to the browser and will neither inherit nor affect any other settings.

---

### Post by ibutho on 2008-08-14
> **pluviosity said:**
> Dude, about time KDE gets some Firefox love, especially since Windows and Mac got better visual integration.  And the article says it only took 5 days to port it?!  Makes me wonder why it wasn't done sooner.

I'm really looking forward to this :popcorn:
There was a project that did the same thing a few years ago and released a few qt firefox development builds, but no production release.

---

### Post by ggaaron on 2008-08-14
With KDE4 making GTK applications look good is really easy. Yes, it looks different, but it is not the only GTK app I use, so it does not annoy me. As for integration with desktop - it won't integrate with KDE, the open/save dialog you mention will still be different, because it will be the Qt one, not the KDE one. And as for default applications, I haven't noticed it does use GNOME applications by default, fresh install always asked me what to use first time I opened files. So to sum up I don't know if it is worth it - maintaining Firefox in Qt will need developers attention, but NOKIA is making this port to use on their phones and there it can be important if you use only Qt or have to port GTK.

---

### Post by pluviosity on 2008-08-14
> **p_quarles said:**
> Firefox doesn't really integrate with anything.
...
It's also worth noting that another major browser (Opera) already uses Qt, but doesn't integrate with KDE at all, because it's compiled with a static Qt library. Your KDE appearance and dialogue settings won't be inherited by Opera at all.


OK, so maybe integrate was the wrong word for what I wanted to convey.  But the point is that Firefox plays a lot more nicely with Gnome than KDE, and it would be nice to have it leveled off, no matter how unlikely it may be.

As for Opera, there is a build of it that will take on some of the Qt settings being used by KDE.  I tried it to see if it works, and it does.  But to be honest, I'm not really a fan of Opera, mostly because it lacks some functionality I can get in a few specific FF extensions.

---

