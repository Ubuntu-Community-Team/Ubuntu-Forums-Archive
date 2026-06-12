---
title: "SQL Injection Blocker"
date: 2009-04-06
forum: General Help
---

### Post by CrusaderAD on 2009-04-06
I know the best prevention for SQL injections is good code, but is there anything else we can use? I've seen a few 3rd party programs, here's one: [http://www.sqlinjectionhelp.com/]("http://www.sqlinjectionhelp.com/"). Is there anything for Ubuntu?

---

### Post by hellz99 on 2009-04-06
I don't think I would use that program from your link.
What language are you programming in?

For the most part, if you're using prepared statements you're safe.  A lot of the major sql mapping frameworks out there use prepared statements.  I use iBatis, but there are others like hibernate.

---

### Post by CrusaderAD on 2009-04-06
We're programming in PHP, but we also use ASP on our windows servers. Thanks for the info, I'll check into your suggestions.

---

