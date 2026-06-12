---
title: "Logging into a terminal rather than the Ubuntu desktop"
date: 2018-08-02
forum: Desktop Environments
---

### Post by robertcull1 on 2018-08-02
Ubuntu 16.04.5 LTS

On the advice of someone working at "zoom" technical support I reinstalled a bunch of dependencies using Synaptic Package Manager to try and get zoom going. Unfortunately it produced another problem. Now it starts up into a terminal instead of the Ubuntu desktop. I login and then I come to a bash prompt.

I have tried:

# startx
xauth: timeout in locking authority file /home/<user>/.Xauthority

then the screen blanks out for about 30 seconds. Then I get another prompt where the text is very tiny, but when I type nothing shows up on the display.

I really need to repair this rather than do a new Ubuntu installation  because I have a lot of precious files that I don't want to lose. If there is another forum where I could post this problem where I would be more likely to get help, please suggest it to me.

These are the dependencies that I reinstalled with Synaptic Package Manager.
libglib2.0-0
libgstreamer-plugins-base0.10- 0 
libxcb-shape0
libxcb-shm0
libxcb-xfixes0
libxcb-randr0
libxcb-image0
libfontconfig1
libgl1-mesa-glx
libxi6
libsm6
libxrender1
libpulse0
libxcomposite1
libxslt1.1
libsqlite3-0
libxcb-keysyms1
libxcb-xtest0

---

### Post by ajgreeny on 2018-08-03
From the command-line login I think you should try ```
sudo apt install --reinstall ubuntu-desktop
``` which may make sure anything that is missing is brought back into your system.

Was anything removed when you installed those missing dependencies, and do you have any idea why they were missing in the first place?
If you know when the dependencies were added you can look for removed packages at that time with command ```
grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log
``` which will list amnything removed and show the date and time that it happened.

Perhaps you have installed some packages from sources other than the usual ubuntu repos which require a different version of those dependency packages?

---

### Post by robertcull1 on 2018-08-03
```

# sudo apt-get install --reinstall ubuntu-desktop > temp.txt
# grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log > templog1.txt
```
The output for both these commands was beyond the allowably size to attach to this post.

I was not able to connect to the internet by wifi or ether-net cable. So I expect these commands would not work anyway.

Currently I believe I am using the Unity or Ubuntu desktop for 16.04 LTS. I believe that 18.04 LTS uses the Gnome desktop. I believe that there is an upgrade option when using the 18.04 LTS installation flash drive. If I understand it correctly, when you upgrade it preserves your files, drivers, and previously installed programs.

This is particularly important for me because I want to preserve my bookmarks in Firefox and my emails in Mozilla Thunderbird email client.

I wonder, since an upgrade to 18.04 LTS would install the Gnome desktop, would that fix my dependencies and get me into the Gnome GUI?

---

### Post by SeijiSensei on 2018-08-04
Backing up your home directory will preserve your bookmarks and emails. /home/username/.thunderbird and /home/username/.mozilla contain all the material you want to preserve.

Note the leading dots in those directory names. They are "hidden" but can be viewed from the command prompt with "ls -a" or from a GUI file manager like Nautilus after exposing hidden files and directories.

---

### Post by hrsetrdr on 2018-08-04
A quick and simple thing I do:   boot system to a 'live' session in Linux, and navigate to your /home and copy files to USB or other media.  Done.

I do this for friends that are Windows users.  Grab date and re-install OS.    Your Ubuntu install is 'fixable' but grab data anyway.

---

### Post by robertcull1 on 2018-08-05
I was not able to upgrade and save my files with an upgrade. But I was able to backup my desktop from the command line to a flash drive and then restore my desktop and home directory after the reinstall.

Thanks everyone!

---

