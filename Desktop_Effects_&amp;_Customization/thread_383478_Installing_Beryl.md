---
title: "Installing Beryl"
date: 2007-03-13
forum: Desktop Effects &amp; Customization
---

### Post by scurlaruntings on 2007-03-13
Right i have 2 problems. The long and short is my Ubuntu box got corrupted and seeing as im not advanced enought to recompile the gnome i elected to rebuild the box.This has presented me with 2 problems both of which i was able to resolve before.

1) I have added **"deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main"** to my repository under system/admin/sources ( or just edit the source list manually as root) but when i try to update the source im returned with an error that the public key isnt available. Tp circumvent this i went to the beryl.project website and done as advised to enter the command **"wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add - "** to update the public key but now im being retured with the error **"gpg: no valid OpenPGP data found."** I am now at my wits end and pulling my hair out to install Beryl which although a fiddly process is fairly straight forward to do from the wiki page.

2) There is a utility that allows you install windows drivers Ndiswrapper style (thats gui based) rather than use the ndiswrapper commandline. I have blacklisted the driver by editing my black list manually but am getting zero joy trying to run the command line to install the driver.I have done some googling and the version of ndiswrapper with Ubtuntu 6.10 is out of date.But it did work last time for me when i first built this box.But since im having no joy and have downloaded the current version form sourceforge but am having no joy trying to install the goddam thing from the command window. 

So all in all a very unhappy Linux noob who may go back to good ol Windows unless someone can give me some step by step idiot guides on how to install a goddam driver and 1 application!!?!??! I mean why doesnt Linux use .exe`s? Surely that would be easier...?

---

### Post by nachotronics on 2007-03-13
For Beryl follow [URL="http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL"][B][U]this howto
[/U][/B][/URL]
For ndiswrapper follow [**_this howto_**]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

Hope this helps

---

### Post by scurlaruntings on 2007-03-13
I followed the wiki page thats the link i already posted. But when i add the URL to my repository i get the error noted in my previous post about the public key not being correct.When i try to enter it with the command line in my previous post again i get the wollowing error listed in my above post.

As for Ndiswrapper again i did what was listed in the page but keep getting a returned error that it cant copy the line to ndiswrapper. To be honest im close to giving up..

---

### Post by shingalated on 2007-03-13
You could try using the GUI to add the key manually (download it with your web browser instead of wget)  and then add it in the software sources GUI.  It usually works better.  If that doesn't work maybe you should wait a month until feisty comes out before you use beryl, it is much easier to set up on feisty.  as for NDIS, the gui for it is broken, it has to be configured with the command line.  It isn't hard though, I know you can do it.  Just follow the how to.  Don't give up!

---

### Post by scurlaruntings on 2007-03-13
> **shingalated said:**
> You could try using the GUI to add the key manually (download it with your web browser instead of wget)  and then add it in the software sources GUI.  It usually works better.  If that doesn't work maybe you should wait a month until feisty comes out before you use beryl, it is much easier to set up on feisty.  as for NDIS, the gui for it is broken, it has to be configured with the command line.  It isn't hard though, I know you can do it.  Just follow the how to.  Don't give up!Strangely enough when i ran that command line it dumped the public key in my home folder so i imported it with the Key ring manager manually and her presto it worked! I then added back to the repository and updated it and Beryl is running as sweet as. Made some inroads with NDIS iv managed to install the driver after realising the goddam thing was case sensitive!! What a load of rubbish. But now i cant get the card to see my network and am really stuck for idea`s as to what to do as the driver is installed the card is present and device manager recognises its presence..

---

### Post by scurlaruntings on 2007-03-13
Right the Windows guys knows more than all of you Linux genius`s! I finally managed to get it to work.Basically it would appear the version of Ndiswrapper that comes with 6.10 isnt sufficient enough to configure my card correctly so i downloaded version 1.27 from sourceforge installed it and ran ndiswrapper again and hey presto i got my card to see my VLAN!!! Iv taken the liberty of anotating it all so you Linux newbies can make this thread into a sticky!!

[B]Install ndiswrapper version 1.27 with the "make install" command after browsing to the correct directory IE cd /home/homefolder (where homefolder is replace with your name)

Browse to /etc/modprobe.d/blacklist and edit the file "blacklist" on the last line with:

#bad linux driver
blacklist bcm43xx (this is the default linux driver for linux complient hardware in this case where going to use ndiswrapper to encapusulate the windows driver in order to get your windows driver to work in a linux enviroment)

Browse to the directory where you have stored the following 2 files BCMWL5.INF & BCMWL5.SYS - both are required in order for your card to work correctly - Use the switch ndiswrapper -BCMWL5.INF to install the driver. NOTE THIS COMMAND IS CASE SENSITIVE SO WHICH EVER CASE THE DRIVER IS WRITTEN IN USE THAT BE IT CAPS OR LOWER CASE ( or the command will return an error with invalid driver ) 
Then run the switch ndiswrapper -l which will say hardware present (providing the card is inserted) and driver present (once it has been installed correctly) 

run switch modprobe ndiswrapper. if no error is returned then the card has been installed and configured correctly.

Now go into network tools and configure the parameters of the card IE the SSID Encryption and Ip address be it dynamic or static.
[/B]

---

### Post by nachotronics on 2007-03-15
I'm glad it worked, also if you read carefully in every ndiswrapper howto one of the first steps is to remove previously installed version and install the latest, reading may make things easier for you.

---

### Post by scurlaruntings on 2007-03-15
How can you read it when the version of Ndis packaged with 6.10 is already out of date and in the repository????

---

### Post by falsenames on 2007-03-15
Nachotronics said that the how-tos had that recommendation.  In the link posted above as an Ndiswrapper how-to, one section says this:
> Upgrading

It is always a good idea to uninstall the current version and reinstall the new version. This way, if there are changes in formats of configuration files, etc., the new version will work without problems. 

---

### Post by shingalated on 2007-03-15
I'm glad everything worked out, as you will find out most commands in unix/linux ARE case sensitive.
Good luck! :)

---

