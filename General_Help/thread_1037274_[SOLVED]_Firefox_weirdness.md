---
title: "[SOLVED] Firefox weirdness"
date: 2009-01-11
forum: General Help
---

### Post by njalmagnus on 2009-01-11
Upfront - I'm new to Linux and try to fit some learning in around a hectic schedule so KIS (keep it simple)

Not sure if this is an Ubuntu 8.04 or Firefox problem. Last night I downloaded the updates for Ubuntu and now today my Firefox is misbehaving.
1) Firefox fills almost the whole screen. Not in a full screen sense but the desktop panels at the top and bottom are covered and the close window "x" is off the edge of the screen and inaccessible. If I F11 to fullscreen and then F11 to restore, everything comes right again for a while but after opening a few tabs we're back to the browser page being a little bigger than my screen.

2) Flashing - everytime the pointer goes over a hyperlink the screen flashes. If I click to open a new tab the screen flashes and when I click on a tab to open it, the screen flashes. It's getting really annoying, really fast!

I've used Firefox for some years and never encountered this before which is why I'm thinking it has something to do with the Ubuntu updates I downloaded last night. Has this happened to anyone else?

Thanks for reading and any assistance you might provide.

---

### Post by gettinoriginal on 2009-01-11
I will try to help you fix the first problem (size) now, and then I will have to research further for your second problem.
When the window is to large and you do the F11 twice thing, then manually minimize the window to a smaller size, then maximize with the max button.  Close firefox and reopen and the problem should be fixed  :p
And just so we know what we are looking at with the "flashing" problem, are you using compiz or metacity as your window manager, and gtk or emerald as your window decorator ??

---

### Post by bill516 on 2009-01-11
If you have the problem identified njalmagnus in no. 1 in which Firefox seems too large for its window, the solution offered by gettinoriginal will work.  I also had the problem and his suggestion fixed it.  I had been fiddling with this for several days with no success.

BTW, it is not possible to uninstall and reinstall Firefox in an attempt to solve the problem.  In fact, I am not certain it is possible to uninstall Firefox!  Now that is peculiar, but a different issue.

In the meantime my thanks to gettinoriginal for a solution.

---

### Post by gettinoriginal on 2009-01-11
You're welcome bill516, glad to have helped.  And yes, you can uninstall Firefox (or other applications), in terminal type:
```
sudo apt-get remove <app name>
```
To reinstall:
```
sudo apt-get install <app name>
```

---

### Post by njalmagnus on 2009-01-11
Thanks for the help gettinoriginal ---- sort of.

I tried what you suggested and it made it worse :shock: instead of better because when I first posted the window would open normal and then get weird after a couple of window changes BUT using your advice it opened weird. I repeated your process five or six times and no improvement. Then on the last attempt it (belched???) --- I don't know what to call it --- I never touched the x Firefox just closed itself when I minimized. When I restarted it it was back to normal.:D I've opened and closed it a number of times, I've opened a dozen tabs and closed them, I've open a couple of windows at once and now everything seems to be back to normal -- completely. The screen has even stopped flashing when the pointer passes over hyperlinks and when I open tabs. So, for now at least it seems to back to normal. Must have had something stuck in its throat and needed to hock up a hairball or something. 

I'm sure following your advice, even if it did take multiple tries, had something to do with the correction so thank you for your help. When I posted I was at my wits end.

---

### Post by gettinoriginal on 2009-01-11
:lolflag: at hairball  glad it finally fixed itself.  Please go to thread tools and mark this as solved.

---

