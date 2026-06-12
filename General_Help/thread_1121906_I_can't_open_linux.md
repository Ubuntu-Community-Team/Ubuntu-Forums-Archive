---
title: "I can't open linux"
date: 2009-04-10
forum: General Help
---

### Post by matteo123 on 2009-04-10
I am new to linux and I have been using for some time now. I only use the visual interface and don't know how the command option works. Now I have a problem, last time I used ubuntu, it froze and I forced shut it down. Now it won't open the visual interface, where I have many files. I can use to command option, I manage to log in, but that's it. 
I need some help. Can anyone help me?

---

### Post by N_Nick on 2009-04-10
> **matteo123 said:**
> I am new to linux and I have been using for some time now. I only use the visual interface and don't know how the command option works. Now I have a problem, last time I used ubuntu, it froze and I forced shut it down. Now it won't open the visual interface, where I have many files. I can use to command option, I manage to log in, but that's it. 
I need some help. Can anyone help me?

```
startx
```

Try that after logging in using the command line but there may be something wrong with Xorg

---

### Post by maheshasolkar on 2009-04-10
After you login, can you run the following:

```
  startx &
```

What happens when you run that?

Is there a way to collect the output of some commands and post it here? In other words, can you get some file from your Linux partition and post them here?

---

### Post by iponeverything on 2009-04-10
what is the output of:

```
startx

```

---

