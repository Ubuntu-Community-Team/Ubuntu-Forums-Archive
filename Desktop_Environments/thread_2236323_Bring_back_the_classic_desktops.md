---
title: "Bring back the classic desktops?"
date: 2014-07-26
forum: Desktop Environments
---

### Post by justin-c-hawkins92 on 2014-07-26
I was wondering if I was the only one who wants Ubuntu to make an option during install or just an alternate install cd to have the same desktop environment as 8.04 and/or 9.04. I like unity and everything, but for some reason I have an itch to go back to 8.04 or 9.04 (8.04 being my first install of Ubuntu and what made me fall in love with it years ago).....am I the only one who thinks about it? lol

It's not like we can still use those releases since support is completely dropped, but to have an option to have it look, feel, and act like 8.04 or 9.04 would be pretty cool imo and would be a way to run the latest kernels on older machines right?

---

### Post by cariboo on 2014-07-26
You could always install Mate from the repositories, if you want to make your system look like it is 2006 again. :). You may have to install Utopic, to get all the packages.

---

### Post by justin-c-hawkins92 on 2014-07-26
That sounds like a good idea :)

---

### Post by QIII on 2014-07-26
I want KDE to look like this again!

[ATTACH=CONFIG]255036[/ATTACH]

---

### Post by ibjsb4 on 2014-07-26
You could install thh Flashback desktop to your current install and choose at login.  It has the old school look.
```
sudo apt-get install gnome-panel
```
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

---

