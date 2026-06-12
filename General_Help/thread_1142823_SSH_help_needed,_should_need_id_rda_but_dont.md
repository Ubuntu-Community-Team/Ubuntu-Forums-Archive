---
title: "SSH help needed, should need id_rda but dont"
date: 2009-04-29
forum: General Help
---

### Post by Gondee on 2009-04-29
i created a ssh server, and i set it up so that you just need the id_rda file on your system to connect. But when i attempt to connect without the id_rda on the remote computer, it simply asks for the password of the server and allows me to logon. All the Guides and things i have looked at say this souldnt happen. So how do i make it where i just need the id_rda file and if the computer dosnt have it, it refuses connection...??

side question, the instalation created 2 of the id_rda files, one with no extension, and one with pub as the extension, which is the working copy?

---

### Post by Chris Musampa on 2009-04-29
From: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

To disable password authentication, open /etc/ssh/sshd_config and look for the following line: 

PasswordAuthentication yes

Change it to the following (or add it if you couldn't find that line): 

PasswordAuthentication no

---

