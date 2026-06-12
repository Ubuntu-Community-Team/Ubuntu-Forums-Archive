---
title: "Backup All Settings/Files"
date: 2009-02-08
forum: General Help
---

### Post by dazzler on 2009-02-08
Hi all i've recently come back to Ubuntu after previously trying 7.x flavours but gave up because of particular hardware issues at that time.

I have now got 8.10 installed and first off its amazing, completely ditched other OS's now its my main one, even the wife and my 6 year old daughter are happily using it with not one how do i do this question.

Basically my question is....drum roll

I've got Ubuntu running so nice after days of tweaking etc and just how i want it on my laptop i want to transfer all settings programs to my main desktop, is this a no no or is there a simple way of doing this?

*Ps both are running AMD dual cores and will be using 32bit versions

Many thanks

Born Again Ubuntuist ;)

---

### Post by mb_webguy on 2009-02-08
Most user configuration files are user-agnostic -- that is, you can copy the file from one user home directory to another without problems.  The one important thing is to retain file permissions.  The easiest thing to do would be to copy everything in your home directory to an external drive formatted as ext3 (or any other filesystem that supports Linux-style file permissions) using "cp -Rp ~/ /path/to/ext_drive/", then copy them from that drive to your home directory of your laptop using the same command (except with the paths reversed, of course).

It's probably a good idea, though, to first back up your current configuration on your laptop using "cp -Rp ~/ /path/to/ext/backup/".

If you use a different username on your laptop, you'll have to change the ownership of the files with "find . -user old_username -exec sudo chown new_username::new_usergroup {}".  I don't think it should matter whether you do this from the external drive before you copy the files over, or from your home directory after you copy the files over.

---

### Post by dazzler on 2009-02-08
Thanks mb_webguy i knew good old linux would have a way :)

I purposely used the same user/pass on both machines as i thought that would be an issue.

Not to be a pain and just to clarify will this install everything the same as my current laptop setup inc firefox extensions, software installs?

thnx again

---

