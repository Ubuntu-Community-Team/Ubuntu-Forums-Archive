---
title: "wine problems.... font issues?"
date: 2005-06-28
forum: Desktop Environments
---

### Post by holr on 2005-06-28
Hi,
   Been trying desperately to get wine running but i seem to keep getting weirder and weirder problems! My current one is after getting the cvs of wine, compiline / installing  and by running the useful winetools program to update it.

When I go through the options, I start off with "create fake windows drive" and I get a big long list going up to 100% saying "font metrics: ....% done". This goes fine up until 98.7 percent, and I start getting messages like:

err:font:XFONT_BuildMetrics failed to load -unknown-freemono-bold-r-normal--100*-100-100-c-0-iso8859-14

(see the attached image for other similar problems). It then gets to 100% and quits with the "unhandled page fault" thingy.

Am i missing some core fonts or something? I have only just installed ubuntu fresh this evening and am trying to get wine working!

Please help! im going crazy trying to get wine going!

---

### Post by dfghost on 2005-06-28
Do you have the full support for X devels on?  Also, are any subsidary packages that are listed while wine is installing not loaded.  If so, do an sudo apt-get install updates and then install the missing support packages.

---

### Post by holr on 2005-06-29
[QUOTE=dfghost]Do you have the full support for X devels on?  Also, are any subsidary packages that are listed while wine is installing not loaded.  If so, do an sudo apt-get install updates and then install the missing support packages.[/QUOTE]
 Ok, have tried a few things but still not getting any luck. Have removed the CVS wine and installed the one from synaptic (wine 0.0.20050524-winehq-1). I also then try using the other setup tool ,winesetuptk, but when i select this package to install it from synaptic, winesetuptk, it tells me that wine has to be removed?!? (see screenshot)

What am i doing wrong? I thought I needed wine for winesetuptk....

---

### Post by dfghost on 2005-06-30
hmmm....What i had to do to get Wine to work (although don't expect too much out of it, it didn't support any of my windows programs properly, o well.  I guess i'll have 1 windows and 1 linux) is install everything it needed:

x devels
x support
fonts
C++
bison
flex
etc.....

to add the fonts [visit here](http://ubuntuguide.org/#extrafonts)

And then redo wine from the beginning, in terminal i might add, from the winetools setup, or whatever it's called.  It then worked.  Lemme know of any further problems.

---

### Post by holr on 2005-07-04
Thanks for the suggestions, I had better luck with the extra packages you suggested but run into further troubles. I reinstalled ubuntu and first thing I did was get wine and winetools and its all set up lovely now! thanks for your help!

---

