---
title: "Beryl on Fiesty fawn : no valid OpenPGP data found."
date: 2008-02-04
forum: Desktop Environments
---

### Post by Zenodilodon on 2008-02-04
[B]Hey,

 This is my first time on the forums myself, I got into ubuntu because I hate vista. 
I have used the forum page on installing Beryl desktop manager on my computer 3 times previously, I updated my hardrives a few times. I have used the same 7.10 mini edition iso to load ubuntu in my computer each time.  The site I used was here:[/B]

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

_As I stated before I ran the installation perfect the last 3 times I installed beryl but on this attempt this is what the terminal chatters up:_

patrick@patrick-desktop:~$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
--13:49:21--  [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
           => `-'
Resolving ubuntu.beryl-project.org... 82.140.42.54, 88.191.250.18, 80.77.247.17, ...
Connecting to ubuntu.beryl-project.org|82.140.42.54|:80... failed: No route to host.
Connecting to ubuntu.beryl-project.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:49:42 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.
patrick@patrick-desktop:~$ patrick@patrick-desktop:~$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
bash: patrick@patrick-desktop:~$: command not found
gpg: no valid OpenPGP data found.
patrick@patrick-desktop:~$ --13:49:21--  [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: --13:49:21--
bash: --13:49:21--: command not found
patrick@patrick-desktop:~$            => `-'
> Resolving ubuntu.beryl-project.org... 82.140.42.54, 88.191.250.18, 80.77.247.17, ...
> Connecting to ubuntu.beryl-project.org|82.140.42.54|:80... failed: No route to host.
> Connecting to ubuntu.beryl-project.org|88.191.250.18|:80... connected.
> HTTP request sent, awaiting response... 404 Not Found
> 13:49:42 ERROR 404: Not Found.
> 
> gpg: no valid OpenPGP data found.
> patrick@patrick-desktop:~$ 

I am unsure what this means in Linux, I am a newbie but I see 404 errors on non existent or moved websites, broken links and such.

if there is any way around this or of there is an updated Deb source for beryl core please inform me My e-mail is       [email]Jaws8472@aol.com[/email]

---

