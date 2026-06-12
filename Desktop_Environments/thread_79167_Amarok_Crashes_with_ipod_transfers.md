---
title: "Amarok Crashes with ipod transfers"
date: 2005-10-19
forum: Desktop Environments
---

### Post by Hitman1 on 2005-10-19
There is an issue with Amarok when I try to transfer files to my ipod. Everything else works well in the program, but when I hit "Transfer" after quing some files it crashes. No files end up on the iPod. gtkpod works just fine transferring files to the ipod but not Amarok.

---

### Post by Seth on 2005-10-19
[http://bugzilla.ubuntu.com/show_bug.cgi?id=16375](http://bugzilla.ubuntu.com/show_bug.cgi?id=16375)

---

### Post by Hitman1 on 2005-10-19
Thank you. Now I either have to compile 1.3.3 myself or wait for someone to make a deb :(

---

### Post by shanghaipi on 2005-10-23
I am also waiting for that deb....

---

### Post by Staesys on 2005-10-23
Try this:

[http://www.downpourdesigns.com/amarok-1.3.3_1.3.3-1_i386.deb]("http://www.downpourdesigns.com/amarok-1.3.3_1.3.3-1_i386.deb")

I managed to compile and make a .deb with **checkinstall**. I'm not a professional .deb maker, so I'll try and help if there are any problems, but I make no guaruntees.

Here's taglib-1.4 also, in case you need it. I did.

[http://www.downpourdesigns.com/taglib-1.4_1.4-1_i386.deb]("http://www.downpourdesigns.com/taglib-1.4_1.4-1_i386.deb")

**Use at your own risk!**

---

### Post by shanghaipi on 2005-10-24
Thank you very much for the hard work.  The install worked great.  I can also transfer songs onto my ipod.  Thank you, now if I could just get the ipod to unmount properly....not working so well....

---

### Post by CaptainMorgan on 2005-10-24
I installed Amarok and there appears to be no icon for the program.. when I want to launch it I get the error message, Icon Failed to Load. Any suggestions? 



[img]http://www.fs-gilde.de/Forum/images/smilies/saufen.gif[/img]

---

### Post by ltmon on 2005-10-24
[QUOTE=shanghaipi]Thank you very much for the hard work.  The install worked great.  I can also transfer songs onto my ipod.  Thank you, now if I could just get the ipod to unmount properly....not working so well....[/QUOTE]

Ipods need to be unmounted and then ejected.

So once you've hit "Safely remove" open a terminal and type:

> sudo eject /dev/sdaX

where sdaX is sda1 or sda2 or wherever your ipod appears.

L.

---

### Post by Asraniel on 2005-10-24
doesent work, and nearly all my music on the ipod has been deleted. it didnt crash on transfer, but the musics hasnt been added. now the music database seems to be corrupted

---

### Post by taavi on 2005-10-24
[QUOTE=Staesys]Try this:

[http://www.downpourdesigns.com/amarok-1.3.3_1.3.3-1_i386.deb]("http://www.downpourdesigns.com/amarok-1.3.3_1.3.3-1_i386.deb")

I managed to compile and make a .deb with **checkinstall**. I'm not a professional .deb maker, so I'll try and help if there are any problems, but I make no guaruntees.

Here's taglib-1.4 also, in case you need it. I did.

[http://www.downpourdesigns.com/taglib-1.4_1.4-1_i386.deb]("http://www.downpourdesigns.com/taglib-1.4_1.4-1_i386.deb")[/QUOTE]

Thanks for this. I'll certainly try those out at home and let you know, how they work for me.

---

### Post by Staesys on 2005-10-24
[QUOTE=CaptainMorgan]I installed Amarok and there appears to be no icon for the program.. when I want to launch it I get the error message, Icon Failed to Load. Any suggestions?[/QUOTE]

What happens if you type **amarok** from a konsole window?

---

### Post by Staesys on 2005-10-24
[QUOTE=Asraniel]doesent work, and nearly all my music on the ipod has been deleted. it didnt crash on transfer, but the musics hasnt been added. now the music database seems to be corrupted[/QUOTE]

I'm not entirely sure what the issue could be here. One thing to check is that you unmounted and ejected the iPod correctly. If removable media isn't unmounted and ejected it can cause corruption.

---

### Post by Asraniel on 2005-10-24
well thats it, but since there is no easy way to unmount a ipod under linux, i simply remove it.

---

### Post by Hitman1 on 2005-10-24
[QUOTE=Staesys]Try this:

[http://www.downpourdesigns.com/amarok-1.3.3_1.3.3-1_i386.deb]("http://www.downpourdesigns.com/amarok-1.3.3_1.3.3-1_i386.deb")

I managed to compile and make a .deb with **checkinstall**. I'm not a professional .deb maker, so I'll try and help if there are any problems, but I make no guaruntees.

Here's taglib-1.4 also, in case you need it. I did.

[http://www.downpourdesigns.com/taglib-1.4_1.4-1_i386.deb]("http://www.downpourdesigns.com/taglib-1.4_1.4-1_i386.deb")

**Use at your own risk!**[/QUOTE]
Worked like a charm brother. Thank you=D> 

[QUOTE=ltmon]So once you've hit "Safely remove" open a terminal and type:
Ipods need to be unmounted and then ejected.
> sudo eject /dev/sdaX
where sdaX is sda1 or sda2 or wherever your ipod appears.[/QUOTE]
That works, but is there anyway to do it from the GUI icon that appears on the desktop when the ipod gets connected? right now all I can do is unmount it from the icon but it doesnt give an eject option. Is there any config file that I can edit for the GUI to put "eject" in the menu when I right click on the ipod icon?

---

### Post by npu on 2005-10-24
Thanks for the deb, Staesys! Works fine.

---

### Post by Staesys on 2005-10-25
You're welcome guys! I'm glad I could help!

---

### Post by torstenprahl on 2005-11-17
Originally Posted by Staesys
Try this:

[http://www.downpourdesigns.com/amaro...3.3-1_i386.deb](http://www.downpourdesigns.com/amaro...3.3-1_i386.deb)

I managed to compile and make a .deb with checkinstall. I'm not a professional .deb maker, so I'll try and help if there are any problems, but I make no guaruntees.

Here's taglib-1.4 also, in case you need it. I did.

[http://www.downpourdesigns.com/tagli...1.4-1_i386.deb](http://www.downpourdesigns.com/tagli...1.4-1_i386.deb)

Use at your own risk!


Thanks for the info....helped me out big time.  Now I am really enjoying amaroK!!!!:razz:

---

