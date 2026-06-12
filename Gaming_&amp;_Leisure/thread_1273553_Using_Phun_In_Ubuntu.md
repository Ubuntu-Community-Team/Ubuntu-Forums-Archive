---
title: "Using Phun In Ubuntu?"
date: 2009-09-23
forum: Gaming &amp; Leisure
---

### Post by Aaron_Griffiths_92 on 2009-09-23
Im stumped, i double click the executable file and click run then nothing happens, what do i need to do?

---

### Post by hikaricore on 2009-09-23
Try running it from a terminal.  Paste any output.

---

### Post by Bölvaður on 2009-09-23
oh god, dont say you downloaded something your self from a random website which didnt have any how-to to get it running.

if you did click on [this link to install phun]("apt:phun").
it will create a launcher under Applications &#8594; Games &#8594; Phun

---

### Post by lykwydchykyn on 2009-09-23
> **Bölvaður said:**
> oh god, dont say you downloaded something your self from a random website which didnt have any how-to to get it running.

if you did click on [this link to install phun]("apt:phun").
it will create a launcher under Applications &#8594; Games &#8594; Phun

Your link doesn't work, and anyway phun is not in the repos (at least not in Jaunty).

IIRC, there's a dependency you have to install to make Phun work -- libpng5 I think, but don't quote me on that.

Run it from the command prompt and paste the output, it should give the info needed.

---

### Post by Bölvaður on 2009-09-23
> **lykwydchykyn said:**
> Your link doesn't work, and anyway phun is not in the repos (at least not in Jaunty).

hmm you are right, it used to be but not any more.
But no worries it is in the playdeb/getdeb repos.

after you have done what is stated on this website my aptlink should work.
[http://www.playdeb.net/updates/#how_to_install]("http://www.playdeb.net/updates/#how_to_install")

---

### Post by Aaron_Griffiths_92 on 2009-09-23
i'll try that now

---

### Post by Aaron_Griffiths_92 on 2009-09-23
the repository update hits an error on file 53 of the update...


the error says:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) jaunty-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CFFailed to fetch [http://repository.cairo-dock.org/ubuntu/dists/jaunty/Release.gpg](http://repository.cairo-dock.org/ubuntu/dists/jaunty/Release.gpg)  
Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/jaunty/cairo-dock/i18n/Translation-en_GB.bz2](http://repository.cairo-dock.org/ubuntu/dists/jaunty/cairo-dock/i18n/Translation-en_GB.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Bölvaður on 2009-09-23
> **Aaron_Griffiths_92 said:**
> 
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the** public key** is not available:


hmmm ok this error states it self. It means that you dont have a key for the repos, which you can ignore to be honest.. but it is a security measure and it becomes annoying when it constantly notifies you that this repo hasnt a key for authentication of it's packages.


[CODE]wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -/CODE]


If this failed then this is what you should do



[LIST=1]
[*]Save [this file]("http://archive.getdeb.net/getdeb-archive.key") to your desktop.
[*]Open *System &#8594; Administration &#8594; **Software Sources***
[*]Go to the *Authentication* tab
[*]Click *+Add Key File...*
[*]Browse to your desktop and select the file named getdeb-archive.key
[*]Close Software Sources and let it refresh.
[*]Check if you can install Phun without this "error" again.
[*]Delete getdeb-archive.key from your desktop.
[*]Play Phun
[/LIST]

Man... a single command vs doing all that... I should have just broken up the command into 2 and made you copy paste it.... but.. what the Shreq

---

