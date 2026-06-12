---
title: "Kubuntu Command Line Install Screwed Everything Up"
date: 2011-11-18
forum: Desktop Environments
---

### Post by HerrStig on 2011-11-18
I apologize if this has been discussed or if it's in the wrong category, as clearly I am a Linux noob.

I recently put Ubuntu (standard Gnome) on my Google CR-48 Chromebook. I was very happy with it, but got curious about Kubuntu. I used some kind of command I found while Googling to install it, and now things are screwed up.

Instead of booting to the GUI login page, it boots to command line. I can start Ubuntu with the 'startx' command, but it seems like I lost some features. Kubuntu is nowhere to be found.

My question is, firstly, what did I do? And secondly, how do I fix it?

Sorry about the long-winded post, and thanks for your help.

---

### Post by dabl on 2011-11-18
> **HerrStig said:**
>  I used some kind of command I found while Googling to install it, and now things are screwed up.



It's hard to know what Google told you to do -- it has so many "instructions".  :D

It sounds like you didn't get the full KDE desktop suite, or if you did, it didn't configure KDM correctly.

If you haven't invested a lot of time configuring it, your fastest path to an installed Kubuntu system is to use a Live or Alternate (my favorite) installation CD, or USB stick, and install it that way.

---

### Post by HerrStig on 2011-11-18
The command I used to install was "sudo apt-get install kde-standard"

I guess what I'm looking for is a command to get it to boot directly to GUI (no more command line).

If that doesn't work, I'll go the USB route.

---

### Post by dabl on 2011-11-18
> **HerrStig said:**
> The command I used to install was "sudo apt-get install kde-standard"


Last I heard, the command is "sudo apt-get install kubuntu-desktop".

After you do that, if it doesn't go straight to the GUI desktop, try 

```
sudo service kdm start
```

that should take you to the greeter. Login there, then shutdown and reboot, and it might straighten it out.

---

### Post by HerrStig on 2011-11-18
> **dabl said:**
> 
After you do that, if it doesn't go straight to the GUI desktop, try 

```
sudo service kdm start
```

that should take you to the greeter. Login there, then shutdown and reboot, and it might straighten it out.

That fixed it! Thank you much, sir.

---

