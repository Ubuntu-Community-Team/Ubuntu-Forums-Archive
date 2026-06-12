---
title: "fortune forgetting to rot13 offensive files?"
date: 2009-03-29
forum: General Help
---

### Post by mythmon on 2009-03-29
I have fortune integrated into conky on my desktop. here is the offending line.
```
fortune -eacs -n 500 | fold -s -w50
```
Until a few days ago, this would work just fine, but now any of the fortunes that come from the fortunes/off folder are rot13 encrypted.

Now, the files in that directory are rot13ed, but until recently fortune would un-encrypt then when it read them. Any idea why it quit doing this? I could manually un-rot13 all of the files, but then next time I reinstall, it would start rot-13ing them again, and I would have to undo what I did. I would rather find the problem so I can fix it.

--Mike

---

