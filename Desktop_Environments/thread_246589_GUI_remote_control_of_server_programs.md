---
title: "GUI remote control of server programs"
date: 2006-08-29
forum: Desktop Environments
---

### Post by grough on 2006-08-29
Hi,

I want to run programs on my Ubuntu headless server, but display those program's GUIs on my Ubuntu laptop.

I understand there are a couple of ways to do this, but I'm not sure which tools/configuration is required for each. Here is my understanding of the different methods:

1) The GUI is rendered on the server and the graphics are sent to the "interactive" machine (in this case, my laptop), and only mouse and keyboard events are sent back to the server.

OR

2) The guts of a program run on the headless server, and the GUI is rendered using the laptop's graphics toolkit which is updated by the server program remotely (sending messages, not graphics).

I would like to use the second method, because I'd prefer not to install a graphics toolkit on my headless server. So far I understand that the 2nd method can be done using X11 forwarding over ssh, but am not clear on the exact configuration.

I've tried running...

ssh -X user@myserver /usr/bin/nicotine

But I get the same error message as when I try to run this program on the server regularly, with no forwarding &#8230; RuntimeError: could not open display

Does anybody know what kind of configuration is needed on each machine to do what I'm describing?

Thanks

---

### Post by kwalo on 2006-08-29
To enable X11 forwarding via ssh, edit **/etc/ssh/sshd_config** and change the following entries:
```
UseLogin [color="Red"]no[/color]
X11Forwarding [color="Red"]yes[/color]
```Restart the ssh daemon with ```
$ sudo /etc/init.d/ssh restart
```And you should have X11 forwarding enabled. Of course your server machine should have X.org, or Xgl running.

I don't think the second option is possible. You cannot distingush, when program does it's drawing part and when it does it's 'main job'. That's all stored in a single executable and shared libs.

---

### Post by apolyak on 2006-08-29
Take a look at very clear explained "Running applications remotely with X11"

[http://tldp.org/linuxfocus/English/January2002/article222.shtml](http://tldp.org/linuxfocus/English/January2002/article222.shtml)

Just in case. host names used in that article, movietux and philosophus, were defined to replace addresses written in form as 192.168.0.1. You can define ip-hostname pairs by editing file /etc/hosts or using menu System-Administration-Networking-Hosts. You can use also files /etc/hosts.allow and /etc/hosts.deny.

To allow recieving of forwarded X (using menu): System-Login_Window-Security and uncheck Deny TCP connections to Xserver.

---

### Post by oliverb on 2006-08-30
Thanks for the pointer, I was going to ask pretty much the same question as grough.

I'm not sure if I understand the answer yet.

---

### Post by apolyak on 2006-08-30
on local PC to allow recieving of forwarded X (using menu): System-Login_Window-Security and uncheck Deny TCP connections to Xserver.

on local PC: xhost +
(it is more secure to use: xhost + xxx.xxx.xxx.xxx_of_remote_PC)

ssh -X user_name@host_name_remote_PC

on remote PC: export DISPLAY=xxx.xxx.xxx.xxx:0.0 (where xxx.xxx.xxx.xxx is for local PC)

on remote PC: application_to_run &

assuming firewall is off or ssh port is open.

hope this helps

---

### Post by grough on 2006-08-31
Thanks for your help, everybody.

"If you use ssh to login to the remote host then the DISPLAY is automatically set correctly." (from link posted by apolyak - [http://tldp.org/linuxfocus/English/January2002/article222.shtml](http://tldp.org/linuxfocus/English/January2002/article222.shtml))

I'm using ssh, but still have to reset DISPLAY for each new session. Anybody seen this before?

A couple other questions:

What happens to the DISPLAY variable if multiple machines try to run X programs on one host at the same time? For example, in a situation where you have multiple thin clients running off a headless central host (like a library or school), or even just 2 or 3 machines on a home network. Is DISPLAY capable of storing more than one address?

Is there a way to configure the list of allowed xhosts by hand, without using the "xhost + &#8230;" command? I don't see a man or help entry for xhost, so I'm a little mystified about how to do other things with it.

---

### Post by grough on 2006-08-31
Thanks for your help, everybody.

"If you use ssh to login to the remote host then the DISPLAY is automatically set correctly." (from link posted by apolyak - [http://tldp.org/linuxfocus/English/January2002/article222.shtml](http://tldp.org/linuxfocus/English/January2002/article222.shtml))

I'm using ssh, but still have to reset DISPLAY for each new session. Anybody seen this before?

A couple other questions:

What happens to the DISPLAY variable if multiple machines try to run X programs on one host at the same time? For example, in a situation where you have multiple thin clients running off a headless central host (like a library or school), or even just 2 or 3 machines on a home network. Is DISPLAY capable of storing more than one address?

Is there a way to configure the list of allowed xhosts by hand, without using the "xhost + …" command? I don't see a man or help entry for xhost, so I'm a little mystified about how to do other things with it.

---

