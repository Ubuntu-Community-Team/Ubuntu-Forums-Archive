---
title: "command line path"
date: 2009-06-05
forum: General Help
---

### Post by gishaust on 2009-06-05
My command line prompt is getting too long how do I make the path shorter an example 

This is the current command line

```

server@server:/var/www/schoolWork/takeToSchool/public_html/website/php/myAssignments/assessOne$ 

```

I would like it to look like something like this 

```

server@server:/assessOne$

```

Is that possible?

---

### Post by DGortze380 on 2009-06-05
> **gishaust said:**
> My command line prompt is getting too long how do I make the path shorter an example 

This is the current command line

```

server@server:/var/www/schoolWork/takeToSchool/public_html/website/php/myAssignments/assessOne$ 

```

I would like it to look like something like this 

```

server@server:/assessOne$

```

Is that possible?

I can give you a place to start, but thats about it.

You can change the information given at the prompt is your bash profile... I'm sure you can come up with something to shorten it.

~/.bashrc

---

### Post by Mike'sHardLinux on 2009-06-05
[[COLOR="Blue"]Here's[/COLOR]]("http://ubuntuforums.org/showthread.php?t=614743") a fantastic thread on customizing the BASH prompt.

---

### Post by gishaust on 2009-06-06
thanks

---

### Post by x33a on 2009-06-06
or you could create symlinks for your frequently used directories.

see 
```
man ln
```

---

### Post by andrew.46 on 2009-06-06
Hi gishaust,

> **gishaust said:**
> 

```

server@server:/var/www/schoolWork/takeToSchool/public_html/website/php/myAssignments/assessOne$ 

```

I would like it to look like something like this 

```

server@server:/assessOne$

```


If you have something like this in your $HOME/.bashrc:

```

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi

```

Try altering to:


```

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\**[COLOR="Red"]W[/COLOR]**\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\**[COLOR="Red"]W[/COLOR]**\$ '
fi

```

This might be what you are after, otherwise you can see all the settings in:

```
man bash
```

and then search for *PS1*. Hope that helps? The changes I have suggested are from a lower case 'w' to uppercase 'W' with the idea:

```

\w     the current working  directory,  with  $HOME  abbreviated
       with a tilde
\W     the ***[COLOR="Purple"]basename[/COLOR]*** of the current working directory, with $HOME
       abbreviated with a tilde

```

Andrew

---

