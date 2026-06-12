---
title: "screenlets"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by rygar on 2007-05-04
Hi, I'm a new user to Ubuntu/Linux.
I'm running Feisty Fawn with Beryl on gnome, and i need a good "widget" tool.

First I tried gDesklets, which is pretty awful in comparison to offerings on Vista/OSX.

Now I'm trying Screenlets.  Aesthetically, it's much better and i think i'll keep it but i have a few questions.

1) is there a website maintained where i can get more screenlets than just the ones that come with it?

2) is there any way to hide/show screenlets, or 'bring to front'?
ideally, i think i'd like to hide them altogether and just bring them up with a shortcut key.
at the very least, i'd like to keep them on my desktop and have them surface above my windows when i press a shortcut key.  i managed to accomplish this in gDesklets, but can't seem to figure it out with Screenlets.
any help?

thanks!
jeff

---

### Post by aidanr on 2007-05-04
the widget layer plugin in beryl does this, it's under desktop plugins

---

### Post by rygar on 2007-05-04
there is no widgets desktop plugin in beryl

how do i get it?

---

### Post by aidanr on 2007-05-04
which version are you using, i'm using 0.3.0 git from [http://download.tuxfamily.org/3v1deb/index.html](http://download.tuxfamily.org/3v1deb/index.html) and it's in beryl-plugins

---

### Post by rygar on 2007-05-04
0.2.1 i think--that's what synaptic package manager tells me.  it's what ubuntu installed on my machine from add/remove programs.  how do i upgrade?

also, i've got a bigger problem now--i tried to add a checkmail screenlet,and it says cannot contact server and freezes all of my screenlets.

i cant stop the screenlets daemon either (screenletsd stop).  i have to restart my computer to restart screenletsd, which doesn't help, because every time i open it, it freezes all of my screenlets.

i tried removing screenlets from synpatic, then re-installing it, but it always brings back the same screenlets i had  before.

help!
thanks!
jeff!

---

### Post by aidanr on 2007-05-04
ok, to upgrade to the git packages, open a terminal and type:
```
gksudo software-properties-gtk
```
go to third party -> add, and copy in either

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
or
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

depending on whether you are on edgy or feisty, then copy in a terminal:
```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add - && sudo aptitude update && sudo aptitude upgrade
```

that's it, logout and log back in, remember these are "unstable" packages so use at your own risk, although i haven't had any issues with them

as for the screenlets issue, is there a hidden screenlets folder in your home directory (something like ~/.screenlets) if so delete it, also remeber it is pretty early in developement so it probably has issues

---

### Post by rygar on 2007-05-04
there was an empty directory called .screenlets in my /home/user which i deleted, but it didnt help :(
there's got to be some way to get ubuntu to forget which screenlets i've loaded, no?

the beryl upgrade didn't work either--a screen pops up and says "Error authenticating some packages"...

:(

---

### Post by aidanr on 2007-05-04
strange, mark screenlets for complete removal in synaptic, then do a ```
sudo updatedb
locate screenlets
``` see if it left any traces and then reinstall it

"Error authenticating some packages", huh.. make sure you hit reload in synaptic and make sure the authentication key has been added, go into authentication in software-properties-gtk and make sure the Trevino key is listed

---

### Post by rygar on 2007-05-04
i got Screenlets working again with the help of
[http://ubuntuforums.org/showthread.php?t=356314&page=14&highlight=screenlets](http://ubuntuforums.org/showthread.php?t=356314&page=14&highlight=screenlets)

( /home/user/.config/Screenlets directory needed to be removed)


when i hit reload in synaptic i get:

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA

i don't think it's adding the keys properly, when i go to the 'Authentication' tab, tuxfamily.org isn't listed.  i typed exactly what you said though!

---

### Post by rygar on 2007-05-05
i got the Trevino key to appear! somehow.  the beryl-project one still isn't there but ill worry about that later.

thanks so much for your help!

---

