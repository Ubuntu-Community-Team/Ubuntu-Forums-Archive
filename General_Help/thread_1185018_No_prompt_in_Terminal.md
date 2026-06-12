---
title: "No prompt in Terminal"
date: 2009-06-11
forum: General Help
---

### Post by dyess002 on 2009-06-11
My terminl will open but will only show a cursor, It won/t show the $ or the username, I can use the run and gnome-terminal -e sh and get a terminal with just a $ nd this ill let me type in commands but the other wont let commands work..
I would love to get it back to where it used  to be.

---

### Post by dyess002 on 2009-06-11
I am using Ubuntu 9.04  on a HP DV8000 2gig RAM 200g hd 1600 cintrino duo

---

### Post by kuja on 2009-06-11
Which shell are you using? Try running "bash" and see if you get a different result.

---

### Post by synapsys on 2009-06-11
Have you been mucking around with PS1 or /etc/bash.bashrc?

---

### Post by dyess002 on 2009-06-12
no I havn't been mucking around with nothing, If I wanted to get hollered at I would have asked my dad. I don't really know how to mess around with Bash. I am pretty new Just got switched from XP to Ubuntu.
I have  book on Ubuntu but I havn't read anything on running Bash.all it seems to cover is commands and what the bash is.
If you will tell me how to run Bash  I will try. There is a lot that I don't understand about Linux yet but everyday i seem to learn something.

Thanks kuja for the help.

---

### Post by colau on 2009-06-12
> **dyess002 said:**
> no I havn't been mucking around with nothing, If I wanted to get hollered at I would have asked my dad. I don't really know how to mess around with Bash. I am pretty new Just got switched from XP to Ubuntu.
I have  book on Ubuntu but I havn't read anything on running Bash.all it seems to cover is commands and what the bash is.
If you will tell me how to run Bash  I will try. There is a lot that I don't understand about Linux yet but everyday i seem to learn something.

Thanks kuja for the help.
What happens?
```

ALT+F2

```
type 
```

gnome-terminal

```

Try reinstalling bash shell.
System>Administration>Synaptic Package Manager
search bash click apply...

---

### Post by dyess002 on 2009-06-12
There was a problem with the command for this terminal: Text was empty (or contained only whitespace)


This is the error i got Colau

---

### Post by colau on 2009-06-12
> **dyess002 said:**
> There was a problem with the command for this terminal: Text was empty (or contained only whitespace)


This is the error i got Colau
Try reinstalling bash shell.
System>Administration>Synaptic Package Manager
search bash click apply...

---

### Post by dyess002 on 2009-06-12
I tried to install Bash and got this message.



E: g15daemon: subprocess post-installation script returned error exit status 1
E: g15stats: dependency problems - leaving unconfigured

---

### Post by dyess002 on 2009-06-12
Ok I finaly got the BASH reinstalled with no errors and no luck still no command prompt.

I havn't seen this problem nowhere in Linux forums.
Leave it to me to have a problem no one has never had before. Hope you guys can come up with something

---

### Post by iponeverything on 2009-06-12
looks like you got passed the dpkg issue, so disregard the below.

==================

Does Ctrl+Alt+F2 open a Virtual terminal?

If so, edit your g15daemon init script like so:

First backup the orginal by copying it to /root/:

```
sudo cp /etc/init.d/g15daemon /root/g15daemon.orginal
```

Next edit it using nano and replace the line with DAEMON= <path-to-prog> with "DAEMON=/bin/true" save the file. Reboot and see if it fixes the the dpkg error.

```
sodo nano /etc/init.d/g15daemon 
```

---

### Post by dyess002 on 2009-06-12
Ok guys i got it fixed.
Heres the deal.
I opened the terminl up and wwent to edit profiles/EDIT/Title and command TAB/and unchecked ( run a custom command instead of my shell ) and restarted the Shell and that done it.
Thanks for your help.
I have learned something.

---

### Post by colau on 2009-06-12
> **dyess002 said:**
> Ok guys i got it fixed.
Heres the deal.
I opened the terminl up and wwent to edit profiles/EDIT/Title and command TAB/and unchecked ( run a custom command instead of my shell ) and restarted the Shell and that done it.
Thanks for your help.
I have learned something.
That was tricky.
Cheers.:D

---

