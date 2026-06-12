---
title: "Command to replace tab characters in a file?"
date: 2009-04-03
forum: General Help
---

### Post by jocko on 2009-04-03
I'm trying to make patches to make the old nvidia soundstorm drivers work on current kernels ([see my howto here]("http://ubuntuforums.org/showthread.php?p=1478381")).
One of the problems right now is that one of the files that needs to be patched contains leading tab characters in stead of spaces on some lines, which makes the patch command fail.

Does anyone know any way to do of any of these:
1. A way to get the patch command to work with lines containing tab characters?
2. A way to replace tab characters with spaces on specific lines of a file?
3. A way to replace ALL tab characters (or all leading tab characters) in a file with spaces?
4. Any other way to replace the text I need to change (some sed command I can include in a script)?

Specifically, I need a command to change this (but with tabs instead of "<tab>"):
```
<tab><tab><tab><tab><tab><tab><tab><tab><tab>[COLOR=Red]:"=m"(currenttask->thread.i387.fxsave) );[/COLOR]
```Into this (tabs or spaces doesn't really matter, as long as the actual code in red gets changed):
```
                                [COLOR=Red]:"=m"(currenttask->thread.xstate->fxsave) );[/COLOR]
```

---

### Post by kuja on 2009-04-03
Okay, well, to do that replace, I would so something like this:

put this in a command for sed to use (too tedious to let bash see all the extraneous characters that you might otherwise have to escape), lets call this file '[color=blue]scriptforsed[/color]'.

```
s/:"=m"(currenttask->thread.i387.fxsave) );/ :"=m"(currenttask->thread.xstate->fxsave) );/
```

Now, lets say you want to do the replacement in a file called '[color=blue]somefile[/code]' We'll need to use a command like this one to do it:
```
 sed -f [color=blue]scriptforsed[/color] -i [color=blue]somefile[/color]
```

For the replacing of the tabs, I would use tr ... an example of its use might be ...
```
cat [color=blue]somefile[/color] | tr '\t' ' ' > [color=blue]somefile[/color]
```

Don't know about making things more specific, but this should work for at least a couple of your needs.

---

### Post by jocko on 2009-04-03
> **kuja said:**
> Okay, well, to do that replace, I would so something like this:

put this in a command for sed to use (too tedious to let bash see all the extraneous characters that you might otherwise have to escape), lets call this file '[COLOR=blue]scriptforsed[/COLOR]'.

```
s/:"=m"(currenttask->thread.i387.fxsave) );/ :"=m"(currenttask->thread.xstate->fxsave) );/
```Now, lets say you want to do the replacement in a file called '[color=blue]somefile[/code]' We'll need to use a command like this one to do it:
```
 sed -f [COLOR=blue]scriptforsed[/COLOR] -i [COLOR=blue]somefile[/COLOR]
```For the replacing of the tabs, I would use tr ... an example of its use might be ...
```
cat [COLOR=blue]somefile[/COLOR] | tr '\t' ' ' > [COLOR=blue]somefile[/COLOR]
```Don't know about making things more specific, but this should work for at least a couple of your needs.
Thanks, that looks promising. I will try it when I get back from work.

---

### Post by lloyd_b on 2009-04-03
> **jocko said:**
> I'm trying to make patches to make the old nvidia soundstorm drivers work on current kernels ([see my howto here]("http://ubuntuforums.org/showthread.php?p=1478381")).
One of the problems right now is that one of the files that needs to be patched contains leading tab characters in stead of spaces on some lines, which makes the patch command fail.

Does anyone know any way to do of any of these:
1. A way to get the patch command to work with lines containing tab characters?
2. A way to replace tab characters with spaces on specific lines of a file?
3. A way to replace ALL tab characters (or all leading tab characters) in a file with spaces?
4. Any other way to replace the text I need to change (some sed command I can include in a script)?

Specifically, I need a command to change this (but with tabs instead of "<tab>"):
```
<tab><tab><tab><tab><tab><tab><tab><tab><tab>[COLOR=Red]:"=m"(currenttask->thread.i387.fxsave) );[/COLOR]
```Into this (tabs or spaces doesn't really matter, as long as the actual code in red gets changed):
```
                                [COLOR=Red]:"=m"(currenttask->thread.xstate->fxsave) );[/COLOR]
```

Have you tried running "patch" with the "-l" option?  This tells patch to use a very loose matching algorithm as far as whitespace characters (tabs, spaces) are concerned.

Lloyd B.

---

### Post by jocko on 2009-04-03
> **lloyd_b said:**
> Have you tried running "patch" with the "-l" option?  This tells patch to use a very loose matching algorithm as far as whitespace characters (tabs, spaces) are concerned.

Lloyd B.
That seems to have done it! So simple. Looks like I didn't read the patch manpage properly.

Thank you!

---

