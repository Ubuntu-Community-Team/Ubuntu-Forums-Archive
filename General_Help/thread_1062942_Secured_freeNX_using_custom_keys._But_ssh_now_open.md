---
title: "Secured freeNX using custom keys. But ssh now open"
date: 2009-02-07
forum: General Help
---

### Post by svaens on 2009-02-07
Hi all, 

Quick question. 
I just installed freeNX so i could graphically access my own computer from work. I also created and installed the custom keys (as per instructions in ubuntu howto: 
[https://help.ubuntu.com/community/FreeNX#Using%20custom%20SSH%20keys]("https://help.ubuntu.com/community/FreeNX#Using%20custom%20SSH%20keys")

And that works great. I can't log in until i've installed the client key on the client. Exactly what I want. 

But, in installing the freenx server i've installed the dependency 'sshd'. 
And, I can now connect to my computer using ssh. AND it does NOT require any key. Just the usual username password pair. This is a bit insecure, and to my mind, makes useless the whole process I just went to in making the freenx more secure by using custom keys there. 

What is the best solution to this?

Can I Secure SSH server with Public/Private key authentification? 
as per website instruction here:
[http://www.debuntu.org/ssh-key-based-authentication]("http://www.debuntu.org/ssh-key-based-authentication")
But then, wouldn't that somehow break the authentication process for freeNX?

What should I do? I would rather the ssh also have the combination key + user/password authentication as does the freeNX!

Thanks in advance for all replies and advice.

---

### Post by dougie173 on 2009-02-07
I've just installed freeNX as I tried using VNC over ssh but it was slow.

The nx protocol uses ssh to encrypt traffic between your remote machine and your client. 

In order to do that it needs to have the sshd daemon running. 

There are a couple of things that I have done to try and make this as secure as possible. 

Run your sshd on a non standard port. When I had port 22 open on my home router, I was getting loads of failed connections in my auth.log. Since I've moved it to a non standard port. Nada, Zilch. As a lot of these attacks are scripted they only really go for the standard ports.

You can change the port that ssh listens to in /etc/ssh/sshd_config
You also need to add this port in /etc/nxserver/node.conf

You can also add 'AllowUsers' in sshd_config, so that ssh will ONLY let those users appempt to log in using ssh. (If you're going to add AllowUsers then user nx needs to be included so that freenx works, it took me a couple of hours of gnashing of teeth and banging my head against the wall to work that one out!! ;) )

Hope this helps

---

### Post by svaens on 2009-02-08
Hi, and thanks for your reply!

The port change sounds like a good idea! I will do that. I didn't yet as i expected those doing an attack would do a port scan and find it anyway. But if the most of these are scripted then, as you say. It will help alot.

As for the AllowUsers option. This would only restrict the number of user names a hacker could try, correct? So it wouldn't increase the security 'that' much then would it? 

```

scenario before using AllowUsers:
system users: mark, mary jane, admin
hacker can try to log in using any of these users

scenario after using AllowUsers (AllowUsers admin)
hacker must try to login using only admin acccount by guess admin password.

```


Do you think it affects the setup of freenx (and the ability of clients to connect) if i setup sshd to use key based authentication?

Is it possible to setup sshd to use both key based authentication AND username password?

thanks again!

---

### Post by joris1977 on 2009-06-09
> **svaens said:**
> Hi all, 

Quick question. 
I just installed freeNX so i could graphically access my own computer from work. I also created and installed the custom keys (as per instructions in ubuntu howto: 
[https://help.ubuntu.com/community/FreeNX#Using%20custom%20SSH%20keys]("https://help.ubuntu.com/community/FreeNX#Using%20custom%20SSH%20keys")

And that works great. I can't log in until i've installed the client key on the client. Exactly what I want. 

But, in installing the freenx server i've installed the dependency 'sshd'. 
And, I can now connect to my computer using ssh. AND it does NOT require any key. Just the usual username password pair. This is a bit insecure, and to my mind, makes useless the whole process I just went to in making the freenx more secure by using custom keys there. 

What is the best solution to this?

Can I Secure SSH server with Public/Private key authentification? 
as per website instruction here:
[http://www.debuntu.org/ssh-key-based-authentication]("http://www.debuntu.org/ssh-key-based-authentication")
But then, wouldn't that somehow break the authentication process for freeNX?

What should I do? I would rather the ssh also have the combination key + user/password authentication as does the freeNX!

Thanks in advance for all replies and advice.

Same issue here. I really like FreeNX and it makes you wonder why vnc still exists. But not having key authentication with ssh is a showstopper. One look at auth.log is enough to realize this is important.
I guess this should be simple to solve but can't find a solution...

I was about to write a new post about this, but i guess it is better to bump this one.

---

### Post by joris1977 on 2009-06-12
> **joris1977 said:**
> Same issue here. I really like FreeNX and it makes you wonder why vnc still exists. But not having key authentication with ssh is a showstopper. One look at auth.log is enough to realize this is important.
I guess this should be simple to solve but can't find a solution...

I was about to write a new post about this, but i guess it is better to bump this one.


Seems I fixed it!

WARNING: I am new to linux and feel uncomfortable efiting config files I don't totally understand. As far I can understand it seems safe what I have done and is safer than a ssh setup without key authentification but try at your own risk.

This two links putted me on the right path:
[http://wiki.centos.org/HowTos/FreeNX](http://wiki.centos.org/HowTos/FreeNX)
[http://linuxgazette.net/135/knaggs.html](http://linuxgazette.net/135/knaggs.html)

Steps to take

Install ssh. I followed this tutorial:
[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

Install freeNX I followed this tutorial:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

So now you have a secure ssh setup with key authentification but cannot login to NX over ssh

Edit the /etc/ssh/sshd_config file and change/add the following lines:
```
AllowUsers nx
AllowUsers (your user name)
UsePAM yes
```

Don't forget to restart the sshd daemon after making that change:

```
sudo /etc/init.d/ssh restart
```

Next step is to copy the  /var/lib/nxserver/home/.ssh/client.id_dsa.key to your client machine. (You probably already did this following the freenx howto)  

But you need to copy the key on the client machine to .ssh and rename it.

like this:

```
cp $HOME/client.id_dsa.key $HOME/.ssh/id_dsa
```

By now, you should be ready to login to the nx server over ssh

You can try this with:

```
ssh nx@remote-server
```
It will respond with
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 

Works? Good. Let's go on. By default, if you try to connect to the NX server, it will use the nx account for the ssh connection (with key authentication) but it will try also to connect in ssh with your own username/password to the host you're trying to reach. Because you've disabled the PasswordAuthentication over ssh, you have to use the NX Database to allow pass-through authentication. Be sure that /etc/nxserver/node.conf file contains the following line :

```
ENABLE_PASSDB_AUTHENTICATION="1"
```
 
I am not sure if it is really necessary but I guess it can do no harm to restart to freenx server at this point.

```
sudo nxserver --restart
```

Last step is to create a account on the NX server. 

```
sudo nxserver --adduser (yourusername)
```

NX server will reply with:

NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 716 Public key added to: /home/yourusername/.ssh/authorized_keys2
NX> 1001 Bye.
NX> 999 Bye

and add a  password

```
sudo nxserver --passwd (yourusername)
```

NX> 100 NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
New password: 
Password changed.
NX> 999 Bye

That's it, now you should be able to do a secure login with the NoMachine NX client for linux using key authentification

Works for me and should work for you.

:popcorn:

Please comment if you think this setup is not secure or unwise for some reason. There is already too much misinformation around.

---

### Post by men8th on 2010-01-20
Works for me too (and I am an amateur). Only slight hiccup was that I had to change the permissions of ~/.ssh/id_dsa before ssh would allow me to use it.

Cheers, Tim

---

### Post by zollie on 2010-01-20
change this setting

#PasswordAuthentication yes

to

PasswordAuthentication no

in

/etc/ssh/sshd_config

and that's it.  Only key-based logins will now be allowed.

---

### Post by lespedeza on 2010-09-22
Not sure if this is a better or easier way, but I finally got mine working the way I wanted it by doing the following.  I think I tried the above, but it only worked when logging in as user nx.  I was unable to ssh as a regular user.  So I banged my head enough and came up with this.

1. Reconfigure freenx to use custom keys
```
sudo dpkg-reconfigure freenx-server
```
-select custom keys and SSH

2. Copy generated key to client machine. On my machine key was located in
```
/var/lib/nxserver/home/.ssh/client.id_dsa.key
```

3. When you configure your nx session on the client, import the key that you just copied over.  Press Configure on main screen and then there is a key button under the server panel on the 'General' tab.

3. Edit sshd_config to use nxserver's keys

-change
```
AuthorizedKeysFile ...
```
to
```
AuthorizedKeysFile /var/lib/nxserver/home/.ssh/authorized_keys2
```

4. Restart sshd.

At this point you should be able to connect to server using the nx client.  But at this point, I was unable to ssh using command line or putty (windows) since the only keys it was seeing were the keys in the nxserver's authorized_keys2 file.

I tried adding keys to this file, but it would only let me connect as user nx.  I'm assuming due to permission issues on the authorized_keys2 file.  I didn't want to mess with the permissions on this file, so in order to resolve the issue, I took advantage of the sshd_config value AuthorizedKeysFile2.

5. Add the following line to sshd_config 

```
AuthorizedKeysFile2 /home/<user>/.ssh/authorized_keys
```

where <user> is your regular user.

6. Add public keys to user's authorized_keys files as usual.

This setup allows me to connect remotely via NX and via regular ssh sessions.

Let me know if this helps or not or if you have any questions.

---

### Post by akurewmgkmhghd on 2012-10-13
This thread has been helpful to me today, so thanks to all you contributors.

Another note on the AllowUsers configuration, I read from the link below that in addition to specifying the user name in AllowUsers you can also specify an IP address such as

```

AllowUsers wilson@127.0.0.1
AllowUsers wilson@192.168.*
AllowUsers wilson@123.222.111.1 
```So that would require the attacker to not only be using the right account and guessing the credential, but also they would need to somehow fake the right ip address.

Reference: [http://notepad2.blogspot.com/2010/11/sshdconfig-settings-for-nx-serverclient.html](http://notepad2.blogspot.com/2010/11/sshdconfig-settings-for-nx-serverclient.html)

---

### Post by wildmanne39 on 2012-10-13
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

