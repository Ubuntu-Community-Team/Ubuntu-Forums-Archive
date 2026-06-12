---
title: "how do i play mp3's"
date: 2007-02-17
forum: Desktop Environments
---

### Post by ikonone on 2007-02-17
hey everyone, 

i am just starting with this and i am running into a few problems. basically, i am just trying to do a few basic things to start with. i have a lot of music on my computer but it is in mp3 format and i would like to be able to play it.

so i read this:

[https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/music.html](https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/music.html)

so i went to the multimedia codecs section here:

[https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/codecs.html)

so then that took me to the repositories page here:

[https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/extra-repositories.html)

i found the 'universe' lines and they said that they needed to be uncommented. the repositories page said they just needed to be enabeled. not sure which is correct. anyway, i tried both. i assume that the two preceeding hash marks are the comment notation so i tried to delete them, however, whenever i would delete them and then try to select another line, the line i changed would revert back to the way it was before i edited it. 

well somehow, i got the first of the two 'universe' lines to be enabeled and got rid of the two hash marks but the word comment still preceeded it. i was not able to do it with the second line. i tried to apply to see what happened. after that i tried to get into adept again and i get the following message:

the APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

so i opened the terminal and entered those two lines, "apt-setup" and "apt-get update" and they were not recognized. what do i do? what have i done? even if i fix what i just screwed up, my next step is "installing the libxine-extracodecs package from the Multiverse repository" how do i do that, it just says to install but gives no details on how.

any help would be greatly appriciated!

chris

---

### Post by jure1873 on 2007-02-17
maybe adept won't start because there is an instance of it opened somewhere in the background, try checking the running processes with ksysguard or simply restart your pc. 
The lines in the /etc/apt/sources.list that you want to be enabled should start with deb or deb-src so remove anything that's before that. I think that in adept you can right-click and select enable/disable to do this. Or you can edit that file by yourself, if you think something is wrong with it.
To install the libxine-extracodecs package just enter libxine in adept and it will display packages matching that name, after that you click the request install button next to the wanted package and then click on the big green apply button at the top in adept.

---

### Post by ardchoille42 on 2007-02-18
xmms plays mp3's out of the box. No need to fiddle with codecs.

---

### Post by ikonone on 2007-02-19
> **jure1873 said:**
> maybe adept won't start because there is an instance of it opened somewhere in the background, try checking the running processes with ksysguard or simply restart your pc. 
The lines in the /etc/apt/sources.list that you want to be enabled should start with deb or deb-src so remove anything that's before that. I think that in adept you can right-click and select enable/disable to do this. Or you can edit that file by yourself, if you think something is wrong with it.
To install the libxine-extracodecs package just enter libxine in adept and it will display packages matching that name, after that you click the request install button next to the wanted package and then click on the big green apply button at the top in adept.

thanks for the advice. i do not see an instance of it open anywhere and i did not see it in the ksysguard either. i would just shut down my computer but ever since i installed kubuntu, it took away the restart or shut down options, all i can do now is hibernate. is this normal?

hmmm, anyway, i still can't get into adept. any ideas?

---

### Post by Mica on 2007-02-19
Easy: xmms plays mp3 fine for me.. i only have one problem my volume is a little bit low on Ubuntu.. but i don't have any problems with it now.. maybe i'll fix it later somehow xD

---

