---
title: "CompizFusion Install from System Updates"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by kprowell on 2007-06-26
When I got home last night I noticed that there were some updates available.  When I clicked on the icon I saw that CompizFusion was part of it! Cool!  So I went forward with te update.  It seemed to install ok.  However, I feel as if I have a mix of Beryl and CompizFusion.  If I turn both off my borders are missing.  My question is this.  Should I remove all desktop effects (Berly, Emerald, CompizFusion) and start over?  It just seems like it isn't right.  The Super Key doesn't work.  The only thing I can get working is the spinning cube.  In Beryl, everything worked.  Any thoughts?

---

### Post by andrewsomething on 2007-06-26
I'm not exacty sure what you're asking. You might want to provide some more information on each issue. But here are a few thoughts...

First of all, after stopping both Beryl and Compiz/Fussion you should run "metacity --replace" inorder to go back to the standard set up.

Second, you can't run both Compiz and Beryl at the same time. You can have both on your machine and switch back and forth though (I am doing that myself).

Like I said, you problem isn't completely clear, but removing ang then reinstalling has solved a lot of problems for some people. Residual configurations seem to muck things up some times. If you didn't remove Compiz before installing Compiz/Fussion, I'd deffinetly sugest doing so.

I hope that helps...

---

### Post by kprowell on 2007-06-26
Thanks andrewsomething!  I know my post wasn't the clearest but that's because I'm not exactly sure what's happening.  I will try what you suggested later tonight and let you know.  Thanks again.

---

### Post by walkerk on 2007-06-26
First I would try removing everything that has to do with Beryl (Compiz Fusion includes the old Beryl plugins...) through Synaptic.. Reboot and see what happens when you do this in the terminal:
```
compiz --replace &
emerald --replace &
```

For emerald ensure you have a recent version.

If this works you can load compiz fusion w/ emerald themes simply by:
```
compiz --replace -c emerald
```


If this didn't work I would remove all compiz related objects through Synaptic as well and then follow one of the easy tutorials on this forum.

---

### Post by kprowell on 2007-06-27
Thank you both andrewsomething and walkerk.  I used info from both of you and got it all working!  It is SWEET!  I ended up removing everything related to Beryl and Compiz.  Followed the instructions per walkerk's suggestion and I now have CompizFusion running.  I still have one problem that I cannot resolve.  If I go back to Metacity, I still don't have my borders.  I tried the commands and it works only during that session.  If I logoff then back on (and turn off CompizFusion) they are still missing.  I guess I still have some work to do but for now my PC is stout enough to handle running the special effects.  Thanks again for the help...   What a great community!!!

---

