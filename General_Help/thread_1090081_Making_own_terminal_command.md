---
title: "Making own terminal command?"
date: 2009-03-07
forum: General Help
---

### Post by linuxisevolution on 2009-03-07
I always type commands like "sudo" wrong in terminal because of the way I sit at my keyboard. (i.e soud). How would i create my own command that would like to sudo, and where would I put the script?

---

### Post by Dr Small on 2009-03-07
In your .bash_aliases file, after uncommenting the 3 lines in the .bashrc file to support .bash_aliases.
Then, do something like this:
```
alias soud="sudo"
```

But I recommend you improve your typing skills, instead of making shortcuts for your laziness :D

---

### Post by DGortze380 on 2009-03-07
[http://linux.about.com/od/bgb_guide/a/gdebgb32t01.htm](http://linux.about.com/od/bgb_guide/a/gdebgb32t01.htm)

I don't suggest you alias sudo though... I'm not sure you even can...

---

### Post by linuxisevolution on 2009-03-07
> **Dr Small said:**
> In your .bash_aliases file, after uncommenting the 3 lines in the .bashrc file to support .bash_aliases.
Then, do something like this:
```
alias soud="sudo"
```

But I recommend you improve your typing skills, instead of making shortcuts for your laziness :D

I am not lazy, I just hate having to hit backspace again and again sometimes. I am a very fast and accurate typer, but when I sit in this chair at this angle it's difficult. :D

---

### Post by Dr Small on 2009-03-07
> **DGortze380 said:**
> [http://linux.about.com/od/bgb_guide/a/gdebgb32t01.htm](http://linux.about.com/od/bgb_guide/a/gdebgb32t01.htm)

I don't suggest you alias sudo though... I'm not sure you even can...
```
[drsmall@darkghost ~]$ alias s="sudo"
[drsmall@darkghost ~]$ s su
[root@darkghost drsmall]# 
```

It worked for me.

---

### Post by linuxisevolution on 2009-03-07
> **Dr Small said:**
> ```
[drsmall@darkghost ~]$ alias s="sudo"
[drsmall@darkghost ~]$ s su
[root@darkghost drsmall]# 
```

It worked for me.

That worked, but how do I make it stay after I close the terminal?

---

### Post by Dr Small on 2009-03-07
> **linuxisevolution said:**
> That worked, but how do I make it stay after I close the terminal?
Uncomment the lines referring to ~/.bash_aliases in your .bashrc file, and add your alias commands to the ~/.bash_aliases file.

---

### Post by linuxisevolution on 2009-03-07
I do not have a .bash_aliases file in my home directory.:(

---

### Post by Dr Small on 2009-03-07
> **linuxisevolution said:**
> I do not have a .bash_aliases file in my home directory.:(
```
touch ~/.bash_aliases
```
Now, you do. :)

---

### Post by linuxisevolution on 2009-03-07
> **Dr Small said:**
> ```
touch ~/.bash_aliases
```
Now, you do. :)

Now I get this:

touch ~.me

touch: permission denied

Just kidding :D

What do I put in that file?

---

### Post by Dr Small on 2009-03-07
> **linuxisevolution said:**
> Now I get this:

touch ~.me

touch: permission denied

Just kidding :D

What do I put in that file?
```
alias soud="sudo"
```

And of course, any other aliases that you would happen to make to save keystrokes.

---

### Post by linuxisevolution on 2009-03-07
Thank you so much!!

So I can also do:

alias die="sudo halt"


:lolflag:

---

