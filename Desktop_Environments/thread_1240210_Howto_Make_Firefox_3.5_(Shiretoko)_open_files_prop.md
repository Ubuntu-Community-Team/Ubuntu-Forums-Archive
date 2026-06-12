---
title: "Howto: Make Firefox 3.5 (Shiretoko) open files properly and support apturl in Jaunty"
date: 2009-08-14
forum: Desktop Environments
---

### Post by SoftwareExplorer on 2009-08-14
[SIZE=3]Why[/SIZE]
If you've installed firefox 3.5 (called shiretoko) from the repositories, you probably know by now that it doesn't know what program to open files with on ubuntu and also doesn't support apturl. This can be quite annoying, because every file you download and open, you have to go and find the right program deep in Ubuntu's program folders to open it with.
[SIZE="3"]Step one[/SIZE]
Go to System->Administration->Synaptic Package Manager.
[SIZE="3"]Step 2[/SIZE]
Put 'firefox-3.5-gnome-support' in the search box.
[SIZE="3"]Step 3[/SIZE]
In the list of results click the box next to 'firefox-3.5-gnome-support' and on the menu that comes up, hit Mark for installation. In the box that comes up, it will tell you what other packages have to be installed to install this package. Hit mark.
[SIZE="3"]Step 4[/SIZE]
Hit Apply, and then Apply again in the box that comes up.
When it's done, you can close all the windows we opened, and restart firefox to instate the changes we made.

Edit:skecher1827 has also suggested a solution in [COLOR="Blue"][post 9]("http://ubuntuforums.org/showthread.php?t=1240210#9")[/COLOR].

---

### Post by NTolerance on 2009-08-22
Thanks for this guide.  The whole Shiretoko thing in Jaunty is a real mess.  I've been battling this problem since the release of Firefox 3.5.  I had tried this same fix a few weeks ago using a newer version of ubufox from a PPA but it didn't work for me.  

This one doesn't work either unfortunately.  Example:

Save [this](http://www.teamfortress.com/images/posts/_08_21_09/kingofthehill_1600x1200.png) PNG image link.  On my system with the version of ubufox you posted, the downloads window comes up with a dialog that asks me if I'd like to open it with GDebi, File-Roller, or choose an application.  I'd like to think that it would just open with Eye of Gnome, but it doesn't.

Anyways, so I go to the "choose application" dialog and put in "/usr/bin/eog".  And this opens the PNG file in Eye of Gnome as desired.

Then I go to Edit->Preferences->Applications.  I would expect my new settings for the PNG filetype to be listed, but they're not.  So next I try to open a .deb file within Shiretoko.  The deb file opens in Eye of Gnome!  What is going on here?

](*,)

---

### Post by SoftwareExplorer on 2009-08-23
I'm not really sure, but it did work for me for awhile and then I started having your problem. So, if anyone knows how to fix it, I would be interested.

---

### Post by seeclark on 2009-08-28
I'm having this issue with Shiretoko. It won't recognize .php files, and when I assign them to Firefox-3.5 it starts opening new tabs like crazy.

I downloaded the ubufox package using the method posted above, but there is no improvement.

Everything was fine when I was using 2.6.28-14, but not after I wiped my drive and reinstalled everything with the 2.6.28-15 kernel.

---

### Post by SoftwareExplorer on 2009-08-29
seeclark, how did you get the .php files? If you got them by opening a webpage link, it should show up as a normal web page in firefox. For example, this page ends is .php, but it is seen as a web page. If you wrote them yourself, you need to set up a web server to see them. Second, welcome to the forums. :)

---

### Post by seeclark on 2009-08-29
> **SoftwareExplorer said:**
> seeclark, how did you get the .php files? If you got them by opening a webpage link, it should show up as a normal web page in firefox. For example, this page ends is .php, but it is seen as a web page. If you wrote them yourself, you need to set up a web server to see them. Second, welcome to the forums. :)

Thanks for the reply! I'm making an effort to use Ubuntu for web development.

I am installing Drupal, so I point my browser to localhost/drupal/install.php, and I get the prompt to open/save.

This happens with Shiretoko and Firefox 3.0.

My LAMP installation is up, and I was able to install Drupal before updating to the -15 kernel. 

I haven't noticed any other issues with Shiretoko.

---

### Post by DJejel on 2009-09-05
[SIZE=3]Hi, I know how to fix this problem ! Just install this package : forefox-3.5-gnome-support and it's work ! :)
[/SIZE]

---

### Post by SoftwareExplorer on 2009-09-06
> **DJejel said:**
> [SIZE=3]Hi, I know how to fix this problem ! Just install this package : forefox-3.5-gnome-support and it's work ! :)
[/SIZE]

Thanks and welcome to the forums! :P I'll have to try it on a fresh install, but you just might have figured out a simpler way to do it. =D>

---

### Post by skecher1827 on 2009-09-07
I had a similar problem and after researching for the answer, the best approach to fix it was to update Firefox which links Shiretoko and Firefox together as just Firefox...

