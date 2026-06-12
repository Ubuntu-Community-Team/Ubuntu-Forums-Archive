---
title: "*ACTUALLY* restart, please!!"
date: 2011-09-19
forum: Desktop Environments
---

### Post by W-Unit on 2011-09-19
Hey all,

So I was tinkering with some of XFCE's settings and managed to dig myself in a bit of a hole - nothing terrible, just killed a few gnome-related processes I shouldn't have, and probably have a few gnome-related processes still running that needn't be. Anyways, the result is just that things are rather screwed up cosmetically.

You would think that this would all be resolved with a simple log-out and log-back-in, but no. When I do that, all my programs that I was running previously pop back up - which would be a nice feature, if it didn't entirely defeat the purpose of logging out in the first place. Same thing happens with rebooting, shutting down, etc - whatever processes I had running when I log out will start back up on the next login.

I was going to remove and reinstall the xubuntu-desktop package to see if that would do the trick (this is originally an Ubuntu Netbook Remix install), but I think my upgrade to Natty a while back messed with apt-get, because when I tried to remove it, I got an error saying it wasn't installed (which it most definitely was - that was how I got xubuntu in the first place). Fine, if I don't have xubuntu, I'll install it, I figured.
Not the best choice. Now things are even more mixed up cosmetically, with pieces of gnome here and there mixed with xfce.

Anyways - CAN I PLEASE GO BACK TO NORMAL NOW!?
And for future reference, how *do* I get a "clean slate" on bootup? My definition of the word "shutdown" is to close all running programs and processes, and the next time I boot up, I want nothing running except the desktop environment components and other essential processes. I don't want it to remember that I had 2 terminals and a Swiftfox window open - none of that. How do I achieve this?

Thanks! :)

---

### Post by Copper Bezel on 2011-09-19
_[Here's]("https://answers.launchpad.net/ubuntu/+source/xfce4/+question/71815")_ how it worked for 9.04 to get a clean slate - I'm not certain if everything's still in the same place, but if you go to Session and Startup from the Settings Manager, you can disable the session saving, and then you can delete ~/.cache/sessions to remove the one you already have saved.

---

