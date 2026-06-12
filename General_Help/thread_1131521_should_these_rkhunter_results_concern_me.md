---
title: "should these rkhunter results concern me?"
date: 2009-04-20
forum: General Help
---

### Post by FreeRangers on 2009-04-20
I'm really new to Ubuntu but so far I really like it. anyway I ran a rkhunter scan and it came up with a few warnings. I also ran chkrootkit and it came up clean, so I think these may be false positives. here are the warnings:

   [I]Running skdet command                         [ Skipped ]
[17:53:32] Info: Unable to find the 'skdet' command[/I]

how to I ensure this isn't skipped (or is it needed)?

[I][17:53:38]   Checking for software intrusions       [ Skipped ]
[17:53:38] Info: Check skipped - tripwire not installed[/I]

how do I install tripwire (if it is needed)?

[I] Checking for enabled xinetd services            [ Skipped ]
[17:53:38] Info: Check skipped - file '/etc/xinetd.conf' does not exist.[/I]

Is this important?

[I][17:54:09] Info: Starting test name 'startup_files'
[17:54:09]   Checking for local host name                    [ Found ]
[17:54:09] Info: Starting test name 'startup_malware'
[17:54:09] Info: Found local startup file: /etc/rc.local[/I]

What does this mean, and how do I fix it?
[I]
[17:54:16]   Checking /dev for suspicious file types         [ Warning ]
[17:54:16] Warning: Suspicious file types found in /dev:
[17:54:16]          /dev/shm/pulse-shm-3974696533: data[/I]

is this warning serious!? If so how do I fix it?

I think these all may be false positives, as I just installed Ubuntu a couple days ago, and have only been to this site, but I just want to make sure everything is fine before I do any more with Linux. Thanks for taking time to help a Linux newbie.

---

### Post by dragos240 on 2009-04-20
No, these don't need to be concerned about. They're fine as they are.

---

### Post by FreeRangers on 2009-04-21
Ok Thanks. But could someone explain to me what they mean so I know why I shouldn't be concerned with them?

---

### Post by blueturtl on 2009-04-21
> Running skdet command [ Skipped ]
[17:53:32] Info: Unable to find the 'skdet' command

This is just something that rkhunter would optionally do, but like said you don't have the skdet command so it is skipped. Totally harmless.

> [17:53:38] Checking for software intrusions .. Skipped
[17:53:38] Info: Check skipped - tripwire not installed

how do I install tripwire (if it is needed)?

My guess is that tripwire gives you additional ways of detecting intruders. Since it isn't installed, you won't be able to use the potential additional info for rkhunter. To install I guess just 'sudo apt-get install tripwire', but you may want to read up on it first to see what it does and how it is configured.

> Checking for enabled xinetd services .. Skipped
[17:53:38] Info: Check skipped - file '/etc/xinetd.conf' does not exist.

Another optional service to be checked, and since you don't have it rkhunter skips it.

> [17:54:09] Info: Starting test name 'startup_files'
[17:54:09] Checking for local host name [ Found ]
[17:54:09] Info: Starting test name 'startup_malware'
[17:54:09] Info: Found local startup file: /etc/rc.local

/etc/rc.local is a file where users can enter their own startup commands. It is common that malware attempts to run at startup, so this file is being checked for known hostile entries. Nothing seems to have come up though.

> [17:54:16] Checking /dev for suspicious file types [ Warning ]
[17:54:16] Warning: Suspicious file types found in /dev:
[17:54:16] /dev/shm/pulse-shm-3974696533: data

is this warning serious!? If so how do I fix it?

The following post seems to explain it, not harmful at all:

[http://ubuntuforums.org/showthread.php?p=4908163](http://ubuntuforums.org/showthread.php?p=4908163)

---

### Post by FreeRangers on 2009-04-21
Thanks! That was very helpful. It's good to know that all that stuff was just false positives.

---

