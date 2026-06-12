---
title: "&quot;No response from server, restarting...&quot; Error from LTSP Client"
date: 2009-04-30
forum: General Help
---

### Post by gamewolf on 2009-04-30
I have setup an LTSP Server from the 9.04 alternate CD. I boot a client from the network and it boots fine. I come to the gdm login screen and login with a user account, but it hangs with "Verifying password" for about 30 seconds, then goes to a "No response from server, restarting..." error. It restarts gdm and then brings the login screen back.

I am not sure what to do to fix it. Any suggestions? Thanks.

---

### Post by gamewolf on 2009-04-30
bump

---

### Post by gamewolf on 2009-04-30
bump again.

---

### Post by gamewolf on 2009-04-30
Nobody has an idea?

---

### Post by elebrin on 2009-05-05
I am having the same problem, I hope you get a response...  even if it is just a pointer to some docs.

---

### Post by Scormen on 2009-05-06
Same problem here...

Ubuntu 9.04 64bit.

Just a question, is there any good tutorial for ltsp?

Thanks.

---

### Post by Scormen on 2009-05-06
I found it.

On the server, do in this order:
sudo ltsp-update-sshkeys
sudo ltsp-update-image

After that, restart your client.

---

### Post by gamewolf on 2009-05-17
awesome! It works! Thanks so much.

---

### Post by encurto on 2009-10-21
> **Scormen said:**
> I found it.

On the server, do in this order:
sudo ltsp-update-sshkeys
sudo ltsp-update-image

After that, restart your client.



YEEEEEEEEES! I don't know why but it works!!!

Thank you so much!

---

### Post by CADutch on 2009-11-14
Hmmmm.. still not working... Did you CHROOT into /opt/ltsp/... before you typed this command ?

---

### Post by parksje on 2009-12-15
Howdy.  I don't know if this is what's happening to you, but I had to enable PasswordAuthentication in /etc/ssh/sshd_config and restart the ssh service.  

If anyone knows how to make LTSP work with ssh keys instead of relying on password auth, I'd be very interested.

JP

---

### Post by meadmarc on 2010-08-19
I nearly had heart failure after I brought down my daughter's school.  No login could occur on any client.

I was working on several things at once, so I had to backtrack.

I had just installed ssh to allow me to remote in to the server from home, and had set the default port to something new to discourage port scanners from finding and hacking the system.

Switched back to 22, re-did the keys and image, and we are now back.  And I have more grey hair.

Now that I know, is there a way to change the ssh port number on LTSP?  I would like to remote in, but keeping 22 open is just not healthy, even with a strong password.

---

### Post by meadmarc on 2010-08-19
ha ha, found this here:  [https://wiki.ubuntu.com/DedicatedLTSPSSH](https://wiki.ubuntu.com/DedicatedLTSPSSH)

Looks like I am not the first, but has any progress been made?

---

### Post by meadmarc on 2010-08-30
I solved this problem by putting a second port number in the ssh conf file.

So now it is open for both LTSP on port 22, and on my "alternative" port.  My router forwards ssh from that alternative port to the server on the alternative port.

So you can list two ports for ssh in the conf file, one on the first line, and the second is identical with another port number.

Hopefully this will help others with the same problem.

Now I can SSH in from home, and use LTSP, while only exposing the secret alternative port to the outside world.

---

### Post by mightyiam on 2012-08-28
I had this issue and as I found out it was caused by DenyHosts adding a specific IP address to /etc/hosts.deny which prevents further login attempts from that IP address. This was caused obviously by a user failing to log in five times (5 is the default). So I manually removed the IP address from /etc/hosts.deny and changed the number of failed attempts to 7 and warned the users.

---

