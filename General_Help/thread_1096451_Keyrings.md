---
title: "Keyrings"
date: 2009-03-14
forum: General Help
---

### Post by old fert on 2009-03-14
I can't delete evolution and I can't seem to get around it.  I have installed Thunderbird as my primary email client, but ubuntu insists on using evolution when I try to send a link.

It wants my password to "Unlock the Default Keyring."  The problem is that I don't have a password.  I never put one in because security wasn't a problem on this computer.  Not having a password for the keyring has also prevented me from doing a wireless connection.

I've tried to enter a password..no luck.. Evidently, if one is not entered on setup, it isn't a mistake you can correct.

I have spent over a month trying to get everything set up.  Do I have to delete this installation and start over again?  How do I save my files and settings to start over again?

Please make answers VERY specific, as you can see, so far I'm not too swift.

---

### Post by phantom3113 on 2009-03-14
anytime ubuntu asks for a password, (the screen goes dark and a prompt box appears in the middle of the screen) it should be your username password, or the same password you use to login. I know you have one, because it's a required field when installing ubuntu :P. Basically, that only pops up whenever you're doing something that will change your system's workings (installing something), trying to do something that requires "administrator" or "root" access, (synaptic or any administration option), or doing anything preceded by "sudo" in the terminal. So, try the password you use to login when that appears, and it should work. Just make sure you know what you're allowing :)

---

### Post by emarkay on 2009-03-15
You have to enter a password on a new install, but I do not know if it will even accept a null (no entry) but I would think not.

Are you using Synaptic Package Mager or Applications/Add-Remove to remove Evolution? 

Personally I would leave it alone and just change your default mail client.  Use: System/Prefernces/Preferred Applications.

All your DATA is in your HOME directory (some of it is hidden, these files are preceeded with a dot) you can show these in Nautilus (the file manager window) by checking:  Edit/Preferences/Show hidden and backup files.  For example, all your stored Thunderburd email is at: /home/<username>/.thunderbird/xxxxxxxxxx.default/Mail

---

