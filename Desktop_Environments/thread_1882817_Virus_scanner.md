---
title: "Virus scanner"
date: 2011-11-18
forum: Desktop Environments
---

### Post by Azyx on 2011-11-18
On 11.10 I have problem with the virus scanner. I first schedule a virus scan for the entire compuer computer (Advanced-->Schedule and marked entire computer. Now I want to just scan my Home (recommended). How do I do that? If I only change, It jump back to entire computer. Have tried run 'sudo clamtk' but that is different, and was not Scheduled at all.

/Cheers

---

### Post by QDR06VV9 on 2011-11-18
Learn About ClamAv's Other Options
From Here
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

Try man clamscan.

Schedule ClamAV

You can use the at command to schedule clamscan or freshclam. For example:

at 3:30 tomorrow
at>clamscan -i /home/user | mail [email]user@example.com[/email]
at> <CTRL-D> 
job 3 at 2005-04-28 03:30

You have now scheduled a ClamAV scan to happen on your home directory at 3:30 AM tomorrow. The output (showing only infected files) will be sent to you by e-mail. 

Try man clamscan.

Schedule ClamAV

You can use the at command to schedule clamscan or freshclam. For example:

at 3:30 tomorrow
at>clamscan -i /home/user | mail [email]user@example.com[/email]
at> <CTRL-D> 
job 3 at 2005-04-28 03:30

You have now scheduled a ClamAV scan to happen on your home directory at 3:30 AM tomorrow. The output (showing only infected files) will be sent to you by e-mail.

---

### Post by Azyx on 2011-11-18
> **runrickus said:**
> Learn About ClamAv's Other Options
From Here
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

Try man clamscan.

Schedule ClamAV

You can use the at command to schedule clamscan or freshclam. For example:

at 3:30 tomorrow
at>clamscan -i /home/user | mail [email]user@example.com[/email]
at> <CTRL-D> 
job 3 at 2005-04-28 03:30

You have now scheduled a ClamAV scan to happen on your home directory at 3:30 AM tomorrow. The output (showing only infected files) will be sent to you by e-mail. 

Try man clamscan.

Schedule ClamAV

You can use the at command to schedule clamscan or freshclam. For example:

at 3:30 tomorrow
at>clamscan -i /home/user | mail [email]user@example.com[/email]
at> <CTRL-D> 
job 3 at 2005-04-28 03:30

You have now scheduled a ClamAV scan to happen on your home directory at 3:30 AM tomorrow. The output (showing only infected files) will be sent to you by e-mail.

I don't understand man-pages symbols and stuff.

And I ask this on the desktop, so terminals are not a solution ^^

But, if i take your CLI solution.. Why just only scan tomorrow, and not the day after tomorrow? And does the computer stop scanning the entire computer every night. It's takes hours, if I don't end the process.

I have tried to totally remove virus-scanner with synaptic, but still I are schedules to scan the entire computer every night.

---

### Post by Azyx on 2011-11-18
By the way thanx for the tip about the CLI-solution.

---

### Post by oldsoundguy on 2011-11-18
The question is WHY?  there are NO virus files or malware for Linux in the wild and the chances of getting one is only if YOU install it yourself!

LINUX is NOT WINDOWS .. it is not a piece of swiss cheese where a baddy can get installed by clicking on a photo.

ALL AV programs you install in Linux are NOT for LINUX .. they are to protect Windows users to stop you from forwarding them an infected eMail. OR IF you have Windows users on your server.

---

### Post by Azyx on 2011-11-18
> **oldsoundguy said:**
> The question is WHY?  there are NO virus files or malware for Linux in the wild and the chances of getting one is only if YOU install it yourself!

LINUX is NOT WINDOWS .. it is not a piece of swiss cheese where a baddy can get installed by clicking on a photo.

ALL AV programs you install in Linux are NOT for LINUX .. they are to protect Windows users to stop you from forwarding them an infected eMail. OR IF you have Windows users on your server.

I have friends I like and they have windos^^ And I have plans to sometime in the futur to get windos ^^

---

### Post by nixblog on 2011-11-18
Virus scanners for Linux seems to be a grey area at best but if you are on a Windows network then it might pay to have some form of scanning on your Linux machine. Rootkits are more of a problem for Linux (and Windows) so I have Rootkit Hunter (rkhunter) installed on my Linux machines.

---

### Post by WasMeHere on 2011-11-18
Hi again Azyx,

Have a look at our new wiki page about basic security for Ubuntu [[COLOR="RoyalBlue"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

Olle

---

### Post by Azyx on 2011-11-18
> **Olle Wiklund said:**
> Hi again Azyx,

Have a look at our new wiki page about basic security for Ubuntu [[COLOR="RoyalBlue"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

Olle

I want to stop my nighty scan of my entire system, nothing else. I made a scan of my entire system (shared folder, externa media and stuff, and I though I only should do I once, but now I cannot turn scanning 'entire system' of in the the schedule. Have made a totall remove and remove the .clamtk folder in home, and reinstalled 'virus scanner', but it is still marked as run 'entire system' in schedules.

---

### Post by Azyx on 2011-11-18
> **nixblog said:**
> Virus scanners for Linux seems to be a grey area at best but if you are on a Windows network then it might pay to have some form of scanning on your Linux machine. Rootkits are more of a problem for Linux (and Windows) so I have Rootkit Hunter (rkhunter) installed on my Linux machines.

Have booth rkhunter and chkrootkit and unhide. I is for people who visit me with their windos-things and connect to my local network and borow thing I have foud on internet. And as I said before, I have planes to get windows on my network.

---

### Post by WasMeHere on 2011-11-18
What if you remove it and do ***not*** reinstall it?
```
sudo apt-get purge <package-name>
```
Then it should not be able to run. Maybe it also helps us understand how it is activated by some kind of error output (to the screen or to a log file).

Do you think it is run as a cron job? Or is there a built-in scheduler in the anti-virus software?

---

### Post by Azyx on 2011-11-18
> **Olle Wiklund said:**
> What if you remove it and do ***not*** reinstall it?
```
sudo apt-get purge <package-name>
```
Then it should not be able to run. Maybe it also helps us understand how it is activated by some kind of error output (to the screen or to a log file).

Do you think it is run as a cron job? Or is there a built-in scheduler in the anti-virus software?

Is't purge the same as totally remove in synaptic? It says that even config-files disappear. It's often being a 'bug' if placement of config-files are changed according to upgrade in gnome or ubuntu (I have upgraded from 11.04) there they have change placement of config files i think.

---

### Post by Azyx on 2011-11-18
> **Olle Wiklund said:**
> What if you remove it and do ***not*** reinstall it?
```
sudo apt-get purge <package-name>
```
Then it should not be able to run. Maybe it also helps us understand how it is activated by some kind of error output (to the screen or to a log file).

Do you think it is run as a cron job? Or is there a built-in scheduler in the anti-virus software?

In 10.04 there are a cron-file in .clamtk, but not in 11.10

---

### Post by WasMeHere on 2011-11-18
I guess you want to get rid of 'everything' concerning the virus-scanner. However some files created by you when configuring might stay anyway. But if the software is gone, it cannot run. That's what I would try if I were in your situation.

---

### Post by Azyx on 2011-11-18
> **Olle Wiklund said:**
> I guess you want to get rid of 'everything' concerning the virus-scanner. However some files created by you when configuring might stay anyway. But if the software is gone, it cannot run. That's what I would try if I were in your situation.

No, I want to have it, but not that It beguinn to scann the hole system with 100% cpu in 4-5 hours. As I said before cos I have sometimes windos here on my local network. So i know how I get rid of the program, but not were configuration for scanning the hole system are stored. I suspect there have been some changes in placment since 10.04 (cos cron does not anymore are placed in .clamtk

---

### Post by Azyx on 2011-11-18
It worket now :) Before I removed the configuration folder in home .clamtk with 'virus scanner' installed and it didn't work. But if i uninstalled virus scanner and then removed .clamtk, and after everything was gone, make a new install it was again set as default (only home) so it work. I think it may be a bug between GUI (clamtk?) and the clamav-scanner. If i remove the .clamtk when the program is still the, it may have a 'backup' of the configuration somewere else?

I 'remove all, inkluding config-files' in synaptic  the same as the command 'apt-get purge' ?

---

### Post by WasMeHere on 2011-11-18
Maybe there was a daemon that was still running, having the settings in its memory. Anyway, congratulations! It is always nice to solve a problem :-)

Olle

---

