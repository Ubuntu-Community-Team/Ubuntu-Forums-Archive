---
title: "inexplicable switch from ubuntu to kubuntu boot screen"
date: 2006-01-05
forum: General Help
---

### Post by waldorf on 2006-01-05
I installed ubuntu 5.10 on my computer in October. About 4 weeks ago I installed kubuntu-desktop through synaptic and played around with kde every once and a while.

I shut down my computer this morning (and not for the first time since I installed kubuntu-desktop) and when I turned it back on I suddenly got the kubuntu boot screen.

When the desktop came up it was gnome and everything seems to be the same.

I don't really mind getting the kubuntu boot screen, but its a bit disconcerting to have it change like that and it does make me wonder if something is scrambled that will cause me problems later.

Any thoughts?

---

### Post by akniss on 2006-01-05
[QUOTE=waldorf]I installed ubuntu 5.10 on my computer in October. About 4 weeks ago I installed kubuntu-desktop through synaptic and played around with kde every once and a while.

I shut down my computer this morning (and not for the first time since I installed kubuntu-desktop) and when I turned it back on I suddenly got the kubuntu boot screen.

When the desktop came up it was gnome and everything seems to be the same.

I don't really mind getting the kubuntu boot screen, but its a bit disconcerting to have it change like that and it does make me wonder if something is scrambled that will cause me problems later.

Any thoughts?[/QUOTE]


The same exact thing happened to me only with the xubuntu screen...  
[http://www.ubuntuforums.org/showthread.php?t=107746](http://www.ubuntuforums.org/showthread.php?t=107746)
After seeing the xubuntu splash for a few days, my computer boots up in text mode now.  I have no idea what's going on.

---

### Post by waldorf on 2006-01-05
Ummm!

I can't say that's very reassuring.

I really don't care about what the splash screen looks like - I'm just worried that something is starting to unravel and who knows what is next.

I guess I'm looking for some kind of fix or some reassurance that the whole thing is not about to fall apart.

---

### Post by byen on 2006-01-05
I have to say .this is wierd. I just installed an AMD compatible kernel (k7)on my laptop and my Ubuntu boot screen turned into kubuntu as well. I dont know how this happened. I tried uninstalling 'kubuntu -artwork-usplash package hoping that it would switch back to its default but somehow the kubuntu usplash persists. 
I will dig in deeper and post back if i figure this out. Please do the same if you do.
thanks.

---

### Post by byen on 2006-01-06
ok fixed it. I found some info in one of the threads. this is what you do. Open the terminal and type:
**sudo update-alternatives --config usplash-artwork.so**
(this will open a selection box that lets you decide which splash you would prefer 1.default(ubuntu) 2.kubuntu and 3.xubuntu. select one and then press <enter>)
Now enter:
 **sudo dpkg-reconfigure linux-image-`uname -r`**
(this will build your choice into the initramfs) (enter)

It will take about 10-30 seconds and thats it you are done. 
Restart and enjoy!

---

### Post by Malac on 2006-04-10
I had the same problem after installing Ubuntu, then thought I'd like KDE as well
after installing it through package collection managed to get everything back to Ubuntu except the post grub splash.
As a total newbie this was driving me mad.
Thanks to you for the fix it worked great.

Found this on the Ubuntu Site which said to try:
"# sudo update-alternatives --all"

This brought up some other stuff as well, hope this may be useful to other newbies out there.



"Time Is Precious, Waste It Wisely"

---

