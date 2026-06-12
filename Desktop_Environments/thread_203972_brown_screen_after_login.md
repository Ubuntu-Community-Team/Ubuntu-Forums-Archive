---
title: "brown screen after login"
date: 2006-06-26
forum: Desktop Environments
---

### Post by haytjes on 2006-06-26
hello everyone,

I have tried to get Ubuntu 6.06 working, but doesn't work.

First I started with a live cd (beta) and got a brown screen. Same problem occurs after the live cd (final). So I was not able to install Ubuntu 6.06 totaly new.

Thereafter I decided to upgrade my ubuntu breezy, by the update manager. Everything went well, but after loging in, I get again a brown screen with my cursor, but nothing else. Next I installed kde and kde worked properly, so I'm sure it is something with gnome.

So atleast I tried with a server cd, changing the kernel to desktop (2.6.25-386 I think) and apt-get install ubuntu-desktop. Again I started and I got an brown screen after login. I made an new user 'test' (useradd in terminal (ctrl-alt-F1)) and tried to login. I was ashtonished it worked. The new user 'test' want to login and now I'm working on it.

But my quest isn't finished. The user I created, hasn't got everything. Like it isn't in the sudo config, the app installer in system does'nt show up ... So I tried more.

I deleted my normal account home-folder "haytjes", but still brown screen. So I think it is something to do with something other.

Now I will search further but I don't know some things.
- how can you search (in the terminal) for every file with "haytjes" in, without "test", because i could be one of these files make Gnome doesn't start.
- how can you make a new user, with the same privileges as your first account (like "haytjes")

or is there already an explanation for the fenomen. I didn't find it on the internet ...

(I'm not an English person, so please don't pay attention to the writing faults)

---

### Post by lkagan on 2006-06-26
The problem is probably with the firewall.  I haven't looked very deeply into it but if your firewall is too strict, the X Windows system cannot fully load.  I have the same issue on booting up my laptop.  But I just flush all iptables rules, set the default policy to accept and then it finishes loading.  I then reset the iptables rules.

Good Luck.

Larry

---

### Post by haytjes on 2006-06-26
can you give me described instruction, because I never did before
and i would be easy

else I will search for it

thanks

---

### Post by lkagan on 2006-06-26
There is a program called Firestarter that is a graphical front end to iptables.  I don't like it but maybe you will.  You can configure your firewall with it.  I don't know how to allow X Windows to start up properly without completing temporarily shutting down my firewall which really isn't a good idea.  But here it is anyway.  First hit <ctl><alt><F2>.  This will bring you to a console window, without graphics.  Now login.  Then type:

```
sudo iptables -F; sudo iptables -A INPUT ACCEPT; sudo iptables -A OUTPUT ACCEPT
```

Then hit <ctl><alt><F7> and you'll be back on your graphical desktop and it should finish loading.  Note that you will not have any firewall.  However, that's how Breezy Badger shipped by default so it's not so far fetched for an Ubuntu system.

Larry

---

### Post by haytjes on 2006-06-26
it took a wile to figure out (needed to use su insteat of sudo (wich doesn't work in my test-gnome account)

But I tried to stop the firewall with Firestarter, but no reaction of my ubuntu on ctrl-alt-F8. Also I tried the script you posted, but I think there aren't totaly correct.

It give the error it doesn't know what ACCEPT is. If I set a \ in the middle, so it take it as one, it still gives an error ...

---

### Post by haytjes on 2006-06-26
I have tried something, but with no advance:

```
sudo iptables -F; sudo iptables -A INPUT; sudo iptables -A OUTPUT
```
```
sudo iptables -F; sudo iptables -A INPUT; sudo iptables -A OUTPUT; sudo iptables -A FORWARD
```

```
sudo iptables -L
```
shows
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination
           all  --  anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
           all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
           all  --  anywhere             anywhere

but still brown screen

---

