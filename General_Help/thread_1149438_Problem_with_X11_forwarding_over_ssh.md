---
title: "Problem with X11 forwarding over ssh"
date: 2009-05-05
forum: General Help
---

### Post by anandamide on 2009-05-05
Oh glorious and kind Ubuntu world

I've finally got around to installing eeebuntu NBR on my Asus, replacing the truly awful Xandros distro which it came packaged with. Very pleased to have made the move - I finally have something I want to use!

My issue right now tho is that I can't forward any graphical interfaces into it using ssh. I'm trying to read some pdfs / run gedit from my desktop, and all I get is:

```
(gksu:9242): Gtk-WARNING **: cannot open display:
```

After an initial search online I had a 'D'oh' moment and changed /etc/ssh/ssh_config to

```
X11Forwarding yes
```

But I'm still getting the same problem. Any ideas would be greatly appreciated.

---

### Post by geirha on 2009-05-05
You changed that setting on the client's ssh_config right? After you've logged in, do ```
echo $DISPLAY
``` It should output something like "localhost:10.0" if X11forwarding is enabled.

---

### Post by anandamide on 2009-05-05
Thanks for the speedy reply :-)

My desktop has a .ssh/ssh_config file which is set to 'yes', and I've just changed the global /etc/ssh/ssh_config to 'yes' (in the process actually managing to learn some of the keybindings for vi ;-) ). Hoever, 

```
$ echo $DISPLAY
```

gives me a blank line?

I should've pointed out in my first message that once I got the config files set up I never had this problem under Xandros.

---

### Post by geirha on 2009-05-05
That's odd. Try specifying X-forwarding on the command-line and see if that works.
```
ssh -X user@hostname gedit
```

---

### Post by anandamide on 2009-05-05
OK, that gives

```
 
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".

```

Helpful?

---

### Post by geirha on 2009-05-05
Based on my initial googling of the message, it sounds like it is a harmless warning. Does the gedit window appear anyway?

EDIT: BTW, I just checked the man-page for ssh, and the proper option is ForwardX11, not X11Forwarding.

---

### Post by anandamide on 2009-05-05
> **geirha said:**
> Based on my initial googling of the message, it sounds like it is a harmless warning. Does the gedit window appear anyway?

Y'know, the first time I tried I got that warning splurged out and nothing opened - I try now (after rebooting my Asus for an unrelated matter) and 

```
$ ssh -X user@host gedit
```

brings no warnings and opens up gedit no problem (!? - I could quite easily be misremembering this, I'm recovering from a big bank holiday and I trust computers to be more consistent than humans!). However, trying to open gedit from an ssh session still returns the above error.

?

> EDIT: BTW, I just checked the man-page for ssh, and the proper option is ForwardX11, not X11Forwarding.

My bad - all files were set to ForwardX11.

---

### Post by geirha on 2009-05-05
For some reason it doesn't read the configfile(s) you've edited then. Check what files it actually reads by adding the -v flag.
```
ssh -v user@host 2>/tmp/ssh.log
```
After logging in, log back out, then look at /tmp/ssh.log
```
grep Reading /tmp/ssh.log
grep X11 /tmp/ssh.log
```

---

### Post by anandamide on 2009-05-05
Thanks again for your time :-)

Here's the grep'd output:

```
philip@synapse:~$ grep Reading /tmp/ssh.log 
debug1: Reading configuration data /etc/ssh/ssh_config
philip@synapse:~$ grep X11 /tmp/ssh.log 
philip@synapse:~$ 

```

So this means it **is** reading the config file? I just checked to ensure this whole scenario wasn't the result of some comedown-induced stupidity, but no - still getting that same error message.

:-/

---

### Post by geirha on 2009-05-05
And there's only one ForwardX11 entry?
```
grep '^[[:space:]]*ForwardX11' /etc/ssh/ssh_config
```

There's not a ForwardX11 no at the bottom or something, I mean.

---

### Post by Portmanteaufu on 2009-05-05
Ah, X11 forwarding. So useful, so half-documented. :P

Scroll down a bit in [this thread]("http://ubuntuforums.org/showthread.php?t=979008") to see my post with a step-by-step on how I got this running on my own machine. 

My best guess having read your situation, though, is that you seem to be editing the /etc/ssh/ssh_config file instead of the /etc/ssh/ssh**d**_config file. (Note the "d".) That file controls the ssh daemon process on the machine you're connecting to and you need to enable X11 forwarding there before it will allow it.

