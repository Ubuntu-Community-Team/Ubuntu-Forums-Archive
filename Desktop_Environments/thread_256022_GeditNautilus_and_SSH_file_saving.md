---
title: "Gedit/Nautilus and SSH file saving"
date: 2006-09-12
forum: Desktop Environments
---

### Post by alanfranz on 2006-09-12
Hello, i've got a fully-updated ubuntu 6.06 and I'm experiencing a rather strange problems.

I've set up an ubuntu server on a machine on my local network, and I'd like to use it remotely via ssh. I've set up the ssh server ok, no problem... now I'm trying to edit some Asterisk config files, which I've already set user-readable and writeable.

If I:
-log in via ssh and use vi on the remote server as a normal user (no root!) I can read, edit and save them perfecly.
-start kate and fish:// to the server, i can read, edit and save perfectly.

but if I:
-connect to the server using Nautilus and SSH, and open gedit to edit a file, I can read and edit it, but when I click save, although gedit reports no error, the file simply doesn't get saved! It stays immutated!

I suspect this may have to do with the way gedit handles file saving... maybe it does something like 'create a new temporary file, then rename the original file to originalfilename.backup, then rename the temporary file to originalfilename' ?

In such case it would fail (because normal user is not allowed to create files on the server in that folder) but I think an error should be raised whatsoever.

---

### Post by skymt on 2006-09-12
Gedit remote editing is buggy right now. You should use a different editor.

Out of curiosity, what kind of situation is this, where you have write permission to files, but not the folder they're in?

---

### Post by alanfranz on 2006-09-16
I'm just trying to manage my own local mini-server, so I gave user write access to some asterisk config files in /etc/asterisk, but not to the folder itself.

It's not a 'real world' situation, otherwise it would be a bit insecure. BTW I'm now using Kate successfully, thank you.

---

### Post by stormoog on 2007-12-10
I have the same problem with gedit and sshfs on my 7.10. Awell, I'll have to switch to a different editor. It is just that I like gedit so well...

---

