---
title: "Compiz cube has a glitch when rotates, and looses window focus"
date: 2011-10-18
forum: Desktop Environments
---

### Post by raster on 2011-10-18
Hi all:

I'm using Ubuntu 11.10 with Gnome Fallback Session and Compiz. I also have the cube active, and it works quite well, except for this:

When I rotate the cube, it rotates smoothly, but when the movement ends, there's a glitch, a fast flash with the old desktop, which appears and disappears fast.

Also, the app in the new desktop looses the focus, so I must click again with the mouse in the window to gain it again. This is particularly annoying when editing a text.

Finally, when I open from another program a web page in Firefox, in Ubuntu 10.04 it switched automatically to Firefox, rotating the cube to the face where it was. Now this doesn't happen.

I tried to disable the cube, but CompizConfig Settings fails with a core dump when I try to do it.

I'm using Ubuntu 11.10 64bit, with the propietary driver for ATI cards.

Thanks.

---

### Post by mc4man on 2011-10-18
Problem here also, actually so bad that i had to go back to wall which I'm sorta getting used.
This is one current bug on
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198)

---

### Post by unc0nn3ct3d on 2011-10-19
Yup, confirmed this as well.. Looks like we have to kiss the desktop cube goodbye, easily the most useful tool in compiz, until this is fixed..

I have unity completely removed and am in Gnome Classic and it still is here..

This entire update is a disaster, I'm this close to moving over to any other distro than ubuntu because of crap like this.  Give us option conical, don't force your new, worthless crap interface down our throats.  If we wanted that we would be windows/mac users.


UPDATE:  I found that if you move the window with ctrl-alt-shift left/right and then when yhou get it where you want it quickly let go of shift and just rotate the cube somewhere else the window will stay in place

---

### Post by julovac on 2011-10-22
same problem here, 11.10 64bit, nvidia-current, fallback session and compiz.
moving window to another workspace makes rest of the windows blink for a second (even though they are on different workspace)

---

### Post by Arathon on 2011-10-24
I have all of these problems as well.  It's pretty frustrating.

---

### Post by A4orce84 on 2011-10-25
Looks like I'm not even going to attempt it, just stick to the desktop wall

---

### Post by verbedr on 2012-01-01
Hi the glitch is actually that the focus goes back to the original window and doesn't stay on the first window of the active cube side. 

The anoying thing is when I use some shortcut it actually is executed on the non visible pane of the cube and with the non visible window. Hopefully someone knows how to fix this.

---

### Post by verbedr on 2012-01-01
BTW maybe related but moving a window to another cube face doesn't work either the window is pulled back to the starting face. Perhaps a general change in passing the active desktop wall and starting desktop wall of the cube when executing these functions?

---

### Post by Cyclops_ on 2012-05-22
This is still happening to me!!! :(

---

### Post by cbanakis on 2012-05-30
yeah, I too am experiencing this.

Spent hours messing with different settings in compiz, and video drivers.

Theres got to be some sortof workaround?
(other than, not using desktop cube)

---

### Post by cbanakis on 2012-06-18
Finally, a solution.

Proposed updates for Compiz.

Add this ppa to your software sources.

deb [http://ppa.launchpad.net/vanvugt/compiz-preproposed/ubuntu](http://ppa.launchpad.net/vanvugt/compiz-preproposed/ubuntu) precise main

Then just do a regular software update.

Seems to solve all my problems.

I did it a couple weeks ago, and have not found a downside yet.

---

### Post by mnrl on 2012-06-23
@cbanakis
thanks it works:p

---

### Post by sendittokeith on 2012-07-13
Hello, 

This worked for me, but now about 1 week later it stopped working.  I am not sure how to fix it again .. i tried to update but had none available.

Thank you for the initial fix - any idea how i can get it working again?  The flahy is killing me!

---

### Post by cbanakis on 2012-08-15
Yeah, stopped working for me as well.

Must have been another update that broke it again.

Bah!!!

---

### Post by cbanakis on 2012-08-29
Found another fix on launchpad.

Works great.

sudo apt-get install synaptic

sudo apt-add-repository ppa:vanvugt/compiz-preproposed

sudo apt-get update

sudo apt-get install compiz=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-core=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-gnome=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-plugins=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-plugins=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-plugins-default=1:0.9.7.8-0ubuntu1vvpreproposed2 libdecoration0=1:0.9.7.8-0ubuntu1vvpreproposed2

(it will downgrade packages, allow it to continue)

Start synaptic

in "Search filter": put "compiz"

select every package that has a (!) next to it.

Select Package -> lock version

(they become red)

exit synaptic

Reboot or Restart X/Compiz.

---

### Post by cbanakis on 2012-09-05
I believe this thread should be solved now.

---

### Post by Cyclops_ on 2012-09-05
cbanakis:  but it's not fixed yet in the mainstream packages...

---

### Post by aboud on 2013-01-19
For two years now I was unable to use the cube due to the problem you have just sloved for me. 

back to the old good days of the cube.

Thank you.

---

### Post by aboud on 2013-06-27
The issue is back with latest update. 

The fix :
sudo apt-get install compiz=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-core=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-gnome=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-plugins=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-plugins=1:0.9.7.8-0ubuntu1vvpreproposed2 compiz-plugins-default=1:0.9.7.8-0ubuntu1vvpreproposed2 libdecoration0=1:0.9.7.8-0ubuntu1vvpreproposed2

Now causes and issue after login, where you land on a page with the default desktop background and not keyboard or mouse functionality unless you to go terminals : alt-ctl-f1

---

