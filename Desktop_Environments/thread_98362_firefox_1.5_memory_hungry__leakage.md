---
title: "firefox 1.5 memory hungry / leakage"
date: 2005-12-03
forum: Desktop Environments
---

### Post by towsonu2003 on 2005-12-03
1.0.7 was buggy and slow and had memory leaks all over... so:

I installed 1.5 using this: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

Now I am looking at my conky memory monitor and, well, let's say I try not to curse :) 

Before installing firefox, my average memory usage was **210MB**, using **epiphany** with 5 tabs on average + gaim + liferea, never closing any of these apps...

Under same conditions, using **firefox** with 4 tabs (did not close now for about 2,5 hours) instead of epiphany, memory averages to **315MB** and increasing!

Firefox (right now) uses about 137.4MB memory (this according to System Monitor - top gives 2MB less :) ). x.org and others stay about the same. 

Anyone with these symptoms? Any workarounds before I file a bug report with firefox?

PS. I'm aware ubuntu (very probably) has nothing to do with this...

[Edit]--------------
Shutting down firefox takes total memory down to 239MB
(10 seconds later)Just launching firefox takes total memory up to 250MB
(15 seconds later)Opening ubuntuforums.org takes total memory up to 252MB
(1 minute later)Openning up 4 more tabs and going to amazon.com & bbc.co.uk & msn encarta & towson university web sites takes total memory up to 261MB
(1 minute later)Closing these 4 tabs and leaving ubuntuforums takes total memory down to 259MB

So, is this memory leak? does it happen to you?

---

### Post by mustang on 2005-12-03
Right now I have 28 tabs open (doing a research paper) and firefox is taking up 137mb of virtual memory. So no, I am not experiencing the same problem you are. The last time I had a memory leak in firefox was on windows.

---

### Post by towsonu2003 on 2005-12-10
I found a hell lot of threads suggestiong to remove adblock and install adblock plus for this issue in mozilla forums. did that but did not work for me... and, I have to tell, they are VERY SENSITIVE (read: will kick your a**) when it comes to this memory leak issue :) so not realy helpful :) am i used to ubuntuforums to much or what??

---

### Post by Rackerz on 2005-12-10
Are you running Firefox 1.5 without plugins and extensions? Or do you have some installed?

---

### Post by towsonu2003 on 2005-12-10
I have the plugins described in wiki's NewFirefoxVersion. The extensions now are: 

DOM - disabled (was enabled when first posted)
Talkback - disabled  (was enabled when first posted)
NoScript
Flashblock
User Agent Switcher
Google Toolbar (was not installed when first post)
Adblock - removed (was installed when first post)

edit/// Forgot this: firefox --safe-mode reduces total memory by 2 MB (so, if total memory used was 254MB, in safe mode it is 252MB). But don't know if there is memory leak (I kinda dont wanna run fx for 3 hours in safe mode:) would that matter?

---

### Post by arthur_kalm on 2005-12-13
I'm having a similar problem. I'm using the binary off of the Firefox site.

Firefox starts out at 50 mb and slowly climbs as I browse. After about 6 hours I start swapping :(. When I check top Firefox is taking up 180 - 200 mb.

This would be fine as I have 512 mb of ram, but unfortunately it seems that as Firefox's memory usage climbs for some reason so does xorg's. Xorg takes more memory than Firefox!! If I close Firefox the memory clears up and drops to 40%. I have read somewhere that Firefox's new "fastback" feature (which caches previous pages, I assume into memory) is responsible for this. I haven't found a way to turn it off yet, if anyone knows how to turn it off I would love to see if it helps.

Here is a list of extensions I'm using:
- DOM inspector (came with firefox)
- Talkback (came with firefox)
- FlashGot
- Adblock
- PDK Download
- Download Statusbar
- Flashblock
- Viamatic foXpose
- Mouse Gestures
- CuteMenues - Crystal SVG
- Dictionary Search
- Tabbrowser Preferences
- SessionSaver
- View formatted source
- FormFox
- Find Selection
- Fasterfox (installed recently, was slow before this was installed)

Can anyone using a clean install confirm these memory usages?

---

### Post by pataphysician on 2005-12-14
[QUOTE=arthur_kalm]I have read somewhere that Firefox's new "fastback" feature (which caches previous pages, I assume into memory) is responsible for this. I haven't found a way to turn it off yet, if anyone knows how to turn it off I would love to see if it helps.[/QUOTE]

i'm not running 1.5 so i can't confirm, but have you tried about:config in the addressbar. lots of options there.

edit: apparently the option is call "browser.sessionhistory.max_viewers" and it should be set to 0

---

### Post by arthur_kalm on 2005-12-14
I forgot to mention that I followed [http://www.freerepublic.com/focus/f-bloggers/1327586/posts](http://www.freerepublic.com/focus/f-bloggers/1327586/posts) and it has done absolutely nothing :P

I also looked a tried to disable caching but then kde-look.org won't load :P

Anyone have any other ideas or know the about:config entry?

---

### Post by Sokraates on 2005-12-14
Memory leakage is an old and well known problem and [numerous bugs](https://bugzilla.mozilla.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=Firefox&content=memory) have been files on bugzilla on different aspects.

The real problem is, that noone really knows how memory leakage appears or why. If you suffer from it, it's always reproducable. If you don't, you'll propably never encounter it. There are plugins and extensions (like ad-block) that consume a lot of RAM on their own, but the true leakage is caused by FF itself.

This is also the reason why this is a very sensitive topic on the forums. I've been with FF since 0.91 and this problem has been discussed hundreds of times to no avail and a lot of members are simply frustrated. Mostly because there is absolutely no way to help.

The devs are working on this and a few fixes have already been check in. Some caused regressions and had to be removed while others successfully fixed leakages from appering under certain conditions. Still the one error that causes all this in the first place has eluded them yet.

---

### Post by arthur_kalm on 2005-12-14
I can understand that memory leakage is a frustrating problem but I think that this doesn't have to do with a memory leak.

I notice that when I browse image intensive websites like kde-look.org the RAM usage begins climbing steadily until it gets to the point where it starts to swap and then it gets really slow.

I didn't notice this problem with 1.07 and it seems to do with the "Fastback" feature. If there is a way to either turn it off completely, or, better yet, limit the amount of RAM that can be used for this feature that would more helpful.

---

### Post by towsonu2003 on 2005-12-15
did I post this before? sorry for the delay, but everything is so slow with dial up, you forget what your gonna do before the page comes up :)

You may want to vote / comment to these bugs to help bugzilla -This should help developers solve our problem: 
[https://bugzilla.mozilla.org/show_bug.cgi?id=319262](https://bugzilla.mozilla.org/show_bug.cgi?id=319262) (memory leak)
[https://bugzilla.mozilla.org/show_bug.cgi?id=319259](https://bugzilla.mozilla.org/show_bug.cgi?id=319259) (memory usage)

You could also search for similar bugs and vote / comment for them. 

I found a couple of workarounds in firefox' website, but none works...

PS. For those who have limited RAM (under 320MB?), I suggest Epiphany till this is fixed, although it lacks couple of features :)

---

### Post by arthur_kalm on 2005-12-16
Thank you for the heads up. I added in my findings to the memory leak bug report. Hopefully we can figure this out. I shall post back when more information becomes available.

---

