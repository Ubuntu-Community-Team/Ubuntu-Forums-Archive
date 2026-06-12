---
title: "Evolution Hidden File / Nautilus / Permissions"
date: 2005-10-27
forum: Desktop Environments
---

### Post by dmBriarwood on 2005-10-27
I have used Evolution as my email client from Red Hat Days to Warty through to Breezy.  When upgrading distros I back up my data on CD-RWs, wipe the hard drive and install the latest OS version.  

Before opening evolution for the first time, I copy the <.evolution> file from my back up CD-RW to my home directory.  The first time I start evolution I set up my email account, and evolution opens containing all my emails, folders, addressbook, tasks, calendar items etc that I've accumulated from the previous distro.

After installing Breezy, I followed my SOP for setting up evolution.  Due to a permission problem, I can see everything, but touch nothing.  Evolution has imported my set-up from evolution on Hoary, but cannot access anything.  The <.evolution> folder is full of the little orange lock icons.

I tried using Nautilaus to change the permissions of the <.evolution> folder, but for some reason it will only allow me change the particular folder I have selected.  Any folders/xml files deeper in the tree remain locked. 

In Hoary, the <.evolution> file was owned by root, and in Breezy it is owned by my Ubuntu user name. 

Is there a way in Nautilus to change the permissions of the entire <.evolution> directory?

Is changing the permissions what I need to do to make my data available in evolution?

Thanks in advance for any ideas!

---

### Post by Diziet Asahi on 2005-10-27
in a terminal, you could type 
> chown -R <user>:<group> ~/.evolution
to change the owner of the .evolution folder and everything inside it
and
> chmod -R  u=rwX ~/.evolution
to grant read/write permission to everything as well

---

### Post by dmBriarwood on 2005-11-07
Thanks!  I appreciate the reply - sorry for the long delay in responding.

Evolution appears to give folders, files and cmeta files different permissions.  A friend of mine had a python script that automatically went through and changed permissions appropriately.  It worked on his install of Breezy, but for some reason not on mine.  The script couldn't find the hidden .evolution file in my home directory.

When I transferred the .evolution file from my cd backup, the ownerships were changed appropriately - after much fiddling around with this script, I gave up and entered the following:

chmod -R 755 .evolution

and everything worked - though my permissions pants are down so to speak.

It would be great (as linux OS users tend to upgrade OS's frequently) if the Ubuntu installer, or the evolution software package could somehow ease the transition of these files to the newest OS version.

---

