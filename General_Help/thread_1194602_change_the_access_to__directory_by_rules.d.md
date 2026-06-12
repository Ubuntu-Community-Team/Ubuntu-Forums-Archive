---
title: "change the access to / directory by rules.d"
date: 2009-06-22
forum: General Help
---

### Post by chang5562 on 2009-06-22
I have both 8.10 and 9.04 version installed on separated machine.  Just  read few articles about write something into the /etc/udev/rules.d to change the accessibility of certain device.  Can I create a file there to deny the access of the /, root directory.  How?  Never done this before.  Any danger to do this?  any good tutorial about this rules.d

My 8.10 plateform has a lot XX-xxxx.rule files, but 9.04 only has 2, for net and cd.

---

### Post by geirha on 2009-06-22
There's really no point in restricting access to /, other than making sure only the root user has write access to it, which is the default. If a user doesn't have access to /, the user is useless, as it will have no access to any programs at all.

---

### Post by Agent ME on 2009-06-22
Every single file in the system is under /. If you prevented any user read-access to it, you've made that user completely useless.

---

### Post by chang5562 on 2009-06-23
Thanks, Agent and Geirha, Both of you have the point.  However, I run into a situation that caused a little alarm.  

When a user opens a text editor, ex gedit, the user can access the "File System" and cruise around the / and some of the files underneath, deep down inside, are common executable file to everyone.  For example, gnome-terminal, can be dragged / run on the desktop.   From there, a user can do a lot of unexpected things.  Because I am setting up an environment that the regular user only can use whatever I gave to them on the desktop.  So I tried to avoid any un-ordinary to happen.  

Then I noticed the /etc/udev/rules.d from other thread. It seems appealing to my intention.  I intent to hide or to deny the user to access the File System, /, but only to the user's home directory.

Any hope to do this?  I only began to work on Ubuntu, or any flavor linux, 3 months ago.

---

### Post by sdennie on 2009-06-23
There are two ways you could at least give the appearance of doing this.  If the user will never use the command line, try this:

```

sudo sh -c "ls / > /.hidden"
sudo sed -ie "s/home//" /.hidden

```

That will make it so that in the root directory nautilus will only show the home folder unless the user turns on "show hidden files".

For a more extreme example of this, check: [http://www.gobolinux.org/index.php?page=doc/articles/gobohide](http://www.gobolinux.org/index.php?page=doc/articles/gobohide).  That implements the hiding at a kernel level but, the files are still accessible.

---

### Post by bodhi.zazen on 2009-06-23
I have to agree, hiding everything or restricting access in / is not a viable solution. I suggest you stop for a minute and look at how Linux works and Linux security :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Changing permissions on system files is a sure way to break Ubuntu and again this is not how security is handled.

If basic permissions is not sufficient for you, take a look at apparmor or selinux.

---

### Post by chang5562 on 2009-06-23
Totally agree with your points.  I do not intent to deny the access for user.  I just want to hide those / from user for unnecessary detour.  (of course, if an user tends to break in, he/her still can find the way in)

Actually I started another thread to target the exact problem, ie. to remove the "File System" under the Places of the gtk File chooser. Do any one of you know how?

---

