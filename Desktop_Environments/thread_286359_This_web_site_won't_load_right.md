---
title: "This web site won't load right?"
date: 2006-10-27
forum: Desktop Environments
---

### Post by elpuerco on 2006-10-27
When I go to this web site in IE everything displays correctly, but when at home on Kubuntu Edgy, (happened in Dapper too), the display looks like the attached image?

[http://www.justlets.com/properties_derby.htm]("http://www.justlets.com/properties_derby.htm")

I tried installing the user agent plugin but this makes no difference!

Any help or ideas?

Thnx

---

### Post by tturrisi on 2006-10-28
The page displays that way because the html code is incomplete.
If this is your code, try setting a width property for <div id="rightmove" style="width:xx;"

Somewhere earlier in the code the width is being controlled and the inline frame IS occupying 100% of the set width value.

```
<!--Info layer ------------------------->
<!-- InstanceBeginEditable name="RightmoveLayer" -->
<div id="rightmove" style="position:absolute; left:167px; top:121px; z-index:21; background-color: #990000; visibility: visible;">
<iframe id="rm" src="http://www.rightmove.co.uk/letsearch/9947" frameborder="0" width="100%" height="480" scrolling="yes"></iframe>

</div>
<!-- src="http://www.rightmove.co.uk/letsearch/9946" -->
<!-- src="http://www.d-ga.com" -->
```

Also, the pages that load in that inline frame do NOT have <body> witdh set.
[http://www.rightmove.co.uk/letsearch/9947](http://www.rightmove.co.uk/letsearch/9947)

---

### Post by elpuerco on 2006-10-28
Thanks, but this is not my site.

I found that if I right click and modify the frames display i get it to work ok

---

### Post by Blutack on 2006-10-28
Looks good in opera 9.  Are you using Konq or Firefox?

---

### Post by mdurham on 2006-10-28
take a look in Tools->Error Console

---

### Post by Blutack on 2006-10-28
Ah, fair enough.  Still, even ubuntu forums generate errors in opera console.

---

