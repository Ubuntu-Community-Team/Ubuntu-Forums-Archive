---
title: "Connect to remote desktop via SSH- connection refused no matter what"
date: 2012-09-09
forum: Desktop Environments
---

### Post by varelov on 2012-09-09
Hi, As a part of a kinda larger project (trying to take my Ubuntu 11.04 desktop headless and control it only via secure VNC), I am trying to set up a SSH connection between my Ubuntu 11.04 virtual machine and two Ubuntu desktop machines (one running 10.04 the other 11.04). The idea behind this is to try to use SSH as means to connect to those two machines from my virtual machine without those two machines needing to be connected to a screen, mouse and keyboard (a.k.a headless), but also to practice some SSH. However, I am running into problems that I didn't expect I would ever encounter. Every attempt at a SSH connection got refused. I can ping the machine, it is visible on the network via my VM, I can see and drive its desktop via VNC so networking is obviously not an issue. Firewalls: firewall at the Ubuntu box is set to allow incoming and outgoing connections on port 22 and 5900 (why 5900, later). Firewall at Ubuntu VM is disabled. So is the Windows host's firewall. Still, no go. OpenSSH servers: installed at both machines, up and running. ssh_config and sshd_config files: the X11 forwarding option is set to Yes. Why 5900? As per instructions in "Ubuntu 11.04 Essentials" available at Techotopia as a wiki, after running: ```
ssh -L 5900:localhost:5900 remote_host
``` and replacing remote_host with remote host's IP address, it should be possible to get a secure VNC on remote host's desktop. I saw a topic on headless desktop hosts already exists and suggested solution doesn't work for me (missing file /etc/default/grub in all of my Ubuntu installs), but even SSH is a no-go and I would really like to see this work.
What else is there to be done to make SSH work?

---

### Post by markbl on 2012-09-09
Forget about the port forwarding until you get the basic ssh connection to work. Two places to see debug why this is not working. 1) Add "-vvv" to your ssh client options; and 2) look in /var/log/* for sshd messages.

A very common problem people have here is they have the wrong permissions on their home dir. Your ~ dir (e.g. /home/varelov) MUST have permissions 755 (i.e. not 775), and your ~/.ssh dir MUST have permissions 700.

BTW, you don't need to open incoming port 5900 on your server. The point of tunnelling VNC over ssh is that it gets encrypted within the port 22 traffic. Yes, the sshd server will forward the VNC traffic locally back to port 5900 on your box but that connection is via the local interface.

---

### Post by varelov on 2012-09-10
Thank you for trying to help me markbl, maybe it was your suggestion that in part solved the problem.
Sshd was listening to port 2222, and all my requests were by default sent to port 22. Further, I didn't precisely directed my request by username (like some_user@some_address) and was at times using username of a currently logged in user of the remote machine.
So I edited the sshd config file to listen to port 22, directed the request with a username of a user not currently logged in at the remote machine and after presenting correct credentials, I got in.
Great! On to the next step of enabling X11 tunneling on my local network.

---

