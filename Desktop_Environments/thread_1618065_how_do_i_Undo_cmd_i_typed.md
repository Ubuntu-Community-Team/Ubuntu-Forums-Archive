---
title: "how do i Undo cmd i typed"
date: 2010-11-10
forum: Desktop Environments
---

### Post by kismeras on 2010-11-10
Hello everyone, 

I typed this cmd :
sudo ln -s /home/user_name/.themes /root
trying to link themes to root so that apps run as root would use the theme. However, now i can't run nautilus from a terminal...i get this:

sudo nautilus

(nautilus:3229): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

(nautilus:3229): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:3229): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


Help please........Thanks.

---

### Post by 3Miro on 2010-11-10
Lets be careful here. Try:

```
 sudo ls -al /root/ 
```

You don't have to post everything that you get back. Just look for something like .themes

---

### Post by kismeras on 2010-11-10
lrwxrwxrwx  1 root root   23 2010-11-10 04:25 .themes -> /home/user_name/.themes

---

### Post by 3Miro on 2010-11-10
OK, so to undo the original command, you have to type:

```
 sudo rm -f /root/.themes 
```

Also, if you want Nautilus to see your theme when you are running it as root, you have to copy the content of /home/your_name/.themes into /usr/share/themes.

---

### Post by kismeras on 2010-11-10
Still still getting the same thing :
(nautilus:2234): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Initializing nautilus-open-terminal extension


Nautilus does launch...but i'd like to get rid of that error msg..

Thanks for the quick replies.

---

### Post by ironic.demise on 2010-11-10
copy your ubuntulooks theme into /usr/share aswell?

By the by, cmd is Windows.
C:\WINDOWS\System32\cmd.exe
where as Ubuntu uses Bash
/bin/bash

---

### Post by kismeras on 2010-11-10
Yeah, i copied the entire contents from the themes folder over to the other themes folder. The problem is i don't think that GTK+ themes engine is installed. Been trying to figure out how to do that, but i can't.

---

### Post by 3Miro on 2010-11-10
If you go to Synaptic Package Manager (System -> Admin -> Synaptic) you should be able to look for "ubuntulooks". At any rate, the gtk engine cannot get messed up by the link in /root

There may be a cache problem, something may have been cached and that is why it is still looking for it. You can try to logout and login, which may clear the problem.

---

### Post by kismeras on 2010-11-10
I was reading something...can't find the link to it now for some odd reason. It looks like 'ubuntulooks' was replaced by Murrine GTK+ engine. That's why i can't seem to find it using SPM.

Here it is:
ubuntulooks has been depricated. It is no longer developed in Ubuntu or as an upstream project. It has been superseded by gtk2-engines-murrine since intrepid, and it has been removed from the archive in lucid. Due to this, I am closing this bug as "Won't Fix."

Closing the human-gtk-theme task as it no longer uses ubuntulooks.

