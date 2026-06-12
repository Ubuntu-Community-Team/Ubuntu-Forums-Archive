---
title: "Lucid Lynx_ start-up program"
date: 2010-06-23
forum: Desktop Environments
---

### Post by nhong on 2010-06-23
I'm using Ubuntu 10.04 LTS 

I added a command in system > preference > startup Applications, the command is to establish a ssh connection to a ssh server: 
```

ssh -p 443 -D 9999 -i /home/nhong/Documents/my_dsa administrator@x.x.x.x
```

This actually don't work at all, I always have to login and open a terminal typing that in order to connect to Internet through a proxy.

How can I get it done automatically after each login session, I've checked both Gnome session and fallsafe gnome session (dont remember exactly) but nothing seems to work

Thanks in advance

A little bit more information, Ive tried another command (gedit) then it works fine that open a unsaved document after login. I've also checked that the command ssh is used without sudo right. it really confuses me.

---

### Post by 3Miro on 2010-06-23
ssh is "secure shell" meaning it runs in terminal. gedit is a graphical program. Here is what is happening:

ssh:
1. terminal opens in the background
2. ssh command is executed and connections is established
3. the terminal stays open in the background and you never see it

gedit:
1. terminal opens in the background
2. gedit command executes and the editor pops up
3. when you exit gedit, the terminal closes

Here is probably what you want to do:

Add gnome-terminal before the ssh command, that is:
```
gnome-terminal "ssh -p 443 -D 9999 -i /home/nhong/Documents/my_dsa administrator@x.x.x.x"
```

---

### Post by nhong on 2010-06-24
I did what you say but it just show up a terminal only, ignoring the ssh command, please help.

Actually I want the command it self runs in the background without noticing it, Ive done this well by editing the /etc/rc.local (put the command before line "exit 0") but it's only for system start up not for login.

---

### Post by 3Miro on 2010-06-24
> **nhong said:**
> I did what you say but it just show up a terminal only, ignoring the ssh command, please help.

Actually I want the command it self runs in the background without noticing it, Ive done this well by editing the /etc/rc.local (put the command before line "exit 0") but it's only for system start up not for login.

I was testing this for xfce terminal, for gnome-terminal you have to use 
```
 gnome-terminal --command="ssh -p 443 -D 9999 -i /home/nhong/Documents/my_dsa administrator@x.x.x.x" 
```

I am not sure what you mean by "it self runs in the background without noticing it". What good is an ssh connection if you cannot use it (i.e. type commands in some sort of a terminal).

---

### Post by nhong on 2010-06-30
Thanks for your help, I've been in a trip for some days...

I mean I want it run as a service (there still a connection but not show up the terminal windows) Can I do that?

---

### Post by computermacgyver on 2010-06-30
Hi Nhong,

I do the same thing. Add the -N and -f switches to the command to tell ssh it will not need to accept commands and should go to the background. 

```

ssh -N -f -p 443 -D 9999 -i /home/nhong/Documents/my_dsa administrator@x.x.x.x

```

If you add this to the System->Preferences->Start up applications it should do what you want.

---

### Post by computermacgyver on 2010-06-30
> **3Miro said:**
> 
I am not sure what you mean by "it self runs in the background without noticing it". What good is an ssh connection if you cannot use it (i.e. type commands in some sort of a terminal).

He is using ssh only to forward ports (in this case basically acting as a proxy server). As such, he does not want an interactive prompt to type with, but only a background process.

---

### Post by nhong on 2010-07-02
> **3Miro said:**
> I was testing this for xfce terminal, for gnome-terminal you have to use 
```
 gnome-terminal --command="ssh -p 443 -D 9999 -i /home/nhong/Documents/my_dsa administrator@x.x.x.x" 
```

> **computermacgyver said:**
> Hi Nhong,

I do the same thing. Add the -N and -f switches to the command to tell ssh it will not need to accept commands and should go to the background. 

```

ssh -N -f -p 443 -D 9999 -i /home/nhong/Documents/my_dsa administrator@x.x.x.x

```

If you add this to the System->Preferences->Start up applications it should do what you want.



wow, it works like a charm! you're fantastic, I'm truly grateful. Thank you thank you , the command should be
```

 gnome-terminal --command="ssh -N -f -p 443 -D 9999 -i /home/nhong/Documents/my_dsa administrator@x.x.x.x"
```

---

