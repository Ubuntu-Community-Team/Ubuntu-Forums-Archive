---
title: "Error Updating Azureus"
date: 2006-03-26
forum: Desktop Environments
---

### Post by twoseids on 2006-03-26
When trying to update Azureus, I get the following error message:

**Warning: The location '/opt/azureus' isn't writable, this update will probably fail. Check permissions and retry the update.**

How can I fix this so I can update?

---

### Post by s6dalane on 2006-03-26
Type in terminal
> sudo Azureus
Then update it and open again with your own user. Please tell me how it went, because I am not 100% that it will work.

---

### Post by twoseids on 2006-03-26
Command not found. I tried uppercase and lowercase for Azureus. Any ideas?

---

### Post by s6dalane on 2006-03-26
Before executing the command, try
> cd /opt/azureus

---

### Post by twoseids on 2006-03-26
[QUOTE=s6dalane]Before executing the command, try[/QUOTE]
Tried that. Still says command not found. I did "file azureus" and it said:

azureus: Bourne-Again shell script text executable

So it should work, right? Not sure why it's not.

---

### Post by Rory on 2006-03-26
If you have no luck, you may find it easier to refer here for instructions, which should get you back up and running:
[http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)

Good luck.

---

### Post by twoseids on 2006-03-26
[QUOTE=Rory]If you have no luck, you may find it easier to refer here for instructions, which should get you back up and running:
[http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)

Good luck.[/QUOTE]
That did the trick, thanks! It doesn't answer why I couldn't sudo open Azureus, but I can live with that. :^)

---

### Post by Rory on 2006-03-26
[QUOTE=twoseids]That did the trick, thanks! [/QUOTE]

Good to hear the Easy Linux guide did the trick. :)

R.

---

