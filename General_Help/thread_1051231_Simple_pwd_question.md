---
title: "Simple pwd question"
date: 2009-01-26
forum: General Help
---

### Post by Joe Momma on 2009-01-26
I'm confused on the difference between typing pwd and /bin/pwd (I do not have anything aliased to pwd)

```
which pwd
/bin/pwd
```

I have a second partition mounted on /disk1 and I have my /opt directory linked from /disk1/opt

```

opt -> /drive1/opt/
```

now if I am in the /opt directory I get a different result using pwd and /bin/pwd

```
pwd
/opt

```

but

```
/bin/pwd
/drive1/opt
```

---

### Post by ajcham on 2009-01-26
**pwd** is a built-in command in bash, and takes precedence over the binary located at **/bin/pwd**.

The **pwd** command will print the name of the link, as though it were an actual directory in its own right, whereas **/bin/pwd** follows the link and prints the path to the target directory.

---

### Post by Joe Momma on 2009-01-27
Thank you,

This was bugging me because I had my prompt set up to look like this:

$USER@`hostname`:`/bin/pwd`>

and it took me forever to figure out that it needed to be like this:

$USER@`hostname`:`pwd`>

Even then I had no idea why it worked.  I much prefer it says /home/username than /disk1/home/username

---

### Post by geirha on 2009-01-27
It's more common to set the prompt to
```
export PS1='\u@\h:\w> '
```

To see all the escapes you can use, run ```
man bash
``` and search for ^PROMPTING by hitting 
```
/^PROMPTING
``` followed by enter in less, the default pager.

Also, you might want to familiarize yourself with the type command. See what the following outputs. ```
type -a pwd
```

---

### Post by Joe Momma on 2009-01-28
thanks,

Yeah this was converted from an old .cshrc I used to use.

So with \w is there a way to not abbreviate my home directory with a '~'

---

### Post by geirha on 2009-01-28
If the man-page don't mention a way, then you probably can't. You can, however, use variables, so you can do: ```
export PS1='\u@\h:$PWD\$ '
```

---

