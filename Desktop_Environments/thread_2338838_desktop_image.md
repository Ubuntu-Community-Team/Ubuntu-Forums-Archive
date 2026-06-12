---
title: "desktop image"
date: 2016-10-02
forum: Desktop Environments
---

### Post by realmainer on 2016-10-02
When I put a custom image on my desktop  when I start my computer the next day it is gone back to what was there when I bought it how do I get it to stay?

---

### Post by Frogs Hair on 2016-10-02
Moved to *Desktop Environments. *

---

### Post by ajgreeny on 2016-10-02
What DE do you have and on which version of *ubuntu?
Where is the image that you want to use as your wallpaper and what image type is it?

---

### Post by realmainer on 2016-10-03
I have ubuntu version the image is from my file and a jpeg

---

### Post by howefield on 2016-10-03
Can you explain what you did to get the image to your desktop, right clicking the desktop and selecting Change Background, then selecting one of the default backgrounds or navigating to one of your own should be enough.

If you have used one of your own and later moved or deleted the image, it won't appear on the desktop.

---

### Post by Bucky Ball on 2016-10-03
Sounds like the partition your desktop image is on is not being mounted at boot. When you click the folder it is in, does the wallpaper also come up?

---

### Post by realmainer on 2016-10-03
I get the image from my folder on my computer I just moved it to my document and will see if it works

---

### Post by tea for one on 2016-10-03
> **realmainer said:**
> I get the image from my folder on my computer I just moved it to my document and will see if it works

In order to use an image as wallpaper, you have to store it in the Pictures folder of your home directory.

---

### Post by howefield on 2016-10-03
> **tea for one said:**
> In order to use an image as wallpaper, you have to store it in the Pictures folder of your home directory.

Not exactly, right click on a picture anywhere on a mounted file system and select *Set as Wallpaper*.

---

### Post by tea for one on 2016-10-03
> **howefield said:**
> Not exactly, right click on a picture anywhere on a mounted file system and select *Set as Wallpaper*.

Is that a newish (Nautilus) feature? I'm sure that years ago the image had to be in the Pictures folder? 

Anyway, thanks for the tip.

When one is a satisfied Ubuntu user and all personal settings constantly work OK, these newer features are often missed.

I'm sure the OP will use your latest advice.

Cheers

---

### Post by howefield on 2016-10-03
> **tea for one said:**
> Is that a newish (Nautilus) feature? I'm sure that years ago the image had to be in the Pictures folder? 

Not particularly new as far as I can remember. You can also right click an image in Firefox and set as desktop background. I'm sure both have been around a long time.

> I'm sure the OP will use your latest advice.

As alluded to above, could simply be that the image is in a folder that resides on an unmounted partition.

---

### Post by realmainer on 2016-10-04
Thanks to all I got it to stay there

---

### Post by deadflowr on 2016-10-04
As of at least 16.04 maybe even 14.04, any image anywhere invoked as the wallpaper will get a clean copy placed in a Wallpapers folder in the Pictures folder.
So even if you have an image in an external partition or other place, a copy is made so the image will always get opened, regardless of where originally it came from.

---

