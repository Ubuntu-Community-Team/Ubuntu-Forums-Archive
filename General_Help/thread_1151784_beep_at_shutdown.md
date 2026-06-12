---
title: "beep at shutdown"
date: 2009-05-07
forum: General Help
---

### Post by ravica on 2009-05-07
I've desactivated the terminal's beep but it already sounds, but only when I click the shutdown button. 
I use Ubuntu 9.04 on a Dell Vostro 1000

Thank you.

---

### Post by BslBryan on 2009-05-07
Hello, ravica. :-)

Firstly, *the system does beep for a reason.*  It's a warning.

However, it is very annoying. :P

Since you've already tried quieting it with the terminal, I'll point you to this:

```
gksudo gedit /etc/modprobe.d/blacklist
```

And paste this line at the end:

```
blacklist pcspkr
```

Please come back and post whether or not it actually worked? 

Best to you, ravica, and good luck. :-)

---

### Post by ravica on 2009-05-07
thank you but this file doesn't exist in 9.04 in this folder.

i'm using jackalope

---

### Post by BslBryan on 2009-05-07
Yes, there very much is a Jaunty blacklist.  

I'm almost one hundred percent sure that I gave you the right path, too:
/etc/modprobe.d/blacklist

It's just something that doesn't change in the distros and flavours.  

Try checking again. 

Regards. :-)

EDIT: You have to either use that code, or open it up in a text editor to paste the line in, by the way. :-)

---

### Post by wsonar on 2009-05-07
I have noticed on Jaunty I think the shutdown beep is really loud at least on my latitude 620

I need to disable mine eventually

---

### Post by davev on 2009-05-07
/etc/modprobe.d/blacklist.conf

---

### Post by ravica on 2009-05-07
Very thank to everybody.
It works but the exactly name file is blacklist.conf.

---

### Post by BslBryan on 2009-05-07
#-o ravica, I am terribly sorry.  I completely forgot to put the file extension, and you could have had this solved hours ago.

Anyway, I'm glad it worked out for you. :-)

---