### Post by Dreamer Fithp Apprentice on 2014-07-26
If you look back aways in the archived older threads you'll see that for several months variations on this idea constituted a remarkably high percentage of the total posts here. So, no, you aren't the only one. I don't know any way to do EXACTLY what you said without serious compromises in functionality and security but you can come pretty close. The easiest way to get what you'd probably consider the closest would be this:
[http://blog.linuxmint.com/?p=2627](http://blog.linuxmint.com/?p=2627)
Mint (well, that variety of Mint anyway, there is also a Debian derived one) is essentially Ubuntu tweaked a little differently, with their own repo, which includes the Mate desktop environment. That page has a link to an installer CD iso with the current Mint with Mate. Mate is a fork of the abandoned desktop environment that used to be the standard one with Ubuntu. Pretty much identical really, except it is an actively maintained project. I ran it for a while. I liked it fully as much as the older, leaner, "classic" style of the Ubuntu of 4 or 5 years ago. All in all, it may have the best panels I've used.

And yes, it is lighter and will run better on older machines. But if a big part of your motivation for asking is> **justin-c-hawkins92 said:**
>  . . .  to run the latest kernels on older machinesyou might like to consider other options as well. There are DEs even lighter. Lubuntu is probably lighter. Not having run the latest version of either (I abandoned both in my gradual drift toward lighter and more customised systems a few versions back) I can't swear to it, but I'd be surprised if I'm wrong. Plain LXDE (I say "plain" because Lubuntu is built on top of LXDE so it is like LXDE that has gained a little weight but still much more nimble than the rather portly Unity) is a little lighter still. And plain Openbox, which is what I use currently, is still lighter. Again I say "plain" because LXDE is built on top of openbox.  In other words you can add some more stuff to an Openbox system, give it some more tricks, slow it down a bit and you have LXDE. Do the same thing again with still more stuff and you have Lubuntu. In fact if you have Lubuntu, you'll have the options at the login screen of starting EITHER of these 3 desktop environments, so if hard drive space isn't an issue, you can choose to boot fast and simple, or faster and simpler, or much faster and simpler. If hard drive space is really tight, plain Openbox of course is a little smaller as well. There are some DEs lighter still, although I personally haven't eperimented much with them yet.
----------
Wow, this thread got popular suddenly. It was in the no-replies list when I started typing. Likely some of this is redundant in consequence.

---

### Post by justin-c-hawkins92 on 2014-07-26
Lol Q has the idea. I like that idea too ib, but in the screenshot the panel was on the bottom instead of the top. Trying to see if there is anything already made like a complete theme to make it look, feel, and act exactly the same as it did back then. A little bit of nostalgia kicking in lol


[ATTACH=CONFIG]255037[/ATTACH]

---

### Post by justin-c-hawkins92 on 2014-07-26
I just seen your reply dreamer +1. Yes it did get popular quick lol. You  make a very good point on all the other environments. I think I'm going to choose the mate desktop. Is there any way to customize the theme where it looks and acts like 9.04?

---

### Post by Dreamer Fithp Apprentice on 2014-07-26
> **justin-c-hawkins92 said:**
> Would it be better  to install mate or abandon reguarding getting the closest look and functionality from the picture I posted earlier?Guessing here, but I suspect that if the main objective is to have a retro-look environment that came as close as possible to the old look in visual details and UI, you'd probably get there fastest and easiest with Mate, since it IS a fork of the old DE and maintaining that look and feel was a major objective. You may have to learn to edit theme files if you really are perfectionist but that shouldn't be too hard. Putting a panel (or two, or three, or as many panels as you want) where you want it is trivially easy. So are things like changing color, width, font size, etc.

Two points I may have been misleading on:

One from ignorance. I didn't realise until I read Cariboo's post that Mate had finally been admitted to the Ubuntu repo. Canonical resisted that for quite a while. So if you want to try it you don't have to go off the reservation if you don't just crave installing another system. However if you want an installation CD with Mate automatically installed, as far as I know Mint is still the nearest thing to a Ubuntu that has it (though several other distros had Mate versions of their installer disks shortly after Mate came out). 

On another point I may have mislead through oversight. May not apply to you but I caution anyone who is intrigued by my remarks re Openbox, LXDE, and Lubuntu, that although you can technically log in to an Openbox session if you have installed Lubuntu, getting the Openbox menu to work in that case is a nightmare if you don't have some pointers because of the INSANELY byzantine layers of modification added first by LXDE, and then Lubuntu. It can be done fairly easily once you know how. Anyone who wants to I'd refer to a thread I posted maybe a year ago (as an inquiry, not a tutorial) on the LXDE forum where several folks pitched in and jointly figured it out. Some smart fellows over there. I wouldn't do it that way again though if it were me. A lot easier to just install plain openbox and pick and choose some of the LXDE goodies, like lxterminal, lxappearance, lxpanel, etc., a la carte so to speak.

---

### Post by deadflowr on 2014-07-26
> One from ignorance. I didn't realise until I read Cariboo's post that  Mate had finally been admitted to the Ubuntu repo. Canonical resisted  that for quite a while. 

Nobody from Canonical resisted it. Simply put, nobody bothered to build it, until recently.
And also, it wasn't just Ubuntu devs that didn't build it, but Debian as well.

Like a whole lotta packages, mate in Ubuntu is built upon what the devs for Debian have done.

---

### Post by grahammechanical on 2014-07-26
Did someone say Mate?  Take a sip of this:

[http://ubuntu-mate.org/](http://ubuntu-mate.org/)

It is installable. I have it installed. It is stable. It is fast and as regards memory usage it sends out a challenge to other so called light desktop environments. It is built upon Utopic Unicorn. It is not my beverage of choice. But there you go. Mate developers are doing this and who better to do it. There are others including at least one Canonical developer.

[http://ubuntu-mate.org/team/](http://ubuntu-mate.org/team/)

If you people would really like something like Ubuntu Mate to be successful, then stop wishing and join some teams. Help make Ubuntu Mate Remix an official Ubuntu Flavour.

[http://ubuntu-mate.org/community/](http://ubuntu-mate.org/community/)

Regards.

---

### Post by oldos2er on 2014-07-26
xfce4 is a lot like GNOME 2.x was, if you want to give it a try.

---

### Post by justin-c-hawkins92 on 2014-07-26
Deff sounds like I will be going with mate if it's the closest to the look, feel, and functionality of ubuntu 9.04. I can edit themes and all of that so I will be working on it to look exactly like it....well....the closest I can. Then if at all possible try and make a theme package so others that want the same thing can use it. Idk if you can load a theme package in mate or if it's only able to manually bc I've never used it before, but either way will try to duplicate it. :)

graham I just saw your reply to the post. The links you have provided is awesome :) I have heard of mate here and there, but ubuntu having their own site for it is amazing :) I am downloading the alpha remix now to check it out. How does one join some teams like you were suggesting?

oldos2er I like xfce and is a good choice as well.

---

