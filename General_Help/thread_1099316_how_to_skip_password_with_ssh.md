---
title: "how to skip password with ssh?"
date: 2009-03-18
forum: General Help
---

### Post by flatcoke on 2009-03-18
Hi,
When I use ssh I really wish to skip typing passwords all the time. However, my remote host won't support key pair method. Is there any other way(like by using scripts) to automate my login process? I understand that it might compromise security but I'm willing to take the risk. I also use kinit to authenticate myself to AFS services by Kerberos. I would like to skip that password as well, if possible.

p.s. Sometimes my terminal window just stop taking keyboard inputs. This can be really annoying. If I tab to other apps and tab back, I get a 80% chance to get it working again. Mouse worked well all the time though.

Thanks for your time and efforts.

---

### Post by lovinglinux on 2009-03-18
> **flatcoke said:**
> I understand that it might compromise security but I'm willing to take the risk.

Not a good idea.

> If your SSH server is visible over the Internet, you should use public key authentication instead of passwords if at all possible. If you don't think it's important, go to your /var/log/ folder and have a look at the files named auth (attempted logins for this week) and auth.0 (attempted logins for last week). My computer - a perfectly ordinary desktop PC - had over 4,000 attempts to guess my password and almost 2,500 break-in attempts in the last week alone. How many thousand random guesses do you think it will take before an attacker stumbles across your password?

> **flatcoke said:**
>  I also use kinit to authenticate myself to AFS services by Kerberos. I would like to skip that password as well, if possible.

I guess you can use Kerberos to authenticate the ssh connection.
Try this thread [http://ubuntuforums.org/showthread.php?t=532561](http://ubuntuforums.org/showthread.php?t=532561)

---

### Post by t0p on 2009-03-18
> How many thousand random guesses do you think it will take before an attacker stumbles across your password?

Maybe more than you think.  The other day I was helping a friend gauge the strength of his wpa key.  I ran a 40MB wordlist against it with aircrack-ng - about 1.5 million "words" - and didn't get anywhere.  Last night I used johntheripper to variate the wordlist up to over 400MB - over 15 million "words" - I'll run it against his key later, but I don't expect any more success than last time.  If you have a strong password, even rainbow tables won't necessarily get anywhere with it.

Of course, the operative phrase is "strong password".  If you use real words or l337 speak as a password, it is in far more danger of being cracked.  But using special characters (£$%^&*) somewhere in there magnifies the strength considerably.

As far as the OP here is concerned: putting your password into a script is very very insecure.  Maybe you "don't care" about security.  But you'll change your mind when you find your computer's being used to store some cracker's "sensitive" files.

---

### Post by brian_p on 2009-03-18
> **flatcoke said:**
> 

Is there any other way(like by using scripts) to automate my login process? 

An expect script would do this.

---

### Post by fieroboom on 2009-03-18
Can you give a little more detail on *why* the server doesn't support key pair auth?
Correct me if I'm wrong, but AFAIK, SSH-1, SSH-2, and OpenSSH all support public/private key pair authentication, and key pair auth is going to be 100 times safer than any script you write with your passwd in it.

In case you are just unaware of how to set up key auth, here's a crash course:

- cd into your ssh folder:
```
cd ~/.ssh
```
- Generate the key pair:
```
ssh-keygen -t <rsa|dsa> -b <number_of_bits> -C <some_comment>
```
- Place the pub key on the server
```
scp <key_name> <server>:/home/<username>/.ssh/
```
- On the local machine, edit your /etc/ssh/ssh_config to use your private key
```
sudo nano /etc/ssh_config
```
Find, uncomment, and edit one of the these lines:
```
#   IdentityFile ~/.ssh/identity
   IdentityFile ~/.ssh/<key_name>
#   IdentityFile ~/.ssh/id_dsa
```
- On the remote server, add the public key to your 'authorized_keys' file:
```
cd ~/.ssh
cat <key_name> > authorized_keys
```
- Disable password auth on the server (OPTIONAL - I do this on my machines, so you *can't* get into it unless you have *my* key... But if you ever lose your private key, you'll need physical access to the machine.)
[ssh-keygen man page](http://linux.die.net/man/1/ssh-keygen)
:D
-Paul

---

### Post by KeyserSoze93 on 2009-03-18
It may not work if the two machine have different versions of the SSL library (I assume that's what is causing it)

Make sure you've done and apt-get update and apt-get upgrade on both machines or what fieroboom said may not work.

---

### Post by flatcoke on 2009-03-19
Thanks for all the help. I have 3 servers I login to several times a day, and I managed to get key pair working on only one server. Running the same procedure won't work on the other two. I'll probably try googling to see if I can use kerberos to authenticate with ssh though I don't really have a clue how.

---

