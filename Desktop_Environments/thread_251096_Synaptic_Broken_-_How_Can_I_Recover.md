---
title: "Synaptic Broken - How Can I Recover?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Niwotian60 on 2006-09-04
I followed the steps in the ubunto dapper "howto" guide to install jedit (my editor of choice on Windows).  The steps I followed are exactly as defined [here.]("http://ubuntuguide.org/wiki/Dapper#How_to_install_jedit")

Unfortunately, the dpkg installation failed with a serious error. From then on, every time I try to use Synaptic or install from apt-get I get the following errors;

E: The package jedit needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Synaptic doesn't display any packages at all and I'm unable to use apt-get to install anything either.  How can I recover from this?

<< side note: I was able to install jedit much easier simply by downloading the jedit installation jar from [www.jedit.org](www.jedit.org) and running 'java -jar jedit4.3pre6install.jar' .  The simple gui set it up perfectly. >>

---

### Post by catlett on 2006-09-05
Try removing the deb or even more purging the deb. Run this command 
```
sudo dpkg -r jedit_4.3pre6_all.deb
```
If that didn't do it try to purge it with 
```
sudo dpkg -P jedit_4.3pre6_all.deb
```
If that doesn't work try opening Synaptic Package Manger and search for the package. Either search for jedit or use broken as the search parameter. Try re-installing or removing.
If all that fails, try re-downloading the file and then re-install/unintsall it.
```
wget -c http://optusnet.dl.sourceforge.net/sourceforge/jedit/jedit_4.3pre6_all.deb
```
Then run the install again since it is asking you to reinstall
```
sudo dpkg -i jedit_4.3pre6_all.deb
```
Sorry to not have a definate answer. I just start trouble shooting with whatever I can when I have a new error come up.

P.S. apt keeps all installed packages debs in /var/apt/cache/archives. See if the deb is in there from the wget install. Double click it and start the install. Maybe that will satisfy the "reinstall" need

---

### Post by Niwotian60 on 2006-09-05
> **catlett said:**
> Try removing the deb or even more purging the deb. Run this command 
```
sudo dpkg -r jedit_4.3pre6_all.deb
```
If that didn't do it try to purge it with 
```
sudo dpkg -P jedit_4.3pre6_all.deb
```
I tried both of those things before posting, but they are good suggestions so I tried them again.  No joy.
> If that doesn't work try opening Synaptic Package Manger and search for the package. Either search for jedit or use broken as the search parameter. Try re-installing or removing.
Synaptic wouldn't let me do anything. Nothing showed up in broke or any of the sections. No packages were displayed anywhere and I couldn't even reload them.
> If all that fails, try re-downloading the file and then re-install/unintsall it.
```
wget -c http://optusnet.dl.sourceforge.net/sourceforge/jedit/jedit_4.3pre6_all.deb
sudo dpkg -i jedit_4.3pre6_all.deb
```
I had tried this as well before I posted but I figured why not. Again, it failed, but this time I took a good look at what the errors were.  It appears that in the install script at times it wants to install files in "/usr/share/doc/jEdit" and at times in "/usr/share/jEdit/doc" (note the transposition. So I sudo mkdir'd both directories in advance and reran the script.  It again failed, but this time with a new error that it couldn't find a cleanup script.  But this last step fixed everything with apt-get and Synaptic!

> Sorry to not have a definate answer. I just start trouble shooting with whatever I can when I have a new error come up.
No apologies! I appreciate anyone willing to provide thoughts and advice.

I just started using Linux over the weekend (I used Unix in college, so it wasn't totally new) and I've managed to set up a server and laptop with Linux, Apache/SSL, Geronimo, Java 1.5.8, SAMBA, WPA2-secured wireless, FireStarter, Nvidia drivers, etc.  I muddled through issues in just about every one of these things (note to everyone: if you are using WPA/WPA2, do not hide the SSID and save yourself a ton of headaches!), but I'm starting to get a feeling for how things work!

---

### Post by dleuen on 2006-09-05
I just ran into this same problem with jEdit 2 weeks ago. From the dpkg man page:

> 
reinst-required
        A package marked reinst-required is broken and requires
        reinstallation. These packages cannot be removed, unless
        forced with option --force-remove-reinstreq.


Give that a go, it worked for me.

Don

---

