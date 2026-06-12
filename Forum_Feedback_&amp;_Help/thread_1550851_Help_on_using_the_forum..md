---
title: "Help on using the forum."
date: 2010-08-11
forum: Forum Feedback &amp; Help
---

### Post by Isaacgallegos on 2010-08-11
I tried to get questions answered here, but the results were less than positive. 
[http://ubuntuforums.org/showthread.php?t=1550360](http://ubuntuforums.org/showthread.php?t=1550360)

I'm still left with questions, however I'm unsure how to proceed seeing how this thread was handled by the staff. 

If I want to talk further about my first post in that thread, so how would I continue with positive reception?

Thank you!

---

### Post by ibuclaw on 2010-08-11
If I were to slim your OP down to just one question:
> 
Is they any way of limiting employees' ubuntu accounts from executing files at the user level, which risks sensitive material?

The answer would be to suggest you looking at:
[LIST=1]
[*]Setting /home as noexec (if it lies on a separate partition)
[*]Have a look at [this page]("http://library.gnome.org/admin/deployment-guide") for tips on locking down the gnome desktop. Ideally, you'd want it all to be mandatory, so users can't change the restrictions you impose.
[/LIST]
Regards
Iain

---

### Post by Isaacgallegos on 2010-08-11
Thank you so much!

edit:
In the future I think I should keep questions to a single question. That's better, right?

---

### Post by bodhi.zazen on 2010-08-11
> **Isaacgallegos said:**
> I tried to get questions answered here, but the results were less than positive. 
[http://ubuntuforums.org/showthread.php?t=1550360](http://ubuntuforums.org/showthread.php?t=1550360)

I'm still left with questions, however I'm unsure how to proceed seeing how this thread was handled by the staff. 

If I want to talk further about my first post in that thread, so how would I continue with positive reception?

Thank you!

In the future, if you need support, ask for support, as outlined by ibuclaw .

This site is for Ubuntu support, not writing scripts to harm other people's property.

As I indicated on the thread in question, your original thread was closed for this post:

[http://ubuntuforums.org/showpost.php?p=9707258&postcount=7](http://ubuntuforums.org/showpost.php?p=9707258&postcount=7)

That post is not a support question and I interpreted your intentions as blatant disregard for forum policies regarding cracking / proof of concept as well as disrespect for other people's data.

See : [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

The post was so far off topic in fact the thread was closed.

If you need security assistance, that is fine, but self destructive behavior (writing malicious scripts) is not neither malware or even a security issue.

There is no solution to such behavior on any OS, if you wish to delete your data or write a malignant script and execute it as root -> neither software or hardware can protect yourself from your own bad behavior.

Now if you wish to learn about permissions or apparmor or selinux or any security issue, ask away.

---

### Post by Isaacgallegos on 2010-08-11
> **bodhi.zazen said:**
> This site is for Ubuntu support, not writing scripts to harm other people's property.

This line is evidence of a miscommunication, which as the writer is my fault. In the future I will try to be more clear. 

Back on topic: 
ibuclaw performed professionally and was able to quickly provide a reference. I will try to narrow problems down to a single question,  as he did in his reply; - solved.

---

### Post by bodhi.zazen on 2010-08-11
> **Isaacgallegos said:**
> This line is evidence of a miscommunication, which as the writer is my fault. In the future I will try to be more clear. 

Back on topic: 
ibuclaw performed professionally and was able to quickly provide a reference. I will try to narrow problems down to a single question,  as he did in his reply; - solved.

IMO your first post was marginal and you crossed the line regarding cracking and "proof of concept"

This is covered in this post:

[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

You writing a malignant script is you acting as a cracker, not asking for security support.

Suggesting that you would post such material on these forums, as in you last post, moved the conversation further off topic.

So while my post in the thread stirred the pot, the thread itself moved far enough away from security support that I closed it. While we could argue about semantics (is the script you suggested malware, proof of concept, etc ..) , the point is -

Please keep your posts on topic and relevant to security.

Please do not post "proof of concept" material here.

---

