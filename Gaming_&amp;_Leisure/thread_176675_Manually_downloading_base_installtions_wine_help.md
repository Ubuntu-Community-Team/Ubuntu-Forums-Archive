---
title: "Manually downloading base installtions wine help"
date: 2006-05-15
forum: Gaming &amp; Leisure
---

### Post by Damnation667 on 2006-05-15
Good day to all

I just joined.

I'm running Ubuntu 5.10. I followed this ([http://www.ubuntuforums.org/showthre...ght=wine+howto](http://www.ubuntuforums.org/showthre...ght=wine+howto)) tutorial. Very good how-to btw. A lack of internet at home atm forces me to go download DCOM98, IE6SP1, etc manually. 

I wanted to know where wine downloads these files to? So I can go and download these and place them in whatever folder wine would normally do.

Then I could just go through the winetools setup again after I've copied the installations to the correct folder and after it fails to download them, it wil start to run the installation.

Ok, theoretically that should work. I havn't been using Linux that long.  

Regards

---

### Post by Damnation667 on 2006-05-16
Ok, if you ever wanted to install Wine and you are having problems with your wireless and you're internet is down here's what worked for me.

Depending on where you installed winetools, if you have a active internet connection the files would be downloaded in /winetools/sys.

When you start winetools from your terminal, you can see everything it does in the terminal. After you set up your fake windows drive, etc, you begin by installing DCOM98. When you click to install a Downloading window pops up and you can see the link in the terminal. Copy that link to a text file somewhere, keeping the capitals and non capital letters exactly the way it is. Linux is case sensitive, correct me if I'm wrong. Next, close the Downloading window and you can see in your terminal that it failed, blah, blah. So, now you have the links to all the files you need. Go and download them. You can do this with all the downloads (MDAC, Common Controls, etc) except Internet Explorer 6 SP1. 

Firstly download the IE6SP1 installer here: [http://download.microsoft.com/downlo...s/ie6setup.exe](http://download.microsoft.com/downlo...s/ie6setup.exe)

Next, go to your start menu and run the following command (I did all of this in Windows): "C:\Downloads\ie6setup.exe" /c:"ie6wzd.exe /d /s:""#E"

Including the quotation marks. Just change the Downloads to the directory that you downloaded the install file. Just follow the instructions and choose to download the Windows 98 files. When you have done all the downloads, go back to Linux.

Now, you have to go through the Winetools installation again (not the fake windows drive, etc, just the install of DCOM98, etc.) So, when you click for example to install DCOM98, the Downloading window appears again. Then just go and copy that windows installation file to /winetools/sys. The Downloading window will go away and in your terminal you can see that winetools starts the installation of DCOM98. Follow the instructions and repeat with all the installs.

That should be it.

Regards

---

