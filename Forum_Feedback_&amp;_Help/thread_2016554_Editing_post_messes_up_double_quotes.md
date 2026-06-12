---
title: "Editing post messes up double quotes"
date: 2012-07-04
forum: Forum Feedback &amp; Help
---

### Post by sysmastr on 2012-07-04
Hello there,  once I try to write some Linux console stuff in code tags, like:  ```
 $ echo &quot;helloworld&quot; 
```  the double quotes are always replaced by '&quot' **after the post got edited** as you can see above. (I affirm I put TRUE double quotes in the part above. First it looked great, after editing my post it changed to this "quot" stuff.) This is why I switched to using single quotes now for the &quot;-T 'helloworld'&quot; line in my other thread  But since you are claiming to use a 2012 version of vBulletin, this problem should actually have been fixed aeons ago. For I can't see it in dozens of other forums based on vB either.  Maybe it's because you insist on HTML code (respectively auto-rewrite everything in HTML code) instead of the (usually used) BBcode.

---

### Post by sysmastr on 2012-07-04
THIS POST IS MEANT TO REMAIN UNEDITED.  ```
$ echo "this is a test"
```

---

### Post by sysmastr on 2012-07-04
As you can see, IT WORKS, as long as the post remains unedited. Now I will deliberately write a similar line and edit it ONCE:  ```
$ echo &quot;this is another test&quot;
```  {now edited once}

---

### Post by CharlesA on 2012-07-04
Are you allowing javascript?

Also, instead of an inline edit, have you tried clicking on "go advanced" and see if the quote tags get messed up.

---

### Post by coffeecat on 2012-07-04
> **sysmastr said:**
> Maybe it's because you insist on HTML code (respectively auto-rewrite everything in HTML code) instead of the (usually used) BBcode.

Not so. HTML is disabled globally in posts. You can post html code with syntax highlighting by using [noparse][html][/html] tags, but that's a different matter.

@sysmaster, I cannot reproduce what you are seeing, even after 8 edits of a post both inside and outside the ```

``` tags. I have occasionally seen "&quot" appear in posts instead of double-quotes, but not inside code tags. It is infrequent and because it only seems to affect some posters, it is perhaps a browser issue. If someone can shed light on this, it would be helpful.[/noparse]

One question - do you have greasemonkey Firefox extension enabled? I've noticed that can cause garbling of content between code tags.

---

