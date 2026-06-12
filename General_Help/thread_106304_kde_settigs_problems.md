---
title: "kde settigs problems"
date: 2005-12-20
forum: General Help
---

### Post by ramaswamyps on 2005-12-20
i fetched cds od ubuntu 5.10 and installed ubuntu desktop without any hassles .
prior to this i tried to install kubuntu downloaded the iso 2 times and was not successful in installing fully.
the second download i was able to install but it gave error in configuraton and left me with a broken install.
noa i installed kde in my successful install of ubuntu 5.10.
why the livecd also is given with installer i dont know.
installer cd itself installs everything.
as i had the two kubuntu burnt cds i used some packages from them and successfully oinstalled the kde
i cant find the controlcenter for kde the fonts on the screen are too small like news print.
kcontrol i invoked from konsole it gave many errors but started the controlcenter
i changed the allfonts size it changed for the time but when i exited they r all back to the small size
it seems it does not really change settings
also i didnot see the administrator button in the screen
can someone tell me what more kde packages i should install
the ubuntu desktop is fabulous.
i could not keep the panel downside .as soon i select position bottom the nautilus exits.
give me some idea for these troubles .
:p :p

---

### Post by adie273 on 2005-12-20
You could try adding this repository to Synaptic and installing the new KDE packages it gives you...

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

Thats what I did, and everything in KDE works fine for me. Not only that, its the latest KDE (3.5) Which personally I rather like due to a few small little features.

Adie

---

### Post by ramaswamyps on 2005-12-20
i thought the fubuntu cd gave the latest fde packages.
i will try adding the repository and try 
thanks for sharing ur experience
will come back and post the result
am really afraid the kubuntu package may again break the installation as it did before when installed from the kubuntu 5.10 iso .
it gave me an error of dependent-try failed whaile configuring installation for the first time.
:???: :???:

---

### Post by ramaswamyps on 2005-12-21
[QUOTE=adie273]You could try adding this repository to Synaptic and installing the new KDE packages it gives you...

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

Thats what I did, and everything in KDE works fine for me. Not only that, its the latest KDE (3.5) Which personally I rather like due to a few small little features.

Adie[/QUOTE]
apt-get update complaints kubuntu packages public key is not available
how do we overcome that?
how u could install it?
synaptic running anyway now
it may give an error after downloads.
it takes abt an hr to get the files in my comp

---

### Post by adie273 on 2005-12-21
Try adding the key. Just do the following...

wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
sudo apt-key add kubuntu-packages-jriddell-key.gpg

Hopefully that works.

Adie

(If that complete URL doesn't show up since on my preview this forum is shortening it. The last part after '~jriddell' is 'kubuntu-packages-jriddell-key.gpg')

---

### Post by ramaswamyps on 2005-12-21
apt-get install kdeaddons went through nicely
it gave me an option to install without verifying the pubkey
so i installed without key

synaptic said not authenticted but installed kdebase and depends without any trouble.
so now i have kde3.5 up and running.
thanks veru much for the help.
any way now i will add the key to apt sources
but it gives result like this:


root@ubuntu:/home/ramaswamy# wget [http://people.ubuntu.com/~jriddell/k...iddell-key.gpg](http://people.ubuntu.com/~jriddell/k...iddell-key.gpg)
--19:44:26--  [http://people.ubuntu.com/~jriddell/k...iddell-key.gpg](http://people.ubuntu.com/~jriddell/k...iddell-key.gpg)
           => `k...iddell-key.gpg'
Resolving people.ubuntu.com... 82.211.81.132
Connecting to people.ubuntu.com|82.211.81.132|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:44:28 ERROR 404: Not Found.

root@ubuntu:/home/ramaswamy#                     
i can try again later if its network busy
i can try and find the url for the key or i can copy the repository from kubuntu 510 installer cd whuch gives other errors.

thanks for the support.

---

