---
title: "HTML issue"
date: 2005-10-13
forum: Forum Feedback &amp; Help
---

### Post by imagine on 2005-10-13
Hi,
the threads have a title-attribute, so that you can read the first words in a tooltip when hovering over the thread with the mouse-cursor. That's a nice feature.
However the title-attribute is assigned to the td-element which is hidden behind two div-elements (threadname and authorname). I hope that picture makes it clearer, although I always sucked at ASCII-art.
```

-------------------------------------
| TD with title-attribute           |
| ********************************* |
| * inner DIV (linked threadname) * |
| ********************************* |
| ********************************* |
| * inner DIV (authorname)        * |
| ********************************* |
-------------------------------------
```

Ok now some browsers also show the title-tooltips of elements in the background (which have other elements above them), but other browsers as eg Opera don't. That means I have to hit the border of the td-element to read the title, because the other part of the td-element is hidden behind the two divs. No really big problem, but still it bothers me.
So would it be possible to assign the title-attribute (additionally) to the anchor-element which encloses the threadname?

Eg for the sticky-thread here:
```
<a href="showthread.php?t=4409" id="thread_title_4409" title="I would like to get other peoples input on stuff they would like to see here on the forums. :) So feel free to offer any suggestions, comments or ideas.. to make the forums rock even more.">Post your forum suggestions..</a>
```

Thanks.

---

### Post by kassetra on 2005-10-13
[quote=imagine]
Eg for the sticky-thread here:
```
<a href="showthread.php?t=4409" id="thread_title_4409" title="I would like to get other peoples input on stuff they would like to see here on the forums. :) So feel free to offer any suggestions, comments or ideas.. to make the forums rock even more.">Post your forum suggestions..</a>
``` 
Thanks.[/quote]

eeeeeh.  that may not be possible, but I'll look.  Everything on these forums is enclosed in template work... so maybe, but the forum links themselves might not be editable without a massive amount of hacking.

---

### Post by imagine on 2005-10-13
Ok thanks.
This isn't the first vBulletin-based forum I ask for this change, and in the others it was possible. But since I don't have any experience with the administration of vBulletin I don't know if they had to do some massive hacking or not. So can't help you here, sorry.

---

### Post by kassetra on 2005-10-13
[quote=imagine]Ok thanks.
This isn't the first vBulletin-based forum I ask for this change, and in the others it was possible. But since I don't have any experience with the administration of vBulletin I don't know if they had to do some massive hacking or not. So can't help you here, sorry.[/quote]

LOL We run a VERY customized version.  I will check though.

---

