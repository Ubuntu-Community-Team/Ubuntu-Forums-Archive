---
title: "Manual installation of package for Kubuntu Breezy"
date: 2005-09-21
forum: Desktop Environments
---

### Post by Keel on 2005-09-21
Interresting, Kubuntu is now installed on my PIII laptop. It has detect all of the hardware easily excet for the flash disk. Don't know what is going on. However, will continue serach the forum to see how to work out.

As a "completely new" linux user, I have a few questions.

First of all:
The laptop on which the Kubuntu is installed doesn't have access to Internet. 

According to my understanding most of the software are on the Ubuntu server and I should use Kynaptic to download them. Then the problem is that I can't use the laptop to access Internet for now. 

- Is it possible to download package from the Server and install?
- If yes what is the process of installation. Please bear with me,  and provide step to step info.

As a new user i will appreciate having the possibility to test Gnome also. 
Do i have to installed Gnome or it is already Installed.
How to switch from KDE to Gnome.

Thanks for any reply, home that it makes sense.

---

### Post by Takis on 2005-09-21
Welcome to the forums! Congratulations on your first install. Let's see what we can do.
[QUOTE=Keel]It has detect all of the hardware easily excet for the flash disk. Don't know what is going on.[/quote]
Do you know what the model of your flash disk is? If you do, it will REALLY help get it working.

> The laptop on which the Kubuntu is installed doesn't have access to Internet.

According to my understanding most of the software are on the Ubuntu server and I should use Kynaptic to download them. Then the problem is that I can't use the laptop to access Internet for now. 
It's true, there's a huge amount of software on the servers as compared to on the CD, but it's still possible to have a fully working system without being connected to the Internet.
On a side note, if you notice that when booting that a service will keep failing, and it mentions something about ntp.ubuntulinux.org, type
```
sudo mv /etc/rcS.d/S51ntpdate /etc/rcS.d/disabled_S51ntpdate
``` at a terminal (if you don't know how to access a terminal, please ask how). You'll be asked for your password.
To undo this change, type
```
sudo mv /etc/rcS.d/disabled_S51ntpdate /etc/rcS.d/S51ntpdate
```

> - Is it possible to download package from the Server and install?
- If yes what is the process of installation. Please bear with me,  and provide step to step info.
It is possible, but reasonably tedious. What software did you have in mind? There should be a lot already on CD that can do the job you need.

> Do i have to installed Gnome or it is already Installed.
How to switch from KDE to Gnome.
Well, I've managed to prove myself wrong in one hit! You can't install Gnome off the Kubuntu CD, you'll need to either download the Ubuntu CD or hook up to the Internet. For something as complicated as Gnome, it's not worth the effort to download the packages off another computer and copy them to your laptop; there's just waaaaay too many and you'd likely keep forgetting stuff.

---

### Post by Keel on 2005-09-22
Thanks Takis, your answer is clear.

> **Takis]Do you know what the model of your flash disk is? If you do, it will REALLY help get it working.[/QUOTE]
The model of the flash disk is: Easy Drive

[QUOTE=Takis]On a side note, if you notice that when booting that a service will keep failing, and it mentions something about ntp.ubuntulinux.org,[/QUOTE]
Up to now no such message. Will keep the piece of codes you provides.

[QUOTE=Takis]What software did you have in mind? There should be a lot already on CD that can do the job you need.[/QUOTE]

Will like to use TeX, Scribus, Kile, Firefox (for testing HTML page), Catdoc, Ghostscript, Gimp,DBDesigner, I will appreciate having Java, Perl, PHP, Python, Shell and MySQL installed. Will also like to have the possibility to run some Win32 applications.
Other toosl: English, French, Italian Dictionnaries and Thesaurus said:**
>  You can't install Gnome off the Kubuntu CD, you'll need to either download the Ubuntu CD or hook up to the Internet. For something as complicated as Gnome, it's not worth the effort to download the packages off another computer and copy them to your laptop; there's just waaaaay too many and you'd likely keep forgetting stuff.
Installing Gnome is only for testing purpose. As it needs that much download will just forget about it.

