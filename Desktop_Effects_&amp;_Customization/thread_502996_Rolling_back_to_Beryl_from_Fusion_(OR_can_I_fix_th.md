---
title: "Rolling back to Beryl from Fusion? (OR can I fix this?)"
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by loopjeremyloop on 2007-07-17
Let's just suppose I had a wonderfully functional version of Beryl that ran perfectly on my system.  Let's further suppose I went and installed Fusion because, well, nothing's ever quite good enough until you break it, right?  Let's then suppose that Fusion is acting like a crash-test-dummy, hard locking my system whenever I enter its preferences.  

I could see fusion as being decent IF it was more stable than, say, my friend's mom after an all-night crack binge... but since it's not, I want my nice, solid Beryl back.

What's the best way to go about doing this?  (OR) Is there a nice, easy troubleshooting technique I can use to find out why Fusion drops its crap every time I want to configure it?  How about the idea of maybe using themes through emerald without having to deal with the Beryl-Manager applet?

Thanks for any assistance!

---

### Post by ittiam on 2007-07-17
> **loopjeremyloop said:**
>   How about the idea of maybe using themes through emerald without having to deal with the Beryl-Manager applet?

```
compiz --replace -c emerald &
```

---

### Post by Happy_Man on 2007-07-17
Well, if you used Trevino's repos, run this command ```
sudo apt-get remove compiz-core compiz-plugins-*
sudo apt-get install beryl emerald-themes
```

If you want to fix emerald so it works with Compiz Fusion, do this: ```
sudo apt-get remove emerald
sudo apt-get install emerald
```

Then press alt+f2 and type ```
emerald --replace
``` (Make sure you have Fusion running first)

---

### Post by loopjeremyloop on 2007-07-17
Thank you for your assistantce here - looks about right as far as emerald working correctly now (yay)... but I'm still locking the display in the configuration manager.  Are there any settings which could help to alleviate this?  I am running whatever nvidia driver is in the restricted repos for feisty, if that helps.

---

### Post by hyperair on 2007-07-17
I did notice recently that Compiz Fusion had a bit of problem with CompizConfig Settings Manager. The latest update from Trevino's repository fixed that though.

---

### Post by SkiesOfAzel on 2007-07-17
If you have problems with compiz fusion from Trevino's repo you could try [this]("http://vorian.org/?p=82") repo instead. Remove compiz first and disable Trevino's repo in sources.list before you try it though, else it might brake ;). 

Choppiness with nvidia cards can be fixed most of the time like [this]("http://ubuntuforums.org/showpost.php?p=3022544&postcount=16").

---

