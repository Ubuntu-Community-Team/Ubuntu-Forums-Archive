---
title: "changing ownership"
date: 2005-05-26
forum: Desktop Environments
---

### Post by bobgreen5s on 2005-05-26
How do you change all the subdirectories in a folders user ownership and group ownership? I know you use 'chown' but I don't know the command. NOT PERMISSIONS.


Any help would be appreciated.

---

### Post by angkor on 2005-05-26
That would be 'chmod'

chmod user.user /foo.bar

---

### Post by Takis on 2005-05-26
Man page hard to read? You get that with some of the more inbuilt commands because the author wants to be absolutely correct with what they're saying (a good cause, but not fun when you want to learn how to use something new).

Is it okay if the files' owners/groups are changed as well? I think it may be a little tricky otherwise. To change all files/folders recursively in subdirectory bob, you go:
```
$ chown -R newowner:newgroup bob/
```
If you just want to change owner, it's:
```
$ chown -R newowner bob/
```
If you just want to change group, it's:
```
$ chown -R :newgroup bob/
```
There's a heap more info in the man pages, if you feel a bit adventurous (man chown isn't very hard to read, actually) you would do well to skim-read it.

---

### Post by Takis on 2005-05-26
[QUOTE=angkor]That would be 'chmod'

chmod user.user /foo.bar[/QUOTE]

Does that work? I've never seen that before.

```
$ touch newfile
$ chmod otheruser.othergroup newfile
chmod: invalid mode string: `otheruser.othergroup'
$
```

---

### Post by angkor on 2005-05-26
](*,)  ](*,) 

The above post was deleted due to stupidity caused by fatigue

 ](*,)  ](*,)

---

### Post by bobgreen5s on 2005-05-26
[QUOTE=Takis]Man page hard to read? You get that with some of the more inbuilt commands because the author wants to be absolutely correct with what they're saying (a good cause, but not fun when you want to learn how to use something new).

Is it okay if the files' owners/groups are changed as well? I think it may be a little tricky otherwise. To change all files/folders recursively in subdirectory bob, you go:
```
$ chown -R newowner:newgroup bob/
```
If you just want to change owner, it's:
```
$ chown -R newowner bob/
```
If you just want to change group, it's:
```
$ chown -R :newgroup bob/
```
There's a heap more info in the man pages, if you feel a bit adventurous (man chown isn't very hard to read, actually) you would do well to skim-read it.[/QUOTE]

Thanks I really appreciated it.

---

