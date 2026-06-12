---
title: "(SCRIPT) Ventrilo w/ Text-To-Speech Installer"
date: 2008-02-03
forum: Gaming &amp; Leisure
---

### Post by FrozenFox on 2008-02-03
_**UPDATE Wed Apr. 30 '08:**_ As the script and readme say, the links to the files in the script are likely to eventually be broken concerning the ventrilo exe. Simply open the script installer in your favorite text editor and replace the bad link (ventrilo 3.01) to a working direct link if you get a 404 causing something in the script to fail. You can easily do this by googling ?intitle:index.of exe ventrilo and searching for a link. Here's one I found in just a few seconds. [http://www.olderan.net/raznoe/ventrilo/ventrilo-3.0.1-Windows-i386.exe](http://www.olderan.net/raznoe/ventrilo/ventrilo-3.0.1-Windows-i386.exe)  just change the url line for ventrilo in the script and it will work again. They're right at the top of the script, obviously labeled, you can't miss them. I won't update the file attached to this post, because -that- link is likely to eventually break too. If someone finds a direct mirror that won't go down, tell me and I'll update the file. Until then, it only takes a minute or two to follow directions.

_**UPDATE:**_ Small bugs fixed and an error in the instructions here fixed. See the end of the post.

(**Pre-note**: Before you start, **it might be illegal to use this if you don't own Windows**. By using it, you should probably have a valid windows license. If you don't agree with this, please use another means of installing ventrilo that does not involve the text-to-speech part or the codec from microsoft, the responsibility is yours to deal with. Perhaps remove those lines from the script, if that is the case).

Hey all,

I'm not sure if someone has a better way to do it (or if this is the appropriate forum to put it in.. I don't think many people would look in the wine forum for vent. shrug. sorry if it is), as I'm not one to normally use ventrilo. But here goes, anyway..

I've put together a script based on one -someone else- made a ways back. The cool stuff:

* Sets up ventrilo **with text to speech** working correctly, via wine. 
* Sets up ventrilo such that you can **install multiple versions** of it, in case you know someone who refuses to (or cant) update their server to the newest version.
* The script is **more broken/slow-link and future-release friendly**. You can open the script in your favorite text editor and change 1-2 lines at the top for new versions, and 1 line for each broken link. 

**NOTES: **

* I don't imagine the text-to-speech link in the script will break any time soon, as they're from MS. But I imagine the ventrilo link might. I couldn't find a direct http link to it for some reason on a server that seemed 'permanent'. We'll see what happens. **If a link breaks**, please tell me (and preferably find a new one hehe) and I will update the script with a new link. Or one of you can, it's a piece of cake to change it ;P

* **I only take credit** for rearranging the script and adding a few parts (text to speech, letting it remove the vent installer exe, future-release and broken-link friendliness, multiple version capability). I couldn't find the thread I downloaded the original script from or the name of the poster to give due credit, but it appears to have been the one that WAS located here [http://kanava.org/~hifi/linuxventrilo.sh](http://kanava.org/~hifi/linuxventrilo.sh)  but the link is toast. If someone knows, by all means, please tell me who it was.

* **Please be careful.** I've tested this on Linux Mint Daryna (ie it should work on Gutsy due to their similarities), and Ubuntu Hardy Heron. Note that I am also COMPLETELY NEW to scripting, so this may not work perfectly or may even do something strange or harmful (unlikely, but possible I suppose). You've been warned.

* As per above, please, experienced script writers: don't slaughter me for my inefficiency. :) I did what I could, and it has worked on 2 different systems. Hehe. That's good enough for me!

With that said and done, **PLEASE FOR THE LOVE OF CTHULHU LOOK AT THE README!**

_**--- DOWNLOAD AND INSTALLATION ---**_

Anywho, **attached to the END OF THIS POST** are the two scripts. They are exactly the same except for maybe 1-2 lines. gametools_Ventrilo301install.tar.gz installs ventrilo version 3.01 and the other file of course installs ventrilo 2.30. Unless you're sure your desired server is running the old version, go with 301. Or install them both. I don't care.

To install this:

* **Look at the readme!**

* **Extract the tar file**. You can right click on it and extract, I believe. Alternatively, in the terminal/console use tar -xvf /path/to/the/tarfile/tarfile.tar.gz.

* **Make sure the file is executable.** You can right click the file and go to properties and find the place to make it **executable.** For the sake of not confusing gnome users vs kde users as to the position of this particular setting, I will keep that statement vague. Alternatively, in the terminal/console you can chmod a+x /path/to/the/installer/installventrilo.sh.

