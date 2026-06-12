---
title: "SSH question"
date: 2008-12-02
forum: General Help
---

### Post by redonwhite on 2008-12-02
Hello.  I was able to successfully connected my two home computers using SSH.  But every time i try to connect to my SSH server from outside of my home network it says No host found.  Any ideas what I'm doing wrong?  Also do I need to do anything else in regards to security if I'm using SSH to connect to my server at home from other devices?  Thank you!

---

### Post by Waappu on 2008-12-02
Hi

Is SSH port fowarder from your local network to internet ?

---

### Post by redonwhite on 2008-12-02
I apologize, I'm very new at this =/.  How would i find out if my ssh port is forwarded to the internet?

---

### Post by Waappu on 2008-12-02
Hi

Check your adsl box/router manual how foward port.
If ssh working in your local network, problem must be in that port is not open to internet.

---

### Post by adult swim on 2008-12-02
youll need to forward port 22 (assuming you havent changed the default) on your router to the local ip address of the box you are trying to connect to.

---

### Post by lovinglinux on 2008-12-02
> **redonwhite said:**
> Also do I need to do anything else in regards to security of I'm using SSH to connect to my server at home from other devices?  Thank you!

You should use encryption keys instead of passwords to authenticate the client machine, setup /etc/ssh/sshd_config in onder to NOT allow root ssh access, neither password authentication.

Take a look at [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

You can find how to setup your keys there too.

---

### Post by redonwhite on 2008-12-02
> **adult swim said:**
> youll need to forward port 22 (assuming you havent changed the default) on your router to the local ip address of the box you are trying to connect to.

cant seem to access router for port forwarding.  Linksys router.  Followed directions on one site.  But when i put IP in browser 404 error came up.

---

### Post by redonwhite on 2008-12-02
> **lovinglinux said:**
> You should use encryption keys instead of passwords to authenticate the client machine, setup /etc/ssh/sshd_config in onder to NOT allow root ssh access, neither password authentication.

Take a look at [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

You can find how to setup your keys there too.

Thank you i will look more into this.

---

### Post by spiderbatdad on 2008-12-02
> **redonwhite said:**
> cant seem to access router for port forwarding.  Linksys router.  Followed directions on one site.  But when i put IP in browser 404 error came up.

try clearing your browser cache. double check correct ip...```
netstat -r
```look where default and gateway intersect...

---

### Post by adult swim on 2008-12-02
are you putting in 192.168.1.1 ?

---

### Post by lovinglinux on 2008-12-02
> **redonwhite said:**
> cant seem to access router for port forwarding.  Linksys router.  Followed directions on one site.  But when i put IP in browser 404 error came up.

Are you the network administrator? Did you ever accessed the router administration pages?

Your router address is probably 192.168.2.1, so type [http://192.168.2.1/Forward.htm](http://192.168.2.1/Forward.htm) to access the forwarding page. If that doesn't work, try [http://192.168.1.1/Forward.htm](http://192.168.1.1/Forward.htm) 

There is a command to get the router IP, but I don't remember it.

---

### Post by redonwhite on 2008-12-02
> **adult swim said:**
> are you putting in 192.168.1.1 ?

I tried my static IP address the directions told me to set up.  But ive reversed that and put in 192.168.1.1 in the browser.  A log in screen poped up for my Router.  I left user name blank and entered ADMIN for the password as instructed.  But it did not work.  It is possible that this router has had a password set up years ago on it.  Is there anyway to hack or reset that?

---

### Post by adult swim on 2008-12-02
there should be a reset button on the back of the router that will reset everything so youll have to set up your wireless encryption again.  did you try ADMIN or admin? i think lowercase admin is the default with a blank username

---

### Post by redonwhite on 2008-12-02
> **lovinglinux said:**
> Are you the network administrator? Did you ever accessed the router administration pages?

Your router address is probably 192.168.2.1, so type [http://192.168.2.1/Forward.htm](http://192.168.2.1/Forward.htm) to access the forwarding page. If that doesn't work, try [http://192.168.1.1/Forward.htm](http://192.168.1.1/Forward.htm) 

There is a command to get the router IP, but I don't remember it.

I am the network Admin.  But my father and I shared this router years ago and it is possible he had accessed the admin pages and set up a name/pass. =//.

---

### Post by spiderbatdad on 2008-12-02
admin
admin

or see here:[http://www.phenoelit-us.org/dpl/dpl.html](http://www.phenoelit-us.org/dpl/dpl.html)

if you suspect a password, push a pin into the reset button hole in the back for several seconds.

---

### Post by redonwhite on 2008-12-02
> **adult swim said:**
> there should be a reset button on the back of the router that will reset everything so youll have to set up your wireless encryption again.  did you try ADMIN or admin? i think lowercase admin is the default with a blank username

Haven't gone wireless yet =) Too paranoid hehe.  I tried lowercase admin.  I will reset it like you said.  Thanks for the tip i had no idea i could do that.  I have to take a shower and hang out with the girlfriend now though.  I will test this out further tonight and update this thread.  THANK YOU ALL SO FAR FOR YOUR HELP.

---

