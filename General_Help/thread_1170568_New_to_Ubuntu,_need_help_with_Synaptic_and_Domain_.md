---
title: "New to Ubuntu, need help with Synaptic and Domain Proxy Server"
date: 2009-05-26
forum: General Help
---

### Post by davemarker on 2009-05-26
Well, as the title says, I'm new to Ubuntu. I tried out V8.04 and V8.10 a while back and had the same problems that I have with 9.04 now.  At work where I'm trying this out we're on a domain and have an ISA proxy server.  I can enter my proxy server information into firefox and it prompts me for a username and password when I try to hit the internet. That all works as I'm used to.  However, when I load up synaptic and try to add the http proxy and my credentials, it fails to authenticate with the proxy server and as a result I can't get updats for the package list.

It appears my google skills are lacking, as I haven't had much luck finding a solution.  I've tried this, which a coworker found and forwarded me:
> [SIZE=1]ssh -fND1080 myusername:mypassword@mywindozisaclientname
(myusername and mypassword must be an account for Windoz with ISA client)

So I create a dynamic port forwarding (ssh behaves as a socks server).

I configure my mail client program (PROXY SOCKS = localhost , PORT = 1080)[/SIZE]This didn't work and I also tried to follow the directions here: [http://ubuntuforums.org/showthread.php?t=765330&highlight=domain+proxy+server](http://ubuntuforums.org/showthread.php?t=765330&highlight=domain+proxy+server)
That just bombed out on the first line of code.

I also tried a line involving the export command, but I can't find the page I found it on (it's been a rough day).

I'm really hoping someone can help me with this, I'm a desktop support technician where I work and can handle windows fine, I'm just clueless with linux.

Edit:
The same coworker that sent me the above quote just sent me this link: [http://www.linux-tutorial.info/modules.php?name=Howto&pagename=Web-Browsing-Behind-ISA-Server-HOWTO/Web-Browsing-Behind-ISA-Server-HOWTO-4.html](http://www.linux-tutorial.info/modules.php?name=Howto&pagename=Web-Browsing-Behind-ISA-Server-HOWTO/Web-Browsing-Behind-ISA-Server-HOWTO-4.html)

I was able to download the tar.gz to my desktop, unpack it to my desktop, edit the config file and start it up. It worked and after configuring my local host as the proxy server in Synaptic I was able to update my package list.  That being said, is there a way to have this automatically run at startup?

---

### Post by raymondh on 2009-05-26
Hello Davemarker,

I hope this tutorial and this link (thread) can help you

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

[http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)

The second link is for ubuntu servers but you may get clues/hints as well

Good Luck and regards,

---

### Post by davemarker on 2009-05-26
Raymond,

Thanks for the help. I tried to add the following to the Synaptic Package Manager:

Per the instructions in the first link, I changed the connection settings from Direct Connection to the Internet to Manual proxy configuration and I used the following:

for HTTP proxy: DomainUsername:MyPassword@ProxyServer.my.full.domain.name
I didn't put anything in the FTP proxy.

I received errors from Synaptic when it tried to access the packages

---

### Post by raymondh on 2009-05-26
> **davemarker said:**
> 

I received errors from Synaptic when it tried to access the packages

Can you quote or post the synaptic errors?  That can give us clues/directions to take.

Regards,

---

### Post by davemarker on 2009-05-26
> **raymondhenson said:**
> Can you quote or post the synaptic errors?  That can give us clues/directions to take.

Regards,

Sure, no problem. I've deleted out my actual username, password, and proxy server.FQDN information for the sake of where I work.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Name'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'username:MyPassword@Server.My.Full.Domain.Names'

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by davemarker on 2009-05-26
In addition, if I just put servername.my.full.domain.name into the server box, put the port as 8080 then I get http 407 errors from synaptic. I've also tried using the authentication button and adding a variety of username password combinations in there. I don't know what the syntax is for adding a domain name to the username, so I don't know how to set that up.

---

