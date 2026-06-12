---
title: "How to localize window controls of maximized windows in Unity"
date: 2014-08-21
forum: Desktop Environments
---

### Post by ufarmer on 2014-08-21
After much futzing around with <insert curse word> Unity in 14.04, I have managed to get the menus of maximized windows to stop merging with the top panel in the desktop and sharing space with the titles, and I have managed to get the title bar and the menu options within unmaximized windows top stop sharing space and display on two separate lines.

However, the window controls (closing, minimizing, and maximizing) of maximized windows are still being displayed on the top panel of the desktop beside the windows titles and I would like to localize them as well.

Any advice is appreciated.

---

### Post by Dreamer Fithp Apprentice on 2014-08-21
Screenshots might help. Are the maximised windows in front of and obscuring the panels? Does Unity have an rc.xml file that you could edit?

---

### Post by ufarmer on 2014-08-21
Here is a screenshot showing Firefox maximized on the Unity desktop:

[ATTACH]255710[/ATTACH]

In the top left-hand corner, it shows the controls to close, minimize, and maximize the window are being displayed on the top panel -- although mercifully not being overlaid by the window title anymore.  If I un-maximize the window, these controls are displayed locally in the top bar of the window, thusly:

[ATTACH]255711[/ATTACH]

I would like to localize these controls in the windows even when it is maximized.

---

### Post by Dreamer Fithp Apprentice on 2014-08-22
I confess I had to study the images a bit, but I see what you mean. Image 1 is quite weird. It's as if the Unity panel (pardon my old school nomenclature - I think Unity users call it something else, but the vertically oriented thing with icons in it) isn't overlaid on TOP of the Firefox window, as it seemed on first impression, but seems to be pushing the Firefox window out of rectangular shape, so that the body of the window isn't aligned with the title bar, but is instead offset to the right. 

It looks like image 2 is cropped. Is that right? If so you might want to post an uncropped one to give context. It might help somebody see what needs to be done. I'm afraid I don't. There is probably a preference setting to tell the window manager to keep even maximised windows out of the first 100 pixels or so (whatever figure you need) on the left margin, but not being a unity user (I use plain Openbox as window manager and DE under 14.04, a bit like a minimalist Lubuntu) I don't know where Unity keeps that. I haven't kept up with the details of the default DE since I started using lighter ones, but I think maybe compizconfig-settings-manager may provide a way to make an adjustment like that. I think that might be worth a try at any rate until somebody who knows the Unity-g3 environment well speaks up.

---

### Post by ufarmer on 2014-08-22
Until I futzed around for an hour or so, all of the menu options of maximized windows were displaying on the Unity top panel immediately to the right of the window controls.  So I would see, say:

[close] [minimize] [toggle-maximize] File Edit View History Bookmarks....

But I could only see these elements when I moused over the top panel.  By default it was displaying the window's title instead.  After much Googling about Unity, it seemed that my problem was that the title bar was merging with the top panel and the solution seemed to be to turn on local menus -- which I have done.

I hadn't considered that the vertical launcher was not reaching the top of the display area and thereby causing some kind of overflow from maximized windows.  If the launcher and the maximized window are crowding each other, then the displays of the maximized and un-maximized windows might be consistent.  Thanks for the keen observation.  It gives me some new angles to work.

---

### Post by ufarmer on 2014-08-22
After searching from some screenshots of Unity, it looks like the top panel is meant to span the width of the display and the launcher is meant to span the remaining height.  So my installation seems typical.  I would gladly ditch <insert curse word> Unity for my old favourite Gnome, but, on my first attempt to install 10.04, attempting to install Gnome was an epic disaster.

---

### Post by ufarmer on 2014-08-22
After searching from some screenshots of Unity, it looks like the top panel is meant to span the width of the display and the launcher is meant to span the remaining height.  So my installation seems typical.  I would gladly ditch <insert curse word> Unity for my old favourite Gnome, but, on my first attempt to install 10.04, attempting to install Gnome was an epic disaster.

---

### Post by Dreamer Fithp Apprentice on 2014-08-25
> **ufarmer said:**
> I would gladly ditch  Unity for my old favourite Gnome, but, on my first attempt to install 10.04, attempting to install Gnome was an epic disaster.The older style Gnome desktop environment, the Gnome of Lucid for example, is now usually called Gnome 2 and it is no longer maintained. The gnome in the repositories now is Gnome 3 and is sufficiently different that it caused a lot of gnashing of teeth  when it replaced Gnome 2.  The furor of dissatisfaction was so great it prompted a fork of Gnome 2, called Mate. If you liked the old Gnome 2 environment you'll like Mate. It is the same thing except named differently and actively maintained. I'd suggest using synaptic (which if you don't have, I'd install first. Synaptic is the best way to browse the repo imo), search "mate", order the result alphabetically if it isn't already, and scroll down to the packages that begin with "mate", check them all, and install them. It might do as well to just "sudo apt-get install mate-desktop" but I believe there are some goodies that doesn't pull down. I haven't actually done it either way myself. I used Mate under Ubuntu shortly after it was published but I got it from the Mate website as Canonical drug their feet a long time before finally putting it in the repo. Later I ran Mate under PClinuxOS and LMDE Mint. It was very satisfactory in all 3 environments and I doubt you'd have any problem with it. You select which environent you want to run from a drop down menu at login, so it isn't like you are giving up anything. Mate gets installed in addition to, not a replacement of, your present environment. Which for that matter is how all of the alternate DEs work. You might like to experiiment with several. I've sinced moved in a more minimalist direction, running Lubuntu for a while and now just plain Openbox.  You can try as many DEs as you want without having to reinstall.

