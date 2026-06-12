---
title: "Main Admin Tool"
date: 2006-07-27
forum: Desktop Environments
---

### Post by Geffers on 2006-07-27
As a previous user of mandrake a few years back I got quite au faix with the configuration tools to alter settings.

I need to set up file and printer sharing but am going round in circles, I cannot get Samba SWAT to work, neither can I get Webmin to work, the latter always reporting an incorrect log in details and SWAT telling me it cannot connect.

I need to be able to see a list of running servers/services and be able to start or restart but cannot find the utility to do this on Gnome, K Desktop's System Settings appears better than anything I can find on Gnome but still not as good as I recall on Mandrake.

Any suggestions would be appreciated.

Geffers

---

### Post by ifokkema on 2006-07-29
Does System=>Administration=>Services do what you want?

---

### Post by w_r_cromwell on 2006-07-29
Hi,

System -> Admin -> Services doesn't do much on my system. It shows a few of the services but does not allow stop/start/restart/configure. This is in the Breezy section so I assume we are all talking about the same version.

On RedHat there was a service command. On my Ubuntu boxes I have learned to use sudo /etc/init.d/<service> stop/start/restart. "ps -A" will give you some of the information you want about services and other jobs that are running.

My Sys/Admin/Shared Folders stopped working one fine day. I resorted to manual configuration of my smb.conf file in /etc/samba to add new shares. I posted here about that issue but nobody has an answer. I have a slow <SLOW!!> dialup connection to the net. I have not done very many updates....its very painful. That might resolve the issues.

If you update and your tools still don't work you will probably have to go around the broken applets and use the tried and true command line. There are man pages for all of these. Hope this helps

Bill

---

### Post by ifokkema on 2006-07-29
> **w_r_cromwell said:**
> Hi,

System -> Admin -> Services doesn't do much on my system. It shows a few of the services but does not allow stop/start/restart/configure. This is in the Breezy section so I assume we are all talking about the same version.
It allows you to stop/start services by clicking the checkboxes next to the services. It may not be much, but it's something.

---

### Post by Geffers on 2006-07-29
> **w_r_cromwell said:**
> Hi,

System -> Admin -> Services doesn't do much on my system. It shows a few of the services but does not allow stop/start/restart/configure. 


I'm not in Linux at the moment so cannot check but I did look at that one and don't recall it being too helpful either.

> 
On my Ubuntu boxes I have learned to use sudo /etc/init.d/<service> stop/start/restart. "ps -A" will give you some of the information you want about services and other jobs that are running.


Yes, I think I'm going to have to do similar.

> 

There are man pages for all of these. Hope this helps

Bill

Yes, thanks.

I have resolved the Webmin/Samba issue through this forum so there is light at the end of the tunnel :D 

Geffers

---

### Post by Geffers on 2006-07-31
> **ifokkema said:**
> It allows you to stop/start services by clicking the checkboxes next to the services. It may not be much, but it's something.

Strangely I had a closer look and managed to stop and restart some services but I'm having problems with CUPS, it shows as started at boot but STOPPED.

Tried a restart but the status does not alter :( 

Geffers

---

### Post by ifokkema on 2006-07-31
> **Geffers said:**
> Strangely I had a closer look and managed to stop and restart some services but I'm having problems with CUPS, it shows as started at boot but STOPPED.

Tried a restart but the status does not alter :( 

Geffers
Do you get an error message when (re)starting it from the console?
```
sudo /etc/init.d/cupsys restart
```

---

### Post by Geffers on 2006-08-02
> **ifokkema said:**
> Do you get an error message when (re)starting it from the console?
```
sudo /etc/init.d/cupsys restart
```

Not in Linux at time of reading this but I will give it a try.

Thanks for suggestion.

Geffers

---

