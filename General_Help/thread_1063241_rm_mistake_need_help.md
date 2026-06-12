---
title: "rm mistake need help"
date: 2009-02-07
forum: General Help
---

### Post by nbo10 on 2009-02-07
Okay, so I did something really stupid. I'm running 7.10, I had files in the trash that I couldn't empty. so I went to a command 

```
>> cd .Trash
>> sudo rm -r ./*
```

I immediately ctrl-c to kill the process, but I was already to late. stuff got deleted. bash shell commands wouldn't work, networking stopped working, shutdown didn't work and I got an error 15 from grub when I tried to restart.

Now, how do I restore my system? 

And the irony is that I was emptying the trash so that I could create an image of the drive for backup.

So could I upgrade to 8.10 with a liveCD with destroying all the documents I have on the HD? Or do I need to get an internal HD enclosure backup all my data and then reinstall? Thanks for the help.

---

### Post by heindsight on 2009-02-07
> **nbo10 said:**
> 
```
>> cd .Trash
>> sudo rm -r ./*
```



Are you sure that's the command you used? usually * only expands to names not starting with . So it should only have deleted files and directories under .Trash and not elsewhere. Something like
```
sudo rm -r .*
``` would be more destructive though -- depending on where in the filesystem you run it (eg in /.Trash/ it would be very bad, in /home/username/.Trash/ it would only delete everything under /home/username)

Anyway, whatever the exact rm command you used, it seems you have done some serious damage.

To fix it, I'd recommend booting from a live CD, mount your HD, back up any files you want to keep that haven't been deleted and then do a fresh install.

---

