---
title: "Changing the colour of Gnome Classic App menu"
date: 2012-01-28
forum: Desktop Environments
---

### Post by Jamie_Edwards on 2012-01-28
Hi guys,

I just wanted to know how to change the colour of the applications menu ( the one thats found at the top in gnome classic ). The theme I have at the moment is Ambiance here's the screen shot:

[ATTACH]211616[/ATTACH]

Now for my window theme I have Vista Basic which is blue. I want to change the colour whole colour of my app menu to the same ish colour of my windows only problem is, as the picture below shows:

[ATTACH]211617[/ATTACH]

I don't get very far, so here's my question... Is it possible and  how do I fully change the colour of my app menu?

Thanks

---

### Post by Dennis N on 2012-01-28
This may help out:

[http://askubuntu.com/questions/69576/how-to-customize-the-gnome-classic-panel](http://askubuntu.com/questions/69576/how-to-customize-the-gnome-classic-panel)

---

### Post by Jamie_Edwards on 2012-01-29
No luck, and I have 11.04, not 11.10 :L

---

### Post by Dennis N on 2012-01-29
How are you changing the color, by using the solid color option or by using a different panel background image? From your shots, looks like an image to me. I just tried to replicate what you did with a "real" gnome 2 panel in Ubuntu 10.04 with Ambiance theme and could not.

---

### Post by Jamie_Edwards on 2012-01-29
I'm using the solid colour option, the image behind is my desktop wallpaper.

---

### Post by Dennis N on 2012-01-29
Ok, did a quick Google search and this might give a method, as it seems to be the same problem you have:

[http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244](http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244)

He edits the gtkrc file for the theme to get full transparency by commenting out the line setting the panel background image. Although it is done in Lucid, the same idea should work.

Good luck.

---

### Post by Jamie_Edwards on 2012-01-29
Thanks @Dennis N but that method didn't quite work... But I did find out eventually, all I did was go into nautilus and did the following:

pressed alt - h to show the hidden files, 
went into .themes, 
then Ambiance,
then gtk-2.0,
then apps,
of which I then opened gnome-panel.rc in gedit
and commented out the following line:
bg_pixmap[NORMAL] = "img/panel.png"

saved the file and logged out and then back in so the changes could take hold, and now my panel looks like this:

[ATTACH]211637[/ATTACH]

which is mostly what I wanted... Now I have to figure out how to make the icons darker XD

Any idea's? And if I figure out how then I'll post up what I did

---

### Post by Jamie_Edwards on 2012-01-29
Found out lol XD

You just have to go to System settings,
Appearance,
In the 'Theme' tab click the one your using,
Click 'Customize',
Then in the 'Icons' tab click on the folders till you find the one you like.

And that's..!

If you want to take it a bit further, click the 'Controls' tab and go through the options in there till you find one you like too!

---

### Post by Dennis N on 2012-01-29
Glad you got it sorted out. Nice, isn't it, how customizable the old Gnome 2 desktop environment is.

---

### Post by Jamie_Edwards on 2012-01-29
Aye, very true. Although it's not so with Gnome3 from what I've heard?

Also I think I edited the original file will it get overridden if the theme is updated? If it will how do I make a copy of the file and make gnome use that copy?

---

### Post by Dennis N on 2012-01-29
Forgot to mention, there is an tool called Gnome Color Chooser that can do a lot of color and some other customization. Very nice. Don't know if it's available and works in 11.04 or not. Designed for gnome 2.

---

### Post by Dennis N on 2012-01-29
> **Jamie_Edwards said:**
> Aye, very true. Although it's not so with Gnome3 from what I've heard?

Also I think I edited the original file will it get overridden if the theme is updated? If it will how do I make a copy of the file and make gnome use that copy?

There is a 'Save As' button on the Themes tab in the Appearances Dialog. That will save it with a different name of your choice into your ~/.themes folder. Suggest you use something similar, such as 'my-ambiance'. It also shows up with this new name in your Appearances > Theme Tab. The original Ambiance is still in there also, unchanged.

---

### Post by Jamie_Edwards on 2012-01-29
Thanks, and I found the GNOME color chooser app, and have changed the colour of the sub menu to how I like, I'm trying to figure out how to make that sub menu transparent too XD

---

