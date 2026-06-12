---
title: "Missing EnvyNG GUI"
date: 2009-01-15
forum: General Help
---

### Post by AdamMPkins on 2009-01-15
I installed EngyNG to help me with the drivers for my Nvidia Geforce go 7900 gs. I installed it using the command "sudo apt-get install envyng-gtk". Now, when i check under system tools, there is no envy interface available. I can use its terminal interface using -t but no GUI. Can anyone offer assistance?

---

### Post by AdamMPkins on 2009-01-15
any help?

---

### Post by redilyn on 2009-01-16
Did you install the right GUI for envyng? 

What happens when you try the command

```

envyng -g

```

---

### Post by AdamMPkins on 2009-01-16
> **redilyn said:**
> Did you install the right GUI for envyng? 

What happens when you try the command

```

envyng -g

```

I tried 
```

envyng -g

```
I got the message:
```

ERROR: Make sure that envyng-qt is installed

```
I assume this is talking about the qt4 interface, if so how do i install that?

---

### Post by DeMus on 2009-01-16
> **AdamMPkins said:**
> I tried 
```

envyng -g

```
I got the message:
```

ERROR: Make sure that envyng-qt is installed

```
I assume this is talking about the qt4 interface, if so how do i install that?

To install envyng qt use Synaptic Package Manager. Start it, type your password en search for envyng.
You'll find 3 answers, one of them is called envyng-qt. I don't have it installed and I do have a GUI. I did install envyng-core and envyng-gtk.
Success.

DeMus

---

### Post by AdamMPkins on 2009-01-18
> **DeMus said:**
> To install envyng qt use Synaptic Package Manager. Start it, type your password en search for envyng.
You'll find 3 answers, one of them is called envyng-qt. I don't have it installed and I do have a GUI. I did install envyng-core and envyng-gtk.
Success.

DeMus

but why should i have to install a qt4 interface with ubuntu. Its not kde.

---

### Post by Nepherte on 2009-01-18
You should verify that envyng-gtk is installed, not envyng-qt.

---

### Post by deanjm1963 on 2009-01-18
There is no GTK gui for Envy if you're using Intrepid, it's only a "dummy package", you must use the text interface. I remember reading in another post about it being difficult to port to Intrepid.

Hope this helps

---

