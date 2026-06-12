---
title: "[SOLVED] printing pdf only prints one copy, no matter how many are selected"
date: 2008-12-03
forum: General Help
---

### Post by moore.bryan on 2008-12-03
well, the title says it all. i'm running intrepid at work and i've connected to a networked printer. i can print to the printer without problems, save one: no matter how many copies i select, it will only print-out one. i've tried evince, okular, epdfview, xpdf; all without luck.

any suggestions/ideas?

---

### Post by ohzopants on 2008-12-03
I had a sort-of-almost-kind-of-similar problem with printing pdfs from a windows computer to a network printer.  Whenever I tried to print a pdf, only the first page would print.

It turned out that I was using the wrong driver.  I was using a driver for HP4000 when the printer is in fact an HP4100.

This may or may not help you, but make sure you are using the correct driver.

---

### Post by moore.bryan on 2008-12-03
thanks for the response... that was the first thing i tried, since i'd seen other posts in other forums talking about that being an issue in xp/vista. unfortunately, i've got the right make, model, and driver. it doesn't do it in any other program or for any other files, just pdf's.

and the issue isn't it only printing page one, it's when i select to print more than one copy--even of a single-page document--it only prints one copy.

---

### Post by ohzopants on 2008-12-03
Does it show up and appear to complete normally in the print queue?

---

### Post by moore.bryan on 2008-12-04
yup. everything appears **completely** normal until i head-over to the printer to find only one copy printed.

_EDIT_:
so i figured what have i got to lose, but time and went through *every single one of the "other" drivers listed for my hp4100 laserjet networked printer* and, voila, one of them works properly. now, i'm just left to wonder why the "recommended" driver didn't work, but one of the random other ones did...

---

### Post by RichardG891 on 2009-10-14
I'm not in the habit of replying to old posts (honestly!) but in case anyone new stumbles on it, I've come across this problem as well when using the Generic PCL drivers with postscript/PCL networked lasers. I think it's a "lost in translation" problem - if you set the number of copies in the Job Options section of the printer properties page (default is 1) it will print that number, regardless of how many you told it to print via the application's menu.

---

### Post by moore.bryan on 2009-10-14
That's okay... I've found none of my drivers or HP's work now after going to Jaunty over the summer. I'll try your "trick" and see if it works for me, though!

---

### Post by moore.bryan on 2009-10-16
An upgrade to Karmic has this working out of the box now, so I'm leaning towards the whole thing being a Jaunty miscommunication.

---

