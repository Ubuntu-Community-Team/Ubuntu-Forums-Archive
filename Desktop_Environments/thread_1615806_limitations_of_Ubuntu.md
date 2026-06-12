---
title: "limitations of Ubuntu ?"
date: 2010-11-07
forum: Desktop Environments
---

### Post by AM_SOS on 2010-11-07
Hi all,

I am wondering what disadvantages accrue from the fact that Ubuntu versions cannot be optimised to work with a particular set of hardware. I mean while Ubuntu now more and more works automatically out of the box with almost all (?) laptops, what kind of compromises does this entail?

One area where I think this happens is the display. e.g. my toshiba A 200 has a native resolution of 1280 * 800. Now I have noticed that when I use it with XP there seems to be more amount of screen space. With Ubuntu things on the screen seem to be lighter tighter. Its almost as if the Ubuntu screen is actually operating a slightly lower resolution than XP. And perhaps this is why it feels like things are more cramped on the Ubuntu screen when compared to the XP screen. Perhaps this is a necessary fallout of the fact that Ubuntu has to be able to work with a huge variety of laptops? And unlike OS supplied as OEM there is no way for the manufacturer to tune it to a particular set of hardware?

Would love to hear more on this. And of course if there are ways of fine tuning the setup :o)

thanks!

---

### Post by P4man on 2010-11-07
Assuming ubuntu actually works at the correct resolution on your laptop, then all you are seeing is probably a side effect from gnome having two horizontal panels by default. That doesnt work great when you only have 800 pixels vertically. Move everything to a single panel and autohide it, or use something like docky (or unity).

As for compromises to work on a wide variety of hardware.. Thats not the real issue. The real issue is that when ubuntu doesnt work, people blame ubuntu (because "it works on windows"), and when some piece of hardware doesnt work properly with windows, everyone blames the OEM, or card or printer or whatever vendor. Thats the problem. 

As a result, OEMs make damn sure their stuff works with windows, even if that means implementing acpi bios fixes to work around problems that are not theirs, but windows'. If that fix happens to bork an OS that actually follows acpi specifications, like Linux, they dont care and the user blames linux when their LCD backlight doesnt work, or the machine doesnt resume from suspend or their wifi doesnt work because the vendor doesnt disclose specs or drivers or doesnt allow canonical to redistribute the firmware.

---

### Post by 3Miro on 2010-11-07
+1 for P4man.

The default theme for Ubuntu uses larger fonts and tabs and buttons then the default theme for windows. You can try to download a more compact theme (or even one that makes Ubuntu look like windows 7).

[http://gnome-look.org/content/show.php/Radiance+Compact?content=134316](http://gnome-look.org/content/show.php/Radiance+Compact?content=134316)

[http://gnome-look.org/content/show.php/Windows+7+for+linux+ubuntu?content=134186](http://gnome-look.org/content/show.php/Windows+7+for+linux+ubuntu?content=134186)

(you probably don't need everything from the last one, the GTK theme should be enough)

Ubuntu doesn't look any more unoptimized or bloated than any other distro that ships with binaries. With Gentoo, I managed to get Gnome + Compiz working while taking only 97MB of RAM at boot, but that is way too much trouble (unless you are like me and you like compiling)

---

### Post by AM_SOS on 2010-11-07
hey thanks both of you for these informative replies.
yes i understand what you mean about people blaming linux when their hardware doesnt work.

btw, i am planning to buy either the toshiba portege R 705 or the satellite T 235.
do any of you have an idea as to how ubuntu performs with these ?
i mean are there any hardware problems etc?

also i tried the radiance theme. it did make a difference but not much :o(
guess will have to live with what i have.
thanks!

---

### Post by 3Miro on 2010-11-07
Got to System -> Prefs -> Monitor to make sure you are running the correct resolution. You can try the windows 7 theme, it will change the tabs and fonts and it will be very close to windows. You can change the default two panel mode by removing one panel or making a smaller panel to the side (I often put a small panel on the left side with a menu and a bunch of shortcuts, this cleans a bit of vertical space). Also, remember that Linux comes with several workspaces by default. If you have a lot of windows open, you can distribute them between two-three workspaces and then switch with either shortcuts or mouse wheel.

For the laptops, I don't have any of those and from what I have heard Toshiba has bad reputation for laptops. This may be wrong of course.

On portege R 705, it should work out of the box. Intel wifi is well supported as well as Intel graphics.

On satellite T 235, I couldn't find what kind of wifi it has so this is a potential problem.

In my experience, the only way you can guarantee that a laptop will work with Ubuntu (and get good professional support for it) is to get one from System 76.

---

### Post by AM_SOS on 2010-11-07
Well I'll try the windows theme, but have no great love for it! Quite dislike vista / 7. XP was neater and simpler...

Sorry I should have said earlier that I deleted one panel soon as I installed Ubuntu. Frankly, the Mac system of having only the top panel which also runs the functions for the applications seems like a much better idea to me.

Btw, I played around a little with the settings and things are better now. So I set the system fonts to times new roman and set all the fonts to size 9.
I also double checked and the monitor settings show this -
1280 * 800 (16:10)

Speaking of themes I think one of the best desktop displays i've recently come across is from the macs. The blue really gels well with the other application colours, and makes for great readability!

Hey, what's System 76 ? Never heard of it.
Please enlighten me!

---

### Post by 3Miro on 2010-11-08
You like Mac? Why didn't you say so:

[http://gnome-look.org/content/show.php/eGtk+Leopard?content=134017](http://gnome-look.org/content/show.php/eGtk+Leopard?content=134017)

Just go to gnome-look.org and look around for all sorts of themes. The bottom panel is called Avant Windows Navigator or simply AWN. You can get it via the Software Center.

System 76 is a US company that sells and SUPPORTS computers with Ubuntu preinstalled. They will test all the drivers and all the possible issues before they sell you something. Then again when it comes time to upgrade to a new version of Ubuntu. They have official sub-forum here, where couple of people from their staff answer questions. this is their job, they are not volunteers like the rest of us. With them, you will not have to pay for a windows license (they do provide windows drivers, but no windows support or license). They stuff is not cheap, but from what I have seen it is the best quality for the price. I have one of their Pangolin Laptops (an older model than what they offer now) and I love it. You can go to system76.com and you can browse on their sub-forum (from the main page of this forum, go to system76).

---

