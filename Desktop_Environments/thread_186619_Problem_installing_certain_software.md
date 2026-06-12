---
title: "Problem installing certain software"
date: 2006-06-02
forum: Desktop Environments
---

### Post by mrk112 on 2006-06-02
Just installed the new version but have ran into a problem..

I've enabled all the repositories in Synaptic and clicked Reload except it still won't find things like java, msttcorefonts, flash, etc..

Am I supposed to manually add the correct repository?

---

### Post by Sutekh on 2006-06-02
I find 'enabling' repositories in Synaptic, to be too fiddly for my liking.  I prefer to do this from the command line?  It's very easy to do too.
 
 Start by opening a Terminal Window (Applications -> Accessories Menu) and then backing up your current sources using this command
 ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` Then edit it with your preferred editor, I am using **nano** in this example.  You may prefer **gedit**. If so just swap nano for gedit in the next command.
 ```
sudo nano /etc/apt/sources.list
``` When the editor opens you need to find these lines
 ```

 # deb http://archive.ubuntu.com/ubuntu breezy universe
 # deb-src http://archive.ubuntu.com/ubuntu breezy universe
 
 ...
 
 # deb http://security.ubuntu.com/ubuntu breezy-security universe
 # deb-src http://security.ubuntu.com/ubuntu breezy-security universe
``` You need to uncomment them - remove the # signs. This enables the universe repository. To enable the multiverse repository, add multiverse to the end of these lines.
 
 It would look something like this when you finish making the changes
 ```

 deb http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
 deb-src http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
  
 ...
 
 deb http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
``` If you save the file (Ctrl +O if you are using nano) and exit (Ctrl + X in nano) you can then update the repositories with
 ```
sudo apt-get update
``` Then you are set, and can use Synaptic.

---

