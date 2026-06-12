---
title: "open a graphical aps from within terminal logged in as a secondary user"
date: 2009-04-14
forum: General Help
---

### Post by Primefalcon on 2009-04-14
ok here's my situation

I've created a secondary user on my system with minimum privileges called primechat... for security....

Anyhow, I logged into this second user account from the terminal using....

```
sudo su primechat
```

it worked as expected I logged into the account with minimum privileges, however when I ran the command xchat to open xchat I got the following error

```
primefalcon@Blackbeard ~ > sudo su primechat
primechat@Blackbeard:/home/primefalcon$ xchat
No protocol specified

(xchat:10276): Gtk-WARNING **: cannot open display: :0.0
primechat@Blackbeard:/home/primefalcon$ 

```

what am I missing here?

---

### Post by Primefalcon on 2009-04-14
I know it's probably only something simple I'm missing

---

### Post by unutbu on 2009-04-14
As primefalcon, type
```

xhost +local:
```

Then as primechat, try xchat again.

The xhost command will allow all local users to connect to your X server display. I have not found a way to limit it to just one user.

---

### Post by Yashiro on 2009-04-14
[COLOR="green"]xhost +[/COLOR]
[COLOR="green"]su - primechat[/COLOR]
<password>
[COLOR="green"]export DISPLAY:0.0[/COLOR]
<run app here>

---

### Post by Primefalcon on 2009-04-15
> **unutbu said:**
> As primefalcon, type
```

xhost +local:
```

Then as primechat, try xchat again.

The xhost command will allow all local users to connect to your X server display. I have not found a way to limit it to just one user.
Great thats what I wanted, thank you!

---

### Post by HermanAB on 2009-04-15
Another trick is to use SSH to do a loopback connection:
$ ssh user@localhost gedit

---

