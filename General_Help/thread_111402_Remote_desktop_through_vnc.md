---
title: "Remote desktop through vnc"
date: 2006-01-02
forum: General Help
---

### Post by gslater on 2006-01-02
Hi

I have set up my computer to run remote desktop (despite the warnings about security).  I am now able to view my Ubuntu pc from my windows pc over my LAN.

My next trick is to do it from a remote computer over the internet.  When I set up vnc on my windows computer I had to open ports 5900 and 5800 and then when I accessed over the internet I just had to know my IP address from my providor....lets say it was 186.74,89.2.....in which case I could access remotely by putting in 186.74,89.2:5900 into the browser and I would be up and running.

How do I set my Ubuntu pc to access over a specified port number...since I have multiple pc's on my network I need to be able to specify the ports....the remote desktop application doesn't seem to allow this (from the front end that is....I know I should be able to do this from the terminal somehow).

---

### Post by gslater on 2006-01-02
ok....done a bit more reading up on the topic.....the man pages seem to suggest that vnc runs as standard on port 5500.

Is this correct for all linux installations versus ports 5800 and 5900 on windows installations?

---

### Post by DaMasta on 2006-01-02
I set my password through gnome's vino setting's. Then I run vncserver -geometry 1024x768 -depth 16 :1. This needs port 5901 to be open in the firewall. This works for me.

---

