---
title: "Bash Script Help!!"
date: 2008-12-07
forum: General Help
---

### Post by joec369 on 2008-12-07
Hello, I need help writing this Bash Script.  I know the basics, how to create an excutable script.  I use VI.  But this is way beyond me.  Any help would be apreciated.  I am using ubuntu 8.10. Thanks again.

Write a script that:
(a) asks for input from the user for a specific IP address
(b) asks for the number of times to check (ping) the host to
determine whether it is up
(c) determines whether the host is up with a ping, and reports
back to the user
(d) if the host is up, queries the user whether they would like
to make a telnet connection
(e) if the user answers affirmative, attempts the telnet
connection

---

### Post by schauerlich on 2008-12-07
Wouldn't it be easier to just ping the remote machine and then telnet to it?

---

### Post by joec369 on 2008-12-07
It's for a school project.  So I basically have to do it.

---

### Post by joec369 on 2008-12-07
Anyone out there that can help?  Anything, copy script in, point me to another thread, or website.  Thanks

Joe

---

### Post by mike2357 on 2008-12-07
Maybe entering "bourne shell" in your favorite search engine will do the trick.  You can play around with the commands, like ping, and check the exit status, which you can display with ```
echo $*
```

Doing someone's homework assignment for them is generally frowned upon; that's not the purpose of help forums.

Good luck.  There's a wealth of information about the bourne and bash shells on the net.

---

### Post by bapoumba on 2008-12-07
> **joec369 said:**
> It's for a school project.  So I basically have to do it.

We do not support homework here, sorry. Closing the thread.

---

