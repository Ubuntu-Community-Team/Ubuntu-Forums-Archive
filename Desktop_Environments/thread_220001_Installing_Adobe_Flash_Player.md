---
title: "Installing Adobe Flash Player"
date: 2006-07-20
forum: Desktop Environments
---

### Post by srunni on 2006-07-20
OK, I'm running Kubuntu 6.06 x86. I downloaded the official flash player tar.gz from the Adobe website, and followed the instructions. The two files that the readme says needs to be the in the firefox folder (i have two: usr/lib/mozilla-firefox and usr/lib/firefox, for some reason) are there. Is an incompatibility issue with Ubuntu or something?

Thanks in advance for the help!

---

### Post by catlett on 2006-07-20
Flash player is in the repositories. You don't need to compile it.
```
sudo apt-get install flashplugin-nonfree
```
```
 sudo update-flashplugin
```
If you don't have the extra repositories enable3d it will not install. This is the how to from the dapper guide.
[http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories](http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories)
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

---

### Post by srunni on 2006-07-20
I've already tried the first part in the past, the sudo apt-get flashplugin-nonfree. When I tried it this time, it said it was already installed. However, when I tried the sudo update-flashplugin, I got "installation failed". Do you have any idea what could have caused this?

EDIT: Forget about that problem, I got it fixed: I had to close Firefox. But after that, I used both commands you posted, and I still can't get Flash to work, eg. I try to play a video at YouTube, and it says that I don't have the Flash player installed.

---

### Post by catlett on 2006-07-20
Sorry to not reply. I had to go to the grocery store. (I'm my wife's honeydew, honey do this. honey do that :D )
Let's see what firefox says about your flash plug in. Open firefox. Erase the address bar. Type this in```
 about:plugins
``` Then hit go. It will take you to your firefox plugin page. Scroll down to flash and see what is listed.

---

### Post by srunni on 2006-07-21
Don't feel like you have to respond right away - take your time; you have no obligation to do any of this, though I do greatly appreciate it :). It's you and all the other helpful people at the Ubuntu Forums that make it so widely known for it's helpfulness.

Anyway, I did what you said in Firefox, and I got nothing. There was no Flash section, and I will have a screenshot up tomorrow. Anyway, I have to go to sleep now. I will talk to you in the morning.

---

### Post by srunni on 2006-07-21
Here's the screenshot:

[[IMG]http://img139.imageshack.us/img139/5968/firefoxpluginsyd9.th.jpg[/IMG]](http://img139.imageshack.us/img139/5968/firefoxpluginsyd9.jpg)

It seems that there just isn't any sign of the plugin, which is strange, because the .so and .xpt files are where they should be.

---

### Post by catlett on 2006-07-21
I think there is something wrong with your plugin location in ubuntu. When I go to the panel and select Places<Computer<Filesystem<usr<lib that is the folder firefox's folder is in. When I open the firefox folder there is a plugin folder. What is in your folder? I posted a screenshot of my plugins. As well as a shot of my about:plugin.
The 2 files you need in firefox's plugin folder are flashplayer.xpt and libflashplayer.so. Are these 2 files anywhere else on your system?

---

### Post by srunni on 2006-07-21
I can't follow your exact directions, as I'm in KDE, so instead I opened Konqueror and went to the locations where I thought the plugins should be. Here are screenshots of the two locations in which I added the two files for the plugin:

---

### Post by Palansil on 2006-07-21
I think you might have multiple copies of firefox installed.  This is what happened to me when I just tried to install it on my own machine.  The way I fixed the problem was to first find out which version of firefox is my default.  I then had to create (symbolic) links to the flash files in my default firefox directory.  After that flash worked fine.

Here's how you can try what I did.

To find out which is your default copy of firefox, open Konqueror and goto /usr/bin  right click on the 'firefox' link and notice what the link target is.  

In your terminal type ```
cd  */plugins
``` where * is your firefox directory.  For example, mine was /usr/local/firefox  Then type ```
sudo -s /usr/lib/flashplugin-nonfree/libflashplayer.so
``` Assuming that this is where your flash plugin is actually installed.  Do the same for the file called flashplayer.xpt.  This creates symbolic links to the flash plugin.  After that restart firefox and let us know if it worked.

---

### Post by catlett on 2006-07-21
I don't understand the issue your having. You have the correct plugin and it is in the correct place? It doesn't make sense. You have the plugin and it is installed to the correct folder.
Try running ```
sudo update-flashplugin
``` one more time. I'm going to hiunt around for any hint

---

### Post by srunni on 2006-07-21
OK, catlett, I tried what you said, but it didn't make any difference. I already tried this in the past, so I think that something else is the problem. Palansil, I'm about to try your suggestion, will report on if it works out.

---

### Post by srunni on 2006-07-21
OK, I finally fixed the problem! And the funny part is, I did it on accident. When I ran the "./flashplayer-installer" command, I forgot to add the "sudo" part. And as I was in a rush to get through the installation, I just went through everything fast, and accidentally installed to "home/[user]/.mozilla/plugins" ... and it worked!

@ Palansil
However, when I looked to see in "/usr/bin", there were two files, "firefox" and "firefox.ubuntu". "firefox" linked to "/opt/firefox", while "firefox.ubuntu" linked to "/usr/lib/firefox". Either way, installing to the ".mozilla" folder in the home directory obviously puts the plugin into effect system-wide on that account, regardless of whether I launch Firefox from "/usr/lib/mozilla-firefox", "usr/lib/firefox" or "opt/firefox". Anyway, I installed to "opt/firefox" anyway after that, just in case, so there shouldn't be any more problems. I guess the important thing is to "./flashplayer-installer", not "sudo ./flashplayer-installer", because that removes the problem of having to find the directory.

---

### Post by catlett on 2006-07-21
Well that was easy :D . Glad you worked it out because I sure couldn't.:p

---

### Post by srunni on 2006-07-22
Well thanks anyway. Any help is appreciated :)

---

