---
title: "problem with minecraft and another games"
date: 2012-04-25
forum: Gaming &amp; Leisure
---

### Post by hemoeshock on 2012-04-25
games stop working in my ubuntu lap i was searching for solve for the lag in minecraft and i did some changes using termial after that minecraft stop working( after i log in the blank screen appear). i tried also openarena it also stop working and window appear (video setting error or something like this)
plz help me ](*,)

---

### Post by xtjacob on 2012-04-25
Need more information, what changes did you make?

---

### Post by hemoeshock on 2012-04-25
i am not sure what changes i did because i was just read alot of post and web pages about mincraft problems and copy past to terminal

---

### Post by xtjacob on 2012-04-25
Okay, there is a way to see what commands you have run. Open the terminal and press the up key until you see the ones you ran, then post them here.

---

### Post by hemoeshock on 2012-04-25
this is the commands i used :
1-sudo apt-get install sun-java6-jreD
2-sudo update-alternatives --config java
3-sudo apt-get remove gweled pyscrabble
4-sudo apt-get install gweled pyscrabble
5-sudo apt-get remove xserver-xorg-video-intel
6-sudo apt-get install xserver-xorg-video-intel
7-set r_allowSoftwareGL 1 +set r_mode 0 +set r_lodbias 4
 8-set r_textureMode GL_NEAREST_MIPMAP_NEAREST +set r_picmip 2 +set r_vertexLight 1
