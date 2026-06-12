---
title: "How to install wallpaper tray on 10.04"
date: 2010-07-20
forum: Desktop Environments
---

### Post by kuriharu on 2010-07-20
I did a fresh install of 10.04 x64 on my laptop. I used to run wallpaper-tray (wp-tray) and it worked perfectly. Now it seems to have been removed from 10.04. I've read some posts that some people have installed it somehow, but I can't. It keeps being listed as not in my repositories.

Any clues?

---

### Post by irw on 2010-07-21
Is Desktop Drapes what you are looking for?
```
sudo apt-get install drapes
```wallpaper-tray

---

### Post by kuriharu on 2010-07-21
Hi IRW,

I think Drapes didn't work. If memory serves me right, I have to choose individual pictures, not a directory. I have all of my pics in one directory; my photos, graphics, political cartoons, etc. But Drapes wanted me to choose individual pictures if memory serves me right. This is really tedious and stupid, so I ditched it.

I'm using Wally right now which works well but has 3 drawbacks that Wallpaper tray did not. First, if I rolled over the wallpaper tray icon, it told me the directory and name of the picture. This is helpful since I have tens of thousands of files there and I don't always remember which folder each pic is in. Second, Wally makes a copy of pictures while it displays them. It has a cache which stops at 200 MB so it's not a major issue, but still, that strikes me as silly (just display the damn picture!) And finally, I could easily delete pictures using WPtray but I can't do that with Wally.

I guess upgrading means not getting to use the software you want to use sometimes. Ugh.

---

### Post by hansdown on 2010-07-21
Hi kuriharu.

Walpaper tray was dropped in 10.04, but good news!

An older version is said to work.

[http://ubuntuforums.org/showthread.php?t=1497421](http://ubuntuforums.org/showthread.php?t=1497421)

Thanks go to, autocrosser.

---

### Post by kuriharu on 2010-07-21
BIG thanks to you and autocrosser for this!!!!!

---

### Post by irw on 2010-07-22
It sounds like you have found the answer you were looking for, but for information for others:

> **kuriharu said:**
> I think Drapes didn't work. If memory serves me right, I have to choose individual pictures, not a directory. I have all of my pics in one directory; my photos, graphics, political cartoons, etc. But Drapes wanted me to choose individual pictures if memory serves me right. This is really tedious and stupid, so I ditched it.

I don't know about previous versions, but the one I installed from the repos yesterday would work OK for you:
To initially select the pictures in a directory, you can select individual ones, but you can also press Ctrl-A to select all, and it loads them.
You can also tell it to watch the directory for new pictures automatically.

As far as the drawbacks with Wally, I don't know for Drapes - I am not using it. (yet another start-up app to slow me down, and I don't really need - I'm trying to go on a diet with all these things!)

---

### Post by kuriharu on 2010-07-22
> **irw said:**
> 
To initially select the pictures in a directory, you can select individual ones, but you can also press Ctrl-A to select all, and it loads them.
You can also tell it to watch the directory for new pictures automatically.

As far as the drawbacks with Wally, I don't know for Drapes - I am not using it. (yet another start-up app to slow me down, and I don't really need - I'm trying to go on a diet with all these things!)

I should have tried that! ARRGGGGH!! Oh well, I guess I just sort of panicked when it didn't work the way I expected it to. I feel foolish now. Thanks for the tip.

You're right, I probably should "diet" on these things, too. But things like this really are pretty cool....

---

