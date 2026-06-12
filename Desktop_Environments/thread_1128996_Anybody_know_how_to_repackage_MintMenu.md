---
title: "Anybody know how to repackage MintMenu?"
date: 2009-04-18
forum: Desktop Environments
---

### Post by har02052 on 2009-04-18
I am new to linux and Ubuntu.  I tried out LinuxMint and I liked it ok, but I decided to stick with Ubuntu except that I love the LinuxMint MintMenu.  I know that I can install it on Ubuntu, which I did, but I don't like that it is "Mint flavored" ie contains MintUpdate, MintInstall, and you have to install MintDesktop, MintUpdate, and MintInstall as dependencies.  Post install I was able to change the icon to a standard Gnome icon and changed the MintUpdate and MintInstall shortcuts so that they are now Ubuntu update and Synaptic by manually editing the system_management.py file. (I don't know programing languages, I found someone else that had done it for Fedora and followed their instructions but tweaked them for Ubuntu.)  Anyway, how can the program be repacked into a deb file so that it can be installed without the mint dependencies and mint flavor?  I just thought others might like to have the menu but Ubuntu flavored.

---

### Post by hesjnet on 2009-04-18
What is it you actually want? A menu like the one in linux mint without having to install the menu from linux  mint?

Is it some functionality you are missing or is it because of the apperance. If it is the last, try to look within [gnome-look.org]("www.gnome-look.org")

Maybe this?
[Carbon theme]("http://gnome-look.org/content/show.php/Carbon+theme+for+GnoMenu?content=93299")

[Where Can I Get The Linux Mint Menu?]("http://ubuntuforums.org/showthread.php?t=621000")(ubuntuforums.org)

---

### Post by har02052 on 2009-04-19
I did install the Mintmenu from linuxmint.  I do really like it.  I like both how it looks and how it functions.  I have tried the Gnomenu but I don't like it that much.  It is made to be like the Vista start menu and I don't like the vista menu at all.  What I want is a stand alone menu similar to the mintmenu but one that doesn't also require the dependencies that mintmenu does.  It requires that you also install mintinstall, mintupdate, mintsystem among other things.  There was someone else that repackaged mintmenu as a deb file that didn't have those dependencies, but that was when it was version 3.0 it is now 4.3.  I was just wondering how it can be done.  I am betting that there are others that would like to have it for Ubuntu.

---

### Post by har02052 on 2009-04-20
Little help?

---

### Post by har02052 on 2009-04-21
So I did it myself.  After some searching I found someone else that had created a deb with version 3.0 but there was some lost functionality to it.  After much more searching, I found someone that had installed it on PCLinuxOS.  They kind of showed the steps how they did it with modifications for PCLinux.  So I took those and backwards enginered some of it to work with Ubuntu.  Now I have a working MintMenu with no dependencies and it hasn’t altered my system to think that I am running linux mint.  There is no deb file (I don't know how to make one) and I am sure there could be mistakes in what I did because I really don't know how to code.  But it works for me.  This is what I did, at the bottom of the post is a tar file that you won't have to go through all of the steps, you just have to copy the contents of the tar file in the /usr folder into your /usr folder and that's it.  But here are the steps anyway.
Here is what you do:

Download the source for the menu from here:
[http://packages.linuxmint.com/pool/main/m/mintmenu/](http://packages.linuxmint.com/pool/main/m/mintmenu/)

If you want the right-click uninstall to work, download the MintSystem source from here:
[http://packages.linuxmint.com/pool/main/m/mintsystem/](http://packages.linuxmint.com/pool/main/m/mintsystem/)

unpack both of them somewhere like your desktop.
Copy all the files and folders within:
(unpacked mintsystem folder here)/usr/lib/linuxmint/

And paste them into
(unpacked mintmenu folder here)/usr/lib/linuxmint/

Now, copy all of the files and folders within:
(unpacked minmenu folder here)/usr/

And sudo or root paste them into your /usr/ folder.

On one of the gnome menu bars right-click and select add applet to this panel.  Scroll down and there will be MintMenu.  Go ahead and add it.

Next, in the System menu there is a LinuxMint icon that says Software Manger (or it might say MintInstall) but it doesn’t work because you didn't also install mintinstall, you have to change that to whatever you want.  I changed it to the update manager.  You do that by manually editing the file to point to something else.
So:
sudo gedit /usr/lib/linuxmint/mintmenu/plugins/system_management.py

Scroll down to line 100.  There you will see:

Button1 = easyButton( "/usr/lib/linuxmint/mintSystem/icon.png", self.iconsize, [_("Software manager")], -1, -1 )

Button1.connect( "clicked", self.ButtonClicked, "/usr/lib/linuxmint/mintInstall/frontend.py" )

Button1.show()

self.systemBtnHolder.pack_start( Button1, False, False )
s
elf.mintMenuWin.setTooltip( Button1, _("Browse and install available software") )		

As you can see, it points to mintinstall.  You can now change it to whatever you want.  I changed it to the system update manager by editing it to this:

Button1 = easyButton( "update-manager", self.iconsize, [_("Software Update")], -1,-1
Button1.connect( "clicked", self.ButtonClicked, "update-manager" )

Button1.show()

self.systemBtnHolder.pack_start( Button1, False, False )

self.mintMenuWin.setTooltip( Button1, _("Update Your Software") )


You could change it to whatever you want, that is just what I did.
Last of all you can change the icon for both the menu button and then the “All” in the applications list.  The main menu icon is easy to change, just right-click on it and click preferences and on the main button tab, you can change the icon and the title.

The All aplications icon is a little harder, but simple enough.  The icon is found within:
/usr/lib/linuxmint/mintsystem

sudo replace that icon with an icon of your liking, making sure that the one you put in there has the same name as the one that  you replaced.

That's it. You now have a working MintMenu without all of the other stuff that would go with it if you had installed it from the mint repos.  I will try to upload a modified tar file with the mintsystem folder, modified system_management file, and changed icons so that all you would have to do is copy and paste them into your /usr folder to make it work.  If anybody else wants to run with this and make it a deb or a self installing script, go ahead, I don't know how.

---

### Post by Myranti on 2009-04-29
That works great :D

Just a little note when changing preferences, I was having some trouble with the preferences taking affect and found you need to right click on the Menu button and 'Reload plugins', or at least, that worked best for me.

This was one thing I didn't want to lose coming from Mint 6 to Ubuntu 9.04.

---

### Post by heffo_j on 2009-05-04
Hi there,

I really want to set my menu this way as I've just moved from Mint back to Ubuntu. 

Anyway, I've unpacked the tar files to my desktop. There are two main folders within. One is named "debian" and the other "usr". 

In your description you say to put the contents of the usr folder into the equivalent installed usr folder (and sub folders I assume) already on my system. This is what I did.

Mintmenu shows up in the "add applet" list but when I try to add it, it sends an error message.

Also, what do I do with the debian folder? I'm not sure when to put this. 

Sorry for the confusion. I'm not really sure what I am doing here. Do I need to reboot for this to take affect?

Regards
John

---

### Post by har02052 on 2009-05-07
I didn't do anything with the debian folder.  I don't think you need it.  I kept it in there in case somebody else who is smarter than me wanted to repackage it and they might need it.  Try restarting or at logging out and back in and see if the menu is there.  I did occasionally have it say there was an error, but then it went away after a restart.

---

