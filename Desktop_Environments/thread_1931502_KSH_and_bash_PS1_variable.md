---
title: "KSH and bash PS1 variable"
date: 2012-02-25
forum: Desktop Environments
---

### Post by Rocky007 on 2012-02-25
Hi,

I have ubuntu 11.04. I have installed ksh in my ubuntu 3 months back. All these days it was working fine, now all of a sudden, when I enter to ksh it is showing this instead of my PC name.

"[e]0;u@h: wa]u@h:w$ "

instead of my computer name. 

I set PS1 variable as this in my .profile file

PS1=`uname -n`":$PWD\>"
export PS1

In bash It shows my computer name properly

Rocky-Inspiron-1525:~$

But however even in this the PWD is not displayed.

This same PS1 expression works in AIX unix ksh. Why is it not working in ubuntu ksh?
Could some one please help me understand this and fix this?

Thanks.

---

### Post by just_ken_here on 2012-11-03
Hey. Have u found the fix for yours ?

I was kinda wondering almost the same trick for the prompt, but on OpenBSD 5.1

I spent 4+ hours looking lotsa stuff online that all don't work.

I got the pwd to show on prompt.
But I could not get it to change after changing path.

Do you know that ksh uses 2 : .profile & .kshrc
[http://osr507doc.sco.com/en/OSUserG/_The_Korn_shell_profile_and_kshrc.html](http://osr507doc.sco.com/en/OSUserG/_The_Korn_shell_profile_and_kshrc.html)

What version of ksh did u get from ubuntu ?

---

