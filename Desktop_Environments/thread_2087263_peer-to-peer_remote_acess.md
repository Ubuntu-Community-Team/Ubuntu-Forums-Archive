---
title: "peer-to-peer remote acess"
date: 2012-11-23
forum: Desktop Environments
---

### Post by leandromartinez98 on 2012-11-23
Sometimes I need to help my mom to solve some problems in her computer, and being able to access her desktop (or even her shell) remotely would be of great help. However, she is in a dynamic-ip commercial network, so that her computer does not have a real IP which I can set as a server on RemoteDesktop applications, at least the way I understand them.

Is there any way for me to access her desktop or shell remotely using some kind of peer-to-peer connection?

Thank you,
Leandro.

---

### Post by SlugSlug on 2012-11-23
I used dyndns for this but I think there free option has stopped.

Look into no-ip or similar. There are clients for ubuntu to auto update or some routers support updating too

---

### Post by leandromartinez98 on 2012-11-23
I found this option:

First, my mom must log into my machine (which fortunately has a real ip, and can be accessed by ssh):

ssh [email]momatserver@server.work.com[/email] -R 1100:localhost:22

That stablishes a reverse ssh connection which will be available at the port 1100 of my machine.

Then, here (at server.work.com), I do:

ssh momatserver@localhost -p 1100

And it will connect to a shell on my mom's computer. I tried this with two machines here at work, and it seems to be working. If I can do that with my mom's computer, than the problem will be solved for me (or part of it, because it does not solve the problem if neither of the computers have a real IP).

The detailed data, and other options, were at this site:

[http://www.debianadmin.com/howto-use-ssh-local-and-remote-port-forwarding.html](http://www.debianadmin.com/howto-use-ssh-local-and-remote-port-forwarding.html)

---

### Post by Lars Noodén on 2012-11-23
It should work from your mom's computer.  It's just that she will have to make that connection from her machine to the outside server any time you need to log in.  Your ability to connect is contingent on her having the reverse tunnel set up.

---

### Post by leandromartinez98 on 2012-11-23
> **Lars Noodén said:**
> It should work from your mom's computer.  It's just that she will have to make that connection from her machine to the outside server any time you need to log in.  Your ability to connect is contingent on her having the reverse tunnel set up.

Sure. Fortunarely she is not that afraid of using the command line. Still, a more direct option for remote support would be of great value, I think, this is something windows has for a long time, through MSN (I never used, but friends told me that that exists).

---

### Post by SlugSlug on 2012-11-23
If she's able to use the PC when she needs support then maybe teamviewer is what your looking for?

---

### Post by sammiev on 2012-11-23
> **SlugSlug said:**
> If she's able to use the PC when she needs support then maybe teamviewer is what your looking for?

I agree, I used [teamviewer]("http://www.teamviewer.com/en/index.aspx") a few times now and it work great.

---

### Post by leandromartinez98 on 2012-11-23
Yes, teamviewer should do the trick, apparently. I couldn't manage her to install it, but the next time I go there I will do it and probably that will solve it all (I couldn't either manage her to use that ssh trick...)

---

### Post by Lars Noodén on 2012-11-23
You could probably set up an icon to create the reverse tunnel back to your external machine.  Then all she would need to do is click on it and enter the password.  If you use passwordless keys then she can skip even the password.  Though if you do that, you should set *command=* in the authorized_keys file to something innocuous like "/bin/sleep 86400".

---

