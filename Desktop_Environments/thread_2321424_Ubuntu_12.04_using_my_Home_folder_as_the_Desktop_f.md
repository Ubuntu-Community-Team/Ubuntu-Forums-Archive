---
title: "Ubuntu 12.04 using my Home folder as the Desktop folder, suddenly"
date: 2016-04-22
forum: Desktop Environments
---

### Post by Elijah_Rockers on 2016-04-22
[COLOR=#111111][FONT=Ubuntu]Installed gdm, using GNOME Classic. Also using LDAP for authentication and home folder designation.

I realized my home folder was set to /home/users/ldapuser which is undesired behavior, because that means my home folder will depend on which machine I'm logged into. This was after I already had a decent amount of information built up in my home folder. 

I edited the appropriate LDAP field to use the NFS share home directory, /nfs/home/ldapuser, which is empty. I copied files from my machine into the NFS share to 'migrate' my info/settings etc.
Originally the Desktop was using ~/Desktop as the Desktop folder which was fine with me. 

But now it seems after I've switched, it is simply using ~ as the Desktop folder. So, **now I have a folder on my Desktop named 'Desktop' which has all the stuff that was on my original Desktop. Also, all the files from my home folder now appear on the Desktop**, the whole situation is very disconcerting.
How can I get the interface to treat ~/Desktop as the actual Desktop directory again, and why did it change?


[/FONT][/COLOR]

---

### Post by Elijah_Rockers on 2016-04-22
#gnome IRC helped me fix it.

[COLOR=#111111][FONT=Ubuntu]$XDG_CONFIG_HOME/user-dirs.dirs was determining that my desktop should be $HOME instead of $HOME/Desktop.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The rest of my folders were also set to $HOME, which is why they were gone, which I didn't even realize until now.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Not sure how it happened, but changing these values back fixed the problem.[/FONT][/COLOR]

---

