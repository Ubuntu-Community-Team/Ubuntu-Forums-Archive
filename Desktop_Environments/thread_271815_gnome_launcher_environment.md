---
title: "gnome launcher environment"
date: 2006-10-05
forum: Desktop Environments
---

### Post by dharrigan on 2006-10-05
Hi,

If I create a launcher, that invokes a script, how do get that
launcher to use my .bashrc? I have a script that works fine on the command line in ~/bin (with ~/bin added to my path in .bashrc). When I create a launcher invoking that script, it doesn't read my .bashrc, and if I source it using . ~/.bashrc that doesn't work either...

Any ideas on how to get the launcher to honour my .bashrc?

-=david=-

---

### Post by PriceChild on 2006-10-05
I'm not the most bash savvy around here....

Why don't you copy it into /usr/local/bin ?

---

### Post by dharrigan on 2006-10-05
Hi,

Thanks for your reply, but that, to me, is unclean. I like to keep everything under my $HOME directory for ease-of-backup. I could copoy the script in there, as you very rightly mention, and it would work, but I prefer in my $HOME/bin, that way, I just backup my home directory and I leave the system "untouched".

I've lost count the number of times I've restored my system from a clean install, then just copied across my $HOME directory from a backup and been up and running quickly, and not forgetting that I've shoved files into /usr/local/bin or /usr/bin or modifed some /etc/ settings...

I appreciate the help, but it's not quite what I'm after...

-=david=-

---

### Post by nikhilk on 2006-10-05
> **dharrigan said:**
> if I source it using . ~/.bashrc that doesn't work either...
Are you sourcing bashrc in your script itself? If yes that should probably work.

---

### Post by dharrigan on 2006-10-05
Yes, 

In my script I have

. ~/.bashrc
...
...

but when I echo the $PATH for example, it gives the default GNOME path and not my modified $PATH.

-=david=-

---

### Post by CatKiller on 2006-10-05
Out of interest, are you using the ~/bin path or the absolute /home/dharrigan/bin path? Might make a difference.

---

