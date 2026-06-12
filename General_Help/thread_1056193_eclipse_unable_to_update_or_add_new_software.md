---
title: "eclipse unable to update or add new software"
date: 2009-01-31
forum: General Help
---

### Post by prokaryot on 2009-01-31
Hi,

I installed eclipse 3.4.1 "ganymede" for linux, then unzipped it. Before I was using older version of eclipse (3.1 or 3.2), I was able to update things. But I need to install a new version of eclipse to install uml add-on. Now I can't update or add new software through update manager. 

I can't find any problem related to in the Internet. What am I doing wrong?

Thank you

---

### Post by Nepherte on 2009-01-31
If you unzipped the new eclipse somewhere other than your home directory, installing a plugin/updating generally requires admin privileges. Try installing/updating the plugin by running eclipse as root:
```
gksudo eclipse
```
Be sure not to run eclipse as root for any other thing than this purpose, that would be a very bad idea.

---

### Post by prokaryot on 2009-01-31
Sorry doesn't that work. I moved eclipse directory to my home directory.

Then I run eclipse via gksudo but nothing changed.

I ran software update manager then clicked on something like "Ganymede Update Site", than it writes "Pending", after 10 minutes or later, it lists something. Then I selected "uml2 and uml2 tools" and "Calculating requirements and dependencies" phase starts.

Then after 10 or 15 minutes when it's in 90% of calculating, I was able to install them. I accepted and clicked install. Now in details there was "install" and "calculating size (cancel requested)".

After 5 minutes I see "Synchronizing task list" at the bottom of the details list.

For about after 45 minutes it still installs... :S

---

### Post by cyber-monk on 2010-05-11
If this is your work machine you might want to make sure your proxy is set.  To set the proxy in **Eclipse 3.5.2** go to:

**"Window > Preferences > General > Network Connections"  **

From this Window you see an "**Active Provider**" drop menu with three  options:  

**Direct**: provider causes all the connections to be opened without the use  of a proxy server.  
**Manual**: causes settings defined in Eclipse to be used. 
**Native**: (On some platforms) causes settings that were discovered in the  OS to be used.

I have a system proxy as well as a settings in my bash file but I selected Manual and entered my proxy (need to change for your proxy):

[FONT=Fixedsys]host=my.proxy.com
port=80[/FONT]

Make sure to enter a proxy for **HTTP** and **HTTPS**.  For my system I didn't  need a proxy for the **SOCKS** protocol.

To ensure that your proxy is working go to:

**"Help > Install New Software > Available Software Sites"** and add  the following location (if not already present):

**[http://download.eclipse.org/releases/galileo/](http://download.eclipse.org/releases/galileo/)**

After clicking "Test Connection" you should see a progress bar and eventually you should get a "**[http://download.eclipse.org/releases/galileo/](http://download.eclipse.org/releases/galileo/) is  available**" message.

NOTE:  I downloaded eclipse manually and unzipped to my home directory, rather  than doing the **apt-get install eclipse-platform** or the **Ubuntu Software Center**  tool.

---

