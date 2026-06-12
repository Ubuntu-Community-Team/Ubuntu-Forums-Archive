---
title: "pad-locked folder hplip desktop icon"
date: 2012-01-19
forum: Desktop Environments
---

### Post by jj97403 on 2012-01-19
I had to install hplip printer-driver software from HP for my printer. I downloaded hplip to my desktop and followed the hp tutorial to install the drivers. (Normally I don't have to install drivers manually, but the automatic install wasn't working).

Printer is working fine now, but now I have an hplip-3-11.12 desktop folder icon on my desktop that I can't move or delete. The desktop folder has a small padlock symbol in it. I keep getting a message 'permission denied' when I try to move it to the Home folder or delete.

Anybody know how I can get permission to move or delete it?

I might need to keep it if the HP Device Manager needs it for me to continue to use my printer, so I'd be satisfied just to move it off my desktop so I don't have to see it all the time.

Thanks.

---

### Post by coffeecat on 2012-01-19
Did you download the hplip-3.11.12.tar.gz file from here?

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

Because, if so, it sounds as though you extracted the tarball with sudo rights, which was not necessary, and the hplip-3.11.12 folder is now owned by root.

Before I tell you how to remove that, what did you do after extracting the tar.gz file? Did you cd into the hplip folder and run hplip-install?

Also - right click on the hplip-3-11.12 folder -> Properties -> Permissions. Who is the owner?

---

### Post by jj97403 on 2012-01-19
Thanks. I'll do my best to re-enact what I did, but don't know for sure.

Downloaded HPLIP from here: (i think this is same site you referenced)

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

what was downloaded was (almost like a document, not a folder. it didn't seem to be a tar.gz file, but I wouldn't know). 

--- hplip-311.12.run. ---  

I moved it (hplip-311.12,run) from my download folder to the Unity desktop.

Now this is what I don't remember: 

1)-- whether I went through the "installer walkthrough" here:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

2) or, if I went through the wizard here: 

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

I am almost positive it was the second one(2), because I think I ended up at this site: 

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) 
-- yes, i think this is it.

And YES, I am positive I did whatever I did with SUDO rights, because I remember typing in SUDO, because I was trying to follow the guide and it wasn't working, so I did type in SUDO and password. So you are definitely right that it is owned by root.

Furthermore, per your instructions -- right click folder - properties -- permissions -- owner -- root.

So the owner is root.

And the last thing is i think the wizard i followed was for 11.04, because the wizard i ended up at didn't have 11.10, so i just went with the latest, which was 11.04.

Thanks for your help.

---

### Post by coffeecat on 2012-01-19
Interesting - I see what you downloaded now. On different parts of your first link (which is the link I posted) you can download either the hplip-3.11.12.tar.gz tarball or the hplip-3.11.12.run installer script which contains a self-extracting archive. They both seem to do the same thing in slightly different ways.

Anyway, as far as I can make out, the script *should* have created a temporary archive folder in /tmp, not on your desktop. Why it did so, and why it's owned by root, is unclear. Since the important files have now been installed to various system folders, I'm 99.9% confident that's it's OK to simply delete that desktop folder and its contents.

This is what you do. From a terminal:

```
sudo chown -R yourusername: ~/Desktop/hplip-3.11.12
```

Substitute your account name for "yourusername" and don't forget the trailing colon after yourusername. That command will change ownership of the desktop and contents to yourself, and you can then delete it. If you ever need to re-installl the hplip drivers, you simply run the script again, since that desktop folder seems to be a temporary archive.

---

### Post by jj97403 on 2012-01-19
Yes, that did the trick, thank you. I was able to delete it and still able to print.

When it comes to working in the terminal I really have no idea what I'm doing. Just through brute force, blind trial and error, and sometimes sheer luck something things works out, but this is why I think it ended up with a folder controlled by root on my desktop.

I obviously downloaded the automatic installer ("hplip-3.11.12.run" installer script) to my download folder in Home. 

Then I moved it from my download folder to my Unity desktop. 

Then I was trying to follow the wizard, and the first commands per the wizard are:

user@host: ~$ cd Desktop  (this one worked for me)
user@host: ~/Desktop$ sh hplip-3.11.12.run (but this one did not)

So at this point I think I tried something like:
Sudo hplip-3.11.12.run

And from there on I just kept hitting "enter" or "yes" or "whatever" until I got to the end, I that is why I ended up with a folder controlled by root on my desktop.

Or not :D who knows. cheers, and many thanks, jim.

---

