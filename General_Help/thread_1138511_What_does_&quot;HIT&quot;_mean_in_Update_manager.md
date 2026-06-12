---
title: "What does &quot;HIT&quot; mean in Update manager?"
date: 2009-04-26
forum: General Help
---

### Post by AlexBellisBrown on 2009-04-26
I upgraded to jaunty from 8.10 a day before the release, and all is working perfectly except for 2 things. 

First:

Updates seem to have stopped, i dont think this is normal, but who knows, i was expecting updates every day to be honest... but its been 4 days and not 1! I get this in terminal, what does Hit mean? Is it the same as failed?

alex@alex-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty Release.gpg                           
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Translation-en_US                
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-backports Release.gpg
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-backports/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-backports/universe Translation-en_US
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty Release
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-backports Release
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Packages               
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-backports/universe Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Sources
Reading package lists... Done


And Second:

I dont get the new notifications. I still have the old ones in a bubble. Why is this? Can i manually reinstall with terminal or synaptic? 

Many thanks, loving ubuntu, its been 2 great years now :guitar:

---

### Post by doccolinni on 2009-04-26
I'm pretty sure "hit" means that it managed to download it. Are you using the main server? Switch to main server in "System -> Administration -> Software Sources -> Download from:" if you're not using that one already, I got some updates since I upgraded to 9.04.

---

### Post by darkstaar on 2009-04-26
> **AlexBellisBrown said:**
> ...what does Hit mean? Is it the same as failed?

Hmmm...that appears to be a spelling error. The 'S' is missing and terminal only displaying the last three letters.

--Leisa

---

