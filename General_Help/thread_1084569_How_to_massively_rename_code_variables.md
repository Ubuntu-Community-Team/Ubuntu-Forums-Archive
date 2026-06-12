---
title: "How to massively rename code variables ?"
date: 2009-03-02
forum: General Help
---

### Post by tarekeldeeb on 2009-03-02
Hello all,

I have a project with a long tree of file structure.
I want to massively rename variables (aka: refactoring).

I usually go to the source root and run
```
find . -name '*.cpp' -exec sed -i s/MyOldVar/MyNewVar/ {} \;
```

It works perfect and fast.

But I usually need to perform many substitutions! So I manually re-run the command with different names, many times !

I want to have a file (name it a dictionary), and modify the command to run dictionary.length times, where each time the command gets its  names from the dictionary.

For example the dictionary file should look like:

varOld1 varNew1
varOld2 varNew2
(EOF)

hence, the command with loop twice and do 2 substitutions.

Can anyone help me with this? I really do not know shell scripting.

Thanks in advance,
Tarek

---

### Post by heindsight on 2009-03-02
This is probably not the most efficient way of doing this, but it should work.

Make a file, called dict containing:
```
varOld1 varNew1
varOld2 varNew2
```

Then do:
```
cat dict | while read from to; do
    find . -name "*.cpp" -exec sed -i "s/$from/$to/g" \{\} \;
done
```

---

### Post by tarekeldeeb on 2009-03-02
> **heindsight said:**
> This is probably not the most efficient way of doing this, but it should work.

Make a file, called dict containing:
```
varOld1 varNew1
varOld2 varNew2
```

Then do:
```
cat dict | while read from to; do
    find . -name "*.cpp" -exec sed -i "s/$from/$to/g" \{\} \;
done
```

It works!

Thanks a lot :)

---

### Post by geirha on 2009-03-02
You can also read the substitutions from a file.
```
$ cat sed-commands.txt
s/\<myvar\>/anothervar/g
s/\<foo\>/bar/g
$ find -name "*.cpp" -print0 | xargs -0 -- sed -i -f sed-commands.txt

```

---

