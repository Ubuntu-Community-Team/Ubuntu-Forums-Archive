---
title: "&quot;su&quot; command memory limit?"
date: 2009-05-25
forum: General Help
---

### Post by WhiteShepherd on 2009-05-25
I was wanting to generate some .jpg thumbnails.  I want to run imagemagick's "convert" as a different users.  To do this I run the "su" command.

This command below works fine.
/bin/su - whiteshepherd -c /usr/bin/convert

However this command below fails even though it works when not preceeded by the "su".

/bin/su - username -c /usr/bin/convert -sample 150 "/homedir/test.jpg" "/homedir/test2.jpg"


I suspect that the "su" command may have a memory limit and the convert my require to much memory when working with images. 

So the question becomes if "su" is to allow you to run programs as different users what do you do it can't run a memory intensive application?  Is there another way (short of running chown on everything)? I'm running Ubuntu Jaunty 9.04.

---

### Post by sisco311 on 2009-05-25
you have to quote the command:
```
su - username -c "/usr/bin/convert -sample 150 "/homedir/test.jpg" "/homedir/test2.jpg""
```

or simply log in, run the command and log out:
```

su username -
/usr/bin/convert -sample 150 "/homedir/test.jpg" "/homedir/test2.jpg"
exit #or Press Ctrl+d

```

---

### Post by Soul-Sing on 2009-05-25
su - and ubuntu?

---

### Post by sisco311 on 2009-05-25
> **leoquant said:**
> su - and ubuntu?

```
su USERNAME
```
Allows one user to temporarily become another.

If USERNAME has a password, *su* prompts for the password.

If no USERNAME is given, *root* is the default.

By default, in Ubuntu the *root* account password is locked, so you can't use su to become *root*.

---

