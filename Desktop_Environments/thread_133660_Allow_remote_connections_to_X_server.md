---
title: "Allow remote connections to X server"
date: 2006-02-20
forum: Desktop Environments
---

### Post by joaocosta on 2006-02-20
Can anyone give some tips as to how can I allow other machines to connect to my X-Server ?

I have some applications that I need to run at a remote host. I ssh to the remote host, and did:

export DISPLAY=my.ubuntu.host:0.0


then, I ran the following at my ubuntu machine:

xhost +remote.machine

But when I try to run remote applications it says it can't connect to my X-server.

I tried running netstat on my own machine, and indeed it is not listening on port 6000.

How can I configure Ubuntu so that the remote machine can connect to my X-Server ?

TIA

---

### Post by joaocosta on 2006-02-20
I need to allow a remote host to connect to my local X-server in Ubuntu.
I ssh to the remote host and ran the command:

export DISPLAY=my.ubuntu.host:0.0


At my local machine I ran:
xhost +remote.host


Now when I try to execute something on the remote host, it gives me back the message:

"kedit: cannot connect to X server my.ubuntu.host:0.0"


In my ubuntu host, I used netstat to see what ports were opened, and indeed, port 6000 is not running.

Can anyone help me on how to configure my machine to accept remote X server connections ?

TIA

---

