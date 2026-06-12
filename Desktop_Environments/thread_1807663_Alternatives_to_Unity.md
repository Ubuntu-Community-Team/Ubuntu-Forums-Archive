---
title: "Alternatives to Unity"
date: 2011-07-19
forum: Desktop Environments
---

### Post by Skaperen on 2011-07-19
If Ubuntu is going to go with exclusive Unity, where does that leave the machines which don't have the graphical power for it?  Will there become a separate "gubuntu" to have Gnome?  Will Kubuntu and Lubuntu and Xubuntu still be around in future versions?

I have been getting less and less happy with Gnome being harder and harder to configure.  So I have been looking at KDE so far.  I have not looked at the others, yet, though maybe I should.  KDE seems to be easier to configure in terms of getting to the menus and alternatively editing the config files in a text editor.  But KDE is still weak in some areas that configuration just can't deal with (Kwin just doesn't compete with Compiz, yet).  What about the others?

I'm not specifically wanting a light weigh desktop.  But maybe lightweight would allow my heavier usage to still work.  For example, I currently use 36 virtual desktops with Compiz arranging it in a 6x6 grid.  The best I can get from Kwin is 20 (so I settled for 5x4 grid), and the switching just isn't quite as smooth.  I may need to go with even more desktops.  People have suggested to use some other feature I cannot remember the name of, but this was much more cumbersome to do the switching for (so back to virtual desktops).

But, back to Ubuntu.  Why not have separate Unity and Gnome setups, as separate installer images, with both sets of packages installable for those that want to have both?  Just make a Gubuntu ISO and keep moving.

---

### Post by FormatSeize on 2011-07-19
> **Skaperen said:**
> If Ubuntu is going to go with exclusive Unity, where does that leave the machines which don't have the graphical power for it? Will there become a separate "gubuntu" to have Gnome? Will Kubuntu and Lubuntu and Xubuntu still be around in future versions?
The lighter versions, like Lubuntu and Xubuntu will still be around. In the next installment of Ubuntu, I hear, there will be a GNOME 3 DE. Sadly, though, it's likely that machines like yours and mine won't be able to handle that either. I'm in the process of building a machine with over-the-top graphical power, so that will be able to handle it, but being that it is for gaming, it won't be running the heavy distros that are coming out now. I'll stick with Slackware (with XFCE) for when I need to do real work. I've found Unity, GNOME 3 in Fedora Core 15, and KDE 4.6.x to be unusable when it comes to a work environment. 
 
> **Skaperen said:**
> I have been getting less and less happy with Gnome being harder and harder to configure. So I have been looking at KDE so far.
This won't work either. The latest releases of KDE are as heavy, if not heavier, than GNOME 3 and Unity.

---

### Post by enimeizoo on 2011-07-19
You can use compiz with kde, right? I know I have the option, I just never tried. 

About your virtual desktops problem, you might want to have a look at activities. Its is basically a third dimension for the pager, and I don't think activities are limited in quantity. That said, activities are not really mature yet, and the management and navigation lack a bit of usability. But with 20 desktops and 3 activities, you get the equivalent of 60 desktops. I'm not sure that without desktop effects and a few memory consuming softwares (people often disable nepomuk and strigi) kde is so heavy. I wouldn't say lightweight neither, though. 

If you want something lightweight, I tried clfswm, and it is quite nice. You don't have any eyecandy, though, it is only aimed for usability and it is fully configurable. It works a bit differently compared to more common window managers. All you have is a tree of frames (you could call them virtual desktop). Frames can contain views of windows or other frames. The navigation can be performed from mouse or keyboard, or both. It is really dynamic (once you got a little bit familiar with basic shortcuts), since you can add, remove, resize frames on the fly. You just need an X server and a lisp interpreter. Since it is fully scripted in lisp (unless you download the binary version), you can change about anything on the fly. 

Hope it helps.

---

### Post by Skaperen on 2011-07-28
If at all possible, I'd like to avoid using Compiz with KDE, and at least try to exhaust all possibility to make Kwin work.

