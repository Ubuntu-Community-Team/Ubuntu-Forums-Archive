---
title: "problem with ssh running shell scripts without #!/bin/bash"
date: 2009-02-06
forum: General Help
---

### Post by chupachups on 2009-02-06
Similar to this report

[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/299690](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/299690)

I'm running a clean (new) 32bit intel ubuntu 8.10 install, with openssh-server

I am connecting from a windows xp machine running the latest putty version, the connection works fine

But...

If I try to execute a simple shell script (contains just an echo command), from the putty ssh session, where this script doesn't contain #!/bin/bash, the session completely hangs

If I use ssh under ubuntu to run the same command, it also hangs

If I use terminal under ubuntu to run the same command, it works fine

Is there a resolution ?

---

### Post by mb_webguy on 2009-02-06
Does the ssh session use the bash shell?

If not, then there's your problem.  Without a shell declaration at the beginning of the file, the current working shell is used.  If the script is written for bash and you're currently using ksh, it won't necessarily work.  Both bash and ksh are sh-compatible shells, but they each have functionality the other doesn't, and a script written for one won't necessarily run under the other.

During a ssh session, change to bash and then try running the script.  If it works, then you've found the reason why it won't normally run for you.  This is the reason it's a good idea to have the shell declaration at the beginning of a script, to tell the system which shell it should use.

---

### Post by wirelessmonkey on 2009-02-06
It doesn't look resolved per se, but adding a proper shebang is good form anyway, so until it's fixed it seems that the workaround is simple enough.

---

### Post by chupachups on 2009-02-07
> **wirelessmonkey said:**
> It doesn't look resolved per se, but adding a proper shebang is good form anyway, so until it's fixed it seems that the workaround is simple enough.

this problem was encountered when I was installing oracle 11g, one of the oracle scripts (called dbhome), does not specify the shell. 

Its simple enough to change, but bizarre it works under terminal but not ssh.

Both terminal and ssh were initiated with the same userid, which defaults to bash

I've never encountered this type of problem with putty under windows accessing AIX, so looks like it is specific to linux/ubuntu

---

### Post by chupachups on 2009-02-07
> **mb_webguy said:**
> Does the ssh session use the bash shell?

yup both ssh and terminal sessions invoked from the same userid, which defaults to bash

> **mb_webguy said:**
> If the script is written for bash and you're currently using ksh, it won't necessarily work.

this isn't the issue, I put together a test script, and all it contains is

echo "hallo"

and this exhibits the problem

> **mb_webguy said:**
> During a ssh session, change to bash and then try running the script.

this isn't the issue, from my ssh session, echo $SHELL gives me /bin/bash

---

### Post by Locutus_of_Borg on 2009-02-07
you can try:
```
`cat $file`
```
where $file is the script, and note that those are backticks (same key as ~ ) and not apostrophe's

this will execute the contents of the file as if you had typed them into the terminal

---

### Post by chupachups on 2009-02-07
> **Locutus_of_Borg said:**
> you can try:
```
`cat $file`
```
where $file is the script, and note that those are backticks (same key as ~ ) and not apostrophe's

this will execute the contents of the file as if you had typed them into the terminal

thanks for the suggestion, but not really the prefered choice in this case where the oracle script (dbhome) can be modified to include #!/bin/bash

what I really want is ssh to behave like terminal, so no code changes are required - and how often do we all write a quick script and forget the #! bit ;) ? Don't want it just hanging and have to kill the session

---

### Post by geirha on 2009-02-07
How exactly are you running the script? I just tried on both Ubuntu 8.04 and 8.10, and it worked as expected on both.
```
ssh localhost ./foo.bash
```

---

### Post by chupachups on 2009-02-07
> **geirha said:**
> How exactly are you running the script? I just tried on both Ubuntu 8.04 and 8.10, and it worked as expected on both.
```
ssh localhost ./foo.bash
```

I establish an ssh session first, and then run the command

ie

ssh localhost
cd projects
./foo.bash


BTW, running it in the manner you have, does work for me too, we are getting a little closer to understanding whats going on

---

### Post by chupachups on 2009-02-07
geirha

As you have come closest to understanding the steps I am taking, would you mind taking a few more mins out of your day to try to reproduce the problem on your system ?

I just want piece of mind to confirm that it isn't some quirk of my system/me

ta muchly

---

### Post by geirha on 2009-02-07
Right, I'm able to reproduce it now. The notable difference I can see, is that when logging in with ssh, you'll get to a login shell, while the shell you have in a gnome-terminal, is a non-login shell by default. One difference between a login shell and a non-login shell is that the login shell reads .profile (or .bash_profile), while the non-login shell only reads .bashrc. I don't know if that can have anything to do with it, and I don't know much of what the other differences are.

Notably, when ssh-ing in, then running ./foo.bash, it does hang. Only way to get the shell back seems to be to stop it with Ctrl+z or kill it from another shell. If however, you first start a non-login shell, it runs fine. On the other hand, if you skip the ssh-bit, and start a login shell, it will also hang. This does not happen at all on Hardy.
```

ssh user@host
./foo.bash    # Hangs

ssh user@host
bash
./foo.bash    # Works.

bash --login  # (no ssh involved)
./foo.bash    # Hangs

ssh user@host ./foo.bash   # This works, because ssh actually runs: bash -c "./foo.bash"

```

You shouldn't really expect a script to work this way without a sh-bang, but if anything, bash should give you a warning or error, not hang, so I'd say this is a bug in bash.

So, in conclusion: It's not just you. :)

---

### Post by chupachups on 2009-02-07
> **geirha said:**
> This does not happen at all on Hardy.


glad to know its not just me

from your investigations its specific only to intrepid ibex ? how do things like this creep into new versions ?

being new to ubuntu, how do I get it investigated/fixed ? or at least see if it has already been reported ?

---

### Post by chupachups on 2009-02-07
thanks for your assist geirha, reassures me that I am not a complete twonk

---

### Post by geirha on 2009-02-07
> **chupachups said:**
> glad to know its not just me

from your investigations its specific only to intrepid ibex ? how do things like this creep into new versions ?

being new to ubuntu, how do I get it investigated/fixed ? or at least see if it has already been reported ?

[http://launchpad.net](http://launchpad.net) is the place to go to report bugs. Search for the app in question, then go to the bugs page for the app/project and then search and/or report the problem.

In this case:
[https://bugs.launchpad.net/bash/+bugs](https://bugs.launchpad.net/bash/+bugs)

EDIT: Uhm, strike that. This would be the place. Searching on launchpad is not always easy :/
[https://bugs.launchpad.net/ubuntu/+source/bash](https://bugs.launchpad.net/ubuntu/+source/bash)

---

