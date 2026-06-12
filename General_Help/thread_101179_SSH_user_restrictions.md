---
title: "SSH user restrictions"
date: 2005-12-09
forum: General Help
---

### Post by ScreemingBlue on 2005-12-09
I have a ssh server running on my box and use it to access files etc. while I am at work using WinSCP to browse  my PC.
My problem now is how would I give limited file access to say a guest user to allow them only to see a certain part of the filesystem. In other words I would like to achieve what you can with a FTP server but more securely with SSH.

Is this possible????

---

### Post by matid on 2005-12-09
[QUOTE=ScreemingBlue]Is this possible????[/QUOTE]
Actually that's the wrong question, 'cause ssh shouldn't be used for transfering files. That's what you use FTP for. If you want to be more secure you should go for SFTP not SSH.

---

### Post by ScreemingBlue on 2005-12-09
Point taken. I will investigate the SFTP route, I think this is what I was trying to say. SFTP uses SSH, right?

---

### Post by isaric on 2005-12-09
I do not speak English and I am not on answering your question! But if that can help you!

[http://mysecureshell.sourceforge.net/]("http://mysecureshell.sourceforge.net/")

---

### Post by soulestream on 2005-12-09
you would setup the system just like they were logging in, in front of the machine. 

Disable root logins in sshd_config

the just create them a user, and a home directory. You can use scp of sftp to copy files then. 

of just setup ftp. vsftp/proftp whatever. But I like the ssh approach myself.


soule

---

### Post by Arvin on 2006-01-12
Look at [Mysecureshell]("http://mysecureshell.sourceforge.net/") if you are interested in SFTP server. MSS is a very good soft for it. Note a [forum]("http://216.239.37.104/translate_c?hl=fr&ie=UTF-8&oe=UTF-8&langpair=fr%7Cen&u=http://mysecureshell.free.fr/&prev=/language_tools")  exist for help ;)

---

### Post by Arvin on 2006-01-12
[QUOTE=Arvin]Look at [Mysecureshell]("http://mysecureshell.sourceforge.net/") if you are interested in SFTP server. MSS is a very good soft for it. Note a [forum]("http://216.239.37.104/translate_c?hl=fr&ie=UTF-8&oe=UTF-8&langpair=fr%7Cen&u=http://mysecureshell.free.fr/&prev=/language_tools")  exist for help ;)[/QUOTE]

If you speak [french]("http://doc.ubuntu-fr.org/serveur/mysecureshell_sftp-server").

---

