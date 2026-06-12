---
title: "noob needs help setting up not so noobish things"
date: 2008-12-09
forum: Desktop Environments
---

### Post by Rio_Hasegawa on 2008-12-09
^ as the above says or so I think.

Setting up ubuntu was an easy process for my 1TB which I intend to make a server, now here is where I get lost.

First I want to make it able to receive files from my vista laptop *shivers from saying vista* onto my ubuntu machine and I think it needs something called samba which I have no idea how to set up. But then i want to have access to the media/files using my laptop and PS3 not to mention me able to access this form the internet (I think is called FTP or something like that)

Who ever is willing to help you have my deepest thank (if its worth something to you)

Thank you very much in advance

---

### Post by modmadmike on 2008-12-09
You should just be able to install the samba server from synaptic and read the manual for it (google it) to set it up. Then you can make a batch script on the laptop and place it into startup thus it will copy the files over when it boots.

---

### Post by modmadmike on 2008-12-09
> **modmadmike said:**
> You should just be able to install the samba server from synaptic and read the manual for it (google it) to set it up. Then you can make a batch script on the laptop and place it into startup thus it will copy the files over when it boots.

Don't worry the manual it only a few short pages.

---

### Post by Rio_Hasegawa on 2008-12-09
Thx I'll give that a try and see how it goes from there, is there anyone else?

---

### Post by jonobr on 2008-12-09
Hello

modmadmike is right that samba is probably the app for you, however, 
I would like to add a few more suggestions if your feeling adventurous.

First  you should figure out whats pulling and whats pushing.

For example, with FTP you mention ( the file transfer protocol)
you can have a client and a server, the client can pull or push files depending on what you want to do.
Its the same for most client/server systems.

That being said , heres a couple of things you could try,

on your xp machine you could install the ftp server. You could use XP ftp or an available download client. I use a simple program called 3cdaemon for my windows ftp server , its simple and easy and by default allows anonymous users to download.

WHen you setup 3cdaemon on your xp, you point to a directory where you want to place your files for download.

When they are there, you can do two things,
From a browser you could type [ftp://anonymous@your_ip_address/](ftp://anonymous@your_ip_address/)
this will get you to the root directory of your ftp on the other machine, just click the file you want,,
The password for anon access is anything you want but its courteous if the server is not yours to put down your email addr.

If your handy at typing and dont want a browser, jump to your ubuntu terminal window,
and then type the following commands to download.

```

ftp Your_xp_ip_address <- opens the ftp protocol
user - anonymous  <- anonymous user is default
password- anything <- again courtesy dictates in ftp you enter your email addr for anonymous download



```

then type the following commands (imagine you are downloading a film called 3kings.avi

```

bin <- this changes to binary mode
hash <- this changes to hash mode ( it shows the progress)
mget 3kin* < get anything that starts with 3kin


```

If you wanted , you could get everything in the directory
instead of typing 3kin*  you could jsut do * , and that means everything.

It will prompt you for the files to download.
You could enter the command prompt to stop it asking and just download everything.

to put files to the windows box, you would type mput *.avi

Ok, so now if you wanted to change it around and have the ubuntu box as the server, then you could install a program using synaptic called vsftp which is pretty simple.
This time you open a command prompt on windows box anf type the same commands to move files.

The problem with FTP is it is insecure.
Your username and password are sent clear text. THis is only a concnern if you going across the internet or insecure connections.

A good utility for comparing files between systems and copying the difference is rsync which is secure.
On windows you could install cwrsync and ubuntu has rsync on it.
If you would like more info on that google man rsync or post here.

one other thing you could try is installing your own web server.
Using synaptic you could install apache2.
I could post a simple home page file (index.html) to allow you post files and upload and download them from your other machine.
You could have a simple directory strucutre which you could put your files and then just do simple point and click from your windows box.

Hope this was of some use.

---

### Post by Rio_Hasegawa on 2008-12-14
thank you very much everyone now my other question how do I set up synergy(sp?) with my vista laptop being the server and my linux machine being the client?

---

### Post by Rio_Hasegawa on 2008-12-14
thank you very much everyone Im going to give everything a try in a little bit so I'll give you my feedback on it, and now my other question how do I set up synergy(sp?) with my vista laptop being the server and my linux machine being the client?

Ok I just tried the 3CDeamon and it was exactly what I wanted now I just have two queries about it. Is there a way of using this on linux machine instead of my laptop or is the program itself designed to be used in both? thanks in advance

and by the way how do I delete my previous reply? I can't seem to find the delete button

---

