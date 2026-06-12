---
title: "Project SSHed Firewall TCPDump info securely"
date: 2008-12-04
forum: General Help
---

### Post by hansoffate on 2008-12-04
I'm not sure which subforum to post this, so I decided to post in General Help. 

I have setup an Ubuntu Server 8.10 with "ubuntu-desktop" and ClamAV so that when Window users bring potentially virus infected drives, we can get rid of them before plugging it into one of our domain windows computers.  

Since we have it sitting here doing nothing, the network admin would like it to be set so that we can SSH into our OpenBSD firewall and display the TCPDump info live, projected on his wall.  Obviously, this poses security risks to be logged in and SSHed to our firewall.  Anyone can walk in, CTRL+C and end the TCPDump session and have full access to our firewall.  We want to lock this down.

Is there a way to have the SSH session disconnect if the TCPDump session is ended?  Can you think of any other alternatives?

Please post even if you think it's not possible.

Thanks for the help,
Hans

---

