---
title: "Innotek Virtual Box - Sharing Folders"
date: 2007-08-07
forum: Desktop Environments
---

### Post by johnnybgood115 on 2007-08-07
Not sure I'm in the right category but maybe someone can help me. . . . 

I'm running Win XP in an Innotek Virtual Box.  I basically want to get some executable files into that Windows environment.  Where are the files stored on my hard drive and can I just drag and drop files to the windows environment.  

Thanks in advance.

---

### Post by HeavyAl on 2007-08-07
First you'll want to install the guest additions on your virtual machine. If you are running your machine in a window, click on Devices/Install Guest Additions to do that.

After you've got Guest Additions installed you'll notice there is a bunch of icons near the bottom right of the host window for your virtual machine. One of them looks like a folder. If you right click this folder and hit open it will show you a list of folders that are accessible to your virtual machine - since this is your first time there probably wont be anything there - just click the add folder icon the right of the list and navigate to a folder you want to share.

After you've added a folder that you want to be accessible in your virtual machine, you need to map a drive to that folder within your Windows vm. You can do this easily at a command prompt by entering the following and substituting the necessary values:

```

net use x: \\vboxsvr\share

```

where x: is the drive you want to map the folder to in your vm and \share is the folder you want to get to.

Have fun!

---

