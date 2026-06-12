---
title: "How to execute two commands in a gnome-terminal without a script?"
date: 2007-08-27
forum: Desktop Environments
---

### Post by Pinnocchio on 2007-08-27
Hi

I'm trying to execute two seperate commands in a gnome-terminal using the --command="xxxx" option and can't see how to get it working.....anyone got any ideas please.

For example:-

gnome-terminal --command="do some command" --command="do some other command"

I've worked out that I can't have two --command entries in the line.....but was hoping I could use the | seperator to run more then one command, however this doesn't seem to want to work either.

I don't want to write a script for this as it's already getting called from a script and it's getting too complicated with too many nested scripts. As simple solution keeps my life easier to manage!!

TIA

---

### Post by vambo on 2007-08-27
```
command1 **;** command2
```

---

### Post by raijinsetsu on 2007-08-27
If you want two windows:
```
gnome-terminal --command="command 1" & gnome-terminal --command="command 2"
```

If you want to run both commands in the same window:
```
gnome-terminal --command="command 1;command 2"
```

---

### Post by Pinnocchio on 2007-08-27
Thanks but that doesn't work.....any more ideas anyone.

---

### Post by raijinsetsu on 2007-08-27
Which one doesn't work?

---

### Post by Pinnocchio on 2007-08-27
gnome-terminal --command="echo hello > /~/hello;echo hello again >>/~/hello"

doesn't work (and I've tried assorted variations of different quote mark positions to test the structure).

If someone can give me a working example of command1;command2 I'd love to see it.

---

### Post by raijinsetsu on 2007-08-27
try
```
gnome-terminal --command="echo Hello!! > ~/hello ;echo Hello AGAIN!!! >> ~/hello"
```
I don't know why you had extra forward slashes in your command... Hopefully this fixes your problem...

---

### Post by Lord Illidan on 2007-08-27
Why do you need gnome-terminal to do it anyway? Try this in any bash term, and it will work.

```
echo hello >> hello && echo hello again >> hello
```

---

### Post by Lord Illidan on 2007-08-27
> **raijinsetsu said:**
> try
```
gnome-terminal --command="echo Hello!! > ~/hello ;echo Hello AGAIN!!! >> ~/hello"
```I don't know why you had extra forward slashes in your command... Hopefully this fixes your problem...

That doesn't work...It should create a file called hello, but it doesn't..

---

### Post by FriedChips on 2007-08-27
I would say just bite the bullet and make another script....:wink:

---

### Post by vambo on 2007-08-27
> **Pinnocchio said:**
> gnome-terminal --command="echo hello > /~/hello;echo hello again >>/~/hello"

doesn't work (and I've tried assorted variations of different quote mark positions to test the structure).

If someone can give me a working example of command1;command2 I'd love to see it.

Try this

```
xterm -e "echo hello > hello ; echo hello hello >> hello"
```

---

### Post by Pinnocchio on 2007-08-27
I can't do this easily using a script....

The first command opens a ssh session to a remote machine   the second command then should get executed as a command on the remote machine.  I don't want to drop executable scripts onto the remote boxes (much more difficult to manage), I want a simple solution that allows me to.....

gnome-terminal --command="ssh xxxx@xxxxxx (some seperator) second command"

---

### Post by Pinnocchio on 2007-08-27
> **vambo said:**
> Try this

```
xterm -e "echo hello > hello ; echo hello hello >> hello"
```

That works......if anyone can thing of a way of doing it in gnome-terminal I'd be appreciative, I'm just more used to the features in gnome-terminal (God I'm an awful ungrateful git aren't I ;)

---

### Post by heyhey on 2007-08-27
Give a better example of what you really want to do.   To merely execute a command through ssh, you don't even need to open a gnome terminal. For example, you can do

ssh hostname "uname -a"

> **Pinnocchio said:**
> I can't do this easily using a script....

The first command opens a ssh session to a remote machine   the second command then should get executed as a command on the remote machine.  I don't want to drop executable scripts onto the remote boxes (much more difficult to manage), I want a simple solution that allows me to.....

gnome-terminal --command="ssh xxxx@xxxxxx (some seperator) second command"

---

### Post by Lord Illidan on 2007-08-27
>  		I can't do this easily using a script....

The first command opens a ssh session to a remote machine the second command then should get executed as a command on the remote machine. I don't want to drop executable scripts onto the remote boxes (much more difficult to manage), I want a simple solution that allows me to.....

gnome-terminal --command="ssh xxxx@xxxxxx (some seperator) second command"

Quite simple.

 gnome-terminal -e "ssh xxxx@xxxxxx -t name of program" should work.

---

### Post by Pinnocchio on 2007-08-27
> **Lord Illidan said:**
> Quite simple.

 gnome-terminal -e "ssh xxxx@xxxxxx -t name of program" should work.

That's perfect thanks.......

---

