---
title: "php issue"
date: 2009-02-09
forum: General Help
---

### Post by lostscotsman on 2009-02-09
Hi all I know nothing at all about Linux (and I bet you hear that a lot), but I have been making a web site for my local Earthday and was looking for an easier life doing the php scripts.

Would appreciate some help I suspect my issue is simple.

I worked through the examples to get apache 2 and php 5 working on the Ubuntu box I just set up, (on a POS HP machine I had lying around). My desire is simple I want to render php script in firefox, thats all! 

Up till now I have been having to upload my php scripts to look at them test them etc. 

Now when I entered

 $ gksudo "gedit /var/www/testphp.php"

At the terminal prompt it told me that I have nice running php. 

But, when I try to open a html file with a simple php script in it as a test the markup renders as normal but not the php. Any ideas what is wrong?

---

### Post by bgates on 2009-02-09
Can you open testphp.php in a browser?  [http://localhost/testphp.php](http://localhost/testphp.php)

---

### Post by lostscotsman on 2009-02-09
Yes that was part of the install routine that I followed. Is there something I should be looking for in those php settings?

Thanks for answering my post mate!

---

### Post by bgates on 2009-02-09
OK, but if you put like 

```
<?php

echo 'Hello World!';

?>
```

into a text file, save it in /var/www as test.php, then that is not loading in the browser at [http://localhost/test.php](http://localhost/test.php) ?

---

### Post by lostscotsman on 2009-02-09
I did not realize that that was needful I have been trying to open the files on the "desktop" or whatever its called in Linux.

Ok how to I get to the /var directory to move a file there, (seriously I know nothing about this stuff mate), is there an internal browser or file mover built into the GUI ?

---

### Post by lostscotsman on 2009-02-09
Ok I was being a lazy bugger I just found the directory, I will try it out with the test files I already made.

---

### Post by bgates on 2009-02-09
Yes, go to Places.  On the default panel in between Applications and System.  There is no link in there by default to go to /var or / so just click on Home for starters.  Now you are at /home/lostscotsman (or whatever your actual username is on your system).  Either click File System from the tree on the left, or click Up twice.  Now you are at /

Double click var and then www.  Now you can put any files you want in here like an index.php or test.php that contains your php code and once you save it, navigate to it in your browser to test it.  You can add /var/www to the bookmarks of the file browser as well.

---

### Post by lostscotsman on 2009-02-09
I can't move a new test file into the /var/www because it says I do not have permission as owner. I am confused I thought that "root" referred to the administrator (me). Any idea how I change this so I can get change the permissions on /var/www ?

---

### Post by lostscotsman on 2009-02-09
By the way where do I send the wine to for your help? (Wine seems to be the local currency around here).

---

### Post by mb_webguy on 2009-02-09
Unlike Windows, your primary user account does not have superuser (root) privileges by default (as a security measure).  To copy files to /var/www, you can temporarily gain superuser privileges by prefacing commands in the terminal with "sudo" (for text-based commands) or "gksu" (for GUI applications).  So you can use the command "sudo cp somefile.php /var/www/" to move the file (assuming it's in the current directory) or you can do it with nautilus by opening the terminal or pressing Alt+F2 and typing the command "gksu nautilus".

---

### Post by the_hardy_kid on 2009-02-09
The reason you are not the "owner" is because ubuntu doesn't want you deleting system files.

Anywho, to change the permissions of the folder, go to the terminal (Applications > Accessories > Terminal) and enter

```
sudo chown your-username /var/www/
```

(no offense, but just so we're clear, replace "your-username" with, well, your user name)

---

### Post by bgates on 2009-02-09
Oops I forgot that part.  root is account 1000 and yours is account 1001 (the account that can perform actions as the superuser).  It is designed that way to be more secure, so you're not just logged in as root doing things all the time.

There are several ways to go about this, the easiest and best is probably open a terminal and type gksudo nautilus

You will be prompted for your password, then the file manager will open.  Only now you will have root permissions in the file manager only.  Careful what you do in there, best to use that window for web development only unless there's a good reason to use it for something else.

Lol ninja'd twice.  Wine or WINE?  :)

---

### Post by lostscotsman on 2009-02-09
> **mb_webguy said:**
> Unlike Windows, your primary user account does not have superuser (root) privileges by default (as a security measure).  To copy files to /var/www, you can temporarily gain superuser privileges by prefacing commands in the terminal with "sudo" (for text-based commands) or "gksu" (for GUI applications).  So you can use the command "sudo cp somefile.php /var/www/" to move the file (assuming it's in the current directory) or you can do it with nautilus by opening the terminal or pressing Alt+F2 and typing the command "gksu nautilus".

Is there a global way to enter a command that allows that one folder to become drag and drop able so that I do not need to type the file allocation command every time?

---

### Post by lostscotsman on 2009-02-09
I think the other post just answered my question, do you lads mind hanging on while I change myself to super mega user in the way you described?

---

### Post by mb_webguy on 2009-02-09
Oh, and do be careful acting as root.  Since you have the capacity to do anything you want to your system, you could do quite a bit of damage if you're careless about it.

---

### Post by lostscotsman on 2009-02-09
It reported back seahorse nautilus module initialized, so thats a good thing I expect.

---

### Post by the_hardy_kid on 2009-02-09
Once the permissions of said folder are changed, you do not need to make yourself a super user.

Basically, now you have a folder which the permissions of ownership are yours, you can create edit and delete files within it.

Now, put, create, or whatever index.php in /vaw/www/ and in the url bar in firefox put 127.0.0.1.

That, will display index.php.

---

### Post by lostscotsman on 2009-02-10
Thanks lads 


Got the folder permission changed,
just tried a few different scripts all ok in the browser and I can get what I need done, without wrecking other parts of the system. 

Thanks for the info you have helped make the Earth day in my little town be a success.

---

