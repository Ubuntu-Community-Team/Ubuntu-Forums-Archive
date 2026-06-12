---
title: "Forum search: Search in Forum and Search by Prefix are too small"
date: 2014-10-18
forum: Forum Feedback &amp; Help
---

### Post by R33D3M33R on 2014-10-18
If you take a look at the advanced search page, you can see that the boxes **Search in Forum** and **Search by Prefix** are tiny compared to the contents. They display 5 items at once, but the contents have 130+ and 70+ items. By adding **resize: both** into the CSS, the user can resize them freely. See images for more details.

[ATTACH=CONFIG]257334[/ATTACH]

[ATTACH=CONFIG]257333[/ATTACH]

---

### Post by bapoumba on 2014-10-19
Well, I suppose the idea is to have all the options available without having to scroll down too much. Not everyone has huge screen space,

---

### Post by R33D3M33R on 2014-10-19
But my idea is making the boxes resizable, nothing else would change ...

---

### Post by R33D3M33R on 2014-10-27
Bump. The code below is all you have to add to additional.css:
```

#forumchoice {
resize:both;
}
#prefixchoice {
resize:both;
}

```

---

### Post by bapoumba on 2014-10-27
Asked for some other admins input. Thanks for your patience :)

---

### Post by R33D3M33R on 2014-11-18
No problem :).

---

### Post by R33D3M33R on 2015-01-19
I'm surprised that such a simple fix and a major usability improvement takes so long. At least someone could write: "No, we won't do it". and we could forget this thread ever existed ...

---

### Post by bapoumba on 2015-01-19
Well, I'm no css specialist and vBulletin templates are a nightmare I wont happily venture into. If you see the forums broken, cheer me up :)

---

### Post by Elfy on 2015-01-19
> **R33D3M33R said:**
> I'm surprised that such a simple fix and a major usability improvement takes so long. At least someone could write: "No, we won't do it". and we could forget this thread ever existed ...

It's not that we didn't want to do this, but in addition to 
> **bapoumba said:**
> Well, I'm no css specialist and vBulletin templates are a nightmare I wont happily venture into. If you see the forums broken, cheer me up :)
this

We probably forgot about it somewhat. 

Anyway - have a look now.

---

### Post by Elfy on 2015-01-19
> **R33D3M33R said:**
> Bump. The code below is all you have to add to additional.css:
```

#forumchoice {
resize:both;
}
#prefixchoice {
resize:both;
}

```
Thanks R33D3M33R - sorry it took a while.

---

### Post by bapoumba on 2015-01-19
Thanks Elfy :)

---

### Post by R33D3M33R on 2015-01-20
It works great now, thanks! :)

---

