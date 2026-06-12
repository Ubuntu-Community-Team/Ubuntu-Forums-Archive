---
title: "How to use SCIM Chinese input?"
date: 2009-02-27
forum: Desktop Environments
---

### Post by matthew_exon on 2009-02-27
Is there any English-language documentation anywhere on how to actually use the SCIM Chinese input stuff?  It's very confusing, and I'm only a beginning Chinese learner so I'm not used to how Windows does it.  I can't even read the names of the Chinese input engines, since they're all in Chinese!

There's one engine that seems fairly intuitive.  It allows me to type "pinyin" and get the word "&#25340;&#38899;", and insert that word with the space bar, or a different word with the same pinyin by typing a number.  But when I type "nu" I don't get "&#22899;".  Possibly this is because the pinyin isn't "nu" but "nü".  But typing "nü" doesn't work either.  I have the same problem with other "ü" words.

I'd also like to be able to type characters by strokes, but I have no idea how to enable that.

Is this stuff documented anywhere?

---

### Post by kentty on 2009-02-27
Pls choose “(System) --> (Administration) --> (language support)”.
choose the&#65288;Chinese&#65289;in list. 
And enable support to enter complex characters.
update and upgrade.
Ubuntu will download all need. 

You can use "v" to instead of "ü" to write what you need.

If you want to type characters by strokes.
One way, you can install scim and find the "wnwb.bin" by google.
Put "wnwb.bin" to "/usr/share/scim/tables", so you can enble the Wubi input.

PS, sorry for my poor english, but hope it can help you.

---

### Post by matthew_exon on 2009-02-28
Aha!  That "v" thing is exactly what I was missing.  That'll help a lot, thanks!

I already seem to have wubi installed, but I can't figure out how to use it.  What strokes are on what keys?  It unfortunately doesn't seem to do the same thing as my phone, and display a list of the strokes typed so far.

P.S., Apologies for my poor Chinese ;-)

---

### Post by kentty on 2009-02-28
The "wnwb.bin" include "pinyin" and "wubi" input, the two type way.
It means that you can type in "pinyin" or "wubi", not any exchange.

And the "wubi" type is one of the stroke way. You can know more about it by google.
For example, look for "&#20116;&#31508;&#23383;&#26681;&#34920;" by Images search. You will know what strokes are on what keys. It's a fast way to input chinese.
For phone, I don't know how to use it. You also search other way for strokes input.

what strokes are on what keys:(FYI.)
[IMG]http://dl.getdropbox.com/u/325330/wubi/86%20%E4%BA%94%E7%AC%94%E5%AD%97%E6%A0%B9%E8%A1%A8.jpg[/IMG]

---

### Post by matthew_exon on 2009-02-28
OK, I get it.  The wikipedia article on "Wubi method" seems good.  Thanks for the pointers!

---

