---
title: "plz show me some ways to optimize the font display in ubuntu"
date: 2004-11-16
forum: Desktop Environments
---

### Post by kixvn on 2004-11-16
I installed Ubuntu for a while and really like it, just this (and also the problem on some other linux distros i've installed), that's the font displayed so bad .. compare to that with windows (cleartype turned on, since i use laptop)

i already chose "subpixel smoothing (LCD)" in the "font options" , the more detail is (smoothing : subpixel, hinting : full, subpixel order : RGB, resolution : 96)

i also copy all the fonts under C:\Windows\Fonts to ///fonts (use GNOME), to display the unicode character correctly in my browser

but, the font the desktop and the font in browser (firefox) looks fine but not really nice as those with Windows,
i attach the screenshot, can u tell me that's the most i can get, or any other steps that i can do ?

thanks

screenshot
[http://sim.gate4vn.net/share/font.jpg](http://sim.gate4vn.net/share/font.jpg)

---

### Post by Crisp on 2004-11-16
It looks fine to me, but perhaps that's just because I'm used to those font's now.  I remember the first time I used Linux, one of the first things I thought was "those fonts are nasty" but they have come on a bit since then.  Even so, if it causes you a lot of distress, I think I heard of a project that emulates Windows fonts, it shouldn't be too hard to find with Google.

-Crisp

---

### Post by ~zoey~ on 2004-11-16
There is a thread in the 'How To' section of this forum titled 'Make your fonts smooth enough to drool over.  You might want to check it out!

zoey  :smile:

---

### Post by kixvn on 2004-11-16
[QUOTE=~zoey~]There is a thread in the 'How To' section of this forum titled 'Make your fonts smooth enough to drool over.  You might want to check it out!

zoey  :smile:[/QUOTE]
 I did that (which is to enable the hinting option), and things look the same .. someone stated in that thread that it's already enabled in hoary (i use hoary array 1 now .. )
thanks 4 all the suggestion, any else ? :)

---

### Post by Magneto on 2004-11-16
[QUOTE=kixvn]I did that (which is to enable the hinting option), and things look the same .. someone stated in that thread that it's already enabled in hoary (i use hoary array 1 now .. )
thanks 4 all the suggestion, any else ? :)[/QUOTE]
 try setting up TrueType Fonts

There's a font howto in the howto section.  The appearance of fonts in X have surpassed Windows XP/2000/2003 Cleartype for the past 2 years when configured correctly.

---

### Post by kixvn on 2004-11-16
[QUOTE=Magneto]try setting up TrueType Fonts

There's a font howto in the howto section.  The appearance of fonts in X have surpassed Windows XP/2000/2003 Cleartype for the past 2 years when configured correctly.[/QUOTE]
 >  when configured correctly.

that's the point man .. :) but i will try the howto section, tks :D

---

### Post by Magneto on 2004-11-16
[QUOTE=kixvn]that's the point man .. :) but i will try the howto section, tks :D[/QUOTE]
 :) sorry i thought it was in there but it wasnt 

do this

[http://www.paulandlesley.org/linux/xfree4_tt.html](http://www.paulandlesley.org/linux/xfree4_tt.html)

I had to do the same in slackware before.

---

### Post by adbak on 2004-11-16
There's a package in apt-get that you can download that gives you all the Windows fonts.  I'd look it up, but I'm not using Ubuntu right now (or Linux for that matter).  Search for "ms" and something should come up.

---

### Post by Magneto on 2004-11-16
[QUOTE=adbak]There's a package in apt-get that you can download that gives you all the Windows fonts.  I'd look it up, but I'm not using Ubuntu right now (or Linux for that matter).  Search for "ms" and something should come up.[/QUOTE]
sudo apt-get install msttcorefonts is what you are referring to, but he basically did that already 

read the page on that link above or read this thread [http://www.ubuntuforums.org/showthread.php?t=4456](http://www.ubuntuforums.org/showthread.php?t=4456)

there is more to do besides installing the microsoft truetype fonts which is what he did by copying those fonts from windows

---

### Post by zabilcm on 2004-12-13
[QUOTE=kixvn]I installed Ubuntu for a while and really like it, just this (and also the problem on some other linux distros i've installed), that's the font displayed so bad .. compare to that with windows (cleartype turned on, since i use laptop)

i already chose "subpixel smoothing (LCD)" in the "font options" , the more detail is (smoothing : subpixel, hinting : full, subpixel order : RGB, resolution : 96)

i also copy all the fonts under C:\Windows\Fonts to ///fonts (use GNOME), to display the unicode character correctly in my browser

but, the font the desktop and the font in browser (firefox) looks fine but not really nice as those with Windows,
i attach the screenshot, can u tell me that's the most i can get, or any other steps that i can do ?

thanks

screenshot
[http://sim.gate4vn.net/share/font.jpg](http://sim.gate4vn.net/share/font.jpg)[/QUOTE]
 I did the following to improve the font quality.
**Beware, that the following steps involved the tweaking of XF86Config-4 file so take a back up.**
1) Check if the follwing line is available
	RgbPath		"/usr/X11R6/lib/X11/rgb"

---

### Post by zabilcm on 2004-12-13
I did the following to improve the font quality.
**Beware, that the following steps involved the tweaking of XF86Config-4 file so take a back up.**
1) Check if the following line is available in your XF86Config-4
	*RgbPath		"/usr/X11R6/lib/X11/rgb"*
        Under **"Section Files" **
        If not then manually add it.

2) Comment the following line
     *FontPath	"unix/:7100"*

3)  Under Section "Module"
     Comment  the line
     *Load	"xtt"*

4) Cross check the file /etc/fonts/local.conf to see if  the relevant lines are uncommented.

5) You will have to restart your machine to see the effects.

Hope it helps.

---

