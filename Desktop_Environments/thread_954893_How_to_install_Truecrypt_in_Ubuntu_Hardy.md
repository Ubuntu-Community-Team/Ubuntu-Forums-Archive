---
title: "How to install Truecrypt in Ubuntu Hardy?"
date: 2008-10-21
forum: Desktop Environments
---

### Post by BuntuFirstTimer on 2008-10-21
I followed this website and tried to install this via terminal

[http://www.ubuntu-unleashed.com/2008/02/truecrypt-v50-gui-released.html](http://www.ubuntu-unleashed.com/2008/02/truecrypt-v50-gui-released.html)

And I didn't get it right. I still don't know how to use terminal commands properly. Any ideas?

---

### Post by bench on 2008-10-21
Go to [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php), under Linux, select Ubuntu deb (either x86 or x64 depending on your install), and download.

Go to terminal, cd to the directory you downloaded to (eg. ~/Desktop), then type:

```
tar xzf truecrypt-6.0a-ubuntu-x86.tar.gz
```

Make sure the filename matches the file you downloaded.  This extracts an installer.  Use ls to get the filename to execute:

```
sudo ./truecrypt-6.0a-setup-ubuntu-x86
```

You should then be able to follow the instructions.

---

### Post by BuntuFirstTimer on 2008-10-21
> **bench said:**
> Go to terminal, cd to the directory you downloaded to (eg. ~/Desktop)

CD to the directory?

---

### Post by Queue29 on 2008-10-22
> **BuntuFirstTimer said:**
> CD to the directory?

Open a terminal. (Applications/Accessories/Terminal) 
If you downloaded it to the desktop (the default for firefox) , type:

```
cd Desktop
```

and press enter.

This changes your current directory to the desktop folder. 

Then follow the previous commands.



If you're going to jump into linux, I suggest you go ahead and learn how to really use the terminal. Here's a guide that might help you on your quest: [http://linuxcommand.org/lts0010.php]("http://linuxcommand.org/lts0010.php")

---

### Post by BuntuFirstTimer on 2008-10-22
Somehow I can't open a tar.gz file via terminal. This is getting more hectic than I expected.

I typed "tar xzf truecrypt-6.0a-ubuntu-x86.tar.gz" after I command to the directory and it said:

tar: truecrypt-6.0a-ubuntu-x86.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

While "truecrypt-6.0a-ubuntu-x86.tar.gz" file is already inside the Desktop directory.

---

### Post by bench on 2008-10-22
OK, you can't be in the correct directory.  Can you see the file on your desktop? When you open the terminal, you should be in your home directory (folder).  If so then "cd Desktop" (without the quotes) will change directory to the Desktop folder.  Type "ls" and press enter and verify that you can see the truecrypt download and that it is indeed named as you said.  You should now be able to use tar to extract the file.

Just so you know, you're home folder is by default in Ubuntu at /home/<your username>.  This can be abbreviated to ~/ (the terminal shell expands the ~).  Therefore if you want to get to your desktop regardless of where the terminal's working directory currently is, type "cd ~/Desktop".

---

### Post by BuntuFirstTimer on 2008-10-22
> **bench said:**
> OK, you can't be in the correct directory.  Can you see the file on your desktop?

Yes.

And I got it. Thanks...

Though I'm still getting to know about the terminal...

is there a difference between "zxvf" and "xzf"?

---

### Post by pirattrev on 2008-10-22
> **BuntuFirstTimer said:**
> Yes.

And I got it. Thanks...

Though I'm still getting to know about the terminal...

is there a difference between "zxvf" and "xzf"?

tar is the actual program you're running, z,x,v, and f are just triggers for it.  The only difference between zxvf and xzf is the order of the triggers and 'v' which is is short for [v]erbose which just means in command line it prints the name of the new untar'd file.  Other then that, they're the same thing.

---

