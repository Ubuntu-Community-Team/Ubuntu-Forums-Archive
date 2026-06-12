---
title: "Print working directory; ~ for $HOME?"
date: 2009-02-04
forum: General Help
---

### Post by computer_freak_8 on 2009-02-04
Okay, there's a really long story behind this, but I think I can get an answer without having to get too far into it. 

First, I've looked around, and I can't seem to find what I need; Google and "man bash" didn't seem to help me.

What command could I use to print the full working directory (that is, multiple levels, if existent) that will substitute "~" for the contents of "$HOME"? 

If necessary, I can specify something in my "~/.bashrc" file that (I think) would be something like this (pseudo-code)
```
if "$TEXT" contains "$HOME"
{
"$HOME" = ~ (in $TEXT)
}
```


This isn't quite how it would work, but I don't know how it would work, hence why I am posting.

Any ideas?

---

### Post by icheyne on 2009-02-05
I'm not sure what you're asking, but wouldn't ```
ls -R ~
``` work?

---

### Post by computer_freak_8 on 2009-02-05
> **icheyne said:**
> I'm not sure what you're asking, but wouldn't ```
ls -R ~
``` work?
Thanks for the response. Unfortunately, that's not what I was trying to inquire about. 

What I need is to be able to set a variable (let's say "$DIFFPWD") that will have the same contents as the variable "$PWD", except that it would have "~" instead of "/home/username". 

The comparison would be something like this:
```
username@hostname:~/Scripts/Linux$ echo $PWD
/home/username/Scripts/Linux
username@hostname:~/Scripts/Linux$ echo $DIFFPWD
~/Scripts/Linux
```

---

### Post by dcstar on 2009-02-05
> **computer_freak_8 said:**
> Thanks for the response. Unfortunately, that's not what I was trying to inquire about. 

What I need is to be able to set a variable (let's say "$DIFFPWD") that will have the same contents as the variable "$PWD", except that it would have "~" instead of "/home/username". 

The comparison would be something like this:
```
username@hostname:~/Scripts/Linux$ echo $PWD
/home/username/Scripts/Linux
username@hostname:~/Scripts/Linux$ echo $DIFFPWD
~/Scripts/Linux
```

So you just want the output of the "pwd" command with a literal "~" in front of it?

---

### Post by computer_freak_8 on 2009-02-05
> **dcstar said:**
> So you just want the output of the "pwd" command with a literal "~" in front of it?
I'm not sure what you mean by "literal", but that sounds correct. The output of "pwd" with "~" replacing "/home/username".

---

### Post by computer_freak_8 on 2009-02-07
Hello? Bump.

---

### Post by dcstar on 2009-02-07
> **computer_freak_8 said:**
> I'm not sure what you mean by "literal", but that sounds correct. The output of "pwd" with "~" replacing "/home/username".

The "/home/username" data is in the variable $HOME, you should be able to do a simple string replace of this for the "~":

[http://tldp.org/LDP/abs/html/string-manipulation.html](http://tldp.org/LDP/abs/html/string-manipulation.html)

or:

```
test =${PWD/$HOME/"~"}
echo $test
```

---

### Post by computer_freak_8 on 2009-02-07
> **dcstar said:**
> The "/home/username" data is in the variable $HOME, you should be able to do a simple string replace of this for the "~":

[http://tldp.org/LDP/abs/html/string-manipulation.html](http://tldp.org/LDP/abs/html/string-manipulation.html)

**_Awesome!!!_** *Thank you!*

```
MPWD=${PWD#$HOME}
MPWD="~$MPWD"
```

---

### Post by computer_freak_8 on 2010-01-20
> **computer_freak_8 said:**
> **_Awesome!!!_** *Thank you!*

```
MPWD=${PWD#$HOME}
MPWD="~$MPWD"
```
Hmmm... this doesn't seem to work now. But, the following code (which is now in my ***~/.bashrc*** file) does:
```
mpwdtmp()
{
MPWDTMP=${MPWDTMP/$HOME\//\~\/};
MPWD=${PWD/$HOME/\~};
echo $MPWD
}

alias mpwd=mpwdtmp
```

(Note: Now that the "Mark thread as Solved" feature is back, I'm going through my solved threads an marking them, as well as updating the information, if needed... hence this post.)

---

