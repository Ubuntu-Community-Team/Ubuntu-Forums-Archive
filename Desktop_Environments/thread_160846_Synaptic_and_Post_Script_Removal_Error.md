---
title: "Synaptic and Post Script Removal Error"
date: 2006-04-15
forum: Desktop Environments
---

### Post by totfit on 2006-04-15
Synaptic is totally hung up because of the following error:

E: mozilla-thunderbird-enigmail: subprocess post-removal script returned error exit status 1


I can neither install or remove programs with synaptic, because it insists on removing enigmail first and can't seem to pull it off. I can't find enigmail in Thunderbird, though I do recall seeing it at one time. Not sure where it could be. Does anyone have experience with this problem? Much would be appreciated. Have just been using Linux Ubuntu flavored since the end of January. I use it 100% of the time now, both desktop and laptop. Have gone through the scanner and laptop wireless issues and this has me stumped. Thanks in advance.

Gregg

---

### Post by Ramses de Norre on 2006-04-15
sudo apt-get install -f && sudo apt-get remove mozilla-thunderbird-enigmail
may be able to solve it.

---

### Post by totfit on 2006-04-15
Thanks for the reply. Had already tried apt-get. Here is what I get:

gregg@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  mozilla-thunderbird-enigmail
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
Need to get 0B of archives.
After unpacking 1438kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162658 files and directories currently installed.)
Removing mozilla-thunderbird-enigmail ...
Updating mozilla-thunderbird chrome registry...find: /usr/lib/mozilla-thunderbir d/defaults/profile/extensions/: No such file or directory
E: /usr/lib/mozilla-thunderbird/extensions/installed-extensions.txt still presen t. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-thunderbird/defaults.ini': No such file or dir ectory
dpkg: error processing mozilla-thunderbird-enigmail (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 mozilla-thunderbird-enigmail
E: Sub-process /usr/bin/dpkg returned an error code (1)
gregg@ubuntu:~$ sudo apt-get remove mozilla-thunderbird-enigmail
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mozilla-thunderbird-enigmail
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
Need to get 0B of archives.
After unpacking 1438kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162658 files and directories currently installed.)
Removing mozilla-thunderbird-enigmail ...
Updating mozilla-thunderbird chrome registry...find: /usr/lib/mozilla-thunderbird/defaults/profile/extensions/: No such file or directory
E: /usr/lib/mozilla-thunderbird/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-thunderbird/defaults.ini': No such file or directory
dpkg: error processing mozilla-thunderbird-enigmail (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 mozilla-thunderbird-enigmail
E: Sub-process /usr/bin/dpkg returned an error code (1)
gregg@ubuntu:~$
gregg@ubuntu:~$


It seems that I have to remove enigmail, but it can't be found to remove. Can't find any reference to the old Thunderbird in my folders. Problem is the extension is present and I have upgraded to 1.5, where the extension won't function. I am perplexed. 

Thanks,
Gregg

---

### Post by totfit on 2006-04-16
Just in case anyone needs this, I found a solution. The only thing that I could figure to do was downgrade Thunderbird to its previous version. I also deleted any mention of enigmail in the var/lib/dpkg/info file. Tried to delete only first and it didn't work. There is for some reason a bug/conflict with enigmail and installation of Thunderbird 1.5. I now have access to updates, upgrades and installations. Only thing I can figure is that downgrading eliminated the conflict.

Gregg

---

### Post by cjj on 2006-04-26
Gregg, 

Can I ask how you downgraded? I have the same exact problem...actually I am thinking that thunderbird 1.0 may be better for me since I like enigmail and the vtiger integration (neither available in 1.5). I was tempted to upgrade in search of vCard support, which I didn't find. 

Anyway, so I would like to fix the problem with packages and downgrading sounds great - any tips on doing so? 

Thanks!

Chris

](*,)

---

### Post by totfit on 2006-04-26
Chris, if I recall correctly, I just found 1.5 in Synaptic and marked it. It asked if I wanted to downgrade. It worked for me. Good luck.

---

### Post by cjj on 2006-04-27
Thanks, Gregg. Apprehensively I tried and then installed thunderbird 1 and it worked! :) Even kept my settings (I didn't get a message about downgrading).

But it still hung on the enigmail part. I reinstalled that and now everything seems to be fine again. 

Thanks again,

Chris

---

