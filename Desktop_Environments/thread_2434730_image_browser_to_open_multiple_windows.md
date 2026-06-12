---
title: "image browser to open multiple windows"
date: 2020-01-09
forum: Desktop Environments
---

### Post by holiday on 2020-01-09
I'm looking for an image browser that will open all the image files in a directory, each in its own simple window i.e. without sidebars or additional panes. 

I need to zoom in and out on each of these images.

Ideally I could put them into a cascade with a single action but never mind about that.

I've tried :

- Eye Of Gnome/MATE using --new-instance in a for loop:  but it opens a new window only when I close another.
- geeqie selecting all and then "open in new window":  but this opens only one window.
- gimp with a wild card:  but I haven't found a way of getting the windows out of the gimp 'workshop' -- if you know what I mean.
- ImageMajick with a wild card : but this opens only one window 

What else can I try?  

It seems like a very simple application -- which is perhaps the problem with it. Anyone putting time to an image browser is going to want to add features.

---

### Post by Frogs Hair on 2020-01-09
You could give [nomacs]("https://nomacs.org/") a try which will let you open multiple windows while in the same directory. 

```
sudo apt install nomacs
```

---

### Post by vanadium on 2020-01-10
[/quote] - Eye Of Gnome/MATE using --new-instance in a for loop: but it opens a new window only when I close another.[/quote]
Have each instance spawn in the backgroud by appending the command with ' &'.

---

### Post by holiday on 2020-01-10
Yes indeed. Thanks That's a nice little viewer. Do you know someway of setting the window size to the image size from the command line? I don't see anything like that in the man page.

---

### Post by holiday on 2020-01-10
> **vanadium said:**
>  - Eye Of Gnome/MATE using --new-instance in a for loop: but it opens a new window only when I close another.[/quote]
Have each instance spawn in the backgroud by appending the command with ' &'.[/QUOTE]

I had done that but there was an error about the placement of the '&'. This is the right way to do it:

   ```


   for f in *jpg;do eom -n $f & done;

  
```

I had been putting a second semicoln after the &. This command works very nicely.

---

