---
title: "Ubuntu desktop LAMP server help"
date: 2009-03-20
forum: General Help
---

### Post by joro550 on 2009-03-20
Hey I am really, really new at Linux so try and keep it as simple as possible.
So I've been using a tutorial I have found on google to set up a LAMP server and got up to setting up sampa where it says and i quote
"Setting up samba

sudo apt-get install samba
sudo ambpasswd -a username

Where username is your Linux username. Here you want to have your Windows username and password identical to that of your Linux username and password. Capitals matter. If you log into Windows with Fred but your Linux username is fred then you need to change your Windows username to fred also. First change it to fred1 and then fred, because Windows thinks Fred and fred are the same and won’t change it directly."

But then when I type in the sudo ambpasswd -a username (my Linux name) it tells me that the "sudo ambpasswd" is and i quote from the terminal "sudo: ambpasswd: command not found"
So my question is, if anyone can help me find an alternative command for this? Thanks in advance :)

[URL="http://www.spoffle.com/technical/configure-ubuntu-lamp-with-windows/"]
http://www.spoffle.com/technical/configure-ubuntu-lamp-with-windows/[/URL]

---

### Post by Chris Musampa on 2009-03-20
Try **s**mbpasswd

---

### Post by joro550 on 2009-03-20
Cheers man but now I'm having problems with the next bit of the tutorial where it says
"gksudo /etc/samba/smb.conf"
Which I think should open a file for me to edit but It's not anyone got a fix for it I have tried searching google :(

---

### Post by Chris Musampa on 2009-03-20
gksudo **gedit** /etc/samba/smb.conf

You might be able to find a better guide ;)

---

### Post by joro550 on 2009-03-20
Yeah.... that did work but I'm stuck again because of another broken link I'm going to find a better tutorial for this... cba with this one any more

---

### Post by joro550 on 2009-03-20
"Configuring a new DocumentRoot for apache

Create a directory in your /home/username/ called webpages. This will be where we put the websites we work on. Now we need to make apache look there instead of /var/www/.

mkdir /home/username/webpages/testsite01
gksudo /etc/apache2/sites-available/default

Alter DocumentRoot /var/www/ to DocumentRoot /home/username/webpages/testsite01/

Also change Directory /var/www/ to Directory /home/username/webpages/ and then directly under this alter AllowOverride None to AllowOverride All.

Now restart apache and you&#8217;re done.

sudo /etc/init.d/apache restart"

Can someone please tell me what to do here seeing as it won't create the directory, this is the last question promised xD
try and make it as simple as possible Thanks to Chris Musampa and who ever else will help me THANK YOU!!!!!!

---

### Post by lovinglinux on 2009-03-20
I don't think using the same password/username for Windows and Linux is necessary. I used samba before with different users and it worked like a charm. Besides, I wouldn't trust my Linux login details to a Windows box :)

Here are some tutorials that might help you:

[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

