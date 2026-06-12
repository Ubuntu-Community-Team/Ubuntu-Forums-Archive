---
title: "help recovering"
date: 2009-04-15
forum: General Help
---

### Post by alonse on 2009-04-15
hello i´m a windows user and my computer doesn´t start. it give me 4 options to start in safe mode, normal mode and others but anyway in the 4 options the computer restarts and go to the last screen. 

Now I am trying to recover my files with ubuntu live cd. My computer has 2 partitions C: and D:, I can recover every D file but in C i have this problem:

[http://www.hiboox.es/go/imagenes/auto-moto/screenshot,5b60bca2828c85a350ecf40cc64ab8ce.png](http://www.hiboox.es/go/imagenes/auto-moto/screenshot,5b60bca2828c85a350ecf40cc64ab8ce.png)

Can anyone help me?
Thank you for your help!!

---

### Post by silentrebel on 2009-04-15
What's the problem?  You forgot to state it...  
I'm guessing you did not cleanly shut down windows the last time.  Perhaps you should try force-mounting the c-drive.
Nothing is certain until you state the problem.

---

### Post by DGortze380 on 2009-04-15
The Easy Way:
Boot into Windows, shutdown correctly, try again.

The Linux Way:
Since windows won't boot, you'll have to force mount it.

Go to Applications -> Accessories -> Terminal

Enter the following one at a time, press Enter after each.

```

sudo mkdir /media/windows

sudo mount -t ntfs3g /dev/sda1 /media/windows -o force

```

If it asks for your password, type it and press enter. Nothing will show on the screen while you type.

---

### Post by DGortze380 on 2009-04-15
> **silentrebel said:**
> What's the problem?  You forgot to state it...  
I'm guessing you did not cleanly shut down windows the last time.  Perhaps you should try force-mounting the c-drive.
Nothing is certain until you state the problem.

He posted a screen shot of the error message ...

it's an unclean shutdown.

---

### Post by silentrebel on 2009-04-15
There we go!

As I suggested, you may have to force-mount the drive (though it isn't the safest approach for you data and my make your Windows partition unbootable, but it seems you already have that problem :P).  Just use the command they give you (and that *DGortze380* already posted above) in a terminal (opened from the Applications menu):
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
```

> **DGortze380 said:**
> He posted a screen shot of the error message ...
it's an unclean shutdown.
Sorry about that, it wasn't there when I checked the first time.  It only appeared after my first post.  That's odd though; he didn't edit his post...

---

### Post by alonse on 2009-04-15
i have the problem since  i had a electrical problem at home and the computer shutdown, and then i had the same screen with the 4 options again and again..

so i would like to recover my files and i´m trying with ubuntu live cd but the problem is that i can´t mount the c: device, in the file I upload appears the error

thanks

---

### Post by silentrebel on 2009-04-15
Follow the instruction in Post#3 by *DGortze380*, they are quite clear and should greatly help you.  
Let us know if there is still an issue.

---

### Post by alonse on 2009-04-15
thank you for your help! i can´t enter in windows so i hope the other option could solve this. Sorry i´m a very new user in ubuntu. I´m going to try it. i´ll tell you

---

### Post by alonse on 2009-04-21
hello i have trying to write the lines you tell me. after enter the last line it tells me that there is not any device called ntfs3g

---

### Post by silentrebel on 2009-04-21
I think DGortze380 uses different commands on his mac... Try this as suggested in post#5 :
```
sudo mkdir /media/windows
sudo mount -t **ntfs-3g** /dev/sda1 /media/windows -o force
```
...as opposed to...
```
sudo mkdir /media/windows
sudo mount -t **ntfs3g** /dev/sda1 /media/windows -o force
```
Let us know if that works...

---

### Post by alonse on 2009-04-21
now it appears...

failed to access 'dev/sna1' no such file or directory

---

### Post by bumanie on 2009-04-21
Hello alonse. Although I primarily use ubuntu and think it is great, with what appears to be a lack of experience with command lines, you may find it easier to save your stuff off C:\ via puppy linux. Puppy is a small distro of around 90mb and it is great at mounting drives and does not seem to worry about unclean shutdowns as much as ubuntu (and most other linux) does. It too runs off a live cd. I once had an issue with windows on my dual boot, was unable to mount the windows drive with ubuntu, but puppy linux mounted it without any problems. Once the live cd has installed into ram, puppy has an icon on the screen that looks like a usb stick - click on that and it will find the drives/partitions on your computer and will display a window where you can choose which drive/partition to mount.
If you want to use ubuntu, rather than trying to force mount C:\ I suggest you install ntfsprogs and then try fixntfs - it usually fixes unclean shutdowns and resets the ntfs filesystem. Post back if you don't want to try puppy and someone will help you with the commands to use from ubuntu live cd.

---

### Post by silentrebel on 2009-04-21
If you don't want to use PuppyLinux, make sure you entered the command we posted properly.

From you post, it seams to me that you must have typed *dev/sda1* as *dev/sna1*.  Otherwise, I do not know why it would complain about the latter; you shouldn't have referred to it...

---

### Post by alonse on 2009-04-21
Now!! There it is!!i didnt write correctly. my data appears. thank you a lot mates!! i think that now it is working

after i enter the last line appears this

$Logfile indicates unclean shutdown (0,0)
WARNING: forced mount, reset $logfile.

thanks too for puppy linux i´m downloading it

---

### Post by silentrebel on 2009-04-21
I'm glad it works.  
Why don't you set this thread to *solved* so that others can know that this is a source for help and no longer requires attention.

---

