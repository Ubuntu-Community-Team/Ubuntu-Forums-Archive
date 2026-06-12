---
title: "How do i pause the ls command"
date: 2009-04-21
forum: General Help
---

### Post by sefs on 2009-04-21
Hi all,

I want to be able to pause the ls command so that i can examine a directory listing before it scrolls of the screen.

I already know about ls | more and ls| less but those will not do.

You see .. if I for example do this

ls -R * it presents each directory and the files under that directory ... and futhermore the files are color coded...for example executable files appear in lime green.

when I do ls -R * | more  then I lose the color coding that I need.

Is there anyway to pause the ls and keep the color coding?

Thanks.

---

### Post by meierfra. on 2009-04-21
```
ls -R --color=always * | more
```

---

### Post by Slim Odds on 2009-04-21
less is even better...

---

### Post by meierfra. on 2009-04-21
> less is even better...
But  the colors don't  work with "less" (even if one adds "--color=always")

---

### Post by sefs on 2009-04-22
Thank you very much.  That hit the spot.

---

### Post by 3Miro on 2009-04-22
```

ls -whatever_options > some_filename

```

This will create a text file called some_filename and the output of ls would be stored in it. You can open it with gedit or some other program.

---

### Post by Slim Odds on 2009-04-22
> **meierfra. said:**
> But  the colors don't  work with "less" (even if one adds "--color=always")

Works fine for me (with more or less).

---

### Post by sisco311 on 2009-04-22
> **meierfra. said:**
> But  the colors don't  work with "less" (even if one adds "--color=always")

```
ls -al --color="always"| less -R
```
;)

export LESS="-R"
ls -al --color="always"| less

---

### Post by Greslore on 2009-04-22
Because less is more.

(Sorry couldn't resist!)

---

### Post by meierfra. on 2009-04-22
> ```
ls -al --color="always"| less -R
```


Thanks, that for works me. 

```
ls  color=always * | less -R
```

works, too. But 

```
ls  -R  color=always * | less
```

does not.

---

### Post by sisco311 on 2009-04-22
> **meierfra. said:**
> Thanks, that for works me. 

```
ls  color=always * | less -R
```

works, too. But 

```
ls  -R  color=always * | less
```

does not.

You have to set the -R flag.

Options are also taken from the environment variable "LESS".  For example, to avoid typing "less -R ..." each time less is invoked, you might tell bash:
export LESS="-R"

To make it permanent append the ~/.bashrc file with the export command. 

On my Arch installation the environment variable is set to -R by default.

Did you change your shell from bash to something else?

---

### Post by meierfra. on 2009-04-22
> Did you change your shell from bash to something else? 
No. "env |grep SHELL" gives  me   "SHELL=/bin/bash". 

> On my Arch installation the environment variable is set to -R by default.


"env |grep LESS" returns

LESSOPEN=| /usr/bin/lesspipe %s
LESSCLOSE=/usr/bin/lesspipe %s %s


So it seems Arch sets  "LESS" to "-R" and Ubuntu does not.

---

