---
title: "fvwm-crystal"
date: 2007-03-09
forum: Desktop Environments
---

### Post by thypeacefrog on 2007-03-09
Hey I'm a pretty new ubuntu user with my only other linux experience being with fedora core 2 a few years ago. I'm trying to get a third party desktop enviroment and would rather not go with beryl because of it's development status so I was looking at [www.fvwm-crystal.org](www.fvwm-crystal.org) 

Has anyone got any experience with this? Thanks in advance

---

### Post by TheKid965 on 2007-03-09
I've had opportunity to sample fvwm-crystal about a week ago.  It's not a bad desktop, but FVWM in any form is probably not the best thing for a relative newbie; it just doesn't work the same as GNOME or KDE, and the differences will cause you much grief if you're not prepared for them.

As long as you know what you're getting into, however, it can be a useful skill to learn a more "hands-on" window manager.  However, FVWM is really something I'd recommend for the intermediate-to-advanced user; you might also want to look into [Window Maker](http://www.windowmaker.info), which is a really slick and easy-to-configure WM based on the old NeXTSTEP look-and-feel.  That's usually the one I suggest relatively new users try out for their first steps away from GNOME/KDE-land, as there's really no need to configure text files to set things up (although you *could* do it that way if you wanted to!), due to the inclusion of a GUI preferences utility that lets you alter just about every aspect of Window Maker that you'd want to.

Feel free to disregard this advice, however, if you have your heart set on fvwm-crystal... I just wanted you to have some idea what you were getting into.  It's not quite as straightforward as it might appear to be...

(Oh, and some free advice to avoid getting snickered at by others:  A "window manager" is the term for the program that allows you to move and resize windows, and that draws the titlebar decorations.  A "desktop environment" is a suite of programs that *includes* a window manager, among other applications that include taskbars, file managers, and so on.  For instance, the default window manager in GNOME is called "Metacity," but with some tinkering you can set it up to use Window Maker instead.  FVWM and Window Maker are not desktop environments in and of themselves, which is partially why they aren't as heavy on system resources as, say, GNOME is.  Common mistake made by newbies, but no real harm done. ) ^^;

---

### Post by thypeacefrog on 2007-03-09
Thanks I think I'm gonna try it but if I can't do it I'll just try window maker. I'm trying to install it using the guide at [https://help.ubuntu.com/community/FVWM-Crystal](https://help.ubuntu.com/community/FVWM-Crystal)
when I try to untar the file I get this message:

jack@jack-laptop:~$ tar -xvzf fvwm-crystal-3.0.4-tar.gz
tar: fvwm-crystal-3.0.4-tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jack@jack-laptop:~$ 

Any ideas?

And thanks for differentiating between desktop enviroment and window manager for me =P

---

### Post by TheKid965 on 2007-03-09
Make sure you're issuing the tar command while in the directory containing the fvwm-crystal-3.0.4-tar.gz file.  An easy way to check is to type:

tar -xvzf fvwm-crystal

...and then press Tab after typing "fvwm-crystal."  If the file is present, you'll see that this completes the filename for you (and you'll have learned one of the niceties of the bash shell as opposed to, say, the Windows command line!).

If you *are* in the proper directory and you're still getting the error, try entering it this way:

tar -xvzf ./fvwm-crystal-3.0.4-tar.gz

The difference is the leading "./" I added.  That forces tar to look in your current working directory for the file.

---

### Post by thypeacefrog on 2007-03-09
The tab thing worked. thanks alot

---

### Post by girishv on 2007-03-10
Hi,

You can also visit fvwm users forum at
[http://fvwm.lair.be](http://fvwm.lair.be)
if you face any problem with FVWM as a whole. It also has a section on fvwm-crystal.
There are many user made themes available on the forum and also a tutorial on how
to write your own theme from scratch.

Good luck with FVWM

Girish

---

