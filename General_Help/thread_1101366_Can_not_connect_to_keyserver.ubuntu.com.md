---
title: "Can not connect to keyserver.ubuntu.com"
date: 2009-03-20
forum: General Help
---

### Post by bohn002 on 2009-03-20
I am trying to add keys to my update manager so I can continue to get stuff from PPA, but the connection to the keyserver.ubuntu.com keep timing out. I kinda figure its my works firewall. Is it using a special port? I tried pinging in firefox and terminal and getting timeouts.

Well the site doesnt seem to be blocked here at work, but I am going to try my machine at home.

---

### Post by bohn002 on 2009-03-20
looks like my firewall is blocking port #11371

---

### Post by Dr Small on 2009-03-20
Actually, not too long ago, I wasn't able to connect either. It seemed to me as if the server was having connection problems.

---

### Post by MeanEYE on 2009-04-27
I had a same problem. In my case I was behind a firewall. You can simply set any proxy in your browser until you download key file. 

For all those who need PPA key files I have downloaded for Blueman and Shiki-Colors. 

Just ask :D

---

### Post by SirSeptember on 2009-11-10
I've been trying to add the gpg keys for Karmic, however I've been getting server time outs whilst trying to access keyserver.ubuntu.com... Is the server still down? Does anyone know of a working mirror that I can access the keys from?

Cheers

Never mind, I tried at home all is working damn firewalls.

---

### Post by caio2112 on 2010-10-29
In case you are using a command that uses port 11371 by defaut like:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com <key>

you can force it to use port 80, that is usually not blocked:
sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 <key>

---

### Post by netJackDaw on 2010-10-29
Is there a simple way to make the script "add-apt-repository" to use port 80 rather than 11371 for this as well?

---

### Post by jzaruba on 2011-01-24
> **netJackDaw said:**
> Is there a simple way to make the script "add-apt-repository" to use port 80 rather than 11371 for this as well?
I assume you already figured that out but you can add the repository using Synaptic and download the key later as suggested above. At least that's how it has worked for me.

---

