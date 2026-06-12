---
title: "can i set a default window size?"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Somenoob on 2006-07-09
I'm tired of reseting my terminal window size every time i execute it, can i set a default window size for it?

---

### Post by chajuram on 2006-07-09
An answer I too would love to know.

---

### Post by roostishaw on 2006-07-09
Yes, you can. Right click on the shortcut you're using to launch it, then go to 'Properties'. Then make the 'Command' box look something like this: ```
gnome-terminal --geometry 640x480+30+30
```

And obviously change the hight, width, and top and bottom spacing.

By no means am I an expert with ubuntu or linux, so tell me if it works...

---

### Post by Somenoob on 2006-07-09
> **roostishaw said:**
> Yes, you can. Right click on the shortcut you're using to launch it, then go to 'Properties'. Then make the 'Command' box look something like this: ```
gnome-terminal --geometry 640x480+30+30
```

And obviously change the hight, width, and top and bottom spacing.

By no means am I an expert with ubuntu or linux, so tell me if it works...

Thanks mate

---

### Post by Jucato on 2006-07-09
thanks! I was wondering about that, too.

Now if I could only force windows to stay that way (no resizing...)

---

### Post by mdurham on 2006-07-10
> gnome-terminal --geometry 640x480+30+30

This doesn't work for me, it starts up full screen for some reason. I think my sizes are specified in chars & lines say 120x30

man says:
>  --geometry=GEOMETRY
                 X geometry specification (see "X" man page), can be specified once per window to be opened.

whatever that means!
Cheers

---

### Post by strabes on 2006-07-10
I tried this with firefox and it doesn't seem to work. I know it saves the default sizes for firefox and other applications, I just wanted to see if I could change it with the command line. Apparently not though.

---

### Post by bzzhuh on 2007-07-19
What if you're using a keyboard shortcut to open the terminal?

Is there a place on the file system where this shortcut is located?

thanks!

---

### Post by MangasColoradas on 2007-12-18
> **Jucato said:**
> thanks! I was wondering about that, too.

Now if I could only force windows to stay that way (no resizing...)

Yes, I want the un-maximise window size to stay the same evn after it has been maximised again and then the window closed.

---

### Post by catach on 2007-12-18
You could try some [DevilsPie](http://live.gnome.org/DevilsPie). I've been playing around with it to get programs to open on the workspace I wish, but it looks like it supports Geometry too.

---

### Post by MangasColoradas on 2007-12-19
Thanks cat, thats a bit too advanced for me at this stage. :)

I can live with it for now. :KS

---

### Post by quixote on 2008-04-19
> **mdurham said:**
> This doesn't work for me, it starts up full screen for some reason. I think my sizes are specified in chars & lines say 120x30

man says:

whatever that means!
Cheers

That's what I found too.  When I set geometry=some-pixel-values it always opened full screen.  That's because you've told it, in effect, I want 600 lines x 480 chars (or whatever).

Once I set that to geometry=136x36 it was exactly right for me.

---

### Post by kirsis on 2008-04-20
You can also set default size/position with Compiz (if you use it). That way you don't have to alter any existing shortcuts, they will all work.

---

### Post by x1a4 on 2008-04-20
Hi,

Many default settings for X applications can be configured in the ~/.Xdefaults file using the following syntax: 

appname.class.resource: value

An asterisk (*) can also be used to specify all classes or apps.

appname*resource: value

To set the geometry of the Xfce Terminal for instance add this line: 
```
Xfce4-terminal*geometry: WIDTHxHEIGHT+XOFF+YOFF
```

Or XTerm
```
XTerm*geometry: WIDTHxHEIGHT+XOFF+YOFF
```

From the X man page:
> 
The WIDTH and HEIGHT parts of the geometry  specification  are  usually measured  in either pixels or characters, depending on the application.  The XOFF and YOFF parts are measured in pixels and are used to  specify the  distance  of  the window from the left or right and top and bottom edges of the screen, respectively.

For terminal, WIDTH and HEIGHT are characters and not pixels. 

To get the application name and class execute **xprop** in a terminal, then click on the application you want information for.  Application name is in WM_NAME, class in WM_CLASS. 

To get information about an application's resources see its man page.  You can also get information about many X applications using the **editres** tool. 

After making changes you have to load them into the X resource database like so: 
```
xrdb -merge ~/.Xdefaults
```

Google 'Xdefaults' for more information.

---

