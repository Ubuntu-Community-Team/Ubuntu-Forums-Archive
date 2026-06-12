---
title: "nautilus wont ssh"
date: 2009-04-10
forum: General Help
---

### Post by pavel989 on 2009-04-10
hello everyone,

I keep trying to ssh to my server box through nautilus, and i can't. it wont let me, where as using a terminal i can do it freely.

on this box i set the default ssh port to 35, could that interfere with nautilus defaults?

im doubtful of that because i specify for it to connect to port 22 when i try.

any ideas?

---

### Post by ibuclaw on 2009-04-10
Have you tried it with the IP address of the Server?

ie:
```
ssh://192.168.4.80
```

And have you tried it by specifying a port?
```
ssh://192.168.4.80:35
```

Regards
Iain

---

### Post by pavel989 on 2009-04-10
i only use IP, and yes ive tried specifiying the port too.

---

### Post by cariboo on 2009-04-10
Can you connect using a terminal?

Jim

---

### Post by ibuclaw on 2009-04-10
> **cariboo907 said:**
> Can you connect using a terminal?

Jim
> **pavel989 said:**
> I keep trying to ssh to my server box through nautilus, and i can't. it wont let me, **where as using a terminal i can do it freely.**


Yes, he can connect using a terminal.


pavel989, how do you connect to the server in the terminal?

also, shot in the dark, but try this in the terminal:
```
nautilus ssh://**192.168.1.1**
```
using the IP of the server instead, that is, and see if any information is outputted into the console upon the failure.

Regards
Iain

---

### Post by lavinog on 2009-04-10
I find that adding your server settings to ~/.ssh/config reduces some issues
```

Host MYhost1 Otheralias
 HostName ###.###.###.###
 port ###
 user XXXXXXX
 ForwardX11 true
 ServerAliveInterval 300

Host Lappy486
 HostName ###.###.###.###
 port ###
 user XXXXXXX
 ForwardX11 true
 ServerAliveInterval 300

```

---

### Post by Yashiro on 2009-04-10
sftp://yourname@192.168.4.80:35/home

If that doesn't work something is messed up.

---

### Post by pavel989 on 2009-04-12
> **Yashiro said:**
> sftp://yourname@192.168.4.80:35/home

If that doesn't work something is messed up.

it never did, i used psftp, from putty.

Ima try to add my server settings to ~/.ssh/config

also, running nautilis ssh://...

doesnt work. it gives me an error, and on top of that, it gives me an error about sftp. not ssh, idk if that matters.

---

### Post by Yashiro on 2009-04-12
If you enter an ssh bookmark into nautilus it converts it to sftp anyway. That link I provided is basically a copy of what was in my address bar to my server. So the syntax is correct. Perhaps something with your system is not right. Try setting the port back to 22 in the sshd config.

You can try a slightly more involved method. Install 'sshfs'.
Then using a terminal you can mount the server with something like:
> mkdir /home/yourname/Public/ssh
sshfs yourname@192.168.4.80:/home /home/yourname/Public/ssh

If you open nautilus now it should be there in the side bar with the rest of your drives.

---

### Post by pavel989 on 2009-04-12
> **Yashiro said:**
> If you enter an ssh bookmark into nautilus it converts it to sftp anyway. That link I provided is basically a copy of what was in my address bar to my server. So the syntax is correct. Perhaps something with your system is not right. Try setting the port back to 22 in the sshd config.

You can try a slightly more involved method. Install 'sshfs'.
Then using a terminal you can mount the server with something like:


If you open nautilus now it should be there in the side bar with the rest of your drives.

that sounds kinda kool, i think ima just try the sshfs

---

### Post by HermanAB on 2009-04-12
I think you got the syntax wrong.  Try this:
$ nautilus sftp://johndoe@1.2.3.4:35

---

