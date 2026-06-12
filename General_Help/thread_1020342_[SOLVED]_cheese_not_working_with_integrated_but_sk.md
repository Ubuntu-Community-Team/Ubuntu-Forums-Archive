---
title: "[SOLVED] cheese not working with integrated but skype does."
date: 2008-12-24
forum: General Help
---

### Post by andresmh on 2008-12-24
I am not able to get my built-in webcam to work with cheese but it works out of the box with Skype. 

After starting cheese the LED of the camera turns on but no image shows up. Then when pressing the "Take a photo" button cheese it goes through the 1-2-3 count down and it flashes but no picture is taken.

I've tried video as well and the same happens.

When running cheese from the command line and this is what happens:
$cheese 
```

** (cheese:31681): WARNING **: Cannot extract frame (0, 0) from the grid
** (cheese:31681): WARNING **: Cannot extract frame (36, 0) from the grid
** (cheese:31681): WARNING **: Cannot extract frame (72, 0) from the grid
** (cheese:31681): WARNING **: Cannot extract frame (108, 0) from the grid
** (cheese:31681): WARNING **: Cannot extract frame (144, 0) from the grid
** (cheese:31681): WARNING **: Cannot extract frame (180, 0) from the grid
** (cheese:31681): WARNING **: Cannot extract frame (216, 0) from the grid
** (cheese:31681): WARNING **: Cannot extract frame (252, 0) from the grid

```
At this point the LED of the webcam is on but then when I click on "Take a photo" nothing happens (see above).
Any suggestions?

---

### Post by andresmh on 2009-01-04
I found a way to solve it: [http://ubuntuforums.org/showthread.php?t=1025992](http://ubuntuforums.org/showthread.php?t=1025992)

---

### Post by faust99 on 2010-03-22
I had a similar problem with cheese in that it would not save the photos it took, thought the video would be saved. The reason was that I had set the permissions of the folder in which cheese saves photos (~/Photos/Webcam) as read only. Changing to read/write solved the problem.

---