9-sudo crontab -e
10-sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner" && sudo apt-get update
11-java -jar ~/.minecraft/minecraft_name.jar
12-dpkg -x liblwjgl-java-jni_2.4.2+dfsg-3_i386.deb /tmp/lwjgl
13-sudo dpkg-reconfigure xserver-xorg
14-cd ~/Desktop
15-sudo dpkg -i xorg-edit*.deb
16-sudo service gdm start
17-sudo dpkg-reconfigure xserver-xorg
18-hemoeshock@ubuntu:~$
19-sudo dpkg-reconfigure xserver-xorg
20-gksudo gedit /etc/X11/xorg.conf
21-sudo wget [http://launchpadlibrarian.net/26193373/fixmtrr.sh](http://launchpadlibrarian.net/26193373/fixmtrr.sh) -O /usr/local/bin/fixmtrr.sh
22-sudo chmod +x /usr/local/bin/fixmtrr.sh
23-sudo ln -s /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default
24-gksudo gedit /etc/apt/sources.list
25-sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
26-sudo apt-get update
27-sudo apt-get dist-upgrade
28-sudo apt-get install alien

---

### Post by corrytonapple on 2012-04-25
Number 20:  What did you edit there?

What are your issues with Minecraft?  Crashes, Lag, what?

---

### Post by hemoeshock on 2012-04-25
> **corrytonapple said:**
> Number 20:  What did you edit there?

What are your issues with Minecraft?  Crashes, Lag, what?

when i write it in terminal the text editor open but i didn't edit anything there just quit

there was some lagging and after i used the commands in terminal minecraft stop working and after i log in blank screen appear

---

### Post by regor210 on 2012-04-26
lets look at your 3D drivers.

Try these

# update
$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mesa-utils

# video driver 3D test FPS
$ glxgears

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.

---

### Post by hemoeshock on 2012-04-26
for # video driver 3D test FPS
$ glxgears :
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

for #video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA:

Device:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	Mobile GM965/GL960 Integrated Graphics Controller (primary)
SVendor:	Acer Incorporated [ALI]
SDevice:	Device 011d
Rev:	03
Driver:	i915
Module:	intelfb
Module:	i915

---

### Post by regor210 on 2012-04-26
Most Intel chipset video drivers are supported automatically on the Kernel, so you may not have to install any 3rd party drivers for your video card. But if the Intel Graphics on your system don&#8217;t seem to be working correctly, you can try installing the latest drivers for your Intel Graphics.

ubuntu-x-swat
ubuntu-x-swat is more stable than xorg-edgers

[https://launchpad.net/~intel-gfx-testing/+archive/ppa](https://launchpad.net/~intel-gfx-testing/+archive/ppa)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)


$ sudo apt-get update
$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade

If this driver doesn&#8217;t help there is another unstable driver you can try, xorg-edgers.

xorg-edgers
xorg-edgers is for testing and can be unstable 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

you will have to get the full ppa name from the web page as it seens to make a happy face. LOL!

$ sudo apt-get update
$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo apt-get update
$ sudo apt-get upgrade

If you try a ppa and find you don't need it, you can purge it.

$ sudo apt-get install ppa-purge
$ sudo ppa-purge ppa:xorg-edgers/ppa
$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates

And theres a property driver I've never tried my self.
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=3319&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=3319&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A)

---

### Post by hemoeshock on 2012-04-26
still not working and about the last link "http://downloadcenter.intel.com/Deta...=%0ADrivers%0A"
i open the link and then go to "http://intellinuxgraphics.org/" but still don't know how to download

---

### Post by regor210 on 2012-04-26
It looks to me like 
$ sudo dpkg-reconfigure xserver-xorg

probley muck up xorg.conf and other things.
try this

$ sudo apt-get install ppa-purge
$ sudo ppa-purge ppaorg-edgers/ppa
$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates
$ sudo apt-get update

Then try reinstalling xserver

$ sudo apt-get remove --purge xserver-xorg
$ sudo apt-get install xserver-xorg
$ sudo dpkg-reconfigure xserver-xorg
$ sudo reboot

If still no luck you could try doing it the long way.
Note. This is last gasp before reinstalling. Best to back up your hard drive before trying this.  

Try to completely remove your intel drivers from your system:

$ sudo apt-get purge intel*

# Remove your xorg.conf

$ sudo rm /etc/X11/xorg.conf

# Reinstall xorg completely

$ sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64

# Re-configure Xorg

$ sudo dpkg-reconfigure xserver-xorg

# Reboot

$ sudo reboot

# You should be greeted with lightdm, this will default everything x the same way a fresh install would.

After this you can try installing the drivers again using the 'Additional Drivers' tool in Ubuntu but if those drivers don't work you can test the latest drivers from the x-swat ppa

$ sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
$ sudo apt-get update
$ sudo apt-get upgrade

---

### Post by hemoeshock on 2012-04-26
the command $ sudo apt-get update not work and this what appear 

""E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list""

also u can see an error icon above the screen near to dropbox icon
it also give me window with same msg  

""E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list""

---

### Post by hemoeshock on 2012-04-26
also still the problem with games

---

### Post by regor210 on 2012-04-26
To fix it

$ sudo apt-get install synaptic
$ sudo synaptic

goto

 Settings > Repositories  > Other software 

and uncheck the 2 lines with x-swat in them. close synaptic.

$ sudo apt-get update

$ sudo apt-get install ppa-purge

$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates

I&#8217;m using  xorg-edgers my self on my Intel PC's.
There the most up to date open source intel drivers you can find but they are so new that they may be unstable.

Seeing how your drivers were working I don't think the property drivers would do you much good. I would only recomend the property drivers to someone with crazy new hardware that wasn&#8217;t yet supported by the open source intel drivers. 

Xsever is a monster pile of code. Its likely that there is an error some place but finding it will more than likely take more time than a reinstall.  That or your having some kind of hardware failure. but I would try  xorg-edgers first.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

$ sudo apt-get update
$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo apt-get update
$ sudo apt-get upgrade

---

### Post by hemoeshock on 2012-04-26
after $sudo synaptic

---

### Post by hemoeshock on 2012-04-26
also when open update manager

---

### Post by regor210 on 2012-04-26
Try starting here.

$ sudo apt-get install ppa-purge

$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates

---

### Post by hemoeshock on 2012-04-26
terminal

---

### Post by regor210 on 2012-04-26
open your packing list and very carefully place a # in front of the lines with &#65279;x-swat in them.

gksudo gedit /etc/apt/sources.list

then save and start back at 

$ sudo apt-get update

$ sudo apt-get install ppa-purge

$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates

---

### Post by hemoeshock on 2012-04-26
you mean the last two lines there are already # before them 

BTW i remember that they were not there in source file but i am add it :)

is that wrong?

---

### Post by regor210 on 2012-04-26
Very odd, it seems you have both lucid and oneiric repositories enabled.

# comment out the lines with lucid in them. I count 4 lines that need to be #   

&#65279;$ gksudo gedit /etc/apt/sources.list

save 

$ sudo apt-get update

---

### Post by regor210 on 2012-04-26
Just a note. &#65279;The x-swat repositories were not working because they were for jaunty, there not compatible with oneiric.

---

### Post by hemoeshock on 2012-04-26
terminal and source list

---

### Post by hemoeshock on 2012-04-26
and this is the file it continue tell that there is error in line 3 in it
should i delete the word inline 3 ?

---

### Post by regor210 on 2012-04-26
No, theres a new relationship between sources.list.d and the sources.list sometimes things get stuck on a distribution grade.

