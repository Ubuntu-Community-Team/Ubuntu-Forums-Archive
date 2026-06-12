---
title: "Can't update Clam Antivirus/clamtk"
date: 2009-03-05
forum: General Help
---

### Post by ifindcomputersreallyhard on 2009-03-05
Greetings, all.

Hope this hasn't partially appeared elsewhere - I paged bck to check something, returned here and found my text had disappeared.

After successfully avoiding computers for over four decades, I recently discovered them to be quite interesting. I managed to install Ubuntu 8.10 on an old desktop.

Although I realise that anti-virus software isn't as vital as is the case on Windows (where all my limited computer experience lies), I prefer to have it available. I regularly e-mail friends with Windows computers, and I transfer files between this and my Windows machines (using e-mail, usb flash drives, CD/DVD and floppy discs).

Following instructions on the following site:

[http://ubuntuexperiment.wordpress.com/2009/01/23/installing-clamav-antivirus-software-on-ubuntu-810/](http://ubuntuexperiment.wordpress.com/2009/01/23/installing-clamav-antivirus-software-on-ubuntu-810/) 

I installed ClamAV, using terminal commands (definitely a new experience) for the bulk of the packages, and downloading the clamtk GUI from SourceForge, as directed in the above article.

Alas, I wasn't paying attention fully, and installed the app as a single user (forget the exact term and every time I try to go back to look, I lose everything I've written here.)

Whenever I try to update the Clam AV database, I'm advised "Update Failed." I've now tried to fully uninstall and reinstall the whole Clam AV package three times in hope of getting the necessary options when opening the ClamTK window the first time - but it always defaults to what I thought I had uninstalled, and warns me that my last virus data-base update took place on the 18th February. 

I uninstalled through the Synaptics Package Manager; it seemed to show that there was nothing left each time.

When I try to update, there is no mention of having to sign in as root, which seems to crop up on forums - presumably doesn't apply to this version (Ubuntu 8.10). It simply says "Update Failed," and is beginning to really annoy me - not least of all because it's doubtless something I'm doing wrong.

I also have Firestarter Firewall, which seems to need launching manually (when I remember) every time I start the computer, and whose workings remain a complete mystery - so far, it seems to do nothing unless I use Skype, when it has great fun blocking all sorts of things - Skype still works, though.

I've tried updating with Firestarter disabled (I think - no visible sign of it), in case it's blocking updates - doesn't seem to help.

If anyone has any suggestions, I'd be very grateful. Apologies in advance if I take a day or two to respond - it's getting near my bed-time! - but I'll watch for an hour or so, then check every couple of days.

Thanks for slogging through this long post. And - deeply grateful though I'll be for assistance, please remember that what I know about computers generally, and Linux specifically, is next to nothing! Only recently figured out what a terminal was, for instance...

Thanks again!

---

### Post by Rallg on 2009-03-05
If you have ever uninstalled a program in Windows, you know that it can leave settings behind, either in the registry, or in a hidden Documents and Settings folder. Re-install, and your prior settings are still there. Ubuntu does something similar, sometimes.

