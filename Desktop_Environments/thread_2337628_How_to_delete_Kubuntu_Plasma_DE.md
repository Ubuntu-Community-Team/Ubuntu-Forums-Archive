---
title: "How to delete Kubuntu Plasma DE?"
date: 2016-09-20
forum: Desktop Environments
---

### Post by Citta on 2016-09-20
Hi, 

I tried this:

~$ sudo apt-get autoremove --purge kubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Result: KDE is still existing, also in the login box...but never worked, therefore I want to delete it. I searched the internet, tried a few cmds in vain....not just the above mentioned.

PS: On the top right corner is a halt sign, an "error" occurred. An update is offered, when clicked: Software Updater: Package system broken.
Suggesting: apt-get -f install
Result:
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by denter2 on 2016-09-20
```
sudo apt-get -f install
```

---

### Post by Citta on 2016-09-22
> **denter2 said:**
> ```
sudo apt-get -f install
```
Already done  before posting, it was suggested by the OS, did not work, as mentioned in the post!

---

### Post by Bucky Ball on 2016-09-22
[QUOTE=Citta]Already done before posting, it was suggested by the OS, did not work. [/QUOTE]

You said you did this:

> Suggesting: _**apt-get -f install**_
Result:
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? 

No 'sudo'. Did you add it, as advised by denter2?

```
sudo apt-get -f install
```

Which release and flavour of Ubuntu are you using? 

Please use code tags for terminal output. See link in my signature. Thanks.

* Also, try
```

sudo apt-get remove --purge kde-telepathy-minimal
sudo apt-get remove --purge kubuntu-desktop
``` 

Use 'sudo apt-get remove', not 'autoremove'.

---

### Post by Citta on 2016-09-22
It is Ubuntu 16.04, default DE, flavour does mean what? What are code tags, what is the link in your signature, used for? 

Terminal output:

~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-de kde-l10n-engb libqqwing2v5 linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-34-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-34-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  kde-config-telepathy-accounts
The following NEW packages will be installed:
  kde-config-telepathy-accounts
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
517 not fully installed or removed.
Need to get 0 B/137 kB of archives.
After this operation, 825 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 369701 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.12.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+16.04.20160126-0ubuntu1
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

