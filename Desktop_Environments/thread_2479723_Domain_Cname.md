---
title: "Domain Cname"
date: 2022-10-04
forum: Desktop Environments
---

### Post by Geoff_Lane on 2022-10-04
This is not an Ubuntu issue but hoping some knowledgeable folk may enlighten me.

I run a small web server for personal and family use on my network using apache, all works fine.  

I am trying to understand Cnames on DNS management.  Do any additional Cnames resolve to the root directory or do they need an additional html file like the index.html

Reason I ask is that my FQD brings up my index.html page as expected, I added www as a Cname and this resolves to the same location but for test purposes I added a further Cname 3lanes and this shows up on [https://dnschecker.org](https://dnschecker.org) as enabled but does not resolve to my web page, I get error 404 page not found.

I've read up a few web pages and watched a couple of YouTube videos but none hint at a different location for any files.

Error 404 suggests another location within the web site needs to be available.

Appreciate if anyone can enlighten me.

Geoff

---

### Post by &amp;KyT$0P# on 2022-10-04
You need to add your CNAME alias domain to your Apache configuration as a hostname for your site, so that your Apache knows to serve your site for requests it receives for content on that domain.  Sorry I don't know specifics of how (I use nginx and my server isn't even Debian-based anymore).

---

### Post by SeijiSensei on 2022-10-04
Somewhere you have an Apache configuration file for your site. On Ubuntu, the Apache configuration files live in /etc/apache2/sites-available/. "Enabled" sites, which actually handle requests, are created by using the command "sudo a2ensite sitename" which creates a symbolic link in the /etc/apache2/sites-enabled/ directory to the corresponding file in /sites-available/ 

I don't know where your site is located, perhaps a modified /etc/apache2/sites-available/000-default.conf. In the configuration file for your site, you should have something like
```

<VirtualHost *:80>
ServerName     yourdomain.com
ServerAlias    www.yourdomain.com, your.other.domain.com
...
</VirtualHost>

```
There should also be a similar declaration with "<VirtualHost *:443>" if you maintain an encrypted site with an SSL certficate.

Apache looks at the request it received from the client and compares the host part to the ones defined in those ServerName or ServerAlias declarations. If there is no match, Apache returns the default page. So check and make sure every name you want your site to respond to in the ServerAlias statement.

Adding a CNAME or A record to your DNS tells users the host on which your site is located. You also have to tell Apache to respond to any requests it receives.

---

### Post by mIk3_08 on 2022-10-04
If the custom nameservers you mean under the reverse dns it could be something like this;
The ns1 will be the primary and the ns2 will be the secondary dns this will be pointing domain methods. Regards and cheers
```

@    IN    NS    ns1.yourservername.net. (sample dns domain name primary)
@    IN    NS    ns2.yourservername.net.(sample dns domain name secondary)


yourservername.net.    IN    MX     10    yourservername.net
yourservername.net.    IN    A    108.61.202.229

ns1            IN    A    173.199.96.96 (sample dns ip primary)
ns2            IN    A    173.199.96.97(sample dns ip secondary)
www            IN    CNAME    yourdservername.net
mail            IN    A    108.61.202.229
ftp            IN    CNAME    yourservername.net
```

---

### Post by Geoff_Lane on 2022-10-05
> **halogen2 said:**
> You need to add your CNAME alias domain to your Apache configuration as a hostname for your site, so that your Apache knows to serve your site for requests it receives for content on that domain.

Thanks, I'm slowly getting to grips with apache configs.  Managed to get a reverse proxy to work along with a working ssl certificate but haven't quite got these sub domains worked out.  Can do it using different port numbers though.

Geoff

---

### Post by Geoff_Lane on 2022-10-05
> **SeijiSensei said:**
> Somewhere you have an Apache configuration file for your site. On Ubuntu, the Apache configuration files live in /etc/apache2/sites-available/. "Enabled" sites, which actually handle requests, are created by using the command "sudo a2ensite sitename" which creates a symbolic link in the /etc/apache2/sites-enabled/ directory to the corresponding file in /sites-available/ 

I don't know where your site is located, perhaps a modified /etc/apache2/sites-available/000-default.conf. In the configuration file for your site, you should have something like
```

<VirtualHost *:80>
ServerName     yourdomain.com
ServerAlias    www.yourdomain.com, your.other.domain.com
...
</VirtualHost>

```
There should also be a similar declaration with "<VirtualHost *:443>" if you maintain an encrypted site with an SSL certficate.

Apache looks at the request it received from the client and compares the host part to the ones defined in those ServerName or ServerAlias declarations. If there is no match, Apache returns the default page. So check and make sure every name you want your site to respond to in the ServerAlias statement.

Adding a CNAME or A record to your DNS tells users the host on which your site is located. You also have to tell Apache to respond to any requests it receives.


Thanks, that has pointed me in the right direction.

My Apache runs on a Raspberry-Pi so is debian based.  I have, merely for practice purposes, created a second and third site using different ports but haven't yet managed using a Cname.  I do have a FQD but no fixed IP for my site so use [https://www.noip.com/](https://www.noip.com/) that gives me a domain name that points to a dynamic IP.   My FQD has a cname that points to that and it actually works quite well.

Fortunately the Ubuntu laptop is my main system and makes managing the ssh to the web site easy.

Geoff

---

### Post by Geoff_Lane on 2022-10-05
Further to my original post and the interesting replies, thank you.

What is puzzling me, if my FQD brings up my index.html page and my www cname also brings up the same index.html page why doesn't the extra cname of 3lanes not bring up the same index.html page?   It is after all pointing to my default FQD

Geoff

---

### Post by SeijiSensei on 2022-10-06
Probably because somewhere in the configuration there's a <VirtualHost> declaration for "www" but none for "3lanes."

I'd dump the separate ports and learn how to create "name-based" virtual hosts. [https://phoenixnap.com/kb/how-to-set-up-apache-virtual-hosts-ubuntu](https://phoenixnap.com/kb/how-to-set-up-apache-virtual-hosts-ubuntu)

I'm pretty sure everything is the same between Ubuntu and Debian when it comes to configuring Apache.

---

### Post by Geoff_Lane on 2022-10-07
> **SeijiSensei said:**
> Probably because somewhere in the configuration there's a <VirtualHost> declaration for "www" but none for "3lanes."

I'd dump the separate ports and learn how to create "name-based" virtual hosts. [https://phoenixnap.com/kb/how-to-set-up-apache-virtual-hosts-ubuntu](https://phoenixnap.com/kb/how-to-set-up-apache-virtual-hosts-ubuntu)

I'm pretty sure everything is the same between Ubuntu and Debian when it comes to configuring Apache.

Thanks, that looks an excellent link you provided.  I shall backup my current setup and restart trying the name based options.

Geoff

---

