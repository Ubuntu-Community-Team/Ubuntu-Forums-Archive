---
title: "Ink2Text handwriting recognition announcement"
date: 2011-04-19
forum: Desktop Environments
---

### Post by bcw on 2011-04-19
Hi,

I am releasing a new project to provide handwriting recognition service on Linux/Unix computers, named [[COLOR="Blue"]Ink2Text[/COLOR]]("https://sourceforge.net/projects/ink2text/").

This provides a shared library which can receive a stream of points representing handwriting on a tablet and returns what is written as text.

The idea is that any program can be enabled for hand-written input.

Unlike my first solution, this system does not require any copies of Windows - it only requires WINE (tested with v1.2 on Lucid 10.04 LTS) and some packages installed, and is much easier to set up.  The details are in the included file named INSTALL.

At this time, you will also need to install my [[COLOR="Blue"]Stylus/Handwriting Input Panel[/COLOR]]("https://sourceforge.net/projects/ship-project/") project, which I have upgraded to use the new recognition system.

Together this provides printed and cursive handwriting input for tablet computers.

Please try it and help me iron out any bugs in the install process. Then start bugging the Gnome & KDE people to tablet-enable their UI components.  8-)

Please use the sourceforge project forums for support questions so others may benefit from the information.

Cheers,
bcw

---

### Post by Mr.Kappa on 2011-04-19
This is great!! i can't wait to try it out!! I've been waiting a vey long time for something like your project to show up! Man you're great! :guitar:
If you want to translate the program in italian i can offer my help!

---

### Post by bcw on 2011-04-19
Hi,

Your help will be useful.

The Ink2Text server has only a few error messages, so there is no particular translation needed - the idea is you should never see any.

The Stylus/Handwriting Input Panel allows creation of keyboards with any characters Unicode fonts allow, and you may find you want to add some characters or change the layout.

But there may be another problem with the Ink2Text approach.  With my first solution, which involved a server running in an actual full copy of Windows XP Tablet, you could set the Windows environment to a language and the recognizer would switch (Italian is provided along with several others).

With the Ink2Text server running on WINE, I don't know how to set another keyboard/language - and the outupt appears to simply not know about characters outside of the default (US English).  I speak some Spanish, and I am finding '?' characters being substituted for some of the non-English alphabet characters.

If you are using your Linux desktop set to other than US English, please try and let me know if the proper characters are reported back.  This will give me some idea of what to do about getting the system to use other recognition languages now it's running in WINE instead of Windows.

Cheers,
Bret

---

### Post by 3rdalbum on 2011-05-22
Why does it use Wine?

---

### Post by a.sarkar on 2011-06-21
Dear Bret,

Thank you for your time and effort. I am trying to use your Ink2Text software. 

Installed ship client. Also followed your instructions to install Ink2Text software. 
In the instructions to install Ink2Text software just before the command 
```
sh winetricks dotnet20
```I ran the following command to download winetricks.
```
wget http://kegel.com/wine/winetricks
```Installation went smoothly. Started a dedicated shell to run the 2 commands
```
export WINEPREFIX=$HOME/.wine-Ink2Text
wine /usr/local/bin/RecognitionServer.exe 8888
```In a different terminal ran the command
```
Ink2TextUtility 
```The result was just as you predicted. Now I ran the commands

```
cd ~/ship/client
java  -Djna.library.path=/usr/local/lib -Dswing.aatext=true -jar SHIP_Ink2Text_v1.1.0.jar ship.properties 

```I have installed the ship client in my $HOME directory. The starting msg I get is

```
Passed new Ink2Text()
Ink2Text Library not found: jnidispatch (/com/sun/jna/linux-i386/libjnidispatch.so) not found in resource path
InkServerURL is http://192.168.56.251/TabletPC/MSInkService.rem
Using xmlrpc client:  org.apache.xmlrpc.client.XmlRpcClient@743399
```Notice that it cannot find the Ink2Text Library. However, the dedicated shell is still running. 

I then opened gedit and wrote something with my stylus in the ship input panel, and pressed the "Send" key. After a while I got a whole list of error msg. The last line was

```
org.apache.xmlrpc.XmlRpcException: Failed to read server's response: Connection timed out
```Am I missing something? I would really love to make this thing work. BTW I am using Ubuntu 10.04.

