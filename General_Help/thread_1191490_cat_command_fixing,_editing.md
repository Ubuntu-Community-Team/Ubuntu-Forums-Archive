---
title: "cat command_fixing, editing"
date: 2009-06-19
forum: General Help
---

### Post by boarder428 on 2009-06-19
I was wondering if there was a way to change or edit text on a line after hitting enter when creating a file using the cat command?
```
corey@corey-desktop:~$ cat > products
S0107:Lobby Furniture:1201
S0109: Ballroom Specialties:1221

```
I would like to move the text "Ballroom Specialties" back one space but cannot seem to do so after pressing enter.

---

### Post by asmoore82 on 2009-06-19
I assume you mean *without* using a text editor after the fact :P ...
Not that I know of.

---

### Post by iponeverything on 2009-06-19
```
cat | sed 's/: /:/g' > products
S0107:Lobby Furniture:1201
S0109: Ballroom Specialties:1221

```

cat products
S0107:Lobby Furniture:1201
S0109:Ballroom Specialties:1221

---

### Post by boarder428 on 2009-06-30
> **iponeverything said:**
> ```
cat | sed 's/: /:/g' > products
S0107:Lobby Furniture:1201
S0109: Ballroom Specialties:1221

```

cat products
S0107:Lobby Furniture:1201
S0109:Ballroom Specialties:1221

Thanks for the script/reply!

---

### Post by t4thfavor on 2009-07-01
To break that down a bit for us non sed types.

sed 's/: /:/g' > products
s/:(space) means match the first occurance of :(space) replace it with :(nospace)
/g makes this global so that all occurances are matched. 
> then stuffs it into pruducts as we all know so well.

I'm learning sed and friends so that I can have ninja stream editing skills and get lots of work done faster...

EDIT:
Can't get the smilies to go away, so they are all occurrences of :

---

### Post by ghostdog74 on 2009-07-02
> **boarder428 said:**
> I was wondering if there was a way to change or edit text on a line after hitting enter when creating a file using the cat command?
you can use the ed editor.

---

