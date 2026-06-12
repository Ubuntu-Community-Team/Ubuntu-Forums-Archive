---
title: "Add 'gnome shell' to Karmic login &quot;sessions&quot;"
date: 2009-11-01
forum: Desktop Environments
---

### Post by Kirk M on 2009-11-01
Hi all,

I downloaded and installed "Gnome shell" via the Ubuntu Software Center and set up the correct command line for the "Accessories" menu item (menu item command line is missing the " --replace" at the end). Activating the Gnome shell desktop via the "Accessories" menu works fine.

My question is; is there a way to add "Gnome shell" to the Karmic Koala login screen "Sessions" menu? It currently has "Gnome Safe" (whatever), "Gnome" and "xterm". I've found no "Session settings or manager" anywhere in the Karmic menus or anyway to add the Gnome shell desktop to the login screen Sessions menu.

Anyone know how this might be done?

---

### Post by coffeecat on 2009-11-01
Well - first I want to thank you for stimulating me to install gnome-shell at last. I like it! Odd that the Accessories menu entry is not ticked in the menu editor by default, and odd that the --replace option is not in the command.

Anyway, I have no idea how to get gnome-shell as a session option in the login screen - if that is indeed possible - but I have an admittedly not so elegant alternative. If you go to System > Preferences > Startup Applications, you can add gnome shell with the command 'gnome-shell --replace' and next time you login, you'll go straight into gnome shell.

This gave me a few heart-stopping moments because at first I couldn't find out how to stop gnome-session and revert to the ordinary gnome desktop. System > Preferences doesn't appear under Activities - not that I could find anyway. But then I typed 'Startup' in the search field, it gave me the Startup Applications app, and I was able to untick gnome-shell in that, log out and in again and get back to the ordinary desktop.

I hope that is useful.

---

### Post by Kirk M on 2009-11-01
coffeecat - Glad to see another who doesn't mind living dangerously. :D

Now that I think of it, there probably isn't a way to stick Gnome shell into the Sessions menu on the login screen since Gnome shell isn't a Linux "desktop" by definition rather than another way to use the Gnome desktop.

In case you haven't come across it yet, here's a link to the Gnome shell "cheat sheet":

[http://live.gnome.org/GnomeShell/CheatSheet]("http://live.gnome.org/GnomeShell/CheatSheet")

But you'll need to keep Gnome shell updated by adding this PPA in order for a couple of the items in the cheat sheet to work as described (there's a newer version available via the Update Manager once you add the repository):

[https://launchpad.net/~ricotz/+archive/testing]("https://launchpad.net/~ricotz/+archive/testing")

Now if I could only find a way to exit out of Gnome shell back to Gnome without having to log out. Using "metacity --replace" in terminal only works sporadically and usually locks up the desktop with no way out but a power down restart. Oh well, it's all new yet isn't it?

---

### Post by autocrosser on 2009-11-01
Good to hear of people that are not bashing the Shell (my--is that a many-meaning statement :)  )--you might look at: [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)  & look at the commits to see what is being worked on at the moment--I use the git-installed Gnome-Shell that you can find on the page--it's very up-to-date as far as features (but sometimes won't work for the same reason)--There is also a list to see what the developers are up to....As far as adding it to sessions--I tried that a couple of months ago & b0rked my testing install very neatly--I'm waiting for the developers to "green-light" a session install for the Shell--so far--it is not happening----but I would guess that there will be a testing way in the next couple of months.

As far as what is happening with testing, watch the testing group forum for more info & the current thread going is: [http://ubuntuforums.org/showthread.php?t=1308932](http://ubuntuforums.org/showthread.php?t=1308932)

---

### Post by Kirk M on 2009-11-01
autocrosser - Thanks for the links. I'm always a hound for info like this. And why bash the Shell (yup, many meanings alright) especially when it's still in the early devlopment stage? The only reason for anyone to start howling about it is if Gnome.org decided to make Gnome shell their only desktop offering once it goes gold. *Then* users would have a reason to sound off.

I don't mind sticking to the (PPA added) repository for keeping Gnome shell updated. Not quite ready to deal with bleeding edge builds.

---

### Post by autocrosser on 2009-11-01
Good to hear--keep a eye on the links I posted & come & join us when it looks "fun" ;)

---

### Post by TWilliam on 2009-12-16
> **Kirk M said:**
> Now if I could only find a way to exit out of Gnome shell back to Gnome without having to log out. Using &quot;metacity --replace&quot; in terminal only works sporadically and usually locks up the desktop with no way out but a power down restart. Oh well, it's all new yet isn't it?
I realize that this post is several weeks old and that you may have found an answer to this by now, but since I don't see anything addressing it in this thread I thought I'd pipe up.

It's a simple matter to revert to 'normal' Gnome if you've launched Gnome Shell from the Applications-->Accessories menu. Merely hit Alt+F2, type 'debugexit' (without the quotes of course) in the command prompt that appears and hit <Enter>.

Oh, and I am REALLY liking Gnome Shell!

---

