---
title: "how to install a new look for the panel"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by bosshoof on 2007-05-23
Hi
how to install a new look for the panel?

---

### Post by crimesaucer on 2007-05-23
Do you mean you want a glossy panel like the Windows Vista task bar?

Since I think you use xubuntu from one of your other post's, the only way is to make a .gtkrc-2.0 file in your home directory. Mine looks like this:

```

style "panel"
{
  bg[NORMAL] = "#B9C09C"
  bg_pixmap[NORMAL] = "panel-2b.png"
  fg[NORMAL] = "#F0F2E7"
  }

widget_class "*Panel*"      style "panel"
widget "*Panel*"            style "panel"
class "*Panel*"             style "panel"

```

I made a 1 pixel wide 34 pixel tall image using GIMP. It was of an image to match my Emerald Glass theme. It is my panel-2b.png

---

### Post by crimesaucer on 2007-05-23
This is a theme I made last night, and that is my homemade panel, that matches my original Emerald theme:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-20-9.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-20-8.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-20-8.png)

---

### Post by bosshoof on 2007-05-23
what to do ?
> **crimesaucer said:**
> Do you mean you want a glossy panel like the Windows Vista task bar?
[COLOR="Red"]yes[/COLOR]

Since I think you use xubuntu from one of your other post's, the only way is to make a .gtkrc-2.0 file in your home directory. 
[COLOR="Red"]
please tell me,how to do so ?[/COLOR]


---

### Post by crimesaucer on 2007-05-23
I'll find a guide with a download image for you.

It'll be a moment...but really, it's just like that gtkrc-2.0 that I posted. All you would have to do is have your own image and font colors.

---

### Post by crimesaucer on 2007-05-23
So try this out, I haven't seen it but it probably looks like Vista: [http://gnome-look.org/content/show.php/Lindows+XP+panel?content=58902](http://gnome-look.org/content/show.php/Lindows+XP+panel?content=58902)

This is how I did mine: [http://ubuntuforums.org/showthread.php?t=430947&highlight=bg_pixmap%7Bnormal%7D+background+image](http://ubuntuforums.org/showthread.php?t=430947&highlight=bg_pixmap%7Bnormal%7D+background+image)

...I just made my own image.

here is another page of info: [http://ubuntuforums.org/showthread.php?t=334570&highlight=xfce+panel+gtkrc-2.0](http://ubuntuforums.org/showthread.php?t=334570&highlight=xfce+panel+gtkrc-2.0)

...and this is another page that used to have links to people's images for the panel, but they are all old and no longer there: [http://ubuntuforums.org/showthread.php?t=351517&highlight=panel+glossy+image](http://ubuntuforums.org/showthread.php?t=351517&highlight=panel+glossy+image)

Now if you search the ubuntu forums for the "glossy panel" and any other things having to do with "gtkrc-2.0", you will see many more posts.

And if you download a theme from Xfce-Looks.org or Gnome-Looks.org, they sometimes include the panel theme in the folder. Especially the Linsta themes: [http://gnome-look.org/content/show.php/LiNsta+%28LiNsta+is+Not+Vista+%3B-%29?content=42697](http://gnome-look.org/content/show.php/LiNsta+%28LiNsta+is+Not+Vista+%3B-%29?content=42697)

or this nice one: [http://gnome-look.org/content/show.php/Darker+theme?content=32768](http://gnome-look.org/content/show.php/Darker+theme?content=32768)

---

### Post by bosshoof on 2007-05-23
thanks ,man
you are really helpful

---

### Post by crimesaucer on 2007-05-23
No problem.

---

