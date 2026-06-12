---
title: "Changing the desktop background in Ubuntu 12.4"
date: 2012-08-30
forum: Desktop Environments
---

### Post by merzik on 2012-08-30
I just installed Ubuntu 12.4 and can't figure out for the life of me how to change the desktop background to one of my pictures. I am to the point where I think that maybe something is not working right. Here is what I did (following logic and then confirming this with an ubuntu 12.4 help page).
1) Right click on desktop, choose "Change desktop background". 
2) Click on a picture in Wallpapers. That works fine. But I want to use one of my own.
3) Click on Wallpapers, choose "Pictures Folder"
4) Click on the + sign. This opens /home/myname/Pictures
5) Pick a picture that I have placed there
6) Click "open".

Nothing happens.

I can try the above again, this time clicking the + sign from "Wallpapers". Nothing happens either.

I have thought of a workaround, but I can't implement it because I can't find the folder where the default images are stored. If I could place my pictures there, my hope is that they would show up along the default images in Wallpaper and then I could use mine.

Where are the default Wallpaper images?

---

### Post by leosubhadeep on 2012-08-30
Why don't you download some cool images to the ~/home/[your name]/Pictures/ folder and consider using them as your desktop background?

---

### Post by coffeecat on 2012-08-30
@merzik, I'm puzzled because what you describe is the way to change your wallpaper with an image in the ~/Pictures folder, and it works in my 12.04 installation. 

Anyway, to answer your question, the default wallpapers are stored in /usr/share/backgrounds. Unfortunately, what you suggest didn't work when I tried it - the wallpaper I added to that folder didn't show up in the default set of backgrounds. I was, however, able to set my image as wallpaper from the backgrounds folder by clicking on + and navigating to /usr/share/backgrounds. After clicking on open my selected image became the wallpaper, but the appearance window told me it was in the Pictures Folder, which is odd.

---

### Post by Frogs Hair on 2012-08-30
In order to add backgrounds manually to usr/share/backgrounds in 12.04 the creation of an .xml file and folder is required. Look at the one included with the default wallpapers if you feel ambitious. I don't know why the pictures folder is not working. ???

---

### Post by merzik on 2012-08-31
Like I thought, my installation is buggy. I looked around other threads and tried installing wallch. That did the trick. As a bonus, it does a slide show of the images. I like that. 

[http://www.liberiangeek.net/2011/09/automatically-change-wallpaper-with-wallch-in-ubuntu-11-0411-10/](http://www.liberiangeek.net/2011/09/automatically-change-wallpaper-with-wallch-in-ubuntu-11-0411-10/)

---

