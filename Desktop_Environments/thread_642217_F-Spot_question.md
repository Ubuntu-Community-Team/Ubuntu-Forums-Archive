---
title: "F-Spot question"
date: 2007-12-16
forum: Desktop Environments
---

### Post by peterthewolf on 2007-12-16
Very basic - where does fspot store the photos I can see them in fspot but cannot find them anywhere:confused:

---

### Post by CanonKen on 2007-12-16
In the G-spot, never found that either :)

Sorry, couldn't resist that one, I'd help if I could but I have never used it

---

### Post by catach on 2007-12-16
Your imported pictures should be deep in the Photos directory. 
/home/<username>/Photos

Alternatively, you should be able to right-click on any photo in F-Spot, and the top menu entry will place that picture's location on to the clipboard.

---

### Post by peterthewolf on 2007-12-16
Two more useless answers I have never seen but at least the first was trying to be funny.

---

### Post by catach on 2007-12-16
Nice snark--but unless your install of F-Spot is broken somehow, I can't think of another possible interpretation of your original question. Clairify?

---

### Post by peterthewolf on 2007-12-17
F-Spot shows the impotred photos. Now the first is shown having a label 00049.jpg I cannot find a file with that label anywhere on the system.
I found elsewhere that F-Spot stores all the photos in an encoded database which ubuntu wont read.

Ideally what I want is a photo manager that stores the photos in ordinary file structures.

---

### Post by catach on 2007-12-17
> I found elsewhere that F-Spot stores all the photos in an encoded database which ubuntu wont read.The F-Spot devs [disagree](http://f-spot.org/User_Guide/Organize) with that: [quote=f-spot.org]By default, F-Spot copies your photos to the ~/Photos folder. You can change the folder F-Spot uses in Preferences dialog (Edit » Preferences).[/quote]

Are you sure you're looking in the Photos directory instead of Pictures?

---

### Post by peterthewolf on 2007-12-17
In F-Spot I have 15 photos, in Photos there is nothing.
I can find no trace of the individual jpgs and presume F_Spot is keeping them in /peter/.gnome2/f-spot/photos.db but I cannot read that file.

---

### Post by catach on 2007-12-17
Have you tried, from F-Spot, opening up an image in another program? (right click>Open With>) Doing so you should be able to find out the path. 

Is the size of photos.db consistent with what you'd expect from 15 photos?

Have you tried File>Export>Export to Folder?

---

### Post by peterthewolf on 2007-12-17
When I select a photo and choose export to folder it says it cannot find the photo in Photos. I think I shall have to delete F-Spot and reinstall.

---

### Post by catach on 2007-12-17
Yikes. 

I'd advise checking out digiKam. It seems more mature than F-Spot.

---