It seems the ability for apps/widgets to bind to keyboard actions is more limited in KDE.  So I don't know how Compiz would even behave in KDE.  It seems what no app/widget in KDE can do is bind to key down and key up actions specifically, and are limited to only binding to complete keystrokes (down then up).  I can make Kwin use Ctrl+Alt+ARROW to move, just as I have in Compiz (where that is the default at least under Ubuntu).  The difference is that as long as I hold Ctr+Alt down, Compiz holds the grid over the screen.  In Kwin, the grid fades based on (configurable) time delay.  Maybe a KDE expert can tell us how to make Kwin behave more like Compiz.

Otherwise, it looks like Compiz is the way to go.  I would like to get some understanding of how Compiz and Kwin do what they do to understand just what impact might exist by using Compiz under KDE.

BTW, Compiz can also do Ctrl+Shift+Alt+ARROW and it will drag the selected/focused window along with the move to a new desktop.  When it does that, the window stays at its exact position within the (new) desktop.  When I move windows to other desktops by other means, the relative position moves down somewhat each time.  I've asked about this before and no one else sees it happening.  It does it on both my desktop and my netbook (both 10.10 but amd64 for the desktop and i386 for the netbook).

GUI programming just has so many places for so many things to go wrong.

---

### Post by Skaperen on 2011-07-28
> **FormatSeize said:**
> The lighter versions, like Lubuntu and Xubuntu will still be around. In the next installment of Ubuntu, I hear, there will be a GNOME 3 DE. Sadly, though, it's likely that machines like yours and mine won't be able to handle that either. I'm in the process of building a machine with over-the-top graphical power, so that will be able to handle it, but being that it is for gaming, it won't be running the heavy distros that are coming out now. I'll stick with Slackware (with XFCE) for when I need to do real work. I've found Unity, GNOME 3 in Fedora Core 15, and KDE 4.6.x to be unusable when it comes to a work environment. 
 

This won't work either. The latest releases of KDE are as heavy, if not heavier, than GNOME 3 and Unity.
Can Compiz be used, or does something equivalent exist, in the lighter desktops like Lubuntu and Xubuntu?  I don't need effects like sliding or cubes (I have those turned off).  But I would want the grid view and the same keybindings ... and 36 desktops.

