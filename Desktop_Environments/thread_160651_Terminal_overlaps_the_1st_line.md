---
title: "Terminal overlaps the 1st line"
date: 2006-04-15
forum: Desktop Environments
---

### Post by dohko on 2006-04-15
Hello fellows!

I've recently installed Kubuntu on a desktop and noticed a different behavior on my terminals (konsole and xterm).

Basically, the terminal "overlaps" the first line I write. For example, if I wanted to type this hipotetical long command (assume for the examples below that the column with the "p" is the last column of the terminal),

```
                                                                           
bash# 123456789abcdefghijklmnop
qrstuvwxyz
```

the terminal would wrap the line and star outputting the second overlapping the first line, like:

```
                                                                                      
qrstuvwxyz456789abcdefghijklmnop

```

This overlapping happens only between the 1st and 2nd lines, though.

I searched the man page for bash and found something about *shopt -s checkwinsize* that could be the solution to this problem. However, my .bashrc already uses that.

Does anyone know how to correct this behavior?

Thanks!

---

### Post by z-vet on 2006-04-15
$PS1 is broken. Check your ~/.bashrc file for the line defining your $PS1, i think there's some syntax error in it.

---

### Post by dohko on 2006-04-15
This is my $PS1:

```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \[\033[01;34m\]\w \$\033[00m '
```

I have changed it a little bit to get a colorful prompt.

---

### Post by z-vet on 2006-04-15
I fixed it:
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[01;34m\] \[\033[01;34m\]\w\[\033[00m\]\$ '
```
If you want to know more, read [this HOWTO](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html), it's very good.

---

### Post by dohko on 2006-04-15
Hummm, I see that I had messed up the last portion of the code to make the prompt color return to normal...

I'm using this now:
```

PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h \[\033[01;34m\]\w \$ \[\033[00m\]'
```

This way the "$" char is also displayed in blue and there is no redundant "\[\033[01;34m\]" anymore.

Thanks very much for your help z-vet, and thanks for the tutorial link also!

---

