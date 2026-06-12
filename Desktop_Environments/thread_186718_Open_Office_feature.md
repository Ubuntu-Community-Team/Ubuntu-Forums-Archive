---
title: "Open Office feature"
date: 2006-06-02
forum: Desktop Environments
---

### Post by jethro10 on 2006-06-02
hi,
been trialing open office on Ubuntu as a replacement for Office on windows, but have come across a problem that the open office forum was unable to answer.

In MS office there is two storage areas for templates. Local and Workgroup. Local on your local drive and workgroup on a network share.

I can't find how to replicate this in OOo, just get local ones. The answer, if there is one, needs to be a generica OOo answer I feel, as some users may stay on windows for compatibility to our accounting s/w.

anyone any ideas ?
Jeff

---

### Post by lkagan on 2006-06-02
Good morning.  You pose an interesting question so I just tried something that worked perfectly.  Local templates as you probably know are located in ~/.openoffice.org2/user/template/.  Well you can simply have your remote (shared) directory of templates and use a symlink (ln -s) to create a subdirectory under the template directory and OOo can see it.  I just tried it and it works.  So you would do something like this:
```

mount -t smbfs //SomeWinServer/SomeShare/ /mnt/SomeShare
ln -s /mnt/SomeShare/OfficeTemplates ~/.openoffice.org2/user/template/Shared

```
Then fire up OOo and you'll see the shared directory when you click on the 'Templates' icon in your 'Templates and Documents' dialog box.

Hope this helps.

Larry

---

### Post by jethro10 on 2006-06-02
[QUOTE=lkagan]Good morning.  You pose an interesting question so I just tried something that worked perfectly.  Local templates as you probably know are located in ~/.openoffice.org2/user/template/.  Well you can simply have your remote (shared) directory of templates and use a symlink (ln -s) to create a subdirectory under the template directory and OOo can see it.  I just tried it and it works.  So you would do something like this:
```

mount -t smbfs //SomeWinServer/SomeShare/ /mnt/SomeShare
ln -s /mnt/SomeShare/OfficeTemplates ~/.openoffice.org2/user/template/Shared

```
Then fire up OOo and you'll see the shared directory when you click on the 'Templates' icon in your 'Templates and Documents' dialog box.

Hope this helps.

Larry[/QUOTE]
Hi, never thought of a link, thats fine.
Now just the 5 windows XP users, wonder what I can do for them that's similar..........

Jeff

---

### Post by simonn on 2006-06-02
Throw rocks at them? :)

Why not a short cut to a network share?

---

### Post by lkagan on 2006-06-02
[QUOTE=jethro10]Hi, never thought of a link, thats fine.
Now just the 5 windows XP users, wonder what I can do for them that's similar..........

Jeff[/QUOTE]

Hi ho... hi ho.... it's off to [MS Office Forums]("http://reviews.cnet.com/5204-6129-0.html?forumID=29&start=0") you go!

Larry

---

### Post by jethro10 on 2006-06-05
[QUOTE=lkagan]Hi ho... hi ho.... it's off to [MS Office Forums]("http://reviews.cnet.com/5204-6129-0.html?forumID=29&start=0") you go!

Larry[/QUOTE]
Yep your right.
But Can I say to them?

"Hi , can you tell me how to do ABC so I can dump lots of windows PC's ?"

hmmm...
J

---

