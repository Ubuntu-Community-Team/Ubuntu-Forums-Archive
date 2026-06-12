---
title: "synaptic &quot;dangling&quot;?"
date: 2005-06-30
forum: Desktop Environments
---

### Post by geofff on 2005-06-30
I've been getting into a mess with networking. Not knowing whether or not I needed it I loaded samba. I am now trying to start afresh and have via synaptic marked samba for removal and applied it but the little clock just keeps on going round! Nevertheless the message in the "Changes applied" window says "successfully applied all changes. You can close the window now". 

Clicking on terminal in that window I get the following 

Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba

I'm not sure whether the process has finished or not. Can anyone please help?

TIA Geoff

PS I note that there is also a K09samba file in /etc/rc3.d. I am inclined to remove them both, but would welcome reassurance!

---

### Post by davahmet on 2005-06-30
The K09samba is the smaba service kill script for the runlevels.  For example, /etc/rc2.d/K09samba is the runlevel 2 kill script for samba.  Since these are normally called by the rc.d script via symlinks to appropiate scripts in current runlevel directories during startup and shutdown, it is most likely saying that removal of samba left broken links.  If you are removing samba, then make sure the corresponding /etc/rc<runlevel>.d/K##samba and /etc/rc<runlevel>.d/S##samba scripts and links are removed and also any reference to them in /ect/rc.d.  This should have done with a clean removal so I'm not sure why synaptic failed to do this properly.

WARNING--Be very careful editing rc.d and init files since a mistake here can seriously impair your ability to startup a Linux system.  As a matter fo fact, for safety I would try again to have synaptic remove it by selecting samba for 'complete removal' or by running
>  sudo dpkg  --purge samba 

---

### Post by geofff on 2005-06-30
Thanks for the above. Both links now safely removed.  :smile: 

G

---

