---
title: "eroor when trying to install Auromatix"
date: 2007-02-05
forum: Desktop Environments
---

### Post by comodor64 on 2007-02-05
hi
i installed ubuntu 3 days ago and since then i am learning new things
i tryed to install automatix  but an error came up all the time
ia m trying this from a "normal" usre-not the administrator (root?) account
thats the konsole lines:

pixel@omega-desktop:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main" | sudo 
tee -a /etc/apt/sources.list
Password:
pixel@omega-desktop:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--16:10:14--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.5'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s

16:10:15 (527.62 KB/s) - `key.gpg.asc.5' saved [1730/1730]

pixel@omega-desktop:~$ gpg --import key.gpg.asc
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
pixel@omega-desktop:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
gpg: [stdout]: write error: Broken pipe
gpg: iobuf_flush failed on close: file write error
pixel@omega-desktop:~$        

what am i doing wrong?                                   
thanks for your time

---

### Post by true_friend on 2007-02-08
I think u can get better help from GetAutomatix.com.

---

