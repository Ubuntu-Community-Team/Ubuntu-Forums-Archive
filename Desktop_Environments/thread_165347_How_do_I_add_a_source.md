---
title: "How do I add a source?"
date: 2006-04-24
forum: Desktop Environments
---

### Post by scottylans on 2006-04-24
Sorry to post this but I don't know how fella's.

My ISP keeps a fairly fresh update of the ubuntu mirrors.
[ftp://ftp.iinet.net.au/pub/ubuntu/](ftp://ftp.iinet.net.au/pub/ubuntu/)

I'd love to add this as the ONLY site to get updates from, since it's fast and the traffic is "free" for me to download from.

Does anyone know how to do this? I'm guessing I need to do something in sources.lst right?

Also is there any way of installing dapper directly from that site? without even an install CD maybe just a boot CD? I'm pretty sure there is.

---

### Post by Ramses de Norre on 2006-04-24
add line ```
deb ftp://ftp.iinet.net.au/pub/ubuntu main restricted universe multiverse
```
and comment all the others, then run sudo apt-get update.
I'm not sure whether it will work but you can always delete the line and uncomment the others again.

---

### Post by aysiu on 2006-04-24
In case Ramses' post made no sense to you...

Go to Applications > Accessories > Terminal and copy and paste these commands: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
``` Paste in this line: ```
deb ftp://ftp.iinet.net.au/pub/ubuntu main restricted universe multiverse
``` and then save and ```
sudo apt-get update
```

---

### Post by scottylans on 2006-04-24
Thanks gentlemen that was great.


Now what about umm installing a fresh copy of dapper from the ftp site?

---

### Post by Ramses de Norre on 2006-04-24
I see I wasn't very clear, sorry. I posted it very quick.
First: you'll want to add this lines instead of the one I gave you (man I should think before I post..): ```
deb ftp://ftp.iinet.net.au/pub/ubuntu breezy main restricted universe multiverse
deb ftp://ftp.iinet.net.au/pub/ubuntu breezy-backports main restricted universe multiverse
deb ftp://ftp.iinet.net.au/pub/ubuntu breezy-proposed main restricted universe multiverse
deb ftp://ftp.iinet.net.au/pub/ubuntu breezy-security main restricted universe multiverse
deb ftp://ftp.iinet.net.au/pub/ubuntu breezy-updates main restricted universe multiverse
```
If you want to move to dapper change all the words breezy into dapper and run sudo apt-get update && sudo apt-get dist-upgrade.
Now my post should be correct ;)

---

### Post by scottylans on 2006-04-24
[QUOTE=Ramses de Norre]I see I wasn't very clear, sorry. I posted it very quick.
First: you'll want to add this lines instead of the one I gave you (man I should think before I post..): ```
deb ftp://ftp.iinet.net.au/pub/ubuntu breezy main restricted universe multiverse
deb ftp://ftp.iinet.net.au/pub/ubuntu breezy-backports main restricted universe multiverse
deb ftp://ftp.iinet.net.au/pub/ubuntu breezy-proposed main restricted universe multiverse
deb ftp://ftp.iinet.net.au/pub/ubuntu breezy-security main restricted universe multiverse
deb ftp://ftp.iinet.net.au/pub/ubuntu breezy-updates main restricted universe multiverse
```
If you want to move to dapper change all the words breezy into dapper and run sudo apt-get update && sudo apt-get dist-upgrade.
Now my post should be correct ;)[/QUOTE]



I figured out how to manually upgrade to dapper but what about a complete fresh install from either CD or network?
and since there's no dapper iso (at least on the ftp I linked) I guess a bootable CD which downloads it is best.

I'm sure this exists right?

---

### Post by scottylans on 2006-04-24
Anyone, anyone?

---

### Post by aysiu on 2006-04-25
[QUOTE=scottylans]
and since there's no dapper iso (at least on the ftp I linked) I guess a bootable CD which downloads it is best.[/QUOTE] [Here's](http://cdimage.ubuntulinux.org/daily/current/dapper-install-i386.iso) a Dapper ISO.

---

### Post by scottylans on 2006-04-25
[QUOTE=aysiu][Here's](http://cdimage.ubuntulinux.org/daily/current/dapper-install-i386.iso) a Dapper ISO.[/QUOTE]

Yes but it can be installed directly off the internet from a mirror right?
My isp hosts a mirror, full speed, doesn't add to my monthly quota.


All I need to know is how to do it.... I beleive years ago you used to make install floppy disks and then install from the net - can that be done?

---

### Post by mjm115 on 2006-04-25
[QUOTE=scottylans]Yes but it can be installed directly off the internet from a mirror right?
My isp hosts a mirror, full speed, doesn't add to my monthly quota.


All I need to know is how to do it.... I beleive years ago you used to make install floppy disks and then install from the net - can that be done?[/QUOTE]

Try taking a look [here]("https://wiki.ubuntu.com/Installation/Netboot?action=show&redirect=NetbootInstall").

---

### Post by scottylans on 2006-04-27
[QUOTE=mjm115]Try taking a look [here]("https://wiki.ubuntu.com/Installation/Netboot?action=show&redirect=NetbootInstall").[/QUOTE]


Sorry, I think you've mis-understood me.

I want to install on a laptop which can boot from USB / CD / Floppy / HDD etc (normal) but I want the SOURCE files to be downloaded from the internet? 

Like I add my ISPs' mirror to the sources.lst file on the installer CD and then simply partition / set stuff up but it downloads from the net?

Got me?

---

### Post by scottylans on 2006-05-01
[QUOTE=scottylans]Sorry, I think you've mis-understood me.

I want to install on a laptop which can boot from USB / CD / Floppy / HDD etc (normal) but I want the SOURCE files to be downloaded from the internet? 

Like I add my ISPs' mirror to the sources.lst file on the installer CD and then simply partition / set stuff up but it downloads from the net?

Got me?[/QUOTE]

anyone plz?

how to fresh install from the internet, using a boot cd? NOT boot installer cd?

---

### Post by Ramses de Norre on 2006-05-01
Why do you want to do it that way? Seems like it isn't that simple.. Guess you'll need to download an iso once and you can use you isp's repo to (dist-)upgrade after that.

---

### Post by scottylans on 2006-05-05
[QUOTE=Ramses de Norre]Why do you want to do it that way? Seems like it isn't that simple.. Guess you'll need to download an iso once and you can use you isp's repo to (dist-)upgrade after that.[/QUOTE]

I saw a guy do it 6 years ago with slackware :/

I was under the impression you boot up, point to a repository and install direct from the net?

---

### Post by scottylans on 2006-05-08
Anyone know? - I just wanna install it from the internet (not boot off the network card - but install from internet sources) ?

---

### Post by SkyNet2029 on 2006-05-08
Well, if you peruse this ftp directory (your isp's) :[ftp://ftp.iinet.net.au/pub]("ftp://ftp.iinet.net.au/pub") you will see the Ubuntu dist folder, which you can add as Installation source when using Ubuntu CD via expert installation option. (expert at boot prompt) . This is more than likely slower than the file transfer (local) between cd-hd media...but it would ensure a reasonably more up to date install...depending on your isp's mirror update of course, which is what you were after if I understood your question correctly.

---

