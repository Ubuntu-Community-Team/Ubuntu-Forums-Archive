---
title: "a problem whit update"
date: 2009-01-30
forum: General Help
---

### Post by alis313 on 2009-01-30
alis313@Tux:~$ sudo apt-get update

Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) intrepid-backports/main Sources
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) intrepid-backports/restricted Sources
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) intrepid-backports/universe Sources
Hit [http://ir.archive.ubuntu.com](http://ir.archive.ubuntu.com) intrepid-backports/multiverse Sources
Fetched 3400B in 37s (90B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FE8956A73C5EE1C9
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5DC4E17435661D98
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CA1F91146F087E5A
W: You may want to run apt-get update to correct these problems

---

### Post by odinb on 2009-01-30
I get the same thing. Seems to be with the openoffice Repo, Do not get this message when I disable it.

---

### Post by mikhmv on 2009-01-30
I have same problem

---

### Post by SmileManVesa on 2009-01-30
same problem here

---

### Post by paranoid_humanoid on 2009-01-30
i think something is new with the way ppas work and they all have to be signed now or something. i'm trying to map the pub_keys to their ppa pages so i could import their keys individually. this really sucks cause i have a lot of ppas in my list, but the message is really annoying since i "sudo apt-get update" a lot.

---

### Post by blazingnikons on 2009-01-30
I'm having the same problem.  When I try to check synaptic package manager or update manager, I get the following:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

---

### Post by Zeedok on 2009-01-30
Someone has written a script which fixes the problem for me.  You can find it [here]("http://ubuntuforums.org/showthread.php?t=1047743&page=5").

---

### Post by blazingnikons on 2009-01-30
> **Zeedok said:**
> Someone has written a script which fixes the problem for me.  You can find it [here]("http://ubuntuforums.org/showthread.php?t=1047743&page=5").
That didn't do anything.  Besides, I've been able to update since then -- I think that issue was fixed a while back.

---

### Post by odinb on 2009-02-02
If you have not found a solution yet, here is some info:

Launchapad has added keys to all PPAs: [http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

Solution found elsewhere in these forums:

Issues with missing Public Keys?
Enter this command, replacing 247D1CFF with your NO_PUBKEY-key last eight digits from the error-message to import the key:
gpg --keyserver keyserver.ubuntu.com --recv 247D1CFF

Then add the key to your software sources, again, replace 247d1cff with the keynumber used in above command:
gpg --export --armor 247D1CFF | sudo apt-key add -

Then update your software sources:
sudo apt-get update

Done!

---

### Post by TCMuffin on 2009-02-08
> **odinb said:**
> If you have not found a solution yet, here is some info:

Launchapad has added keys to all PPAs: [http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

Solution found elsewhere in these forums:

Issues with missing Public Keys?
Enter this command, replacing 247D1CFF with your NO_PUBKEY-key last eight digits from the error-message to import the key:
gpg --keyserver keyserver.ubuntu.com --recv 247D1CFF

Then add the key to your software sources, again, replace 247d1cff with the keynumber used in above command:
gpg --export --armor 247D1CFF | sudo apt-key add -

Then update your software sources:
sudo apt-get update

Done!

Awesome - thank you :)

---

### Post by LouisZepher on 2009-02-15
> **odinb said:**
> If you have not found a solution yet, here is some info:

Launchapad has added keys to all PPAs: [http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

Solution found elsewhere in these forums:

Issues with missing Public Keys?
Enter this command, replacing 247D1CFF with your NO_PUBKEY-key last eight digits from the error-message to import the key:
gpg --keyserver keyserver.ubuntu.com --recv 247D1CFF

Then add the key to your software sources, again, replace 247d1cff with the keynumber used in above command:
gpg --export --armor 247D1CFF | sudo apt-key add -

Then update your software sources:
sudo apt-get update

Done!

Ditto, here. Thanks.

---

### Post by forger on 2009-02-15
Here's a script that fixes ppa links and gets ppa keys:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by KerryLB on 2009-03-05
Thanks from me too Odinb! :)

---

### Post by mkrahmeh on 2009-04-12
thx Odinb..it workt like a treat :)

---

### Post by brew1086 on 2009-05-13
Thanks [odinb]("http://ubuntuforums.org/member.php?u=334499") that did it for me too !!!!  :)

---

### Post by OnOffPT on 2009-06-04
That's perfect.
Thank you.

---

### Post by comicosmos on 2011-03-30
> **odinb said:**
> If you have not found a solution yet, here is some info:

Launchapad has added keys to all PPAs: [http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

Solution found elsewhere in these forums:

Issues with missing Public Keys?
Enter this command, replacing 247D1CFF with your NO_PUBKEY-key last eight digits from the error-message to import the key:
gpg --keyserver keyserver.ubuntu.com --recv 247D1CFF

Then add the key to your software sources, again, replace 247d1cff with the keynumber used in above command:
gpg --export --armor 247D1CFF | sudo apt-key add -

Then update your software sources:
sudo apt-get update

Done!

Good. This solved my problem perfectly.:)

---

### Post by NZJem on 2011-07-10
> **odinb said:**
> If you have not found a solution yet, here is some info:.....

July 2011 and this solution still works a treat.  Thanks 10^6 :)

---

### Post by erikson879 on 2011-08-24
> **TCMuffin said:**
> Awesome - thank you :)


The best jejejeje done!

---

### Post by farstrider on 2012-03-06
> **odinb said:**
> If you have not found a solution yet, here is some info:

Launchapad has added keys to all PPAs: [http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://news.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

Solution found elsewhere in these forums:

Issues with missing Public Keys?
Enter this command, replacing 247D1CFF with your NO_PUBKEY-key last eight digits from the error-message to import the key:
gpg --keyserver keyserver.ubuntu.com --recv 247D1CFF

Then add the key to your software sources, again, replace 247d1cff with the keynumber used in above command:
gpg --export --armor 247D1CFF | sudo apt-key add -

Then update your software sources:
sudo apt-get update

Done!

Thanks, I know that this is pretty old but thanks nonetheless, I appreciate the help! :popcorn:

---

### Post by oldos2er on 2012-03-06
Old thread is old. Closed.

---

