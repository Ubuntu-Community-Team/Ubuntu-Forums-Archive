---
title: "Folding screen? Dont know how to describe it..."
date: 2009-06-08
forum: General Help
---

### Post by garrettcrowlone on 2009-06-08
):PHi everyone. I don't know what all I'm doing in ubuntu because I've only used windows and mac operating systems. I had a cd of ubuntu 5 and liked it and noticed it was outdated... Everything worked. I installed the newest version January Jackelope I believe it was called (crazy names btw). Anyway, It's like someone had folded the screen. Where the midle part isn't shown. And on the other side of the part that is folded over is the also the left part of the screen? O.o So, I was like ok. It doesn't work. So I installed the version before that. (whatever version 8 is called) Same problem. Then, I thought one last try and installed version 9 xumbuntu (or whatever it's called. xD) and it has the same problem. If you are thinking its the monitor itself I disagree. 5 worked fine and when its booting the text is in the middle of the screen etc. I tried searching for "screen" (because I don't know what to search for) and couldn't find anyone... I would give you a snap of it but the snapshot looks normal... so I'm going to try to draw it with text... (sorry)
 
_____________________
|xxxxxxx|xxxxxxx|xxxxxxx|
|xmxxxx |xxxxxxx|xmxxxx |
|xxxxxxx|xxxxxxx|xxxxxxx|
|xxxxxxx|xxxxxxx|xxxxxxx|
|xxxxxxx|xxxxxxx|xxxxxxx|
|xxxxxxx|xxxxxxx|xxxxxxx|
|xxxxxxx|xxxxxxx|xxxxxxx|
---------------------------------
 
Hopefully you can see what I'm trying to say. -.- "M" stands for mouse cursor when it is on the left part of the screen... Like I said its like someone took and folded it over to the left. The middle section is actually the right side of the screen. The middle seems to be gone. The "x" is empty space. The forum automatically changed it to one space when I tried to do it that way (sorry). I hope I've done a good job trying to explain it. Any help would be appreciated. ^^ (oh if this is in the wrong section or it's already been answered, forgive me. T_T)

---

### Post by QIII on 2009-06-09
You must have used the Royal Fizbin option on install.  (Old Star Trek episode).

Is there any way you could post a screenshot (even if it seems to show a normal desktop), if you can get to it?

Applications -> Accessories -> Take a Screenshot.

Save it to your desktop (if you can see it!)

In your post, use the attachment button above (the paperclip) and use the tool to browse to your desktop post the image.

---

### Post by spillin_dylan on 2009-06-09
Can you see any of the menus on the screen?  I had a similar problem to this, (I think, based on the description) and I found that for some reason Ubuntu detected my monitor at 1600x1200 at 75Hz!  If you can adjust either the resolution or the refresh rate down to something a little more mellow, (say maybe 1024x768-60Hz?) that might help.  For me changing this setting fixed this issue, and the screen came up properly.

The remaining problem is that it still defaults back to 75Hz every time I restart X.  

I think this has something to do with the xorg.conf file, but I haven't figured mine out just yet....   :(

---

### Post by garrettcrowlone on 2009-06-09
K here is the screenshot. as you can see it looks normal. I only have two options for changing resolution and both options and refresh rates don't help... I should have mentioned that before. :o

---

### Post by garrettcrowlone on 2009-06-11
Oh, I might as well put this up... The computer stuffs... Pentium 3, 256 ram, Dell Latitude Laptop.

And in case my description was confusing. I edited the screenshot with paint to make it look somewhat like what it is. xD

Looks something like this:

---

### Post by Frenziefrenz on 2009-06-11
My old laptop with an Ati Radeon 9600 Mobility used to have that same issue in Ubuntu 5 and 6 (and possibly 7?). Did you upgrade from Ubuntu 5 or did you burn a new Ubuntu 9 CD? In the first case there might be some lingering old config files causing troubles.

---

### Post by garrettcrowlone on 2009-06-11
I burned a 9 cd, then tried 8, and now have xumbuntu or whatever 9. I didn't upgrade from 5 or any of em. Burned new cds for all of em. :)

---

### Post by garrettcrowlone on 2009-06-15
Anyone else have any ideas? O.o

---

### Post by garrettcrowlone on 2009-06-17
Maybe its because this forum is so huge or no one really understands ubuntu? Well, I'll give up and go to Windows XP soon.  I'll check back now and then... -.-

---

### Post by garrettcrowlone on 2009-06-22
T_T  Ubuntu 5 can't download anything. Someone please help! I'll end up having a comp with nothing on it. Someone help me figure this out.

---

### Post by StOlEnDeStInY on 2009-06-23
Is the screen fine with Ubuntu 5? What error is it giving while downloading stuff?

---

### Post by garrettcrowlone on 2009-06-26
Basically it works fine with ubuntu 5. I just downloaded 6 and 7 to see if they work. 8 and 9 have the screen problem. no error messages appear.

---

### Post by themusicalduck on 2009-06-26
Not sure if you've done this already.. but perhaps there are some graphics drivers that need to be installed? If you can see well enough to look under System > Administration > Hardware drivers (in Ubuntu, might be different in Xubuntu) and see if anything is listed there.

---

### Post by t4thfavor on 2009-06-26
Sure sounds to me like a resolution/refresh rate issue, if you can navigate to the appropriate (I have nvidia, so I don't remember where it is) place, and change the refresh rate it might help you. Also if you have an ATI video card you may as well not even try as ATI's drivers are all messed up at the moment.

---

### Post by garrettcrowlone on 2009-06-27
It does not have ATI and I've tried changing the resolution. I just burned ubuntu 6 and 7. So, now the only one that even works is 5. All the rest have this issue with my machine. I'm gonna try doing what you said about hardware. Thanks for the suggestion I hope it works.

---

### Post by garrettcrowlone on 2009-06-28
Ok. I looked into the system hardware thing and it had nothing listed. What now? :o I decided to take a pic of it with my camera.

---

### Post by garrettcrowlone on 2009-07-01
So I play around with it. I try to play yu-gi-oh abridged on it. I acidentally double click and it goes to fullscreen, and it works! O.o  When it plays a vid in fullscreen there is no problems. But when I exit out it goes back to the way it was before. So, maybe that new info might help find a solution? xD

---

### Post by Flying caveman on 2009-07-01
In your workplace switcher, I would try to select the "show only current workspace" button or just make one desktop to see if it makes a difference.

---

### Post by ad_267 on 2009-07-01
What video card do you have?

---

### Post by garrettcrowlone on 2009-07-06
As for the workspace... It crossed my mind. It is not the issue. I swaped workspaces, didn't do anything. I turned number of workspaces to one, same problem.

Video? Not sure. It's an old laptop. I think I put what I know about what it has in a previous post. Could a lack of video card be a problem? (I'm not sure if mine has one or not)

---

### Post by Jackelope on 2009-08-29
Just a thought...

Are you running compiz-fusion? It may be autostarting on some newer versions of Ubuntu and causing trouble. Its a shot in the dark, but look in "appearance" on the desktop effects tab and see if you're using desktop effects. That's underGnome, anway. If you're running Xubuntu, it might be in a different place.

---

