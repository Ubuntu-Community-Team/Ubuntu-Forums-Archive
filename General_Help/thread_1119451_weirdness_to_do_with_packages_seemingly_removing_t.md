---
title: "weirdness to do with packages seemingly removing themselves...?"
date: 2009-04-08
forum: General Help
---

### Post by Karpah on 2009-04-08
OK, this is going to sound weird, but I have to try.

I'm a web developer, and as such I have Apache, PHP, PostgreSQL, etc. installed on my desktop. I sat down today to do some web development, only to find that I could no longer access my development sites that worked before.

First stop was to reload Apache. But Apache was not present on my computer anymore. 

Me: Huh?

I installed Apache, and then found that PHP was no longer installed. And then PostgreSQL. Etc. Etc.

Looking through the Apache logs to see what went bang, there's the usual dummy connections that stopped abruptly on February 22nd. This might be a long shot, but is there any way of seeing logs of what happened on my computer on that date, such as packages removed/added, or does anyone have any idea what might have happened, seeing as I *know* I did not remove the packages myself?

cheers,
Rebecca

edit: Yup, solved it, turns out I *did* remove them myself by accident... while in the process of removing kubuntu-desktop, I copied and pasted a long list of package names and removed them and yup they were all in there. At least it's a relief to know it was just my stupidity and nothing malicious! :D

---

