---
title: "Automatically save screenshots with Ksnapshot?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Brighid on 2006-06-10
Hi all,

I must say that I love the Ksnapshot program.  It gives a lot more options for taking screenshots than did Windows.  However, I don't like having to manually save images every time I take a picture.

Is there any way (perhaps using a script?) to make Ksnapshot take a picture and automatically save it to a file (snapshot#.png) without any window coming up?

Also, this might not be a problem if I used a script, but would there be a way to disable the bouncing logo next to the mouse when it takes the picture?  I've had the problem of the logo showing up in some of my pictures (most notably, ones taken while running a 3D game).

Any help would be greatly appreciated.

Thanks,
Bríghid

---

### Post by GeneralZod on 2006-06-10
There's a rather ... ahem ... "inelegant" way of doing this if you have imagemagick installed (available from the repositories).

The command-line call:

```

xwd -root | convert - "~/pictures/snapshot1.png"

```

will dump a screenshot (in png format) into a file in /home/**<username**/pictures/snapshot1.png.  You can modify this with some handy scripting to increment the number in the filename if that file already exists, and add it as a key combination using e.g KControl->Region & Accessibility ->Input Actions if you wish.

Hope this helps - I don't think ksnapshot has the precise functionality you're after, although it should be noted that if ksnapshot is currently running, you can probably use dcop calls to get it to take a screenshot and dump it to the provided filename :)

Not helpful in this case, but KDE also provides shortcuts for taking screenshots without ksnapshot, and adding them directly to the clipboard - you'll be able to see the thumbnail if you have klipper in your system tray, and paste it into an art package, or paste it into the konqueror file manager.

---

### Post by chavo on 2006-06-10
Actually with Imagemagick installed you can use import. You don't have to pipe xwd into convert like that you just do this 

```
import -window root screenshot.png
```

You can of course customize it by changing to .jpg or even adding the date in the filename using `date`.

 There's also another commandline screenshot program called scrot. It's in the universe repos, so if you have that enabled just apt-get install it. Scrot has a lot of options, I'm not going to list them here. Just try it out, run scrot --help to see what it can do.

Whichever method you choose, you could write a script and then bind that to the PrintScreen key.

---

### Post by GeneralZod on 2006-06-10
Handy tips; thanks, chavo! :)

---

### Post by aysiu on 2006-06-10
I was just reading *Linux Format* today at Borders, and there's a program called *gtkshots* that may help you out. It has a Ubuntu .deb, too!

[http://freshmeat.net/redir/gtkshots/63787/url_homepage/gtkshots](http://freshmeat.net/redir/gtkshots/63787/url_homepage/gtkshots)

---

