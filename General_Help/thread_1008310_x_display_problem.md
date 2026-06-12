---
title: "x display problem"
date: 2008-12-11
forum: General Help
---

### Post by davidbd on 2008-12-11
Hi,
I installed wubi with xubuntu and it works fine.
When i connect to another server and set the display to my IP display seen.

I run the command : xhost +

But still get and error:

xterm Xt error: Can't open display: 192.168.1.86

I try to connect via vnc and display is OK.

Can someone help me please ?

---

### Post by albinootje on 2008-12-11
> I installed wubi with xubuntu and it works fine.
> When i connect to another server and set the display to my IP display
> seen.
>
> I run the command : xhost +
>
> But still get and error:
> xterm Xt error: Can't open display: 192.168.1.86
> I try to connect via vnc and display is OK.

Please tell us which program you use to "connect to another server".

For example with "ssh -X some-other-server" you don't need to set a DISPLAY variable or to use xhost.

Disclaimer:
Using xhost + is a potential dangerous thing to do.

---

### Post by davidbd on 2008-12-12
i used both "ssh -X" rlogin/telnet with "setenv DISPLAY my_ip " 
both failed to opne the display.
Display works with VNC

---

### Post by davidbd on 2008-12-13
Can someone help please - I can not work with this problem !

---

