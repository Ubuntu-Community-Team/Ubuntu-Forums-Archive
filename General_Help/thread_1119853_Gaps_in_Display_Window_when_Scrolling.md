---
title: "Gaps in Display Window when Scrolling"
date: 2009-04-08
forum: General Help
---

### Post by GenePayne on 2009-04-08
I have a display problem with text and images in scrollable windows. Often when I scroll up or down, "gaps" appear in the page where the contents that were previously off-screen either don't get displayed, or they are displayed on the wrong part of the page. If I click and drag to highlight text, everything shows up as it should be. When it happens in a web browser, I have to click refresh to fix the display after every scroll.

This is a problem when viewing PDFs, open office docs, web browsing, etc. I see it in a lot of different programs so it is more like a general problem with scrollable windows, and not specific to any particular app.

I recently upgraded to 8.10 Ibex, which seems to be when this started happening.

Any thoughts?

---

### Post by GenePayne on 2009-10-09
This was on old issue with no replies, but I learned something new about it recently.

I recently switched from compiz back to no visual effects (because of another issue), but after using without compiz for a while, I noticed that this gap display problem no longer occurs.

So, I think this is an issue with compiz, or my nvidia video card driver (using 180.44), or my video card (nvidia Quadro NVS 140M).

Has anyone seen a similar problem?

---

### Post by GenePayne on 2010-11-30
This is an old issue for me, and the problem became more irritating when I started using compiz more frequently. Since I started this thread a year-and-a-half ago, I'm still running compiz on the same laptop (lenovo T61 14") with the same nvidia Quadro NVS 140M video card. I'm now running ubuntu 10.04, and my nvidia driver version is now 173.14.22.

Anyway, I now use an ugly but effective fix for this when the "tearing" occurs in the window when scrolling. I simply restart compiz:
```
compiz --replace
```

Sometimes it doesn't take long for the tearing to re-appear after restarting compiz. Some days I have to do this a dozen times, but it works.

---

