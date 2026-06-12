---
title: "Installing THEMES by just putting the packages in the right folders.. not working, Y?"
date: 2010-12-23
forum: Desktop Environments
---

### Post by djpurity on 2010-12-23
I was trying to get some more themes for my Ubuntu 64-bit 10.10 installation, by you know, right clicking on the desktop, clicking Change Desktop Background, and then entering that screen.

Basically it gives the option of "get more <backgrounds> online" where <backgrounds> can be swapped with <themes>, <whatever>, etc. So I did. I got them and then I was like, what do I do with these images? 

The themes seemed relatively self-explanatory. You just clicked them and they seemed to install, but they would appear to install as a "custom" theme and it wouldn't appear as its own selectable option in the menu. Neither would the images. So I figured that I would put them in the same folders that the other things were in.

So, by sneaking temporarily in with **nautilus**, I was able to put the unpacked folders I downloaded for the themes into the themes folder in ~/usr/shared/themes/ and then the backgrounds in ~/usr/shared/backgrounds [sic] and this is where I saw where the backgrounds that circulated were: they were in their own folder! So I made my own folder and named it and put all the fun images in there, thinking I would be creating my own circulating folder of background images that would show up in the Appearance Preferences menu.

Survey says.... 

[CENTER]**[COLOR="Red"][X][X][X][/COLOR]**
<bbbbzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzZ!!!!!>[/CENTER]

**_Wrong_**! Not only do my images NOT show up, the folder does not show up either! But if I go to the Appearance Preference tab Background and click ADD, I can manually ADD all the images, and NOW they show up as selectable image options, but STILL I cannot make the rotating images that the folders seem to create (the folders I speak of are the ones that came pre-existing with the installation).

And now with the Themes tab, under Customize... I can see some of the options for Window Border, Controls, Colors, Icons, etc, all showing up, although for the Icons, they do not seem to work, although they sure appear exactly like they should in the selection menu side, but translating it into appearing on my actual menus? Not so much. EHhh.. not so much at all...

So could someone _please_ tell me what I need to do to get these things to show up and function like the ones around them (the ones that came with the installation)? I went back and set the permissions for _all_ that was placed in the rightful folders to be *exactly* like the other ones. I guess there must be some master list somewhere (else), maybe under my user directory under ~/.themes or .icons or .something. I was reading briefly about the (dot) files like (dot) themes on the gnome site where you go when you click on "get more themes online" link... and I guess I should read more there. Is that the answer? Read more there?

Or can someone *maybe* just describe if I should just _**delete**_ _everything_ I added to the ~/usr/shared/themes and ~/usr/shared/background [sic] folders that I added and start all over? Because now when i try to click them to install, they will not, and I get the big (\) red symbol when doing so, probably because I already installed them before, or something similar.

I just need a *_little_* help, because this is a *little*   [COLOR="Gray"]f o g g y [/COLOR]  for me, but I'm slowly waking my game up, toggling that old ancient linux switch in the ol' brain from those college days back when I went to **GA Tech** and wasn't a *helluva engineer* (I was a comp sci major, derr, but I was a *rambling wreck*, that's fershizzle), but anyway, those UNIX and Red Hat lust days are <scratch that> WERE over with, and I am trying to break this rusty cage back into lusting for linux all over again thru Ubuntu, so help kickstart the brain, please?

I am especially interested in getting those cycling background images, which seemed obvious by using a folder to put them in, but that just didn't work so easy, not like a charm at all. Shameful, really.

Anyway, thanks for any help or pointers in the right direction. And I do sincerely want and need the help, so I do also sincerely appreciate any I do receive.

---

### Post by nilarimogard on 2010-12-23
Just dragging and dropping a .tar.gz theme archive onto the Appearance Preferences "Themes" tab should work and install a theme (except for some custom themes). If you want to manually install it, you can extract the archive into ~/.themes (/home/YOUR_USERNAME/.themes) if you only want to install them for your user or /usr/share/themes (and not "~/usr/shared/themes" like you wrote in the post) for system-wide usage.

Note that to install the theme in /usr/shared/themes, you'll need to open Nautilus as root (press ALT + F2 and enter: "gksu nautilus" without the quotes).


Regarding the rotating wallpapers: you can't just place the images in that folder... an .xml file is required which includes the paths to the images, duration time and so on. There's an application that does all that automatically - [CreBS]("http://www.webupd8.org/2010/06/crebs-creates-background-slideshows-in.html").

---

