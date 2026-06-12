---
title: "su -c command gives error"
date: 2009-01-22
forum: General Help
---

### Post by nowhere@cox.net on 2009-01-22
Hey all, I'm trying to write an init script for hellanzb and I am using the command 
```
su -c '/usr/bin/hellanzb --daemon' $HELLAUSER
```
in the start case. It works but gives and error, and the same error occurs if I execute the command on the command line.
```
Sessions still open, not unmounting
```

How do I get rid of this error?

Thanks!

---

### Post by mssever on 2009-01-23
> **nowhere@cox.net said:**
> Hey all, I'm trying to write an init script for hellanzb and I am using the command 
```
su -c '/usr/bin/hellanzb --daemon' $HELLAUSER
```in the start case. It works but gives and error, and the same error occurs if I execute the command on the command line.
```
Sessions still open, not unmounting
```How do I get rid of this error?

Thanks!
Try using sudo: ```
sudo -u $HELLAUSER /usr/bin/hellanzb --daemon
```
Also, that error is almost certainly unrelated to su, because there's no need for su to unmount anything. I'm guessing that hellanzb (whatever that is) is causing that error.

---

### Post by nowhere@cox.net on 2009-01-24
Hey thanks for the reply! The sudo command gave me permission denied errors. 

```
Starting hellanzb/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Exiting: FatalError'>: Unable to create directory for option: Hellanzb.LOG_FILE dirName: /home/username/Private/.hellanzb error: [Errno 13] Permission denied: '/home/username/Private/.hellanzb'

```

I'm not sure if root is not a sudoer. I assume the init scripts are run as root so root would need to me a sudoer in order to invoke the command? Or maybe it's the encrypted folder? I put most of my stuff in it for security.

I agree about su and mounting but when I run the hellanzb command without su directly as the user I don't get the error. I was thinking it was one of those errors that don't really say what they mean. 

AH! Wait! I bet when su logs in as the user, it mounts the encrypted folder! When it finishes the command somehow it's not unmounting it properly. I don't know the process so what do you think? I love it when the light bulb comes on!

Thanks!

---

### Post by nowhere@cox.net on 2009-01-26
I am now almost 100% convinced this is what is happening. After running the command with su it "logs out" but notices the encrypted folder is still in use so it doesn't unmount it.

---

### Post by timtoo on 2009-04-14
Reading this, I now feel completely retarded. I had been wondering why my fetchmail wasn't running anymore on boot up since upgrading to jaunty and encrypting my home directory. It is started in rc.local with an su -c command. Duh!! 

And then I'd see the mysterious message above when starting it by hand. Then reading your message *finally* clued me in.

Of course it's so painfully obvious now. My home directory's encrypted at boot time: can't read ~/.fetchmailrc!

---

