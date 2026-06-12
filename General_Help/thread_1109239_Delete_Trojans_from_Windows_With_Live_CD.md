---
title: "Delete Trojans from Windows With Live CD"
date: 2009-03-28
forum: General Help
---

### Post by iswear on 2009-03-28
Is it posable or will the trojan keep copying its self even though im not in windows.

---

### Post by anjilslaire on 2009-03-28
You can in theory delete it via linux, as the code is not active. However, once a system is compromised, the best option is to format, as you really can't be 100% sure the system is clean afterwards, due to the likelihood of other, undetected malware piggybacking in via the initial compromise. Additionally, you'll probably have to do some indepth cleasning of the registry as well.

---

### Post by iswear on 2009-03-28
Alright, well i dont want to format the hard drive cause its my sisters computer and i dont have a windows CD to reistall windows. I would get her to use ubuntu but it would take me a decade to teache her every thing. Is there any way to find the files that would be piggybacking. Also how would i accsee the windows file from a live cd? 

Thanks!

---

### Post by anjilslaire on 2009-03-28
It's a catch-22. You can never know what may else be present, so you really can't go looking and hope to find everything.

From a live CD, you should just be able to view the partitions without much effort, depending on what type of live environment you're using.

Depending upon the PC manufacturer, there should be a restore partition you can acess from within the system and restore the machine back to a out-of-the-box state.

---

### Post by igor. on 2009-03-28
You can try knoppicillin, it's a linux-based virus scanner that boots live from cd.

[http://www.heise.de/software/download/knoppicillin_download_edition/37894](http://www.heise.de/software/download/knoppicillin_download_edition/37894)

---

### Post by Xero Xenith on 2009-03-28
If I were you I'd get the Ubuntu live-CD, and run this command to install clam-av (good virus scanner for Linux):
```
sudo apt-get install clamav
```
Then run it, after mounting the partition you want to scan.

[size=1](Random waffling note - on my installation of Ubuntu, I'd just type "pie clamav", as "pie" corresponds to "sudo apt-get install" in my .bashrc - I'm lazy that way.)[/size]

---

