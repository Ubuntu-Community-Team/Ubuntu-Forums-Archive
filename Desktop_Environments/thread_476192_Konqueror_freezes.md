---
title: "Konqueror freezes"
date: 2007-06-16
forum: Desktop Environments
---

### Post by spadgos on 2007-06-16
I have a problem with Konqueror, when using it to browse local files. It will freeze every single time I open it up, taking CPU usage to 100%, and i have to "killall konqueror" to close it. It works fine for the web, just when browsing local files. Could anyone help?

---

### Post by kuja on 2007-06-21
I have a couple of ideas, first one is to upgrade to the latest kde you can (kde 3.5.7 in feisty). Apart from this, it's probably having issues parsing a file, or generating thumbnails, or some such, it's hard to say what.

---

### Post by spadgos on 2007-06-21
it happens every time I open konqueror to browse any local folder - not just particular ones (ie: ones with pictures, etc). If it is a problem with generating thumbnails, is it possible to turn off that feature?

Regarding having the latest version, I'm not at my Kubuntu box now so I'm not sure, but I think it already has the latest version. Would reinstalling the same version help? Is there an easy way to uninstall/reinstall konqueror? ...or is it integral to KDE and therefore I'd have to reinstall it all?

---

### Post by kuja on 2007-06-21
Umm, sudo apt-get install --reinstall kdebase should do the trick.
If it really is a thumbnail problem try running "rm -Rf ~/.thumbnails"
also try  settings -> configure konqueror -> previews & meta-data -> and uncheck both internet and local
Oh, and Kubuntu Feisty doens't ship with the latest KDE, it's a version behind (seeing as KDE 3.5.7 was released after feisty)

---

### Post by spadgos on 2007-06-21
Hi Kuja,

thanks so much for your help, but unfortunately I tried all three of those things you suggested and still had the same problem. When I start konqueror, if i don't kill it within about 5 seconds, then the entire system completely locks up (the mouse doesn't even move).

is there anything which it could be? I'm not a fan of Gnome and would really like to stick with KDE.

---

### Post by spadgos on 2007-06-21
I just noticed this when I ran Konqueror from the terminal

```
nick@ubundesk:~$ konqueror
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

could this have something to do with it?

edit:
then, when I browsed to a local folder, this error appeared:
```
konqueror: WARNING: Pixmap not found for mimetype inode/directory
```

---

### Post by spadgos on 2007-06-24
I found out that the BadDevice errors were to do with a mysterious Wacom tablet being enabled in my xorg.conf file, though I don't have one at all... strange, but anyway... I got rid of that error but still no luck with Konqueror.

From some googling, I found that some people had the same problem with the Pixmap errors and the suggestion there was that the KDE mime types weren't installed properly, yet they didn't say how to install them. Maybe that is the problem? Does anyone know how to install KDE mime types?

Also, I ran the task manager and watched the processor/memory usage when I tried to run Konqueror. It very quickly used up the 1gb of memory then maxed out the 2gb swap drive.

---

### Post by rdoolen on 2007-08-23
I seem to have the same issue. Did you ever figure it out?

---

### Post by spadgos on 2007-08-23
yep - i re-installed windows. it sucks but at least I can view the files on my hard drive.

---

### Post by rdoolen on 2007-08-24
Windows?!?!?!  

Did you try gnome? Thats what I use most. I have never had a problem with Nautalis.

I also tried Dolphin. That sems to work. I would replace Konqueror if I knew how.

---

### Post by dannybuntu on 2008-02-08
This is an old thread but I would like to wish to post my concern here since I have almost the same situation.

> yep - i re-installed windows. it sucks but at least I can view the files on my hard drive.

I find that solution sad but practical. Well next time don't give up so easily. A solution is just around the corner.

Here's the code for my concern.

```
konqueror: WARNING: Pixmap not found for mimetype inode/directory
konqueror: WARNING: Pixmap not found for mimetype image/jpeg
konqueror: WARNING: Pixmap not found for mimetype text/plain
konqueror: WARNING: Pixmap not found for mimetype image/jpeg
konqueror: WARNING: Pixmap not found for mimetype inode/directory
konqueror: WARNING: Pixmap not found for mimetype application/x-iso
konqueror: WARNING: Pixmap not found for mimetype text/plain
konqueror: WARNING: Pixmap not found for mimetype inode/directory
konqueror: WARNING: Pixmap not found for mimetype image/jpeg
konqueror: WARNING: Pixmap not found for mimetype image/jpeg
konqueror: WARNING: Pixmap not found for mimetype inode/directory
konqueror: WARNING: Pixmap not found for mimetype image/png
konqueror: WARNING: Pixmap not found for mimetype image/jpeg
konqueror: WARNING: Pixmap not found for mimetype application/x-zerosize
konqueror: WARNING: Pixmap not found for mimetype image/x-bmp
konqueror: WARNING: Pixmap not found for mimetype text/xml
konqueror: WARNING: Pixmap not found for mimetype application/x-shellscript
konqueror: WARNING: Pixmap not found for mimetype inode/directory
konqueror: WARNING: Pixmap not found for mimetype inode/directory
konqueror: WARNING: Pixmap not found for mimetype application/x-shellscript
konqueror: WARNING: Pixmap not found for mimetype inode/directory

```

Symptoms: The file icons don't appear when browsing locally. Just a blank white screen.

Tried: apt-get reinstall kdebase from above same results.

---

### Post by dannybuntu on 2008-02-10
someone please help

---

### Post by kuja on 2008-02-10
> **spadgos said:**
> I found out that the BadDevice errors were to do with a mysterious Wacom tablet being enabled in my xorg.conf file, though I don't have one at all... strange, but anyway... I got rid of that error but still no luck with Konqueror.

From some googling, I found that some people had the same problem with the Pixmap errors and the suggestion there was that the KDE mime types weren't installed properly, yet they didn't say how to install them. Maybe that is the problem? Does anyone know how to install KDE mime types?

Also, I ran the task manager and watched the processor/memory usage when I tried to run Konqueror. It very quickly used up the 1gb of memory then maxed out the 2gb swap drive.

Old as the thread and that particular post may be, I do have a couple ideas worth trying if the issue still exists:

Plan A: Try creating a new user account and see if the new user has the same problem - if the new user doesn't have any issues with it then it's some sort of configuration issue or other, and the easiest way to fix it would be to nuke your configs.

Plan B:
```
sudo apt-get remove --purge kdebase kde-core kdelibs kdelibs-data
```

The list of packages to remove will likely be very, very large. Copy + paste all of them and save them in a file in your home directory called "packages"

Here's a script to remove the asterisks and line breaks .... it'll also start the reinstall too.

```
sed -i $HOME/packages -e "s/\*//g"; cat packages > tr '\n' ' ' > toinstall; sudo apt-get install `cat toinstall`;
```

Best of luck.

---

### Post by dannybuntu on 2008-02-11
I added new user and true enough it worked. Thank you Kuja. One last question, mmm, how exactly do I nuke my configs?

---

### Post by kuja on 2008-02-11
2 ways I can think of to do it. First way would be to open up a file browser and rm any folders whose name starts with a dot. The other way is to add a new user (lets call him dummy for now), copy your non-config (likely non-hidden) files over to the dummy users folder. Delete the original user and its home directory, then add back the original user and copy your files back, then delete the dummy user ..... long way around it sounds like, but you probably won't miss anything that way, 'tis how I usually do it.

---

### Post by dannybuntu on 2008-02-11
Worked like a treat thanks dude.

---

