---
title: "nohup: can't close terminal"
date: 2011-06-18
forum: Desktop Environments
---

### Post by lucacerone on 2011-06-18
Dear all,
I connect to my server using ssh.
I then try to run a script executing matlab in background,
in /usr/bin/matlabbg I have the following line of code
```
nohup /softwares/matlab2010b/bin/matlab -nosplash -nodesktop -r $1 2 > $2  &
```

When I run a matlab script using:
```
matlabbg mymatlabscript logfile 
```
the process starts being executed correctly and after pressing
enter i can also issue commands in the shell.

However whenever I try to logout from the ssh session
using
```
 exit 
```

The message 
```
logout 
```
appears, but the shell hangs, the connection doesn't close, andit doesn't
goes "back" to my hold shell.
If I try to close it or press CTRL+C
the process on my remote computer is closed.

The connection finishes closing correctly only after the matlab job terminates when 
```
 Connection to myhost closed 
```
appears.

How can I fix this? Till a few days ago everything was working
fine I don't understand what can be causing this.
Thanks a lot in advance, any help would be really appreciated.
Luca

An update: Just a hint: it seems that the logout problem arises only
when I connect using ssh -X myhost.
The issue is not present when I connecto using ssh myhost without the -X option.
Hope it can help figure it out what is wrong.
Thanks a lot in advance,
Cheers, Luca

---

### Post by lucacerone on 2011-06-18
Just a hint: it seems that the logout problem arises only
when I connect using ssh -X myhost.
The issue is not present when I connecto using ssh myhost without the -X option.
Hope it can help figure it out what is wrong.
Thanks a lot in advance,
Cheers, Luca

---

### Post by zadehas on 2011-06-18
To be honest, I don't really know what's wrong with nohup in this case, but I strongly recommend using byobu instead ([https://launchpad.net/byobu](https://launchpad.net/byobu))

With byobu, you can just issue the command in a window and then spawn a new one for other tasks. You can then detach the session with Ctrl+A,D and even logout afterwards, your session will be waiting for you to issue 
```
# byobu -x
```
and all your windows will be restored, including that with your earlier command and its output.

---

### Post by lucacerone on 2011-06-20
thanks zadehas.
I'll try to have a look to byobu (I've also read about "screen"..)
but still would like to solve the original issue :)
Thanks a lot,
Cheers. Luca

---

