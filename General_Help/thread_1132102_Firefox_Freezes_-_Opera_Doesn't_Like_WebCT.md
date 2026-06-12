---
title: "Firefox Freezes - Opera Doesn't Like WebCT"
date: 2009-04-21
forum: General Help
---

### Post by Skootle on 2009-04-21
Hi!

I've got a bit of a problem. I've tried searching google and these forums a bit, but don't really have the time to do so in depth since I have exams in a week now. So if this has already been asked, please just point me in the right direction, thanks!

So, yesterday I dropped my laptop (Dell Inspiron 1520) from about 12 inches high while it was on (I know, stupid me...). Turns out, everytime I open firefox it completely jacks the whole computer after around 10 seconds trying to actually open up the browser. Best case scenario, I control + alt + backspace and relogin, worst case scenario I have to force the computer to restart. Weird thing is, this ONLY happens with firefox, not a single other program (others work perfectly: VLC, Totem, Amarok, Opera which I'm using now, Deluge, Qalculate!, terminal, etc.).

I then tried uninstalling firefox, purging it and then reinstalling. The exact same thing happened...

In reality, I wouldn't really care (I can just use Opera which I like a lot), but there's a problem: I need to access my university's WebCT but, once I log on (successfully, no problems yet) and I try to download a PDF file, the screen just kind of goes blank, loading (not like Opera freezing, more like waiting for the server to reply) but I've tried with SeaMonkey and it works fine (so it's an Opera thing, not server-side).

Any ideas as to how I can solve one problem, the other or both?

Thanks!

---

### Post by codeseer on 2009-04-21
Well that's strange with Firefox. Did you also delete the .mozilla folder from your home directory after removing, before reinstalling, Firefox? Also have you tried a different profile:

```
firefox -profilemanager -no-remote
```

On a side note, with Opera, what happens when you right click on a PDF link and choose the 'save as' or whatever it is in Opera?

---

### Post by ajgreeny on 2009-04-21
Was firefox running when you dropped it?  If so it may have been writing to disk at the time and your profile could be corrupt, so follow codeseer's advice and rename your ~/,mozilla folder as ~/.mozillaold and restart firefox.  A new profile will be made and then you can copy the important files back to the new profile, eg your bookmarks (now *places.sqlite* not *bookmarks.html*)

---

### Post by Skootle on 2009-04-22
thank you so much, it seems to work now :)

---

