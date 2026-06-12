---
title: "Metacity application switcher with compiz"
date: 2010-08-19
forum: Desktop Environments
---

### Post by dmelliot on 2010-08-19
Hi,

Is there a way to restore only the application switcher from metacity when using compiz?

I generally like compiz on, but there is not an application switcher within compiz that provides the usability of the standard metacity switcher.

They are fine when you have only a few windows open, but if you are running many apps (some of them with multiple windows) it becomes quite hard to identify the app you want.

This was discussed in [this archived forum]("http://ubuntuforums.org/showthread.php?t=587201"), but I have not been able to find a solution anywhere.

Any help appreciated...

---

### Post by earthpigg on 2010-08-19
hi,

i don't have an exact solution to your question.

however, i have found that using "static application switcher" in compiz is very similar to metacity's alt-tab behavior.

---

### Post by dmelliot on 2010-08-19
Thanks for the reply earthpig.

I do currently use the compiz static switcher, but still find it quite difficult to quickly identify the window I want.  

I think if there were options to only show icons (i.e. no window preview) and control the size of the icons (and title text) then most of my issues would be resolved..... ;-)

---

### Post by Ginsu543 on 2010-08-19
I have no clue how to get Compiz to do what you want, but may I suggest two alternatives to give you the functionality you're looking for?

First, have you tried using the "Show Windows" function in Compiz? You can assign one of the corners of your screen as a hotspot that will tile all currently open windows and you can select the one you want by simply clicking on it. The easiest way to do this is to download and install [_Ubuntu Tweak_]("http://ubuntu-tweak.com/"), go to Compiz Settings under Desktop, assign one of the corners as "Show Windows." Now, all you have to do is move your mouse pointer to the hotspot corner and voila! Take a look at the first picture I've uploaded.

Second, have you checked out Tint2? If you look at the second picture I've uploaded, you can see Tint2 along the bottom of the screen. You simply click on the application/window that is open to access it. Tint2 works great with Compiz. It is HIGHLY customizable, so you can make it look like pretty much whatever you want.

---

### Post by dmelliot on 2010-08-29
Hi Ginsu543,

Thanks for the reply and suggestions.
Unfortunately neither of those would resolve my concerns (although I will give tint2 a shot to see how customisable it is).

I really just want something similar to the standard metacity switcher.  Just having the icons visible and the text available to distinguish between multiple windows of the same app seems to work best for me.  Using the compiz static switcher I get no use from the window previews, most of my windows look the same and the icons are harder to identify with the extra clutter...

I think the option for icons only may be coming in compiz 0.9, so maybe I'll just sit tight (hopefully ability to control the icon size as well).

---

### Post by dmelliot on 2010-09-04
Hi,

I've ended up solving this with brute force.

Downloaded the compiz-fusion-plugins-main source package and made a couple of small tweaks, rebuilt and installed. (see attached pic for example).

Will try and wrap the changes up into a patch or maybe a .deb for others to try.

---

### Post by triplemaya on 2010-11-05
Hi dmelliot, this looks really good. Any progress on a .deb?

---

### Post by alexcriss on 2010-11-23
> **dmelliot said:**
> Hi,

I've ended up solving this with brute force.

Downloaded the compiz-fusion-plugins-main source package and made a couple of small tweaks, rebuilt and installed. (see attached pic for example).

Will try and wrap the changes up into a patch or maybe a .deb for others to try.

Hi dmelliot, your changes look great. I am trying to replicate them, would you mind sharing the staticswitcher.c? I am not very familiar with that C code and your modifications might help me. A diff with the original will suffice :)

Thanks a lot,
Alessandro

---

### Post by Valery Kondakoff on 2010-11-25
I'm interested into the 'icons only' Static Application Switcher too.

---

### Post by abraxyz on 2010-12-16
bump

also interested in how to do that

---

### Post by mikkatterina on 2010-12-16
Under normal circumstances
 When I found a bug, and it can not be solved simply
 I would choose to re-install the system
 Try it

---

### Post by dmelliot on 2010-12-16
Hi Guys,

Big apologies for not posting back earlier.
Have been overseas, then flat out with work...

Have not had a chance to roll up a nice .deb or even a patch file, but have attached an archive with all the necessary files.

The archive has the pre-compiled files of interest - if you're on x86 Ubuntu 10.04 (2.6.32-25-generic) then these should work.  On other systems it's a gamble...

I've also included the src files that I had to change.  So you should be able to download the source package "compiz-fusion-plugins-main-0.8.4" (or whatever the current version is) and then either replace these files or edit them manually as needed.  Compile it up and then either install it separately or copy the necessary files to your existing install (probably in /usr/lib/compiz and /usr/share/compiz).

You can use something like:
```
compiz --replace; sleep 30; metacity --replace
```
to test the changes and avoid getting stuck on a broken WM if it doesn't work.

Also, if someone has the time/skills to roll this up into a proper patch or .deb, or thinks it's even worth submitting to the compiz project, please be my guest.

Will try and be a bit more responsive with any further queries ;)

---

### Post by bamdad.khan on 2011-02-22
you sir, are a genius. i've been searching for something like this for years. this looks so much nicer than the default switcher in compiz, and is currently the only workaround for those ugly, stretched icons.

i managed to successfully build version 0.8.6 of compiz-plugins-main on my arch system with your patches. it works without any problems at all.

this is definitely worth submitting to the compiz devs.

thanks again,
bamdad

---

