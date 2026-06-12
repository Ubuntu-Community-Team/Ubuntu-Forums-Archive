---
title: "&quot;SOLVED&quot; button ... (it is not what you think...)"
date: 2009-07-27
forum: Forum Feedback &amp; Help
---

### Post by LepeKaname on 2009-07-27
Please don't close/move/remove/disintegrate this thread, please read.

I'm aware that the "[SOLVED]" button/link was removed because of performance issues: [http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

But still there are plenty of people (including me) that want to use that feature. We know that these are the only ways to do it right now:

1) to go back to the first post, edit -> go Advanced and then add "[SOLVED]" to the title. 
2) Adding the Tag solved 

Adding a tag is faster than the first one, but still is not the "common" way, not easy to find, and we end now with 2 different methods.

As many (much) of the people asking for help are new (or almost new) in this forum, we need a way to make it visible. That way, we can help them better.

If modifying your own title is not hitting the server load, then just add the "SOLVED" button (pretty visible), and when clicking on it, let the code to pre-append automatically the "[SOLVED]" string to the title:

```
UPDATE threads SET title = CONCAT("[SOLVED] ",title) WHERE thread_id = $id
```

And that's all! ... of course one more line should be added to the php code:

```
$solved_button = (strpos($title,"[SOLVED]") === false)?true:false;
```

With those simple 2 lines (almost), we all can be beneficed of the "SOLVED" feature.

Who agrees/disagree? 

-----------------------------------------------------------------
"SOLVED" related threads:
[http://ubuntuforums.org/showthread.php?t=1207190&highlight=solved](http://ubuntuforums.org/showthread.php?t=1207190&highlight=solved)
[http://ubuntuforums.org/showthread.php?t=1195792&highlight=solved](http://ubuntuforums.org/showthread.php?t=1195792&highlight=solved)
[http://ubuntuforums.org/showthread.php?t=1197010&highlight=solved](http://ubuntuforums.org/showthread.php?t=1197010&highlight=solved)

---

### Post by LepeKaname on 2009-08-02
BUMP :confused:

---

### Post by Tipped OuT on 2009-08-02
I think this sounds like a great idea.

---

### Post by isee on 2009-08-05
I'm a relatively new user, and am frustrated right now trying to add "solved" to my question.  I know I am supposed to do this, and have been able to do so before, but it seems I have to spend time searching for how to add it every time I post a question, which is not very often so I can't remember.

Where is the Tag option again?

Just my two cents.

---

### Post by snova on 2009-08-05
> **isee said:**
> I'm a relatively new user, and am frustrated right now trying to add "solved" to my question.  I know I am supposed to do this, and have been able to do so before, but it seems I have to spend time searching for how to add it every time I post a question, which is not very often so I can't remember.

Where is the Tag option again?

Just my two cents.
Under the "New Reply" button is Bookmarks and then Tags; at the far right of that bar click Edit Tags.

---

### Post by Bodsda on 2009-08-05
> **LepeKaname said:**
> Please don't close/move/remove/disintegrate this thread, please read.

I'm aware that the "[SOLVED]" button/link was removed because of performance issues: [http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

But still there are plenty of people (including me) that want to use that feature. We know that these are the only ways to do it right now:

1) to go back to the first post, edit -> go Advanced and then add "[SOLVED]" to the title. 
2) Adding the Tag solved 

Adding a tag is faster than the first one, but still is not the "common" way, not easy to find, and we end now with 2 different methods.

As many (much) of the people asking for help are new (or almost new) in this forum, we need a way to make it visible. That way, we can help them better.

If modifying your own title is not hitting the server load, then just add the "SOLVED" button (pretty visible), and when clicking on it, let the code to pre-append automatically the "[SOLVED]" string to the title:

```
UPDATE threads SET title = CONCAT("[SOLVED] ",title) WHERE thread_id = $id
```

And that's all! ... of course one more line should be added to the php code:

```
$solved_button = (strpos($title,"[SOLVED]") === false)?true:false;
```

With those simple 2 lines (almost), we all can be beneficed of the "SOLVED" feature.

Who agrees/disagree? 

-----------------------------------------------------------------
"SOLVED" related threads:
[http://ubuntuforums.org/showthread.php?t=1207190&highlight=solved](http://ubuntuforums.org/showthread.php?t=1207190&highlight=solved)
[http://ubuntuforums.org/showthread.php?t=1195792&highlight=solved](http://ubuntuforums.org/showthread.php?t=1195792&highlight=solved)
[http://ubuntuforums.org/showthread.php?t=1197010&highlight=solved](http://ubuntuforums.org/showthread.php?t=1197010&highlight=solved)

If thats all it takes then I think it is an excellent suggestion

---

### Post by konqui on 2009-08-06
I support this idea. It is very irritating to reply threads for no reason. The majority of forums nowadays have that feature and it's a pity ubuntuforums no longer has.

---

### Post by Bodsda on 2009-08-06
> **konqui said:**
> I support this idea. It is very irritating to reply threads for no reason. The majority of forums nowadays have that feature and it's a pity ubuntuforums no longer has.

Well yes a lot of forums may have this feature, but the problem is due to the forums size. So I think we should be congratulating UF for getting so big that they have to disable these features :)

And then kindly ask them to create a similar feature that can handle massive databases.

---

### Post by LookTJ on 2009-08-09
I think this is a great solution to the solved feature :)

---

