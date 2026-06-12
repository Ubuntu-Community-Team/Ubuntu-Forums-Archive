---
title: "Terminal commands: the cd command, howto"
date: 2009-05-03
forum: General Help
---

### Post by RedRat on 2009-05-03
I saw this here someplace. How do you make the command to change to a directory with a compound name, ie. say I have a directory named "foo bar" note the space between the two names.

If I use the command cd foo bar, it comes back with no such directory. I saw once here how to do it but can;t find it.

MY bad. both the "foo bar" and 'foo bar' worked. My fault in not looking at the subdirectories. Thanks for all your help.

---

### Post by meierfra. on 2009-05-03
```
cd "foo bar"
```

---

### Post by akakingess on 2009-05-03
> **RedRat said:**
> I saw this here someplace. How do you make the command to change to a directory with a compound name, ie. say I have a directory named "foo bar" note the space between the two names.

If I use the command cd foo bar, it comes back with no such directory. I saw once here how to do it but can;t find it.
I think that you have to put a /in front of the space, or it could be a \. Or behind the space for that matter, sorry I can't remember exactly off of the top of my head.

Earl

---

### Post by DeMus on 2009-05-03
> **RedRat said:**
> I saw this here someplace. How do you make the command to change to a directory with a compound name, ie. say I have a directory named "foo bar" note the space between the two names.

If I use the command cd foo bar, it comes back with no such directory. I saw once here how to do it but can;t find it.

Try
```
cd "foo bar"
```

This applies to all instructions where you also have to type the name of the folder.

---

### Post by RedRat on 2009-05-03
> **DeMus said:**
> Try
```
cd "foo bar"
```

This applies to all instructions where you also have to type the name of the folder.

No this does not do it. When I use that command it comes back with "no such file or directory"

---

### Post by bigboy_pdb on 2009-05-03
The command that you were given is correct. You can use that or:
cd 'foo bar'

If neither is working then there might be other characters in the file name, such as leading or trailing spaces or non-printable characters. You can use the following command to check this:
od -c < <(ls *foo*bar*)

EDIT: Sorry, I should also mention that it won't work if the non-printable characters are between the characters in foo or bar. However, if that's the case, you won't see a listing for the file name.

---

### Post by CatKiller on 2009-05-03
Or you can escape the space (or any other control character) with \, like *cd foo\ bar*. Or (by far the easiest) *cd foo*<Tab> to let the shell auto-complete the filename for you.

---

