---
title: "Adept and synaptic"
date: 2006-03-19
forum: Desktop Environments
---

### Post by Geffers on 2006-03-19
When I installed kubuntu adept and synaptic both displayed lists of repositories (It think I have the description correct but I'm not on Linux at the moment so cannot check), some are greyed out.

I'm interested in installing a couple of programs that do not appear on either adept or synaptic so do I create new repositories of downloaded programs or have I got it completely wrong.

Geffers

---

### Post by alamba on 2006-03-19
Either add the "non-standard" repositories or download a .deb file and install using dpkg -i <packagename.deb>

A

---

### Post by dermotti on 2006-03-19
**sudo** dpkg -i <packagename.deb>  , just incase you didnt know :-)

---

### Post by vidak on 2006-03-19
[QUOTE=Geffers]When I installed kubuntu adept and synaptic both displayed lists of repositories (It think I have the description correct but I'm not on Linux at the moment so cannot check), some are greyed out.

I'm interested in installing a couple of programs that do not appear on either adept or synaptic so do I create new repositories of downloaded programs or have I got it completely wrong.

Geffers[/QUOTE]

you can try to edit and uncomment the *universe* and *multiverse* lines in /etc/apt/sources.list
if the package you need still isn't there (don't forget to update the package list with "apt-get update"), try 
apt-get.org
for new repositroies or download and install the .deb-s as posted above...

---

### Post by Geffers on 2006-03-19
[QUOTE=dermotti]**sudo** dpkg -i <packagename.deb>  , just incase you didnt know :-)[/QUOTE]

No, I didn't actually.

Linux is a new learning curve  :-? 

Geffers

---

### Post by lowey23 on 2006-03-20
Hi Geffers

You may find this link very useful

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

It's helped me a great deal.

Cheers

Lowey

---

