---
title: "No GNOME Apps Load... Could Not Send Message to gconf Daemon"
date: 2009-02-27
forum: General Help
---

### Post by tammer on 2009-02-27
So I booted up today to a nasty surprise. I guess the system wasn't shut down correctly, since I left the system on sleep without plugging it in, and the battery died. All I get after the bootloader is a black screen, a cursor, an error from update-notifier and an error from gnome-power-manager. Both contain this:

> Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks to due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))

The strange thing is, if I log in as a different user, everything works fine. If I log in as my usual user but choose a Fluxbox session, every GNOME app I try to open gives me the same error. Is there any easy way to fix this, or should I just scrap my user and make a fresh one? Let me know if there's any more logs I should produce. Thanks for any help you can provide.

---

### Post by Yellow Pasque on 2009-02-27
No need to scrap the user. You probably just have stale lock files in that user's /home/<username>/.gconfd directory.
See the "gconfd and locking" here: [http://www.win.tue.nl/bcf/linux/usage/emptymenu.php](http://www.win.tue.nl/bcf/linux/usage/emptymenu.php)

---

### Post by tammer on 2009-02-27
Thanks for that link, but I think the problem might go deeper than that. My system doesn't recognize the "dur" command on that page, and I don't think the problem is the disk quota. I went on to the gconf commands.

$gconftool-2 --shutdown appears to work, but $gconftool-2 --spawn prints this:

> Failed to spawn the configuration server (gconfd): Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details - 1: Not running within active session)

The weird thing is those "lock" files don't appear to be in the proper place. The contents of my .gconfd folder is a file named "saved_state," and two empty files named "." and ".."

---

### Post by tammer on 2009-02-28
Well, to anyone who stumbles on this thread, I found something that worked. I just deleted these folders from my home directory: .gnome, .gnome2, .gconf, .gconfd, and .metacity. The only thing I lost was my customizations, which is easy are re-do.

---

### Post by exile on 2009-03-04
Seems like the latest update to 8.10 I ran 3rd of March caused all sorts of brokenness for gnome. KDE worked fine but this was the error it was giving. deleting those directories enabled me to get back into gnome, but I am still getting weird breakages. I can't even get to GDM when using the kernel from the update, older versions work though.

:(

---

### Post by realgt on 2009-06-16
> **tammer said:**
> Well, to anyone who stumbles on this thread, I found something that worked. I just deleted these folders from my home directory: .gnome, .gnome2, .gconf, .gconfd, and .metacity. The only thing I lost was my customizations, which is easy are re-do.
tammer,

thanks, renaming ~/.gconfd .gnome and .gnome2 worked for me

---

### Post by dgovin on 2009-07-28
same for me too///am a newbie, and i had the same error..
and it went quite smoothly by renaming .gnome, .gnome2,.gconf folders..restart and you have completely new set of folders in your /home/<user>/ and everything went fine
thanks to all :)

---

### Post by BinaryMn on 2009-09-27
I'm not so much a newbie and I had the same error. I stumbled across this thread, and just renamed the "saved_state" (mv .gconfd/saved_state .gconfd/.saved_state) file in the .gconfd folder to something else and restarted GDM (sudo /etc/init.d/gdm restart). Everything came back up the way I had it.

Use one of the consoles (Ctrl+Alt+F1 - F6) to run the commands, since you can't get into GNOME.

---

### Post by palle kuling on 2009-10-21
Hello !
I just wanted to thank you for this nifty little fix(mv .gconfd/saved_state .gconfd/.saved_state), now the desktop is up and runnin' again !

;) Palle Kuling

---

### Post by mathias.bonert on 2010-06-09
Thanks for this fix.

Mathias

---

