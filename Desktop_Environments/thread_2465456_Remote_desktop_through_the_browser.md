---
title: "Remote desktop through the browser?"
date: 2021-08-02
forum: Desktop Environments
---

### Post by josephchrzempiec on 2021-08-02
Hello, I'm unsure how many people ask this. But a lot of people wondering including myself if it is possible to do a remote desktop through the browser? I know using a remote desktop program like RealVNC or windows remote desktop even teamviewer. But Myself including a lot of people i know are wondering if it is possible in a web browser? 


Joseph

---

### Post by ajgreeny on 2021-08-02
I have never come across this before but a quick search found [https://remotedesktop.google.com/](https://remotedesktop.google.com/) 
This is for Google Chrome that I use only when on Android so can tell you nothing more about it but it could be useful as long as security is good enough, and again, I do not know about that so it will have to be investigated a lot more before you decide whether or not it's for you.

Depending on exactly what you want or need to do have you thought about using X-forwarding using ssh?

---

### Post by scorp123 on 2021-08-02
> **josephchrzempiec said:**
> Hello, I'm unsure how many people ask this. But a lot of people wondering including myself if it is possible to do a remote desktop through the browser? 

Yes. Been there, done that. There are various approaches you could take to achieve this.

I have used _all_ of these at various points in the past:

Chrome Remote Desktop
[https://remotedesktop.google.com/]("https://remotedesktop.google.com/")

NoVNC
[https://novnc.com/info.html]("https://novnc.com/info.html")

Apache Guacamole
[https://guacamole.apache.org/]("https://guacamole.apache.org/")

Cendio ThinLinc
[https://www.cendio.com/thinlinc/download]("https://www.cendio.com/thinlinc/download")

[LIST]
[*]ThinLinc is a commercial product
[*]It is free to use at home for as long as you don't have more than 10 x concurrent users
[*]Good installers, good documentation, easy to get running
[/LIST]

Oracle Secure Global Desktop
[https://www.oracle.com/virtualization/technologies/vm/secure-desktop-overview.html]("https://www.oracle.com/virtualization/technologies/vm/secure-desktop-overview.html")

[LIST]
[*]Secure Global Desktop is a commercial ($$$) Enterprise product
[*]Can be VERY pricey ($$$)
[*]Very long list of Enterprise features, e.g. failover array, integration into LDAP, Active Directory, and what not
[*]Excellent documentation
[*]You need a server OS such as Oracle Solaris, Red Hat Enterprise Linux or Oracle Linux to run this
[*]Requires you to have an "Oracle Login" to download the packages
[*]Requires you to have a valid support ID to download patches for this software
[/LIST]


Then there's this one.  I have never used this myself and can't tell you if it's "good" or not. I just know that it exists.

DWService
[https://www.dwservice.net/en/home.html]("https://www.dwservice.net/en/home.html")

[LIST]
[*]Supposedly "very simple" to use??
[*]Seems to be a cloud service, you only install an agent into your desktop machine... [https://www.dwservice.net/en/overview.html]("https://www.dwservice.net/en/overview.html")
[/LIST]

---

### Post by ActionParsnip on 2021-08-03
One side question though is why are you connecting to the remote system in such a way? What are you doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve......

---

### Post by TheFu on 2021-08-03
A remote desktop over a browser connection adds a huge layer of security risks.  HTTPS has lots of issues, unless you get everything perfect.  TLS versions under 1.3 have all been cracked, for example.  Better to limit that security issue by avoiding browsers for this need, when ssh + X/Windows can accomplish the same things.  Every workstation should have both of those capabilities, so there isn't anything new to install.  Just a few config lines (which are the defaults already) should be added.  Securing ssh is required and a well-traveled path with plenty of how-to articles.

---

### Post by scorp123 on 2021-08-03
> **TheFu said:**
> A remote desktop over a browser connection adds a huge layer of security risks. 

Totally agree. If I had to implement something like this these days I'd do it with **X2go** and SSH keys. Having access to your desktop environment via a browser is in theory "nice" and all that but you are at the same time opening a huge can of worms.

The only area where I could see a potential benefit if you do browser-based desktops is e.g. if you do it in an Intranet-only setting and all your client devices are in fact some kind of thin clients that only have a browser locally installed. But this means you'd also need to have the required computational firepower on the server side to handle x-100 simultaneous user desktops and are able to deal with the CPU-, RAM- and storage-requirements such a setup comes with. Been there, done that.  Such a scenario is only really interesting for very large companies.

---

### Post by TheFu on 2021-08-03
Agreed, but I'd go with TinyCore Lite and x2go for a desktop.  

Plus, there are efficiencies when end-users are running their desktops on the same system. A week after they move over, I show them how to share files between their userids and setup a directory area for each team to use for their work.  Those teams quickly stop using their HOME directories for work files and start using the shared storage area.  Then they learn to use collaboration-capable tools which allow multiple people to edit the same document concurrently, showing live modifications to everyone.  This is where people running personal computers, alone, outside a team environment really have no clues.  They often thing they need to copy files around, because that's the way they did it on Windows.

It doesn't take long, but until they are shown the capabilities, as they are ready to learn, then they will do it the same old, slower, way.

---

