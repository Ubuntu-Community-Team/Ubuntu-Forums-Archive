---
title: "Gnome Splash hangs at Update-Manager"
date: 2005-05-08
forum: Desktop Environments
---

### Post by thegreedyturtle on 2005-05-08
When you first start up Gnome, there's a pretty little splashy window that shows all of the things that are being loaded.

Well, my issue is that when the icon for Update-Manager appears, it stops loading. Everything seems to load and run as normal, but the Splash screen stays there until I actually click on it, at which it disappears into the night like a banshee.

Now, I could go on and pretend it doesn't happen or exist, but I've had some other problems that seem a little strange to me, and I'm thinking that they might be cropping up due to things not being loaded when Gnome starts... and because I hate when something mysterious like this happens. If it's broke, I at least want to know why it's broke.

The biggest issue that I have been noticing is my usb isn't working like it should anymore. My Palm doesn't hotsync, and my printer is permanently paused. When I try to resume my printer, it immediately goes back into pause mode.

I know enough about Linux, but honestly not that much about X and Gnome, so I can't quite spew useless logs like I usually do for forums people to pick over and realize that they are worthless... but if you want a log and you know where it is, all you have to do is ask... feel free to tell me where the gnome stuff is kept even if you don't want 'em!

---

### Post by tread on 2005-05-08
Hmm, I don't know where X stores the log either, but when I was trying to get some error messages, I disabled gdm and started X from the commandline. Then ctrl-alt-f1 allowed me to see the error messages.

---

### Post by thegreedyturtle on 2005-05-09
I think I found the problem, one of my startup items was getting hung. I deleted the line, and now it seems to be starting w/out a problem... I think.

I'd still like to know where gnome stores it's logs.

---