* **Change directories to the appropriate folder** and **run the program directly**.** I don't think the script will work correctly if you run it via double click or whatnot because of path issues. **Open the terminal/console and cd to the directory the installer is located. Ie, if its in vent310install on the desktop of the user jim, type cd /home/jim/Desktop/vent310install. tar -xvf I believe defaults to /home/yourname. Finally, run it with the command ./installventrilo.sh.

* **When done, delete the extracted installation files.**

The script should tell you (thanks to the original author, and a small tweak for the new stuff included by me) whether you need something else or not, like wine or other small programs. The only thing you should need OOTB is wine, unless I'm mistaken. I have tested this script with wine versions 0.9.52 and 0.9.54 and all appears to work well. If you do not have wine installed, visit winehq.com for instructions on adding the repositories for the newest version or install your current version with sudo apt-get update and then sudo apt-get install wine. Or, install wine from synaptic. Whatever floats your boat.

Apologies for being verbose, and good day.

**_UPDATE:_** I've fixed the instructions. You are supposed to use ./installventrilo.sh not sh ./installventrilo.sh. Oops. I've also fixed a couple small bugs concerning ventrilo2.ini being hardcoded to -my- setup (oopsies! hehe. strangely enough, vent seemed to work anyway in another setup with another user name on another machine i tried!) and default.vet not being included or generated by ventrilo. If you downloaded before, you may wish to re-download, delete /home/yourname/ventrilo3 (or ventrilo2), and the directory /home/yourname/.ventrilo3 (or .ventrilo2) and install again. I don't think it would cause problems to warrant starting over that way, but do so if necessary.

Please tell me if it works correctly now.

---

### Post by FrozenFox on 2008-02-03
Apologies for bumping this, but I've updated the thread's instructions and the installation files to fix bad instructions and an installer bug. All should work well now. Please tell me if you have problems or it works correctly on a distro/version other than the two I've mentioned. Also, if the installer tells you it is in need of a certain file, you can probably just sudo apt-get update and then sudo apt-get install name-of-program-that-you-need. Thanks, and apologies for those prior obvious bugs :)

---

### Post by mdntsurfer on 2008-05-21
Heya, I,m fairly new to scripting and haven't ran linux in a few years, Anywho I'm working on getting Wine, WoW, Vent, and my USB headset going.

So I came across your post and looked interesting so I'm playing around with it. Was thinking about the problem with getting the files for the script and the ventrilo changing. I just put the vent exe on my server that I use to play around with on my own PC and linked to it and the script worked. Might take a little more work if you don't have a url for http or ftp set up but if you already have it was just an idea if you was having trouble finding one.I'm guessing though that a permanent link makes it easier.. just run the script and let it do the work kinda the point of it aye. I just did it to keep going today.

So I have now fixed script to what I needed and ran the script and all loaded just fine. So when it came time to fire everything up and test... Vent loaded.. my headset mic worked.. I could hear people talk but no text to speech. Then I fired up WoW and the sound came out my speakers...So I have WoW playing can use vent to raid and my headset works. Im happy so thanks for your work .. might not have done what I originally dl it for to try. I have some other machines Ill play around with it on.

---

### Post by FrozenFox on 2008-05-21
You're welcome, thanks for the input. :)

Odd, the TTS has worked for me on several different machines and distros without issue. I just tested the SDK link in the script and that appears to be OK. As such, I will need some information to figure out what the problem is, as I can't think of any immediately obvious problem.

* What version of Wine are you using? (wine --version in the terminal/console). 
* 32 or 64 bit?
* What distro and version? Ubuntu I'm assuming, since it's here on these forums, but are you using 7.10 Gutsy or 8.04 Hardy?
* Does the microsoft SDK installer window come up and appear to install correctly?
* Did you alter the part of the script to grab the microsoft SDK exe off your webserver too? If not, please rename the folder /home/yourname/.ventrilo3 and the file /home/yourname/ventrilo3 to something else really quick (ie .ventrilo3WORKS and ventrilo3WORKS respectively) and then run the installer script again, and post everything the script says, or at least what it says after this text:

"---------------------------------------"
"Downloading microsoft's text-to-speech stuff. You will be asked to click next as usual."
"Just use whatever default info it gives."
"I've confirmed TTS to work in wine version 0.9.52."
"DO NOT WORRY about the errors before and immediately after the installer comes up."
"---------------------------------------"


You can of course remove the new folder and file and restore your old ones if you wish. If I can't figure out anything based on the above, I will try running a virtual machine with your system setup and see what happens.

---

### Post by dawtry on 2009-09-23
I keep getting the error "wine: cannot find 'C:\Ventrilo3\Ventrilo.exe'". How can I fix this?

Thanks for any help.

---

