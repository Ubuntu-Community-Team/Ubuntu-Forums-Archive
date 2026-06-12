---
title: "how do I set the correct permisions for my /home drive"
date: 2006-07-10
forum: Desktop Environments
---

### Post by handy on 2006-07-10
I've created a separate **/home** drive to use with both Dapper & Breezy.  I set it up with Dapper yesterday, & am finishing up with Breezy tonight.

I seem to have a permissions problem from Breezy:  When trying to install a .deb file I am told that this kind of file is not supported?

Or if using dpkg from the command line I get the following:

**dpkg: requested operation requires superuser privilege**

Anyway, if someone could educate me with what I suspect is the appropriate chmod command, I will be greatful, & be able to move on with the setting up my installation.

Thanks in advance for your help!

**[Edit:]**  Is this the correct input: **chmod =rwx /home**

I want read, write, execute permission for all in my **/home** partition?

---

### Post by Athropos on 2006-07-10
> **handy said:**
> 
I seem to have a permissions problem from Breezy:  When trying to install a .deb file I am told that this kind of file is not supported?

Or if using dpkg from the command line I get the following:

**dpkg: requested operation requires superuser privilege**


This is independent from your /home permissions, you need 'to be root' (sudo dpkg -i ...) to install packages, don't you?

---

### Post by handy on 2006-07-10
> **Athropos said:**
> This is independent from your /home permissions, you need 'to be root' (sudo dpkg -i ...) to install packages, don't you?

Ok, I can not install using archive manager, the same file that I installed using archive manager last night, when booting from Dapper? :confused:

---

### Post by aysiu on 2006-07-10
Do not change permissions on your /home directory as a whole. [It can be disastrous.](http://www.ubuntuforums.org/showthread.php?t=211891)

Can you post the output of this command? ```
sudo dpkg -i *.deb
```

---

### Post by handy on 2006-07-10
> **aysiu said:**
> Do not change permissions on your /home directory as a whole. [It can be disastrous.](http://www.ubuntuforums.org/showthread.php?t=211891)

Can you post the output of this command? ```
sudo dpkg -i *.deb
```

Here you go Aysiu...

handy@birdfish:~$ sudo dpkg -i *.deb
Password:
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
handy@birdfish:~$

---

### Post by aysiu on 2006-07-10
Is the .deb you're trying to install in your home directory or on the desktop?

---

### Post by koshari on 2006-07-10
are you evecuting the command from the same dir as the deb is located?

also the command you want to execute will need to write to the /bin and other directorys that you need root access to perform, 

this is one of the fundimental safeguards the system uses to protect you from accidently deleting something that will break your system, 

can you install the dep through synaptic and a repository?

also you can mount your new folder in your existing directory, then the write permissions will recursive.

---

### Post by handy on 2006-07-11
> **aysiu said:**
> Is the .deb you're trying to install in your home directory or on the desktop?

/home

I often just double click on a .deb, & that opens Archive Manager.

It will not do that now.

**Archive type not supported**

is as far as it goes.

---

### Post by handy on 2006-07-11
> **koshari said:**
> are you evecuting the command from the same dir as the deb is located?

also the command you want to execute will need to write to the /bin and other directorys that you need root access to perform, 

this is one of the fundimental safeguards the system uses to protect you from accidently deleting something that will break your system, 

can you install the dep through synaptic and a repository?

also you can mount your new folder in your existing directory, then the write permissions will recursive.

This particular .deb is the Cedega install.

I will reboot into Dapper, & just make sure that I'm not fooling myself...

My memory ain't what it used to be.

---

### Post by handy on 2006-07-11
So, how do you use archive manager for .debs, if you have to be root to do it?

I'm sure that I have double clicked on downloaded .debs in the past.  Why aren't I asked for a password?

I must be too tired, at the moment, I could be making much harder work out of something than I need to.

---

### Post by handy on 2006-07-11
As far as my Breezy drive goes, I can atlast use the drive for something else.  

As I have found that the problem I have been experiencing since Dapper's arrival, which demonstrated itself by Guild Wars saying that I have an unidentified graphics card.  Is one very much akin to the way some windoze networks behave when initially being set up:  That is you do all the right things, & it doesn't work, so you undo it & do it again, repeating until it does work.  Then usually they keep working reliably!!

So, thankyou ALL for your support.

If you want to straighten me out on anything, please do, I know I know very little... :KS

---

