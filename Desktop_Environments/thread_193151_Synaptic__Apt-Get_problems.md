---
title: "Synaptic / Apt-Get problems"
date: 2006-06-09
forum: Desktop Environments
---

### Post by xxrealmsxx on 2006-06-09
For some reason Synaptic will not allow me to edit my repositories, when i click it the app waits for a second and then does nothing!

I had a pop up box last time however I clicked the check box that said it should not pop up again 8-[ and I dont remember what it said :(

Furthermore when i try apt-get to install wine It doesnt work:
jamiewitter@jamiewitter-laptop:~$ apt-get install wine
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jamiewitter@jamiewitter-laptop:~$


I am a complete newbie to using Linux so I am thinking i probably did something dumb and messed my system up. I also have automatix installed if that may have affected anything.

Thanks for the help in advance!

Other than this and having no 3d acceleration I really like Ubuntu 6.06.
I just need to install wine/vmware so I can do some work for a class that only uses Microsoft products :(

---

### Post by jturnbul on 2006-06-09
I know you cant have both Adept or Synaptic open at the same time, and have them work, or use apt with either of them open.  You can only use one of the three at a time.

---

### Post by xxrealmsxx on 2006-06-09
Yeah I know that, They are all closed :( I wish it were that easy.

---

### Post by BungaMan on 2006-06-09
you need to use sudo to do tasks that require administrative rights such as apt-get so try
$  sudo apt-get etc...

it will ask for a password which is the password of the first account you created during install

---

### Post by xxrealmsxx on 2006-06-09
[QUOTE=BungaMan]you need to use sudo to do tasks that require administrative rights such as apt-get so try
$  sudo apt-get etc...

it will ask for a password which is the password of the first account you created during install[/QUOTE]
Thanks!

If terminal says that a package cannot be found that means I need to add the repository correct?

If so I still cannot add the repositories I need due to the problem i mentioned earlier :(.

---

### Post by styven on 2006-06-09
Hi,

Have you tried Add Applications (applications, add applications)

After you entered your root password, go to settings, repositries and add what is required.

From my experience i use "synaptic" as a last resort, "add applications" works well, for everything else the "terminal" is quick and fuss free in most cases.

Hope that helps....

Steve

---

### Post by sparhawk on 2006-06-09
[QUOTE=xxrealmsxx]Thanks!

If terminal says that a package cannot be found that means I need to add the repository correct?

If so I still cannot add the repositories I need due to the problem i mentioned earlier :(.[/QUOTE]


To add a repository try this in the terminal.

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

That will create a backup of your current list and allow you to edit it.

I suggest you do not use unofficial repositories until you know what you are doing because that will open up a whole new can of worms... of course if I followed that logic I would not know linux as well as I do now. Just be ready to break some stuff and spend your time learning and fixing :)

---

### Post by xxrealmsxx on 2006-06-09
[QUOTE=sparhawk]To add a repository try this in the terminal.

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

That will create a backup of your current list and allow you to edit it.

I suggest you do not use unofficial repositories until you know what you are doing because that will open up a whole new can of worms... of course if I followed that logic I would not know linux as well as I do now. Just be ready to break some stuff and spend your time learning and fixing :)[/QUOTE]

Well, I tried the first command you gave and this is what happened:

jamiewitter@jamiewitter-laptop:~$ sudo cp /etc/apt/sources.list/etc/apt/sources.list_backup
cp: missing destination file operand after `/etc/apt/sources.list/etc/apt/sources.list_backup'
Try `cp --help' for more information.

furthermore Sources.list when I open it is blank, is that a problem?

Yeah I'm actually buying the official ubuntu book in a couple of weeks but I just want vmware to work (which for some reason apt-get wont download the files i need) so i can access windows xp for some school work :(.

---

### Post by aysiu on 2006-06-09
[QUOTE=xxrealmsxx]Well, I tried the first command you gave and this is what happened:

jamiewitter@jamiewitter-laptop:~$ sudo cp /etc/apt/sources.list/etc/apt/sources.list_backup
cp: missing destination file operand after `/etc/apt/sources.list/etc/apt/sources.list_backup'
Try `cp --help' for more information.[/QUOTE] You're missing a space. It should be ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` instead of ```
sudo cp /etc/apt/sources.list/etc/apt/sources.list_backup
``` See the difference? > furthermore Sources.list when I open it is blank, is that a problem? If you called it ```
Sources.list
``` it would be blank. Everything in Ubuntu is case-sensitive. So the command to edit the sources.list would be ```
gksudo gedit /etc/apt/sources.list
``` instead of ```
gksudo gedit /etc/apt/Sources.list
```

---

### Post by sparhawk on 2006-06-10
yeah sorry about that. There should be a space and the sources.list should never be blank. I didn't know that Ubuntu had a book... that's cool. Maybe I will get one. In the meantime I would suggest looking online for a basic linux/unix tutorial to help answer some of your basic user issues like the case sensitive file names and copy command, thats what I did when I started. It helped a lot.

---

### Post by xxrealmsxx on 2006-06-10
[QUOTE=aysiu]You're missing a space. It should be ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` instead of ```
sudo cp /etc/apt/sources.list/etc/apt/sources.list_backup
``` See the difference?  If you called it ```
Sources.list
``` it would be blank. Everything in Ubuntu is case-sensitive. So the command to edit the sources.list would be ```
gksudo gedit /etc/apt/sources.list
``` instead of ```
gksudo gedit /etc/apt/Sources.list
```[/QUOTE]

I followed what you said and got this output:

jamiewitter@jamiewitter-laptop:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
cp: cannot stat `/etc/apt/sources.list': No such file or directory
jamiewitter@jamiewitter-laptop:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
cp: cannot stat `/etc/apt/sources.list': No such file or directory
jamiewitter@jamiewitter-laptop:~$ gksudo gedit /etc/apt/sources.list

(gedit:5490): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
jamiewitter@jamiewitter-laptop:~$

sources.list is also empty. Is it possible the file got deleted somehow?

---

### Post by xxrealmsxx on 2006-06-10
[QUOTE=sparhawk]yeah sorry about that. There should be a space and the sources.list should never be blank. I didn't know that Ubuntu had a book... that's cool. Maybe I will get one. In the meantime I would suggest looking online for a basic linux/unix tutorial to help answer some of your basic user issues like the case sensitive file names and copy command, thats what I did when I started. It helped a lot.[/QUOTE]

Yeah this is the book: [http://www.phptr.com/bookstore/product.asp?isbn=0132435942&rl=1](http://www.phptr.com/bookstore/product.asp?isbn=0132435942&rl=1)

A basic tutorial would be a good idea, i'll look into it thanks

---

### Post by sparhawk on 2006-06-10
[QUOTE=xxrealmsxx]Yeah this is the book: [http://www.phptr.com/bookstore/product.asp?isbn=0132435942&rl=1](http://www.phptr.com/bookstore/product.asp?isbn=0132435942&rl=1)

A basic tutorial would be a good idea, i'll look into it thanks[/QUOTE]

Cool Thanks for the link.

As for your problem the cp command is saying you do not have a file named sources.list at the path of /etc/apt/

If thats the case then how is it you know its empty. I would create a new one there and find the default ubuntu repositories to add and then do an apt-get update to check for updates and get you back on track.

Let me know how it goes

---

### Post by aysiu on 2006-06-10
Well, I guess your sources.list really *is* blank, then.

This will help you populate it.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by xxrealmsxx on 2006-06-11
[QUOTE=aysiu]Well, I guess your sources.list really *is* blank, then.

This will help you populate it.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)[/QUOTE]

Following the instructions exactly didnt help but the repository listing and ideas behind the link did. I was able to fix it and I am now installing Windows XP Professional Under Vmware, you rock :D

---