:~$ sudo apt-get remove --purge kde-telepathy-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy : Depends: kde-telepathy-minimal (= 15.04.20ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

~$ sudo apt-get remove --purge kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

PS: After starting the Software Updater, it complains: The package system is broken.....

---

### Post by Bucky Ball on 2016-09-22
Code tags? Look in the bunch of links at the bottom of this post. See the one on the first line that says 'Using ```
 tags'? Click it and you it will show you how to add them. Please add them to your last post. Thanks.

Flavour = Ubuntu, Xubuntu, Lubuntu, or one of the other official Ubuntu flavours. 

It would complain the package system is broken. That's what the terminal's doing as nothings changed. What do you get with

[code]sudo apt autoremove
```

Exactly the same output? Please post, between code tags. :)

---

### Post by denter2 on 2016-09-24
it looks like this is the crucial bit:```
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.12.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service',  which is also in package account-plugin-google  0.12+16.04.20160126-0ubuntu1
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```looks to me like "kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb" is not the proper filename, maybe because of the "%3a" (note how it becomes a ':' in the next line)?
there's also this line:
"trying to overwrite '/usr/share/accounts/services/google-im.service',  which is also in package account-plugin-google  0.12+16.04.20160126-0ubuntu1"
oooh, very fishy.

i have no clue what happend there, but i'd try to
a) uninstall the packages "account-plugin-google"
OR
b) uninstall "kde-config-telepathy-accounts"
OR
c) delete /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb

each time after you tried one of these things, you have to do "sudo apt-get install -f" again.
when it goes through without errors, try to do what you originally wanted to do.

lesson learned:
be more careful with ppas in general, and google's in particular.

---

### Post by Bucky Ball on 2016-09-24
You could also check in 'Software and Updates> Other Software' tab and see if you simply still have the PPA enabled in there. Disable or remove it from there if so. Sounds silly, but you never know ...

---

### Post by Citta on 2016-09-24
```
sudo apt autoremove
```


Exactly the same output? Please post, between code tags. :)[/QUOTE]

Terminal output:


```
~$ sudo apt autoremove
[sudo] password for u: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not installed
E: Unmet dependencies. Try using -f.

```

> lesson learned:
be more careful with ppas in general, and google's in particular.                 
Could you expound that a bit more, thus avoiding problems in future? Would it be better to delete the OS, seems to be a ceaseless adventure...

I checked this. "PPA" is not mentioned and those two boxes are unchecked.

---

### Post by Citta on 2016-09-24
I tried to uninstall as suggested, output:
```
u@ubuntu:~$ sudo apt-get remove account-plugin-google
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
 unity-scope-gdrive : Depends: account-plugin-google but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
u@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-de kde-l10n-engb libqqwing2v5 linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-34-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-34-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  kde-config-telepathy-accounts
The following NEW packages will be installed:
  kde-config-telepathy-accounts
0 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
517 not fully installed or removed.
Need to get 0 B/137 kB of archives.
After this operation, 825 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 369701 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.12.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+16.04.20160126-0ubuntu1
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
u@ubuntu:~$ sudo apt-get remove kde-config-telepathy-accounts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'kde-config-telepathy-accounts' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
u@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-de kde-l10n-engb libqqwing2v5 linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-34-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-34-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  kde-config-telepathy-accounts
The following NEW packages will be installed:
  kde-config-telepathy-accounts
0 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
517 not fully installed or removed.
Need to get 0 B/137 kB of archives.
After this operation, 825 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 369701 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.12.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+16.04.20160126-0ubuntu1
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
u@ubuntu:~$ sudo apt-get delete /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
E: Invalid operation delete
u@ubuntu:~$ sudo apt-get remove /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not installed
E: Unmet dependencies. Try using -f.
u@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-de kde-l10n-engb libqqwing2v5 linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-34-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-34-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  kde-config-telepathy-accounts
The following NEW packages will be installed:
  kde-config-telepathy-accounts
0 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
517 not fully installed or removed.
Need to get 0 B/137 kB of archives.
After this operation, 825 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 369701 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.12.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+16.04.20160126-0ubuntu1
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by denter2 on 2016-09-25
seems like you're in dependency hell.
anyhow, you MUST get this account-plugin-google off your system.
(btw, i'd use "purge" instead of "remove").
maybe it helps to remove the google ppa from your system, and then run "apt-get update" and "apt-get upgrade".

and, i'll say it again, BEFORE each step and AFTER each FAILED step you should run "apt-get -f install". just to be safe.

---

### Post by Citta on 2016-09-25
I'll delete this OS. Some time ago I tried Lubuntu, that never worked, too. Frittered time and temper away, getting things done with Linux, well, seems to be something for enthusiastic lovers with much time, patience and readiness for suffering!

---

### Post by Bucky Ball on 2016-09-25
Or those that don't add PPAs manually without knowing what the consequences might be and being prepared for them. PPAs that you add yourself are clearly labelled 'USE AT YOUR OWN RISK' on the packet, or words to that effect. If you install one, it breaks your system, what has that got to do with Ubuntu???

You also seem to have overlooked denter2's advice in post #13, or at least it has gone without comment. 

Anyhow, good luck and please mark this thread as solved to save others some time. Thread Tools at top right or see the last blue link at the bottom of this post.

---

### Post by Geoffrey_Arndt on 2016-09-25
Not so much "suffering" really . . . . but just a few hours (2-3)  over a couple of months of reading, including watching a few experts on Youtube.   Check out "OhHeyIt'sLou" or "Joe Collins" or "AJ Reissig" on Youtube's Linux Channels.   They'll help get your head turned around in the right direction . . . before it's too late.

---

### Post by Citta on 2016-09-27
Tried what denter wrote with no avail, I will not continue, having  experiences with Lubuntu, as mentioned, spent very much time with that,  no success. Just a few hrs did not do it. In such a case I could tinker  with Arch. But that has nothing to do with getting things done.  As I  already wrote in #11: No ppa. I even do not know what it is. Nevertheless  Bucky wrote about ppas, without explaining how he came to this  conclusion. Simply installed a DE as prescribed to improve learning on a  different DE. Result: OS broken. Linux holy rollers claim always the customizability of  Linux, but even a wider scroll bar seems to be an unsurmountable  obstacle. I just finished a Linux course, 3 different Linux in the VM  Player, Ubuntu is one of them. It was a cute idea having them on a  hypervisor and not on a SSD! Lesson learned with Lubuntu and Ubuntu,  too. Also why Linux sits just on 1% of all machines.

> **Geoffrey_Arndt said:**
> Not so much "suffering" really . . . . but just a few hours (2-3)  over a couple of months of reading, including watching a few experts on Youtube.   Check out "OhHeyIt'sLou" or "Joe Collins" or "AJ Reissig" on Youtube's Linux Channels.   They'll help get your head turned around in the right direction . . . before it's too late.

Would you recommend "Getting Started with Ubuntu"?

---

### Post by vasa1 on 2016-09-27
> **Citta said:**
> ... Linux holy rollers claim always the customizability of  Linux, ...
I suggest you tread carefully.

Please check the [Ubuntu Forum Rules]("https://ubuntuforums.org/misc.php?do=showrules") and read the [Forum's Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945").

---

### Post by Citta on 2016-09-27
Read your points, enigmatic. No solution.

---

### Post by CantankRus on 2016-09-28
Being a smartass and abrasive does you no favours.
Believe it or not we weren't born using Linux but realized the benefits, and took the time to learn.
Sometimes, for a new user the easiest solution is to reinstall and regard it as a learning experience.
 
If you don't have the patience maybe Linux is not for you.

---

### Post by denter2 on 2016-10-02
just for the record, i'm neither a holy roller, nor do i like suffering.
looking at the situation, for me the problem is clearly one of "i was tinkering, and accidentally overdid it".
sure, this doen't happen to $proprietary_os users.
if op were a friendly person in my neighbourhood, i'd offer them to bring the machine and i'll fix it.
as things are, that isn't an option.
imho, a little more attentiveness and diligence in this thread could have solved the issue easily.
whatever.

---

### Post by Citta on 2016-10-02
As before: No solution, but accusations. But those cute remarks quadrupled the performance of Ubuntu. Marked as "Solved"! Awesome.

---

### Post by CantankRus on 2016-10-02
Glad to see you found a solution.
Bye.

---

### Post by oldos2er on 2016-10-02
Closing since this has crossed the line laid out in the CoC:

**Trolling, Attacks and Flaming:** These are always forbidden. 
[LIST]
[*]Trolling is posting in a way that provokes emotional responses.
[*]Attacks and derogatory terms of any kind are not welcome. This  includes references to any operating systems or the companies that  produce them.
[*]Flames are messages that personally attack or call any people names  or otherwise harass. These, along with any generally condescending posts  will be edited or removed at the moderators discretion.
[*]If a thread is flame-bait (appears to be intended to start an  argument or is likely to cause an argument rather than enhance  discussion, as in trolling), it will be locked or removed without  notice. Individual flame-bait comments in a post may be deleted or  edited at the moderators' discretion.
[*]If the thread turns into an argument, it can be closed to further  comment or removed without notice. Sometimes a moderator may split the  thread or jail certain portions in order to keep the discussion  going,this is not always possible.
[/LIST]

> No solution Removing Solved tag, which is intended to help others find a solution to a similar problem.

---

