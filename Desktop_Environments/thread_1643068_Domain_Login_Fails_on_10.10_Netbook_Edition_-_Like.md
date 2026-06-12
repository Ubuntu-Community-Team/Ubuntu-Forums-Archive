---
title: "Domain Login Fails on 10.10 Netbook Edition - Likewise-Open 5.4"
date: 2010-12-11
forum: Desktop Environments
---

### Post by pwebster25 on 2010-12-11
I did a fresh install of the netbook version of 10.10 on a Gateway CX2618.  I ran all updates and then rebooted. I installed LWO 5.4 from the repository and joined the domain.  I put in a kerberos realm (same as my domain) but I don't know for sure if I have a kerberos realm.  I successfully joined the domain with the GUI.  I rebooted, per instructions.

I tried to login with domain username and password (DOMAIN\username).  It takes a couple seconds to think and then kicks me right back to the GDM login screen.  I have tried several times with the same login and have tried other domain users.  It doesn't say "authentication failure" but I should have tried to use the wrong password to see if it would do the same.

I'm stumped.  Is there a ppa I need to add?  Is Likewise-Open supposed to work with the maverick netbook edition.  I saw the previous notice on the [Likewise site]("http://www.likewise.com/community/index.php/forums/viewannounce/863_29/") about OpenLDAP but I thought that was resolved in the updates and no longer in effect.  Should I install LWO 6.0?  If so, from where? From a ppa somewhere? From the Likewise site?

Maybe there is a simple solution.  

I can still login with a local admin account.

My ultimate goal is to automatically mount network windows shares for various students, based on their login credentials and using CIFS.  I almost had this figured out before this fresh install.

---

### Post by e79 on 2010-12-11
I've been playing a bit from time to time with Ubuntu in a Windows domain and had a VM laying around with an Active Directory domain created under Server 2003. I also happened to have a fresh Ubuntu 10.10 in another VM so I tried the following, with success :

On Ubuntu :
1. After a fresh install + updates, I edit my Network Connexion to make it static, specifying the Domain DNS server as well as putting the domain name in 'Search Domains'. I reloaded the connexions and made sure the new config applied successfully (ifconfig && cat /etc/resolv.conf).

2. I then opened /etc/nsswitch.conf and changed the 'Host' line with this one :
```
hosts:          dns files mdns4_minimal [NOTFOUND=return] mdns4
```3. Installed LikeWise 5.4 from the Software Center, opened the GUI dialogue and joined the domain (probably as you did). I restarted the machine afterward.

4. Once rebooted, I could log in as domain\username (but not just username) and browse the network server/shares (see included screenshot) and was able also to manually create shortcuts/bookmarks for allowed shared for a said user that were persisting upon reboots. But this is as far as my tests went.

I had to manually create a DNS entry for this machine on the domain, I don't know why but it was not created automatically.

You could also try uninstalling LikeWise and install Centrify Express, I did few basics test that were also successful.

As for automatically mouting the network shares (bit like logon scripts  on windows), I didn't start yet my researches on that topic as I don't have much time, so I unfortunately can't help you on that matter.

hope this helps

---

### Post by pytheas22 on 2010-12-11
Did you check /var/log/auth.log to see if it provides any clues about where/why the authentication as failing?  As I recall, Likewise keeps various log files of its own that could also be helpful.

Another thing worth trying would be to install an ssh server on the computer in question, then try to ssh to localhost as a domain user, with a command like:
```

ssh 'DOMAIN\user'@localhost
```

If you're lucky, you might get some useful feedback on the command line about what's wrong; this will also rule out any issue specific to gdm (the process that handles graphical logins, which are totally separate from ssh logins in this respect).  In a worst case, it at least gives you a quick and easy way of testing whether the log in is working, or generating a login attempt so you can see what gets dumped to the logs immediately after.

If none of the above (in my post or the one preceding it) helps, you could try removing your current Likewise installation and installing it using the package from Likewise's site, rather than the one in the Ubuntu repositories.  They make you register but it's a free download after that: [http://likewise.com/download/](http://likewise.com/download/)

I also second giving Centrify a try, unless you have a reason to prefer Likewise.  It pretty much does the exact same thing (although via a somewhat different approach), and in my experience is just as easy to use.  The only downside is that as far as I know Centrify doesn't provide a GUI, but the CLI interface is not too complicated.  I've used both Likewise and Centrify from the command line extensively at work and although I'm a bit rusty on some of the commands right now, I have them all documented somewhere and would be happy to look them up if you run into difficulties.

---

### Post by pwebster25 on 2010-12-11
Thanks to both of you.  These give me some good ideas with Likewise as well as pointing me towards Centrify Express.  I will look for some documentation on that.  My only reason for using Likewise-Open is that it has worked for me in the past (I started using Ubuntu in 8.04).  It has been promoted by Ubuntu as an important feature.  I have stuck with it, although there have been some glitches that regular users probably wouldn't have put up with.

---

### Post by e79 on 2010-12-11
Always a pleasure !  Good luck in your endeavor  :p

---

### Post by atworkwithjf on 2010-12-22
[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=358340")There was a bug in OpenLDAP which caused Likewise to fail if users failed to run the updates on their system prior to attempting a domainjoin.  The bug was fixed in early December.

Centrify is NOT Open Source and those who wish to make use of and support OpenSource products may not want to pursue closed source solutions.

Likewise Open 6.0 always worked with Maverick, it has not dependency on OpenLDAP like the one in Ubuntu main.

---

### Post by e79 on 2010-12-31
> **atworkwithjf said:**
> Centrify is NOT Open Source and those who wish to make use of and support OpenSource products may not want to pursue closed source solutions....
 
The 'Centrify Express' mentionned in this thread IS free. If not, it would not be in the Software Center, would it ?

---

### Post by atworkwithjf on 2010-12-31
There is a VERY real difference between free closed source software and free open source software.  If it was Open Source they would not be in an external repository.

---

### Post by pytheas22 on 2011-01-03
> The 'Centrify Express' mentionned in this thread IS free. If not, it would not be in the Software Center, would it ?

It's free but not Free.  In other words, it costs no money to use, but it is not open-source.

There are several applications in the Software Center which are not open-source, such as Skype.  In Ubuntu 10.10, there are also some that cost money to install.

---

