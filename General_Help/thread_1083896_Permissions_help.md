---
title: "Permissions help"
date: 2009-03-01
forum: General Help
---

### Post by phr33k-dc on 2009-03-01
I got a message saying 'You don't have the right permissions to extract archives in the folder "file:///usr/share/nautilus-scripts"'

I also tryed to delete a folder in an internel 'media' drive and go tthe message 'you do not have permission' etc....

How can i give myself full permissions on everything and try to keep passwords?

Any help would be great
Thanks

---

### Post by taurus on 2009-03-01
Run nautilus with root privilege.

```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by phr33k-dc on 2009-03-01
Thanks but how do i enable permissions in general?

and i tryed that command and got: 


seahorse nautilus module initialized
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:10644): WARNING **: Unable to add monitor: Operation not supported

What the hell is this?

---

### Post by phr33k-dc on 2009-03-01
just completely enable permissions

---

### Post by taurus on 2009-03-01
Permissions are there for a reason.  Changing permissions (or ownership) to files/directories outside your $HOME because you want to make life easy for you will result in completely trashing your machine beyond repair.  

Now, what do you want to unpack to /usr/share/nautilus-scripts?

---

### Post by phr33k-dc on 2009-03-01
wow ok then defo wont do that.
im trying to when i right click to have an option that says shred. so i dont have a clue what i am doing with scripting or anything

---

### Post by taurus on 2009-03-01
Did you download something to your desktop?  What is it and what makes you think you need to unpack it in /usr/share/nautilus-scripts?  Open a terminal and post the output of this command.

```
ls -la ~/Desktop
```

---

### Post by phr33k-dc on 2009-03-01
What i think i am doing is adding a script to nautilus so when i right click 'shred' is one of the options

i typed that command and got:

total 8
drwxr-xr-x  2 root root 4096 2009-03-01 18:54 .
drwxr-xr-x 17 root root 4096 2009-03-01 19:21 ..

---

### Post by taurus on 2009-03-01
Have you downloaded that script that you want to move to /usr/share/nautilus-scripts?

Wait a second, are you currently logged in as root?

---

### Post by phr33k-dc on 2009-03-01
how do i know if im root or not? im the only user in this laptop.

yes i have that script i think

---

### Post by phr33k-dc on 2009-03-01
the script is in that attachment

---

### Post by taurus on 2009-03-01
What username did you log in with?

```
cd ~
ls -la
```
Post the output of the second command.

---

### Post by phr33k-dc on 2009-03-01
I just logged in with 'david-dc' what would that tell you?



root@david-dc-laptop:/home/david-dc# ls -la
ls: cannot access .gvfs: Permission denied
total 256
drwxr-xr-x 42 david-dc david-dc  4096 2009-03-01 19:20 .
drwxr-xr-x  3 root     root      4096 2009-02-26 08:32 ..
drwx------  3 david-dc david-dc  4096 2009-02-26 20:12 .adobe
-rw-------  1 david-dc david-dc  1165 2009-02-28 22:43 .bash_history
-rw-r--r--  1 david-dc david-dc   220 2009-02-26 08:32 .bash_logout
-rw-r--r--  1 david-dc david-dc  3115 2009-02-26 08:32 .bashrc
drwxr-xr-x  4 david-dc david-dc  4096 2009-03-01 14:58 .cache
drwx------  3 david-dc david-dc  4096 2009-02-26 08:51 .checkgmail
drwx------  3 david-dc david-dc  4096 2009-02-26 09:18 .compiz
drwxr-xr-x  8 david-dc david-dc  4096 2009-03-01 14:58 .config
drwx------  3 david-dc david-dc  4096 2009-02-26 08:36 .dbus
drwxr-xr-x  2 david-dc david-dc  4096 2009-02-28 13:13 Desktop
-rw-------  1 david-dc david-dc    28 2009-03-01 15:17 .dmrc
drwxr-xr-x  3 david-dc david-dc  4096 2009-02-26 17:53 Documents
drwxr-xr-x  3 david-dc david-dc  4096 2009-02-28 22:43 Downloads
-rw-------  1 david-dc david-dc    16 2009-02-26 08:36 .esd_auth
drwxr-xr-x  8 david-dc david-dc  4096 2009-03-01 14:04 .evolution
lrwxrwxrwx  1 david-dc david-dc    26 2009-02-26 08:32 Examples -> /usr/share/example-content
-rw-r--r--  1 david-dc david-dc  9267 2009-02-28 21:49 .face
drwxr-xr-x  2 david-dc david-dc  4096 2009-03-01 14:13 .fontconfig
drwx------  3 david-dc david-dc  4096 2009-03-01 19:19 .fr-PvDJtS
drwx------  5 david-dc david-dc  4096 2009-03-01 15:17 .gconf
drwx------  2 david-dc david-dc  4096 2009-03-01 19:25 .gconfd
drwx------  4 david-dc david-dc  4096 2009-03-01 14:13 .gegl-0.0
drwxr-xr-x 22 david-dc david-dc  4096 2009-03-01 14:13 .gimp-2.6
-rw-r-----  1 david-dc david-dc     0 2009-03-01 19:41 .gksu.lock
drwx------ 12 david-dc david-dc  4096 2009-03-01 19:20 .gnome2
drwx------  2 david-dc david-dc  4096 2009-02-26 08:36 .gnome2_private
drwx------  2 david-dc david-dc  4096 2009-02-26 08:36 .gnupg
drwxr-xr-x  2 david-dc david-dc  4096 2009-02-26 23:21 .gstreamer-0.10
-rw-r--r--  1 david-dc david-dc   120 2009-03-01 17:28 .gtk-bookmarks
d?????????  ? ?        ?            ?                ? .gvfs
-rw-------  1 david-dc david-dc  2832 2009-03-01 15:17 .ICEauthority
drwxr-xr-x  2 david-dc david-dc  4096 2009-03-01 14:15 .icons
-rw-r--r--  1 david-dc david-dc 28271 2009-02-26 16:06 .jap.conf
drwxr-xr-x  3 david-dc david-dc  4096 2009-02-26 15:41 .java
drwx------  3 david-dc david-dc  4096 2009-02-26 08:36 .local
drwx------  3 david-dc david-dc  4096 2009-02-26 20:12 .macromedia
drwx------  4 david-dc david-dc  4096 2009-02-26 08:53 .mozilla
drwxr-xr-x  2 david-dc david-dc  4096 2009-03-01 14:58 Music
drwxr-xr-x  3 david-dc david-dc  4096 2009-03-01 15:09 .nautilus
drwx------  3 david-dc david-dc  4096 2009-03-01 17:23 .openoffice.org2
drwxr-xr-x  3 david-dc david-dc  4096 2009-02-28 13:06 Photos
drwxr-xr-x  2 david-dc david-dc  4096 2009-02-26 08:57 Pictures
-rw-r--r--  1 david-dc david-dc   675 2009-02-26 08:32 .profile
drwxr-xr-x  2 david-dc david-dc  4096 2009-02-26 08:36 Public
drwxr-xr-x  2 david-dc david-dc  4096 2009-02-26 08:36 .pulse
-rw-------  1 david-dc david-dc   256 2009-02-26 08:36 .pulse-cookie
-rw-------  1 david-dc david-dc   623 2009-02-26 11:28 .recently-used
-rw-------  1 david-dc david-dc  2231 2009-03-01 19:20 .recently-used.xbel
-rw-r--r--  1 david-dc david-dc     0 2009-02-26 08:45 .sudo_as_admin_successful
drwxr-xr-x  2 david-dc david-dc  4096 2009-02-26 08:36 Templates
drwxr-xr-x  2 david-dc david-dc  4096 2009-03-01 14:15 .themes
drwx------  5 david-dc david-dc  4096 2009-02-28 13:04 .thumbnails
drwxr-xr-x  2 david-dc david-dc  4096 2009-02-26 08:49 .update-manager-core
drwx------  2 david-dc david-dc  4096 2009-02-26 08:36 .update-notifier
drwxr-xr-x  3 david-dc david-dc  4096 2009-02-26 08:58 Videos
drwxr-xr-x  2 david-dc david-dc  4096 2009-02-28 13:12 .wapi
-rw-------  1 david-dc david-dc   126 2009-03-01 15:17 .Xauthority
-rw-r--r--  1 david-dc david-dc  3817 2009-03-01 18:37 .xsession-errors
root@david-dc-laptop:/home/david-dc#

---

### Post by taurus on 2009-03-01
Did you save 66603-shred_file.tar.gz to your desktop (Desktop) or download directory (Downloads)?

```
cd Desktop
ls -la
```
p.s.  And by the way, I am looking at the README and no where in there that it tells you to move shred_file to /usr/share/nautilus-scripts.  If you want to shred a file, you just run it from a terminal.  Therefore, you just need to move shred_file somewhere on your path so you can call it anytime or from anywhere.

```

