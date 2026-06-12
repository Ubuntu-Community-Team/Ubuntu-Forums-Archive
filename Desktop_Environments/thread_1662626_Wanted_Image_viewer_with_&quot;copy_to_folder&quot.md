---
title: "Wanted: Image viewer with &quot;copy to folder&quot; shortcut"
date: 2011-01-08
forum: Desktop Environments
---

### Post by mogliii on 2011-01-08
Hi,

I have tried

[LIST]
[*]Shotwell
[*]gThumb
[*]F-Spot
[/LIST]

None of them has the possibility to define a shortcut which will move current picture to a defined folder.

I want to get a collection of pictures to send to a friend. Before that I want to resize using imagemagick.

Irfanview allows definition of locations for "Copy to" or "Move to" (F8 shows list of predefined locations, press 0-9 for copy. So effectively two key strokes). Does anyone know about an ubuntu image viewer that makes this possible with one key combination?

Shotwell has publish to Picasa etc., but not publish to folder :(

---

### Post by Tamlynmac on 2011-01-09
Have you checked out [XnView]("http://www.xnview.com/en/index.html")?

Good Luck & hope this helps

---

### Post by nothingspecial on 2011-01-10
If you want to go through your photos and save a copy of the ones you like to a folder, and you don`t mind the cli, try feh.

```
feh -rF ~/Photos
```

This assumes the photos are in ~/Photos.

The -r option will let feh look through all the folders and sub folders

The F option displays each image fullscreen

Move to the next one with the spacebar or arrow keys

When you find one you like just press S and it will save it in the directory you launched feh from.

So when I get back from a holiday or wedding or whatever, I do
```

mkdir holiay_pics
cd holiday_pics
feh -rF /path/to/all/of/them 
```

When I get to the end, a copy of all the good ones are in holiday_pics which I can then upload to my favourite photo printing service.

There are tons of other options
```

man feh
```

---