---

### Post by Takis on 2005-09-22
[QUOTE=Keel]The model of the flash disk is: Easy Drive[/quote]
[http://www.papyrus.co.il/Products/pc_card_drive_with_ide_interface.htm](http://www.papyrus.co.il/Products/pc_card_drive_with_ide_interface.htm)
Is that your disk? Or maybe this:
[http://www.xbitlabs.com/articles/storage/display/usb-flash-roundup.html](http://www.xbitlabs.com/articles/storage/display/usb-flash-roundup.html)
(scroll down to "EasyDisk")
Or maybe this?
[http://www.altec-computersysteme.com/web/h_en/prod/aktu/flashcard_drives/ide/easydr/index.htm](http://www.altec-computersysteme.com/web/h_en/prod/aktu/flashcard_drives/ide/easydr/index.htm)

> Will like to use TeX, Scribus, Kile, Firefox (for testing HTML page), Catdoc, Ghostscript, Gimp,DBDesigner, I will appreciate having Java, Perl, PHP, Python, Shell and MySQL installed. Will also like to have the possibility to run some Win32 applications.
Other toosl: English, French, Italian Dictionnaries and Thesaurus; Winamp or any good app for audio and video;
Okay let's go through your list. I think Tex is almost certainly on the CD, as would be Firefox, Ghostscript, PHP, Python, and the most popular shells (although you should already have a couple of them installed already!). Gimp and Java may be on the CD, I can't remember.

I haven't heard of most of your other programs. If you know what they're called, try typing ```
sudo apt-get install <program-name>
``` and post which ones don't work.

---

### Post by Keel on 2005-09-23
[QUOTE=Takis][http://www.papyrus.co.il/Products/pc_card_drive_with_ide_interface.htm](http://www.papyrus.co.il/Products/pc_card_drive_with_ide_interface.htm)
Is that your disk? Or maybe this:
[http://www.xbitlabs.com/articles/storage/display/usb-flash-roundup.html](http://www.xbitlabs.com/articles/storage/display/usb-flash-roundup.html)
(scroll down to "EasyDisk")
Or maybe this?
[http://www.altec-computersysteme.com/web/h_en/prod/aktu/flashcard_drives/ide/easydr/index.htm](http://www.altec-computersysteme.com/web/h_en/prod/aktu/flashcard_drives/ide/easydr/index.htm)
[/QUOTE]
Sorry, there was a mistake on my last post: the flash disk is EasyDisk.
> 
Okay let's go through your list. I think Tex is almost certainly on the CD, as would be Firefox, Ghostscript, PHP, Python, and the most popular shells (although you should already have a couple of them installed already!). Gimp and Java may be on the CD, I can't remember.

I haven't heard of most of your other programs. If you know what they're called, try typing ```
sudo apt-get install <program-name>
``` and post which ones don't work.
Have tried all the  apt-get and found that only Perl is installed. For the other apps, the systems display an error saying that it could not find.

Will aslo like to now how to launch an application that is not available within the KDE menu.
 ](*,)

---

### Post by Takis on 2005-09-26
[QUOTE=Keel]Sorry, there was a mistake on my last post: the flash disk is EasyDisk.

Have tried all the  apt-get and found that only Perl is installed. For the other apps, the systems display an error saying that it could not find.

Will aslo like to now how to launch an application that is not available within the KDE menu.
 ](*,)[/QUOTE]
Okeydokey:
Could you please type ```
lsmod | grep usb
``` at a terminal? (You'll need to open the KDE Menu->System->Konsole).
Using the Konsole (or any terminal emulator) is how you can run any program. Simply type the name of what you want to run (presumably you know the name - for example javac for the Java Compiler).

---

