---
title: "vinagre remote dekstop connection"
date: 2011-03-16
forum: Desktop Environments
---

### Post by slwx on 2011-03-16
Hi,
im trying to connect to a remote device, which I can't acces physically atm. 
So I'm trying to do this with vinagre, but I get an error:Connection to host IP was closed.

so normally i should go to system > preferences > remote desktop acces, on the remote device
and allow connections. 
But how do i do this remotly? I can only acces to the device through ssh!

Any ideas?

Thanks, 
Mathias

---

### Post by robertmf on 2011-10-09
> **slwx said:**
> Hi,
im trying to connect to a remote device, which I can't acces physically atm. 
So I'm trying to do this with vinagre, but I get an error:Connection to host IP was closed.

so normally i should go to system > preferences > remote desktop acces, on the remote device
and allow connections. 
But how do i do this remotly? I can only acces to the device through ssh!

Any ideas?

Thanks, 
Mathias
[COLOR="DarkRed"]
:confused:  [BUMP] Same connection to host problemo on a .local network of two boxes.   Seems that after some @@ 3 days, the connection closes of its own will :lolflag: :o  The ssh connection closes also ... then, after a rest, vinagre will allow a re-connection.  :)

Ideas ?  Suggestions ?  Clues ?
[/COLOR]

---

### Post by vajorie on 2011-10-10
Have a look at this: [http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981)

I never tried running it from ssh but give x11vnc a try, it might turn out to be easier? 

```

/usr/bin/x11vnc -display :0 -forever -shared -usepw -rfbport 5900 & 
netstat -nltp | grep 5900 &   # to check if all is well
```

The password is in ~/.vnc/passwd
You create that file using this command (after which x11vnc exists)

```

x11vnc -storepasswd somepassword ~/.vnc/passwd

```

Edit: This would be more secure, as vnc is not encrypted: [http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html](http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html) / [http://www.cyberciti.biz/faq/linux-unix-tunneling-xwindows-securely-over-ssh/](http://www.cyberciti.biz/faq/linux-unix-tunneling-xwindows-securely-over-ssh/)

---

### Post by robertmf on 2011-11-10
> **robertmf said:**
> [COLOR="DarkRed"]
:confused:  [BUMP] Same connection to host problemo on a .local network of two boxes.   Seems that after some @@ 3 days, the connection closes of its own will :lolflag: :o  The ssh connection closes also ... then, after a rest, vinagre will allow a re-connection.  :)

Ideas ?  Suggestions ?  Clues ?
[/COLOR]

[COLOR="DarkRed"]
I'm now using vino server on the remote and xtightvncviewer.

[/COLOR]

---