ok looks like we need to move some files

$ gksudo nautilus

navigate to 

/etc/apt/sources.list.d

right click and create new > folder 

place the files with swat-x in them into the new folder

close out and try

$ sudo apt-get update

---

### Post by hemoeshock on 2012-04-26
ok now it work in update

---

### Post by hemoeshock on 2012-04-26
it end now

i will reboot and see if it work

---

### Post by regor210 on 2012-04-26
looks like its not liking the WE folder.  You should use 

&#65279;$ gksudo nautilus

navigate to 

/etc/apt/sources.list.d

And move it to your home folder.

then try to upgrade
$ sudo apt-get update
$ sudo apt-get upgrade

Then check to see if your game are working

---

### Post by hemoeshock on 2012-04-26
ok now update work :)

i have two update i will make it then make upgrade for the system

---

### Post by hemoeshock on 2012-04-26
ok i do what u told me in the last post and still games not work and this is photo for terminal

---

### Post by regor210 on 2012-04-26
ok I think edgers is the way to go. its what I use.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

$ sudo apt-get update
$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo apt-get update
$ sudo apt-get upgrade

$ glxgears

---

### Post by hemoeshock on 2012-04-26
upgrade the system will take 4h X_X after that i will i try if games work or no if not work i will try ur last post 

thank you for help

---

### Post by hemoeshock on 2012-04-26
OMG it will take 8h X_X

---

### Post by regor210 on 2012-04-26
With today being the release date of Precise Pangolin its bound to take longer to get a distribution upgrade. But the good news is with every new release things just keep getting better. You will be getting newer video drivers as well.

---

### Post by hemoeshock on 2012-04-27
also after the upgrade is complete, games notwork :(

i don't know what's wrong with graphic and video setting

---

### Post by regor210 on 2012-04-27
Have there been any changes to your BIOS?
Get into your BIOS and check and make sure your Intel video adapter has the maximum amount of shared ram aloud. 16 megs seems to be the cut off any less and its likely you wont have 3D rendering.

Next I would check to see if you just need a fresh installation of Ubuntu.

It looks like you went from Jaunty, Lucid, Organic, Precise and where the upgrade processes works well its not yet flawless.

I think you should boot from a live flash drive or cd into  Precise
and run this to see if you have 3D rendering.

$ sudo apt-get install mesa-utils

$ glxgears

If yes its likely you have a bad install of Unbuntu.

The fastest way to get Ubuntu 12.04 LTS (Precise Pangolin) iso
would be a torrent
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

I find unetbootin to be more reliable than the startup disk creator that comes with Ubuntu by default.

$ sudo apt-get install unetbootin

$ /usr/bin/unetbootin

After you have the live USB its likely you will need to get into your BIOS and set your Boot priority to boot from a usb drive first.

---

### Post by hemoeshock on 2012-04-27
this is the bios photos

---

### Post by regor210 on 2012-04-27
Your showing &#8220;Video memory 8MB"
Thats not good! Use the arrow key to highlight that line and bump it up as high as it will go.
Then save changes when logging out of the BIOS.

---

### Post by hemoeshock on 2012-04-27
i can't edit the video memory. 

and what about unetbootin

what should i use in it

---

### Post by regor210 on 2012-04-27
In your BIOS, you used the arrow key to highlight  Video Memory [8MB]

You may need to press Enter.

Then press the F6 key to increase the amount of  Video Memory as high it will go.

If the F6 key doesn&#8217;t increase it try the F5 key.

Then press the F10 key to save and exit.
  
I say this because I dont think you can get 3D drivers working on 8MB of ram.
 
With netbootin you click on the .... box and navigate to Downloads  and click on the iso but if you can&#8217;t get more than 8MB of ram there may be no reason to reinstall.

And with more video ram your system may work good now.

---

### Post by hemoeshock on 2012-04-27
i try but i can't change the value of video memory :(
i now use unetbootin

---

### Post by hemoeshock on 2012-04-27
They were work good. What should i do next ?

---

### Post by regor210 on 2012-04-27
8MB of video ram is extremely little by todays standards. With a laptop computer you are stuck with the hardware it comes with. On a desktop computer if you need more video ram most of the time you can upgrade if needed. With 8MB of video ram you will be lucky if you can play the most basic games like &#65279;Tux Racer. Its likely you have the best video GNU/Linux Ubuntu can offer right now.

---

### Post by hemoeshock on 2012-04-27
ok thank you

---

