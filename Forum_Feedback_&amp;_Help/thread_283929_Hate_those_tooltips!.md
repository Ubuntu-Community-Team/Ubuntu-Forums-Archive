---
title: "Hate those tooltips!"
date: 2006-10-24
forum: Forum Feedback &amp; Help
---

### Post by glotz on 2006-10-24
I can appreciate tooltips when pointing at something but when pointing at the background...

I HATE THEM I HATE THEM I HATE THEM!!!1

---

### Post by wieman01 on 2006-10-25
What exactly are you referring to?

---

### Post by glotz on 2006-10-25
Hit the new posts link [http://www.ubuntuforums.org/search.php?do=getnew](http://www.ubuntuforums.org/search.php?do=getnew)

scroll to middle of the page and lo and beholde, the disgusting tooltips are starting to creep up at your cursor!

---

### Post by wieman01 on 2006-10-25
> **glotz said:**
> Hit the new posts link [http://www.ubuntuforums.org/search.php?do=getnew](http://www.ubuntuforums.org/search.php?do=getnew)

scroll to middle of the page and lo and beholde, the disgusting tooltips are starting to creep up at your cursor!
Ah... Got it. I guess I can live with them. But can be annoying, right.

---

### Post by aysiu on 2006-10-25
Are you using Firefox?

---

### Post by glotz on 2006-10-25
Yes I am but I don't want to turn off all tooltips.

---

### Post by aysiu on 2006-10-25
> **glotz said:**
> Yes I am but I don't want to turn off all tooltips.
That's okay.

Type ```
about:config
``` in the address bar.

Then look for a key called *allinonegest.showLinkTooltip*.

Set the value to ```
false
``` That should turn off the link hover tooltips, but you should still have other tooltips functional.

**Edit**: Never mind. I'm an idiot. The key you're looking for is *browser.chrome.toolbar_tips*, and it will turn off all tooltips.

---

### Post by glotz on 2006-10-25
Thanks for trying to help. I guess I meant this rant at the web masters of the site.

---

### Post by orb9220 on 2006-10-26
> Thanks for trying to help. I guess I meant this rant at the web masters of the site.

It is not the forums or website it is how you browsers is set. If you don't want to be annoyed then do as "aysui" has suggested in his post above.

---

### Post by elanthis on 2006-10-26
Bull.  I should not have to disable all of that behavior on all sites in my browser just because this one single site uses tooltips in such a broken and retarded fashion.

The problem is that if you are looking at a list of topics, if you leave your cursor _anywher_ in the main window, you end up with a huge and near pointless tooltip that covers a very large portion of the browser window.

At the very least, change the code so the tooltip is only displayed if I have the cursor over the topic's title, and not anywhere in the entire row of the topic in the list.  Give me _somewhere_ to put the cursor that won't result in half my screen being blighted out by a useless hunk of text.

---

### Post by Immortal_one on 2006-10-29
> **orb9220 said:**
> It is not the forums or website it is how you browsers is set. If you don't want to be annoyed then do as "aysui" has suggested in his post above.

This annoys me too; instead of tooltips when hovering over a link they pop up anywhere on the page.

-Immortal_one

---

### Post by Schluppy on 2006-10-29
> At the very least, change the code so the tooltip is only displayed if I have the cursor over the topic's title, and not anywhere in the entire row of the topic in the list.

Just wanted to echo this sentiment. The current tooltip behaviour is highly annoying and not the slightest bit conventional.

---

### Post by glotz on 2006-10-31
Also on the subject of tooltips. When pointing at a topic, the tooltip shows the first few words of the topic. I used to think this feature made a lot of sense. However now, since the tags are introduced, I think the tooltip should rather show the tags than the first words.

---

### Post by slimdog360 on 2006-11-01
I like it, I can look at the first post without having to click on the thread and waiting for it to load.

---

### Post by 23meg on 2006-11-03
> At the very least, change the code so the tooltip is only displayed if I have the cursor over the topic's title, and not anywhere in the entire row of the topic in the list.That's exactly what should be done.

---

### Post by glotz on 2007-06-29
A polite little kick in the crotch is in order methinks...

---

### Post by saulgoode on 2007-07-06
> **Schluppy said:**
> Just wanted to echo this sentiment. The current tooltip behaviour is highly annoying and not the slightest bit conventional.

QFT

---

### Post by Happy_Man on 2007-07-20
> **23meg said:**
> That's exactly what should be done.
+1. Over the title of the post ONLY, not everywhere on the page. I swear.... if I was using Firefox, I would use Aysiu's tip. But I'm on Opera.... so I must battle on.

---

### Post by 23meg on 2007-08-27
I'm too busy to do it right now, but it would perhaps be possible to disable tooltips for ubuntuforums.org only with a Greasemonkey script. Any takers?

---

### Post by tribble222 on 2007-09-14
> **23meg said:**
> I'm too busy to do it right now, but it would perhaps be possible to disable tooltips for ubuntuforums.org only with a Greasemonkey script. Any takers?

Good idea!  I had some free time so I whipped up my first greasemonkey script ever.  Hopefully I didn't break any other parts of the website with it...

[http://userscripts.org/scripts/show/12249](http://userscripts.org/scripts/show/12249)

```

// ==UserScript==
// @name	Remove ubuntuforums.org tooltips
// @version	0.1
// @description	Removes annoying ubuntuforums.org tooltips
// @include	http://*ubuntuforums.org/*
// ==/UserScript==


var allTDs, thisTD;
allTDs = document.evaluate(
    "//td[@class='threadbit']",
    document,
    null,
    XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE,
    null);
for (var i = 0; i < allTDs.snapshotLength; i++) {
    thisTD = allTDs.snapshotItem(i).removeAttribute("title")
}
```

---

### Post by glotz on 2008-01-22
bump

---

### Post by KiwiNZ on 2008-01-22
Noted and filled

---

