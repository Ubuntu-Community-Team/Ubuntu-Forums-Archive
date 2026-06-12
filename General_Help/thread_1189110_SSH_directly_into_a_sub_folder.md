---
title: "SSH directly into a sub folder"
date: 2009-06-16
forum: General Help
---

### Post by Phoenix` on 2009-06-16
Is there any way i can use the SSH command to log directly in to a sub folder on a remote server?

---

### Post by ohzopants on 2009-06-16
Yup.

```

ssh user@host_address/path/to/dir

```

I **_believe_** (and by "believe" I mean I may have heard something along these lines once but never actually investigated it) the ssh daemon sets a "root" directory so if your server is not setup to use / as the root you will not be able to go "higher" in the file system and you will need to specify the path relative to this root directory.

The default sshd installation in ubuntu sets the root at /.

---

### Post by Jose Catre-Vandis on 2009-06-16
Close, ohzopants, but you need to run a command like this:
```
ssh -t jose@10.10.10.70 "cd /home/jose/Documents ;bash"
```

This does however put you into a bash shell, so to depart you need to type "exit" as opposed to "logout"

---

### Post by ohzopants on 2009-06-16
Granted your way will work Jose, but I frequently use my way to connect to my desktop from my laptop.  The only thing I'm not sure about is whether a / or a : is required after the host address.

---

### Post by Jose Catre-Vandis on 2009-06-16
Hmmm, neither : nor / "your way" works for me, I also tried with spaces and without spaces. 

Not sure I understand:
> I frequently use my way to connect to my desktop from my laptop.
in which case, why you don't know:
> whether a / or a : is required after the host address

---

### Post by ohzopants on 2009-06-16
The reason I can't remember whether it's a colon or a slash is because I always just use "history | grep ssh" then !NNN.

I'll try it out again when I get home...

---

### Post by Jose Catre-Vandis on 2009-06-17
Thanks, would be good to know :)

---

### Post by ohzopants on 2009-06-17
Well... my router died so now I can't ssh at all :(

---

### Post by Jose Catre-Vandis on 2009-06-18
:lol:

---

### Post by geirha on 2009-06-18
I think you are confusing ssh syntax with scp syntax. Jose Catre-Vandis's suggestion is the one I'd suggest as well.

---

### Post by ohzopants on 2009-06-19
So... ummm... can we please pretend I never said anything  :oops:

I think I was thinking of scp... because that definitely does not work with ssh.

---

### Post by Jose Catre-Vandis on 2009-06-24
said what? :)

---

