---
title: "SSH key problems - computer reinstallation"
date: 2009-04-17
forum: General Help
---

### Post by Nixie Pixel on 2009-04-17
Hi, I recently killed and reinstalled my server - moving from desktop Intrepid to Ubuntu server 8.10.  Unfortunately I had a public/private key set up on the ip address that I want to continue to use as the server, and of course running OpenSSH.  My machine tells me that the RSA signature has changed and won't authenticate.

So how can I connect to a new machine/OpenSSH server with the same hostname/ip address as the old server?

Thanks!

---

### Post by StuartN on 2009-04-17
You might be able to find and delete the key using Seahorse (Applications->Accessories->Passwords and Encryption Keys), so you should be prompted for the new key next time you try to connect.

---

### Post by Bachstelze on 2009-04-17
> **Nixie Pixel said:**
> 
So how can I connect to a new machine/OpenSSH server with the same hostname/ip address as the old server?

Delete the old key from [font="monospace"]~/.ssh/known_hosts[/font] (the error message should tell you on which line it is in the file). The correct key will be automatically added to it next time you connect to the server.

---

### Post by Nixie Pixel on 2009-04-17
> **HymnToLife said:**
> Delete the old key from [font="monospace"]~/.ssh/known_hosts[/font] (the error message should tell you on which line it is in the file). The correct key will be automatically added to it next time you connect to the server.
Thanks, this worked like a charm!

---

### Post by ranch hand on 2009-04-17
HymnToLife
I have to thank you for this information.  I don't know about the OP but this fixed my problem.

Thank YOU

---

