---
title: "Blank Terminal"
date: 2005-05-31
forum: Desktop Environments
---

### Post by Amdmhz on 2005-05-31
Hi all. I just ran into a very strange problem today. Everytime I start up the terminal window it stays completely Black for about 3 minutes and then finally goes to the command prompt. Just as a test I opened up Konsole terminal window and that comes right up.  Has anyone else seen this problem? Or can someone make a suggestion on how to fix this?

Thanks for your time O:) 

Amdmhz

---

### Post by Xerampelinae on 2005-05-31
[QUOTE=Amdmhz]Hi all. I just ran into a very strange problem today. Everytime I start up the terminal window it stays completely Black for about 3 minutes and then finally goes to the command prompt. Just as a test I opened up Konsole terminal window and that comes right up.  Has anyone else seen this problem? Or can someone make a suggestion on how to fix this?

Thanks for your time O:) 

Amdmhz[/QUOTE]
 As a shot in the dark
```

sudo fc-cache -fv

```

You might also try
```

strace gnome-terminal

```
And watch the output.  There's a chance that you'll be able to tell what is hanging the program up.

---

### Post by Amdmhz on 2005-06-01
I did more testing and the terminal seems to be fine until I turn on my wireless connection. Then it takes 3 minutes before the terminal program starts to work? strange

---

### Post by Xerampelinae on 2005-06-01
On my machine the output of 'hostname' produces 'xu'.  So in my /etc/hosts I have the following:

```

127.0.0.1       localhost.localdomain   localhost       xu

... (and other ip6 stuff that we don't care about) ..

```

Yours should look similar, if not you might want to make sure your network connections are all set up correctly in terms of your host name and such.

---

### Post by Amdmhz on 2005-06-01
Thanks for the help. Here is where is hangs for 3 minutes:

read(18, "127.0.0.1 localhost.localdomain "..., 4096) = 219
close(18)                               = 0
munmap(0xb6fec000, 4096)                = 0
socket(PF_INET, SOCK_STREAM, IPPROTO_IP) = 18
fcntl64(18, F_SETFD, FD_CLOEXEC)        = 0
setsockopt(18, SOL_SOCKET, SO_REUSEADDR, [1], 4) = 0
connect(18, {sa_family=AF_INET, sin_port=htons(16001), sin_addr=inet_addr("127.0.0.1")}, 16

does not say what hostname it is looking for.

---

