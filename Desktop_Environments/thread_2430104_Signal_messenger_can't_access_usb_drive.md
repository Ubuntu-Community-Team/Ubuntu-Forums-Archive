---
title: "Signal messenger can't access usb drive"
date: 2019-10-28
forum: Desktop Environments
---

### Post by Deanobats on 2019-10-28
Hi all,
I'm running Kubuntu 18.04 with Signal messenger as a desktop app (v 1.27.4 as a snap). The app works fine for chatting but when I try to save or attach files to an external usb drive I get a 'permission denied' error. I don't get this with any other programme, the usb drive is mounted correctly, and everything else can read and write to it, so I'm assuming it may be the permissions of that particular program to access that drive. Can permissions be altered to that level? I've done a fair bit of searching but so far come up with no workable answer.

Ta!

---

### Post by Dennis N on 2019-10-28
Since it's a snap, go to the program's page in the Snap Store and use the 'permissions' button. You might see the option to 'Read/Write files on removable storage devices' - See the attached example. It is probably 'off' by default. Turn it on.

---

### Post by Deanobats on 2019-10-28
Great, got to that bit thanks, but Signal can only access the home folder, guess it doesn't have a channel for accessing remote media. Oh well!

---

### Post by Dennis N on 2019-10-28
Instead of saving directly to removable media, you could always save a file to your home folder, then transfer it with the file manager to the removable media.

---

