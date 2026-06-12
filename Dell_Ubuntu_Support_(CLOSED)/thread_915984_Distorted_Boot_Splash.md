---
title: "Distorted Boot Splash"
date: 2008-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jorwex on 2008-09-10
Hi All,

I installed Ubuntu on my roommates Dell laptop last night. He isn't around right now, so I can't go check to see his hardware info or model #, but I was wondering if this was some known issue. It's a year and a half or so old, and is using Nvidia-based graphics. The only hint of a problem is when the bootsplash or the log-off progress bar is on screen. It's as if you took each item on the screen, moved it to one side or the other, and compressed them so they're only an 1/8th of an inch or so tall. looks pretty wacky.

Things look fine at the log on screen tho. It doesn't affect anything so it doesn't quite matter, but I thought I'd look into it.

Thanks.

---

### Post by Dennis N on 2008-09-11
In Hardy, the startup-manager package will help configure the spash screen. It might fix your problem.

---

### Post by Zakhafr on 2008-09-12
We are currently making a little script to help rebuilding the USplash screen.

Sorry, it's on the French forum, and thus only it French at the moment.
If anyway you want to have a try, it's here:

[http://forum.ubuntu-fr.org/viewtopic.php?id=248233&p=1]("http://forum.ubuntu-fr.org/viewtopic.php?id=248233&p=1")

Basically you have to remember that during the USplash process, no matter what gorgeous NVidia, ATI... card you got, your PC is only capable of basic things. That's because at this point, the filesystems are not yet mounted, so you can imagine, NO superb screen driver is working. Your system is only capable of what BIOS can do. Generally it is 800x600 or 1024x768 on more recent PC.

Also, USplash MUST be made at a 4/3 ratio, and 256 colour. As you can see, not really artworks !

So if you scren is kind of 16/10, take a 16/10 image, transform it to 4/3, it would look distorted on The Gimp, but OK on the USplash as the reverse distorsion is applyed due to your screen format.

Once the script above is finished debugging, if you should need it I'll propose translation to the author.

---

