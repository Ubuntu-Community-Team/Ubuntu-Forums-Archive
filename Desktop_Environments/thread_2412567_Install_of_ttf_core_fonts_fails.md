---
title: "Install of ttf core fonts fails"
date: 2019-02-14
forum: Desktop Environments
---

### Post by johnaaronrose on 2019-02-14
In 18.04: when I do "sudo apt install ttf-mscorefonts-installer" & say Yes to the EULA question, it fails:ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) [198 kB]
Fetched 198 kB in 16s (12.2 kB/s)                                              
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
Err:1 [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
  Redirection from https to 'http://downloads.sourceforge.net/mirrorproblem?failedmirror=netix.dl.sourceforge.net' is forbidden [IP: 87.121.121.2 443]
E: Failed to fetch [https://netix.dl.sourceforge.net/project/corefonts/the](https://netix.dl.sourceforge.net/project/corefonts/the) fonts/final/arial32.exe  Redirection from https to 'http://downloads.sourceforge.net/mirrorproblem?failedmirror=netix.dl.sourceforge.net' is forbidden [IP: 87.121.121.2 443]
E: Download Failed

I've tried it repeatedly today after doing "sudo apt purge ttf-mscorefonts-installer" followed by "sudo apt install ttf-mscorefonts-installer".

Any ideas please?

---

### Post by howefield on 2019-02-14
As a workaround...

Create a folder in ~/home called mscorefonts and download the fonts from : 

```
https://sourceforge.net/projects/corefonts/files/the%20fonts/final/
```

and store them in the /home/$USER/mscorefonts folder that you created earlier, then run..

```
sudo dpkg-reconfigure ttf-mscorefonts-installer
```

You should be prompted to give the path for the downloaded files and the rest should be self explanatory.

---

### Post by johnaaronrose on 2019-02-14
Thanks, howefield. Workaround Ok.

---

### Post by howefield on 2019-02-14
> **johnaaronrose said:**
> Thanks, howefield. Workaround Ok.

Cool, might be worth saving a copy of the fonts. This happens all too regularly with the ttf-mscorefonts-installer package.

---

