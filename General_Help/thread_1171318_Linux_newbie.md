---
title: "Linux newbie"
date: 2009-05-27
forum: General Help
---

### Post by ebenfourie on 2009-05-27
I'm trying to install some apps on ubunto and get the following : 

eben@eben-laptop:~$ su
Password: 
root@eben-laptop:/home/eben# apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                                   
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_ZW                                        
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_ZW                                  
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_ZW                                    
  Unable to connect to security.ubuntu.com http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_ZW                                  
  Unable to connect to security.ubuntu.com http:
Err [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) jaunty Release.gpg                                                          
  Could not connect to zw.archive.ubuntu.com:80 (155.232.191.229), connection timed out
Err [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) jaunty/main Translation-en_ZW
  Unable to connect to zw.archive.ubuntu.com http:
Err [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) jaunty/restricted Translation-en_ZW
  Unable to connect to zw.archive.ubuntu.com http:
Err [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) jaunty/universe Translation-en_ZW
  Unable to connect to zw.archive.ubuntu.com http:
Err [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) jaunty/multiverse Translation-en_ZW
  Unable to connect to zw.archive.ubuntu.com http:
Err [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) jaunty-updates Release.gpg
  Unable to connect to zw.archive.ubuntu.com http:
Err [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) jaunty-updates/main Translation-en_ZW
  Unable to connect to zw.archive.ubuntu.com http:
Err [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) jaunty-updates/restricted Translation-en_ZW
  Unable to connect to zw.archive.ubuntu.com http:
Err [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) jaunty-updates/universe Translation-en_ZW
  Unable to connect to zw.archive.ubuntu.com http:
Err [http://zw.archive.ubuntu.com](http://zw.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_ZW
  Unable to connect to zw.archive.ubuntu.com http:
Reading package lists... Done                             
W: Failed to fetch [http://zw.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://zw.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to zw.archive.ubuntu.com:80 (155.232.191.229), connection timed out

W: Failed to fetch [http://zw.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_ZW.bz2](http://zw.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_ZW.bz2)  Unable to connect to zw.archive.ubuntu.com http:

W: Failed to fetch [http://zw.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_ZW.bz2](http://zw.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_ZW.bz2)  Unable to connect to zw.archive.ubuntu.com http:

W: Failed to fetch [http://zw.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_ZW.bz2](http://zw.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_ZW.bz2)  Unable to connect to zw.archive.ubuntu.com http:

W: Failed to fetch [http://zw.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_ZW.bz2](http://zw.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_ZW.bz2)  Unable to connect to zw.archive.ubuntu.com http:

W: Failed to fetch [http://zw.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://zw.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Unable to connect to zw.archive.ubuntu.com http:

W: Failed to fetch [http://zw.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_ZW.bz2](http://zw.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_ZW.bz2)  Unable to connect to zw.archive.ubuntu.com http:

W: Failed to fetch [http://zw.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_ZW.bz2](http://zw.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_ZW.bz2)  Unable to connect to zw.archive.ubuntu.com http:

W: Failed to fetch [http://zw.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_ZW.bz2](http://zw.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_ZW.bz2)  Unable to connect to zw.archive.ubuntu.com http:

W: Failed to fetch [http://zw.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_ZW.bz2](http://zw.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_ZW.bz2)  Unable to connect to zw.archive.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_ZW.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_ZW.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_ZW.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_ZW.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_ZW.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_ZW.bz2)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_ZW.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_ZW.bz2)  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
root@eben-laptop:/home/eben# 


Can you please help me with this?

---

### Post by deadlockedgamer on 2009-05-27
Go to administration software sources and make sure everything is checked. Then it may ask to reload when you close. let it reload and when it is done it will close by it's self. Then go to add remove and at the top change it to all available. Then check all programs you want and click apply. This is how you get most programs you want. (Please note this requires internet and i assume you are connected) Also what version are you using?

---

### Post by Soul-Sing on 2009-05-27
Systeem: software sources: try another server, this one isn't working.

Try using ```
sudo
``` instead of ```
su
```. ```
sudo
``` is the "ubuntuway"...:D

---

### Post by deadlockedgamer on 2009-05-27
Or if I misunderstood and you are trying to install the os just don't use wubi.

---

### Post by pastalavista on 2009-05-27
First of all, it looks like you aren't connected to the internet. Programs need to be downloaded from the repositories before they can be installed. Unless you are, connected, then it means your package server isn't. Rather than use the terminal, try using Add/Remove in the Applications menu or Synaptic Package Manager in the System->Administration menu. In the Synaptic settings, you can check the repositories (Software Sources) and automatically select the best (fastest) one for you.

---

### Post by ebenfourie on 2009-05-27
> **deadlockedgamer said:**
> Go to administration software sources and make sure everything is checked. Then it may ask to reload when you close. let it reload and when it is done it will close by it's self. Then go to add remove and at the top change it to all available. Then check all programs you want and click apply. This is how you get most programs you want. (Please note this requires internet and i assume you are connected) Also what version are you using?

I get the same response, that i cant connect. I have my laptop at work and i cab connect to the internet via the browser, if i put in the correct proxy settings and type in my n/w credentials (for access to the internet)

---

### Post by HereInOz on 2009-05-27
If your laptop is at work, I wonder if your IT administrators are blocking something.  

Are you able to enter

[http://zw.archive.ubuntu.com/](http://zw.archive.ubuntu.com/)

in a browser address bar and get a folder list of that site?  If you can, it means that you can indeed connect to it, so there must be another reason, possibly related to your work network environment.

Just a guess but could be worth thinking about.

---

### Post by ebenfourie on 2009-05-27
> **HereInOz said:**
> If your laptop is at work, I wonder if your IT administrators are blocking something.  

Are you able to enter

[http://zw.archive.ubuntu.com/](http://zw.archive.ubuntu.com/)

in a browser address bar and get a folder list of that site?  If you can, it means that you can indeed connect to it, so there must be another reason, possibly related to your work network environment.

Just a guess but could be worth thinking about.

Yes, I can connect. Like i said, if i open my browser i have to type my n/w credentials to authenticate to get internet access. Is there i way to configure or get past this so that when i want to connect without my browser i will still be authenticated. Dont know if i make any sence?

---

### Post by ebenfourie on 2009-05-27
Thanx, just figured it out. Just had to look. :) I saw in package manager there is an option to put in my proxy settings, working perfect now.:p

---

### Post by pastalavista on 2009-05-27
> **ebenfourie said:**
> Yes, I can connect. Like i said, if i open my browser i have to type my n/w credentials to authenticate to get internet access. Is there i way to configure or get past this so that when i want to connect without my browser i will still be authenticated. Dont know if i make any sence?

If you can connect with the browser, keep the browser open while running the updates and installs. Or maybe you could do the authentication setup in network manager...

---

