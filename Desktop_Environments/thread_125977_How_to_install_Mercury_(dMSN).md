---
title: "How to install Mercury (dMSN)"
date: 2006-02-05
forum: Desktop Environments
---

### Post by bartekk on 2006-02-05
Hi,

How to install Mercury (also known as dMSN) ???
I downloaded the file from [http://www.mercury.to/](http://www.mercury.to/) and I received 1709_Linux_VM.bin

The site says this on how to install the programm:

 1. Download the Setup.bin file from the download page (Make sure you have a JVM or not )
2. Start your favourite terminal
3. go to the directory you saved the Setup.bin
4. make the Setup.bin executable (chmod +x Setup.bin)
5. run: "su -" without the quotes if you want to install Mercury in a directory which needs write access
6. start the Setup.bin (./Setup.bin)
7. follow the instructions of the installer. We recommend installing Mercury in /usr/local/Mercury if you have root access, otherwise install it in /home/yourusername/mercury, in lowercase (read the explanation for this at the end of this page)


So I downloaded the file and now it's here:   /home/bb/mercury/1709_Linux_VM.bin
I start the terminal and opend the directoy /home/bb/mercury via Places on top of my desktop.
But how do I make this file executable with chmod ???
How do I start the setup.bin ????

Sorry, I'm new here :( , thx for the help

---

### Post by taurus on 2006-02-05
At the prompt from the terminal that you have open, type

chmod 755 1709_Linux_VM.bin
sudo ./1709_Linux_VM.bin

---

### Post by Brynster on 2006-02-05
There is also a .deb package available also for that you just type in the terminal window


```
 sudo dpkg -i name_of_package.deb
```

where name of package use the name of the .deb file you have downloaded. It will askfor a password also simply type in the password you use log in when you boot up.

---

### Post by bartekk on 2006-02-05
@ Taurus: When I copy and paste the first line it says :
chmod: cannot acces '1709_Linux_VM.bin': unknown file or map 

@Brynster When I typ :
sudo dpkg -i 1709_Linux_VM.bin.deb    ...  it says:
could not reach archive: Unknown file or map
Find fault during ... :
1709_Linux_VM.bin.deb
(free translation from the dutch Ubuntu 5.10 version)
:( 

Thx for the help so far guys, what can I do now ???

---

### Post by hamil on 2006-02-05
If you would like to go for the .deb pack, this is what you should do:

1. Download the *.deb pack from [Mercurys deb package]("http://surfnet.dl.sourceforge.net/sourceforge/projeto-messias/mercury-messenger_1710_S7_i386.deb")
2. Open the terminal
3. Go to the folder where you downloaded the file, in most intances, it is in your home folder or on the desktop. (cd /home/myusername/Desktop/
4. In the terminal, issue this command: sudo dpkg -i mercury-messenger_1710_S7_i386.deb
 
This should do the trick.

---

### Post by bartekk on 2006-02-05
@ Hamil,

Thx now it works fine me, I didn't now that I should typ : cd/home/ ... in the Terminal.

Stupid me, but learning every day  lol

thx for the reply

---

### Post by hamil on 2006-02-05
Glad it worked out for you! And glad I could help!

---

