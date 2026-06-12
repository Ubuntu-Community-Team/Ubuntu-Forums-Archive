---
title: "ridiculous fglrx gnome problem: screen 320x240 how to reset?"
date: 2009-01-28
forum: General Help
---

### Post by fsando on 2009-01-28
SOLVED (For some reason there is no 'marked as solved' option)

I'm having a serious problem now. I accidentally set my screen resolution to 320x240 and I simply can't to the menu to change it back.

My system:
Lenovo T500, ati3650, 15" 1680x1050
Second screen hp lp2475w 1920x1200

I have tried the last week to get my new two screen setup to work. After three-four days of intensive testing and searching (and even a complete reinstall) I've got it to work (not yet satisfactory but acceptable). 

Then I in one reckless moment I wanted to test some strange behavior of the new screen and set it to 320x240. Now the resolution is such that I can't reach anything with the mouse so I don't know how to get my old resolution back.

I can log in to a kde session which is where I'm sitting now (never done that before but I'm finding kde is really cool btw)

I've done the following:
started in recovery mode and used the 'xfix' method. This resets the driver to the open source one. which actually works ok and have better rendering than the fglrx. Problem is that several of my apps don't run with this driver (most notably google earth).
I then re-enabled the restricted fglrx driver, logged out/logged in, and the ridiculous 320x240 resolution was back. 

I've changed my xorg.conf to the backup one - no change - I don't think the fglrx driver uses the xorg.conf at all at least not for its resolution.

I read somewhere that it has its settings store in /etc/ati/amdpcsdb. Tried to change it to the 'default' one but not change.

So now I really need some kind of help. 

I'll keep on researching until I succeed or give up (complete reinstall). It just feels so stupid to do a complete reinstall just because of a wrong resolution. If it gets solved I will of course post the details.

There are other problems too but this is the most serious as I can effectively not use Gnome at the moment. With fglrx it is (before the 320x240) set to 1920x4500 which i can't change. I would really like to know where it's getting the '4500' from. It should be 1920x2250 (width of broadest screen) times (heights of the two screens) (I have them setup to be above each other).

With the open source driver it is set to 1920x2250 as it should be.

any help will be appreciated.

---

### Post by fsando on 2009-01-28
SOLVED! 

Turns out it was really simple (depending on definition of 'simple'). In the '~/.config' folder is a file called 'monitors.xml' (the name gives it away) opened in text editor (gedit) found the 'default' part toward the buttom. And there in clear (xml)text width '320', height '240'. Just changed to my screens default resolution. :popcorn::-({|=

For some reason the 'Marked as solved' option is not available. I'll mark it as soon as it gets there

---

