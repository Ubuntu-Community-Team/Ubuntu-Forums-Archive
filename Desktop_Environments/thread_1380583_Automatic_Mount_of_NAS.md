---
title: "Automatic Mount of NAS"
date: 2010-01-13
forum: Desktop Environments
---

### Post by rbscairns on 2010-01-13
I am very new to Linux, using Ubuntu 9.10 and enjoying the experience.

My Ubuntu computer is connected to my WLAN. On this WLAN, I also have a network attached storage (NAS) FreeBSD with FreeNAS. My current method to connect to the NAS must be done each time I log in to Ubuntu and consists of-
[LIST]
[*]Places > Network - displaying the network:/// file browser.
[*]Double click the NAS icon - displaying the smb://nas.local/ file browser.
[*]Double click the Data icon - displaying the smb://nas.local/data/ file browser, mounts the drive and places a "data on nas.local" icon on the desktop.
[/LIST]
I then close the file browser and, whenever I want to access the data on my NAS, double click the desktop icon to access the contents of my NAS.

What I would like to do is have this whole process automated so that it occurs at my login and I don't have to go through the process with each login.

Is this possible and how can it be done?

---

### Post by kellemes on 2010-01-14
> **rbscairns said:**
> Is this possible and how can it be done?
Yes, possible indeed..

This is one of my entries in /etc/fstab for connecting to a Synology ds207+ NAS Device
```
//<IP_TO_NAS>/shared_folder /mnt/myfolder cifs user,uid=1000,rw,suid,credentials=/etc/credentials 0 0
```

The shared_folder is the location on the NAS you need to have mounted, not sure how this works with your specific NAS.

You need to create folder /mnt/myfolder (name it as you wish)..
From terminal-window, like so..
```
sudo mkdir /mnt/myfolder
```

Where /etc/credentials is a file holding login-data for the NAS... (again, name it as you wish)
Syntax:
```
username=john
password=mypassword
```

Create it from terminal-window like so..
```
gksudo gedit /etc/credentials
```

You need to have "smbfs" installed afaik.
So..
```
sudo apt-get install smbfs
```

---

### Post by Morbius1 on 2010-01-14
You've got three choices as I see it.

(1) Classic mounting as described above. It's universal in that it will work for all distros regardless of what desktop environment you happen to be running.

(2) Once you gain access using the method you're doing right now, you could just bookmark it:  **Nautilus > Bookmarks > Add Bookmarks**
It will show up under "Places" in nautilus as sort of a "mapped drive" in Windows terminology. You will however have to go into Nautilus and click on the entry under "Places".

(3) This method :                 **Map Windows Shares Permanently with GVFS**
[http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)
It's not really confined to windows shares. It blew me away the first time I saw it. It will automatically place a mount icon on your desktop so you won't have to go into Nautilus.

---

### Post by rbscairns on 2010-01-15
Option 1. got me lost with the first Code: entry. As I said, I am very new to Ubuntu and Linux.

Option 2. was then tried. Problem here is that I cannot find Nautilus anywhere.

Option 3. looked good at first. I started with-

1. Select the "Network" option from the "Places" menu. OK

2. Select the "Windows Network" icon. OK

3. Select the workgroup that your share resides in. Problem

When I double clicked on the network's icon, I get a message "Unable to mount location. Failed to retrieve share list from server". That stumped me.

Basically, in Windows terminology, I would like to map the NAS drive to my desktop and have it reconnect automatically on login.

---

### Post by Morbius1 on 2010-01-15
>  Option 2. was then tried. Problem here is that I cannot find Nautilus anywhere.Nautilus is your "Home" folder. It's the file manager for gnome. It's how you're getting to "Places" now.

> When I double clicked on the network's icon, I get a message "Unable to mount location. Failed to retrieve share list from server". That stumped me.But you don't get that error when you do this:
> My current method to connect to the NAS must be done each time I log in to Ubuntu and consists of-
[LIST]
[*]Places > Network - displaying the network:/// file browser.
[*]Double click the NAS icon - displaying the smb://nas.local/ file browser.
[*]Double click the Data icon - displaying the smb://nas.local/data/ file browser, mounts the drive and places a "data on nas.local" icon on the desktop.
[/LIST]
[COLOR=Blue]EDIT: Try this:[/COLOR]

Open **Terminal**
Type [B]nautilus smb://nas.local/data

[/B]It should open up Nautilus to the data share on nas.local**. **From there you can explore either Option 2 or Option 3

[COLOR=Blue]OR This way:
[/COLOR]
Press **Alt+F2** ( press the Alt and F2 keys at the same time )
Type **nautilus smb://nas.local/data**

---

