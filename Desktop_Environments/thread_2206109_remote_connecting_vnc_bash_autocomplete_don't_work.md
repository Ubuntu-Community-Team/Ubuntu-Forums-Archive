---
title: "remote connecting vnc bash autocomplete don't working"
date: 2014-02-17
forum: Desktop Environments
---

### Post by e_defranco on 2014-02-17
Hi to all,

I have a strange problem: when I connecting to my desktop (but I have tested also on other 12.04 install) with vnc from remote, the bash autocomplete don't working for any users.

I have checked that the autocomplete is not commented in .bashrc, in /etc/bash.bashrc and in /etc/skel/.bashrc

Some ideas ?

Thank in advance, 

emilio

---

### Post by Toz on 2014-02-17
Have a look at [this post]("http://ubuntuforums.org/showthread.php?t=1771058&p=11107297&viewfull=1#post11107297") for one possible solution. You can also use Ctrl+i to auto-complete through vnc.

---

### Post by e_defranco on 2014-02-17
Thank you very much for your very very quickly answer !!!

After the modifications that you have suggested, all working fine.

In my case the row to change is 124 (I see also another one but it was with the modification done)

I have replicated this on other 4 my workstation and in all, after the modificazion, autocomplete working fine trought vnc.

In any case, ctrl + i working always.

Thank you very much,

Emilio

---

