---
title: "Kiosk Help"
date: 2012-11-14
forum: Desktop Environments
---

### Post by ataylor1988 on 2012-11-14
I have been looking all over the web trying to get a good how two on building a linux Kiosk.

I think i have pretty much got it to where i want it to be except these 2 issues. I guess really they are 1 issue just different ways to go about it.

1. Find a way to automatically log the user off if firefox is closed
2. automatically launch firefox in TWM instead of gnome, and also auto logout if it is closed.

I am doing this on ubuntu 10.04LTS.
i have firefox automatically loading and the user automatically loging in.  It loads in kiosk mode via the rkiosk extension. but they can still alt+f4 and close it to get to a gnome session.  I need to be able to do one of the following above with it.

I have used this as my main resource on getting this setup but have not been able to solve my current issues.

[http://ze.phyr.us/kiosk-mode-in-linux](http://ze.phyr.us/kiosk-mode-in-linux)

Thanks

---

### Post by lykwydchykyn on 2012-11-14
I did a pretty thorough write-up on linux kiosks a while back, you can read it here:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

If you look in the comments section, there are some ideas for implementing a shutdown after the browser is closed.  Most of the other issues you mention are solved by following the method I outline.

---

### Post by ataylor1988 on 2012-11-15
> **lykwydchykyn said:**
> I did a pretty thorough write-up on linux kiosks a while back, you can read it here:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

If you look in the comments section, there are some ideas for implementing a shutdown after the browser is closed.  Most of the other issues you mention are solved by following the method I outline.

Thanks I might switch to that in the future.
I have one more issue to add.  is there anyway to allow printing from firefox with rkiosk installed?

---

### Post by lykwydchykyn on 2012-11-15
> **ataylor1988 said:**
> Thanks I might switch to that in the future.
I have one more issue to add.  is there anyway to allow printing from firefox with rkiosk installed?

No idea; I gave up on using Firefox for kiosks years ago.  I tried rkiosk a few times, but I didn't care much for its "all-or-nothing" approach.

That's why I ended up writing a custom kiosk-oriented browser.

---

