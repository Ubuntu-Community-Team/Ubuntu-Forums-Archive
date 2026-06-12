---
title: "Tiling Windows"
date: 2007-06-10
forum: Desktop Environments
---

### Post by Eoghanalbar on 2007-06-10
I know this has been asked before. I'm sorry, but I just haven't been able to figure it out.

I want to tile windows, kind of the same way I used to in windows by holding ctrl and selecting the windows I wanted from the bar of open windows (what's the right term for that bar?), then right clicking and selective the way I wanted them to tile.

I'm sure the open source community has improved this, too, but I haven't been able to get it to work.

I used synaptics to get DWM, and also beryl unsupported plugins, but it hasn't had any effect I can find.

---

### Post by Pragmatist on 2007-06-10
Someone figured it out! :)

[http://ubuntuforums.org/showthread.php?t=470160&highlight=tile+windows](http://ubuntuforums.org/showthread.php?t=470160&highlight=tile+windows)

---

### Post by Eoghanalbar on 2007-06-10
Oh yes, they did. And they were not very happy with the results... especially considering how much time it took when they could have been studying for a physics test or going mountain biking.

But I dunno, maybe what I learned there'll eventually help me to get something that's actually good working.

---

### Post by asmoore82 on 2007-07-20
forgive me for sidestepping the question.... but I've been a Linux user for nearly 6 years now and I've honestly never noticed it the Tile Windows ability  is there or not... (looks like it's not from the posts)

However, who needs to tile windows when you can have as many desktops (workspaces) as you want?
There is also a very handy GNOME panel applet formerly known as "Window Pager," I think it's now
called "Window List" that shows you all windows you have open regardless of what workspace they are on.

EDIT: After getting back to my Linux Box, I have found that the applet I was talking about is now called "Window Selector"

---

### Post by Afoot on 2007-08-26
> **asmoore82 said:**
> 
However, who needs to tile windows when you can have as many desktops (workspaces) as you want?

For many users being able to tile windows would be very good. Here are a few cases:
[LIST]
[*]Someone who uses GIMP, for instance. Then it would almost behave like a single-interface program, and would be a lot more manageable.
[*]A laptop user without a mouse. To be able to tile windows and not having to worry so much about placement all the time would be great (just think of how easy it is to manage windows with something like ion, with only a keyboard).
[*]A developer who uses many terminal windows. Or a user who uses many CLI programs for some reason.
[*]A user who doesn't like wasted space... or just want an overview of things. 
[/LIST]
And I'm not sure why workspaces would make tiling window management worse, it would only improve it!

---

### Post by Endolith on 2007-08-26
> **asmoore82 said:**
> However, who needs to tile windows when you can have as many desktops (workspaces) as you want?

Uhhh...  Someone who wants to use two programs on the same screen at the same time?

Does anyone know of a way to make GNOME behave like a [tiling window manager]("http://en.wikipedia.org/wiki/Tiling_window_manager")?  I want to be able to pick a few windows and tile them without dragging the borders around and resizing them by hand.  I want to be able to drag the borders and have all the windows resize at once.  I want to be able to set resizable "frames" into my WM and maximize a window into a certain frame just by clicking and dragging.  At the very least I would like window borders to snap to each other or to a grid so that I don't need to waste time with fine manual adjustments.

---

### Post by syarlett on 2007-08-29
Couldnt agree more! Anyone got an update on this?

---

### Post by DanielBeaver on 2007-10-07
The lack of tiling support in gnome baffles me. This functionality has existed in windows since 1995.

---

### Post by Endolith on 2007-10-07
> **DanielBeaver said:**
> The lack of tiling support in gnome baffles me. This functionality has existed in windows since 1995.

Yes, but this is GNOME.  Functionality is baaaad.  :-)

---

### Post by Pragmatist on 2007-10-07
You have four choices if you want to fix this problem:

1.) Use **wmtile** software
[http://ubuntuguy.wordpress.com/2007/06/12/how-to-tile-windows-in-gnome/](http://ubuntuguy.wordpress.com/2007/06/12/how-to-tile-windows-in-gnome/)

This is the most common approach right now, and it might be incorporated into Ubuntu in the future:
[https://blueprints.launchpad.net/ubuntu/+spec/gnome-tile-windows](https://blueprints.launchpad.net/ubuntu/+spec/gnome-tile-windows)


2.) Use a different window manager; one that does window tiling.  Apparently IceWM can do tiling:
[http://ubuntuforums.org/showthread.php?t=277283](http://ubuntuforums.org/showthread.php?t=277283)

  While researching answers for this thread, I have noticed a common misconception about window managers.  A window manager is just a program.  GNOME is not a program.  GNOME is a collection of programs and settings designed to give a consistent "look and feel".  GNOME and KDE are both "environments", thus the 'E' at the end of the acronym.  GNOME includes a default window manager in its collection of programs.  Right now that program is called "metacity", but GNOME used other programs in the past.  You can use a different window manager, and still be using GNOME.  Just as you can change the default background, or use a different terminal program, or a different set of fonts, or a different widget set, and so on, and so on.  Does this mean you can use ANY window manager program with GNOME?  No.  Since GNOME is, by definition, just a collection of programs and settings, the key issue is whether or not alternative programs will play nicely with the others in the collection.  The window manager is just one of the programs in GNOME, but it is also a "low-level" program that many other programs depend on.  Every progam in the GUI uses a window, so obviously the window manager program has a more important role than many other individual programs.  This is why it is necessary to only use window managers that are compatible with the other programs and settings within the GNOME collection.  There are many such window managers: xfce, kwin, fluxbox, iceWM, WindowMaker and many many more.  Here are some examples demonstrating these concepts:

(a) Install iceWM, and when you get to your display manager, choose iceWM as your temporary window manager.  Then, when inside iceWM, open a terminal (let's use gnome-terminal), and run the program called "gnome-panel".  Now change your background to the one you had "in GNOME", and everything looks like GNOME.  Will it act exactly like your previous setup?  Of course not.  In your previous setup, a script was run that automatically started a whole bunch of GNOME programs.  You can set things up so that script will run under your new setup, and then things will mostly work like your previous setup, except your window manager is different.  In this method, you are starting with a window manager and a bare minimum of programs.  Many people like these "lightweight" systems, since they don't want many programs started everytime they boot.  They want to choose which ones are started and which aren't.  This is why their systems run so much faster.  They aren't weighed down by a bunch of running programs that they don't use or need.

(b) Keep your current system just the way it is, but just change the window manager.  Install iceWM, for example, and then edit the appropriate configuration file that chooses the window manager, and now everytime you start your system, you have iceWM as your window manager and everything else is the same.  This is the inverse of method (a).

3. Contact the GNOME team and request a tile feature that works like the Windows tile feature.  This is the easiest approach, but you have to wait for results, and it is possible that they will never implement your suggestion.

4. Figure out who makes metacity, and make a feature request.

---

### Post by Endolith on 2007-10-07
> **Pragmatist said:**
> 
4. Figure out who makes metacity, and make a feature request.

[http://bugzilla.gnome.org/show_bug.cgi?id=85523](http://bugzilla.gnome.org/show_bug.cgi?id=85523)

Don't hold your breath.

---

### Post by Forlong on 2007-10-07
Gutsy has Compiz as the default window manager of GNOME and Compiz has support for tiling. :)

---

### Post by Endolith on 2007-10-07
> **Forlong said:**
> Gutsy has Compiz as the default window manager of GNOME and Compiz has support for tiling. :)

How do you get to the tiling?

---

### Post by DanielBeaver on 2007-10-08
Pragmatist-> Nice name :)
I tried the wmtile solution, and it works (weee! window tiling at last!).
Is it possible to create a keybinding for this program?

> Gutsy has Compiz as the default window manager of GNOME and Compiz has support for tiling.
Are you talking about the expose clone? That is not the kind of tiling I am talking about; what I am talking about is resizing two windows so that I can view and work with them both at once.

---

### Post by Endolith on 2007-10-23
I've been trying compiz, and it definitely seems like a feature that the plugin writers would want to implement, but I don't see any plugins that do this currently.  Is there one?

---

### Post by Endolith on 2007-10-23
Ooh it looks like there's one in Beryl.  Probably not as good as Ion, but a start:

[http://www.youtube.com/watch?v=oyBU8RK-qzY](http://www.youtube.com/watch?v=oyBU8RK-qzY)

---

### Post by phrostbyte on 2007-11-07
Ion and wmii implement tiling features that pants anything seen in anywhere else. Tiling windows is becoming more and more relevant as monitor size and number increases.

---

### Post by Endolith on 2007-11-08
> **phrostbyte said:**
> Ion and wmii implement tiling features that pants anything seen in anywhere else.

Too bad they don't do anything else.

---

### Post by MigBc on 2007-11-22
Ion does a lot more than Metacity! The tiling and tabbing is great, so are the workspaces and the keyboard controls (after changing the default settings to a usable key configuration). You can even make the windows floating and drag them around, although that is not so nice, because the title bars are very small. But once you have it, you don't want to push the windows around anymore (not that I ever liked it very much ever before). I use Ion3 with Gnome for some months now and it's great. I wrote a wiki article about it and the Gnome integration. It's german, but maybe it can help some of you nevertheless: 
[http://wiki.ubuntuusers.de/Ion3]("http://wiki.ubuntuusers.de/Ion3")

Thats how it looks like:
[[img]http://yourlinuxdesktop.org/d/67-2/GNOME_Ion3.png[/img]](http://yourlinuxdesktop.org/d/65-1/GNOME_Ion3.png)

Mhh the screenshot isn't available right now, but maybe it will come back. There is also a screenshot in the article.

---

### Post by rune0077 on 2007-11-22
Okay, maybe I'm stupid, but...

I have never, in my life, used tiled windows, but it seems to me that if you're using compiz, couldn't something like the scale plugin do about the same thing? It could, as far as I can tell, certainly do all the things mentioned in the above examples (I think I would far prefer it to tiling).

Oh, and that was just that. If I have completely misunderstood the concept of tiling, or if you're not using Compiz, then feel free to call me an idiot (or just ignore this post, whatever you chose)...

---

### Post by Endolith on 2007-11-22
> **rune0077 said:**
> couldn't something like the scale plugin do about the same thing?

Wasn't this already covered in this thread?  Scale plugin is not the same as tiling.

It *could* be done with Compiz, but I don't think a plugin exists for it yet.  This is the closest:

[http://www.youtube.com/watch?v=oyBU8RK-qzY](http://www.youtube.com/watch?v=oyBU8RK-qzY)

---

### Post by MigBc on 2007-11-23
yes  and first, such a plugin had to be very complex to be as functional as a real tiling window manager like ion, which you can script to do almost everything you want and second, i wouldn't use it, because such a huge window manager as compiz can never be as fast as a small one, that also does everything i want. 

and the scale plugin isn't the same at all. it wastes a lot of space and you would still need to adjust the size of windows by yourself, while when tiled, they get as big as the frame. i even think that it wastes so much space that you could only use it with a huge monitor. and one reason to use ion for me is, that i don't want to waste space on my laptop display.

---

### Post by the yawner on 2007-11-23
There is a tile plugin on Compiz. But I guess it's not installed on the default Gutsy install of Compiz. I needed that plugin to compare documents and other stuff side by side, and no, having transparent windows don't cut it.

---

### Post by MigBc on 2007-11-23
I think that is what Endolith mentioned as "closest to a tiling plugin" right? I didn't try it, though... I think it is installalled and choosable if you install the compiz-settings-manager, but not sure.

So if you know it, yawner, is it what you can see in the video posted by Endolith? If you can just tile the windows like in the video and not exactly how you cofigured it for each program or workspace, thats no real tiling.

---

### Post by Irony on 2007-11-25
Here's how to tile like in Windows.

The latest version of tile is here;

[http://ftp.unixdev.net/pub/debian-udev/pool/main/t/tile/](http://ftp.unixdev.net/pub/debian-udev/pool/main/t/tile/)

Download the tile_0.7.4_i386.deb and install it by double clicking on it.

Now go to;

[PHP]/usr/share/applications[/PHP]

Scroll down to;

[PHP]Tile Windows Horizontally
Tile Windows Vertically[/PHP]

Drag them to your desktop or to your panel. Open a couple of windows and test the tile program by clicking the tile icons.

Now right click on the tile icons and choose Properties. Click the No Icon symbol and link to your prepared vertical and horizontal pictures - you can download these svg images I made;

[http://www.box.net/shared/08i4ldlmot](http://www.box.net/shared/08i4ldlmot)
[http://www.box.net/shared/cyvs9s4o6v](http://www.box.net/shared/cyvs9s4o6v)

Note, the tiling only works on non-maximised windows.

Now do;

[PHP]gksudo gedit /usr/share/tile/wmprofiles[/PHP]

And change the numbers to suit your screen, for example change;

[PHP]Gnome2 0 0 36 0[/PHP]

to;

[PHP]Gnome2 0 0 00 0[/PHP]

to allow full screen tiling (if your panels are on autohide like mine).

---

### Post by bazzer on 2007-12-06
I cannot believe that development of this INCREDIBLY USEFUL feature has slowed or stopped. There used to be a plugin got Compiz called 'Tile' which was in the unsupported plugins package, but to use it you have to install the unofficial version of Compiz. 

This is like, BASIC functionality and should really be finished before adding stupid stuff like wobbly windows. How are they going to help you?!!

---

### Post by Forlong on 2007-12-06
> **bazzer said:**
> I cannot believe that development of this INCREDIBLY USEFUL feature has slowed or stopped. There used to be a plugin got Compiz called 'Tile' which was in the unsupported plugins package, but to use it you have to install the unofficial version of Compiz.
That's not true. You can compile the plugin from [here](http://releases.compiz-fusion.org/0.6.0/). 
> **bazzer said:**
> This is like, BASIC functionality
So basic that it's not part of Metacity?
Do Kwin and xfwm4 support tiling (serious question, I don't know but I wouldn't be surprised if they don't)?
> **bazzer said:**
> and should really be finished before adding stupid stuff like wobbly windows. How are they going to help you?!!
Wobbly windows has been written by David Reveman himself.
Since Tile is not a much sought-after plugin, it has low priority. If you want that to change, you'll have to participate in the Compiz community.

---

### Post by bazzer on 2007-12-06
> **Forlong said:**
> That's not true. You can compile the plugin from [here](http://releases.compiz-fusion.org/0.6.0/). 
Thanks for that I'll check it out...
> **Forlong said:**
> So basic that it's not part of Metacity?Erm... So basic it's been part of Windows since 95....
> **Forlong said:**
> Do Kwin and xfwm4 support tiling (serious question, I don't know but I wouldn't be surprised if they don't)?

Wobbly windows has been written by David Reveman himself.
Since Tile is not a much sought-after plugin, it has low priority. If you want that to change, you'll have to participate in the Compiz community.I know you're helping here but can you see how frustrating that answer is? I want to use the system, not develop it!!

---

### Post by Forlong on 2007-12-06
> **bazzer said:**
> Erm... So basic it's been part of Windows since 95....
So? Is Windows the ne plus ultra when it comes to window managers now?
It's a fact that most people do not use tiling. Don't blame Compiz - many other WMs are ignoring the feature as well.
It's simply not true that this is a basic feature.
> **bazzer said:**
> I know you're helping here but can you see how frustrating that answer is? I want to use the system, not develop it!!
Participating doesn't mean you have to develop something.
The Compiz devs need to know there are people out there demanding this feature. Right now there aren't many.
So go ahead and make yourself heard (not here, where no devs will read it).

---

### Post by bazzer on 2007-12-06
The link you've supplied is great, but doesn't work without the 'git' version installed, which is what I do not want to do.

I never said Windows was the best OS in the world, but anyone must surely realise that having a widescreen monitor means you can get more columns on the screen at once. And to get the windows organised into columns requires something to take the strain for you. The usefulness of the plugin should become apparent as more people have wider screens.

I'm not arguing, I'm just pointing out a shortcoming in an otherwise good product.

---

### Post by Endolith on 2007-12-06
> **Forlong said:**
> Participating doesn't mean you have to develop something.
The Compiz devs need to know there are people out there demanding this feature. Right now there aren't many.
So go ahead and make yourself heard (not here, where no devs will read it).

Are you serious?  Tiling hasn't been implemented because there is no demand for it, but wobbly windows has been implemented because....  why?

There's a huge group of people in the Compiz community clamoring for wobbly windows?  I doubt that.

How do we express our interest for tiling windows in a place where Compiz fusion people will see it?

---

### Post by Forlong on 2007-12-06
> **bazzer said:**
> The link you've supplied is great, but doesn't work without the 'git' version installed, which is what I do not want to do.
This is the stable release for Compiz Fusion. It should work with Compiz 0.6.0 (which is installed in Gutsy by default).
> **bazzer said:**
> I never said Windows was the best OS in the world, but anyone must surely realise that having a widescreen monitor means you can get more columns on the screen at once. And to get the windows organised into columns requires something to take the strain for you. The usefulness of the plugin should become apparent as more people have wider screens.

I'm not arguing, I'm just pointing out a shortcoming in an otherwise good product.
I totally agree with you but that's beside the point. You said tiling would be a basic feature of window managers and I showed you that it's not. That's why it has low priority for the Compiz (Fusion) developers.
> **Endolith said:**
> Are you serious?  Tiling hasn't been implemented because there is no demand for it, but wobbly windows has been implemented because....  why?
Because someone (David Reveman, the guy who started Compiz) developed the plugin. It's easy as that. If you're able to code something like this, you can do whatever you want.
But if you don't, you have to find someone who's listening to you and your wishes. Compiz (Fusion) developer proved a lot in the past that they do.
> **Endolith said:**
> There's a huge group of people in the Compiz community clamoring for wobbly windows?  I doubt that.
Although I never said that this is the case... yes, that's a fact. Wobbly windows was one of the very first features of Compiz. Believe it or not, that's part of what the buzz was about these days.
> **Endolith said:**
> How do we express our interest for tiling windows in a place where Compiz fusion people will see it?
[Compiz Fusion forum](http://forum.compiz-fusion.org/) (we have a specific subforum for [feature requests](http://forum.compiz-fusion.org/forumdisplay.php?f=91)) - or you could post to the [mailing list](http://lists.compiz-fusion.org/).

---

### Post by bazzer on 2007-12-07
Ok, I'll concede a point here. I just followed [this]("http://forum.compiz-fusion.org/showthread.php?t=5303") thread and managed to get Tiled windows first time with no major surprises.

I didn't follow the thread the first time I was it due to the big warning in red letters. But it's not difficult at all, and I'd advise anyone to do the same.
:)

---

