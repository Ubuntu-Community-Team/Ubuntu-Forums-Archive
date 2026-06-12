---
title: "problem with adding new printer"
date: 2009-03-23
forum: General Help
---

### Post by zikril on 2009-03-23
Hello alll

I have using Ubuntu 8.10 remastered with remastersys. All work properly until i'll want to add new printer in System->Administration->printing. I cannot add printer and i saw new printer button is disable and in the bottom type 'not connected'

[IMG]http://i554.photobucket.com/albums/jj414/zikril_photo/Screenshot.png[/IMG]

I open Server->Connect.. i look the CUPS server type localhost. I change it with /var/run/cups/cups.sock and click connect but error window is appear..

[IMG]http://i554.photobucket.com/albums/jj414/zikril_photo/Screenshot-1.png[/IMG]

[IMG]http://i554.photobucket.com/albums/jj414/zikril_photo/Screenshot-2.png[/IMG]

I try open terminal and type sudo /etc/init.d/cups restart

zikril@zikril-ubuntu:~$ sudo /etc/init.d/cups restart
[sudo] password for zikril: 
 * Restarting Common Unix Printing System: cupsd                                cupsd: Child exited with status 1!
                                                                         [fail]
zikril@zikril-ubuntu:~$ 

it fail..

Have you find like this problem before?? please share how to fix this.. thanks all..

---

### Post by rozbarwinek on 2009-03-23
Edit /etc/cups/cupsd.conf
Paste "**DefaultEncryption Never**" between **<Location> </Location>**
And then restart :)
sudo /etc/init.d/cupsys restart

---

### Post by zikril on 2009-03-24
> **rozbarwinek said:**
> Edit /etc/cups/cupsd.conf
Paste "**DefaultEncryption Never**" between **<Location> </Location>**
And then restart :)
sudo /etc/init.d/cupsys restart

I have try it, i put like this

# Restrict access to the server...
<Location />
 DefaultEncryption Never
 Order allow,deny
</Location>

and restart cups, but still fail...

---

### Post by rozbarwinek on 2009-03-24
This is not the best idea but you try this:

```
sudo rm /etc/cups/ssl/server.crt
```

```
sudo rm /etc/cups/ssl/server.key
```

This will delete to files so I recommend to do backup first :)
I never had such problem so I'm not sure :/

---

### Post by zikril on 2009-03-25
> **rozbarwinek said:**
> This is not the best idea but you try this:

```
sudo rm /etc/cups/ssl/server.crt
```

```
sudo rm /etc/cups/ssl/server.key
```

This will delete to files so I recommend to do backup first :)
I never had such problem so I'm not sure :/

sorry my friend, when i try it, there is no fixed the problem, still fail when i restart cups...

uff..it make me crazy....

---

### Post by rozbarwinek on 2009-03-26
Have you installed all updates? :)

---

