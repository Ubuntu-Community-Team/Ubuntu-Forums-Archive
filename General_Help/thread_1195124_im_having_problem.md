---
title: "im having problem"
date: 2009-06-23
forum: General Help
---

### Post by rkae1020 on 2009-06-23
Hello everyone..I am new to ubuntu or lets just say linux in general..I am a windows user and now practising ubuntu..I have a problem which i don't really have an idea..I don't know where to post this question but my problem goes like this...i install apache,mysql,php in ubuntu desktop, it went fine and it works fine, the problem is this permission thing which i don't really know why i don't have permission im the admin here and why when i save my .php file to www folder it keeps on saying that i don't have permission..what the HECK!! is happening to my ubuntu desktop..i don't really have an idea..if anyone who are willing to help me i thank you..im stuck here..please help me..and please don't forget im a total noob in this OS..so please don't expect much..im just starting to learn things..

---

### Post by nice_like_rice on 2009-06-23
Where is this folder you are trying to save to? You should create a folder in your home directory, then you will have permissions for it.

---

### Post by Celauran on 2009-06-23
It sounds like you're trying to save to /var/www, which is owned by root. You can either use sudo to create/edit files in that directory, or modify Apache's DocumentRoot to point somewhere writable.

---

### Post by Sxeptomaniac on 2009-06-23
Permissions work differently in Linux.  You technically aren't operating as the admin, or, in Linux terminology, the "root" user (in fact, it would be risky to do daily tasks as the actual root user).  There are ways around this, usually involving using the "sudo" command in a terminal to temporarily gain root permissions.

It will seem a little strange at first to have this issue now and then, but it's there for a good reason, and just takes a little getting used to.  It's part of what makes Linux more secure.

In your case, a quick way to get the file where you want it could be using the command line in a terminal with sudo and the cp command for copying the file from a save spot you have permissions for.

> sudo cp <source file> <destination>

---

### Post by zadehas on 2009-06-23
If you're simply trying to set up your computer for development, here's how I think you should go about it:

press Alt-F2. In the "Run Application" dialog that pops up, type:
```
gksu gedit /etc/apache2/sites-available/default
```

Change /var/www with a location in your home folder, like /home/username/web/ (replace *username* with your own). Make sure the folder exists and that apache can write to it.

Save the apache config. Open a terminal and run:

```
sudo /etc/init.d/apache2 reload
```

Now when you point your browser to [http://localhost](http://localhost), you should be able to get whatever files you put in the "web" folder and you'll also have no problems writing to it.

---

