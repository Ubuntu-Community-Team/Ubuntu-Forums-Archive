---
title: "need help with calculation  in shell"
date: 2009-05-25
forum: General Help
---

### Post by siuchi on 2009-05-25
I need to do some adding from a file in shell.

For example i have a file called number_file and inside i have the following number:

1
2
3
4
5

The question is, how can i adding all the number and display in shell?

Sorry about my bad english, hope it can be understand. Many of Thanks

---

### Post by KhurramM on 2009-05-26
use awk for this purpose

U can easily see tutorials on awk across the web.

Hope this helps.

---

### Post by ushimitsudoki on 2009-05-26
awk '{sum+=$1}END{print sum}' number_file

How's that? :)

---

