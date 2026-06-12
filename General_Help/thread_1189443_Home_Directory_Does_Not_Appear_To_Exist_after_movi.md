---
title: "Home Directory Does Not Appear To Exist after moving file."
date: 2009-06-16
forum: General Help
---

### Post by fearofsquirrels on 2009-06-16
Hi,
In order to install Yamipod (in order to get my ipod to work with Ubuntu) I moved a file from the Yamipod folder (on my desktop) to my usr/lib folder using the 'sudo mv' command. After the file was moved all applications became unresponsive, so I restarted the computer.

When I tried to log on a pop up notified me that
*'Your home directory is listed as: '/home/mitch' but it does not appear to exist. Do you want to log in with the /(root)directory as your home directory? It is unlikely anything will work unless you use a failsafe session.'*

I clicked yes and it said
*'User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.*

I clicked OK and the screen went black for a few seconds and then said
*Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging on with one of the failsafe sessions to see if you can fix this problem.*

I then viewed the details, which said
[I]/etc/gdm/Xsession: Beginning session setup...

(it then said that it can't create any of the /home/mitch/ directories) 

Setting IM through im-switch for locale=en_US

Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default

(it then said that seahorse was unable to create gnome2 directory because there was no such file or directory and access was denied).
[/I]

I know almost nothing about how Ubuntu works so all of this makes no sense to me. But hopefully someone would be able to explain what this means and how to fix it.

Thanks
-mitch

---

### Post by fearofsquirrels on 2009-06-16
Also, when I press 'Ctrl+Alt+F1' at the login page and then login and enter 'sudo makedir /home/mitch' it says that the directory already exists.

I then ran these commands[I]
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo[/I]
(found them here [http://ubuntuforums.org/showthread.php?t=371052&page=3](http://ubuntuforums.org/showthread.php?t=371052&page=3))
and I was able to log on BUT all my files were gone, no music, no documents, no pictures. All my programs were installed though.
This is becoming very serious because I need to use my computer and access my documents, any help would be greatly appreciated. 

Thanks 
-mitch

---

### Post by justin_guerin on 2009-06-16
Mitch,

Have you checked /usr/lib/ for your home directory?

What comes up when you run this command:
locate mitch

Or how about:
find / -type d -name mitch -print

The locate command will succeed if your computer has been up long enough for the locate database to get updated (it updates once a day at night).  If your computer hasn't been on constantly since you lost your home, you might have to revert to the find command, which is a lot slower.

You don't happen to remember the exact command you ran to move the Yamipod folder, do you?  It might be available in your history, though if all your files are missing, your history is likely missing as well.  Nevertheless, try the history command (history) and see if you can find the move command.

Also, look in /usr/lib/ for your personal files.  That is, you might possibly have renamed /home/mitch to something else, or just moved all of its contents.

Justin

---

### Post by louieb on 2009-06-16
Sounds like you moved all the files in your home folder to usr/lib. (did you use /usr/lib as the target? there is a difference). 

You might want to boot a live cd and browse your Ubuntu install and  see if you can locate them. 

   Might want to add a new user just so you can get a gui
and give newguy sudo privileges. 

```
sudo adduser  newguy
sudo usermod  --append -G admin newguy
```

---

### Post by fearofsquirrels on 2009-06-17
I went into 'usr/lib' and searched for 'mitch' and was able to find a folder (titled 'mitch') with all of my files in it. 
How to I get the folder in 'usr/lib' to run as my home folder? (I'm not sure if that question makes sense, but I can't think of a better way to type it.)

Thanks
-mitch

---

### Post by Malac on 2009-06-17
> **fearofsquirrels said:**
> I went into 'usr/lib' and searched for 'mitch' and was able to find a folder (titled 'mitch') with all of my files in it. 
How to I get the folder in 'usr/lib' to run as my home folder? (I'm not sure if that question makes sense, but I can't think of a better way to type it.)

Thanks
-mitchYou need to move that folder from /usr/lib back to /home/mitch.
I would recommend doing this as another user/or from a live CD
Do the moves in a root nautilus (to do this if you are on gnome then press ALT-F2 then enter "gksu nautilus"). Be careful when in this nautilus it will let you do anything pretty much.
Navigate to the folder in /usr/lib called mitch then right-click on it and choose copy.
Navigate to /home then right-click and paste.
If you have already recreated a mitch folder it will ask if you want to merge them say yes and the same to any replace commands.
Log out and back in to mitch.
This should work for you.
You should delete the /usr/lib/mitch folder if everything is okay.
sudo terminal commands are powerful, as you found out. If you are not _*certain*_ if the command is correct, test it on a less important(or even a mockup)folder structure to see if it does what you expect.

Hope this helps.

---

### Post by fearofsquirrels on 2009-06-17
Thanks for your help. I followed your directions and was able to get all of my files back and my home folder back to normal. Also I changed the permission on my home folder in the category of others to 'none' got rid of the .dmrc error.

But now when I try to run firefox it says 'Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process or restart your system.'
I've looked in system manager and there is no firefox process and I have restarted the computer and still get this error. (When I was following the directions in the previous post I had firefox running, could this have caused the error?)

Also when I try to run transmission it says 'Failed to create the directory /home/mitch/.transmission/gtk: Permission denied'

How can I fix these problems? 

Thanks
-mitch

PS-I also created a new user called 'test' to try to run the commands in the previous post from, but was unable to run the command (it said that 'test' was not on the sudoer list, or something like that) Could this have contributed to the problems? And how do I delete 'test' now that I don't need it anymore?

And it says that all of my music files belong to root and I was unable to change that (even using the gksu nautilus) but am able to access them by setting the others permissions to create and destroy. How can I make 'mitch' the owner of the music files

And I used to be able to access the internet using 'sudo modprobe ndiswrapper' but that no longer works. 

I think it might be better to just backup my files and reinstall ubuntu.

---

### Post by louieb on 2009-06-17
> **fearofsquirrels said:**
> ... also created a new user called 'test' to try to run the commands in the previous post from, but was unable to run the command (it said that 'test' was not on the sudoer list, or something like that) Could this have contributed to the problems? And how do I delete 'test' now that I don't need it anymore?

Did you add user test to the admin group? that's how a user gets sudo rights. (the 2nd command i gave earlier does that)  

Unless you have something else wrong - just adding a user should not cause any problems.

Probably the the safest way to own your music files is to copy them to your home folder using your user id. Since you did the copy as you - you will own the copy. 

Before deleting user test with the **deluser** command. See if it can run firefox without a problem. If user test can the you will know the problem is just with your user id.

---

### Post by Malac on 2009-06-18
> **fearofsquirrels said:**
> Thanks for your help. I followed your directions and was able to get all of my files back and my home folder back to normal.
You're Welcome, though it sounds like we are not quite there yet.

> **fearofsquirrels said:**
>  Also I changed the permission on my home folder in the category of others to 'none' got rid of the .dmrc error.
I have attached pictures of a 'standard' home folder permissions. Depending on whether you have advanced permissions set it should look like one or other of these:
[ATTACH]118058[/ATTACH][ATTACH]118059[/ATTACH]
The easiest way is to do this in a terminal
```
cd /home
sudo chown -R mitch:mitch mitch
```
This should sort out the other problems as firefox probably can't delete the setting that tells it firefox is already running. Should also sort out transmission too.

> **fearofsquirrels said:**
> 
PS-I also created a new user called 'test' to try to run the commands in the previous post from, but was unable to run the command (it said that 'test' was not on the sudoer list, or something like that) Could this have contributed to the problems? And how do I delete 'test' now that I don't need it anymore?
System->Administration->Users and Groups.
> **fearofsquirrels said:**
> 
And it says that all of my music files belong to root and I was unable to change that (even using the gksu nautilus) but am able to access them by setting the others permissions to create and destroy. How can I make 'mitch' the owner of the music filesThis should be fixed if the previous chown command worked okay. If your music files are in another folder then 
```
cd <path-to-the-music-folder>
sudo chown -R mitch:mitch *.*
```
> **fearofsquirrels said:**
> 
And I used to be able to access the internet using 'sudo modprobe ndiswrapper' but that no longer works. Not sure about this one but it is probably the permissions again.

> **fearofsquirrels said:**
> I think it might be better to just backup my files and reinstall ubuntu.
If you can be bothered you could do that.

Hope you get it sorted.

---

### Post by fearofsquirrels on 2009-06-18
The chown command did the trick. 
Thank you so much for your help, if I encounter any more problems I'll make a post.

Thanks
-mitch

---

### Post by Malac on 2009-06-19
> **fearofsquirrels said:**
> The chown command did the trick. 
Thank you so much for your help, if I encounter any more problems I'll make a post.
 
Thanks
-mitch
You're Welcome.
Glad I could help,
Malac

---

### Post by fillintheblanks on 2009-06-19
I have the same problem when install a new kernel. I boot into the new kernel and it says my home directory does not appear to exit.. is it because my home folder is on a seperate partition?

---

### Post by Malac on 2009-06-20
> **fillintheblanks said:**
> I have the same problem when install a new kernel. I boot into the new kernel and it says my home directory does not appear to exit.. is it because my home folder is on a seperate partition?
Probably.
Check /etc/fstab for an entry similar to this
```
# /dev/sdb3
UUID=1eceaf58-ace2-409f-9fbf-c041180122c4  /home ext3 noatime,nodiratime,relatime 0  1
```the /dev/sdxx or UUID should be your home partition.

Hope this helps.

---

