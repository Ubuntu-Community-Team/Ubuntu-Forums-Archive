---
title: "What does the command &quot;sudo apt-get update --fix-missing&quot; do?"
date: 2009-04-25
forum: General Help
---

### Post by lindsay7 on 2009-04-25
I was doing some updating in the terminal and I got back a comment to try running "sudo apt-get update --fix- missing". I ran it and everything is OK. I can not find anything on this command and would like to know what it actually does. Is this something that I should run periodically just to make sure I have everything or was this a one time thing.

Thanks,

---

### Post by kpkeerthi on 2009-04-25
> 
--fix-missing
    Ignore missing packages; If packages cannot be retrieved or fail the integrity check after retrieval (corrupted package files), hold back those packages and handle the result. Use of this option together with -f may produce an error in some situations. If a package is selected for installation (particularly if it is mentioned on the command line) and it could not be downloaded then it will be silently held back. Configuration Item: APT::Get::Fix-Missing.  ... from the man page

---

### Post by drs305 on 2009-04-25
You can read what it does on the "man" page for apt-get. Since "--fix-missing" is an option, you would look for the options section of the man page and find it there.

To read a man page, open a terminal and type:
```

man apt-get  # look at the " -m " option

```

The man pages are also available online from many sources. Here's one:
[http://man.he.net/]("http://man.he.net/")

---