In case that was confusing, there are two players in your SSH connection. The client, (the computer that wants to see the forwarded X11) and the host (the computer actually running the program and passing along the graphics). You've edited the file that allows a client to ask for X11 forwarding. I think you still need to edit the file that allows the host to provide X11 forwarding when it's asked for.

Hope that helps! :D

---

### Post by anandamide on 2009-05-05
Nope - all I have is:

```
#   ForwardX11 yes
#   ForwardX11Trusted yes

```

For completeness, here's the config file:

```
#   ForwardAgent no
#   ForwardX11 yes
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

---

### Post by geirha on 2009-05-05
> **Portmanteaufu said:**
> 
My best guess having read your situation, though, is that you seem to be editing the /etc/ssh/ssh_config file instead of the /etc/ssh/ssh**d**_config file. (Note the "d".) That file controls the ssh daemon process on the machine you're connecting to and you need to enable X11 forwarding there before it will allow it.


No, we know that the server side has X11 forwarding enabled, because it worked with "ssh -X". It must be some kind of problem with the client-side configuration.

---

### Post by geirha on 2009-05-05
> **anandamide said:**
> Nope - all I have is:

```
#   ForwardX11 yes
#   ForwardX11Trusted yes

```


Well, there you have it. Remove the # in front of the line. # is the comment character. Anything behind # on a line is not treated as a configuration option.

---

### Post by anandamide on 2009-05-05
> **Portmanteaufu said:**
> Ah, X11 forwarding. So useful, so half-documented. :P 

I'd noticed!

> Scroll down a bit in [this thread]("http://ubuntuforums.org/showthread.php?t=979008") to see my post with a step-by-step on how I got this running on my own machine.

Thanks for the heads-up, will do :-) 

> My best guess having read your situation, though, is that you seem to be editing the /etc/ssh/ssh_config file instead of the /etc/ssh/ssh**d**_config file. (Note the "d".) That file controls the ssh daemon process on the machine you're connecting to and you need to enable X11 forwarding there before it will allow it.

Alas and if only! Thanks for the brief primer on the config files, but it appears that sshd_config is also chugging away quite normally:
```

philip@dendrite:~$ cat /etc/ssh/sshd_config | grep X
X11Forwarding yes
X11DisplayOffset 10
```

This makes sense given that I had X11 forwarding until I moved from Xandros to NBR. I will take a look at that thread tho - cheers :-).

---

### Post by anandamide on 2009-05-05
> **geirha said:**
> Well, there you have it. Remove the # in front of the line. # is the comment character. Anything behind # on a line is not treated as a configuration option.

Well now I feel dumb! I was looking at all the # earlier and thinking that it was odd that the config file needed hashes to make it work properly, against every linux convention.

I think we'll put this one down to comedown-induced stupidity after all - many thanks for your patience and help!

Phil

---

### Post by Portmanteaufu on 2009-05-05
> **geirha said:**
> No, we know that the server side has X11 forwarding enabled, because it worked with "ssh -X". It must be some kind of problem with the client-side configuration.

Oops! He did mention that, didn't he? My mistake.

Glad it worked out anyway!

---

### Post by hoogmike on 2009-05-11
try apt-get install xauth and then reboot. did the trick for me.

---

### Post by SadaraX on 2009-09-20
Though this is an old thread, it did help me to discover my problem. Apparently where you put the -X matters in the sequence of arguments.

I was putting mine -X at the end of my argument list, after some port forwarding. It turns out I needed to put it near the front of argument list.

And for what it's worth, the option "ForwardX11 yes" does not work for me, though "x11Forwarding yes" works just fine.

---

### Post by geirha on 2009-09-22
> **SadaraX said:**
> And for what it's worth, the option "ForwardX11 yes" does not work for me, though "x11Forwarding yes" works just fine.

They're both correct, just in different files. 

ForwardX11 is an ssh_config (client-side) option. Setting that to yes in /etc/ssh/ssh_config, will make -X default when you run ssh (i.e. you won't have to specify -X anymore).

X11Forwarding is an sshd_config (server-side) option. That setting must be enabled in /etc/ssh/sshd_config on the server you connect to if you want to be able to use X11 forwarding at all.

```
man ssh_config | grep X11
man sshd_config | grep X11
```

---

