---
title: "Error icon in gnome-panel from apt won't go away"
date: 2010-09-19
forum: Desktop Environments
---

### Post by Mike Brennan on 2010-09-19
I have an error icon in my Gnome panel that will not go away. It appeared after running an apt-get command (explained below). Everything is working fine, but I cannot get the error icon to go away. Surely there must be some file somewhere storing the state that is making this reappear. Where can I find this to delete it or fix it?

The icon occurred after the following:

I recently upgraded to Ubuntu 10.04. Yesterday, I decided to add the Medibuntu repository to my apt sources based on the instructions at [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository") -- i.e., I ran the command:
> sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

In the terminal window, I saw the following error message amidst the other output:
> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
However, everything appears to have worked fine. The Medibuntu repository has been added to my sources, the keyring has been added, and I am able to install packages from the repository using apt-get without any errors. 

Nonetheless, an error icon appeared in the Gnome panel after running the above command-line, and it will not go away. 

If I move the mouse pointer over it, the following text displays:
> An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was: 'Unknown Error: '<type 'exceptions.SystemError'>' (E:Opening configuration file /etc/apt/apt.conf.d/99synaptic - ifstream::ifstream (13:Permission denied))' This usually mean that your installed packages have unmet dependencies

The file /etc/apt/apt.conf.d/99synaptic it mentions is present and is readable (at least as root).

Running Package Manager works fine with no errors. I've tried running > sudo apt-get check and it runs fine without any errors. Likewise, > sudo apt-get update and > sudo apt-get upgrade run fine with no errors. But the error icon remains.

If I log out of Gnome and log back in, the error icon returns. If I reboot, the error icon returns as soon as I log back into a Gnome session.

How to I get rid of this? This is exceptionally annoying.

---

### Post by Mike Brennan on 2010-09-19
OK, I finally got rid of this. I had to change the file /etc/apt/apt.conf.d/99synaptic to be world readable. It was only readable by root. (I don't know why it was set this way by default if this causes problems. I didn't set it this way.) Likewise, I had to change the file /etc/apt/sources.list.d/medibuntu.list to be world readable. Then, I right-clicked on the error icon, selected "Show updates", and ran a check, and it finally cleared up the error icon.

Sheesh. What a headache this was figuring this out. And google searches didn't help at all.

---

### Post by gauravshah.89 on 2010-10-12
I am new too Ubuntu and was having a similar problem.
This helped me in solving my problem too. Almost lost hope in trying to solve it.

Though I had to make the apt.conf file world readable to solve it.

Thanks!

---

