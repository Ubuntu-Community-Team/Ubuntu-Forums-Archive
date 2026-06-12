---
title: "Automatic proxy configuration url and Synaptic"
date: 2007-07-30
forum: Desktop Environments
---

### Post by leo246 on 2007-07-30
Hi guys & girls

I recently installed Ubuntu 7 Fiesty on a pc at work.  I need to use a proxy to get out to the net.  I have configured Firefox accordingly, and seems to work fine.  

I am now trying to update Ubuntu, but get the following msg:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_GB.bz2)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

I use the proxy in Firefox as follows:

[http://*domain_name.com](http://*domain_name.com)*/proxy.pac

Could anyone advise on the settings I need to change in order to update?

Thanks
Leo

---

### Post by strabes on 2007-07-30
Add this line into your ~/.bashrc:

```
export http_proxy "http://domain_name.com/proxy.pac"
```

Then run ```
source ~/.bashrc
```

---

### Post by izhar81 on 2007-11-29
> **strabes said:**
> Add this line into your ~/.bashrc:

```
export http_proxy "http://domain_name.com/proxy.pac"
```

Then run ```
source ~/.bashrc
```

what is ~/.bashrc. anyway?

Here is my problem

I'm using feisty
My workplace are using Automatic Proxy Configuration URL to connect to internet.

I had put the Automatic Proxy onfiguration on System > Preference > network Proxy

Then i configure firefox and put the Automatic Proxy Configuration url too.. but firefox still won't connect.

Then I install Opera from a thumbdrive and i put the Automatic proxy Configuration URL in Opera menu and guess what ? I now can surf the internet using Opera Browser

But .. Firefox remain cannot surf out.

My main problem here is i cannot update my Ubuntu using Synaptic too, because there is no room for me to set up Automatic Proxy Configuration in Synaptic's preferences..

The question is :

How can i get use of my Synaptic if the only infromation i know is Automatic Proxy Configuration URL. I dont know how to connect manually because i know nothing about network. My system admin said they can just give me the Automatic Proxy Configuration to all user..

Please help me..

Thank you very much for anyone who want to help me

---

### Post by joers on 2008-07-06
The advice given, earlier in this forum looks wrong:
   export http_proxy "http://domain_name.com/proxy.pac"
Lets just say I wrote too many shell scripts in my life.

We happen to have one of those .pac proxies on our network and this syntax works for me:

   export http_proxy="http://domain_name.com/proxy.pac"

NOTE the little '='   :)

(Of course, I am using bash shell for my command line. For somebody using a different shell the syntax would have to be adapted appropriately. my 5 cents worth...)

joers

---

