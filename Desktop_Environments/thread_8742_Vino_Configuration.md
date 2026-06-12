---
title: "Vino Configuration?"
date: 2004-12-20
forum: Desktop Environments
---

### Post by midias on 2004-12-20
Hello.

I've searched this forum and on google for a long time now and was also looking around /etc for vino's configuration files, but didnt find anything useful.

Is there anybody who can tell me where to define things like the used port, standard resolution and such things for the vino-server?

---

### Post by midias on 2004-12-21
anybody?

....or any hint where would be a better place to ask this question?

---

### Post by randy on 2004-12-22
You can configure vino graphically under Desktop Preferences -> Remote Desktop.  I'd bet that the configuration lives in the gconf xml files somewhere.

---

### Post by midias on 2004-12-22
yes, there is an xml-file under ~/.gonc/desktop/gnome/remote_access/. but it is useless because it only contains the information which is also configurable by using "Desktop Preferences -> Remote Desktop"

nothing about the used ports, displays or the resolution. there must be some global system configuration file but I cant find it.

---

### Post by randy on 2004-12-22
I don't think there is a way to change ports and do things like that.  You'll probably need to use a regular vnc server for that.

---

### Post by midias on 2004-12-23
[QUOTE=randy]I don't think there is a way to change ports and do things like that.  You'll probably need to use a regular vnc server for that.[/QUOTE]

Isnt it the advantage of vino to use the actual session of a user instead of starting a new one? that's what I've been missing using a regular vnc server.

and yes. there isnt any way to change ports and stuff. after looking throu the whole documentation I've sent a mail to the developer who told me that there definitely is no way to do so atm.

---

### Post by node on 2005-01-18
I was looking for the configuration aswell, need to enable VNC thru SSH while I'm off-site atm.
There's no other way to do it than with the GUI ?

---

### Post by fakie_flip on 2006-08-13
Download a source code tarball. grep through the source code searching for 5900. Once you find it, change the number to the port that you want. Compile the source code. ./configure, make, make install and hopefully it works.

---

### Post by fakie_flip on 2006-08-13
Where can I find that configuration file? I looked for it in the place you said and this is what I got.

veronica@veronica-desktop:~$ cd ~/.gonc/desktop/gnome/remote_access/
-bash: cd: /home/veronica/.gonc/desktop/gnome/remote_access/: No such file or directory
veronica@veronica-desktop:~$

---

### Post by motin on 2006-10-07
> **node said:**
> I was looking for the configuration aswell, need to enable VNC thru SSH while I'm off-site atm.
There's no other way to do it than with the GUI ?

Here: gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

But I need to change the password as well over SSH - any ideas?

---

### Post by changlinn on 2006-10-16
Don't think it can be done, I was in the same boat, but unless someone is logged in you are better off installing and kicking off x11vnc

---

### Post by Hwoarang on 2006-11-28
So , still nobody know how to change the damn default port of Vino Server?](*,) ](*,) ](*,)

---

### Post by dbott67 on 2006-11-30
According to the research I've done, you can't change vino's default port.

Here's a thread from last year that I posted in that may be of some use:
[http://ubuntuforums.org/showthread.php?p=532501&highlight=vino+port#post532501](http://ubuntuforums.org/showthread.php?p=532501&highlight=vino+port#post532501)

If you really need to change vino's port, you'll need to install x11vnc or some other vnc variant.

-Dave

---

### Post by Hwoarang on 2006-11-30
Yeah man thanks a lot. Thats what I did and worked fine. Thanks again:D

---

### Post by quackking on 2006-12-13
This has been bothering me, too.

I want to be able to view Gnome Session 0 and not spawn another Gnome (eg, i  know I can vncserver :2, but I want to actually work along with a client on the same screen they are on), so the best thing for me would be to be able to specify what port Vino is listening on.

I downloaded the vino source from here [http://linux.softpedia.com/progDownload/Vino-Download-18305.html](http://linux.softpedia.com/progDownload/Vino-Download-18305.html)
to look at it.

If you go into the libvncserver folder in the archive and edit main.c,  line 451 reads:

rfbScreen->rfbPort=5900;

I suspect this may be the actual hard definition. It should be pretty simple to read this out of a config file instead, defaulting to 5900.

Furthermore, you could probably modify the vino_preferences.c file and the vino_preferences.glade dialog and do this interactively.

I wonder why the original maintainer would say something so un-Open Source-like as "there is no way to change the port" - which makes me suspect that there might be more going on here than just a single constant. 

Anybody else want to weigh in here?

---

### Post by jwendell on 2007-05-05
You CAN change vino port. Read [http://www.bani.com.br/index.php/2007/04/25/hidden-features-of-vino-remote-desktop-access/](http://www.bani.com.br/index.php/2007/04/25/hidden-features-of-vino-remote-desktop-access/)

---

### Post by dbott67 on 2007-05-05
I think this is only possible as of Feisty, as the keys do not exist in Dapper.  Back in March, I tried [creating the keys]("http://ubuntuforums.org/attachment.php?attachmentid=28632&d=1175346576") to see if it would work, but did not have success.

-Dave

---

### Post by jobsonandrew on 2007-12-17
I think i changed the port but ive yet to try it from an external location
in a terminal type:
```
gconf-editor
```
then navigate to:

desktop -> gnome -> remote_access

then check:
use_alternative_port

and change:
alternative_port

to whatever you want... I'll try to confirm if this works soon
========
Seems to work, you should specify the port when you attempt to connect though:
<ip_add>:<port>
eg:
1.2.3.4:5

---

