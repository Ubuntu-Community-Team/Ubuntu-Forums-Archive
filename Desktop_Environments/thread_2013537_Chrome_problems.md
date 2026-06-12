---
title: "Chrome problems?"
date: 2012-07-01
forum: Desktop Environments
---

### Post by DMGrier on 2012-07-01
So when I installed 12.04 I installed chrome but my battery went dead before it finished and it has not worked right since.

I have uninstalled it by 
"sudo apt-get remove google-chrome-stable"

and when I reinstall it right off the bat it says 
"Your profile could not be opened correctly.

Some features may be unavailable.  Please check that the profile exists and you have permission to read and write its contents."

My address bar works if I type the exact address but it does let me search anymore.

Any ideas on how to fix this?

---

### Post by ubudog on 2012-07-01
Hi DMGrier, try this from a terminal:
```
sudo chown -R <username> ~/.config/google-chrome
```
(replace username with your username) 

Best,
ubudog

---

### Post by lrcaballero on 2012-07-01
I recently changed the name of my system and forgot to closed Chrome prior to re-starting my system and couldn't open chrome! This is what I did to fix my problem:

go to Filesystem/view/show hidden files/.config/google-chrome
and delete SingleLock file
then re-start Google Chrome

---

### Post by vasa1 on 2012-07-01
> **ubudog said:**
> 
```
sudo chown -R <username> ~/.config/google-chrome
```
(replace username with your username) 
...
Could you please explain what the code does? Is it to fix "Please check that the profile exists and you have **permission** to read and write its contents." ?

---

### Post by DMGrier on 2012-07-01
input
"devon@PowerPC:~$ sudo chown -R <grier.devon> ~/.config/google-chrome"

Output
"bash: grier.devon: No such file or directory"

Then I also tried locate the file and this maybe a newb question but I went filesystem>view>show hidden files but I cannot find the .config/google-chrome? 
Thanks for the help everyone!

---

### Post by vasa1 on 2012-07-01
> **DMGrier said:**
> ... I cannot find the .config/google-chrome? 
Thanks for the help everyone!
Do you at least see a folder called **.config** in your home folder after enabling viewing hidden files and folders?
(The . means that a file having that prefix is not normally visible.)

---

### Post by DMGrier on 2012-07-01
no, is this bad?

---

### Post by vasa1 on 2012-07-01
Please open a terminal
type **cd** and hit enter
then type **pwd** and hit enter
then type **ls -al** and hit enter.
Then copy paste the stuff here within code tags which look like #. Or just paste it anyway you like.

---

### Post by ubudog on 2012-07-01
> **vasa1 said:**
> Could you please explain what the code does? Is it to fix "Please check that the profile exists and you have **permission** to read and write its contents." ?

Yep.  Alternatively, one could remove .config/google-chrome, and Chrome should make a new profile.

> **DMGrier said:**
> input
"devon@PowerPC:~$ sudo chown -R <grier.devon> ~/.config/google-chrome"

Output
"bash: grier.devon: No such file or directory"

Then I also tried locate the file and this maybe a newb question but I went filesystem>view>show hidden files but I cannot find the .config/google-chrome? 
Thanks for the help everyone!

The command would be:
```
sudo chown -R grier.devon ~/.config/google-chrome
```

> **vasa1 said:**
> Please open a terminal
type **cd** and hit enter
then type **pwd** and hit enter
then type **ls -al** and hit enter.
Then copy paste the stuff here within code tags which look like #. Or just paste it anyway you like.

+1, but that would show all of your files.  You could run:
```
cd; ls -al .config
```

If .config doesn't exist it should throw up an error.

---

### Post by DMGrier on 2012-07-01
So I would like to apologize, it was 2 AM and I kept looking under file system. When I looked under the home folder found the .config>google-chrome, I just now cannot find Single lock file?
[ATTACH]220506[/ATTACH]

---

### Post by ubudog on 2012-07-01
Could you run:
```
sudo chown -R grier.devon ~/.config/google-chrome

```

---

### Post by vasa1 on 2012-07-01
> **ubudog said:**
> ...
+1, but that would show all of your files.  You could run:
```
cd; ls -al .config
```

If .config doesn't exist it should throw up an error.

I was curious to know what else was there. Because not to have .config seemed really weird ;)

---

### Post by DMGrier on 2012-07-01
Input
"devon@PowerPC:~$ sudo chown -R grier.devon ~/.config/google-chrome"
ouput
"chown: invalid user: `grier.devon'

When I log into google I put for username [email]grier.devon@gmail.com[/email], do I need to add the gmail.com part?

I know Vasa1, it was like 2 AM and I was like I just dont see this folder and in the morning when I looked at it I was like oh....:p

---

### Post by ubudog on 2012-07-01
> **DMGrier said:**
> Input
"devon@PowerPC:~$ sudo chown -R grier.devon ~/.config/google-chrome"
ouput
"chown: invalid user: `grier.devon'