I wish all these projects to make fancy graphical effects would always include a means to KISS, and have a way to disable these effects (and gracefully just do it when the video card/chip in place can't do it), while still providing otherwise all the same UI and API.

Compiz has one effect that when I release the ekys, the grid shinks to nothing.  The effect doesn't bother me so I would not need to disable it.  But I also don't need it.  If the grid simply just disappeared instantly, that would be fine, too.

---

### Post by XubuRoxMySox on 2011-07-28
I find Xubuntu to be awesomeness on steroids! It has similar (but simpler) functionality to Gnome 2 but is much easier on resources!

KDE is the most resource-hungry desktop in the history of ever! It is really pretty, though. It won't run on my hardware without really slowing things down though.

As a newcomer, I strongly suggest that whicher variant you choose, stick with the LTS (long term support) edition!

Lubuntu is not "official" yet, but it's ultralight, miserly with resources. But not nearly as configurable as the Xfce desktop.

Just for grins, if you have lotsa room on your hard drive, you can install the different desktops on your existing Ubuntu installation and "test drive" them. Let me offer this example:

Open a terminal and type:
```

sudo apt-get install xubuntu-desktop
```

You'll be asked for your password, then Apt will install the awesome Xubu desktop for you!

When it's finished, you can log out and log back in, choosing Xfce as your desktop for that **[COLOR="Purple"]session[/COLOR]**. Kick the tires, drive it around, play, have fun! If you like it, keep it, and make Xfce your **[COLOR="Purple"]default session[/COLOR]** when you log in.

Don't like it? No problem. Try Lubuntu next! 
```

sudo apt-get install lubuntu-desktop
```

Log out, select LXDE for the next session, and so on.

Enjoy!

---

### Post by Skaperen on 2011-07-29
> **dixiedancer said:**
> I find Xubuntu to be awesomeness on steroids! It has similar (but simpler) functionality to Gnome 2 but is much easier on resources!

KDE is the most resource-hungry desktop in the history of ever! It is really pretty, though. It won't run on my hardware without really slowing things down though.

As a newcomer, I strongly suggest that whicher variant you choose, stick with the LTS (long term support) edition!

Lubuntu is not "official" yet, but it's ultralight, miserly with resources. But not nearly as configurable as the Xfce desktop.

Just for grins, if you have lotsa room on your hard drive, you can install the different desktops on your existing Ubuntu installation and "test drive" them. Let me offer this example:

Open a terminal and type:
```

sudo apt-get install xubuntu-desktop
```You'll be asked for your password, then Apt will install the awesome Xubu desktop for you!

When it's finished, you can log out and log back in, choosing Xfce as your desktop for that **[COLOR=Purple]session[/COLOR]**. Kick the tires, drive it around, play, have fun! If you like it, keep it, and make Xfce your **[COLOR=Purple]default session[/COLOR]** when you log in.

Don't like it? No problem. Try Lubuntu next! 
```

sudo apt-get install lubuntu-desktop
```Log out, select LXDE for the next session, and so on.

Enjoy!
I'd like to see a CD that just installs everything right up front.  Oh wait, that would be a DVD.  At that point, it might be worthwhile to have a dual-arch DVD that can do 32 bit and 64 bit.  Anyone know more than I do about making a customized Ubuntu install ISO?

---

### Post by Simian Man on 2011-07-29
> **Skaperen said:**
> I currently use 36 virtual desktops with Compiz arranging it in a 6x6 grid.
Holy cow!  What do you do with 36 desktops??

> **enimeizoo said:**
> You can use compiz with kde, right? I know I have the option, I just never tried. 
Yes, you can use any window manager you want with KDE and even change your window manager from the GUI.

> **FormatSeize said:**
> This won't work either. The latest releases of KDE are as heavy, if not heavier, than GNOME 3 and Unity.
No, KDE now has slimmer hardware requirements than Gnome3/Unity.  Also, if you have an older computer you can turn off desktop effects, and other services like Nepomuk and get largely the same experience as if you had a fast computer which is NOT the case with Gnome any more.  Each release since 4.0 has brought better performance.  I haven't tried Kubuntu though, I hear that it's not very good.

---

### Post by Megaptera on 2011-07-29
> **Simian Man said:**
> Holy cow!  What do you do with 36 desktops ???


+ 1 :confused:

---

### Post by walt.smith1960 on 2011-07-29
> **Skaperen said:**
> Can Compiz be used, or does something equivalent exist, in the lighter desktops like Lubuntu and Xubuntu?  I don't need effects like sliding or cubes (I have those turned off).  But I would want the grid view and the same keybindings ... and 36 desktops.

I wish all these projects to make fancy graphical effects would always include a means to KISS, and have a way to disable these effects (and gracefully just do it when the video card/chip in place can't do it), while still providing otherwise all the same UI and API.

Compiz has one effect that when I release the ekys, the grid shinks to nothing.  The effect doesn't bother me so I would not need to disable it.  But I also don't need it.  If the grid simply just disappeared instantly, that would be fine, too.

I don't know if this will work for you.  I'm running 11.10 fully updated GNOME classic no effects. I have GNOME-panel installed so I have a bar with "show desktop" on the left and desktops on the right.  I was able to get 36 desktops to show up.  I didn't take the time to put something on each one but I was able to move the mouse pointer along the bar and each desktop # appeared in turn.  I did try showing 6 rows and 36 work spaces.  All 36 spaces were in a space less than 1 cm. square so not usable.  36 workspaces on one row might work though.

---

### Post by XubuRoxMySox on 2011-07-29
Yes, some effects can be added to Xubu to make it look cool and permit keybindings and such.

The attached screenshot illustrates some transparency and cool panel effects on my Xfce desktop, inspired by the look of Unity.

[How I made my Xubu Lucid desktop look like Unity]("http://robinsrantsandraves.wordpress.com/2011/07/20/an-unity-inspired-xfce-dock-in-xubuntu-10-04/")

-Robin

---

### Post by Skaperen on 2011-08-02
> **Simian Man said:**
> Holy cow!  What do you do with 36 desktops??
Lots of different things.  Most of them have large terminal windows staying open to various servers I manage.  Not too long ago this was done via text mode virtual consoles ... and I had 60 of those (that was in Slackware and done by tweaking the /etc/inittab file ... would have to be done somewhere else in Ubuntu).  But graphical speeds these days are now up to the point where I can do what I do on the shell inside a terminal window.  With the text mode, I mapped Alt+(60 different keys) to each one.  That's not practical in X, but using Compiz with Ctrl+Alt+arrows works well.

---

