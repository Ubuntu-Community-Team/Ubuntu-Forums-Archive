---
title: "gvim on KDE: /usr/bin/esd not found"
date: 2007-06-15
forum: Desktop Environments
---

### Post by jinzishuai on 2007-06-15
Hi there,

I am running Kubuntu feisty. I am happy with it most of the time but very annoyed by the error given out at the konsole whenever I run gvim:
```

seki@kalmar:~$ gvim
/bin/sh: /usr/bin/esd: not found
seki@kalmar:~$               

```
Is there a way to get rid of this warning message? I am using ALSA for the sound system and happy with it.
Thanks.

Shi

---

### Post by jinzishuai on 2007-06-15
I figured it out.
```

sudo apt-get install vim-gtk
cd /etc/alternatives
sudo ln -s /usr/bin/vim.gtk gvim -f

```
The gvim link was 
```

/etc/alternatives/vim -> /usr/bin/vim.full

```

---

### Post by dennispeters on 2007-06-19
Just a tip: rather than fiddling the /etc/alternatives links by hand, use 

```
sudo update-alternatives --config gvim
```

---

