---
title: "&quot;Check if Already Posted&quot; with special string in title triggers Forbidden"
date: 2017-12-07
forum: Forum Feedback &amp; Help
---

### Post by photonxp on 2017-12-07
I just entered the title for a post. The full title:
> exec >./test
Then I clicked the button of "Check if already Posted" right beside the title field. 
Post url:
> [https://ubuntuforums.org/search.php?do=process&forumchoice](https://ubuntuforums.org/search.php?do=process&forumchoice)[]=331&titleonly=1&query=exec%20%3E%20./test

For some reason the server wasn't happy with what I entered and returned a Forbidden page:
> **Forbidden**

 You don't have permission to access /search.php on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443


---

### Post by slickymaster on 2017-12-07
Can you please start the thread you intend with a more meaningful title. See the [Posting Guidelines]("http://Posting Guidelines")

As for the the issue you're getting, the culprit is the **_exec >./test_** part of that string.

---

