---
title: "Copy to external Hard Drive with Command Line"
date: 2009-03-06
forum: Desktop Environments
---

### Post by ldclan on 2009-03-06
I have a simply question and I was hoping that someone here can help me.

I have a command line string written so files are copied from one hard drive to an external one. The command line string is applied to a alias/shortcut on my desktop so I can just click on it to start.

The problem I have is: it asks for my password before it starts.
I don't want it to ask, just start and go

I am unsure where to add my password, so I am posting my command line spring hoping someone can tell where it should go in it.

"sudo cp -dpRuvx /media/NAS_Disk-1/GRAPHICS-NAS /media/NAS_BU"

There it is, and any help is greatly appreciated. Thank you.

---

### Post by Lord Landis on 2009-03-08
You want to do something like this in your script:

```
echo *password* | sudo cp -dpRuvx /media/NAS_Disk-1/GRAPHICS-NAS /media/NAS_BU
```

That should work for you, just remember that putting your password into a script isn't very secure.

On the other hand, you shouldn't need to do this.  If the drives are properly mounted, you'll be the owner and you shouldn't need sudo to copy files from one to the other.

Check and make sure that your drives are mounted with the correct permissions (that is, with you as the owner) by running 'ls -lah' on /media.  If you're not the owner of both drives, unmount them, unplug them, and then plug them back in and let them get automounted.

Also, try running the copy command without 'sudo' and see if it works or not.

---

### Post by ldclan on 2009-03-09
You are 100% correct. I checked the owner in permissions and changed it, I removed the "sudo" and walla it works and all is well.
Thank you very much for your help.

---

