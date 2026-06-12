---
title: "Desktop Icons disappear and Nautilus Closes"
date: 2009-05-17
forum: Desktop Environments
---

### Post by jrox717 on 2009-05-17
Hey all,

I upgraded to 9.04 yesterday, and it's been working great, except for one thing. It started when I opened a certain folder on my desktop and after maybe two seconds nautilus shut down, and the icons on my desktop disappeared. My background picture was still there but I couldn't click on the background (make the boxes when you click and drag on the desktop). I could still work with programs however, and I could reopen Nautilus from the panel. When I logged out and back in the screen was back to normal, but it happened again consistently with that directory.

I isolated the problem and I found out that it happened when the folder contained one of three files. According to the "file" command they are JPEG 2000 image data. 

I don't need the files, but I'd like to find out what's going on. Does anyone have a clue? Thank you!

PS I don't know if this matters but I have a Compaq Presario V3000 laptop and a nvidta graphics driver.

---

### Post by jrox717 on 2009-05-18
bump?

---

### Post by disturbed1 on 2009-05-19
One of the jpegs could be corrupt, or Nautilus thinks it is corrupt. 

Start with deleting the thumb cache. Use the forum search or google if you don't know where those are. .local, .share - it's in one of those directories inside $HOME.

Once the thumbnail cache is deleted, reopen the troubled directory with Nautilus. If it crashes again, attempt to open the jpeg file with eog (Eye Of Gnome) or some other image viewing app. 

If the troubled jpg can be opened with an image viewer, we know it's a bug with Nautilus's thumbnailer. Create a bug report on Launchpad and attach the jpg in question.

If the troubled jpg also causes the image viewer(s) to crash - you have a corrupt jpeg. Trash it and move on :)

---

### Post by jrox717 on 2009-05-19
I did what you suggested and the program crashed, so I guess the jpeg was corrupt. Thanks a lot!!

---

