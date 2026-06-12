---
title: "How to play ETQW public beta on Ubuntu 7.04"
date: 2007-06-24
forum: Gaming &amp; Leisure
---

### Post by jarhead-x on 2007-06-24
How to play ETQW public beta on Ubuntu 7.04

I'll do my best to help out some of the other Linux users who want to try out ETQW on Linux.

First, thanks to the wine developer team for promptly releasing the new version and patches that make this possible.

Insure that you are running the latest restricted NVIDIA driver in the ubuntu repos. I haven't tried the driver that was just released yesterday.

Test your OpenGL setup by running glxgears.

Uninstall the stock wine if you had previously installed it via apt-get, Add/Remove, or Synaptics Package Manager.

So that you can compile the latest version of wine, install some dependent packages:
sudo apt-get install flex
sudo apt-get install bison
sudo apt-get install fontforge
sudo apt-get install freeglut3-dev

Download wine-0.9.39.tar.bz2 from:
[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

bunzip2 wine-0.9.39.tar.bz2
tar -xvf wine-0.9.39.tar

Now you will have a directory called wine-0.9.39

You need to save two patch files in that directory. Let's call them patch1 and patch2.

To create patch1, click on this link to grab the patch code:
[http://bugs.winehq.org/attachment.cgi?id=6039&action=view](http://bugs.winehq.org/attachment.cgi?id=6039&action=view)

In firefox, just do "CTRL a" to select all of the code.

Open up gedit and paste all of that code into it.

Save this file as patch1 inside the wine-0.9.39 directory.

To create patch2, click on this link to grab the patch code:
[http://bugs.winehq.org/attachment.cgi?id=6849&action=view](http://bugs.winehq.org/attachment.cgi?id=6849&action=view)

In firefox, just do "CTRL a" to select all of the code.

Open up gedit and paste all of that code into it.

Save this file as patch2 inside the wine-0.9.39 directory.

Go into the wine-0.9.39 directory and do:
patch -p1 < patch1
patch -p1 < patch2

Now run configure:
./configure

Now compile your new version of wine:
make depend && make

Now install your new version of wine:
sudo make install

Open winecfg and set pdh, wtsapi32 to native by:
winecfg
Under the Applications tab, change Windows Version to Windows XP
Click on Libraries
Set pdh, wtsapi32 to native by:
Under New override for library: choose pdh then Add then Edit and select native.
Under New override for library: choose wtsapi32 then Add then Edit and select native.

Go to your directory where you have the downloaded ETQuakeWarsBetaSetup.exe and do:
wine ./ETQuakeWarsBetaSetup.exe Pretty much choose the defaults. Go ahead and install punkbuster when it asks. When the install is finished, you will see an error: Unable to launch C:\windows\temp\vcredist_x86.exe. That is fine...just click OK. Then it will also say that DirectX wasn't installed properly...just say OK to that too.

Download this file [http://www.sweetpotatosoftware.com/files/microsoft.vc80.crt.zip](http://www.sweetpotatosoftware.com/files/microsoft.vc80.crt.zip) uncompress it into the game's folder like /home/yourusername/.wine/drive_c/My Product Name
cd .wine/drive_c/Program Files/id Software/Enemy Territory - QUAKE Wars Beta
wget [http://www.sweetpotatosoftware.com/files/microsoft.vc80.crt.zip](http://www.sweetpotatosoftware.com/files/microsoft.vc80.crt.zip)
unzip microsoft.vc80.crt.zip
mv Microsoft.VC80.CRT/* .

Download [http://rapidshare.com/files/39051854/system32.tar.bz2.html](http://rapidshare.com/files/39051854/system32.tar.bz2.html)
Once you download the file, mv system32.tar.bz2 .wine/drive_c/windows/system32/
cd .wine/drive_c/windows/system32/
bunzip2 system32.tar.bz2
tar -xvf system32.tar

Go back to your home directory:
cd (then enter)

Run regedit to set your ScreenDepth variable:
type regedit on the command line and go to "HKCU/Software/Wine".
Add a key called X11 Driver
Inside of X11 Driver, Add a string value called "ScreenDepth" and set its value to 32.

Run ETQW:
cd .wine/drive_c/Program\ Files/id\ Software/Enemy\ Territory\ -\ QUAKE\ Wars\ Beta/
wine ./etqw.exe

The mouse will probably be a little weird...I will post a fix if I find one. It is still very playable though.
I have a Nvidia 7950GT 512M inside of a Dell E521 and a 24" Dell Widescreen Flat Panel. I have my settings at Normal, Ultra for the shaders. 16:10 aspect at 1920x1200 resolution.

I hope that the native Linux version is released and as supported at the same level as the windows version. I have been in the IT industry for 11 years, have some MS certs, and now personally refuse to run any microsoft OS due to the latest Microsoft FUD and patent threats. I have had it with their dirty ways of doing business and licensing nightmares. I am adjusting my professional career and hobbyist computing accordingly.

Thanks again goes out to the other Linux guys that helped out in the forums.

---

### Post by hawko on 2007-06-30
The mouse issues are making it unplayable for me.  Now that the new version of Wine is out, what do I need to do to remove the patched version I installed with this tutorial?

---

