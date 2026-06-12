---
title: "noob question: how to load, not replace"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by TXBDan on 2007-06-26
Hey guys,

Where can i config the defaults for when the ubuntu gui loads? as it is now, i have compiz and emerald both using '--replace' in the session manager.. isnt it a little silly to load one thing, and then reload it? or am i missing something? i think id rather have it just load compiz/emerald from the get go..

---

### Post by mid_night gypsy on 2007-06-26
TXBDan,
 Man, I like your thinkin' on that.For me there are to many files,scripts to edit or gedit for that matter. You must know that Compizfusion is beta (heavy-testing) in time it will break and when it does it will leave your system useless as tits on a boar-hog, I would leave metacity (ubuntu,gnome's window deco) a lone. In sessions delete the emerald one and on the compiz one edit with this command. Hope this helps, gypsy
 ```
compiz --replace -c emerald &
```

---

