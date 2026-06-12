---
title: "error While Copying to &quot;...&quot;"
date: 2006-09-06
forum: Desktop Environments
---

### Post by shallow on 2006-09-06
Im a new guy
i am tring to copy a file to a folder under media, bin, etc... but when i do i get this message

Error while copying to "..." you do not have permissions to write to this folder

this is a brand new install i am using the user name that during the install it asked me to make. so from what i understand i should have admin right to all files. 

how do i go about getting permissions to have control over my own system?

---

### Post by ayoli on 2006-09-06
use sudo in a terminal like this:
```
sudo cp file /path/you/want/to/copy
```
add -r if you need to copy folders.
other way is to create a launcher on your panel wich run this command:
```
gksudo nautilus --no-desktop
```
this will open nautilus as super user (root).
be aware you can delete everything as root and may have your system totally broken.
regards.

---

### Post by shallow on 2006-09-06
Well now I just got my first disappointment with Linux

There is no way for me to go somewhere beside the terminal to allow me to access files I can see in the File System?

I thought as being the admin or root as Linux calls it I can add or delete files or folders from the file browser?

To give a better idea of why I am asking this. I am trying to see if we could use this in our company, I am one of the IT guys looking to get away from evil MS. 

But if a user can’t plug in a thumb drive or an external hard drive and then transfer information onto the thumb drive and they get this error. They will not go for it. Users will not want to go to a terminal to do this.

There isn’t any place I can go to allow a user permission to access files and folders they have on there computer

---

### Post by Tomosaur on 2006-09-06
What are you talking about? By default, your sudo password is your own password. You are the admin, and you can do whatever you like provided you use sudo. It's a security feature because people know a Root account exists (therefore, will try to log on to your system using root user). By not enabling root, they have to guess both a username and a password, effectively doubling the time they need to spend gaining access.

Using Nautilus, you can display hidden files by pressing Ctrl+H. You will not be able to do much with them, since Nautilus is essentially for your /home folder and its subdirectories. If you need to edit files above your /home, you should really be using the terminal, since the tools you need are generally terminal based.

And yes, people will be able to access their thumb drives, provided auto-mounting is working properly. If it isn't, you need to fix that first, since it is enabled by default, and it being turned off could be a symptom of a bigger problem (unless you have previously turned it off yourself)

---

### Post by tribunal on 2006-09-06
With root rights you can change everything on your PC
As a man  of early 90-th, I prefer to write 
sudo mc :)
and copy, remove, move and so on
If you want other users to do smth with protected files, you should give them rights as usual: 
chmod ....
I prefer use mc here again :)
Or, you can use konqurer (in KDE) 
kdesu konqueror

---

### Post by shallow on 2006-09-06
Im sorry guys and gals maybe I am not explaining in detail the problem.

I installed Ubuntu it asked me to for a user name and password
I used Robin as my user and a password I know.

I logged onto the system looked at it a bit surfed the web did some other things.

Here is the where the problem started:

I downloaded a file from the net into the home folder. I need this file for another computer. So I plugged in a LaCie 40gig external USB drive. 
A few seconds later there was a folder on my desktop with the name LaCie (the name of hard drive). I double clicked the folder on the desktop. It opened the external hard drive with all the files that I currently have on the drive. 

The first thing I did was right click the file in my home area "whatever.exe" and clicked cut. I then went to the LaCie drive then right clicked to click paste but it was grayed out. So I tried clicking and dragging the file from the home folder to the LaCie but when I did this I got this error
Error while copying to "/media/Lacie". You do not have permissions to write to this folder.

So I started thinking can I go to any other folder but home to do this same thing. Every time I tried it beside the home folder I got that error.

My thinking was that there was a permissions area I need to set to allow me to do this. Im such a newbie to Ubuntu that I don’t know where to go. 

I haven’t uploaded or added anything to this system yet one because I don’t know how to do anything and two I just installed it yesterday

---

### Post by peabody on 2006-09-06
First of all, I can pretty much gaurantee you're trying to write to an ntfs partition.  NTFS write support is not supported out of the box on Ubuntu for several good reasons.  If you were not using NTFS as a filesystem, you would have no problem writing to the drive.  If you absolutely need ntfs write support, here is a howto worth trying:

[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+howto](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+howto)

See my comments below on your other remarks.

> **shallow said:**
> Well now I just got my first disappointment with Linux

There is no way for me to go somewhere beside the terminal to allow me to access files I can see in the File System?


You can launch a root nautilus and browse as root.  This is, however, a monumentally bad idea.  You are coming from Windows with a windows mentality (run everything as admin).  It is very important that things outside your user folder are not edited unless you know what the heck you're doing.  It's called the principle of least privilege and Windows *is* moving in this direction with Vista.

Also, while I hate to burst your bubble, if you're seriously considering adminning several linux boxen, you are *definitely going to have to learn some basics of the terminal*.  There is just no way around that my friend.  It's not as scary as you think.

> 
I thought as being the admin or root as Linux calls it I can add or delete files or folders from the file browser?


You are not root, you are logged in under your user account.  Your user account does, however, have the privileges as an admin to gain root permissions.  Again, principle of least privilege.  You level up to admin privileges *when you need them*.

> 
To give a better idea of why I am asking this. I am trying to see if we could use this in our company, I am one of the IT guys looking to get away from evil MS. 

But if a user can’t plug in a thumb drive or an external hard drive and then transfer information onto the thumb drive and they get this error. They will not go for it. Users will not want to go to a terminal to do this.

There isn’t any place I can go to allow a user permission to access files and folders they have on there computer

Hotplug should automatically manage permissions for thumb drives.  When a thumb drive is plugged in it's mounted with permissions setup for the user to access and write to the drive.  Same thing for CD burning.  If this is your only concern, it's taken care of.  The only files you need to edit as an admin are generally under /etc, which is better done from the command line, but can be done from the gui by opening the files with a gksu gedit command under "Open With Other Application..."

---

### Post by shallow on 2006-09-06
thank you all for your help
its good to see the people are responding.

i hope my detailed problem helps

---

### Post by peabody on 2006-09-06
> **shallow said:**
> thank you all for your help
its good to see the people are responding.

i hope my detailed problem helps

Did you read my post?  If you are using NTFS you are probably out of luck.

---

### Post by shallow on 2006-09-06
so if we format these external drives to Fat32 
would this work?

---

### Post by ayoli on 2006-09-06
if you dunno how to create a panel launcher, you can simply hit ALT+F2 wich launch run dialog where you type in:
```
gksudo nautilus --no-desktop
```
then you will be prompted for your USER (Robin as i read above) password.
then you have a graphical way to browse your files as super user (root) which is dangerous (don't delete files if you don't know them and their utility).
use also documentation and wiki (support and wiki tabs on this site, above) to learn a bit about your new OS.
almost everything is doable with graphical way.
regards.

---

### Post by peabody on 2006-09-06
> **shallow said:**
> so if we format these external drives to Fat32 
would this work?

Yes.

---

