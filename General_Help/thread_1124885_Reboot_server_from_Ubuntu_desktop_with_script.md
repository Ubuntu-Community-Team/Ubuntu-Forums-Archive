---
title: "Reboot server from Ubuntu desktop with script?"
date: 2009-04-13
forum: General Help
---

### Post by fistikuffs on 2009-04-13
Hi, I've set my gf up with ubuntu on her laptop as xp was giving terrible performance. She has pretty limited computer experience but with a few simple scripts she has been running ubuntu successfully for nearly 4 months now.

I've been setting up some scripts like rsync to a server etc and now i want her to be able to reboot the server from her desktop by simply double clicking a script for whenever this is necessary. However i think it's beyond my limited skills to do it. The server can be rebooted by ssh with the rebbot command so I assume that firstly a ssh connection needs to be made. So to start i made the following script:

```

    #!/bin/sh

    ssh -C xxx.xxx.x.xxx -p xxxx -l admin


```

with "x" representing the real ip and port numbers. Executing this script opens a login in for the server but when i supply the credentials i get nothing. I'm assuming that at this stage i have logged into the server but not getting any output?

Maybe there is a command to open the output in a terminal screen. Can anyone give any suggestions for this and how to then issue the reboot command?

Also is it possible to add the password for the server to the ssh command?

Thanks

shane

Thanks,

---

### Post by freakyzoidberg on 2009-04-13
i dont know about your problem, but for the credential thing, you cannot
but you can use keys to automatically log from this client
[http://pkeck.myweb.uga.edu/ssh/](http://pkeck.myweb.uga.edu/ssh/)

---

### Post by fistikuffs on 2009-04-14
> **freakyzoidberg said:**
> i dont know about your problem, but for the credential thing, you cannot
but you can use keys to automatically log from this client
[http://pkeck.myweb.uga.edu/ssh/](http://pkeck.myweb.uga.edu/ssh/)

Thanks, setting up keys has been a long time on my to do list and that link is a good start, thanks for that.

Can anybody help with the rest? The server is a qnap 209II if that helps..

---

### Post by sedawk on 2009-04-14
Try running only one command instead of an interactive shell:
```

#!/bin/sh

    ssh -C xxx.xxx.x.xxx -p xxxx -l admin hostname


```
Do you see the hostname of the server after entering the
password?


I recommend to generate your own set of keys
(private+public) and to put your public key to 
~admin/.ssh/known_hosts on the server. This
way you get rid of the password prompt.

There are differences between running an interactive
and non-interactive shell.
At the end your command might look like this
```

#!/bin/sh

    ssh -n -i <your_private_key_file> -o BatchMode=yes ...


```

---

### Post by fistikuffs on 2009-04-16
> **sedawk said:**
> Try running only one command instead of an interactive shell:
```

#!/bin/sh

    ssh -C xxx.xxx.x.xxx -p xxxx -l admin hostname


```
Do you see the hostname of the server after entering the
password?


I recommend to generate your own set of keys
(private+public) and to put your public key to 
~admin/.ssh/known_hosts on the server. This
way you get rid of the password prompt.

There are differences between running an interactive
and non-interactive shell.
At the end your command might look like this
```

#!/bin/sh

    ssh -n -i <your_private_key_file> -o BatchMode=yes ...


```

Hi thanks for the reply. What i'm trying to do is create a launcher on the ubuntu desktop which can, with one click, log into the server via ssh and issue a reboot command to the server.

Its for my girlfriend who i don't want to be messing aroung on the server as root but she might need to reboot the server occasionally.

Excuse my ignorance but i'm not sure of the difference between interactive non-interactive shells.

I've no problem logging in to the server when i issue the ssh -C xxx.xxx.xxx.xxx -p xxxx -l admin from a terminal. But when i create a script with the command and launch it from the desktop it brings up a login screen for the server. When i enter the password i get nothing, the screen just disappears.

---

