---
title: "can't connect to remote X font server"
date: 2006-03-27
forum: Desktop Environments
---

### Post by gstrock on 2006-03-27
I started an x font server on a Sun solaris machine.
> **xfs -port 7101**

I can see the font server fine from another sun machine:
> **fslsfonts -server 10.10.30.27:7101**
    -adobe-courier-bold-o-normal--0-0-0-0-m-0-iso8859-1
    -adobe-courier-bold-o-normal--0-0-100-100-m-0-iso8859-1
    etc....

But from my Kubuntu (5.10) workstation I get this:
>** fslsfonts -server 10.10.30.27:7101**
_FSTransOpen: Unable to find transport for tcp
fslsfonts:  unable to open server "10.10.30.27:7101"

I know about the* '-nolisten tcp' *in kdmrc and so I have
  ServerArgsLocal=

I'm stumped.

---