To clean everything: First, uninstall the program in usual fashion. Whether or not you need to use sudo (in most cases, you do) depends on how you installed it in the first place. If you do it with Synaptic Package manager, you are doing it with sudo (that's why Synaptic asks for your password on the way in).

Then, open your user Home directory. Make hidden files visible. Look for a folder that might relate to the now-removed program. The folder name will begin with a dot (indicating it is hidden). Might be something like .clamav, but I don't know. Delete the folder.

If you really need to be thorough, then you might have to do the same thing with root privileges. In Terminal:

gksudo nautilus

will open the file manager in a new window (note that in Kubuntu or Xubuntu, it is something other than nautilus).

Make hidden files visible, and poke around for folders that might contain settings for your removed program. If you are sure that's what they are, then delete them. If course, if you mistakenly delete something that serves another purpose, then you will have a problem. A common complaint is that in Linux, there are many different places where bits and pieces could be stored.

Particularly go to the /etc folder, and see if there is any folder or file that appears to contain settings that you should delete. Also look in the root home folder.

There are a few other possibilities. For example, the info could be added within a file that actually contains a variety of settings, not just for clamav. But I would not know what they are.

Then, try a re-install. Do not guess whether the program should be installed as user or root (sudo); follow instructions.

As for "sign in as root," that can mean one of several things. It is possible to log in as root, without ever using your user name. That is not often done with Ubuntu, since there is no separate password for root (other versions of Linux may do it that way). Or, it could mean booting to the "recovery" mode, which is a command terminal, then switching to root. More likely than not, in Ubuntu, it means logging in as normal user, then opening a Terminal, then using sudo:

sudo enter-some-command-here

It will ask for your password, grant you temporary root privileges, then (if possible) do what you ask. Do not use sudo if you do not need to use it.

In some cases, that is not good enough. You can switch to being root (rather than merely asking for privileges), like this:

sudo -s

After you enter your password, you are now root. You will notice that the prompt ends in a hash (indicates root) rather than dollar sign (indicates user). Now that you are root, you can enter your commands without needing sudo. To leave root, use the exit command, or simply close the Terminal. Do not forget to exit root before using the Terminal for other purposes!

---

### Post by ifindcomputersreallyhard on 2009-03-05
GOODNESS, but Ubuntu's complicated! Good for the soul, no doubt.

Many thanks for the advice - I'll give that try.

Much appreciated!

---

### Post by dcstar on 2009-03-05
> **ifindcomputersreallyhard said:**
> 
.......
Whenever I try to update the Clam AV database, I'm advised "Update Failed." I've now tried to fully uninstall and reinstall the whole Clam AV package three times in hope of getting the necessary options when opening the ClamTK window the first time - but it always defaults to what I thought I had uninstalled, and warns me that my last virus data-base update took place on the 18th February. 
.......

The **clamav-freshclam** package automatically updates clamav, you just install that and there is no need to muck around with anything else.

---

### Post by ifindcomputersreallyhard on 2009-03-05
Thanks very very much for the assistance.

I now seem to have a functioning and up-to-date AV. The comment about the automatic updating is interesting - I wondered why there was no option to manually update.

And Rallg, you were dead right. There was still a clamtk folder (hidden) lurking in the home directory when I thought I'd finished uninstalling. Getting rid of that allowed a full re-install.

Many thanks again, everybody - hopefully resolved!

---

### Post by ajgreeny on 2009-03-05
For future reference, to enable root privileges in a gui application it should be ```
gksudo nautilus
```, not sudo, that is for terminal applications, eg apt-get.  For kde (kubuntu) it is ```
kdesu konqueror
``` or ```
kdesu dolphin
```.  Not sure about xubuntu, perhaps ```
gksudo thunar
```Using sudo for a gui can, but seldom does, lock you out completely.  See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by joshaman on 2009-03-15
> The clamav-freshclam package automatically updates clamav, you just install that and there is no need to muck around with anything else.

This updates clamav, or the virus database?  Is it the the same function as "Update Signatures" in ClamTk?

why doesn't someone just update the repositories with the latest ClamTk?

---

### Post by JDorfler on 2009-03-15
For the launcher, edit the command for clamtk to be gksudo clamtk, and you should be able to download the files you want without any problems.

---

### Post by squirtmph on 2009-10-18
I was reading the other day a book on Ubuntu is Called Linux - Tool box I believe it's new book.
any way this what it say:
> wget [http://db.local.clamav.net/daily.cvd](http://db.local.clamav.net/daily.cvd)This will put update file into the ClamAV folder so that the application will use the latest signatures: ( I didn't know it was update list)
> sudo mv daily.cvd /var/lib/clamavso I would like to know any opinion abut what this author says on moving this file & terminal command to use......... as far I understand we dont need to do nothing ales to update the software ClamAV

please let me know, any opinion about it.
thank you

---

