---
title: "Evolution email is stuck in ofline mode (Ubuntu 10.10)"
date: 2011-01-20
forum: Desktop Environments
---

### Post by achim_59 on 2011-01-20
I recently did a fresh install of 10.10 (previously I had 10.04). I could not do an upgrade because the package manager had a problem with unresolved dependencies resulting from the installation of a Nokia package for my CS-15 usb modem.

Since it was a new install, I did fresh backups of everything I needed, including evolution. After the install I tried restoring my email from the backup. Then I noticed that the send/receive button was disabled and **so was the option to work online in the file menu.**

The version of evolution is 2.30.3.

I thought this thread:
[http://ubuntuforums.org/showthread.php?t=1571313](http://ubuntuforums.org/showthread.php?t=1571313)
had an answer to my problem but it appears to be something different. I tried posting to that thread but repeatedly got a database error message. A new thread is probably a better way to go anyhow.

I tried deleting the .evolution folder in my home directory (as suggested in that other thread) and then re-installed evolution. That didn't work, however. I still have the same problem.

Oddly enough all my account details are still there! I tried checking the supported authentication and that seems to work. 

I've trawled a number of forum posts in this and other forums but haven't seen this problem described anywhere.

Does anyone have an idea how I can get my email to function again?

Achim

---

### Post by achim_59 on 2011-01-26
bump?

---

### Post by achim_59 on 2011-02-07
I noticed that, when I'm on a landline, Evolution wil send and receive email. My suspicion is that Evolution does something similar to Firefox in that it checks for an Internet connection via the network manager (actually called network tools in recent Ubuntu releases). I turned this option in Firefox off and it now starts in online mode even when I have a UMTS connection.

Note: I'm using wvdial for UMTS and this seems to bypass the network manager.

After checking a number of config files i found the following entry in *.gconf/apps/evolution/shell%25gconf.xml*:
```

<entry name="start_offline" mtime="1297009343" schema="/schemas/apps/evolution/shell/start_offline" type="bool" value="false"/>
```

That is obviously what I want. So I checked evolution by starting it from the command line and tried to force online mode. Here's the result:
```

achim@achim-T43:~$ evolution --online
evolution-shell-Message: Network disconnected.  Forced offline.
EI: MAIL PREF

```
My suspicions are thereby confirmed. Anybody have any ideas on how to get Evolution to accept my UMTS connection?

---

### Post by purct on 2011-04-11
I have the same issue.....works fine when I use NetworkManager via Wireless.    NetworkManager has issues with my Mobile Broadband so I downloaded sakis3g, that gives me internet access but I can't Send/Receive emails from Evolution because it gets a status report from Networkmanager and thinks that the internet is down!

Other users say that the answer is to un-install NetworkManager but that is not an option since I use it for my Wireless connection.   You can edit the /etc/NetworkManager/nm-system-settings.conf and change [ifupdown] managed=false to managed=true

but I am not sure if/what that will do to any devices managed by NetworkManager.

---

### Post by achim_59 on 2011-04-12
Thanks for the tip. I have now changed to Mozilla Thunderbird and it works very well... they've improved it greatly since I last used it. However, I will try what you suggest, because I don't use Network Manager for any wireless access. I use wvdial.

If it works, I'll let you know. It may take a couple of days, since I don't have a lot of time for fiddling with these things at the moment.

Thanks again

Achim

---

### Post by dowdberry on 2012-07-09
This just occured to me in 12.04 LTS (Precise) when I switched from network manager (nm) based wifi to wvdial based UMTS (Verizon LTE 4G).  I couldn't get a connection in Evolution--it always claimed there was no network.


I ran 

evolution --force-online

and it worked (in this version of Ubuntu/Evolution):

medberry@serenity:~$ cat /etc/issue
Ubuntu 12.04 LTS \n \l

medberry@serenity:~$ dpkg -l evolution
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-==============================================================================
ii  evolution                       3.2.3-0ubuntu6                  groupware suite with mail client and organizer

---

### Post by achim_59 on 2012-07-09
Thanks for the tip. I gave it a try but after a minute or so of disk thrashing nothing happened. It seems I'll have to upgrade after all... can't put it off all that much longer anyway. 

Thanks again.

Achim

---

### Post by wildmanne39 on 2012-07-09
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

