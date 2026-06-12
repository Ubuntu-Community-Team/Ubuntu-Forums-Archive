---
title: "Redirect command line output"
date: 2009-04-03
forum: General Help
---

### Post by agentn2o on 2009-04-03
Hi there... I'm a relatively newb linux user... I would like to know how to redirect the command line output into a pager file format like the man pages. When I log into a tty (w/ CTRL-ALT-F1) and do a ls command on some of my directories the output scrolls by and I cannot view it all in this window and I do not have the ability to scroll back. Can I output this info using some format using the ">>". Thing is I don't know what should come next:
e.g. ls -a >> "??"

Thanks.

Agent N2O

---

### Post by lisati on 2009-04-03
A quick solution which might go a little way to helping is to do something like this:
```
*command* | less 
```
(The "less" command is a close cousin of the "more" command)
An alternative  which will create a text file that you can browse later is something like this:
```
*command* > *filename*.txt
```

And yes, ">>" will work here too, but appending the command line output to a file instead of replacing the whole file.

Hope these ideas help.

---

### Post by ShaunG on 2009-04-03
You can pipe the output to more if you would or to a text file.

So for example you can type 

```
ls | more
```

or

```
ls > list.txt
```

Then you could view list.txt by using cat list.txt

The following link may help learn a little more about how to do input/output redirection

[http://www.codecoffee.com/tipsforlinux/articles2/042.html]("http://www.codecoffee.com/tipsforlinux/articles2/042.html")

---

### Post by ibuclaw on 2009-04-03
To redirect output to a pager, you **pipe** all the output to the pager's stdin.

ie:
```
ls -A | less
```
But that will make all output in just one colour, so it may be hard to distinguish file from directory.

alternately, you could:
```
ls -F | less
```
so that directories are distinguishable by the trailing **/** symbol, or you could have it in colour.

```
ls --color=always | less -R
```

But that may be a bit too much type. In which case, you can make an alias.
```
nano ~/.bashrc
```
and put at the bottom something along the lines of:
```
alias lsless='ls --color=always | less -R'
```
Save and quit, then source the file:
```
. ~/.bashrc
```
and type in
```
lsless
```
To see the output of it.

Regards
Iain

---

### Post by agentn2o on 2009-04-03
Ah yes... thanks.

"ls -l | less" and "ls -l | more" both work great!

And thanks for clearing up the > and >> output to file tricks.

I have been impressed by the enormous power of the linux command line but it is a bit of a steep learning curve. Sometimes it is difficult to search out the answers as one needs to know how to format the question properly.

Thanks for the patience...

---

