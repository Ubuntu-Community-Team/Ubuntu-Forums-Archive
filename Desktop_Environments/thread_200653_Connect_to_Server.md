---
title: "Connect to Server"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Isoss on 2006-06-20
I have Xubuntu, and I have downloaded ssh and openssh-server. in ubuntu-desktop I used to go to places->Connect to server and create my ssh connetion. What can I do the same in xubuntu?

Thanks.

---

### Post by linuchsan on 2006-06-20
You can use putty

---

### Post by lamego on 2006-06-20
From the terminal:
```
ssh user@server
```

---

### Post by Isoss on 2006-06-20
I know that and that's what I do but I need to SSH folders, putty SSHes with commands only, you can't manage folders ...

---

### Post by muzungu on 2006-06-21
[QUOTE=Isoss]I have Xubuntu, and I have downloaded ssh and openssh-server. in ubuntu-desktop I used to go to places->Connect to server and create my ssh connetion. What can I do the same in xubuntu?[/QUOTE]

gFTP supports ssh connections. It should be available in your unrestricted repositories via Synaptic...

---

### Post by SerafeimG on 2007-12-03
That's it!
gFTP is great! 
You can also install it through the "Add/Remove..."

---

### Post by Chas_E_Erath on 2007-12-03
For future reference: you should be able to use 'scp' which (I think) is part of openssl.

```
scp  local-filename  user@server:remote-filename   
```

it works backwards as well.

---

