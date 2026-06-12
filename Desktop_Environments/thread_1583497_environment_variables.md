---
title: "environment variables"
date: 2010-09-27
forum: Desktop Environments
---

### Post by m.dr on 2010-09-27
I know this has been talked about at length but somehow it's not working for me.

I added a new path /usr/lib/trilinos to the default PATH that is already there in /etc/environment.

I tried adding in 2 ways.
1. Creating a new line PATH="$PATH:/usr/lib/trilinos"
2. I also tried just appending to end of the first line already there by just adding :/usr/lib/trilinos within the quotes.

I saved and started a new terminal and typed echo $PATH and neither time the new path that I added showed up.

What am I doing wrong? I thought that /etc/environment is where its read from.

Thanks.

---

### Post by Tibuda on 2010-09-27
add the same **PATH="$PATH:/usr/lib/trilinos"** line to your ~/.bashrc file instead

---

### Post by lexfati on 2010-09-27
Adding that line to ~/.bashrc will work, but you might find ~/.profile easier to read.  That should work just as well.

---

### Post by m.dr on 2010-09-28
Thanks. But I had added it to .profile and it did NOT work. .bashrc worked however.

Is there a file that I could keep such as .environ_vars and keep all my vars there and add a line in my .bashrc file such as below:


if [ -f ~/.bash_environ_vars ]; then
    . ~/.bash_environ_vars
fi

I am trying to get a portable file, easily modifyable and readable that can be shared between a couple of machines. I thought /etc/environment was for that but i don't understand what it is for really.

But thanks.

monosij

---

