---
title: "Copying data"
date: 2006-05-30
forum: Desktop Environments
---

### Post by InsanePenguin08 on 2006-05-30
A true Linux n00b, I've been using it for several months and just realized that I could log in as root by just typing in 'root' as my username and my regular password at the splash screen.  Now that I've realized that, I was wondering what the easiest way to transfer all of my files and settings from the one account to the root account (i.e. Firefox bookmarks and launch sites.) I really don't want to have to manually change everthing in the GUI.  Any way to do this in the terminal?

Thanks in advance!
InsanePenguin


Oh, and btw, does anyone know any websites that could help me learn most of the basic commands in the terminal?  Thanks again!

---

### Post by aysiu on 2006-05-31
Why do you want to log in as root?

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by InsanePenguin08 on 2006-05-31
Just because I'm the only user on the computer, I figure it's easier to just always log in as root instead of 'sudo su' in the terminal whenever I need to do something that requires higher permissions.  Is there any reason I wouldn't want to always log in as root?

---

### Post by aysiu on 2006-05-31
Sure. It's dangerous.

And, you don't need to *sudo su.*
Read the first link I posted.

---

### Post by InsanePenguin08 on 2006-05-31
Well then, excellent!  Thansk for your help, but do you have anything to tell me about my first question?  If not, that's fine, you've been plenty of help already!

---

### Post by aysiu on 2006-05-31
If you really are intent on using the root account (it's your choice, but just about everyone here will warn you against logging in as root), you can always symlink your folders from your account to the root account.

For example, if you want root to use your Firefox settings, paste this command in ```
sudo ln -s ~/.mozilla /root/.mozilla
``` You may find that using Firefox as root will screw up your user permissions with the ~/.mozilla file, but if you're planning to run as root all the time, that shouldn't bother you.

---

### Post by jones_jj on 2006-05-31
I assume you're using gnome as your window manager.  If so, just open nautalis, it's file system explorer, and navigate to "/" which is the root level of the whole filesystem.  From there you will see a directory called /home, and you will see your username so it will look like /home/<username>  just copy everything that's in there and paste it into the account you want to if you have another one created.

To do this in a terminal you will want to do a:
**cp -R *.* /<directory>**  This will copy everything in the current directory recursively and move it to a directory you want to move it to.  I believe this is the correct command to do what you want.  Also you can use **cp -R <directory1> <directory2>**

---

### Post by aysiu on 2006-05-31
If you want to copy, you don't need Nautilus. ```
sudo cp -R ~/* /root/*
```

---

### Post by jones_jj on 2006-05-31
Do you really need to use sudo to copy something to /root?

---

### Post by InsanePenguin08 on 2006-05-31
Thanks alot for all the information, I'm sure I'll have to use it down the road some time.  For now I'll take your advice and not log in as root.

---

### Post by aysiu on 2006-05-31
[QUOTE=jones_jj]Do you really need to use sudo to copy something to /root?[/QUOTE] Yes.

---

### Post by jones_jj on 2006-05-31
InsanePenguin08, a very smart move on not logging into root to do daily tasks such as browsing and checking e-mail.  Only use root to do administrative things, and even then just use **su** or **sudo**, this is a lot safer and you will not be able to wreak havoc on your Linux box seeing how you are fairly new to Linux.

---

### Post by InsanePenguin08 on 2006-05-31
Aye, aye captain!

---

