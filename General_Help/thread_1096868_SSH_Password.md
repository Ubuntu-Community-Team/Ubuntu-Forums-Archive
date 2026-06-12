---
title: "SSH Password"
date: 2009-03-15
forum: General Help
---

### Post by perrti-y02 on 2009-03-15
I have just installed the OpenSSH-server package on this machine and another that I want to connect to.

When I type ssh music1@192.168.2.102 I get prompted for a password

I try the password to log onto that machine but it fails with the message

Permission denied (publickey,password)

I haven't set a password for ssh so I presume this is my error However I don;t know where to set this password.

I also cannot connect to shuttle@127.0.0.1 (this machine) due to the same error.

Any ideas?

---

### Post by Vadi on 2009-03-15
Maybe [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH) can assist you?

---

### Post by perrti-y02 on 2009-03-15
Can't find what I'm looking for there. There is some stuff about RSA keys that I don't get but I thnik my problem is far simpler than that. Is there a file that holds passwords to allow a ssh to connect?

---

### Post by Slim Odds on 2009-03-15
The default install of openssh-server allows login using usename/password. So you should be able to log in to any account (except root) using the same username and password that you would use if you were sitting at the machine.

---

### Post by perrti-y02 on 2009-03-15
Do I need to specify the username? As in to connect to the computer with hostname music1 and ip address 192.168.2.102 and username tim what would I need to do?

---

### Post by perrti-y02 on 2009-03-15
I was being thick

I was typing the hostname instead of the username.

Thanks anyway

---

### Post by blackened on 2009-03-15
> **perrti-y02 said:**
> I was being thick

I was typing the hostname instead of the username.

Thanks anyway

Heh, I've done that before by accident. It should be

```
tim@192.168.1.51:/home/tim
```

where the IP is the correct IP of the machine you're trying to connect to, obviously.

---

### Post by lovinglinux on 2009-03-15
> **perrti-y02 said:**
> Can't find what I'm looking for there. There is some stuff about RSA keys that I don't get but I thnik my problem is far simpler than that. Is there a file that holds passwords to allow a ssh to connect?

I strongly advice that if you "don't get it", that you read until you do. Otherwise you could be putting your machine at risk. Using RSA keys is the recommended way to authenticate into a remote machine using ssh, specially if you are connection from outside your lan.

From [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

> If your SSH server is visible over the Internet, you should use public key authentication instead of passwords if at all possible. If you don't think it's important, go to your /var/log/ folder and have a look at the files named auth (attempted logins for this week) and auth.0 (attempted logins for last week). My computer - a perfectly ordinary desktop PC - had over 4,000 attempts to guess my password and almost 2,500 break-in attempts in the last week alone. How many thousand random guesses do you think it will take before an attacker stumbles across your password?

With public key authentication, every computer has a public and a private "key" (a large number with particular mathematical properties). The private key is kept on the computer you log in from, while the public key is stored on the .ssh/authorized_keys file on all the computers you want to log in to. When you log in to a computer, the SSH server uses the public key to "lock" messages in a way that can only be "unlocked" by your private key - this means that even the most resourceful attacker can't snoop on, or interfere with, your session. As an extra security measure, most SSH programs store the private key in a password-protected format, so that if your computer is stolen or broken in to, you should have enough time to disable your old public key before they break the password and start using your key. Wikipedia has a more detailed explanation of how keys work.

Public key authentication is a much better solution than passwords for most people. In fact, if you don't mind leaving a private key unprotected on your hard disk, you can even use keys to do secure automatic log-ins - as part of a network backup, for example. Different SSH programs generate public keys in different ways, but they all generate public keys in a similar format: 

---

### Post by Slim Odds on 2009-03-15
> **lovinglinux said:**
> I strongly advice that if you "don't get it", that you read until you do. Otherwise you could be putting your machine at risk. Using RSA keys is the recommended way to authenticate into a remote machine using ssh, specially if you are connection from outside your lan.

From [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

If the OP is connecting over the Internet, then I totally agree (no mention of that in the original post).

I put a machine up using only key authentication and the number of username/password attempts was amazing (starting pretty much immediately).

---

### Post by Slim Odds on 2009-03-15
> **blackened said:**
> Heh, I've done that before by accident. It should be

```
tim@192.168.1.51:/home/tim
```where the IP is the correct IP of the machine you're trying to connect to, obviously.

You don't need the ":/home/tim". That's the default....

---

### Post by lovinglinux on 2009-03-15
> **Slim Odds said:**
> If the OP is connecting over the Internet, then I totally agree (no mention of that in the original post).

Even if he doesn't, it would be good if he at least understand the concept, because he could be unaware of open ports in the router or he could eventually decide to access the machine from the internet in the future, without knowing about the risks. Is not a good idea to ignore the instructions about RSA keys because he doesn't understand them.

---

### Post by Slim Odds on 2009-03-15
> **lovinglinux said:**
> Even if he doesn't, it would be good if he at least understand the concept, because he could be unaware of open ports in the router or he could eventually decide to access the machine from the internet in the future, without knowing about the risks. Is not a good idea to ignore the instructions about RSA keys because he doesn't understand them.

Again, I totally agree....

---

### Post by blackened on 2009-03-15
> **Slim Odds said:**
> You don't need the ":/home/tim". That's the default....

Aye you're right. I'm used to using it with sshfs mounts, so it's just a habit.

---

### Post by perrti-y02 on 2009-03-15
A present I am accesing it simply via a crossover cable but I do plan to set up a wireless network so I shall read about this.

---

