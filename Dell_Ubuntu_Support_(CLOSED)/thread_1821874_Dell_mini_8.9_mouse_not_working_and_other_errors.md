---
title: "Dell mini 8.9 mouse not working and other errors"
date: 2011-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Akhety on 2011-08-09
Please forgive my inexperience with linux. Usually I am able to solve my linux problems by searching the forums, but I am at a loss. I think there are multiple issues going on.

First, when I booted up my dell mini (this is the first dell mini to be released), the background image was gone and my mouse wouldn't move once Ubuntu had fully booted (I can move it before my desktop loads). After figuring out how to launch terminal using my keyboard, I noticed this:

"starting up...
usplash: setting mode 1024x768 failed
usplash: setting mode 800x600

Ubuntu8.04.2 kara ttyl"

I logged in and was able to enter commands. However, I'm not sure exactly what the issue is. I think the problem is with Ubuntu, since I can use the mouse before it fully boots up. However, I'm not sure exactly where the problem with my screen resolution comes in. Should I update/replace my video card driver? How do I do that in linux?

I also tried to make sure Ubuntu was fully updated. However, when I try to do that, I get the following error:

"W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/hardy/Release](http://linux.dropbox.com/ubuntu/dists/hardy/Release) Unable to find expected entry main/binary-lpia/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead."

I can't do a clean install because I lack an optical drive (or even a usb drive, but I could go buy one if that's the only solution. I also haven't backed up my files recently, so whatever I do, I need to be able to keep those.

If anyone has a solution, you will have my complete regard and admiration.

(keep in mind the only way I can acces my computer is through terminal or the setup screen)

---

### Post by Akhety on 2011-08-12
Does no one have any idea what is wrong with my computer? I would love any suggestions at all. Please help?

---

### Post by snowpine on 2011-08-12
You need to back up your important files and reinstall. Ubuntu 8.04 is no longer supported, and the Dell Mini series came preinstalled with a special "Dellbuntu" version based on the abandoned LPIA architecture which has no upgrade path. 

You can purchase a couple of USB "thumb drives" very inexpensively, one for backing up your data and another for installing a currently-supported Ubuntu. 

Good luck! :)

---

### Post by Akhety on 2011-08-12
> **snowpine said:**
> You need to back up your important files and reinstall. Ubuntu 8.04 is no longer supported, and the Dell Mini series came preinstalled with a special "Dellbuntu" version based on the abandoned LPIA architecture which has no upgrade path. 

You can purchase a couple of USB "thumb drives" very inexpensively, one for backing up your data and another for installing a currently-supported Ubuntu. 

Good luck! :)
Thank you!

Next question... How do I backup my files only using terminal?

Second: How do I reinstall to the latest Ubuntu using terminal? The directions on the Ubuntu website aren't clear on that.

---

### Post by snowpine on 2011-08-12
Here are the instructions for creating a bootable USB of the current Ubuntu release (steps 1-2-3; skip step 4 for now):

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Once you have booted your Ubuntu USB, you can use the GUI file manager (Nautilus) to back up your files to your spare thumb drive. You don't need to use the terminal. :)

---

### Post by Akhety on 2011-08-12
> **snowpine said:**
> Here are the instructions for creating a bootable USB of the current Ubuntu release (steps 1-2-3; skip step 4 for now):

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Once you have booted your Ubuntu USB, you can use the GUI file manager (Nautilus) to back up your files to your spare thumb drive. You don't need to use the terminal. :)
Thank you so much! I followed the directions on the link and everything works now, including the mouse. 

Thank you so much!!!

---

