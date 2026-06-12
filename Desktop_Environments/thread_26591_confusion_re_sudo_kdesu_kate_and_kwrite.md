---
title: "confusion re sudo kdesu kate and kwrite"
date: 2005-04-13
forum: Desktop Environments
---

### Post by plockery on 2005-04-13
Hi all. I'm new to Kubuntu though not to linux.

I've been reading about the sudo stuff but in doing a bit of tinkering to set ubuntu up I have found that it creates more frustration than it solves.
So I'm wondering whether I'm missing something.

Open up konqueror in file manger mode and you can open files in Kate but can't edit them - except in your home directory. What is the point in that or the point of the "Open with" menu option?

Sure you can start with # kdesu kate and edit files that way but I and I suspect many others, like to use the file manager to navigate around not the editor!

You might say  - well there is an action menu item which gives the option "Edit as root" and this opens kwrite (why not Kate in root - I did not even know Kwrite was installed until I discovered this option!!). But the problem here is that you have to type in your password for every single file you wish to edit.
Is that really any better that the old superuser/su - option? you don't have to remember two passwords - you just have to type one password in umpteen times!!!

So I decide to create my own superuser option so I only have to put my password in once - # kdesu kfmclient openProfile filemanagement.
This opens fine but what do you discover. In this mode neither Kate nor Kwrite nor anything at all will open!! It seems that once you put konqueror into root mode all the other applications have a problem with root.
Is this because the root user is disabled by default or doesn't have a password? I don't know.

What I simply want to be able to do is open a shell in root in such a way that I don't have to keep typing my password in for every single file i want to edit.

Am I missing something or is the whole sudo/kdesu-mapped-to-sudo thing really more confusing and time consuming than it is worth?

---

### Post by devil28 on 2005-04-13
did you try sudo passwd root? you get asked for a password. this means your user password (quite confusing,yes) then you can set your root-passwd.
then: edit /etc/kde3/kdm/kdmrc and change the line AllowRootLogin to =true
that makes it permanent so you can use su . hope this helps.

---

### Post by dmh-bidlah on 2005-04-13
You cold also edit the sudoers file to allow passwordless sudo. I think it went like this:
```

sudo visudo
```
then you get a nano-like text editor showing sudoers. Add a line

```
%admin ALL=NOPASSWD: ALL
```
and exit.

---

### Post by plockery on 2005-04-14
Thanks for the info.

I will probably try one of those solutions.

My point, however, is that as soon as you need to set a root password you undermine what is supposed to be one of the main aims of sudo, not to have to have a second password!!

sudo to me only seems to be useful if you only edit a single file in a session. If you begin to edit multiple files, then the necessity of repeatedly having to enter your password seems to defeat the purpose of getting around a second password to me.

I was just wondering whether others felt that way too!!

Thanks again.

---

### Post by NTolerance on 2005-04-14
[QUOTE=plockery]Thanks for the info.

I will probably try one of those solutions.

My point, however, is that as soon as you need to set a root password you undermine what is supposed to be one of the main aims of sudo, not to have to have a second password!!

sudo to me only seems to be useful if you only edit a single file in a session. If you begin to edit multiple files, then the necessity of repeatedly having to enter your password seems to defeat the purpose of getting around a second password to me.

I was just wondering whether others felt that way too!!

Thanks again.[/QUOTE]

I totally agree.  I want to be able to click on a shortcut and fire up Konqueror in dual-pane file management mode as root and be able to click on files and edit them after only entering my password one time.  The closest I have come is by getting a bit creative with launcher shortcuts and different combinations of commands, but they always end up crashing on startup after using them a few times.   :-x

---

### Post by windymiller on 2005-04-15
[QUOTE=plockery]So I decide to create my own superuser option so I only have to put my password in once - # kdesu kfmclient openProfile filemanagement.
This opens fine but what do you discover. In this mode neither Kate nor Kwrite nor anything at all will open!! It seems that once you put konqueror into root mode all the other applications have a problem with root.
Is this because the root user is disabled by default or doesn't have a password? I don't know.[/QUOTE]

The problem is that only your user is allowed to connect to the X Server.  I'm not sure why the initial "kdesu konqueror" works, but after that, the X Server won't let root open any progams on the display.  To fix this, open a konsole and type "xhost +local:" (without the quotes, but notice the colon at the end).  This will allow any local users to connect to the X Server.  So you should then be able to double click on a file in your "kdesu konquror" and the file should open as root.

---

