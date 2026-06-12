---
title: "R Question - Summary for a portion of the distribution"
date: 2009-05-04
forum: Education &amp; Science
---

### Post by FiReSTaRT on 2009-05-04
Googling and #R haven't been to helpful, so I'm hoping fellow-Ubuntu users will be able to help me out with this one.
The problem:
1) I have a dataset loaded into R
2) I want to calculate the summary stats for only the inner 90% (arbitrary figure) of the distribution of a variable, thus eliminating the outliers on each end.

Can anyone tell me how I would go about this?

P.S. I only need the mean, but I assume that it would still somehow go through the summary command.

---

### Post by FiReSTaRT on 2009-05-04
Never mind.. The *trim* argument seems to do the trick, as in mean(layer@data$MCGE, trim = 0.05).

---

### Post by gunksta on 2009-05-05
R is a great tool. But it can also be mind numbingly cryptic and Googling for R is often a complete and utter waste of time. That is why R-Seek is your friend.

[http://www.rseek.org/](http://www.rseek.org/)

You can also join the R mailing list which is a great way to annoy Google and make them constantly expand their Gmail account space. It's a very busy list, don't even try to read it all. It is conveniently populated with some very very smart people. Warning: Read the posting directions before posting and I suggest growing a bit of a thick skin. Comments can be direct and more than a little blunt, but the info is worth it. I learn just by lurking.

---

### Post by ahmatti on 2009-05-05
> **gunksta said:**
> I learn just by lurking.

This is what I do too :) I use the nabble interface to follow the R-mailing list, that way my mailbox is a little bit less full: [http://www.nabble.com/R-f13819.html](http://www.nabble.com/R-f13819.html)

---

### Post by gunksta on 2009-05-05
Oooh. I like that. Thanks.

---

### Post by FiReSTaRT on 2009-09-07
Ahhh I didn't even know about rseek. Definitely bookmarked. Thanks for the link!

---

