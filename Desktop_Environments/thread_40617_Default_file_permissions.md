---
title: "Default file permissions"
date: 2005-06-09
forum: Desktop Environments
---

### Post by bryklie on 2005-06-09
Hello everyone,

I am trying configure Gnome so that when I create a file through the UI (i.e. using the nautilus file manager) the default permissions on the new file are set to 
RW-RW----.

I've looked at the umask command but this seems to only work when using a shell such as bash.  I've also tried updating /etc/profile with the line 'umask 007' but this also does not do anything.

Is anyone able to help me out here?

---

### Post by Alexander Kirillov on 2005-06-09
[QUOTE=bryklie]Hello everyone,

I am trying configure Gnome so that when I create a file through the UI (i.e. using the nautilus file manager) the default permissions on the new file are set to 
RW-RW----.

I've looked at the umask command but this seems to only work when using a shell such as bash.  I've also tried updating /etc/profile with the line 'umask 007' but this also does not do anything.

Is anyone able to help me out here?[/QUOTE]
 Hmm... putting umask=007 in /etc/profile should have done it. What permissions do you get if you cretae a file using command line tools ("touch <filename>")? If you type "umask" on command line, what do you get? (It is supposed to give current umask).

---

### Post by bryklie on 2005-06-10
Apologies Alexander for not replying sooner...I was at work when I posted the message and have just got home.

When I create a file using vi from the command line the permissions are rw-rw---- which is just what I want.

When I create a file from nautilus by using the command File -> Create Document -> Empty File the persissions are rw-------

Typing umask from the command line gives me 0007.

---

### Post by Alexander Kirillov on 2005-06-10
[QUOTE=bryklie]Apologies Alexander for not replying sooner...I was at work when I posted the message and have just got home.

When I create a file using vi from the command line the permissions are rw-rw---- which is just what I want.

When I create a file from nautilus by using the command File -> Create Document -> Empty File the persissions are rw-------

Typing umask from the command line gives me 0007.[/QUOTE]
 Indeed, on my system exact same thign happens - Nautilus creates file with permissions -rw------
Never noticed it because I never created files from Nautilus. 

I have to admit I do not know where this permission comes from - definitely not from umask. Maybe you should ask on Nautilus mailing list: 
[http://mail.gnome.org/mailman/listinfo/nautilus-list](http://mail.gnome.org/mailman/listinfo/nautilus-list)

---

### Post by bryklie on 2005-06-10
It's a mystery isn't it...?

If/when I find out the answer I'll let you know.

Thank you for your help...

Bryklie

---

### Post by mikk0 on 2005-07-12
This thing is really annoying!

I ran the following command:
```
sudo find /etc | xargs grep umask
```
and found a whole lot of files that had umask 022 in them. And yes, Nautilus still don't obey even those settings.

Here comes my problem. I am trying to make a shared folder for my users and would like to make the default umask for them 002 so when they create folders or files in the shared folder, they could be used/renamed/moved by others in the same group.
This folder has setgid-bit on, so all files are already owned by the group 'users'. It just isn't enough without different umask setting  ](*,) 

Please. Someone has to know the reason to this.
All I can found with Google is questions about setting umask in Gnome, but no answers!

Mikko

---

### Post by cwaldbieser on 2005-07-12
Maybe I am missing something, but I haven't actually seen an example in any of the above posts where it was demonstrated that umask was not working.  I suspect there is a slight misubderstanding as to what umask actually does.

The umask command is used to *take away* permissions.  So for example, you can use umask to say something like "Regardless of what permissions the program 'gedit' is going to give a newly created file, I want to take away write and execute permissions from the group and others."  The umask command cannot give permissions to a file that a program did not originally bestow on it.

For example, my umask is 0022.  If the "touch" command normally would create a file with permissions rwxrwxrwx (777), my umask would strip it down to rwxr-xr-x.  However, observe the following commands:

```
$ touch newfile
$ ls -l newfile
-rw-r--r--  1 carl carl 0 Jul 12 21:22 newfile
```

So what happened to the executable permissions for group and other?  The explanation is simple-- the touch command *never gave* those permissions to the file to begin with.

The same thing is probably happening with Nautilus.  I set my umask to 0000 and ran Nautilus.  I then created a new file.  The permissions on the file were rw-------.  This means that by default, Nautilus is only giving read and write permission to the user.  No other permissions are granted.

Not sure where (or even if) you can set these default permissions.

---

### Post by mikk0 on 2005-07-13
Thanks.

I didn't think of that although it was obvious when downloading an image from camera would make the resulting file just what I wanted (rw-rw-r--), while Nautilus creates files with permissions of (rw-------).
The Nautilus's behaviour was not my concern, anyway, but what bugs me is that when I create a new directory (by that digicam-program or through Nautilus), it gets a maximum of (rwxr-xr-x), no matter what the umask is (In bash everything works like a charm, though  :-) .
This makes my shared folder a little harder to use than was intended.

But anyway. What is the best method of setting users umask at startup. Where should the setting be to have effect for all users?

/etc/login.defs ? (I changed it there already, so let's give it a go)

Mikko

---

### Post by pmartino on 2007-09-28
For gnome to tale into account settings you must create in your home directory a file called ".gnomerc" and put the umask command in it.
Of course you can also use any other shell command.
Nautilus, etc... will now use the new value (after re-login of course)

Hope it helps

---

