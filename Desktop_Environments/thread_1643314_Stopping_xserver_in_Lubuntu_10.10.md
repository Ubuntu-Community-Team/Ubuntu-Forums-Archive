---
title: "Stopping xserver in Lubuntu 10.10"
date: 2010-12-11
forum: Desktop Environments
---

### Post by whatthefunk on 2010-12-11
```
sudo /etc/init.d/gdm stop
```
 
This code isnt working.  I get "command not found."  Does anybody know the correct code?

---

### Post by hecnabae on 2010-12-13
> **whatthefunk said:**
> ```
sudo /etc/init.d/gdm stop
```This code isnt working.  I get "command not found."  Does anybody know the correct code?
Try:
sudo /etc/init.d/lxdm stop

---

### Post by cavalier911 on 2010-12-13
**Lubuntu 10.04 LTS **default install has lxdm and upstart.

lxdm starts X server, if you stop lxdm it stops X server,this will drop you to console single user mode logon prompt,after logon run the start lxdm command to start X server
if you restart lxdm it will stop X server drop to console then start X server without any additional commands. 

```
sudo service lxdm stop
```

```
sudo service lxdm start
```

```
sudo service lxdm restart
```

---

### Post by rklapp on 2011-04-26
Lxdm tells me that it doesn't recognize stop. Gdm gives me a blank cursor screen and the keyboard locks up.

---

### Post by cavalier911 on 2011-04-27
I don't run Lubuntu 10.10 but these are alternate commands that work on my 10.04 and may work on 10.10 

```
sudo initctl status lxdm
```
```
sudo initctl stop lxdm
```
```
sudo initctl start lxdm
```
```
sudo initctl restart lxdm
```

Who knows maybe they work on 11.04 that is released tomorrow?

---

### Post by Yellow Pasque on 2011-04-27
> **rklapp said:**
> Lxdm tells me that it doesn't recognize stop. Gdm gives me a blank cursor screen and the keyboard locks up.

If you're using gdm, then cavalier911's service commands should work with gdm in place of lxdm.
EDIT: Oh,you just need to press Ctrl+Alt+F1 or F2 to get to another virtual terminal.

---

