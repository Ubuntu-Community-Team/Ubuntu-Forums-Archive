---
title: "Metacity takes ages to load"
date: 2005-06-12
forum: Desktop Environments
---

### Post by andrewsawyer on 2005-06-12
Hiya,

I've done something, although I'm not sure what, and not Metacity takes about 3 minutes to load each time I do a reboot.  The only thing that I can think that I might have done it to change around the panels a bit.  I created a new one, and put quicklinks, desktoplinks, the trash can and the button to view the desktop on it.  I then moved everything else from the bottom panel up to the top one. I deleted the bottom one and replaced it with my new one, with a size of 35px, centred in the midle with autohide (so it looks a bit like the quick launch bar in Mac OSX).

I would really appreciate if someone could let me know whether this might have caused the problem, and also if you could tell me how to fix it I would be most grateful.

I have attached an image of my desktop so people can get an idea of what I have done.

To recap, when booting, and when the GUI is first loaded and it plays the little tune, it hangs on the second icon (Metacity) for about three minutes.

Many thanks to anyone that can help.

Andy

---

### Post by bahumbug on 2005-06-12
Mine does that too, but i added some startup apps. specifically devilspie and Eterm.  But if you just click on it the startup "splash" thingie will go away and if you open an app like firefox or something, everything should be fine.

There's probably a more elegant way to make everything load up, but for now, the above works fine for me.

PEACE  :neutral:

---

### Post by andrewsawyer on 2005-06-12
What would you know - it seems to have rectified itself.  I have no idea what happened - it was working fine, then real slow boot for like 4 or 5 times, then now its back to normal.

I was running it on the campus network at uni rather than at home.  Could have been the reason.  Sorry to be a pain!

---

### Post by bjorn on 2005-06-12
How did you change the gnome foot icon to the ubuntu icon next to the applications menu?

---

### Post by andrewsawyer on 2005-06-12
bjorn: [http://www.ubuntuforums.org/showthread.php?t=26854](http://www.ubuntuforums.org/showthread.php?t=26854)

Looks good doesn't it!

---

### Post by thieumf on 2005-06-18
I have exactly the same problem, but I only have one app to load at startup...
I don't have the least idea of what made metacity take so long to load, and once gnome is launched, any manipulation of windows (displacement, openings,...) is very slow....

Anyone a clue ?

---

### Post by arrizaba on 2005-06-27
I have the same problem with metacity, it takes about 3-4 minutes to load. i cannot start any app in the meantime  :-? 
It has happened about 20 times, and it does not correct by itself (unlike andrewsawyer)
Does anyone knows how to fix this problem? Or should i remove metacity?

---

### Post by derrick1985 on 2005-06-27
[QUOTE=andrewsawyer]bjorn: [http://www.ubuntuforums.org/showthread.php?t=26854](http://www.ubuntuforums.org/showthread.php?t=26854)

Looks good doesn't it![/QUOTE]

Thanks, that does look sweeter. 

Now, lets see about a custom one...

---

### Post by arrizaba on 2005-07-04
Well, I think we should try to solve the problem at hand, namely "[COLOR=Olive]metacity takes ages to load[/COLOR]". This might be of some use to other people as well.
I've been googling a bit and found that the problem seems to be triggered by clicking on "save session" before log out. I remember doing that just before the problem appeared. Can you guys confirm this?

I found this overlapping forum, from the Hoary development (closed). This might be of some help:

[PHP]http://ubuntuforums.org/archive/index.php/t-14959.html[/PHP]

---

### Post by arrizaba on 2005-07-04
Andrewsawyer, what exactly did you do so the problem was fixed after 4-5 times?
It would be very enlightning if you could say precisely what you did (if you remember)?

---

### Post by arrizaba on 2005-07-11
OK, I figured out a quick and dirty method to make it work:

just erase (or better rename) the file [COLOR=DarkSlateBlue]~/.gnome2/session[/COLOR] from your home directory. Metacity loads fast again.

---

