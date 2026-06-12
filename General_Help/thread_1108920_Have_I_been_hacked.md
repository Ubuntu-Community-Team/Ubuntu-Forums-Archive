---
title: "Have I been hacked?"
date: 2009-03-28
forum: General Help
---

### Post by Washer on 2009-03-28
[img]http://img24.imageshack.us/img24/4035/screenshotojy.png[/img]

That's the login I use, but I didn't log out or make a new session or anything. What's happening?

Usually this happens while trying to restart after something randomly screws up with my wireless or compiz or something. I can never tell what. The system monitor doesn't help. It begins the restart process after I authenticate, but sometimes it locks up while restarting & I have to pull the plug.

---

### Post by cmay on 2009-03-28
this does look very strange. how often does it happen. 
you can try run command in terminal  lastb or when it happens try run who and whoami to see if there really is others logged in but you or if you are not logged in as who you think you are by that  i mean with sudo or not sudo powers granted when it happens.

sorry i can not help you anymore than this  but i hope others can.

---

### Post by blackgr on 2009-03-28
> **Washer said:**
> [img]http://img24.imageshack.us/img24/4035/screenshotojy.png[/img]

That's the login I use, but I didn't log out or make a new session or anything. What's happening?

Usually this happens while trying to restart after something randomly screws up with my wireless or compiz or something. I can never tell what. The system monitor doesn't help. It begins the restart process after I authenticate, but sometimes it locks up while restarting & I have to pull the plug.

Type in a terminal:
```
w
```
and see all users logged in to your system

---

### Post by Washer on 2009-03-28
If it is a user, wouldn't he show up in the system->admin->users/groups section?

If it is a user & he's good enough to avoid that, would he show up with the terminal?

W/e thanks anyway, I'll try it next time. It doesn't happen very often, like once a week or two weeks. I should just reformat, but I'm waiting for the next release.

---

### Post by dcstar on 2009-03-28
> **Washer said:**
> 

**Usually this happens while trying to restart after something randomly screws up with my wireless or compiz or something. I can never tell what. **The system monitor doesn't help. It begins the restart process after I authenticate, but sometimes it locks up while restarting & I have to pull the plug.

You have a system where something is obviously crashing and corrupting the system.

There is no "hacking" problem, it is a broken system problem.

---

### Post by Washer on 2009-03-29
Any idea how to track down the problem then?

---

### Post by HermanAB on 2009-03-29
Look at /var/log/messages.  There may be some clue in there:
$ sudo tail -n 10000 /var/log/messages | less

You may also want to invest in a UPS, since these weird problems are frequently due to bad power quality.

---