To run the script is easy:
	
	**shred_file** dirty_little_secrets
	
where "dirty_little_secrets" is the file you wish to shred.

This also works well as a Nautilus Action. See the included screenshot for my example configuration.
The nautilus-actions utility can be obtained from http://gnomefiles.org/app.php/Nautilus-actions or, for Debian based systems, run the following command:
	sudo apt-get install nautilus-actions
to download and install the utility.

```

---

### Post by phr33k-dc on 2009-03-01
Its saved to my downloads. how do i move it to my path?
its says on that site that when you right click you can have an option saying shred and you dont have to go near terminal?

---

### Post by phr33k-dc on 2009-03-01
its on my desktop now.

---

### Post by taurus on 2009-03-01
Then you need to change to your Downloads directory.  Unpack it and move the binary to either /usr/local/bin or ~/bin as in the picture/screenshot.

```
cd ~/Downloads
tar xvzf 66603-shred_file.tar.gz
cd shred_file
mkdir ~/bin
cp shred_file ~/bin
```

> 
its says on that site that when you right click you can have an option saying shred and you dont have to go near terminal? 

Maybe you need to read the last part of the README again.  You have to install the nautilus-actions utility first.  Then, configure it to use shred_file.

```

This also works well as a Nautilus Action. See the included screenshot for my example configuration.
The nautilus-actions utility can be obtained from http://gnomefiles.org/app.php/Nautilus-actions or, 
for Debian based systems, run the following command:
	**sudo apt-get install nautilus-actions**
