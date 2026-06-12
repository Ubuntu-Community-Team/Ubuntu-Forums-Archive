---
title: "about octave print -Thanks"
date: 2010-01-15
forum: Education &amp; Science
---

### Post by siaosong on 2010-01-15
Hi all,
 
I'm faced with a problem. Here is the code:
 
clear
clc
a=[1:3];
plot(a,'linewidth',5)
xlabel('x','fontsize',20)
print('a.jpg','-djpg')
 
In the display window, the figure shows well with thick linewidth and big fontsize of xlabel. However, the figure a.jpg is not the same to what shows in the display window. The linewidth can be as thick as 5, but the fontsize is still very small. Furthermore, i use 
 
set(gca,'fontsize',20) or print('a.jpg','-djpg','-F:20'),
 
they both don't work.
 
I feel it is very strange, could you help me? Thanks a lot.
 
Siaosong

---

### Post by siaosong on 2010-01-15
In addition, is there any other functions instead of print to output plots to files? 
Thanks!

---

### Post by normandin on 2010-01-16
Hi siaosong,

Some more information is needed to diagnose your problem.

What version of Octave are you running?  Is it from the Ubuntu repos or did you compile it yourself?  What graphics backend are you using for plots?  What GNUTERM is this under?

---

### Post by siaosong on 2010-01-16
Hi Normandin,
 
Thanks a lot.
 
The version of Octave is GNU Octave-3.2.2 for windows. The version of GNUTERM is hard to find in this windows-Octave.I viewed the plots in Windows Photo Viewer. Also I tried the same version in Cygwin, but it did not work, too. 
 
Thanks again for your reply.
 
Siaosong

---

### Post by not_a_phd on 2010-01-16
Code works fine in Ubuntu Karmic with octave/gnuplot installs from the repository.

Would recommend you try in Ubuntu.

My personal experience is octave/gnuplot in windows is a bit flaky. The only success that I have had at getting publication quality plots in that environment has been to tweak the plot in the display, copy it to the clipboard, and paste it into the document. This gets really, really old for a report with a lot of plots.

---

### Post by siaosong on 2010-01-16
Thanks a lot. Now I'm using Win7, is there any Octave version in Ubuntu for this OS?

---

### Post by normandin on 2010-01-18
> **siaosong said:**
> Thanks a lot. Now I'm using Win7, is there any Octave version in Ubuntu for this OS?

Hi siaosong,

Ubuntu is an OS based on the Linux kernel and GNU userland.  It's possible to run Ubuntu in a virtual machine under a Windows OS, but strictly speaking there's no "Ubuntu for Windows".

As such, ubuntuforums doesn't seem like the most appropriate place to solicit advice regarding problems that you encounter when running Octave on Windows.  I'd suggest that you search the archives of the Octave-help mailing list ([http://www-old.cae.wisc.edu/pipermail/help-octave/](http://www-old.cae.wisc.edu/pipermail/help-octave/)).  If you don't find an answer there, you might do well to post an inquiry to that list (help-octave@octave.org; [https://www-old.cae.wisc.edu/mailman/listinfo/help-octave](https://www-old.cae.wisc.edu/mailman/listinfo/help-octave)).

---

### Post by siaosong on 2010-01-18
Hi Normandin,
 
Thanks a lot for your suggestions. I'll have a try.
 
Siaosong

---

