---
title: "Animated Wallpaper"
date: 2009-03-18
forum: Desktop Environments
---

### Post by Sojurner on 2009-03-18
Is there such a thing as animated desktops or wallpaper for ubuntu. I remember a while back there used to be something in windows where u could have an animated background but its been far too long since ive seen it. Not looking for anything extreme but something like a starfield or something like that for linux.

---

### Post by mcduck on 2009-03-18
Yes, there is. At least to some level.

Gnome supports fading through a series of images based on time, but there's no tool for making such wallpaper themes but you need to define the images & times in a XML file and then set that as your wallpaper. There are couple of this kind of wallpapers available in gnome-look.org.

Also, one cool one is the Wallpaper Clock screenlet which allows you to use Wallpaper Clocks: [http://www.vladstudio.com/wallpaperclock/]("http://www.vladstudio.com/wallpaperclock/").

For more complex animations you can use Compiz+xwinwrap, which allows running any program you want (including screensavers and movie players) as your wallpaper.

---

### Post by Bleskojd on 2009-03-18
Nice one[http://www.gnome-look.org/content/show.php?content=83443&forumpage=3&PHPSESSID=6]("http://www.gnome-look.org/content/show.php?content=83443&forumpage=3&PHPSESSID=6")

And as mcduck said. Look on [www.gnome-look.org](www.gnome-look.org) and search for "animated wallper" and you should find many of them.

---

### Post by Sojurner on 2009-03-18
that sounds neat but its not waht i was really looking for.. What i wont probably doesn't exit. I was looking for something like the psp background that moves slowly and is actually animated, not just changing backgrounds.

---

### Post by Therion on 2009-03-18
Don't know anything about how well this works, i've not tried it personally, but it sounds like this is what you're looking for:

[http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/](http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/)

---

### Post by kidux on 2009-03-18
I've used animated .gif images before as a background and it worked quite well. The trick is to have it large enough area-wise to cover your desktop.

---

### Post by Sojurner on 2009-03-18
thank you.. thats exactly what im looking for sort of.. cant havce icons over it but i guess now im just getting picky.. lol just hope it works with 2 monitors..  thanx.. now i just have to get it to work.. lol.

---

### Post by larryfroot on 2009-03-18
yep, it will kill your icons, but perhaps a cairo applet/widget stands a chance.

Try cairo-dock its in the repo's
sudo apt-get install cairo-dock
also screenlets might help to put some functionality back on your desktop
sudo apt-get install screenlets

Let us know how you get on with it. I'd be interested to find out! thanks, LF

---

### Post by saxofoner on 2009-03-18
The tutorial on tombuntu works great, I had the matrix screensaver for a wallpaper when I was in one of those "be 1337 and kick-***" phases after I saw Die Hard 4.  :p

---

### Post by Sojurner on 2009-03-18
Well it looks like on a few that ive seen that they still have icons on their desktops but it may be widgets (not sure). But imma get to work on it tonight and tomorrow m orning and ill let u guys know how it works out. 

If someone can tell me if there is any software in the repository to take videos of your screen ill do that and post a link.

---

### Post by Sojurner on 2009-03-18
Alas.. i do not think this is giong to give me what i want. since i am running dual monitors and i dont think it knows how to handle it. besides it covers up everything i use on my desktop. FAIL!! lol ohh well i guess ill have to wait for someone to  write something else

---

### Post by Drokles on 2009-05-31
Is there a way to create new screensavers and use them? or am I stuck with the ones from Gnome-look?

---

### Post by DrDunkMcNally on 2012-05-22
> **Sojurner said:**
> thank you.. thats exactly what im looking for sort of.. cant havce icons over it but i guess now im just getting picky.. lol just hope it works with 2 monitors..  thanx.. now i just have to get it to work.. lol.


if you don't mind your icons being faded you can use this method to make xwinwrap partially opaque: 

xwinwrap -ni -argb -fs -s -st -sp -nf -b -o 0.50 -- /usr/lib/xscreensaver/atunnel -window-id 

notice the "-o 0.50" this makes xwinwrap 50% opaque (range is 1.00 to 0.01) and as you've probably guessed, depending on the value you input the opacity will change thus allowing you to actually see your desktop icons. As a side note, my cairo dock sits on top of xwinwrap and appears unfaded on my desktop.

i've had a lot of fun with this and the helios screensaver is my favorite and you can use any screensaver just by changing where the script points. (ie...... *xwinwrap script* /usr/lib/xscreensaver/helios -window-id)

enjoy!

---

