---
title: "Update Manager"
date: 2009-06-16
forum: General Help
---

### Post by sailho on 2009-06-16
I have 8.10 on my desktop(Duel OS Windows and Ubuntu) Due to some error I inserted through terminal,now when I try to run update manager I get the following error message....
E."malformed line 36 in source list/etc/apt/sources.list(dist parce)"
E."the source list could not be read" How do I correct this?

 Also how do I upgrade 8.10 to 9.04/

---

### Post by Therion on 2009-06-16
Sounds like you've borked your sources.list file (line 36 is being indicated).  Were you trying to add a repository via the Terminal or something?  

Open the sources.list file and then copy and paste the contents of the file in a new post.

```
sudo gedit /etc/apt/sources.list
```

Most likely you just need to clean up a few keystrokes or a badly formed line in this file and re-save it.

---

### Post by sailho on 2009-06-17
Thanks for the help,I think I have the problem corrected!

---

