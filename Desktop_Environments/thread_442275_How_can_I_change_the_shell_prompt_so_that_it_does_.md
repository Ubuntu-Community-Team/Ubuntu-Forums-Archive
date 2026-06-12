---
title: "How can I change the shell prompt so that it does not show the full path?"
date: 2007-05-13
forum: Desktop Environments
---

### Post by yinglcs2 on 2007-05-13
How can I change the shell prompt so that it does not show the full path? 

But just the last 3 directories up from my current directory?

Thank you.

---

### Post by gborzi on 2007-05-13
AFAIK it's not possible in bash to display only the last 3 directories in the prompt. You can show the last one directory by editing your .bashrc file, search for the lines that define the promtp (i.e. PS1=) and change the lowercase "w" to an uppercase one. E.g. I have > PS1='${debian_chroot:+($debian_chroot)}\u@\h:\W\$ ' instead of the default > PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
You can have a look at the bash manpage, at the PROMPTING section.

---

### Post by yinglcs2 on 2007-05-19
Thanks. But how can I put the current directory and 3 levels up at the prompt.

The man page only show either full  path or the current path. I want something in the middle.

Thank you.

---

### Post by Rinzwind on 2007-05-19
gborzi: ofcourse it's possible :)

Here's a page dedicated to the prompt.
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

yinglcs2: here's an example:
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x783.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x783.html)
> #   How many characters of the $PWD should be kept
local pwdmaxlen=30
#   Indicator that there has been directory truncation:
#trunc_symbol="<"
local trunc_symbol="..."
if [ ${#PWD} -gt $pwdmaxlen ]
then
	local pwdoffset=$(( ${#PWD} - $pwdmaxlen ))
	newPWD="${trunc_symbol}${PWD:$pwdoffset:$pwdmaxlen}"
else
	newPWD=${PWD}
fi
This one makes it a maximum of 30 characters. Change that variable into something checking  for more than 3 "/"'es.

---

### Post by gborzi on 2007-05-19
Thanks Rinzwind,
I didn't know that HOWTO.

---

