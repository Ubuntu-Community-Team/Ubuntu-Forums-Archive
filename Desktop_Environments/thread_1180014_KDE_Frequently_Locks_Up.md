---
title: "KDE Frequently Locks Up"
date: 2009-06-06
forum: Desktop Environments
---

### Post by thisnamestoolong on 2009-06-06
I have Ubuntu Jaunty x86-64 installed on my machine, and recently installed KDE to check it out, and was immediately floored by the elegance of the KDE desktop. My only issue is that it locks up CONSTANTLY -- usually every 4 hours or so. It is very strange when it does this as well, I get a bunch of random lines and pictures from different websites (I have yet to have it happen when Firefox wasn't running, but Firefox is running more or less all the time on this machine so it really doesn't mean much). I can very easily fix it by restarting KDE, but it is a pain in the butt nonetheless. Any thoughts?

---

### Post by krazyd on 2009-06-06
Few questions...
Is it a total lock or just an X lock?
Do you have nvidia or fglrx drivers?
What's your video card?

---

### Post by thisnamestoolong on 2009-06-06
Krazyd -- thank you for the prompt response.

#1 -- I apologise but I am a bit of a newb (but working very hard at changing that), so I am not sure what you are asking as to whether it is a total lock or just X, but only the GUI is locking up, if I ctrl+alt+f1 to the CLI the machine keeps running fine, at which point I can restart KDE, if that is what you are asking.

#2 -- Sorry for not including GFX card info, total brain fart -- I am running an Asus 50V with NVidia 9700M running NVidia 64-bit Linux drivers.

---

### Post by krazyd on 2009-06-07
Hey mate, no probs. :)

So it's just X that lock up then. If you can switch to the other virtual consoles then the kernel itself is still running fine.

Unfortunately, the proprietary nvidia drivers are known to be buggy. These bugs seem to most often be exposed by KDE4 (which uses some different acceleration paths to gnome + compiz). Because these drivers are not open source, it's difficult to impossible to figure out exactly what the problem is because no-one outside of nvidia knows how their drivers work.

This leaves you with a few options:
[LIST]
[*]Upgrade your drivers. I assume that you are using the drivers provided by ubuntu for jaunty? If so, there have been a couple of beta releases from nvidia since then which people have been running with varying degrees of success. You might cross your fingers and see if nvidia has fixed the issue. Google around or ask on the forums here - there are plenty of tips for installing the newer drivers.
[*]Try using the open source drivers ( they are called 'nouveau' ). Unfortuantely they don't have support for 3D yet though.
[*]Switch back to gnome :(
[/LIST]

---

### Post by thisnamestoolong on 2009-06-09
Hey -- thanks much for the help -- I actually had a good bit of luck enabling Compiz Fusion -- 2 days and no crashes, I will see how this works in the long term but it seems like Compiz plays a bit nicer with the NVidia drivers than the KDE compositing engine.

---

