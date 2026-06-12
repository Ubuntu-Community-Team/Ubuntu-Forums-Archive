---
title: "Edit multiple htlm files (find and replace)"
date: 2009-02-26
forum: General Help
---

### Post by aktiwers on 2009-02-26
I have lots of HTLM files that all contains this line of html:
```
width: 71px; height: 41px;
```I want it to be changed to:
```
width: 85px; height: 55px;
```But offcause not manually..  

I found this thread
[http://ubuntuforums.org/showthread.php?t=630071](http://ubuntuforums.org/showthread.php?t=630071)

Explaining how to do this, but my string seams to interfere with the command.

This is what I tried to use:
```
find -iname "*.html" -exec sh -cC ' sed 's/**search**/**replace**/' "$1" > "$1".new ' {} {} \;
```where **search** would be the string to be replaced by **replace**.

How can I use this command with my string?

---

### Post by lloyd_b on 2009-02-26
That command has a problem with nesting of the single quotes, but other than that it's just a matter of changing "search" and "replace" with your strings.

```
find -iname "*.html" -exec sh -cC ' sed "s/width: 71px; height: 41px;/width: 85px; height: 55px;/" "$1" > "$1".new ' {} {} \;
```should do the trick.

Lloyd B.

---

### Post by CrucifiedEgo on 2009-02-26
Do you really need to use find?  This should work fine (renaming the original files to .old):
```
sed -i.old "s/width: 71px; height: 41px;/width: 85px; height: 55px;/"
```

---

### Post by aktiwers on 2009-02-26
I love you guys! :)  - Thanks!

Now I want to rename the files:
```
find -iname ".html.new" | sed 's/.new//' | sh
```What am I doing wrong?

EDIT:
Nevermind I did it with pyRenamer GUI app :(
Very nice app though

---

