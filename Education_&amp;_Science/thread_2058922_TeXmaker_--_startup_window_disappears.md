---
title: "TeXmaker -- startup window disappears"
date: 2012-09-16
forum: Education &amp; Science
---

### Post by silbar on 2012-09-16
I've been a happy and experienced user of TeXmaker, on 10.04 and earlier, for many years.  I've now upgraded to 12.04 and installed the 12.04 version from the Software Center.  

After installation, my first attempt to use TeXmaker brought up the usual window containing the latex file.  Which, with <F2> seemed to compile normally.  On doing <F1> to bring up a display of the .dvi file (which I assumed would have been postscript), however, things went awry.  There MIGHT have been a PDF display on the far right side of the window containing the.tex file.  But somehow I never really got to a good display of that.

And, after that, now when I start Texmaker on a .tex file, the window that used to come up now disappears in a series of horizontal bars that migrate down to the bottom of the screen and disappear.  Has anyone else seen that kind of behavior?

I have removed the TeXmaker app, using both the Software Center and Synaptic, then re-installed, but this does not cure the phenomenom of the disappearing bars that might have been the startup window.

Any help out there?  

Rico Silbar

---

### Post by silbar on 2012-09-18
I see that there were 87 views but no responses to this posting.

I am baffled, because on my 12.04 at the lab, TeXmaker acts as I expect.  Here on this home computer, however, even after removing both texmaker and texmaker-data packages **completely** (in Synaptic, not the Software Center), and then re-install both, I still get the failing down horizontal bars and no window.

For what it might be worth, the version at the Lab uses xdvi to create the display on <F1>.  Might there be some problem in that it originally tried to make a PDF display?

Rico Silbar

---

### Post by bryncoles on 2012-09-20
Hi (again) silbar

Have you tried removing texmaker from the terminal?  open the terminal and type:
```
sudo apt-get purge texmaker
```

that will remove texmaker **and** all its configuration files.  I don't know if that'll help any, but it cant hurt!  You can then reinstall using 
```
sudo apt-get install texmaker
```

---

### Post by silbar on 2012-09-20
By golly, that worked!  Thanks bryncoles.

Actually, I had (privately) asked him what he was using these days for compiling and editing LaTeX files, pointing him to this thread.  In the meantime, I had decided to revert back some twenty years and to use the LaTeX mode of emacs (actually, emacs 23).  That does indeed work, and is only slightly less convenient than texmaker.

So, I will now mark this thread as solved (by bryncoles).

Rico Silbar

---

### Post by bryncoles on 2012-09-20
It's fixed -- cool stuff!  There must have been some residual config files causing you troubles after the other disaster.  

Glad that everything is working again now though!

^_^

---

### Post by tumutanzi.com on 2012-09-21
Just one more info, I am using TexMakerX, it is even better than TexMaker.

---

