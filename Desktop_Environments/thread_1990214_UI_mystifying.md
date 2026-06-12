---
title: "UI mystifying"
date: 2012-05-29
forum: Desktop Environments
---

### Post by marcle on 2012-05-29
Hi,
I've been a programmer and support guy for PCs since the early 80's, and have also worked on mainframes and minis. In the process, I learned to use Linux from the command line (although I was never a whiz at it).

Mostly I use Windows, I'm still on XP on my home computer, it runs like greased lightning on modern hardware!

I needed to solve a hardware problem, and downloading Ubuntu seemed like the best way (thanks, gparted!).

However, this UI is too boggling for me. Fortunately, I like purple just fine, but I have no idea how to get around the OS or the computer.

I figured out that alt-F2 will get me a command line of sorts, but it doesn't behave like a normal command line -- I guess it's some kind of search thing. But I have no idea what it's searching for, or where.

I'm used to thinking in terms of files, directories, executables, etc. But your UI seems to be in a whole different world. Is there some map that will show me the relationship?

How can I figure out what apps are loaded? How can I get a regular command line prompt? Is there some write-up about how all this fits together?

Even for an experienced computer guy like me, this is a very clunky and non-instinctive UI. It's got a lot of fancy eye candy, but so far my trial-and-error attempts to use it aren't giving me much success. If there's some consistent scheme here, I haven't figured it out.

I may install Ubuntu, but I doubt I'll want to do battle with Unity. Just a way to get a standard command line would be all I need. Or maybe if there's some concise explanation somewhere on exactly how the UI works, that might help.

Thanks for your help.

---

### Post by LewisTM on 2012-05-29
Coming from Windows you might be more comfortable logging into a GNOME Classic session (from the login screen click the Ubuntu logo and pick GNOME Classic). You will find your familial menus, taskbar and panels. The [Xubuntu]("http://xubuntu.org") variant also provides a similar environment and feels equally like a lubricated electrical event.

From there you can select Applications/Accessories/Terminal to get a terminal window.

There are lots of wikis and tutorials out there on pretty much any topic about Ubuntu. Feel free to ask if you get stuck.

Cheers!

---

### Post by kansasnoob on 2012-05-29
Since you like Win XP you may like this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I'm working on a number of updates for that but spring and summer are always tough for me as far as desk time ;)

---

### Post by bogan on 2012-05-29
Hi!, **marcle**,

The easy way is to click on the Ubuntu Icon top left - that is called the Dash - and enter "term", short for 'Terminal' in the search thingie.

That will give you a choice of four different 'Command line' windows, select one and an Icon for it will appear in the Left-hand Launcher bar.

Right- Click on that, select 'Lock to Launcher' and it will be available when ever you want it.

My heart bleeds for you.

Chao!,** bogan**.

---

### Post by kansasnoob on 2012-05-29
This may also be helpful:

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

Lots of good info there :)

---

### Post by nothingspecial on 2012-05-29
Hi, see this

[https://wiki.ubuntu.com/Unity](https://wiki.ubuntu.com/Unity)

To get a command line, press Ctrl-Alt-T

---

### Post by VanillaMozilla on 2012-05-29
A couple of things to get you started.  I forget a couple of details.  You can figure them out.  It's not hard, really, and there is some VERY nice stuff under the hood once you clear a few hurdles.  (The key to this is patience.)

You said you don't like Unity.  You're not alone.  I recommend Gnome Classic (Without Effects).  Choose it from the Ubuntu login screen.  (There are other desktop possibilities, such as XUbuntu and Lubuntu, but you'll get all bogged down if you start trying to choose the Right One.  Don't even think of it for now.)

To edit the panel (that's kind of the main menu), <Alt> right click.  Just try it.

To edit the Applications menu, I forget, I think it's right click or <Alt> right click.  Then right click on applications and inspect properties.  You'll find it.  That gives you info like what it's called and the command line.

Your home directory is /home/<your login name>.  It is abbreviated
~
or ~./ (depending on what you intend, or context, I guess).

Your application profiles are in hidden directories in your home directory.  Hidden directories have names starting with '.'.  But you knew that.

Everything has at least two names, and there's no obvious connection between the two.  For example, the Gnome file manager is called Nautilus, and it's not really labeled.  Music Player is really called Totem.  Check Help > About to find out what something is really called.  Simple, no?  :D

The Gnome Find Files... tool (aka Gnome File Search Tool) doesn't always find files, especially if they are recently created.  Unfortunately, I don't think Nautilus always finds them either.  :(

Installing and uninstalling.  Start with the Ubuntu software center.  It's very good.  If you need package details, there's Synaptic.  That's a bit complicated, but there's a lot of info there.  Don't forget to right click on stuff.

You asked about the structure of Linux discs, I believe.  What's in the /etc directory?  Does '/etc' really mean 'etcetera'?  Darned if I know, but Google will find you some very good guides.  It's not entirely cut in stone, but it's close.

Good luck.  There's only one way to approach this:  just dive in.

---

### Post by marcle on 2012-05-29
Much appreciation for all the excellent recommendations, and hardly any snark (even tho I probably deserved some).

One nice thing about Linux is the community.

I'll definitely try another front end, and will put up a terminal window just to poke around a little. Let's see, I used to know how to write a script...

---

### Post by VanillaMozilla on 2012-05-30
You probably figured out already, you have to install gnome-session-fallback to get Gnome Classic.  You may have to use Synaptic for that.  It can be done from the command line.  Probably just
apt-get gnome-session-fallback
, but I'm not certain that I remember all the magic words correctly.

---

