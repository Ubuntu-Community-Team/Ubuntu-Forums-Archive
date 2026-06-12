---
title: "PDF mail merge, print *many* fields from database"
date: 2009-03-19
forum: General Help
---

### Post by velmont on 2009-03-19
**I solved it, read solution in next post**

I've tried for a long time to do the following:

Our graphic-dude made a nice PDF, we're going to print ~30.000 versions of this PDF, all with different names on it (we're sending invoices to our members).

I've used many days and much frustration on this. This is how it should be:

[LIST]
[*]I make an FDF-file with 30,000 name-address pairs.
[*]I merge the PDF and the FDF (maybe with pdftk)
[*]I can send this new PDF to print
[/LIST]

What's important to notice is that I don't want to make 30.000 seperate PDF-files. The PDF is 5 MiB, so making seperate files would take almost 145 GiB. The network+printer+computer wouldn't handle that.

I also tried using OpenOffice mailmerge, by putting the PDF as background (however, the computer got totally bogged down by such a big job).

So... Any tips?

References:
[LIST]
[*][http://www.linux.com/feature/53701](http://www.linux.com/feature/53701)
[*][http://ask.metafilter.com/40802/Help-me-move-data-from-a-database-to-a-PDF-automagically](http://ask.metafilter.com/40802/Help-me-move-data-from-a-database-to-a-PDF-automagically)
[/LIST]

---

### Post by velmont on 2009-03-21
Wow, that was friggin easy!

I gave up.

Then I didn't really, so I read even more up on it. And instead of being obsessed by form filling I found out that IFPDF could get another PDF and put it as background. That's what I've been looking for.

But then I read the pdftk man page yet again, and WOW, it CAN put a pdf as a background.

So:

[LIST]
[*]Make a 30.000 page document with the fields filled in.
[*]Run pdftk on it, to use background.pdf as background on all of those 30.000 pages.
[/LIST]

And it works! The PDF doesn't get any bigger! w00t!

This is the command:

```
pdftk names.pdf background big_background.pdf output out.pdf
```

---

