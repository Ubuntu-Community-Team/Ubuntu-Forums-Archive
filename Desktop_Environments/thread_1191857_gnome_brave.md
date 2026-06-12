---
title: "gnome brave?"
date: 2009-06-19
forum: Desktop Environments
---

### Post by John M2009 on 2009-06-19
I have been trying to install themes with little success,  finally i found one that worked but get the message "this theme will not look look as intended beacuse the reqired icon theme gnome brave is not installed"  well,  i tried downloing it,  and tried installing it in the normal way,  but get another error message "does not appear to be a vailid theme"

I have been trying all sorts of things for the past hour,  and am starting to get very frustrated with it now....i want to try and get away from the very bland looking backgrounds.  Please help.

---

### Post by UbuntuNerd on 2009-06-19
post a link to the icon theme i'll try it out

---

### Post by John M2009 on 2009-06-19
heres the link...

[http://www.gnome-look.org/content/show.php/gnome-brave+custom+extras?content=97196](http://www.gnome-look.org/content/show.php/gnome-brave+custom+extras?content=97196)

---

### Post by UbuntuNerd on 2009-06-19
you might have to actually follow the instruction in that page to install the icons. the person who made them is using a script to install them.

---

### Post by John M2009 on 2009-06-19
I give up :(

Im too stupid to use Ubuntu

---

### Post by Therion on 2009-06-19
> **John M2009 said:**
> heres the link...

[http://www.gnome-look.org/content/show.php/gnome-brave+custom+extras?content=97196](http://www.gnome-look.org/content/show.php/gnome-brave+custom+extras?content=97196)


That's an UPDATE to a theme, not a theme package in and of itself:> Here is small update for gnome colors....



This is the DL link for the Icon Theme called **Gnome Colors**:

[http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562](http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562)

---

### Post by londonali1010 on 2009-06-19
Ah, I had this issue as well when I first installed Shiki Colours.  In order to install the Gnome Colours icons, you have to download the archive file from gnome-look.org.  Then extract it to a writeable folder (I always work in my /home/alison/Downloads/ folder).  The archive has several folders, all called things like gnome-brave, gnome-noble etc.  Then you have to copy all these folders into /usr/share/icons/, but you'll need to be root to do it.  You can either do it with sudo nautilus, or (like I did) via the command prompt by typing something like:
```
sudo mv /home/alison/Downloads/gnome-* /usr/share/icons/
```

Good luck...It's worth it!

---

### Post by UbuntuNerd on 2009-06-19
> **John M2009 said:**
> I give up :(

Im too stupid to use Ubuntu
i wouldn't say you stupid but I most say using Ubuntu is learning process and is very rewarding at least to me it is :D
I would just keep trying, look for a different theme !!!

---

### Post by Brandon Williams on 2009-06-19
Here's a step-by-step rundown of the commands to run to get gnome-colors installed from the gnome-colors PPA archive, including most of the expected output.
```
$ sudo -s
[sudo] password for user:
# apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2d79f61be8d31a30
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 2d79f61be8d31a30
gpg: requesting key E8D31A30 from hkp server keyserver.ubuntu.com
gpg: key E8D31A30: public key "Launchpad GNOME-Colors PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
# echo "deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu jaunty main" > /etc/apt/sources.list.d/gnome-colors.list
# apt-get update
[... skipping the output from this command ...]
# apt-get install gnome-colors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-human-icon-theme gnome-noble-icon-theme gnome-wine-icon-theme
  gnome-wise-icon-theme
Suggested packages:
  arc-colors shiki-colors arc-human shiki-human-theme arc-noble
  shiki-noble-theme arc-wine shiki-wine-theme arc-wise shiki-wise-theme
The following NEW packages will be installed:
  gnome-colors gnome-human-icon-theme gnome-noble-icon-theme
  gnome-wine-icon-theme gnome-wise-icon-theme
0 upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
Need to get 15.5MB of archives.
After this operation, 80.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
[... skipping the rest of the output from this command ...]
# exit
```
I recommend installing shiki-colors, too. It's a nice set of themes that uses the gnome-colors icon sets.

---

### Post by Sarai the Geek on 2009-06-19
The version from the PPA is apparently quite out of date- it's better to install it yourself via the archive.
Download the archive from here: [http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562](http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562) and save them to your desktop.
Then, enter these commands in your terminal, one after another-
```
cd ~/Desktop/
tar -xf gnome-colors-3.9.4.tar.gz
tar -xf gnome-brave.tar.gz
tar -xf gnome-human.tar.gz
tar -xf gnome-noble.tar.gz
tar -xf gnome-wine.tar.gz
tar -xf gnome-wise.tar.gz
sudo rm gnome-*.tar.gz
sudo mv gnome-* /usr/share/icons
```

And you're done! If you only want to add ONE of the color schemes, you can follow THIS instead:

```
cd ~/Desktop/
tar -xf gnome-colors-3.9.4.tar.gz
tar -xf gnome-**COLOR**.tar.gz
sudo rm gnome-*.tar.gz
sudo mv gnome-* /usr/share/icons
```
Where COLOR is "brave" (blue), "wine" (red), "noble" (purple), "wise" (green) or "human" (orange).
But I'd recommend just installing them all. :)

---

### Post by Brandon Williams on 2009-06-20
> **Sarai the Geek said:**
> The version from the PPA is apparently quite out of date.
The version in the PPA is kept very up-to-date. It's has the latest versions as of yesterday. Changes that happened over the past 24 hours aren't reflected yet, but based on experience, they will be soon. I recommend using the PPA specifically because it will keep you up-to-date without having to check back on gnome-look.org or google-code.com to find out whether there have been any changes.

Also, having seen the OP's other posts here (and elsewhere), I realize that a list of commands to run without the interspersed expected output is probably a good idea, so here goes:
```
sudo -s
. /etc/lsb-release
apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2d79f61be8d31a30
echo "deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu $DISTRIB_CODENAME main" > /etc/apt/sources.list.d/gnome-colors.list
apt-get update
apt-get install shiki-colors gnome-colors
exit
```

And here's an explanation of each commands, since I know that the OP is very new to linux.

'sudo -s' will take you to a command line with super-user privilege so that you can make system-level changes. 

'. /etc/lsb-release' will put some information about your current installation into the environment for later use. 

'apt-key ...' will add the keys for the gnome-colors software archive to your system so that software packages from that archive can be authenticated. 

The 'echo' line adds the gnome-colors archive to your system's list of archives. 

'apt-get udpate' will update the full list of all software available in all archives that the system knows about. 

'apt-get install shiki-colors gnome-colors' will install the shiki-colors theme and the required gnome-colors icons. 

'exit' will close the super-user command line so that you don't make accidental changes later that break your system.

---

