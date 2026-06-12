---
title: "Printer configuration problems with CUPS"
date: 2011-10-04
forum: Desktop Environments
---

### Post by theronmuller on 2011-10-04
I recently moved and went from a Canon inkjet printer to a Brother HL-3040CN color laser printer, based on the fact that Brother has packages for Ubuntu on their site here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html")

Unfortunately I didn't read carefully enough and came to discover that the lpr package the Brother driver depends on is incompatible with cups, which is what I've been using since I started using Ubuntu three or four years ago.

Unfortunately, in the process of trying to install the Brother drivers, I've somehow screwed up my cups installation as well so that:
```
sudo apt-get -f install
```

returns:```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up cups (1.4.6-5ubuntu1.4) ...
invoke-rc.d: unknown initscript, /etc/init.d/cups not found.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 cups
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

...and I'm not sure how to go about fixing this problem. If at all possible I would much rather fix the problem at hand than have to reinstall my entire system.

Any help would be appreciated. Thanks in advance for your time and consideration.

---

