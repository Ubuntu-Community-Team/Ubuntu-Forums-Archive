---
title: "General question on setting up a simple file sharing server"
date: 2009-03-08
forum: General Help
---

### Post by mahela007 on 2009-03-08
HI. I am curious (meaning I might do it)  about setting up a server on my kubuntu PC. I don't want a fully fledged web server. I just want a simple server which I can use to share files (between myself and my friends only). Is it really difficult to do this? Also what are the practical dangers of doing so?
I don't have much experience with networking. 

If it's relevant the details of my PC are as follows .
I have dual booted kubuntu with windows and am running a pentium 4  2.8 GHz PC with 512 RAM and a 160GB hard disk. ( I know this isn't the most high end PC but that's why I'm willing to experiment :))

---

### Post by Dysport on 2009-03-08
What kind of files do you want to share? Only media files or other types as well? And do you need a web interface?

For media files I can recommend GNUMP3d, great media server with streaming abilities. Although you should lock or protect it somehow if you want to use it outside your local network.

If you want to do something like a public FTP you would need something like PROFTPd or just create a user with restricted access to the shared files and folders, then people can login via SSH.

Whatever you do, if you want to be reachable from the internet you have to open the ports in your firewall and/or router. And in case you don't have a static IP you may want to set up a DynDNS Account.

---

### Post by mahela007 on 2009-03-08
> **Dysport said:**
> What kind of files do you want to share? Only media files or other types as well? And do you need a web interface?

For media files I can recommend GNUMP3d, great media server with streaming abilities. Although you should lock or protect it somehow if you want to use it outside your local network.

If you want to do something like a public FTP you would need something like PROFTPd or just create a user with restricted access to the shared files and folders, then people can login via SSH.

Whatever you do, if you want to be reachable from the internet you have to open the ports in your firewall and/or router. And in case you don't have a static IP you may want to set up a DynDNS Account.
I don't know much about it but from the little I have read I think what I want is FTP. It's like this. I have certain files I would like to share (mostly text documents ) and I want them to be accessible via the Internet and I like toying with my old,tired PC

---

### Post by Dysport on 2009-03-08
Then proftpd would be the right app :) There is a pretty good guide in the forum: [http://ubuntuforums.org/showthread.php?t=79588]("http://ubuntuforums.org/showthread.php?t=79588")
Or you can google something like "ubuntu proftpd install OR setup OR howto"

And don't forget to forward the port 21 in your modem: [http://portforward.com/]("http://portforward.com/")
Plus, as i mentioned before, you might want to set up an account at dyndns.com and configure your modem appropriately, too.
Good luck ;)

---

### Post by hyper_ch on 2009-03-08
I'd use

openssh-server

then install mysecureshell to restrict users to sftp only

then create the system users and alias their UID to one specific so each individual one can write to the same set. Also their shell should be set to  /bin/false

---

### Post by mahela007 on 2009-03-08
> **Dysport said:**
> Then proftpd would be the right app :) There is a pretty good guide in the forum: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
Or you can google something like "ubuntu proftpd install OR setup OR howto"

And don't forget to forward the port 21 in your modem: [http://portforward.com/](http://portforward.com/)
Plus, as i mentioned before, you might want to set up an account at dyndns.com and configure your modem appropriately, too.
Good luck ;)
what is dyndns?

---

### Post by hyper_ch on 2009-03-08
> **mahela007 said:**
> what is dyndns?

[http://tinyurl.com/cxwlvz](http://tinyurl.com/cxwlvz)

---

### Post by mahela007 on 2009-03-08
> **hyper_ch said:**
> [http://tinyurl.com/cxwlvz](http://tinyurl.com/cxwlvz)
:DDid you make that? How'd you do it?

---

### Post by hyper_ch on 2009-03-09
(1) go on [http://www.letmegooglethatforyou.com](http://www.letmegooglethatforyou.com)
(2) enter key words
(3) press "Google search"
(4) convert the given URL to a tiny url (can also be done on lmgtfy)

---

