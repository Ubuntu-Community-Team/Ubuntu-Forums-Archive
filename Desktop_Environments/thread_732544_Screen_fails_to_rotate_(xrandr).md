---
title: "Screen fails to rotate (xrandr)"
date: 2008-03-23
forum: Desktop Environments
---

### Post by Greg T. on 2008-03-23
I seem to have lost the ability to rotate my screen. (I prefer using my monitor in portrait mode.) Ominously, this seems to happen only sometimes, but is becoming increasingly common recently after it worked consistently for many months. I have been unable to even obtain an error message; everything seems like a go except for the fact that it just won't turn. The command:  

```
xrandr -o left --verbose
```

yields this:

 SZ:    Pixels          Physical       Refresh
*0   1920 x 1200   ( 508mm x 318mm )  *50   57  
 1   1600 x 1200   ( 508mm x 318mm )   51  
 2   1280 x 1024   ( 508mm x 318mm )   52   64  
 3   1152 x 864    ( 508mm x 318mm )   53  
 4   1024 x 768    ( 508mm x 318mm )   54   68   69  
 5    800 x 600    ( 508mm x 318mm )   55   73   74   75   76   77  
 6    640 x 480    ( 508mm x 318mm )   56   82   83   84  
 7   1680 x 1050   ( 508mm x 318mm )   58   59  
 8   1600 x 1024   ( 508mm x 318mm )   60  
 9   1440 x 900    ( 508mm x 318mm )   61  
 10  1400 x 1050   ( 508mm x 318mm )   62   63  
 11  1280 x 960    ( 508mm x 318mm )   65  
 12  1280 x 800    ( 508mm x 318mm )   66  
 13  1280 x 768    ( 508mm x 318mm )   67  
 14   960 x 600    ( 508mm x 318mm )   70  
 15   840 x 525    ( 508mm x 318mm )   71  
 16   832 x 624    ( 508mm x 318mm )   72  
 17   800 x 512    ( 508mm x 318mm )   78  
 18   720 x 450    ( 508mm x 318mm )   79  
 19   640 x 512    ( 508mm x 318mm )   80   81  
 20   640 x 400    ( 508mm x 318mm )   85  
 21   640 x 384    ( 508mm x 318mm )   86  
 22   576 x 432    ( 508mm x 318mm )   87  
 23   512 x 384    ( 508mm x 318mm )   88   89   90  
 24   416 x 312    ( 508mm x 318mm )   91  
 25   400 x 300    ( 508mm x 318mm )   92   93   94   95  
 26   320 x 240    ( 508mm x 318mm )   96   97   98  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none
Setting size to 0, rotation to left
Setting reflection on neither axis

I've also tried changing the rotation using the Nvidia Setting GUI, but when I change the setting nothing happens. 

My video card is an Nvidia 6600 and I'm using the proprietary driver (version 100.14.19). I'm quite certain I've got most of my settings right, including default depth (24) and rotation option in xorg.conf ("RandRRotation" "on"). But it's not working, so obviously something needs tweaking. 

I've attached a couple files that might help someone help me.

BTW, I'm running compiz, but this happens if I'm in metacity as well.

---

### Post by Greg T. on 2008-04-13
This has gotten a fair number of hits, so here's an update: Upgrading to Hardy solved the problem.

---

### Post by Hilko on 2008-05-02
I hoped upgrading to Hardy would help for me aswel. But it does not.
I was able to rotate my screen in Dapper, but I've lost this since 7.04 and later.
Can anyone help me to rotate my screen ? please!

---

