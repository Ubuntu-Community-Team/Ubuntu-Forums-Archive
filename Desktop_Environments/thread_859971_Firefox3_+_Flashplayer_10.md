---
title: "Firefox3 + Flashplayer 10"
date: 2008-07-15
forum: Desktop Environments
---

### Post by chrispottrell on 2008-07-15
Hi guys,

I currently have Firefox3.0 and flashplugin-nonfree, this loads Flashplayer 9.

I want to test Flashplayer 10 as I've read about the improvements.

I've tried overwritting the libflashplayer.so in every directory I can find, supposedly my firefox is starting from /usr/bin/firefox which is linked to usr/lib/firefox-3.0.

All the tutorials I've read, and the installation script from Adobe places the plugins in $home/.mozilla/plugins.

This doesn't seem to be the case for me, the only way I can get flash to work is via installing flashplugin-nonfree w/ nspluginwrapper (not sure why it installs the wrapper, im running 64bit chip but 32bit OS).

Is there a way I can start a fresh, remove all Flash/Firefox and make sure it controls plugins and what not from the home directories, it would make it a LOT easier for me to manage the users and their updates. the profiles are being created in $home it's just not loading plugins from there! Nightmare.

---

### Post by merlyn on 2008-07-15
G'day,

use apt-get purge, followed by the names of the packages you'd like to remove.

Separate the package names with a space if you need to remove more than one

For example, ```
sudo apt-get purge firefox-3.0 firefox-3.0-gnome-support flashplugin-nonfree
```

Once completed you'll have a clean slate. though this will only work if the packages in question were installed as .debs.

Cheers.

---

### Post by chrispottrell on 2008-07-15
How can I ensure it loads the plugins from the $home directory, is this a default when it is reinstalled freshly?

Cheers for the reply :) Much appreciated.

---

### Post by merlyn on 2008-07-15
I could be wrong, but my understanding is that any settings / plugin files etc that exist in your home profile directory take precedent over those located elsewhere.

---

### Post by chrispottrell on 2008-07-15
Well, thats what I thought, just in case I completely removed FF etc as you suggested.

In /home/$user/.mozilla/plugins I have libflashplayer.so

I open Firefox and have no flash :(

---

### Post by chrispottrell on 2008-07-15
Hmm, I have a 64bit machine running 32bit OS, does this have an impact on this installation?

I've just done some tests by removing Firefox and installing an all-in-one package I found on the forum, it installs Firefox32 and it loads the plugin fine from the $home directory.

I'm positive this is a 32bit Ubuntu installation, am I missing a blatant problem here? :S

---

### Post by merlyn on 2008-07-15
> **chrispottrell said:**
> Well, thats what I thought, just in case I completely removed FF etc as you suggested.

I didn't actually suggest that you remove firefox, just provided an example of how to use 'apt-get purge'.

If you do decide to remove firefox entirely, it would be worthwhile backing up your bookmarks and stored passwords.

There are addons for Firefox to assist with this.

> **chrispottrell said:**
> In /home/$user/.mozilla/plugins I have libflashplayer.so

I open Firefox and have no flash :(

To determine which plugins are installed correctly and working, open tools / addons / plugins from the menu bar.

Alternatively you can type ```
about:plugins
``` in the address bar.

> **chrispottrell said:**
> Hmm, I have a 64bit machine running 32bit OS, does this have an impact on this installation?

I run Ubuntu on a 32 bit system. As such I have no practical experience in this area.

A search of the forums dug this [howto]("http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox+64+bit") up, which you may find useful.

> **chrispottrell said:**
> I've just done some tests by removing Firefox and installing an all-in-one package I found on the forum, it installs Firefox32 and it loads the plugin fine from the $home directory.

Can I take it from this that Flash is now working for you?

> **chrispottrell said:**
> I'm positive this is a 32bit Ubuntu installation, am I missing a blatant problem here? :S

Can you elaborate regarding this problem please? Perhaps the howto I linked earlier on will be helpful.

Also I found [this thread]("http://ubuntuforums.org/showthread.php?t=795253") in the intrepid forums, which you may also find useful.

Cheers

---

### Post by Tomrade on 2008-07-15
According to konqueror my flash plugin is in usr/lib/iceweasel/plugins 

I use firefox 3 on kubuntu hardy try putting it there

Its really weird but i think you should try and find where the deb for flash 9 puts it or install flash 9 then replace the .so with 10

---

### Post by Tomrade on 2008-07-15
You could look here its a really good blog [http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/](http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/)

---

