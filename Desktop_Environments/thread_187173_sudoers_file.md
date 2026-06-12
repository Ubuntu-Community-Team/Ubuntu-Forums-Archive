---
title: "sudoers file"
date: 2006-06-02
forum: Desktop Environments
---

### Post by jrd on 2006-06-02
Ok, so I've read the man pages on it but keep getting an error when I edit it.
What I'm tring to do is give my wife permission to run "adept_installer" without giving her a full root account. I would like her to be able to do it with no password too.
Thanks in advance for the help.

---

### Post by tonyr on 2006-06-02
How are you editting it?  The correct way is
```

sudo visudo

```

You'll need to know **vi**.

If you are having syntax problems, that's a different story.  What exactly is
the error you are getting?

---

### Post by jrd on 2006-06-02
How are you editting it?  The correct way is
```

sudo visudo

```

You'll need to know **vi**.[QUOTE=tonyr]

If you are having syntax problems, that's a different story.  What exactly is
the error you are getting?[/QUOTE]
I'm having syntax problems, I took two screen shots for you to look at.
Thanks for helping me
(Line 19 is the one that begins with "tabby")

---

### Post by Ramses de Norre on 2006-06-02
To grant a user permission to do that without a password add this line to the sudoers file with the right username:
```
username ALL= NOPASSWD: /usr/bin/adept_installer
```

---

### Post by tonyr on 2006-06-02
Looks like the only difference here is **/usr** instead of **usr**.  I tried
it both ways.  **Norre**'s works.

And I was wrong about **vi**.  I forgot that **visudo** has a default editor.

---

### Post by jrd on 2006-06-02
Well that worked as far as the syntax problem, but it still asks for a password for that user when running that command. (It doesn't accept any passwords.)
I know the way you said to do it is correct because if I run under her name and type sudo-l it says she can run that command as root with no password.

---

### Post by jrd on 2006-06-02
Anybody???

---

### Post by tonyr on 2006-06-02
How are you invoking **adept_installer **from her login session?  In a
terminal (command line), or from **Kmenu->Add/Remove Programs**?

I think the best you can achieve is to have her do
```

sudo adept_installer

```
from the command line in a terminal, which should not ask for a password.   
**Add/Remove Programs** uses **kdesu**, and I'm not sure how well
it plays with **sudoers**.  I haven't explored **kdesu** much.

---

### Post by jrd on 2006-06-03
If I try the command line I get this error...

---

### Post by tonyr on 2006-06-03
Yup, me too.  There is a thing here that I do not understand.  This is already
pretty much beyond my knowledge.  All I can do now is play around, experiment, 
try to learn more.

---

### Post by angrykeyboarder on 2006-06-03
[quote=tonyr]How are you editting it?  The correct way is
```

sudo visudo

``` 
You'll need to know **vi**.[/quote]

Only if vi is your default editor. Otherwise visudo will invoke your default editor (in my case it's nano) to edit the sudoers file.

---

### Post by tonyr on 2006-06-03
So I played around, experimented, wandered in the aether.  Here's what I came up with.

Add **xhost +** as a single new line at the bottom of the file **.bash_profile** in 
the **tabby** home directory. Then do **sudo -H adept_installer** on the command line.

This is a little scary if the machine is on a network.  **xhost +** allows anyone
on the network to open an application on her xserver session.  What it also means
is that there is probably a more restrictive use of **xhost** to allow only one
person on the local machine access. I just haven't figured out what it is.

---

### Post by jrd on 2006-06-03
Thanks for the help. I'll try that. I tried just giving the group "tabby" the same permissions but that didn't work either. I guess Kde just isn't ment to be used like that. Ok I'll stop rambling and try the xhost thing. Thanks for your help!!

---

### Post by Watonga on 2006-06-03
There is indeed a way to make it more restrictive. Here is how to limit it to one certain user:

xhost local:your_user_name

[QUOTE=tonyr]So I played around, experimented, wandered in the aether.  Here's what I came up with.

Add **xhost +** as a single new line at the bottom of the file **.bash_profile** in 
the **tabby** home directory. Then do **sudo -H adept_installer** on the command line.

This is a little scary if the machine is on a network.  **xhost +** allows anyone
on the network to open an application on her xserver session.  What it also means
is that there is probably a more restrictive use of **xhost** to allow only one
person on the local machine access. I just haven't figured out what it is.[/QUOTE]

---

