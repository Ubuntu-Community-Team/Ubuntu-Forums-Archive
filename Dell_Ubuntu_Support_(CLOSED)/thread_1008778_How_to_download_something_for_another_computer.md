---
title: "How to download something for another computer"
date: 2008-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xtian999 on 2008-12-11
Please tell me how to get the software required to enable an internet connection onto a computer that is not connected.

I have an old Dell Inspiron 7000 that now boots Ubuntu 8.10 from a CD. My goal is to eventually have it running exclusively on Ubuntu and connected to the web via USB or Bluetooth through my Sprint HTC 6800 Titan/Mogul.

I have the use of a Dell Inspiron 6400 that runs Win XP and connects nicely via USB or Bluetooth, so I can download anything I need with it.

My problem is that I do not know how to get it from a file on the 6400's desktop to running on the old Inspy 7K.

Actually, I don't even know how to effectively search for the answer to this question, so forgive me if this has been covered elsewhere.

Thank you in advance,
X

---

### Post by unutbu on 2008-12-11
Ignore the first paragraph; start reading at "To avoid the misery":

[http://ubuntuforums.org/showpost.php?p=5568689&postcount=3](http://ubuntuforums.org/showpost.php?p=5568689&postcount=3)

You may also find this helpful:
[http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/](http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/)

---

### Post by xtian999 on 2008-12-12
Thank you for that. I'm still fuzzy on a few things:

If Synaptic is not on the computer I use for downloading, how can it grab the files it needs? Paradoxically, loading Ubuntu onto the Windows machine to get the files kills the connection to the phone. 

So, let's say that I can get a Linux/Ubuntu file from the internet onto the desktop of my XP machine using XP, then what? Using a flash drive as the go-between, what are the specific actions necessary to accomplish this task? Do I just drag the files onto the flash drive and then pull them off with Synaptic? Do I drag them off the flash drive onto the Ubuntu desktop? Do I burn a new ISO with the new files? If so, how do I tell the XP machine to add the files in before burning?

I feel that if I can just get over this hump, then Ubuntu will be more fun.

---

### Post by unutbu on 2008-12-12
On the 7000 (running Ubuntu), go to System>Admin>Synaptic.
It doesn't matter that there is not internet connection.
Select a package that you would like to install. Click it and select "mark for installation". Mark as many packages as you like.

Then go to File>Generate package download script.

Synaptic knows which extra packages need to be installed to satisfy dependencies. This is why this is more efficient than doing it my hand.

The script is just a text file which you can save on your Desktop.

Use a USB thumb drive or other media to transfer the script over to the 6400. Open the script in a text editor and read off the packages listed there. Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) to search for and download the packages. 

For example:
[http://packages.ubuntu.com/intrepid/blender](http://packages.ubuntu.com/intrepid/blender)

Notice near the bottom there is a section called "Download blender". Select the amd64 link if you are running the 64-bit OS or the i386 link if you are running the 32-bit OS. The file you should download will have a ".deb" extension.

Save these deb files on the 6400. Use the USB drive to transfer them to the 7000. Put them in a directory all by themselves and then open a terminal (Applications>Accessories>Terminal)
and type
```

cd /path/to/deb/files
sudo dpkg -i *.deb
```

Change /path/to/deb/files to the actual path. For example, if you make a directory in your home account called Debs, then type
```

cd Debs    # To change directory
ls -l      # To list the files
sudo dpkg -i *.deb
```

---

### Post by xtian999 on 2008-12-12
Awesome answer! I will  try that with newfound confidence and report results back here.
Thank you,
Xtian

---

### Post by xtian999 on 2008-12-19
Well, I guess I don't know what "Put them in a directory all by themselves" really means because I created a folder called SVN Files on the desktop and put the files into it and now the command line will not recognize the destination when I try the cd command.

I type cd /home/ubuntu/Desktop/SVN Files and get the "File not Recognized line.

This is frustrating, to say the least. Even the tutorials are over my head. 

I can only stand about twenty minutes of this per day before I say F*#k it and walk away.

---

### Post by lifestream on 2008-12-19
> **xtian999 said:**
> 

I type cd /home/ubuntu/Desktop/SVN Files and get the "File not Recognized line.


There is a space on your folder name, so Ubuntu thinks you are telling it to go to [FONT="Courier New"]/home/ubuntu/Desktop/SVN[/FONT]  instead of [FONT="Courier New"]/home/ubuntu/Desktop/SVN Files[/FONT]
Because of that space, Ubuntu thinks [FONT="Courier New"]Files[/FONT] is a command to execute ^^:

So either rename the folder to just SVN, or do this:

cd /home/ubuntu/Desktop/SVN**\** Files

(The **\** after SVN  tells Ubuntu to treat the space as part of the folder name)

Let us know how it goes :)

---

