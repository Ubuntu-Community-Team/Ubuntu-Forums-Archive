---
title: "how do I make Ubuntu remember my SSH password"
date: 2009-05-11
forum: General Help
---

### Post by Eugene_Bondarenko on 2009-05-11
Hi!

I've installed
[http://code.google.com/p/nautilussvn/](http://code.google.com/p/nautilussvn/) 
and I use SVN+SSH:// to connect to our repository. The problem is that openSSH password box pops up too often and I want to get rid of it.
I've been trying to go through this
[http://mah.everybody.org/docs/ssh](http://mah.everybody.org/docs/ssh)
but no success. I guess our server is not set up for DSA authentication. Also I think this manual is not exactly what I need. As far as I understand it remembers passwords for the current session only.

In windows I set up tortoiseSVN to use the following SSH client:
C:\Program Files\TortoiseSVN\bin\TortoisePlink.exe -l MY_LOGIN_HERE -pw MY_PASSWORD_HERE (that exe file is Putty)

Is there any way I can do the same in Ubuntu? May be there is some way to make putty the default SSH client?

Thanks for any help!

---

### Post by Eugene_Bondarenko on 2009-05-12
*up*

---

### Post by apmcd47 on 2009-05-12
Okay, the good news is that ssh-agent should already be installed on your system if you use ubuntu. All you need to do is run ssh-add in a terminal window every time you log in. It should be possible to get it to run automatically every time you log in, but I'll leave that to you to find out.

Now I'm going to state the obvious:
[LIST]
[*]Have you created an ssh key on your local machine?
[*]Have you copied the public key to the server?
[*]Have you ensured the .ssh directory on both machines is readable only by you?
[/LIST]
If all this is true, you should be able to use the SVN client without having to enter the passphrase after you have run ssh-add once for each login session.

If you really don't ever want to use a passphrase, you **could** use a passphrase-free ssh key, but I would recommend avoiding that. It should be possible to set up the key so it can only be used at the server end for SVN, which would reduce the security implications of using a passphrase free key, but I think you are better off typing it in once per session.

Andrew

---

### Post by Eugene_Bondarenko on 2009-05-12
Thanks for all that info,  I'll check that things once I get to my linux PC. 

And regarding your questions:
1). Does this thing create the key you mention?
ssh-keygen -t dsa -f ~/.ssh/id_dsa -C "you@example.com"
If yes, then yeah, I've created it :)
2). Nope, I don't have access to it so I'll have to bother our admins. Is there aby way we can avoid this? :)
3). Really not sure about this by at least it is readable-writable by me :)

Doesn't ubuntu have some windows similar way I described earlier? I've been using
```
C:\Program Files\TortoiseSVN\bin\TortoisePlink.exe -l MY_LOGIN_HERE -pw MY_PASSWORD_HERE (that exe file is Putty)
```
and I really like that. Can I just hardcode my password somewhere?

---

### Post by sahabcse on 2009-05-12
Follow below url for setting up the autmatic login via ssh without password

[http://sahabm.blogspot.com/2009/04/automatic-login-with-ssh-without.html](http://sahabm.blogspot.com/2009/04/automatic-login-with-ssh-without.html)

---

### Post by Eugene_Bondarenko on 2009-05-12
Thanks for that manual, I'll try it out.

I've just figured out that I may be confusing something. So "logging in to the server" doesn't mean I must have server root? Is my login I use for svn+ssh:// enough?

---

### Post by apmcd47 on 2009-05-12
> **Eugene_Bondarenko said:**
> Thanks for that manual, I'll try it out.

I've just figured out that I may be confusing something. So "logging in to the server" doesn't mean I must have server root? Is my login I use for svn+ssh:// enough?

There must be some form of username you are using to access the SVN server with. This may be some account the sysadmin of the server set up for you, or some generic SVN account everybody uses. I don't know about SVN, but CVS uses the username in its log for checking out files and committing changes, so the latter would be pointless.

You should be able to login to the server using ssh, then put the public key into the .ssh/authorized_keys file on the server. You may be blocked from doing anything other than SVN, in which case you may have to ask the sysadmin of the server to do it for you.

Andrew

---

### Post by Eugene_Bondarenko on 2009-05-14
I've tried out everything you said here and this manual seems to have some effect.
[http://sahabm.blogspot.com/2009/04/automatic-login-with-ssh-without.html](http://sahabm.blogspot.com/2009/04/automatic-login-with-ssh-without.html)

However I am not sure if I am moving into the correct direction because now SSH pops up two windows. The first one asks to enter passphrase and the second asks to enter password :biggrin:

Tonight I'll try to go through the whole process from the beginning and will let you know if I still have this weird issue.

PS. I've found out that I have full SSH access to that server

---

### Post by cb951303 on 2009-05-14
I'm not sure if that's what you're looking for but you can create a "Secure Shell Key" from "Menu > Accessories > Passwords and Encryption Keys"
That let's me connect to my SSH account without entering any passwords (only the keyring password once)

---

### Post by Eugene_Bondarenko on 2009-05-19
> **cb951303 said:**
> I'm not sure if that's what you're looking for but you can create a "Secure Shell Key" from "Menu > Accessories > Passwords and Encryption Keys"
That let's me connect to my SSH account without entering any passwords (only the keyring password once)
Yeah, that's exactly what I am looking for but unfortunately I didn't have any luck with this. In "My Personal Keys" tab I create a new SSH key, type server, login, password. :( Then I go to terminal and type "ssh my_server" and it asks me to enter password. Typing ssh-add before ssh my_server doesn't help too. :(

---

### Post by cb951303 on 2009-05-19
maybe you can try different encryption types?

EDIT: Also it would be better if you delete the ".ssh" directory on the server so that you can start from scratch.

---

