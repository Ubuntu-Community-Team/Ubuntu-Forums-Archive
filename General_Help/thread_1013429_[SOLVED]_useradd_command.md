---
title: "[SOLVED] useradd command"
date: 2008-12-16
forum: General Help
---

### Post by Maverick1712 on 2008-12-16
Hi,

I am trying to add a user to my server. the command I am using is:

```
sudo useradd -p password adam
```

Obviously trying to create the user adam with password "password". I also tried this with no space between -p and password. The problem occurs when I try to su into the newly created user. I keep getting "Authentication failure". I've even tried not using the -p command but still getting the same behaviour. Any help is appreciated.

Cheers,
Adam

---

### Post by yabbadabbadont on 2008-12-16
Try using ```
sudo su - adam
``` and see if it works then.

---

### Post by iaculallad on 2008-12-16
You could try:

```
sudo useradd adam
sudo passwd adam

```

Or giving the user a home directory in your server:

```
sudo useradd -d /home/adam -m adam
sudo passwd adam
```

*sudo passwd adam = configures the password of your user 'adam'.

---

### Post by Maverick1712 on 2008-12-16
This caused some weird behaviour. All it seemed to do was change the start of the line in the terminal from:
```

administrator@odin:~$
```

to:
```

$
```

I could still run commands from this prompt and if I typed in "exit", instead of exiting the ssh session it would just bring me back to the way the terminal was before i ran "sudo su adam". Any ideas?

Cheers,
Adam

---

### Post by Maverick1712 on 2008-12-16
Nevermind, this seems to be working. I just need to add some switches to the command to make things work properly. Thanks for the guidance.

Cheers,
Adam

---

### Post by eBoxNet on 2008-12-16
typing exit after the command's execution causing your system to get you back to your user session,when you typed exit you just closed the root's shell session

---

