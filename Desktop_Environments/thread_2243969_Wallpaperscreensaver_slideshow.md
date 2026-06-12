---
title: "Wallpaper/screensaver slideshow"
date: 2014-09-12
forum: Desktop Environments
---

### Post by malcolm8 on 2014-09-12
One of the few good things in later versions of Windows was the feature where you set your wallpaper and screensaver to show a picture slideshow.

Does anyone know of any software available to do this in Ubuntu (14.04.1) ?

Thanks.

---

### Post by TheFu on 2014-09-12
I use this in a crontab - that means the image can only change in 1 min intervals:
```
#!/usr/bin/env perl

my @files=`ls -1 ~/Pictures/Best/*g`;

# pick a random file
my $bg = $files[rand @files];

`env DISPLAY=:0 /usr/bin/feh  --bg-scale $bg` ;

```

Of course, you could add a sleep() function, looping and not use a random list of images, if you wanted to control those aspects.

---

### Post by mcduck on 2014-09-14
Gnome has a built-in support for image slideshow wallpapers, but for some reason doesn't come with any tool for creating them. (For example each Ubuntu release comes with a bunch of wallpapers, plus one slideshow usign all of them).

If you go and lok at the system wallpapers folder you'll find out that the slideshow wallpaper is actually just a .xml file, listign all images and transition times between them. So it's not really that difficult to create one yourself usign a text editor (if I remember right the tmes are in seconds, and sicne you can set teh "start" time you can also create slow slideshows that change your wallpaper based on the tiem of the day...).

I suppose there must be some graphical tool around for creatign and configuring them as well...

---

### Post by WB0HYQ on 2014-09-16
What about Variety?  Wouldn't that do well for a slideshow/screensaver?  I use it under Ubuntu 14.04 and Xubuntu 14.04.

Bill

---

