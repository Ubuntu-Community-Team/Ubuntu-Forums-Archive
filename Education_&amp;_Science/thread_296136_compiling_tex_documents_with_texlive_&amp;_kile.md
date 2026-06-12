---
title: "compiling tex documents with texlive &amp; kile"
date: 2006-11-09
forum: Education &amp; Science
---

### Post by col_b on 2006-11-09
OK. I need a bit of help on this one...

I installed ubuntu the other day.  Everything is sweet. :) 

I use latex and texnic in windows, so I'm trying to install latex in ubuntu.  I found a few tutorials and used Synaptic to install texlive and Kile.  texlive is installed and seems to be working, i.e. it displays version info when i type tex -version.

Now, I'm trying to use kile to compile a .tex document, which I know is coded correctly.  But, I get loads of undefined control sequences when i run tex, and the .dvi output is messed up.  Does kile need configured or something? ](*,) 

I appreciate your help.
Cheers,
Col

---

### Post by Nonno Bassotto on 2007-01-10
Usually this is a problem with the font encoding, which is is different from Windows to Linux. Try saving your file in a different font encoding.

---

### Post by neoflight on 2007-01-10
> **col_b said:**
> OK. I need a bit of help on this one...

I installed ubuntu the other day.  Everything is sweet. :) 

I use latex and texnic in windows, so I'm trying to install latex in ubuntu.  I found a few tutorials and used Synaptic to install texlive and Kile.  texlive is installed and seems to be working, i.e. it displays version info when i type tex -version.

Now, I'm trying to use kile to compile a .tex document, which I know is coded correctly.  But, I get loads of undefined control sequences when i run tex, and the .dvi output is messed up.  Does kile need configured or something? ](*,) 

I appreciate your help.
Cheers,
Col

1: try the command line to compile to dvi. it its working then its the problem with kile.
2. run texconfig and set the mode from there..
select "mode" option and select a mode for the metafont to generate the font bitmaps. See that you have installed the approrpiate fonts for texlive from synaptics. if you get write access error, use sudo or su -.

3. check using kile again. if that doesn't solve it then configure kile such that the applications are run outside of kile using the commands you specify. kile might be using kdvi to view dvi and it might not be installed. for eg: then you can tell kile to use evince to view dvi. 

post back the status and lets see...good luck..

---

### Post by skywatcher on 2007-05-16
Can someone perhaps shed some light on this problem?

I have been using teTeX with Kile on Dapper for some time, and everything worked just fine. In particular, viewing the dvi output with the embedded kdvi was great for on-screen previewing -  better than ps or pdf. But then, a day or so ago, I received my TeX Live 2007 discs. After installing TL and reconfiguring Kile, everything was fine, except for one thing: kdvi has trouble with fonts. When I try to view the dvi, all I get is a lot of black lines and blocks, no text -- kdvi tries to generate bitmap fonts. I fiddled around with mode in texconfig, but that didn't help. I can view ps and pdf output, but not dvi.

Any ideas?

Thanks

Added comments: I have just tried running xdvi on a dvi file from the command line, and it works, but it uses teTeX fonts, not TeXLive. I cannot remove teTeX without removing Kile -- catch-22?

---