When I log into google I put for username [email]grier.devon@gmail.com[/email], do I need to add the gmail.com part?

I know Vasa1, it was like 2 AM and I was like I just dont see this folder and in the morning when I looked at it I was like oh....:p

From what I see in the terminal output, your username is devon.  So run the following:
```
sudo chown -R devon ~/.config/google-chrome
```

Best, 
ubudog

---

### Post by DMGrier on 2012-07-01
"devon@PowerPC:~$ sudo chown -R devon ~/.config/google-chrome
[sudo] password for devon: 
devon@PowerPC:~$ "

there was no output, here is my question, how do I do a fresh install of chrome. I have un-installed it by sudo apt-get remove google-chrome-stable but when I reinstall it, it is not like a fresh install cause I do not have to log into my google acount or select it to be my primary browser. Is there a better way to completely remove it?

---

### Post by vasa1 on 2012-07-01
You need to delete (or just rename) the google-chrome folder from within the .config folder after making sure no Google Chrome process is running. Then install afresh.

BTW, put up ls -al ~/.config

---

### Post by nipunshakya on 2012-07-01
```
sudo apt-get purge google-chrome-stable
```
might help you to remove google chrome totally... and then ```
sudo apt-get install google-chrome-stable
``` might install it back..

Goodluck

---

### Post by vasa1 on 2012-07-01
> **WinuxUser said:**
> ```
sudo apt-get purge google-chrome-stable
```
might help you to remove google chrome totally... and then ```
sudo apt-get install google-chrome-stable
``` might install it back..

Goodluck
A total  remove may or may not imply the removal of a profile file which is in ones home folder and which doesn't get removed by purge or remove. One has to go into the home folder and remove or rename such things to prevent them from interfering again.

---

### Post by DMGrier on 2012-07-01
drwx------ 31 devon devon 4096 Jun 30 22:19 .
drwxr-xr-x 40 devon devon 4096 Jul  1 15:49 ..
drwx------  2 devon devon 4096 Jun 12 13:27 autostart
drwxrwxr-x  3 devon devon 4096 Jun 12 10:43 banshee-1
drwx------  2 devon devon 4096 Jun 30 22:19 brasero
drwxrwxr-x  4 devon devon 4096 Jun 17 17:40 bsnes
drwx------  5 devon devon 4096 Jun  1 23:00 calibre
drwx------  3 devon devon 4096 May 31 12:22 compiz-1
drwx------  2 devon devon 4096 Jul  1 20:43 dconf
drwx------  2 devon devon 4096 Jun 30 21:52 Empathy
drwx------  2 devon devon 4096 Jun  1 22:44 enchant
drwx------  2 devon devon 4096 May 31 16:16 eog
drwxr-xr-x  2 devon devon 4096 Jun 18 21:31 gedit
drwxr-xr-x  3 devon devon 4096 May 31 12:22 gnome-disk-utility
drwxr-xr-x  3 devon devon 4096 May 31 12:22 gnome-session
drwxr-xr-x  2 devon devon 4096 May 31 12:22 goa-1.0
drwx------  7 devon devon 4096 Jul  1 00:08 google-chrome
drwx------  2 devon devon 4096 Jun 29 06:28 google-musicmanager
drwx------  3 devon devon 4096 May 31 12:22 ibus
drwxrwx---  2 devon devon 4096 Jun 17 16:39 jstest-gtk
drwxrwxr-x  3 devon devon 4096 Jun 12 14:01 menus
drwx------  2 devon devon 4096 Jun 12 13:44 mupen64plus
drwxr-xr-x  2 devon devon 4096 Jul  1 15:45 nautilus
drwxr-xr-x  2 devon devon 4096 Jun 17 17:46 phoenix
drwxrwxr-x  2 devon devon 4096 Jul  1 01:13 software-center
drwx------  2 devon devon 4096 Jun 23 09:57 totem
drwxr-xr-x  5 devon devon 4096 Jul  1 19:44 transmission
-rw-rw-r--  1 devon devon 4788 Jun  1 23:00 Trolltech.conf
drwx------  2 devon devon 4096 Jun  1 16:44 ubuntuone
drwx------  2 devon devon 4096 May 31 12:23 update-notifier
-rw-------  1 devon devon  632 May 31 12:22 user-dirs.dirs
-rw-rw-r--  1 devon devon    5 May 31 12:22 user-dirs.locale
drwxrwxr-x  2 devon devon 4096 Jun 12 10:46 vlc
drwxrwxr-x  2 devon devon 4096 Jun 12 10:51 yelp

So I would like to thank everybody for the help, I did " sudo apt-get remove google-chrome-stable" Then went into .config and removed google-chrome folder and now my browser works great after I re-installed it.

I do prefer chrome but I was wondering does Ubuntu make any money using the Ubuntu google search?

---

### Post by nipunshakya on 2012-07-01
Glad that it worked out.... Mark the thread as solved please...

well ubuntu is based on donations, investments and money from search engines i guess...

---

