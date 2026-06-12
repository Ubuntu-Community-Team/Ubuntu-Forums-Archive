---
title: "Screensaver gets the screen 'blanked'"
date: 2009-04-14
forum: Desktop Environments
---

### Post by Intrepid Ibex on 2009-04-14
Hello,

I have this issue with my very old laptop (Xubuntu 8.10 with LXDE). 
Yesterday I decided configured my screensavers, because I was annoyed with the old one.
So I went to Settings -> Screensaver and randomly selected a screensaver but unfortunately this particular screensaver was too good for my graphics card, so that when I clicked it, my screen turned blank :-k (black) and it takes hours for my grapchis card to finish that screensaver (though the screen is blank all that time).

The problem is that somehow the screensaver was applied and now every time that screensaver starts up, my screen turns blank and I have to reboot, if I don't happend to have 6 hours of time to wait.

So how to disable this through terminal?

---

### Post by Intrepid Ibex on 2009-04-15
BUMP!

*Why are **MY** issues always so difficult to answer ](*,)*

---

### Post by gali98 on 2009-04-15
Edit: Look Below!

This is only a guess.. But I'm pretty sure it will work.
Press Alt+F2 to open up a "run" dialog. Type in
```
gconf-editor
```
Then go to /apps/gnome-screensaver
In the entries first find the one called "Mode"
Double click on it. It should show the value as some screensaver name.
Change it to ```
blank-only
```
Now go down a bit and find the entry called "themes" (Make sure you do the one with the s)
Double click on it, and there should be a bunch of entries listed. Click on each one then remove it. Remove all of them.
Then I suggest you reboot just to make sure it takes effect.
Hopefully that will fix everything.
Kory

Edit: Look Below!

---

### Post by gali98 on 2009-04-15
Oh nice... I just now realized that you're on Xubuntu.. That won't work :(
Um Try
```
http://forum.xfce.org/index.php?topic=3332.msg13918#msg13918
```
look for an option named screensaver.
and here is a link that might work if that doesn't:
[http://forum.xfce.org/index.php?topic=3332.msg13918#msg13918](http://forum.xfce.org/index.php?topic=3332.msg13918#msg13918)
Hope that helps... 
Kory

---

### Post by Intrepid Ibex on 2009-04-21
Well that was not what I was looking for. I was just looking for to disable the annoying screensaver (Voronoi or whatever it was). Solved it with this tutorial: [http://www.jwz.org/xscreensaver/man1.html](http://www.jwz.org/xscreensaver/man1.html)

**E:** didn't you read the title :D? 
> **[COLOR="DarkOrange"][xubuntu][/COLOR] Screensaver gets the screen 'blanked'**

**E 2:** Why do you people think that post count says how newbie you are? I'm not a newbie =;!

---