to download and install the utility.

```
There is a screenshot, NautilusActionsAdd.png, in ~/Downloads/shred_file that you should look at because he showed you how to configure shred with nautilus-actions--Menu Item & Action.

---

### Post by phr33k-dc on 2009-03-01
ye ye i have nautilus-actions installed. What is the path i use then for it? do you have it or have u esed it before?

and also tryed moving it and got:

Error while moving "shred_file".
There was an error moving the file into /usr/bin.
Error moving file: Permission denied

---

### Post by phr33k-dc on 2009-03-01
made some progress when i right click (made a shred option in nautilus-actions) have a shred option but when i click it nothing happens prob cause no script

---

### Post by taurus on 2009-03-01
Where did you install that file, shred_file, to?  Did you install it to ~/bin in my previous message?  If yes, then the path to that file is /home/david-dc/bin/shred_file.  

In the screenshot, he has it as /home/**josh**/bin/shred_file because his login name is josh so you need to substitute josh with your login name, david-dc.

---

### Post by phr33k-dc on 2009-03-01
Can you tell me how to get to ~/bin because i dont know where it is?
it should work then

---

### Post by taurus on 2009-03-01
The ~ means your $HOME, /home/david-dc in this case.  So, ~/bin means it's the bin (stands for binary) directory in your $HOME--/home/david-dc/bin.  If you want to change to that directory, just cd to it.

```
cd ~/bin
pwd
ls -la
```
And if you copied shred_file to ~/bin as in my previous post, you should see it when you run the last command from above.

---

### Post by phr33k-dc on 2009-03-01
but wen i try and copy it it says i dont have permission

---

### Post by taurus on 2009-03-01
Can you post the exact command that you ran and the error message?

---

### Post by phr33k-dc on 2009-03-01
its ok taurus im to tired il post again tomorrow. Lost is about to start anyhow. thanks a million for your help

---

