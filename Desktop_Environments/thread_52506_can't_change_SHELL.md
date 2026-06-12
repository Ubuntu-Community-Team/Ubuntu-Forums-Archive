---
title: "can't change SHELL"
date: 2005-07-28
forum: Desktop Environments
---

### Post by raoaksha on 2005-07-28
i tried changing the default shell from /bin/bash to /bin/tcsh for a user acct.
1. changed it by manually editing the path in /etc/passwd. (the path is correct, since i've enabled root account and root's shell is /bin/tcsh and that works fine)
2.  tried changing it by using the command usermod -s /bin/tcsh <userid>

Once i change the shell and try logging back in, the login screen just goes blank and am again prompted with the login screen (like X is restarting the moment i enter the password and hit enter)
Have been able to do this in other distros w/o much trouble. is there something i'm missing or ubuntu does something different??
right now i'm going  ](*,)  ](*,) 

any help will be appreciated.

thanks.

---

### Post by frodon on 2005-07-28
I also use tcsh with ubuntu and after a fresh install tcsh is not installed. Basically all I do is "apt-get install tcsh" and then go to System>Administration>Group and users and ...  in user preference I choose to use tcsh. And when I open a terminal it always open a tcsh terminal.

---

### Post by raoaksha on 2005-07-28
[QUOTE=frodon]I also use tcsh with ubuntu and after a fresh install tcsh is not installed. Basically all I do is "apt-get install tcsh" and then go to System>Administration>Group and users and ...  in user preference I choose to use tcsh. And when I open a terminal it always open a tcsh terminal.[/QUOTE]

i did install tcsh using the package manager...and checked to make sure that i'm providing the correct path and all..
will give that a (System>Administration>Group and users and ...  in user preference I choose to use tcsh) shot when i get home today. hopefully it works..
though i still don't get why editing the /etc/passwd won't allow me to log in to X!! :roll:

---

### Post by rcerreto on 2005-07-29
I had the same problem.
You should have in your home directory a file named .xsession-error
Looking at the last lines you will likely find:

"/etc/X11/Xsession.d/61pgp-agent: line 5: setenv: command not found"

end here is /etc/X11/Xsession.d/61pgp-agent :

# $Id:$
# In order to activate the session bus at X session launch
# simply place use-session-pgp-agent into your /etc/X11/Xsession.options file
#
eval $(gpg-agent --daemon)

It seems that the script is not happy to be invoked by tcsh.
I just changed it's name to 61pgp-agent.bak (I guess I'm not using it) and... voila kde now starts perfectly!

Hope this helps

---

