---
title: "Using Nautilus's &quot;Connect to server...&quot; with SSH Certificate"
date: 2008-12-02
forum: General Help
---

### Post by SeanBannister on 2008-12-02
I'm trying to use Nautilus to browse a server via SSH using the "Connect to server..." feature. The problem is I use a SSH key (certificate) to access the server but Nautilus asks me for a password.

How do I make Nautilus use the certificate rather than the password?

---

### Post by WesleyPurdy on 2008-12-03
I also have the same problem, I wonder if there is a way to invoke Nautilus from the command line with the option to use a key.

---

### Post by adult swim on 2008-12-03
do you have password authentication turned off in your sshd_config?

---

### Post by SeanBannister on 2008-12-03
Currently on both the server and the client PasswordAuthentication is commented out. 

Keeping in mind I don't actually want to set a password, I want to use the certificate.

Should I turn it on or off? On the server or the client?

---

### Post by WesleyPurdy on 2008-12-10
I have still had no luck with this problem.  Any other ideas?

---

