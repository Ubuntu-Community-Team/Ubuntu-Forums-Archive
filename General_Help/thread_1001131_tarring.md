---
title: "tarring /"
date: 2008-12-03
forum: General Help
---

### Post by Phases on 2008-12-03
So. I've got a nightly backup of my web server going. It's a cron job running a script with a tar command, that's using -T with a places file that I add stuff too as I need.

It works great and is irrelevant to this question,  but for some reason I thought I'd mention it. 

Now, it dawned upon me as I debated when and how to make an image of the system, can't I just tar the root?  I imagine it would take time but could I do that on say.. a weekly or biweekly bases as a backup, onto an external drive? 

(obviously this will only work while my sites stay tiny ;))

Or can I not? 

What are complications/expectations of trying to do something like this? On backups and restoring. 

Thanks for any insight.

---

### Post by ibuclaw on 2008-12-03
I suppose it could work tar'ing root, though I'd rather just dd the filesystem to a file.

Also, there is a rather cool project called remastersys, which can act as a full backup (including personal setting/data).

Here is the project page: [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

I believe it is written in bash, so you if you only require the full system backup feature, you can snip that out and put it in your own script ;)

Regards
Iain

---

### Post by Phases on 2008-12-03
Hey thanks for the reply. I'll check that project out.

But, perhaps a dumb question, what's dd?

---

