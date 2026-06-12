---
title: "Can't see 3D graphics on Mathematica"
date: 2011-04-06
forum: Education &amp; Science
---

### Post by Fibonacci on 2011-04-06
I'm running Mathematica 7 on a laptop with a Mobility Radeon X1300.
Just as the title says, 3D graphics (such as the output of a Plot3D command) are not displayed – or rather, are displayed as a completely blank rectangle. I can see the graphics when rotating them with the mouse, though, but once I stop the rotation I'm back to the blank rectangle.
Also, any graphics using a ColorFunction have the same problem.

Strangely, Mathematica 7 works fine on my desktop computer, with GeForce 6200 graphics.

I saw someone with the same problem here, but they had Intel graphics, and so solved it differently.

What can I do?

---

### Post by Herrer on 2011-04-08
It sucks when something is displayed as a black rectangle. Good luck getting to see the graphics you want to see.

---

### Post by Fibonacci on 2011-04-08
Happens also on Mathematica 8.
Sucks even worse since such graphics are the main reason I use Mathematica instead of (say) Maxima.
Has anyone got any suggestions?

---

### Post by Bill Simpson on 2011-04-09
1: Use divide and hopefully conquer strategy.  Export[] the graphic as say jpg and try viewing the exported file with something else. If that works then the graphic is probably being created correctly and just not rendered by Mathematica correctly.

2: Google to see if you can find someone else with the same problem and perhaps even a possible solution.  The first possible hit for
[http://www.google.com/search?q=mathematica+plot3d+black+problem](http://www.google.com/search?q=mathematica+plot3d+black+problem)
is [http://kausikdas.blogspot.com/2009/07/ubuntu-904-mathematica-plot3d-problem.html](http://kausikdas.blogspot.com/2009/07/ubuntu-904-mathematica-plot3d-problem.html) that sounds like it might give some advice. Variations on that, particularly including ubuntu in the search find others.

---

### Post by Fibonacci on 2011-04-09
> **Bill Simpson said:**
> 1: Use divide and hopefully conquer strategy.  Export[] the graphic as say jpg and try viewing the exported file with something else. If that works then the graphic is probably being created correctly and just not rendered by Mathematica correctly.

Didn't work. I got an entirely black JPG.

> **Bill Simpson said:**
> 2: Google to see if you can find someone else with the same problem and perhaps even a possible solution.  The first possible hit for
[http://www.google.com/search?q=mathematica+plot3d+black+problem](http://www.google.com/search?q=mathematica+plot3d+black+problem)
is [http://kausikdas.blogspot.com/2009/07/ubuntu-904-mathematica-plot3d-problem.html](http://kausikdas.blogspot.com/2009/07/ubuntu-904-mathematica-plot3d-problem.html) that sounds like it might give some advice. Variations on that, particularly including ubuntu in the search find others.

It looks like it might help, but I haven't got an /etc/X11/xorg.conf file, so I'm not sure of how to apply that solution.
I found a bunch of files on /usr/share/X11/xorg.conf.d/, but I'm not sure of where to put those lines.

I also found this: [http://www.mathkb.com/Uwe/Forum.aspx/mathematica/17264/Plot3d-causes-crash-with-radeon-driver-and-Debian-testing](http://www.mathkb.com/Uwe/Forum.aspx/mathematica/17264/Plot3d-causes-crash-with-radeon-driver-and-Debian-testing) which does look like my problem. Running "mathematica -mesa" does help, and does slow down the rotations a lot, but there is no crash at all.
There doesn't seem to be a solution though.

---

### Post by Fibonacci on 2011-04-09
I did create an /etc/X11/xorg.conf file with the content given here: [http://kausikdas.blogspot.com/2009/07/ubuntu-904-mathematica-plot3d-problem.html](http://kausikdas.blogspot.com/2009/07/ubuntu-904-mathematica-plot3d-problem.html)
It didn't change anything at all. I'm still seeing transparent rectangles instead of 3D plots.

---

### Post by Fibonacci on 2011-04-24
Update: On a Maverick liveCD on the same hardware, this problem does NOT happen. I can see 3D graphics without a problem.

---

