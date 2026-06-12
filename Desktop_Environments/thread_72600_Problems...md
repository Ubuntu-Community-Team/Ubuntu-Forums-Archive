---
title: "Problems.."
date: 2005-10-06
forum: Desktop Environments
---

### Post by abominable on 2005-10-06
Well I am a newbe and I face a lot of problems. If anone knows, please help..

1) Unfortunately, I cannot connect to the Internet through Linux. So I have set a Lan between Widows and Linux.. It seems to be working, but I can't share the Internet conection.. When I had ubuntu it was working on its own. 

2) I was pressing alt+F2 in order to open files, and amarok to listen to the music. For some reason when I pressed alt+f2 to open /media/* it opened amarok.. so did happen when I tried to open any file.. Moreover amarok stopped playing music.. I uninstalled amarok and now I can open no file!!

Any ideas??

---

### Post by mlomker on 2005-10-06
> Unfortunately, I cannot connect to the Internet through Linux. 

Have you gone into Control Center, Internet & Networking, Proxy to set up your proxy server information?

> I was pressing alt+F2 in order to open files, and amarok to listen to the music.

On my machine pressing alt+F2 just brings up the 'run command' line, same as you'd get if you picked that option off of the K menu.  I might be misunderstanding you, though, because I use the mouse for almost everything.

---

### Post by Tilex on 2005-10-07
> Unfortunately, I cannot connect to the Internet through Linux.

Do you have DSL or Cable? (PPPoE or not)

>  I was pressing alt+F2 in order to open files, and amarok to listen to the music.

As mlomker said, you can choose the keyboard shortcuts that you prefer when you right-click on a program in your KDE menu.  You choose "edit this entry" and you add a shortcut for this specific program.

---

### Post by abominable on 2005-10-07
I have 56k :( :( ..

Alt F2 brings up the run command. There I insert /media/* or / , in order to open the specified file, but instead of openning a window with that address, it was openning amaroK. Now that I have removed amaroK I cant open files through the run command.


About the proxy server, I have 2 pcs. (first) 192.168.1.1 (second) 192.168.1.2 . The first one connects directly to the internet. The second one connects to the internet through the first one. As the proxy server I should use the first?

---

### Post by mlomker on 2005-10-07
> About the proxy server, I have 2 pcs. (first) 192.168.1.1 (second) 192.168.1.2 . The first one connects directly to the internet. The second one connects to the internet through the first one. As the proxy server I should use the first?

Yes.  You have installed some kind of proxy server/Internet connection sharing software on the first machine?

If you remove amaroK then it isn't going to be associated with your multimedia files anymore.  You could open up Konqueror and browse to the file that you want--right clicking on the file will present you with some options on what program to open it in.

File associations are in the Control Center under KDE Components, File Associations.  You'll want to expand the inode 'tree' and then look at the 'directory' association.  The default is to have Konqueror listed first and amaroK second under *Application Preference Order.*

---

### Post by abominable on 2005-10-08
[QUOTE=mlomker]Yes.  You have installed some kind of proxy server/Internet connection sharing software on the first machine?
[/QUOTE]

No, should I?? The previous time, I had ubuntu, I hadn't installed any software, but I could connect to the Internet through windows.

[QUOTE=mlomker]File associations are in the Control Center under KDE Components, File Associations.  You'll want to expand the inode 'tree' and then look at the 'directory' association.  The default is to have Konqueror listed first and amaroK second under *Application Preference Order.*[/QUOTE]

Thanks I fixed it..

---

### Post by mlomker on 2005-10-08
[QUOTE=abominable]No, should I?? The previous time, I had ubuntu, I hadn't installed any software, but I could connect to the Internet through windows.
[/QUOTE]

You had Ubuntu on the machine directly connected to the Internet?  Strange if that's true, because normally you have to install and configure **firestarter** for that to work.  I'm in a couple [other threads]("http://www.ubuntuforums.org/showthread.php?t=72926") with people that are setting that up.

If Windows is on the Internet machine (and it is using Windows XP's internet connection sharing) then you'd just have to configure proxy entries on the other box.  Here's [a thread]("http://www.ubuntuforums.org/showthread.php?t=72076") about that.

---

### Post by abominable on 2005-10-08
I set it by accident. Here is my solution..

I went to the kcontrol
Internet&networking->Network settings->Network Interfaces:
Set eth0, configure Interface-> Automatic (dhcp)   Enable Interface.

Routes:Default Gateway 192.168.0.1 (IP Address of windows box) dev: eth0.

In proxy settings

->Automatically detect proxy configuration.


Thanx a lot for your help.

---

