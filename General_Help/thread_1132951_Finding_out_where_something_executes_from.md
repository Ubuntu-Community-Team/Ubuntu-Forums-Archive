---
title: "Finding out where something executes from"
date: 2009-04-22
forum: General Help
---

### Post by Nano_ext3 on 2009-04-22
Is there a command that will show me the PATH that command runs from.  For example running xscreensaver may come from /usr/bin.

SO is there a way to run a command to determine where something executes from?

Thanks,

Nano

---

### Post by dabl on 2009-04-22
> **Nano_ext3 said:**
> 

SO is there a way to run a command to determine where something executes from?



Such a Windows-like question!  :lolflag:

Try 

```
locate xyz
```

to learn where files beginning with "xyz" can be found in your filesystem.  For example

```
locate gedit
```

Probably there is a way in Ubuntu to open a menu editor and see where packages listed on your menu are run from -- in Kubuntu you right-click over the big KMenu button and then choose "menu editor" and you can see the command that runs the executable.

I'm really curious about what you plan to do on a Linux system with this Windows-centric tidbit of knowledge .......   :P

---

### Post by codeseer on 2009-04-22
```
whereis xscreensaver
```

---

### Post by powder on 2009-04-22
I think you would use the whereis command.

```
whereis gedit
```

---

### Post by michy99 on 2009-04-22
The which command will show where the executable is.

```
which firefox
```

---

### Post by Nano_ext3 on 2009-04-22
> **dabl said:**
> Such a Windows-like question!  :lolflag:

Try 

```
locate xyz
```

to learn where files beginning with "xyz" can be found in your filesystem.  For example

```
locate gedit
```

Probably there is a way in Ubuntu to open a menu editor and see where packages listed on your menu are run from -- in Kubuntu you right-click over the big KMenu button and then choose "menu editor" and you can see the command that runs the executable.

I'm really curious about what you plan to do on a Linux system with this Windows-centric tidbit of knowledge .......   :P

I only ask this because I run a blog and thought it'd be a nice thing for a linux user to determine what folder a command runs from , because in distros like Arch Linux, you end up having to make manual launchers for many things, I don't really use Ubuntu, only for teaching others about linux via the Beginners Team on this site.  I wanted to know this command, because it makes it easy to then find where to make the shorcut to with "ln" or the shortcut maker.

Sheesh, sorry for asking.

Nano

---

### Post by Nano_ext3 on 2009-04-22
> **michy99 said:**
> The which command will show where the executable is.

```
which firefox
```


This worked thank you

---

### Post by powder on 2009-04-22
> **michy99 said:**
> The which command will show where the executable is.

```
which firefox
```

Good call. :)

---

### Post by Nano_ext3 on 2009-04-22
> **michy99 said:**
> The which command will show where the executable is.

```
which firefox
```

I gave you credit on [www.linuxcauldron.com](www.linuxcauldron.com)

_Nano

---

