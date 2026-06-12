---
title: "Linux shell - cisco-like auto completion"
date: 2009-02-22
forum: General Help
---

### Post by peter.gastinger on 2009-02-22
Hi guys, 

This question is not necessarily related to Ubuntu, it is just a linux shell question in general, I hope you don't mind :-)

At work, I have to deal with Cisco equipment quite a lot. The best feature of the Cisco IOS cli is the possibility to execute commands without typing the whole command. As soon as it is not ambiguous anymore, I can press enter and the command will be executed, e.g.
```
sh ip r
```

I know that there are some linux commands with a similar behavior, e.g.
iproute2:
```
ip r
```
which is the same as 
```
ip route
```

My point is, that I don't want to press the TAB-key for auto-completion. I want to execute a command as soon as it is not ambiguous anymore, e.g
```
peda@peda-desktop:~$ ifc
bash: ifc: command not found

```
This command is not ambiguous, but I have to press TAB key to get a valid command ```
ifconfig
```.

Is there any linux shell with this feature?

thanks guys

regards
peter

---

### Post by kmac on 2009-02-22
I like this idea. I don't have quite an idea on how to execute it as far as a shell modification. The most primal method I can think of would be copying any ambiguous command names in $PATH to their shortened versions. It would seem like having * automatically appended to any $PATH-referring commands would in theory solve this, but again, I wouldn't know exactly where to start with that.

---

### Post by Faolan on 2009-02-22
This is a God send when working with Cisco hardware, it's something that would be useful with any CLI interface.

---

