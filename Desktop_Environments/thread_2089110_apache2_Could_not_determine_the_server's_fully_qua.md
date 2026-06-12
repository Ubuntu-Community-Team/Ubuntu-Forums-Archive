---
title: "apache2: Could not determine the server's fully qualified domain name, ..."
date: 2012-11-28
forum: Desktop Environments
---

### Post by abiodunaremu on 2012-11-28
Hello guys,

Since yesterday, I haven't been able to logon to my Ubuntu desktop. Every attempt to login shows this: "apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 ServerName"

Find my attachment for more details.

I hv already google searched and got some help to do edit the /etc/apache2/httpd.conf file but this is what I get whenever I opened it and even when I finally edited and try saving, I get no permission errors. Later I tried enabling permission but it would tell me "chmod changing permission: ... Read-only system file". Meanwhile, checking the permissions on that file displays: "-rw--r--r...".

I can't login to my system. I am feed up. What else I'm I suppose to do?

---

### Post by pkadeel on 2012-11-28
> **abiodunaremu said:**
> apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 ServerName
Your inability to get to the desktop will not be due to the apache2 warning mentioned in your post. It is just an indication from apache2 that you have not set a ServerName yet.

Apparently you are able to get to the tty as root so to correct the above warning you can do
```

echo "ServerName localhost" >> /etc/apache2/conf.d/fqdn
service apache2 restart

```

---

### Post by CharlesA on 2012-11-28
Technically that message is just informational and pkadeel give you the instructions on how to get rid of that message.

What happens if you run the machine directly off the mains without the battery attached?

---

### Post by abiodunaremu on 2012-11-29
Thank you guys for your responses.

Attached are what I get after executing some commands.

The screen you saw was "Recovery mode". I am trying to see if I could get the problem solved there. I have also attempted 
"Repair broken packages" in the recovery mode.

But the bottom line is still, I can't access my desktop once the logon screen display - and entered my password - and it is not telling me that my password is invalid. Instead, it does as if it is taking me to the desktop but I keep getting back the logon screen.

What do I need to do to access my desktop, apps, etc?

---

### Post by pkadeel on 2012-11-29
> **abiodunaremu said:**
> Thank you guys for your responses.

Attached are what I get after executing some commands.

The screen you saw was "Recovery mode". I am trying to see if I could get the problem solved there. I have also attempted 
"Repair broken packages" in the recovery mode.

But the bottom line is still, I can't access my desktop once the logon screen display - and entered my password - and it is not telling me that my password is invalid. Instead, it does as if it is taking me to the desktop but I keep getting back the logon screen.

What do I need to do to access my desktop, apps, etc?
I suspected that you are trying to run ubuntu in a virtual environment but I didn't ask in my last post.

Now for the scenario is you have a ubuntu install in vmware and you also have apache2 installed which means you are either using ubuntu server edition or if it is a desktop edition then you were previously able to run ubuntu and installed apache2 on it. May be there is something more which you also installed in ubuntu. Which erver is the case, please provide the 

[LIST=1]
[*]ubuntu edition you want to run
[*]vmware settings you are using (I might not be able to help with vmware but many other members here use vmware)
[*]If you were able to run ubuntu earlier then which softwares you installed or uninstalled during last successfull session.
[/LIST]
It is a matter of choice though I personally like and recommend Oracle VirtualBox.

---

### Post by abiodunaremu on 2012-11-29
> **pkadeel said:**
> I suspected that you are trying to run ubuntu in a virtual environment but I didn't ask in my last post.

Now for the scenario is you have a ubuntu install in vmware and you also have apache2 installed which means you are either using ubuntu server edition or if it is a desktop edition then you were previously able to run ubuntu and installed apache2 on it. May be there is something more which you also installed in ubuntu. Which erver is the case, please provide the 

[LIST=1]
[*]ubuntu edition you want to run
[*]vmware settings you are using (I might not be able to help with vmware but many other members here use vmware)
[*]If you were able to run ubuntu earlier then which softwares you installed or uninstalled during last successfull session.
[/LIST]
It is a matter of choice though I personally like and recommend Oracle VirtualBox.


Thank you so much.

I started having this problem after installing updates found in the Ubuntu Software Centre but my apache wasn't giving issue before that.

Though, I have just finished reinstalling Ubuntu again and have been able to logon.

Thank you all for your support.

Cheers

---

