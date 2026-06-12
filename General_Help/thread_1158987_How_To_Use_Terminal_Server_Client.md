---
title: "How To Use Terminal Server Client"
date: 2009-05-14
forum: General Help
---

### Post by s1mp13m4n on 2009-05-14
Hello everyone.  I was told in another post that TSC will do what I am trying to do, however I have not figured it out so I need more help.  I am trying to "control" two WinXP Pro boxes from my Ubuntu Linux laptop.  I want to be able to log onto them remotely and perform normal maintenance on them from my Linux desktop.  All the computers are connected to a wired Linksys router and are all in the same house and have a 192.168.1.xxx ip address.  How do I use Terminal Server Client to do this?  Is there another choice, a better way?  Thank you for the help.

---

### Post by metcarob on 2009-05-14
I use VNC.
You can get a program called WinVNC (which is free) on the windows machines and install it. Ubuntu romote client actually uses VNC so you can simply point it at the window's machines IP address and see the windows desktop on your ubuntu machines.
There are other programs I think, TinyVNC, RealVNC.
Hope that helps

---

### Post by KhurramM on 2009-05-14
Goto


[http://www.zolved.com/synapse/view_content/28113/How_to_connect_to_a_Windows_terminal_from_Ubuntu](http://www.zolved.com/synapse/view_content/28113/How_to_connect_to_a_Windows_terminal_from_Ubuntu)

But try searching via google before posting

Some issues get solved in one click

---

### Post by s1mp13m4n on 2009-05-14
Thank you all for the help.  I was able to take TSC and log in to the WinXP machine and see the desktop.  In the area of the TSC windows where the line for "Computer" is I placed the IP address of the machine I want to log in to and that was it.  It really was simple. Thank you for the help.

---

