---
title: "dapper clean install using old breezy home file"
date: 2006-03-08
forum: Desktop Environments
---

### Post by markymarknz on 2006-03-08
Hi everyone,

This might be a simple question for some people but I was just wanting to go over a few things before attempting to do this myself.

From what I understand if I blow away the breezy partition and keep the /home partition can I then install dapper from cd and use the existing /home partition when prompted to setup the partitions?

If so will that keep my desktop theme settings? I have a really nice desktop setup and was hoping to keep the themes and cursors. I know I will have to setup all the programs like firefox and stuff again but just in terms of the looks will it stay the same or able to change back using the information in my /home folder?

Thanks in advance :)

---

### Post by o_fortuna on 2006-03-08
[QUOTE=markymarknz]Hi everyone,

This might be a simple question for some people but I was just wanting to go over a few things before attempting to do this myself.

From what I understand if I blow away the breezy partition and keep the /home partition can I then install dapper from cd and use the existing /home partition when prompted to setup the partitions?

If so will that keep my desktop theme settings? I have a really nice desktop setup and was hoping to keep the themes and cursors. I know I will have to setup all the programs like firefox and stuff again but just in terms of the looks will it stay the same or able to change back using the information in my /home folder?

Thanks in advance :)[/QUOTE]
If, when you installed Ubuntu for the first time, you created a separate partition for /home, then yes, and it will keep all your desktop settings, bookmarks, etc.

The Dapper installer has the capability to keep your /home partition without changing it. But remember, it has to be a separate partition. You can check in GParted.

---

### Post by markymarknz on 2006-03-08
Great thanks for the fast reply.
I'm pretty sure that the partitions are separate but I will check when I get home.
Most people feel that dapper is stable enough to use as your main OS now eh?

---

### Post by Xian on 2006-03-08
[QUOTE=markymarknz]Most people feel that dapper is stable enough to use as your main OS now eh?[/QUOTE]

I would strongly advise against that perspective. It is (fairly) stable at present but that could easily change with a single day's update. It is a project heavily in development and has not even reached the beta stage, so by any reasoned opinion it should be approached cautiously. If you are just wanting to run it for fun and testing then that would be fine, but otherwise have backups in place.

---

### Post by sandyeggoboy on 2006-03-09
[QUOTE=o_fortuna]If, when you installed Ubuntu for the first time, you created a separate partition for /home, then yes, and it will keep all your desktop settings, bookmarks, etc.

The Dapper installer has the capability to keep your /home partition without changing it. But remember, it has to be a separate partition. You can check in GParted.[/QUOTE]


Question: is there any way to go back and create the /home partition and then will it begin saving things there from then on?

Thanks,

Deric Stowell

---

### Post by markymarknz on 2006-03-09
Thanks for the info guys,
I unfortunately didn't have time to check it out last night. 

But Deric's question got me thinking. In the off chance that I just lumped my ubuntu installation under one partition can I not just tar the home files save them on a usb key or something, blast away the whole breezy partition, create a new dapper partition (with a home partition) then rewrite the dapper home partition by untarring my home files?

Yeah sorry its a bit long winded, hopefully you get what I mean ( I think its similar to what Deric was wondering)

Thanks

---

