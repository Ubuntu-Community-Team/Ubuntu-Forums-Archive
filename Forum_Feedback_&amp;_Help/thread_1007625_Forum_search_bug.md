---
title: "Forum search bug"
date: 2008-12-10
forum: Forum Feedback &amp; Help
---

### Post by mssever on 2008-12-10
[This post]("http://ubuntuforums.org/showpost.php?p=6343549&postcount=5") alerted me to a bug in the forum. When you search for [FONT=Courier New][COLOR=Green]C++[/COLOR][/FONT], the forum silently turns it into a search for C. Searching for [FONT=Courier New][COLOR=Green]"C++"[/COLOR][/FONT] turns into a search for [FONT=Courier New][COLOR=Green]"C[/COLOR][/FONT] and the term [FONT=Courier New][COLOR=Green]"[/COLOR][/FONT].

---

### Post by jenkinbr on 2008-12-10
What it is doing is searching for "c  " < note the two spaces.  This has to do with the way GET and POST  variables are posted.

edit: this post might not be entirely right now that I realize that UF uses POST processing instaed of GET

---

### Post by mssever on 2008-12-10
> **jenkinbr said:**
> What it is doing is searching for "c  " < note the two spaces.  This has to do with the way GET and POST  variables are posted.

edit: this post might not be entirely right now that I realize that UF uses POST processing instaed of GET
That's not the case, because the browser will escape special characters before submitting them--that applies equally to GET and POST. Instead, it has something to do with the forum software itself.

---

### Post by jenkinbr on 2008-12-10
> **mssever said:**
> That's not the case, because the browser will escape special characters before submitting them--that applies equally to GET and POST. Instead, it has something to do with the forum software itself.
I realized my post was mostly wrong after posting it - hence the edit.

---

