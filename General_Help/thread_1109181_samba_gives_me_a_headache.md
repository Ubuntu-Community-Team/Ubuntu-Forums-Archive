---
title: "samba gives me a headache"
date: 2009-03-28
forum: General Help
---

### Post by Spitphire on 2009-03-28
Hello,

My samba does not appear to be working, it use to work.. but now it doesn't.  My server is called 'lb'.

On the windows client if i type \\lb in the address bar, it shows me what is shared on the linux samba shares..

once i click on one of the shares i get the following error (**see screenshot attached**)

Here is my smb.conf:
```

[global]
    ; General server settings
    netbios name = lb
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[pictures]
    path = /media/tb/pictures/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = am
    force group = am



```

---

### Post by Slim Odds on 2009-03-28
Well, it's clearly an authentication problem.

You share is "guest ok = no", so what is the user name that you're using on your windows machine?

What has changed between the time that it last worked and now? (That's will almost always give you the answer to what when wrong).

---

### Post by eldragon on 2009-03-28
if you want a passwordless access to the shares. you need to add in the global section

guest account = am

and in the shared resource: guest ok = yes

restart samba and you should be able to access.

the force user and force group shouldnt be needed.

---

### Post by HermanAB on 2009-03-28
Here is a Samba debug guide:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

---

### Post by Spitphire on 2009-03-29
> **eldragon said:**
> if you want a passwordless access to the shares. you need to add in the global section

guest account = am

and in the shared resource: guest ok = yes

restart samba and you should be able to access.

the force user and force group shouldnt be needed.


Strangely, this method actually allowed me to access the share.  However; I don't like the idea of my share being accessed openly.

I don't understand what is wrong.  I tried clearing out the saved passwords out of windows client and then retyped them in and it still didn't allow me to connect.

I will go through the debug guide below and see what I can find.

Thanks,
-Spit

---

