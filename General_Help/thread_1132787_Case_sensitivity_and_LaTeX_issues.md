---
title: "Case sensitivity and LaTeX issues"
date: 2009-04-22
forum: General Help
---

### Post by rathotron on 2009-04-22
Hi,

my WinXP installation totally crashed the other day, and decided it was time to make the switch. Ubuntu is much more than it was when I first tried it two years ago!

However, I've got a problem. At school, we write our reports as a group in LaTeX, using SVN to manage our files. I got TexLive and Kile working properly, but then encountered a problem I hadn't thought about.

Because Windows is case-insensitive, and Linux is case sensitive, the guys in my group using Windows can compile the report fine, with no problems. However, we've got quite a lot of inputs in our main file, inputs of picture files and so on, and a LOT of these are typed in with wrong cases (upper/lower) in the .tex files.

So my question is - is there any way I can do a case-insensitive compilation of our report using ```
pdflatex --"insert extremely cool command option here"
``` or something like that? Or do I have to manually edit all filenames in the SVN repo or the .tex files, in order to make it work? (the latter ain't gonna happen :()

Had to reinstall winxp, as we're a bit behind with the report - hope that motivates ;)

Cheers,
Mikkel

---

### Post by lvleph on 2009-04-22
Maybe making newcommands in the preamble like [here](http://www.latex-community.org/forum/viewtopic.php?f=5&t=4172&start=0)?

Not sure how it would work, but some how make \input case insensitive by redefining it.

EDIT: You could have run XP from a virtual machine, so as to avoid a reboot.

---

### Post by rathotron on 2009-04-23
Thanks for the reply. However, I'm not *that *good at LaTeX (yet), so was kinda looking for another option. :( 

Plus, I really want to avoid windows as much as possible. ;)

I'll look into the virtual machine-opt you mentioned though - that way I don't have to run windows all the time ;)

---

### Post by Nepherte on 2009-04-23
Using find and replace in your editor should already save you a lot of time. Ask your group to use the commands that work on linux in the future.

Personally I wouldn't use a virtual machine. Why would you use a virtual windows when latex works on linux as well?

edit: you could use the sed command as well to quickly replace words:
```
sed -i 's/oldcommand/newcommand/g' latexfile
```

---

### Post by rathotron on 2009-04-23
First of all, thanks for your reply.
> **Nepherte said:**
> Using find and replace in your editor should already save you a lot of time. Ask your group to use the commands that work on linux in the future.

The same document ( \input{...tex} ) and picture ( \includegraphics{...} ) are not included several times in the report, so can't see what you mean with this..?
I've already asked the group to use the proper commands/filenames.. ;)

> **Nepherte said:**
> Personally I wouldn't use a virtual machine. Why would you use a virtual windows when latex works on linux as well?
Well, because of the issue with case sensitivity, as mentioned in the first post... 

> **Nepherte said:**
>  edit: you could use the sed command as well to quickly replace words:
```
sed -i 's/oldcommand/newcommand/g' latexfile
```

Will definetely look into it, thanks!

---

### Post by rathotron on 2009-04-24
Should have taken the apparently hard way - it was only a matter of less than 10 file references that needed correction.. :(

Now I compile about ten times faster than XP+WinEdt+MikTex ;)

---

