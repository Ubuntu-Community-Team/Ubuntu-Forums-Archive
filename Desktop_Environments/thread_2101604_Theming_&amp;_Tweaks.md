---
title: "Theming &amp; Tweaks"
date: 2013-01-05
forum: Desktop Environments
---

### Post by bman on 2013-01-05
I am trying to get this theme installed.

[http://gnome-look.org/content/show.php?content=148398](http://gnome-look.org/content/show.php?content=148398)

I copied the content into the folder, but nothing happened.

Also, there was a sudo apt-get install command (i forget what it is now), but that couldn't find the package.

Anyone know how I can install this theme?

Ubuntu 12.04, Unity.

Also, I saw in a few different screenshots, that the people have there devices/mounted drives in nautilus on the bottom instead of the top. How do I accomplish this?

---

### Post by Frogs Hair on 2013-01-05
The apt-get install command won't work unless you are trying to install the theme via a PPA repository which includes that theme. 

I have had that theme installed and there is more than one theme in the folder. Extract the individual themes from the parent folder before moving them to .themes of usr/share/themes.

To use the second location which will make the themes available to all users use the following in the terminal. ```
gksudo nautilus 
```

---

### Post by Frogs Hair on 2013-01-05
Below is a themes PPA.

```
sudo add-apt-repository ppa:webupd8team/themes
```  ```
sudo apt-get update
``` ```
sudo apt-get install mediterraneannight-gtk-theme
```

Source: [http://www.webupd8.org/2012/12/2-beautiful-dark-themes-for-gtk-36-or.html](http://www.webupd8.org/2012/12/2-beautiful-dark-themes-for-gtk-36-or.html)

---

### Post by bman on 2013-01-05
Awesome that worked like a charm.

My second question?

---

### Post by Frogs Hair on 2013-01-05
I have not tried to change the order of the mounted drives and have no way of knowing what version of Nautilus was in use in the screen-shots. Nautilus features have changed in the last few versions.

---

### Post by sigurnjak on 2013-01-06
I believe screenshots you are mentioning are 12.10 .

---

### Post by Frogs Hair on 2013-01-06
I am unable to drag and drop side pane items in 12.10 . I had done this in earlier versions of Nautilus at least with folders.

---

### Post by bman on 2013-01-06
Oh well, that is too bad. 

Wasen't all that important, just interesting.

---