If you're viewing this with Firefox copy all of this and paste it in an empty file FIRST!!! Since you're going to remove it!
Go to desktop, right click, create document, empty file, open the file, right click paste, then save.

First, download the appropriate version for your system from [http://www.getfirefox.com](http://www.getfirefox.com). 
The site should detect your system specs appropriately and provide the right file. 
Save it to your desktop. Do not extract it, do not rename it, Just save it to your desktop.

Now we need to make sure you don't have other versions installed floating around.

Run the following command in Terminal to remove Shiretoko. It might not be installed, but it won't hurt to do this:

sudo apt-get remove firefox-3.5

Now remove any remaining manual Firefox installation:

sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox

Now go to "System >> Administration >> Software Sources" and remove any PPA repository for Firefox that you see in there, if any.

Then delete any firefox-3.5****.tar.bz2 you have downloaded from Mozilla and saved in your home, no matter if it's source code or not.

Now install Firefox 3.5.

Move the desktop firefox file you downloaded to your Home Folder, click Places, Home Folder

Do not extract it, do not rename it, do not put it inside any sub-folder of home. Just move the saved file to your home directory.

Then run these commands, in Terminal one by one:

sudo tar -jxvf firefox-3.5.2.tar.bz2 -C /opt

rm firefox-*.tar.bz2

sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup

sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

Now firefox3.5 will be installed and the confusing Shiretoko one will be gone!

If you decide to revert to Firefox 3.0.11 for some reason, just run this code:

sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox

This is what worked for me!

---

### Post by MountainX on 2009-09-07
I simply installed Swiftweasel and it worked. And it runs faster.

---

### Post by SoftwareExplorer on 2009-09-07
> **DJejel said:**
> [SIZE=3]Hi, I know how to fix this problem ! Just install this package : forefox-3.5-gnome-support and it works ! :)
[/SIZE]
Thanks again, I tried it on a fresh install and it did seem to re-enable apturl, and when I tried a few different file downloads it also seemed to work.

---

### Post by SoftwareExplorer on 2009-09-07
> **skecher1827 said:**
> I had a similar problem and after researching for the answer, the best approach to fix it was to update Firefox which links Shiretoko and Firefox together as just Firefox...

If you're viewing this with Firefox copy all of this and paste it in an empty file FIRST!!! Since you're going to remove it!
Go to desktop, right click, create document, empty file, open the file, right click paste, then save.

First, download the appropriate version for your system from [http://www.getfirefox.com](http://www.getfirefox.com). 
The site should detect your system specs appropriately and provide the right file. 
Save it to your desktop. Do not extract it, do not rename it, Just save it to your desktop.

Now we need to make sure you don't have other versions installed floating around.

Run the following command in Terminal to remove Shiretoko. It might not be installed, but it won't hurt to do this:

sudo apt-get remove firefox-3.5

Now remove any remaining manual Firefox installation:

sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox

Now go to "System >> Administration >> Software Sources" and remove any PPA repository for Firefox that you see in there, if any.

Then delete any firefox-3.5****.tar.bz2 you have downloaded from Mozilla and saved in your home, no matter if it's source code or not.

Now install Firefox 3.5.

Move the desktop firefox file you downloaded to your Home Folder, click Places, Home Folder

Do not extract it, do not rename it, do not put it inside any sub-folder of home. Just move the saved file to your home directory.

Then run these commands, in Terminal one by one:

sudo tar -jxvf firefox-3.5.2.tar.bz2 -C /opt

rm firefox-*.tar.bz2

sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup

sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

Now firefox3.5 will be installed and the confusing Shiretoko one will be gone!

If you decide to revert to Firefox 3.0.11 for some reason, just run this code:

sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox

This is what worked for me!
Thanks! I seem to get more help with this by telling how I got it to work for awhile, than if I had asked for help. (Or maybe that's just what I think, since I'm not waiting for it to work!)

Also, welcome to the ubuntu forums.  :P

---

### Post by SoftwareExplorer on 2009-09-07
> **MountainX said:**
> I simply installed Swiftweasel and it worked. And it runs faster.
Isn't it basically the same thing as Firefox, just with debian's name?

---

### Post by usererror on 2010-01-01
for me the fix was when firefox asked "What do you want to do with this file?" I clicked Choose Application then pointed it to /usr/bin/apturl-gtk and that was all I had to do.

I already had firefox-3.5-gnome-support installed, but it didnt know what to do with apturl's even after my fresh install of 9.10 i just did.

Also just found this:

From: [http://blog.appnr.com/help/](http://blog.appnr.com/help/)

Type in &#8220;about:config&#8221; in the location bar.

Right click, select New &#8211;> String
Type in &#8220;network.protocol-handler.app.apt&#8221; in the name of string,
and type in &#8220;/usr/bin/apturl&#8221; in the value.

One more right click, select New &#8211;> String
Type in &#8220;network.protocol-handler.app.apt+http&#8221; in the name of string,
and type in &#8220;/usr/bin/apturl&#8221; in the value.

---

