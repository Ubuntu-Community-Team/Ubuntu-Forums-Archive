---
title: "Firefox stops seeing drives"
date: 2019-02-04
forum: Desktop Environments
---

### Post by tapasray on 2019-02-04
I have been using Firefox in Ubuntu for years. Suddenly, two problems have come up.

1. It has stopped reading any drive - a partition on the hard drive, a USB stick and an SD card. The only drive it sees is the partition on which Ubuntu is installed.

2. I am unable to enter anything in certain web form fields. The cursor blinks in the field, but does not respond to the 'space' command, and keyboard inputs are not registered.

I have uninstalled and reinstalled Firefox, updated Ubuntu and run its broken packages repair function from the boot menu,but the problems have persisted.

Help will be greatly appreciated.

---

### Post by walts48 on 2019-02-04
Have you tried a "Refresh Firefox..." ?

[https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings](https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings)

---

### Post by tapasray on 2019-02-04
Thanks, walts48. I haven't ... going to try it now.

'Refreshed', but it did not help.

---

### Post by ajgreeny on 2019-02-04
With FF closed down try renaming the hidden .mozilla folder in your home with command ```
mv .mozilla .mozilla~
``` then restart FF to see if that has solved the problem.

This is most likely a corruption of some sort in your configuration, though a refresh of FF would often sort that out.

---

### Post by tapasray on 2019-02-05
Thank you, @ajgreeny. Trying it.

@ajgreeny, the terminal did not respond to that command. I mean, when I entered the code and hit enter, the command prompt came back. Nothing else happened.

So I searched for 'mozilla' and found the following folders:
.mozilla~   at /home/username
.mozilla     at /home/username/.cache
.mozilla     at /home/username//snap/firefox/common
.mozilla     at /home/username//snap/firefox/common/cache
.mozilla     at /home/username/.local/share/Trash/files

Following an intuition, I changed the name of the 3rd one to .mozilla- and opened Firefox. A fresh window opened up, without my history, favourites, etc. But the problem remained. It did not see any drive or partition other than the one on which Ubuntu resides.

---

### Post by ajgreeny on 2019-02-05
> **tapasray said:**
> @ajgreeny, the terminal did not respond to that command. I mean, when I entered the code and hit enter, the command prompt came back. Nothing else happened.

This is what I expected and means that the command worked as it should! If it had failed you would have seen an error message.

> **tapasray said:**
> So I searched for 'mozilla' and found the following folders:
.mozilla~   at /home/username
.mozilla     at /home/username/.cache
.mozilla     at /home/username//snap/firefox/common
.mozilla     at /home/username//snap/firefox/common/cache
.mozilla     at /home/username/.local/share/Trash/files

Following an intuition, I changed the name of the 3rd one to .mozilla- and opened Firefox. A fresh window opened up, without my history, favourites, etc. But the problem remained. It did not see any drive or partition other than the one on which Ubuntu resides.
All that is normal, but it means that my suggestion was unfortunately not a solution to your problem.

You can try downloading FF direct from [https://www.mozilla.org/en-GB/firefox/download/thanks/](https://www.mozilla.org/en-GB/firefox/download/thanks/) then extracting the archive to a folder and running the executable direct from the extracted folder; if that runs as it should, your downloaded .deb package of FF from the repos may be corrupt, so remove the FF packages from the package archive with ```
sudo rm -i /var/cache/apt/archives/firefox*
```
You will be asked if you wish to remove each file so can check removal of each file, one by one.
Once finished try reinstalling FF again from the repos as usual.

Finally can you confirm your version of Ubuntu and also of Firefox for us.

EDIT:
I've just noticed you have a snap version of FF at present, so I suggest to remove that with command ```
snap remove *firefox*
``` and then use the repos version in its place.
I have never used any snap packages so I'm not sure how the snap version of FF is named but you can find it with command ```
snap list
``` and then adjust the snap remove command accordingly.
Once you have removed the snap package use command ```
sudo apt install firefox
``` to reinstall the repos version which I suspect will work properly again.

---

### Post by tapasray on 2019-02-05
Thank you. Will try this.

My OS is Ubuntu 18.04.1 LTS, 64-bit, and Firefox is 65.0 (64-bit), Mozilla Firefox Snap for Ubuntu, Canonical-002-1.0.

@ajgreeny, thank you for all the trouble you are taking.

I uninstalled Firefox with the Ubuntu software installer. Then ran the ```
 sudo rm -i /var/cache/apt/archives/firefox* 
``` - its output was "rm: cannot remove '/var/cache/apt/archives/firefox*': No such file or directory".

Ran ```
 snap remove firefox 
``` -- the output was "snap "firefox" is not installed". 

Downloaded a Firefox .deb file from Sourceforge and tried to install it with Ubuntu software installer, but the installer window with the "Install" button kept coming back. Screen shot attached.

Also tried to install the Tor client. The software installer window indicates installation complete and offers the 'Launch' button. But nothing happens when I click on it. Also, the tor icon does not appear in the list of applications.

---

### Post by ajgreeny on 2019-02-08
**Do not use a firefox package from sourceforge**; use the Ubuntu repos instead to get the best from your system.

Simply run the command I showed you last time ```
sudo apt install firefox
```
Whenever possible you should use the Ubuntu repos, not download packages from third parties and install those.

---

### Post by tapasray on 2019-02-09
I tried out Opera and experienced the same problem with it: It does not see any drive/partition other than the one on which Ubuntu is installed. But Chrome still sees all drives.

Since the problem shows up in two different browsers, I wonder if the issue is with Ubuntu and not with these browsers.

---

### Post by ajgreeny on 2019-02-09
I am a bit confused so let's go back to the beginning.

In what manner do you expect FF to be able to "see" the other disks or partitions; what happens if you try to open an html file on one of those partitions by right clicking and choosing "Open with firefox"? Does that file open or does an error message appear telling you that the file does not exist?

Are those disks and partitions accessible to you as a user, what filesystem are they formatted as, and are they always mounted when you're trying to get FF to "see" them?

I wonder if this is a permissions problem of some sort?

---

