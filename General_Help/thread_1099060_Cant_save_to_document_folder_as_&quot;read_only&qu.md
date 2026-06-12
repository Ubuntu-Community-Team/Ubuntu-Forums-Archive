---
title: "Cant save to document folder as &quot;read only&quot;"
date: 2009-03-17
forum: General Help
---

### Post by MadMax2 on 2009-03-17
All my documents have the lock emblem and when I save (eg .odt) I get a message that the document I'm saving doesn't exist.
Thanks
Max

---

### Post by taurus on 2009-03-17
Where is that documents directory?  Is it in your $HOME or is it on another drive/partition?

---

### Post by MadMax2 on 2009-03-17
> **taurus said:**
> Where is that documents directory?  Is it in your $HOME or is it on another drive/partition?

It is in the Home folder. I can see how to fix an individual folder, but why did they (just about) all aquire a lock emblem.....?

[could this be related to my access to scanner denied problem?]
thanks

---

### Post by taurus on 2009-03-17
What are the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~
ls -la ~/Documents
```

Perhaps you need to change the ownership of those files in ~/Documents from probably root back to your username again.

---

### Post by ene_dene on 2009-03-17
I believe that you have a permission problem. Open command line, go to that directory, and then:
```
ls -l
```
You will see that probably the permissions are not OK. If you're not the owner than you type:
```
sudo chown your_username *.*
```
You can do the same on the directory, and applying the -R switch and you shouldn't have and more troubles.
If you are the owner, than probably permissions are not right, so you should change the permissions by typing
```
sudo chmod 644 *.*
```

---

### Post by Peasantoid on 2009-03-17
Or just recursively chmod everything like so:
```
chmod -R 644 ~
```

---

### Post by MadMax2 on 2009-03-17
Sorry I don't get all of that. I have run below

john@john-desktop:~$ ls -la ~

total 244
[How many do I need?]

drwxr-xr-x 40 john john 4096 2009-03-18 13:25 .

drwxr-xr-x  5 root root 4096 2009-03-15 15:21 ..

drwx------  3 john john 4096 2009-03-15 19:24 .adobe

-rw-------  1 john john  788 2009-03-18 13:39 .bash_history

-rw-r--r--  1 john john  220 2009-03-16 03:49 .bash_logout

-rw-r--r--  1 john john 3115 2009-03-16 03:49 .bashrc
drwx------  2 john john 4096 2009-03-15 17:56 .bogofilter 
drwxr-xr-x  4 john john 4096 2009-03-15 19:18 .cache 
drwx------  3 john john 4096 2009-03-15 15:58 .compiz 
drwxr-xr-x  7 john john 4096 2009-03-18 13:24 .config 
drwx------  3 john john 4096 2009-03-15 14:56 .dbus 
drwxr-xr-x  3 john john 4096 2009-03-18 12:27 Desktop 
-rw-------  1 john john   28 2009-03-18 13:24 .dmrc 
drwxr-xr-x 23 john john 4096 2009-03-18 11:05 Documents 
-rw-------  1 john john   16 2009-03-15 14:56 .esd_auth 
drwxr-xr-x  8 john john 4096 2009-03-18 13:27 .evolution 
lrwxrwxrwx  1 john john   26 2009-03-16 03:49 Examples -> /usr/share/example-content 
drwxr-xr-x  2 john john 4096 2009-03-16 07:56 .fontconfig 
drwx------  4 john john 4096 2009-03-18 13:24 .gconf 
drwx------  2 john john 4096 2009-03-18 13:29 .gconfd 
-rw-r-----  1 john john    0 2009-03-17 17:23 .gksu.lock 
drwx------ 11 john john 4096 2009-03-18 13:06 .gnome2 
drwx------  2 john john 4096 2009-03-15 14:56 .gnome2_private 
drwx------  2 john john 4096 2009-03-15 14:56 .gnupg 
drwxr-xr-x  2 john john 4096 2009-03-17 21:25 .gstreamer-0.10 
-rw-r--r--  1 john john  104 2009-03-18 13:25 .gtk-bookmarks 
dr-x------  2 john john    0 2009-03-18 13:24 .gvfs 
-rw-r--r--  1 john john 9416 2009-03-18 11:15 hp-check.log 
drwxr-----  2 john john 4096 2009-03-18 11:36 .hplip 
-rw-------  1 john john 4116 2009-03-18 13:24 .ICEauthority 
drwxr-xr-x  2 john john 4096 2009-03-15 15:06 .icons 
drwx------  3 john john 4096 2009-03-15 14:56 .local 
drwx------  3 john john 4096 2009-03-15 19:24 .macromedia 
drwx------  4 john john 4096 2009-03-15 17:32 .mozilla 
drwxr-xr-x  2 john john 4096 2009-03-15 14:56 Music 
drwxr-xr-x  3 john john 4096 2009-03-18 13:06 .nautilus 
drwx------  3 john john 4096 2009-03-18 12:04 .openoffice.org2 
drwxr-xr-x  2 john john 4096 2009-03-18 12:04 Pictures 
-rw-r--r--  1 john john  675 2009-03-16 03:49 .profile 
drw-r--r--  2 john john 4096 2009-03-15 14:56 Public 
drwxr-xr-x  2 john john 4096 2009-03-15 14:57 .pulse 
-rw-------  1 john john  256 2009-03-15 14:56 .pulse-cookie 
drwxr-----  2 john john 4096 2009-03-18 11:07 .qt 
-rw-------  1 john john 2331 2009-03-17 14:24 .recently-used 
-rw-------  1 john john 9438 2009-03-18 12:22 .recently-used.xbel 
drwxrwx---  3 john john 4096 2009-03-16 10:35 .sane 
-rw-r--r--  1 john john    0 2009-03-15 15:03 .sudo_as_admin_successful 
drw-r--r--  2 john john 4096 2009-03-15 14:56 Templates 
drwxr-xr-x  2 john john 4096 2009-03-15 15:06 .themes 
drwx------  4 john john 4096 2009-03-15 15:13 .thumbnails 


etc
john@john-desktop:~$ ls -la ~/Documents
total 6288
drwxr-xr-x 23 john john    4096 2009-03-18 11:05 .
drwxr-xr-x 40 john john    4096 2009-03-18 13:25 ..
-r-xr-xr-x  1 john john   28672 2007-09-13 18:20 Addresses.doc
-r-xr-xr-x  1 john john   11368 2007-01-08 07:45 Amazon Purchases.rtf
dr-xr-xr-x  2 john john    4096 2009-03-15 19:33 Beam for lounge
-r-xr-xr-x  1 john john   40448 2009-03-09 10:31 ByBike.xls
etc

At the moment I'm the only user (and owner) but i have set up for two other users.

What code do i use to change permissions?
sudo chmod 644 *Documents* ?

---

### Post by taurus on 2009-03-17
You need to write permission, w, also.

```
cd ~/Documents
chmod -R 644 *
chmod 755 "Beam for lounge"
ls -la
```

---

### Post by fieroboom on 2009-03-17
> **taurus said:**
> You need to write permission, w, also.

```
cd ~/Documents
chmod -R 644 *
chmod 755 "Beam for lounge"
ls -la
```

**His documents folder *does* have write permission:**
> **MadMax2 said:**
> Sorry I don't get all of that. I have run below
john@john-desktop:~$ ls -la ~/Documents
total 6288
drwxr-xr-x 23 john john    4096 2009-03-18 11:05 .
drwxr-xr-x 40 john john    4096 2009-03-18 13:25 ..


MadMax, I think the issue is we didn't quite get enough information from you in the first place.... Where *exactly* is the folder you're attempting to save documents to? Please note the full path, such as:
/home/john/some/folder/

Then run ```
ls -al
``` on that folder, and copy/paste the output here. You need to be really careful with chown and chmod.... It's extremely easy to cripple a system with the quickness if those commands are misunderstood and/or misused. Sure, you can chown and chmod to make anything work, but you need to find the problem first before you chown or chmod anything.
:D
-Paul

---

### Post by MadMax2 on 2009-03-17
john@john-desktop:~$ chmod u=rw Documents
 Document folder is empty?

---

### Post by MadMax2 on 2009-03-17
"MadMax, I think the issue is we didn't quite get enough information from you in the first place.... Where exactly is the folder you're attempting to save documents to? Please note the full path, such as:
/home/john/some/folder/"

It should be
john@john-desktop:~$ /home/john/Documents/folder
bash: /home/john/Documents/folder: Permission denied

(is there someone else here besides me)?

---

### Post by MadMax2 on 2009-03-17
"MadMax, I think the issue is we didn't quite get enough information from you in the first place.... Where exactly is the folder you're attempting to save documents to? Please note the full path, such as:
/home/john/some/folder/"

It should be
john@john-desktop:~$ /home/john/Documents/folder
bash: /home/john/Documents/folder: Permission denied

(is there someone else here besides me)?

---

### Post by taurus on 2009-03-18
> 
john@john-desktop:~$ ls -la ~/Documents
total 6288
drwxr-xr-x 23 john john 4096 2009-03-18 11:05 .
drwxr-xr-x 40 john john 4096 2009-03-18 13:25 ..
-r-xr-xr-x 1 john john 28672 2007-09-13 18:20 Addresses.doc
-r-xr-xr-x 1 john john 11368 2007-01-08 07:45 Amazon Purchases.rtf
dr-xr-xr-x 2 john john 4096 2009-03-15 19:33 Beam for lounge
-r-xr-xr-x 1 john john 40448 2009-03-09 10:31 ByBike.xls

You don't have a folder in ~/Documents so not sure what you are trying to do.  And if you want to change to a directory, you need to put the cd in front.  

```
cd directory_name
```
Did you change the permissions as in my previous reply?

```
ls -la ~/Document
```

---

### Post by MadMax2 on 2009-03-18
I think I tried everything suggested Taurus.

I can't log in at all now I have to log in under my wifes name.

I get this message:
**could not update ICEauthority file/ home/john/ .ICEauthority**

and

[B]There is a problem with the configuration server. (usr/lib/libgconf2-4/config -sanity – excited with status 256)
[/B]

I tried this advice"
"Hi - you could try this - boot into recovery mode from the grub menu. Choose root prompt from the menu, then run these one at a time

Code:
chown user:user /home/user/.ICEauthority
chmod 644 /home/user/.ICEauthority
exit
You must replace user with your username"

I failed due to UNRECOGNISED COMMANDS.

---

### Post by taurus on 2009-03-18
You need to replace user with your own login name, john.  Boot into recovery mode from GRUB menu and get into root shell.  Then, run

```
chown john:john /home/john/.ICEauthority
chmod 644 /home/john/.ICEauthority
```

---

### Post by MadMax2 on 2009-03-18
Thanks
I got a:

grub> chown john:john /home/john/ .ICEauthority

Unrecognised command     ?

---

### Post by taurus on 2009-03-18
There are many ways to do it but that is not the way.  Let's try this way.

Wait for your machine to finish booting and at the GUI login screen, press <Ctrl><Alt>F2 and log in with user john and password.  Then at the prompt, run

```
chown john:john ~/.ICEauthority
chmod 644 ~/.ICEauthority
```
Then log off with the **logout** command.  Now, press <Alt>F7 to bring back the GUI login screen and log in again as john.  Any error message now?

---

### Post by MadMax2 on 2009-03-18
Thanks I did that and typed
chown john:john ~/ .ICEauthority

chown: changing ownership of'//': Operation not permitted
chown: cannot access '.ICEauthority": No such file or directory

(it's really got it in for me!)

---

### Post by taurus on 2009-03-18
> **MadMax2 said:**
> Thanks I did that and typed
chown john:john **[COLOR="Red"]~/ .ICEauthority[/COLOR]**

chown: changing ownership of'//': Operation not permitted
chown: cannot access '.ICEauthority": No such file or directory

(it's really got it in for me!)

You have an extra space in there.

You can also put a sudo in front of those two commands in my previous post if you want.

---

### Post by MadMax2 on 2009-03-18
~/ .ICEauthority
chown[space]john:john[space]~/.ICEauthority  ?

# chown[space]john:john[space]~/.ICEauthority
chown: cannot access '//.ICEauthority': No such file or directory.

---

### Post by taurus on 2009-03-18
What's the output of this command from a prompt, assuming you've logged in as user john?

```
ls -la ~
```

---

### Post by fieroboom on 2009-03-18
> **fieroboom said:**
> You need to be really careful with chown and chmod.... 

> **MadMax2 said:**
> I think I tried everything suggested Taurus.

I can't log in at all now I have to log in under my wifes name.


Point in case. chown & chmod should NOT have been mentioned until there was an ls -al pasted of *exactly* what folder the OP was referring to.

MadMax:
In order to fix this, you need to write/print these steps, and then follow them:
- reboot
- watch for your machine to say:
"GRUB loading. please wait… Press Esc to enter the menu…"
- press the escape key
You'll be presented with a menu. Using the up/down arrows, select the one that's labeled 'recovery mode'
- press enter to boot that kernel
After some time, you'll see it stop at a root prompt similar to this:
root@ubuntu:~#
- CAREFULLY type this command *EXACTLY*:
```
chown -R john:john /home/john/
```
- press enter
- once that is finished, type reboot
- press enter

What that will do is change the ownership of everything in your home directory back to the username john (which is you), and from what I've read in this thread so far, that *should* fix your issue.
:D
-Paul

---

### Post by MadMax2 on 2009-03-18
john@john-desktop:/home$ ls -la
total 20
drwxr-xr-x 5 root root 4096 2009-03-15 15:21 .
drwxr-xr-x 20 john john 4096 2009-03-19 09:24 ..
drw-r--r-- 40 john john 4096 2009-03-18 18:20 john
drwxr-xr-x 41 keiko keiko 4096 2009-03-18 07:39 keiko
( "")       35  _ _                      etc No 3

---

### Post by taurus on 2009-03-18
```
sudo chmod 755 /home/john
ls -la /home/john
```

p.s.  You should _not_ have ran this command to your $HOME from post #6.

```
chmod -R 644 ~
```

---

### Post by MadMax2 on 2009-03-18
> **fieroboom said:**
> 

MadMax:
In order to fix this, you need to write/print these steps, and then follow them:
- reboot
- watch for your machine to say:
"GRUB loading. please wait… Press Esc to enter the menu…"
- press the escape key
You'll be presented with a menu. Using the up/down arrows, select the one that's labeled 'recovery mode'
- press enter to boot that kernel
After some time, you'll see it stop at a root prompt similar to this:
root@ubuntu:~#
- CAREFULLY type this command *EXACTLY*:
```
chown -R john:john /home/john/
```
- press enter
- once that is finished, type reboot
- press enter

Thanks previously I had missed that step (root@ubuntu:~#) and was in grub > I pushed c instead.

root@ubuntu:~#
I typed pushed enter and the command prompt reappeared (no error message or anything).I rebooted but I still have the same problem     ?

---

### Post by taurus on 2009-03-18
Can you at least post the output of this command?

```
ls -la /home/john
```
But if you would rather have somebody else to help you, then I will move on.

---

### Post by MadMax2 on 2009-03-18
> **taurus said:**
> ```
sudo chmod 755 /home/john
ls -la /home/john
```

Thanks that has fixed it!
I seem to have lost my documents however.

---

### Post by taurus on 2009-03-18
Post

```
ls -la ~/Documents
```

---

### Post by MadMax2 on 2009-03-18
john@john-desktop:~$ cd
john@john-desktop:~$ ls -la
total 244
drwxr-xr-x 40 john john  4096 2009-03-19 12:07 .
drwxr-xr-x  5 root root  4096 2009-03-15 15:21 ..
drwx------  3 john john  4096 2009-03-15 19:24 .adobe
-rw-------  1 john john  1553 2009-03-18 18:18 .bash_history
-rw-r--r--  1 john john   220 2009-03-16 03:49 .bash_logout
-rw-r--r--  1 john john  3115 2009-03-16 03:49 .bashrc
drwx------  2 john john  4096 2009-03-15 17:56 .bogofilter
drwxr-xr-x  4 john john  4096 2009-03-15 19:18 .cache
drwx------  3 john john  4096 2009-03-15 15:58 .compiz
drwxr-xr-x  7 john john  4096 2009-03-18 13:24 .config
drwx------  3 john john  4096 2009-03-15 14:56 .dbus
drwxr-xr-x  3 john john  4096 2009-03-18 18:17 Desktop
-rw-------  1 john john    28 2009-03-19 12:06 .dmrc
drw-r--r-- 23 john john  4096 2009-03-18 11:05 Documents
-rw-------  1 john john    16 2009-03-15 14:56 .esd_auth
drwxr-xr-x  8 john john  4096 2009-03-18 18:04 .evolution
lrwxrwxrwx  1 john john    26 2009-03-16 03:49 Examples -> /usr/share/example-content
drwxr-xr-x  2 john john  4096 2009-03-16 07:56 .fontconfig
drwx------  4 john john  4096 2009-03-19 12:07 .gconf
drwx------  2 john john  4096 2009-03-19 12:08 .gconfd
-rw-r-----  1 john john     0 2009-03-17 17:23 .gksu.lock
drwx------ 11 john john  4096 2009-03-18 18:15 .gnome2
drwx------  2 john john  4096 2009-03-15 14:56 .gnome2_private
drwx------  2 john john  4096 2009-03-15 14:56 .gnupg
drwxr-xr-x  2 john john  4096 2009-03-17 21:25 .gstreamer-0.10
-rw-r--r--  1 john john   104 2009-03-19 12:07 .gtk-bookmarks
dr-x------  2 john john     0 2009-03-19 12:07 .gvfs
-rw-r--r--  1 john john  9416 2009-03-18 11:15 hp-check.log
drwxr-----  2 john john  4096 2009-03-18 11:36 .hplip
-rw-------  1 john john  4287 2009-03-19 12:06 .ICEauthority
drwxr-xr-x  2 john john  4096 2009-03-15 15:06 .icons
drwx------  3 john john  4096 2009-03-15 14:56 .local
drwx------  3 john john  4096 2009-03-15 19:24 .macromedia
drwx------  4 john john  4096 2009-03-15 17:32 .mozilla
drwxr-xr-x  2 john john  4096 2009-03-15 14:56 Music
drwxr-xr-x  3 john john  4096 2009-03-18 13:06 .nautilus
drwx------  3 john john  4096 2009-03-18 18:16 .openoffice.org2
drwxr-xr-x  2 john john  4096 2009-03-18 12:04 Pictures
-rw-r--r--  1 john john   675 2009-03-16 03:49 .profile
drw-r--r--  2 john john  4096 2009-03-15 14:56 Public
drwxr-xr-x  2 john john  4096 2009-03-15 14:57 .pulse
-rw-------  1 john john   256 2009-03-15 14:56 .pulse-cookie
drwxr-----  2 john john  4096 2009-03-18 11:07 .qt
-rw-------  1 john john  2963 2009-03-18 14:30 .recently-used
-rw-------  1 john john 11833 2009-03-18 18:20 .recently-used.xbel
drwxrwx---  3 john john  4096 2009-03-16 10:35 .sane
-rw-r--r--  1 john john     0 2009-03-15 15:03 .sudo_as_admin_successful
drw-r--r--  2 john john  4096 2009-03-15 14:56 Templates
drwxr-xr-x  2 john john  4096 2009-03-15 15:06 .themes
drwx------  5 john john  4096 2009-03-18 16:13 .thumbnails
drwxr-xr-x  4 john john  4096 2009-03-17 17:23 .tomboy
-rw-r--r--  1 john john  5508 2009-03-17 17:48 .tomboy.log
drwxr-xr-x  2 john john  4096 2009-03-15 15:02 .update-manager-core
drwx------  2 john john  4096 2009-03-16 19:58 .update-notifier
drwxr-xr-x  2 john john  4096 2009-03-15 14:56 Videos
drwxr-xr-x  2 john john  4096 2009-03-17 17:48 .wapi
-rw-------  1 john john   123 2009-03-19 12:06 .Xauthority
-rw-r--r--  1 john john   129 2009-03-15 15:11 .xscreensaver-getimage.cache
-rw-r--r--  1 john john  2017 2009-03-19 12:07 .xsession-errors
john@john-desktop:~$ cd /home/john/Documents
bash: cd: /home/john/Documents: Permission denied
john@john-desktop:~$ ls -la ~/Documents
ls: cannot access /home/john/Documents/Keiko: Permission denied
ls: cannot access /home/john/Documents/..: Permission denied
ls: cannot access /home/john/Documents/Grandad: Permission denied
ls: cannot access /home/john/Documents/Wieghts.xls: Permission denied
ls: cannot access /home/john/Documents/Deck Quote metalcraft.pdf: Permission denied
ls: cannot access /home/john/Documents/Henry George: Permission

and
-????????? ? ? ? ?                ? ScientificAmerican_Daly_05.pdf
-????????? ? ? ? ?                ? Screen Resolution and monitor settings.odt
d????????? ? ? ? ?                ? Shadows of Forgotten Ancestors
d????????? ? ? ? ?                ? Sreenshots
-????????? ? ? ? ?                ? Step Down Transformer.doc

---

### Post by taurus on 2009-03-18
I assume Documents in your $HOME (/home/john/Documents) is the one you are talking about.

```
chmod -R 755 ~/Documents
ls -la ~/Documents
```

---

### Post by MadMax2 on 2009-03-19
That has fixed it thanks a lot! I have had Ubuntu on my laptop and it works well. :smile:

---

### Post by theozzlives on 2009-03-19
Sometimes when you copy files over the network, etc. ypo get owner: Nobody; Group: Nobody. Just change them back to you.

---

