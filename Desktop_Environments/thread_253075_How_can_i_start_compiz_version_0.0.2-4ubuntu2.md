---
title: "How can i start compiz version 0.0.2-4ubuntu2?"
date: 2006-09-07
forum: Desktop Environments
---

### Post by city-17 on 2006-09-07
Hello,

I'm using Ubuntu Dapper 6.06 64 bits and i have already installed nvidia propietary drivers and 3d acceleration is enabled. I want to try Xgl/compiz and i followed this guide for Xgl install ([help.ubuntu.com/community/CompositeManager/Xgl]("help.ubuntu.com/community/CompositeManager/Xgl")) and these one for compiz install ([help.ubuntu.com/community/CompositeManager/InstallingCompiz]("help.ubuntu.com/community/CompositeManager/InstallingCompiz"))

I have already installed Xgl (in a different session using the startxgl script) and it seems to be working ok since i can log in withoout problems and ps -e | grep Xgl shows something. I also have installed compiz and compiz-gnome with aptitude and compiz --help also shows something. 

The guide suggests to install csm but aptitude can't find any package with that name. Next step in the guide is execute the command compiz-start but shell don't recognize that command. I'm aware that installation guides become obsolete very fast because of the compiz upgrades. Can somebody give me some orientation to start compiz?. What should i do?

---

### Post by Aualin on 2006-09-08
you should try to compile from source, it will add that command

type this in terminal (i must type sudo when using make, to make it compile...)

cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot login
then a password prompt will appear just press enter.
then type this
cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co compiz
and wait until it finish
then
cd compiz
and now
sudo sh autogen.sh
and wait...
Then type
sudo make
and wait...
then type
sudo install
this goes fast, good luck!

---

### Post by city-17 on 2006-09-09
Thanks, i will give it a try but first i want to make sure there is no easier way to start compiz. 
I've tried these commands at console: 

gnome-window-decorator &
compiz &#8211;replace gconf &

but my screen goes black and the cursor is the only thing i can see.

Is it true that compiz-start is the only way to start it since the new upgrades?

---

### Post by city-17 on 2006-09-10
I finally get Xgl/Compiz running and it's awesome!=D> . This confirms that the guides mentioned above are still functional, the only extra steps for Dapper 64 bits users are this ones:

[LIST]
*[*]Add these extra repositories in order to make sure that you are using the latest Xgl/compiz stuff for 64 bits* 
deb [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy
deb-src [http://ubuntu.systemadministrator.org](http://ubuntu.systemadministrator.org) dapper eyecandy 
*[*]Get packeages authenticated*
wget [http://ubuntu.systemadministrator.org/2F306651.gpg](http://ubuntu.systemadministrator.org/2F306651.gpg) -O- | sudo apt-key add -
*[*]Enable downloading*
sudo apt-get update
[/LIST]

After doing this i got an alert from the red update notificator icon and i clicked on it to upgrade my packages, some were new packages like "csm" or "compiz-plugins".

Then i logged in into the Xgl session and typed at console compiz-start. To adjust settings of plugins just type csm.

I hope this become useful for someone. I will post a more detailed explanation of the steps i've taken so far to get Xgl/compiz working.

Note: This worked on a fresh Dapper Drake 64 bits installation and a Nvidia Geforce 6800 (with Nvdia driver version 8762).

---