[https://bugs.launchpad.net/ubuntu/+source/ubuntulooks/+bug/131974](https://bugs.launchpad.net/ubuntu/+source/ubuntulooks/+bug/131974)

---

### Post by 3Miro on 2010-11-10
Something that I just noticed. You should never use "sudo nautilus" You should use:

```
 gksudo nautilus 
```

Does this help?

---

### Post by ironic.demise on 2010-11-10
Why the gk?

---

### Post by 3Miro on 2010-11-10
> **ironic.demise said:**
> Why the gk?

gk as in gtk. This is to run a program in graphical mode with sudo privileges. Simple sudo doesn't always handle all the graphical settings files correctly. If gksudo doesn't work, you can go to /root/ and delete the .nautilus file as well as everything in /root/.gconf/apps/nautilus (just remove the entire folder)

```
 sudo rm -f /root/.nautilus
sudo rm -fr /root/.gconf/apps/nautilus 
```
(be careful when you copy/paste those commands, rm is very powerful and sudo rm can delete important files)

---

### Post by kismeras on 2010-11-10
It still does the same thing. Nautilus will open....but seeing that error msg every time is bugging the heck out of me.

~ $ gksudo nautilus

(gksudo:2388): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Initializing nautilus-open-terminal extension

---

### Post by kismeras on 2010-11-10
> **3Miro said:**
> gk as in gtk. This is to run a program in graphical mode with sudo privileges. Simple sudo doesn't always handle all the graphical settings files correctly. If gksudo doesn't work, you can go to /root/ and delete the .nautilus file as well as everything in /root/.gconf/apps/nautilus (just remove the entire folder)

```
 sudo rm -f /root/.nautilus
sudo rm -fr /root/.gconf/apps/nautilus 
```
(be careful when you copy/paste those commands, rm is very powerful and sudo rm can delete important files)

Not to sound dense or anything, but Linux is still a challenge for me. What and why would i remove those folders? Will i still be able to use nautilus? I appreciate all of the help from you guys and gals. I'm trying to learn as much as i can as i go. Would you mind explaining those cmds to me? Thanks.

---

### Post by theozzlives on 2010-11-10
I don't know if it helps, but I hit alt+F2 and type:
```
gksu gnome-appearance-properties
```
&
```
gksu gconf-editor
```

That modifies the "Root" properties. I also have a separate /root partition so the settings don't change from version to version.

---

### Post by 3Miro on 2010-11-10
> **kismeras said:**
> Not to sound dense or anything, but Linux is still a challenge for me. What and why would i remove those folders? Will i still be able to use nautilus? I appreciate all of the help from you guys and gals. I'm trying to learn as much as i can as i go. Would you mind explaining those cmds to me? Thanks.

The home folder of every user contains a number of .something folders that usually contain the individual user's settings. The .nautilus folders in /home/your_user_name are the settings for your regular user. The ones in /root/ are for the root user (root is the only user that doesn't have home in /home/username). If nautilus is trying to start and there are no settings files, then it will load the safe default settings.

gconf stands for gnome config, those specific configurations for specific Gnome applications. 

sudo means do as root
rm means remove or delete
-f means force
-r means recursive, i.e. remove the entire folder and all of its content
-fr means both force and recursive

You can get information about most of the Linux commands by typing
```
man command_name
```
or
```
command_name --help
```
(man stands for manual). There is also Google of course.

---

### Post by kismeras on 2010-11-10
Cool..thanks for the info. Yeah, i try to google and read, but i don't always get it..:confused:
I'm definitely loving Linux and learning more each day. I figure I'll get good at it in due time just like everything else. I'm on my desktop now and Linux is on my Laptop...gonna fire that up a little later and see if those last set of cmds help. Thanks again everyone for all of the help so far. :guitar:

---

### Post by kismeras on 2010-11-10
> **3Miro said:**
> gk as in gtk. This is to run a program in graphical mode with sudo privileges. Simple sudo doesn't always handle all the graphical settings files correctly. If gksudo doesn't work, you can go to /root/ and delete the .nautilus file as well as everything in /root/.gconf/apps/nautilus (just remove the entire folder)

```
 sudo rm -f /root/.nautilus
sudo rm -fr /root/.gconf/apps/nautilus 
```
(be careful when you copy/paste those commands, rm is very powerful and sudo rm can delete important files)

I tried those cmds, but i still get:

(nautilus:2226): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Initializing nautilus-open-terminal extension

Also, i had to add an r to this one:
sudo rm -f /root/.nautilus
so it looks like this
sudo rm -fr /root/.nautilus

It was telling me that i could not delete .nautilus because it was a dir. Adding the r took care of that for me. See, i learned something :popcorn:

Thanks guys

---

### Post by 3Miro on 2010-11-11
Good news then. 

If you don't have any more questions, mark the thread as "Solved".

---

### Post by kismeras on 2010-11-11
I still throws out the error msg, but i figure i'll upgrade to Mint 10 next month and that may fix it anyways. Going to research backing up my installed apps and configs to be prepared for the pending upgrade. 

Thanks to you and everyone else for all the help. I gotta say the Linux community is probably the most helpful and patient bunch of people I ever came across.

Thanks Everyone.
:guitar:

---