### Post by rbscairns on 2010-01-18
Morbiusd1, thank you for your guidance, I only hope that one day I can help others in a similar way.
> [QUOTE]When I double clicked on the network's icon, I get a message "Unable to mount location. Failed to retrieve share list from server". That stumped me.
But you don't get that error when you do this:
> My current method to connect to the NAS must be done each time I log in to Ubuntu and consists of-

    * Places > Network - displaying the network:/// file browser.
    * Double click the NAS icon - displaying the smb://nas.local/ file browser.
    * Double click the Data icon - displaying the smb://nas.local/data/ file browser, mounts the drive and places a "data on nas.local" icon on the desktop.[/QUOTE]
No, I do not get the error message when I use the above.

When I try this:

Open **Terminal**
Type **nautilus smb://nas.local/data**

I get the same result as the quoted method above.

I think the problem is now solved. What I did was (in Ubuntu 9.10)-

Places > Connect to server...
Server type: "Windows share"
Server: nas.local
Folder: data
"*check*" Add bookmark
Bookmasrk name: NAS

Then Connect

This brought the "up data on nas.local - File Browser" window and also placed in Places a "NAS" bookmark.

Your guidance is VERY much appreciated.

---

### Post by nuffy on 2010-01-20
I've been searching an searching for days for a solution and this worked for me too! ;)

Now, is there a way for this process to be automated so the NAS device is mounted each time I fire up  my pc?

---

### Post by Morbius1 on 2010-01-20
As a matter of fact there is: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

It was option (3) in my earlier post.

---

### Post by nuffy on 2010-01-22
Thanks Morbius1,

Your tutorial is easy to understand and everything worked for me....except that my NAS doesn't auto mount after logging in or restarting.  

It works if I manually enter this in a terminal..

gvfs-mount smb://192.168.1.1/Public... or

gvfs-mount "smb://192.168.1.1/Public"

I am running UUE 2.5 (9.10) but this shouldn't matter should it?

---

### Post by Morbius1 on 2010-01-22
I don't understand the question. If you can access it by:

**gvfs-mount smb://192.168.1.1/Public**

Then you should follow the rest of the steps ( 13 - 17 ) and it should automount.

For example:

In the Terminal:

Type [B]gedit /home/nuffy/sharemount.sh
[/B]
 Paste this into the GEdit window : 
     ```
#!/bin/sh
gvfs-mount smb://192.168.1.1/Public
```Then make the script executable:
[B]
chmod +x [/B]**/home/nuffy/sharemount.sh**

Then the rest of the HowTo:

> 15. Now let's add the script to GNOME startup. Choose the "Startup Applications" option from the "Preferences" submenu located in the "System" menu. 

16. Select the "Add" option. Type a name of your choice in the "Name" field, browse to the path of the script in the "Command" field, and optionally add a comment to the "Comment" field. Press the "Add" button to save your settings.

17.  Now log out and log back in or restart your PC.  Check the "Places" menu and the shares should be automatically mounted.

BTW, much as I'd like to take credit for that HowTo , it is not mine it was done by [NTolerance]("http://ubuntuforums.org/member.php?u=13011")

---

### Post by nuffy on 2010-01-22
Yeah mate I did everything including step 17 logged out and back in .... that didn't work.  Tried restarting too... no joy!

I didn't for a moment suggest you should take credit for NTolerance work! I was merely thanking you for your response!

---

### Post by Morbius1 on 2010-01-23
Hmm........

Lets do this in steps. I'm going to continue using my example:

(1) Verify that you can run **gvfs-mount smb://192.168.1.1/Public **from a Terminal

(2) Create a launcher on your desktop with the following command:

COMMAND: [B]/home/nuffy/sharemount.sh

[/B]See if that launcher will mount the remote share. If it doesn't then there is something wrong with the script - an extra space, etc. , or you did not make it executable. 

If it does work through the desktop launcher but doesn't work in "Start Up Applications" then I suspect that the "start up application" is executing before the network is up. This one I'll have to think about. There's probably a way to have something execute after verifying that the network is up but the trick is to have the script execute in your name and not root's.

---

### Post by nuffy on 2010-01-24
Thanks for taking more time to help me sort this out Morbius1.  

I did as you suggested and created the little launcher and that worked....then tried creating a Start Up Application and that **didn't** work!!!

I ended up digging around Ultamatix (I am running UUE 2.5) and found a little package 'Nautilus Scripts'.... installed that and viola!!! I now have a mounted NAS drive every time I boot up!! 

Maybe this needs to be added to instruction to make sure 'Nautilus Scripts' is installed before attempting the instructions!?

I am a 'Happy Little Vegemite!! :D

---

