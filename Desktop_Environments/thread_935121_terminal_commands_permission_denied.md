---
title: "terminal commands permission denied"
date: 2008-10-01
forum: Desktop Environments
---

### Post by Mike1504 on 2008-10-01
Last nite I was having error messages in terminal (Hardy)
Chown: Permission denied
sudo command not found
chmod permission denied

Not sure what I did.  I had vsftp running and someone was uploading files.  I allowed an update during that time.

I was using chown and chmod to modify files in the homes folder to group=ftpuser and permissions of 644  I had several users set up.  each had a folder to upload files to and each had folders which showed what others had shared.  This was done in fstab by mount - bind  of the upload folders into each users shared folders.  

I last modified fstab on sept 25. I immediately did a remount -a
 no problems until last night (sept 30)

This morning I tried to restart to see if it would clear the problem.  Ouch!:(

the ubuntu loading screen with the scrolling bar starts but then I get the following
code readout:

/etc/rc2.d/s10sysklogd: 150: chown: permissions denied
/ect/rc2.d/s10xserver-xorg-input-wacom: line 12: /bin/cat: permission denied

starting kernel log daemon...
/etc/rc2.d/sllklogd: 63: mkdir: permission denied
/etc/rc2.d/sllklogd: 63: chown: permission denied
mkfifo: cannot create fifo '/var/run/klogd/kmsgpipe.pid' for writing: read-only file system (read-only file system)

end code

at this point the log screen passed my ability to keep up, but when all was finished the only thing left on the screen was an orange asterik

I am a novice user:confused: please help! thanks!:)

---

