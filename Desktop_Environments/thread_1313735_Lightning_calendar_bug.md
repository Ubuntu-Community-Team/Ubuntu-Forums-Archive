---
title: "Lightning calendar bug"
date: 2009-11-04
forum: Desktop Environments
---

### Post by Ubunthree on 2009-11-04
Small calendar in Lightning's sidebar is showing incorrect days/dates.

That was for the benefit of the forum's cursor-hover preview thing. Here's the issue:

I'm not sure whether this is a bug in Thunderbird / Lightning, or just in my system. The small monthly calendar on the left side is not displaying correctly. The abbreviated days of the week along the top of the calendar are "Sa Sa Su Su Mo Tu We," and there are two day 1's at the start of the month. This means that day 2 is in the box where day 3 should be, and so forth through the whole month. The big, main calendar window is fine as far as I can tell. Now...

1) Within each session, the messed-up day abbreviations are consistent for every month as I scroll back and forth. Oddly, though, the first few times I started it, all seven days were "Sa."
2) The duplicated date problem occurs only for this month (November 2009).
3) If I scroll back a month, October's date numbers are correctly arranged, though the duplicated firsts of November are visible at the end.
4) If I scroll forward, December's dates (and the last two days of November) are also placed properly, though in the buggy November calendar, the first days of December are also displaced a day late.

I scrolled through a few years in each direction and didn't find any more months with duplicated first days. However, I do remember installing Lightning once before, maybe a year or so back, and running into the same issue then, which immediately killed my confidence in it as a calendar. I thought I would try it again now and see whether it had been fixed, but apparently not.

Is anyone else running into this, and if so, is there a fix?

(Jaunty, Tbird 2.0.0.23, Lightning 0.9)

Thanks!

(Edit) Here's a screenshot:

[IMG]http://ubuntuforums.org/picture.php?albumid=1465&pictureid=5106[/IMG]

---

### Post by Ubunthree on 2009-11-04
Now today I see that the day abbreviations are back to being all "Sa" again. And, I also notice that the date on the "Events" panel on the right side is tomorrow, not today. Unless there's some glitch in my installation specifically, I'm thinking that Lightning is not quite ready yet.

---

### Post by mrboojive on 2009-11-08
I've never seen this problem, but then again, I use Sunbird and not Lightning. If you're looking for a fix, I would try moving, renaming, or just deleting your Lighting profile and then seeing if you still get this problem. I'm not sure where the profile is located, but it is probably in .mozilla/lightning/ or somewhere under .mozilla/thunderbird/ (Sunbird's profile is in .mozilla/sunbird/). Something else you could try is moving or renaming your entire Thunderbird profile (don't delete it or you'll lose your emails). If Lightning worked right after that, then it would suggest that this is being caused by something weird with your Thunderbird setup. You might also check to see if there are any bug reports at Mozilla about this, or file one yourself. I did a quick search at [https://bugzilla.mozilla.org/](https://bugzilla.mozilla.org/) but I didn't see anything like you've described.

One the whole, I think the Calendar extension is pretty stable. I've been using Sunbird as my calendaring program for the past couple years and I've never had any major issues.

---

### Post by Ubunthree on 2009-11-08
Thanks for the response. I didn't find anything in the bug reports the first time I went through them either, but after I created an account and all just so I could file a report myself, I somehow ran across Bug 281690, which appears to be the same thing or something closely similar:

[https://bugzilla.mozilla.org/show_bug.cgi?id=281690](https://bugzilla.mozilla.org/show_bug.cgi?id=281690)

As far as I can tell from reading through this, it is being fixed in Lightning 1.0.

And just out of curiosity, I installed Sunbird from the repos, to see whether it had the same issue. It did, and was also stubbornly convinced that today, November 8, was November 9. Uninstalled it.

---

### Post by Ubunthree on 2009-11-10
Okay - I downloaded Thunderbird 3 Beta 4 just so I could try Lightning 1.0 (which is not compatible with Tbird 2), and the issue does appear to be fixed. At least, I haven't run into it in the scrolling back and forth that I've done so far. So that's a good thing. I think I'll continue using Evolution until both of these new versions are out of Beta, though.

I'm not sure where Lightning keeps its profile; I can't find a directory or file that looks relevant.

---

