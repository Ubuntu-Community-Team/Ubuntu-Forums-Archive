---
title: "How To Delete Photo Uploaded Into Background &quot;Pictures&quot; — V. 18.04"
date: 2020-03-20
forum: Desktop Environments
---

### Post by Mel Thompson on 2020-03-20
As a low-skills user, I uploaded a picture by going to the "settings" icon, then selected "background." We were given two choices, to select a background for the "Background" or "Lock Screen." I again selected "Background." There were three buttons there: (Wallpapers) (Pictures) (Colors). I didn't prefer any of the preexisting wallpapers or colors at that time, so I selected (Pictures). But there were no pictures in there, so I dragged in two photos from my computer's desktop. Later, however, I decided to go with a simple dark blue from the (Colors) button. Now my computer has the dark blue background I selected. So far, so good. But later I decided I wanted to delete those two pictures I dragged in by going into the terminal. I successfully navigated to /usr/share/backgrounds in the terminal. Then I had it list all the files, and it listed all the image files behind the wallpaper button in the GUI. But it did not list the two photos I dragged into the (Pictures) area. Furthermore, no such directory as /usr/share/backgrounds/pictures shows up in Nautilus, even under root, or in the GUI with full permissions to see everything, even in all folders, even inside the operating system. And this holds true even when doing "Control H" to see hidden folders too. I'm surprised that I could drag the pictures in, but not out of the GUI area involving background pictures. In any case, since I don't like having files I'm not using on my machine, I'd like to delete those two pictures, but they don't show up in my main "Pictures" folder in the Nautilus GUI. (I understand why we can't navigate easily to the images in the (Colors) button, because they may not be actual static files like JPEGs or PNGs, etc. But I mystified as to why I can't seem to navigate to ordinary JPEGS anywhere in the system.

---

### Post by SeijiSensei on 2020-03-20
Open a terminal and run the command "locate name-of-the-image.jpg" or whatever it is called.  You'll see where it resides.

On my Kubuntu 19.10 machine, the background picture is installed in a "Local" directory under my home directory.  (Yes, it has a capital "L".  I did not create that directory; it must have been created when I designated the image to use as my desktop background.)

---

