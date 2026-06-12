---
title: "Checking/managing my /var/mail"
date: 2005-06-08
forum: Desktop Environments
---

### Post by astronerd on 2005-06-08
Hi all, I am fairly new to linux and I still havent been able to figure out how to check and manage my var/mail/usrname  .  Is there some way that gives  you an easier gui than the terminal?  If there isnt can someone please do a step by step as to how to check and delete etc. messages there?  I am using gkrellm and I see that I have messages, but I have no idea how to access them(if possible through gkrellm....).  Thanks, Charles

---

### Post by alastair on 2005-06-08
Your local mail spool (/var/spool/mail) should be OK managed from applications like thunderbird, evolution, mutt etc.

I think one main thing is to make sure your /etc/aliases (mail aliases) file redirects "root" to your admin user e.g. contains :

root:   <your username>

If it doesn't, add the line and run "sudo newaliases".

You can add extra "accounts" to pick up local mail in thunderbird, evolution etc. to read from the local mail spool. Unfortunately, I don't use these (I use mutt) so cannot direct you explicitly - but a new "mail account" I think to pick this stuff up (I've set it up for a colleague before).

---

