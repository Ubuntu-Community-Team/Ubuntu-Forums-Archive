---
title: "Compiz Resizeing Window problem!"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by Slacker.ksg5 on 2008-01-04
Well I have this problem that started this morning after I installed the Updates from the Update Manager. I know non of these files were Compiz files, because after extensively running beryl for sometime I had it crash on me several times with updating it. So now I have this problem that when I put the mouse over the edge of a window (So the resize mouse comes up) and simply click in any shape way or form it makes my XGL process sky rocket in CPU usage. It literally goes from 1% cpu usage to 48% and anything related to the XGL session lags extensively. 

I think the problem is the updates, but I could be wrong. 

Is there a way to roll-back an auto update without knowing the package names?

Any help is appreciated. Also I am rather new to Linux so please bare with me.

---

### Post by Slacker.ksg5 on 2008-01-04
Iv read a few things about the problems in ubuntu 7.10 with resizing and lag issues? Is this probably related to that and if so how do I go about fixing those issues?

---

### Post by Slacker.ksg5 on 2008-01-04
No answers yet =(. Sorry just trying to move my question back up.

---

### Post by Mr Greencastle on 2008-01-04
Not 100% sure, but I think that resizing is an issue with Xgl. I use Xgl myself and have change resizing in Compiz to be 'Outline' rather than animated. Works much nicer and looks cooler to me.

Mr Green

---

### Post by Slacker.ksg5 on 2008-01-05
Well this issue has been solved.
And yes it probably is a XGL problem.
One thing I did.

I disabled everything and than worked my way up through the plugins.
And it appeared to be the Crash Handler plugin. 

The other solution:

Compiz reported several problems with the gnome-panel vanishing. This was caused by the update of compiz 0.6.0 well there was also a new release to solve this problem and the release is copmiz 0.6.1 and it is working well.

I'm not sure if it was the crash handler and or the update that solved this problem, but it went away. Hopefully it stays that way ;)

---

