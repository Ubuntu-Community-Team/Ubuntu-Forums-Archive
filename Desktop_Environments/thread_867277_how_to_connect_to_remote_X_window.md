---
title: "how to connect to remote X window"
date: 2008-07-22
forum: Desktop Environments
---

### Post by b4nsh33 on 2008-07-22
Hi, i have a server running X windows (mwm as windows manager) , how can i connect from my ubuntu desktop?
Note: In windows i use Reflexion X

---

### Post by ProbablyX on 2008-07-22
open up a terminal and run
```

ssh -X *username*@*server address* *program to run*

```

---

### Post by b4nsh33 on 2008-07-23
ok, in Reflexion X i run this command:

(/usr/bin/X11/mwm -display %IP#% &)


running 
ssh -X usera@172.16.10.5 /usr/bin/X11/mwm  got this error:

mwm: Another window manager is running on screen 0
mwm: Unable to manage any screens on display.

i think im missing the -display parameter, but i dont have a clue about what should be it, any hint?

---

### Post by cube3x3 on 2008-07-23
> **b4nsh33 said:**
> ok, in Reflexion X i run this command:

(/usr/bin/X11/mwm -display %IP#% &)


running 
ssh -X usera@172.16.10.5 /usr/bin/X11/mwm  got this error:

mwm: Another window manager is running on screen 0
mwm: Unable to manage any screens on display.

i think im missing the -display parameter, but i dont have a clue about what should be it, any hint?

Well you shouldn't run mwm again as you already started it in Reflexion X as your window manager. So don't run the 'mwm' again and run any other program that you want. For example if you want to run gnome-calculator run this:

ssh -Y usera@172.16.10.5 gcalctool 

I prefer -Y as its more secure than -X.
From ssh manual page:
>      -X      Enables X11 forwarding.  This can also be specified on a per-host
             basis in a configuration file.

             X11 forwarding should be enabled with caution.  Users with the
             ability to bypass file permissions on the remote host (for the
             user’s X authorization database) can access the local X11 display
             through the forwarded connection.  An attacker may then be able
             to perform activities such as keystroke monitoring.

             For this reason, X11 forwarding is subjected to X11 SECURITY
             extension restrictions by default.  Please refer to the ssh -Y
             option and the ForwardX11Trusted directive in ssh_config(5) for
             more information.

     -Y      Enables trusted X11 forwarding.  Trusted X11 forwardings are not
             subjected to the X11 SECURITY extension controls.

---

### Post by warp99 on 2008-07-23
You can use ssh then forward the port and run a vnc server on the host machine if you have a slow connection since vnc is not as bandwidth intensive as X forwarding. More information on this here under "Trick 6: Remote VNC session through an SSH tunnel":

[http://www.ibm.com/developerworks/linux/library/l-10sysadtips/index.html?ca=drs-](http://www.ibm.com/developerworks/linux/library/l-10sysadtips/index.html?ca=drs-)

---

### Post by b4nsh33 on 2008-07-24
I think i didnt explain very well my problem:

i have a suse server running mwm  as window manager, i used to connect to that server using reflexion x for windows using (/usr/bin/X11/mwm -display %IP#% &) as command, that opened a gui aplication, the same as if i log in in the suse console.
Now im trying to connect using ubuntu 8.04, following your advise im able to connect and run xclock or xterm using this command:

ssh -Y acc4000d@172.16.10.5 xclock (or xterm)

it opens in my ubuntu's gnome desktop the xclock or xterm window.
But if i run:

 ssh -Y acc4000d@172.16.10.5 /usr/bin/X11/mwm -display 172.16.10.254:0

where 172.16.10.254 is my ubuntu's ip, it does nothing...

---

### Post by cube3x3 on 2008-07-24
> **b4nsh33 said:**
> 
it opens in my ubuntu's gnome desktop the xclock or xterm window.
But if i run:

 ssh -Y acc4000d@172.16.10.5 /usr/bin/X11/mwm -display 172.16.10.254:0

where 172.16.10.254 is my ubuntu's ip, it does nothing...

Well as far I am sure that this will not work because in Ubuntu, on your local X server display :0, you are already running some window manager and it will not allow you to run another window manager.

Try to run the above command with X server without running any window manager like 'gdm' or 'kdm' and let me know how that goes.

---