---

### Post by a.sarkar on 2011-06-21
Hi Bret, 

Solved the problem :).
Had to install the package libjna-java
```
sudo apt-get install libjna-java
```Copied the ship folder to /usr/local/share/ 
My ship-client.sh script at present is as follows:

```
#!/bin/bash

InstallDir=/usr/local/share/ship/client
JarFile=SHIP_Ink2Text_v1.1.0.jar

cd "$InstallDir"
java -Djava.library.path=/usr/lib/jni -Dswing.aatext=true -jar "$JarFile" ship.properties

```Notice the java library path has been changed. Also the thing that worked was
"-Djava.library.path" not "-Djna.library.path". My guess it's a typo in your "ship" shellscript.

One question: When I start the ship client, it always opens to keyboard. Is there a way to directly open it to ink input?

Will try the ship client again extensively, once I get back home.

---

### Post by bcw on 2011-06-21
Hello,

I'm glad you found the solution.

In the future, please put help requests in the Help forum on the sourceforge site.  That way everyone can benefit from the answers.  You would have read this solution there, although you would have needed to follow the thread to the end.

It is too much work for me to follow requests and duplicate the answers in two (or more) places - there is only one of me.  So please help me out by posting there.

I installed the S/HIP in my home folder, and my script to start it is:```
#/bin/sh

cd ~/ship/client
java  -Djna.library.path=/usr/local/lib -Dswing.aatext=true -jar SHIP_Ink2Text_v1.1.0.jar ship.properties
```

> -Djna.library.path works fine for me.

I think a re-compile would be required to present the ink field at start-up.  In the original system, not everyone could use the recognition, so starting with the keyboard, which everyone can use, seemed best.  I may be re-writing the S/HIP as components using Spring as part of my next Big Idea, but that won't happen in the next two months.

In case you haven't read the S/HIP manual, you will need the XVkbd program installed to transfer the letters to the target window.  If you do have further problems, please read through the (small) Help forum on the sourceforge site, and open a thread there if you can't find the solution.

Cheers,
Bret

---

### Post by messie on 2011-07-20
hi this has been Working nice for Me ( I have written this with My tablet as a Matter of fact)

however i is there possibility for greek character recognition?

---

### Post by majedaly on 2011-11-10
does anyone know of handwriting recognition supporting Arabic text?

---

### Post by spaesani on 2011-12-29
Hi.
First time round everything worked but I got the ship focus freeze.
A reboot later:

steve@steve-ThinkPad-X61-Tablet:~$ wine /usr/local/bin/RecognitionServer.exe 8888
RecognitionServer - Run as a server on port: 8888
fixme:atl:AtlModuleInit SEMI-STUB (0x49b97000 0x49b97ae8 0x49a90000)
* Assertion at marshal.c:5412, condition `mtype != NULL' not met


?? any ideas?

---

### Post by bcw on 2011-12-29
> **spaesani said:**
> ?? any ideas?

Yes.  As mentioned above, support is available in the sourceforge project help forum.

Please read there to see if your issue has a solution already, and post a request if you don't find a solution.  Reading the previous requests will give you an idea of the steps to try and the information to post.

Regards,
bcw

---

### Post by dceggert on 2012-01-25
Do you have any screenshots of what this looks like?  
 
As soon as there is a PowerVR driver available I will be changing my Fujitsu Q550 over and will be looking for something like this.  Very encouraging...

---

### Post by mitchellroe.236 on 2012-09-17
Thank you for your work on this; it looks like a really promising project.
How would I go about uninstalling the package, or could you tell me what files it creates throughout the installation process?

```
# make uninstall
``` returns ```
make: *** No rule to make target `uninstall'.  Stop.
```

Thanks!

---

### Post by a.sarkar on 2012-09-17
@mitchellroe.236

While installing you can use paco to install and gpaco to uninstall. First install gpaco

```
sudo apt-get install gpaco paco
```Then while installing any software from src the command

```
sudo make install 
``` becomes

```
sudo paco -lD "make install"
```Paco takes note of all the files that "make install" command installs. Later you can use gpaco to uninstall the package via the command

```
sudo gpaco
```which opens a graphical interface for uninstallation. More info at [http://paco.sourceforge.net/](http://paco.sourceforge.net/)

Good luck.

---

