---
title: "Rollback wine to 9.16?"
date: 2006-07-16
forum: Gaming &amp; Leisure
---

### Post by echo $USER on 2006-07-16
Since upgrading wine to 9.17 hardly any Steam games work.  They worked very well in 9.16.  Is there a way to downgrade to 9.16 w/out uninstall/reinstall wine?  Thanks.

---

### Post by Blairboy on 2006-07-16
You can just open synaptic, find wine, click package at the top, then force version, and select 9.16.

---

### Post by echo $USER on 2006-07-16
> **Blairboy said:**
> You can just open synaptic, find wine, click package at the top, then force version, and select 9.16.


Thanks, but for some reason I could only rollback to 9.9.  Source games still do not work with 9.9.  I should have kept 9.16.  Oh well

---

### Post by YokoZar on 2006-07-18
You can now easily get old Wine packages by downloading them from the [WineHQ packages archive](http://wine.budgetdedicated.com/archive/index.html).  Just download the version you're looking for.

Now, if it truly is the case that your program works in an old version of Wine but not in the current version, then you have discovered what we call a *regression*.  Regressions are quite serious bugs, as if they go unreported apps can sometimes remain broken for *very* long amounts of time - Fallout 2, for instance, worked fine in 2002 and then became broken for over a year due to an unreported regression in Wine's Direct Input handling.

So, please, do us all a favor and [file a bug](http://bugs.winehq.org/) or send an email to the [wine-devel mailing list](http://winehq.org/site/forums) noting that you have found a "regression".

Anyway, I hope you can get it working again, and if you need help installing the old packages, just ask here.

---

### Post by Footissimo on 2006-07-18
Wine 9.17 buggers up a near perfect American McGhee's Alice too - the mouse movement becomes a complete horror..thankfully, going back to 9.16 fixes it (..and yes, I have reported it)

---

