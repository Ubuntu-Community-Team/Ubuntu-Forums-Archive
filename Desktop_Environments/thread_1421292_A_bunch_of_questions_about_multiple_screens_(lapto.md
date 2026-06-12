---
title: "A bunch of questions about multiple screens (laptop + ATI + drivers + xinerama)"
date: 2010-03-04
forum: Desktop Environments
---

### Post by jptech on 2010-03-04
Hi,

I have a laptop with an ATI Radeon 3400 series GPU.  I also have 2 external monitors that I usually plug in when I'm at my desk.  I'm using the fglrx driver (8.660) on Karmic (9.10).  My current setup has both external monitors configured with the desktop extended from monitor 1 to monitor 2.  The laptop monitor (screen) is disabled.  All of my monitors are 1920x1200.  I have several questions.

1) If I want to switch to using my laptop screen I have to swap xorg.conf files by hand and restart.  If I accidentally start X with no monitors attached and the xorg.conf that the CCC (Catalyst Control Center) built for using my external montiors my system becomes nearly unresponsive.  The only thing that works is an ACPI power down (push the power button and wait for it to shut down).  What's the best (easiest) way to be able to switch between the built in laptop screen or external monitors without having to log out of my Gnome session?

2) When I first installed Karmic (before the fglrx driver) the desktop was mirrored to all three of my screens (laptop lcd + 2 external monitors).  It's unlikely I'd be able to use all 3 at once (independently), right?  I didn't think it was even possible to mirror to 3 screens at once with one video card, so I'm a little confused.  Once I installed the fglrx driver it will only mirror to 2 screens at once (which is what I expected to start with).

3) Is it possible for me to have independent virtual desktops on each monitor, but still be able to drag windows between them.  To be more clear, I don't want virtual desktops on my second monitor.  I want to put a window on it and have it stay there all the time.  I still want to be able to use virtual desktops (expo) on my primary monitor though.  Is that possible?  My machine hangs if I try to use the fglrx drivers with xinerama + dual external monitors.  Would xinerama give me more options if I got it working?

4)  One of my monitors sits about 2 inches higher than the other.  I can adjust the relative positions in the CCC so the positions are offset properly.  However, I get a 'virtual blank space' at the top of one monitor and the bottom of the other.  On my monitor that has the Gnome panels my mouse can go past the top of the screen and it makes hitting the 'Applications|Places|System' menus annoying.  Is there anything I can do?

5) Does the 8.660 version of the fglrx driver work with (g)randr?  If I run grandr I get virtually no options, so I'm assuming no, but I swear I read somewhere they worked together.

6) I was reading the post saying the open source ATI drivers are working quite well, but require kernel 2.6.32.  Will the 2.6.32 kernel eventually hit Karmic or will it always be 2.6.31?  Also, would the open source drivers make things easier to configure?  I see a lot of info on performance, but not much discussion on ease of configuration.

---

