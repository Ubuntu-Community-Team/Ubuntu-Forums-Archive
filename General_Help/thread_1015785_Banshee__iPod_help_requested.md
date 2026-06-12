---
title: "Banshee / iPod help requested"
date: 2008-12-19
forum: General Help
---

### Post by abo999 on 2008-12-19
I'm trying to get my iPod 30GB classic working with Banshee.

When I plug the iPod in it does not automatically mount (none of my removable media does), so I mount it using the terminal.

On starting Banshee, the iPod is detected but when I select it to view the contents, the status bar (with the gnome icon) just reports 'Loading NEAL'S IPOD'. I've left it at this status for about an hour now so I'm guessing nothing good is happening?

Also, if I drag and drop music to the iPod, Banshee appears to copy it but if I disconnect the iPod and check, no music is present. Incidentally, if I try dropping a lot of files to it banshee will exit after a random amount of time.

The iPod is empty BTW, I've just erased everything from it using iTunes on my wife's Windows laptop.

---

### Post by nothingspecial on 2008-12-19
I don`t know what`s up with banshee (I haven`t used it for a while), but have you tried any other ipod software?

I`ve always found gtkpod to be the easiest if not the prettiest. Install gtkpod-aac if you want video support.

Banshee is a media player with added ipod support as far as I know, where as gtkpod was developed to manage your ipod.

Me, I`ve [[COLOR="DeepSkyBlue"]rockboxed[/COLOR]]("http://www.rockbox.org/") my ipod.

---

### Post by abo999 on 2008-12-19
Yeah, I tried Amarok and gtkpod as follows:

Amarok: Media Device: failed to create lockfile on iPod mounted at /media/ipod: Permission denied

gtkpod: Transfer of 'Wartime' failed. Error opening '/media/ipod/iPod_Control/Music/F19/gtkpod121457.mp3' for writing (Permission Denied)

gtkpod: Error initialising  iPod: Problem creating iPod directory or file: '/media/ipod/iPod_Control/Artwork'

couple of examples there...

It looks like permission then, so I tested it from the terminal and I can do stuff like sudo mkdir /test and sudo rmdir /test while in the iPod_Control folder successfully.

I tried setting the permissions like I did with a HD:

sudo chmod -R a+rwx /media/ipod

But this did not help...

---

### Post by nothingspecial on 2008-12-19
I can`t help because although I`ve had ipod issues in the past and asked for help I`m not familiar with your issue.

I have heard it mentioned that it is a good idea to "restore" or "reset" your ipod with iTunes before using it with linux. I can`t say if this is good advice or bad because my ipod has never seen iTunes (or windows or a mac)

What I will say is that I love rockbox (see link in my first post). You can put flac or ogg etc on it and it has loads of cool features - Doom for example instead of that stupid helicopter game. I have installed it, and uninstalled it and my iPod worked perfectly with the original Apple software so I would say give it a go. However I don`t fully understand what it does to your iPod and I believe it invalidates your warranty so do so at your own risk.  

If I were you I`d wait for other replies. If You were Me I`d install rockbox.


Hope you get it sorted.:p

---