---

### Post by Ksiencha on 2014-08-26
When you got your window controls away from the panel, did you try to use to enable that trick: *System Settings -> Appearance* -> on the Behavior tab, selected to show the menus "in the window's title bar"?
Otherwise, sorry, don't know how to change it the in another way.

---

### Post by ufarmer on 2014-09-03
Thanks for the tip about Mate.  I did try to install Gnome again.  I was quite surprised to see how Unity-fied it was and quickly tossed it.  This we-know-what-you-need UI is so un-Linux.  How are you supposed to search for things in the Unity dash if you do not already know what you are looking for?  Among other silliness.

---

### Post by vasa1 on 2014-09-03
By now Unity's "features" are well-known. Nothing new here.

---

### Post by Mike_Walsh on 2014-09-03
> **vasa1 said:**
> By now Unity's "features" are well-known. Nothing new here. 

I have to agree. It's a wee bit like trying to teach your grandmother to suck eggs. These are all standard features of Unity, and Unity's been around for.....what? Four, five years?


Regards,

Mike.

---

### Post by Dreamer Fithp Apprentice on 2014-09-24
> **Mike_Walsh said:**
> These are all standard features of Unity, and Unity's been around for.....what? Four, five years?Indeed. And is STILL intensely disliked by many. With all due respect (and in Vasa1's case, that's quite a bit - Mr. Walsh I don't know as well) and while I doubt it was the intention, the tone of these posts seems appallingly condescending to the OP and without any positive suggestions for him. As Vasa1's sig suggests, DE's are purely a matter of taste. OP is hardly alone in disliking Unity, nor is he in particularly bad company. There is a distressingly common tendency for Unity-loyalists to subtly (or sometimes not) imply that if you don't like the flagship default DE you must be either stupid or senile. Anyone who frequently does internet searches that lead to a variety of IT-related sites, and doesn't confine their reading to these forums, must be aware that people who have a strong distaste for Unity include some of the most technically astute. That's not to say they are "righter" than someone with different tastes, nor that there aren't uber-geeks using Unity, but it does put the lie to implications (which I'm sure aren't all intentional) that anyone who doesn't like your favorite DE is a not-to-bright whiner. So he doesn't like Unity or Gnome 3 and did like Gnome 2. These are perfectly valid views. Give him a break. Lots of people feel the same way. You like steak and I like peanut butter. You like Unity and I like Openbox. Who cares?

---

### Post by Mike_Walsh on 2014-09-24
> As Vasa1's sig suggests, DE's are purely a matter of taste. OP is hardly alone in disliking Unity, nor is he in particularly bad company. There is a distressingly common tendency for Unity-loyalists to subtly (or sometimes not) imply that if you don't like the flagship default DE you must be either stupid or senile...

...So he doesn't like Unity or Gnome 3 and did like Gnome 2. These are perfectly valid views. Give him a break. Lots of people feel the same way. You like steak and I like peanut butter. You like Unity and I like Openbox. Who cares?

I gotta confess, I didn't mean it to come across sounding QUITE the way it did!

I like Unity, yes; but I also like and use Cinnamon (in Mint 17), Gnome 2.....and I have a soft spot for the Xfce desktop ( I have both Unity and Xfce on Ubuntu, and I'm beginning to use Xfce more and more, so....)

I also rather like LXDE, too. I wouldn't describe myself as a Unity-loyalist, at all; I very much enjoy using **ALL **the different DEs that I have. I just wanted to point out that really, there has been an awful lot of documentation by both pro- & anti- camps as to why they love (OR hate) Unity, for quite some time now. 

I guess it's one of those arguments that'll just run, and run.....


Regards,

Mike.

---

### Post by Dreamer Fithp Apprentice on 2014-09-27
Thanks for the response, Mike. I hope I didn't sound hostile. I've tried most of those also. If you like LXDE, you might want to give plain Openbox a try. It is to LXDE, somewhat like LXDE is to Lubuntu. Very light and very configurable. The longer I use it, the more partial I've become to it.

---

