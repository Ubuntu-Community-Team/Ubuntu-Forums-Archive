---
title: "Strange html page"
date: 2008-11-04
forum: Development CD/DVD Image Testing
---

### Post by Nonno Bassotto on 2008-11-04
I'm trying to customize Konqueror start page for a live cd I am creating. It seems that the default page is located under
```

/usr/share/apps/konqueror/about/launch.html

```
The problem is that I don't understand how to edit that page since each content is replaced by a %1
For example you have
```

<td valign="bottom">
<a href="%1">
<img src="%1" height="%1" width="%1" /></a>
</td>
<td valign="bottom">
<a href="%1">%1</a>
<br>
<span id="subtext"><nobr>%1</span>
</td>

```
and so on.

What do all these %1 mean? I don't want to rewrite the whole page, because it has to look like the standard one, just with a couple of links changed.

---

### Post by Valodes on 2008-12-01
Man it's mean nothing ,, really u can replace it by # and this mean no URL ,, u will stay in the same page

---

### Post by Nonno Bassotto on 2008-12-01
Actually it seems that in Konqueror this is automatically replaced by the correct url... I don't know how it works, but it works in Konqueror only.

By the way, please reply in correct english, since it's harder for me to understand what you mean if you write this way (I'm not a native english speaker).

---

