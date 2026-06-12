---
title: "Are attachments broken?"
date: 2013-10-24
forum: Forum Feedback &amp; Help
---

### Post by Lars Noodén on 2013-10-24
Are attachments broken?  I've tried to attach a small PNG, GIF and text file to a thread but have no luck.  Here is a sample error message:

[indent][i]
The following errors occurred:

screenshot.gif: Upload of file failed. Was your file larger than the permitted (1024x768 for images)?
[/i][/indent]

The files have all been of acceptable size and format yet get rejected by the upload software anyway.

---

### Post by cariboo on 2013-10-24
We are aware of the problem, if you try to upload 2 or 3 times, it usually will go.

---

### Post by hloeung on 2013-10-24
[ATTACH=CONFIG]247212[/ATTACH] - works for me.

---

### Post by hloeung on 2013-10-24
Lars, does it work now?

I fixed permissions of one of the directories on one of the forum frontends, if that makes sense. I think it was related to that, but if it's not fixed, I'll try dig deeper.

---

### Post by Lars Noodén on 2013-10-25
Seems to be fixed.  Thanks.


The add attachments window doesn't close using the "close" button it has.  Closing the tab in the browser worked ok though.

---

### Post by cariboo on 2013-10-25
I tried to upload an attachment last night, but ran out of time after failing 3 time. Today I had to try twice before my 1024X768 screenshot uploaded.

---

### Post by bapoumba on 2013-10-26
Same here. Needs at least 4 or 5 tries before it goes through.

---

### Post by hloeung on 2013-10-27
Track this down to the file uploads directory on one of the FEs was being removed by one of the sync scripts. It then falls back to /tmp but that fails because we've configured it to fail - "PHP Warning:  Unknown: open_basedir restriction in effect. File(/tmp) is not within the allowed path(s):".

It should be fixed for good now.

---

### Post by coffeecat on 2013-10-28
@hloeung, thanks for tracking this down. That's really good news.

Test - one of the Saucy wallpapers, original = 2560x1600, to test both upload and auto-resizing of image to permitted maximum:

[ATTACH=CONFIG]247328[/ATTACH]

That seems to work fine.

---

### Post by varunendra on 2013-10-28
Not sure since when, but it used to always fail for me if I used the upper "Upload" button marked in red circle (never tried more than twice though).

But always successful if I used the lower one. Although the "Close" buttons (both the top and bottom one) always worked for me here on chromium.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=247332[/IMG]

Thought about reporting it a few days ago, got disconnected before I could, didn't think of it again..

For this example though, both buttons seem to work now. Thanks for helping us hloeung ! :)

---

