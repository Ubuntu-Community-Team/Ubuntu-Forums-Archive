---
title: "SSH &amp; Public Keys"
date: 2009-03-28
forum: General Help
---

### Post by Darkade on 2009-03-28
I've gone trough the [SSH howto]("https://help.ubuntu.com/community/SSHHowto") in the Ubuntu community documentation and I've succesfully set up an SSH and VNC server, and can VNC over SSH.

I just have one doubt. I have added my laptop's public key to $HOME/.ssh/authorized_keys but I don't understand how to make sure the connection between my Desktop and laptop is using the laptop public key.

So, how can I be sure? the SSH howto even says that public keys are so secure that  you can even disable the SSH's password authentication. And I do know and believe that, but I'm not sure I've set up the public key right.
How can I check?

---

### Post by Dr Small on 2009-03-28
Wen setting up a private SSH key (you can probably do it again, as it won't hurt), use a password that is different from your login on the remote computer. So, after you setup the keys, and it prompts you for the password, if you have to put in the password that is different from the remote system, you are using the SSH keys.

I setup passwordless SSH keys, so it automatically logs me in when connect to the remote server :)

---

### Post by lovinglinux on 2009-03-28
You can also check the logs. If the key is working properly, there should be some entries in the logs with something like "key pair accepted".

---

### Post by Dr Small on 2009-03-28
> **lovinglinux said:**
> You can also check the logs. If the key is working properly, there should be some entries in the logs with something like "key pair accepted".
You're right:
```
Mar 28 17:44:12 mycroft sshd[28847]: Accepted publickey for drsmall from 192.168.0.16 port 53676 ssh2
Mar 28 17:44:12 mycroft sshd[28849]: (pam_unix) session opened for user drsmall by (uid=0)
```

---

### Post by lovinglinux on 2009-03-28
BTW, you can also disable ssh password authentication. This doesn't mean it won't be protected, just means you won't be able to login using plain text passwords, only using keys. So if you disable password authentication and you still can connect, it means your key is working.

---

### Post by Dr Small on 2009-03-28
> **lovinglinux said:**
> BTW, you can also disable ssh password authentication. This doesn't mean it won't be protected, just means you won't be able to login using plain text passwords, only using keys. So if you disable password authentication and you still can connect, it means your key is working.
And if you can't connect, and the remote system is on the other side of the planet.... Well, let's not go there ;)

---

### Post by lovinglinux on 2009-03-28
> **Dr Small said:**
> And if you can't connect, and the remote system is on the other side of the planet.... Well, let's not go there ;)

I never thought about that :oops:

I suggested that because my ssh server is on my local network, as it seems to be the case for the OP.

---

### Post by Darkade on 2009-03-28
Thank you both that worked. Just for future reference this is what I did:

My computers are:
SSH-server: Desktop, Ubuntu 8.04
remote: Laptop, Arch

And this is what I do:
1) In arch I use ```
ssh-keygen
```

2)keygen asks where to save the key, I use default location (~/.ssh/id_rsa)

3)It asks me for a passphrase, I use one different that that of my Desktop. Now in ~/.ssh/ I have two files id_rsa and id_rsa.pub

4)I then copy the key file (over ssh with scp LOL) to my desktop
```
scp ~/.ssh/id_rsa.pub usr@server:/home/user/.ssh/
```

5)open the file and copy the contents at the bottom of ~/.ssh/authorized_keys

6)SSH into the server and now it asks me for the passphrase of the public key.

7)in the server logs (/var/log/auth.log) now I can see those "publickey accepted" lines

:D:D:D THANKS... I miss the thanks button

---

### Post by Hobgoblin on 2009-03-28
> **Darkade said:**
> I've gone trough the [SSH howto]("https://help.ubuntu.com/community/SSHHowto") in the Ubuntu community documentation and I've succesfully set up an SSH and VNC server, and can VNC over SSH.

I just have one doubt. I have added my laptop's public key to $HOME/.ssh/authorized_keys but I don't understand how to make sure the connection between my Desktop and laptop is using the laptop public key.


If you have set it up right then it shouldn't ask for the password.

---

### Post by Darkade on 2009-03-28
> **lovinglinux said:**
> I never thought about that :oops:

I suggested that because my ssh server is on my local network, as it seems to be the case for the OP.
I also use my SSH server in my local network... my home network :lolflag: but from time to time It's nice to log in over the internet, and to use VNC over the internet.

I just had postponed this publickey thing more than I should. And now it works.

:D

---

### Post by Dr Small on 2009-03-28
> **Darkade said:**
> I also use my SSH server in my local network... my home network :lolflag: but from time to time It's nice to log in over the internet, and to use VNC over the internet.

I just had postponed this publickey thing more than I should. And now it works.

:D
Yeah, for local network stuff, you can just setup a passwordless ssh key (it saves you alot of keypresses, if you have a long password and you use SSH alot), yet still have PasswordAuthentication enabled for usage outside of your network. (Just install DenyHosts so you can stop all the cracking attempts ;))

---

