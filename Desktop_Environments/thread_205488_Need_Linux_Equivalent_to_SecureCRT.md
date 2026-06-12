---
title: "Need Linux Equivalent to SecureCRT"
date: 2006-06-28
forum: Desktop Environments
---

### Post by fizz on 2006-06-28
Just switched my office desktop to Ubuntu Dapper today, and forgot to get something to manage my telnet/ssh connections. Im in need of something that can do categories such as follows:

```

Servers->
     Server 1
     Server 2
     Server 3
Switches->
     Switch 1
     Switch 2
Ect...

```

Needs to be able to store passwords as well, I know I should be using Auth Keys, but many pieces of equipment I'll be connecting to, do not support that.

It would be insanely cool, if it could even read my old SecureCRT config :)

Thanks in Advance.

---

### Post by briguy on 2006-06-28
Both konqueror (fish) and nautilus will do ssh connections, you can bookmark them and store passwords in a wallet.  Not sure exactly what you're looking for...

---

### Post by fizz on 2006-06-28
Just need something to "bookmark" for telnet and ssh, ill check nautalus, didnt know it had that ability.  GRCM doesnt appear to do telnet, and gtelnet doesnt appear to exist anymore.

---

### Post by joakim2 on 2006-06-28
[QUOTE=fizz]Just need something to "bookmark" for telnet and ssh, ill check nautalus, didnt know it had that ability.  GRCM doesnt appear to do telnet, and gtelnet doesnt appear to exist anymore.[/QUOTE]

You could try any of these:

[http://people.defora.org/~khorben/projects/gputty/](http://people.defora.org/~khorben/projects/gputty/)
[http://www.oronetes.net/webs/gnome-sshman/download.html](http://www.oronetes.net/webs/gnome-sshman/download.html)
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) (there is a "unix" version available as source)

---

### Post by fizz on 2006-06-28
I tried putty, and gputty looks like a clone, but niether give the option of saving passwords. For example, in SecureCRT, you can set actions, so when it sees Login: it inserts your filled in value, and then more actions, such as word: being the end of password and have it insert that password. I have several hundred devices, and keeping ips, and passwords in a textfile is kinda well... not good heh.

It would also allow, me to login with admin, and then password, look # then send en to goto enable mode, and then recognize the next line and enter the enable password.

I appriciate all responses thus far.

Kelly

---

### Post by fizz on 2006-06-28
I guess a better way to present this would be to mention im looking for Login Script Abilities within one of these applications.. i feel stupid now as this probably makes more sense the the above ramblings by myself.

---

### Post by joakim2 on 2006-06-28
[QUOTE=fizz]I guess a better way to present this would be to mention im looking for Login Script Abilities within one of these applications.. i feel stupid now as this probably makes more sense the the above ramblings by myself.[/QUOTE]

It really sounds like it's time to start looking into using ssh keys... There's a ton of guides on how to set up your keys on the 'net, here are a couple:

[http://www.phy.bnl.gov/computing/gateway/ssh-agent.html](http://www.phy.bnl.gov/computing/gateway/ssh-agent.html)
[http://www-128.ibm.com/developerworks/library/l-keyc.html](http://www-128.ibm.com/developerworks/library/l-keyc.html)
[http://www-128.ibm.com/developerworks/library/l-keyc2/](http://www-128.ibm.com/developerworks/library/l-keyc2/)
[http://www-128.ibm.com/developerworks/linux/library/l-keyc3/](http://www-128.ibm.com/developerworks/linux/library/l-keyc3/)

---

### Post by fizz on 2006-06-30
I appriciate all the ideas and comments, however i have a ton of switches, dslams, atm devices, and other odd ball stuff that only uses telnet.

I think for the time being, ill just piece together a small php cli script to do what im needing, but was hoping to prevent re-inventing the wheel.

Thanks again..

---

### Post by tturrisi on 2006-06-30
fyi, gftp will do ssh and bookmark the connection data.  In windows I use WinSCP for secure transfers & server mgmt, gftp is similar.

---

