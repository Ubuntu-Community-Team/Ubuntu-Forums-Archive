---
title: "Matlab figure fonts in 11.04"
date: 2011-05-19
forum: Education &amp; Science
---

### Post by lippman on 2011-05-19
I have the same problem as [this thread]("http://ubuntuforums.org/showthread.php?t=1728706&highlight=matlab+figure+font"), where Matlab can't render the fonts in figures, but can get the fonts right everywhere else on the desktop. I think the desktop fonts are handled by Java, but the figures are done with X. (I'm making a new thread since that one is closed).

The OP in that thread solved his problem by reverting to 10.10, installing matlab, then upgrading to 11.04. Can they or someone else tell me where there fonts are stored?  My current font path from running

```
xset q
```

is: 

```
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins

```

My bet is that's where the problem is. I have reported this to The Mathworks. They told me to wait for a new release.

---

### Post by rgbrown on 2011-05-24
Hooray, that's it!

That was the elusive information we needed: I looked at my 11.04 that worked (I was the OP on the other thread) and compared font paths. What you need to install is:

xfonts-100dpi and
xfonts-75dpi

logout and log back in again and you should be away laughing! (worked for me on a fresh install)

Do you know what to do about the libc.so.6 not found error?

---

### Post by lippman on 2011-05-24
Bam! That did it!  Thanks.

I'm not sure what you mean by the libc.so.6 error. But I had some library issues trying to compile a MEX function recently, and [this thread]("http://www.mathworks.com/matlabcentral/newsreader/view_thread/162466") had the answer. Instead of running mex in matlab, you run it in a terminal, so Matlab doesn't have a chance to screw up your path.

---

### Post by nuci on 2011-05-31
Thanks a lot! Worked for me on 11.04 64bit with Matlab R2011b.

Regarding the libc.so.6, you have to delete the symbolic link:
```
sudo rm /path/to/matlab/sys/os/glnxa64/libstdc++.so.6
```
and create a new one with the same name to the libstdc++.so.6 on your system lib-path. For me it was:
```
sudo ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6 /path/to/matlab/sys/os/glnxa64/libstdc++.so.6
```

---

### Post by tucuma on 2011-06-27
> **rgbrown said:**
> Hooray, that's it!

That was the elusive information we needed: I looked at my 11.04 that worked (I was the OP on the other thread) and compared font paths. What you need to install is:

xfonts-100dpi and
xfonts-75dpi

logout and log back in again and you should be away laughing! (worked for me on a fresh install)

Do you know what to do about the libc.so.6 not found error?


I'm having this problem running matlab 2011a  (64bit) on my first linux machine (ubuntu 11.04)... did 
sudo apt-get xfonts-100dpi and
sudo apt-get xfonts-75dpi

and the font path now includes /usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi are 
... but matlab still is making the figure fonts look really really bad.  i couldn't change fontsizes before (and now can) but the only reasonably tolerable font is 'Bitstream Charter' and even that doesn't look great.  am i missing something?

---

### Post by yoel.koenka on 2011-08-10
I have the same problem, running Matlab2010b on Ubuntu11.04, 64bit
Installed both packages:
xfonts-100dpi and
xfonts-75dpi

and still only some of my fonts work in Matlab:
- Bitstream charter
- Courier fonts
- Helvetica
- New Century schoolbook
- Symbol
- Times

All of the other fonts don't work (yet I can choose them in the dropbox when I add a textbox).

Help someone?

---

### Post by jab5415 on 2011-08-11
This worked like a charm!  Thanks for the info rgbrown!

---

### Post by frankigia on 2011-08-11
Hey guys,
how does one change the fonts path. I have no idea how to do that. Any help would be highly appreciated.
Thanks.

---

### Post by keretai on 2011-08-24
Nvidia DPI settings may also be the cause of the small fonts, small figure data points.  [This matlab blog entry on ubuntu xorg dpi settings may be the solution.]("http://ifixdit.blogspot.com/2011/08/how-to-fix-matlab-small-figures-and.html")

[http://ifixdit.blogspot.com/2011/08/how-to-fix-matlab-small-figures-and.html](http://ifixdit.blogspot.com/2011/08/how-to-fix-matlab-small-figures-and.html)

---

### Post by tsgouvea on 2012-02-21
> **yoel.koenka said:**
> I have the same problem, running Matlab2010b on Ubuntu11.04, 64bit
Installed both packages:
xfonts-100dpi and
xfonts-75dpi

and still only some of my fonts work in Matlab:
- Bitstream charter
- Courier fonts
- Helvetica
- New Century schoolbook
- Symbol
- Times

All of the other fonts don't work (yet I can choose them in the dropbox when I add a textbox).

Help someone?

Exact same problem here.
Running Matlab R2009a 32-bit on Ubuntu 11.04 64-bit.

---

### Post by souravc83 on 2012-03-19
Thanks. had the same problem with fonts.
Now it works like a charm, after installing the two packages.

---

### Post by ruined1234 on 2012-03-27
> **rgbrown said:**
> Hooray, that's it!

That was the elusive information we needed: I looked at my 11.04 that worked (I was the OP on the other thread) and compared font paths. What you need to install is:

xfonts-100dpi and
xfonts-75dpi

logout and log back in again and you should be away laughing! (worked for me on a fresh install)

Do you know what to do about the libc.so.6 not found error?
Many thanks. I spent almost an hour on this FontSize issue

---

