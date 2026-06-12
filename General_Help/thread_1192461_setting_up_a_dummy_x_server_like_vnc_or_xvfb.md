---
title: "setting up a dummy x server like vnc or xvfb"
date: 2009-06-20
forum: General Help
---

### Post by kruschev on 2009-06-20
Dear All,

I am struggling with an annoying problem. I want to run matlab on many cluster machines (all of which run ubuntu), and these matlabs need a display. Of course, it is not possible to have a real display, so I need some dummy version.

First note that there is no workaround in matlab itself, believe me I have tried to find one! As an aside: matlab is an awfully designed program and I think it should be avoided like the plague, the trouble is I have already written too much code to switch.

Now, I thought I had a great solution: 

```
# create a dummy x server (10 is just for this example)
Xvfb :10 >& /dev/null &
# start matlab and tell it to use the dummy server:
matlab -nodesktop -display localhost:10
```

But this has some problems, as matlab complains: 

```

"Warning: No window system found.  Java option 'MWT' ignored"
```

And it turns out that for certain types of figures, you don't get what you would normally get if you ran with a display, and the results are useless.

So, can anyone propose a better way to start a dummy, data sinking x server that has a window system as close to x11/gnome as possible? Some refinement to the way Xvfb is used? Alternatively vncserver is a possibility I'm not sure what the *best* way of using that would be, and I thought someone may already know of a really good way which may be entirely different.

Any help would be appreciated like you can't imagine!

---

### Post by kruschev on 2009-06-22
If anyone has this same problem, try the attached work around. It worked perfectly for me, much better than the mathworks own advice!

---

### Post by Endolith on 2009-10-11
> **kruschev said:**
>  First note that there is no workaround in matlab itself, believe me I have tried to find one! As an aside: matlab is an awfully designed program and I think it should be avoided like the plague, the trouble is I have already written too much code to switch.

Octave, FreeMat, Scilab, PyLab?

---

