---
title: "Port 80 closed after upgrade from Hardy Heron to Lucid Lynx"
date: 2010-05-24
forum: Desktop Environments
---

### Post by airballrad on 2010-05-24
Hi All,
 
I have been searching, but haven't found anything to help me address this. I had an install of 8.04 running Tomcat 6 on port 80. I did a marathon upgrade session to 8.10, then 9.04, then 9.10, and finally to 10.04. My website no longer loads (from Internet, LAN, or local), and a port scan shows port 80 is not open. I have removed and reinstalled Tomcat 6, to no avail. 
 
Could it be that the 10.04 upgrade saw an existing Desktop install and locked this port down? The /etc/Tomcat6/server.xml shows it is using port 80, so that much appears to be correctly configured. Before this would give me the ROOT webapp. Anything else I can check? Does this sound like a Tomcat problem or something Ubuntu is doing?
 
As a side note, I have installed the Tomcat 6 Docs and Manager apps as well. These also worked before the upgrades, and do not now.
 
Many thanks for your assistance.

---

### Post by CraigInAustin on 2010-06-16
**Authbind is now the standard method for binding Tomcat to ports  lower than 1024.** There is a new option (disabled by default) to  enable authbind in /etc/default/tomcat6. Enabling authbind  means that Tomcat will be allowed to bind to privileged ports, if Tomcat  or its webapps are configured to do so, and if authbind is configured  to allow it. Enabling authbind also presumes the use of IPv4, since  authbind only works with IPv4. The permission for Tomcat to use  privileged port numbers is now configured at Tomcat package install  time. Tomcat itself can be run entirely as an unprivileged user for this  reason, tightening the scope of escalated privileges, improving server  security.

See jasonb's blog at mulesoft. If you look at the tomcat6 daemon he is the one who last updated it for Ubuntu and that is where I copied the above text from. NOTE, I had a problem as well on Ubuntu 10.04 LTS with Tomcat6 using the Ubuntu managed installer until I uncommented the "authbind" statement in /etc/default/tomcat6 and changed it to "yes" from "no". Sure enough it worked.

Craig

---

### Post by airballrad on 2010-06-16
Thanks for the reply!

I should have come in here and updated the thread a couple weeks ago. I resolved the matter by uninstalling Tomcat and installing Apache, because that's really all I needed anyway. I can't remember what inspired me to use Tomcat in the first place, to be honest, since it was only a little static site.

I do appreciate the reply, though. I couldn't find an answer, let alone one so cogent, and I'm sure it being here will be helpful to others in the future. Possibly me, if I install Tomcat again and forget why I couldn't get it to open port 80...

---

