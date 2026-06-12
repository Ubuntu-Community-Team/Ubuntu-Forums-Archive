---
title: "Gnome panel"
date: 2008-03-02
forum: Desktop Effects &amp; Customization
---

### Post by Pap3r on 2008-03-02
Earlier today I had my first go at editing the font color on the panel.  I followed a tutorial, forget which one, that was successful the first time.  It told me to change the font to Bold, which worked, but I decided I wanted a cleaner font instead, so I decided to see if arial worked.  I think I put it in the ```
text[NORMAL] = "#000000"
``` normal part, which I now realize is not for font... :)  I typed killall gnome-panel and awaited results.  Instead, however, I was stuck without panels; they didn't come back.  I also could not get them back.  

I cntr-alt-bkspc and try to log back in.  X starts, and the log in screen functions; however, once I log in, it seems like it is loading, compiz fusion splash comes up, and then it all stops.  I'm left with a black screen with a mouse.  I can rotate my cube, but nothing else.  It doesn't load in fail-safe either.  I can access the terminal, but I don't know what to do.

---

### Post by {BzF}~JOKesTER on 2008-03-05
At Login Screen Press

ctrl+alt+f1 --At Once--

Give Username And Password When Asked And Login.

Now Type:

```
for i in .gnome .gnome2 .gconf .gconfd .metacity; do mv $i $i.old; done
```

That Should Do It

Enjoy!!

---

### Post by Bachstelze on 2008-03-05
Above post edited, instead of harshly deleting your profile, it just moves it somewhere else so you can retrieve it if needed.

---

### Post by ugm6hr on 2008-03-05
> **HymnToLife said:**
> Above post edited, instead of harshly deleting your profile, it just moves it somewhere else so you can retrieve it if needed.

Sorry, I removed the post from the thread while you were editing.  Returned with your edits.

---

### Post by Pap3r on 2008-03-05
I figure it out; a while aog actually, just forgot to put solved in, thanks anyway.

However, is there a way to remove the nasty shadow effect on transparent panels?

---

### Post by Tenken on 2008-03-05
If you're using compiz you can use that to edit shadow effects, I think you need compizconfig-settings-manager or gnome-compiz-manager installed too.

---

### Post by Pap3r on 2008-03-05
Indeed; thanks.

---

