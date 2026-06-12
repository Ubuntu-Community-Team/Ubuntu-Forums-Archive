---
title: "Fonts are horizontally stretched"
date: 2006-12-22
forum: Desktop Environments
---

### Post by jqp on 2006-12-22
On Edgy, my fonts are horizontally stretched, enough so to give me a headache.

One of the first things I've tried was changing the fonts from the default to Deja Sans and Deja Serif.   Those are the fonts I use on my Kubuntu install at work where things don't look stretched at all.

My screen resolution and refresh rates are correct - images, icons, etc don't look stretched at all.

I attached a screenshot.  Any suggestions?

Edit: after making some tweaks, the only things that still look stretched are the titlebars on windows and fonts in Firefox (mainly the chrome).  I fixed titlebars by switching to Emerald for themes, which is what I use at work anyway in Kubuntu.  I'll look around for how to fix my fonts in Firefox chrome (just look at my userChrome settings), so I think I have it under control now.

---

### Post by Schrollini on 2007-03-15
After upgrading to Edgy, I had the same problem with fonts being stretched in Firefox.  Eventually, with hints [here]("https://launchpad.net/ubuntu/+source/firefox/+bug/58511") and [here]("https://launchpad.net/ubuntu/+source/fontconfig/+bug/63403"), I managed to fix the problem by adding to /etc/firefox/firefoxrc the line

```

MOZ_DISABLE_PANGO=0
```

and restarting Firefox.  Others have apparently solved this problem by playing with font configurations or font hinting settings, but neither worked for me.

I suppose this is a bit late for you, **jqp**, but maybe this will help someone else with the same problem.

---

