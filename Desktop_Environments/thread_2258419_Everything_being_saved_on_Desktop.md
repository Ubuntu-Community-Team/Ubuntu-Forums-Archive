---
title: "Everything being saved on Desktop"
date: 2014-12-27
forum: Desktop Environments
---

### Post by james_king2 on 2014-12-27
I am running Ubuntu 14.04.1 LTS on an older ASUS desktop. I had formatted the 500Gb drive and installed Unbuntu as the primary OS only.  What I do not understand is why it seems that everything whether folders or other files seem to end up on the desktop? It seems as though there is not a choice of saving these files elswhere rather than cluttering up my desktop. I have tried making new folders and copying file to them then deleteing the icons on the desktop. However, programs then can't find their files or date and will not operate. One such program is GNUCash which I have searched their site for hours and can't find a solution listed or actually understand how I could actually post a question to either about this problem.
If anyone could steer me in a direction on how I might not have to clutter up my desktop with all these files, I would deeply appreciate it. I know little to nothing as I have just started using Ubuntu and I do not know anything about most everything concerning this area.  Even though I dislike Windows, I didn't have that problem. 
Thanks a bunch

---

### Post by grahammechanical on 2014-12-27
I cannot deal with your specific situation but I can give you a clue as to possible solutions.

Right now I am running Chromium. If I download a file that file will go into the Downloads folder. If I go to Chromium Edit menu>Preferences a settings tab will open and if I open Advanced Settings I get an option to change the downloads location. Ubuntu defaults to saving downloads by a web browser to putting the downloaded file in the Downloads folder. So, if this is not happening on your system it is because something has been changed.

Other applications have their own locations that they use by default for saving documents. We can override that by saving the document using the File>Save As option. We usually get a dialog that lets us browse to a folder that we chose to save the file to. Applications will remember where a file is saved to. Then when we try to open that file the application will try to open the document from the location where it expects the document to be. We can override this function by using the File>Open option. We usually get a dialog that lets us browse to the folder where the file is.

These are standard ways of working in every operating system and have been standard for decades. I do not know of any System Setting that will force applications to save or store files and documents on to the desktop. 

Applications in Ubuntu should default to saving documents into the Documents folder unless we change things. Music applications will default to saving audio files into the Music folder. Video applications will default to the Videos folder and Image applications will default to the Pictures folder. Unless we change things.

Regards.

---

### Post by ajgreeny on 2014-12-27
Are all your files sitting directly on the Desktop or are they in the usually named folders such as Documents, Pictures, Music, Videos, etc etc?

Let's see the output of **ls** in a terminal.  PLease show the output in Code-Tags ("How-to" in my signature below)
This will give us a clue by listing the folders in your /home; it sounds as if something may have gone wrong in the /home setting up at installation.

---

### Post by james_king2 on 2014-12-30
I am running the 32 bit version of Ubuntu it that would make a difference as to a 64 bit version concerning the code tags mentioned? What I had tried was coping the files to folders instead as Save As. But I probably should mention that I had set up Gnu cash and when I closed the program found all of it's files on the desktop. At the moment I am on my windows 7 machine and can't remember the other folders names that were also on the desktop. What I do know even though I do not know the proper names of the lists of icons on the left side of the screen right now, I do know that there are folders with the same names when clicking on the icon with a picture of a file cabinet on it but there was nothing in those folders (0) and the ones on the desktop had data and etc. inside them. That is minus Gnu cash which had nothing at all inside the file cabinet icon area. 
I will dig into it further as per your suggestions and get back to you about it but it will be a little later on as I have some urgent personal matters I have to deal with right at the moment leaving me no time to play with it. Even with the minor problems I have come against in the OS, I like it very much thus far. I really like the E-mail in Thunderbird as it works real well for me. If I can get the wrinkles straightened out, me and Windows will be history. I just need programs similar to Quicken and a few others to work as I do a lot of writing and personal finance as well as Family Tree work etc.,.  I appreciate the input and certainly will get back to you all as soon as I can.

---

### Post by bapoumba on 2014-12-30
How did you install GnuCash ? Did you install it from the Software Center/Synaptic/apt-get (Ubuntu has a GnuCash package in the universe repositories) ? I suspect you directly installed their own source and it all ended up in your Desktop.
[https://help.ubuntu.com/community/GnuCash](https://help.ubuntu.com/community/GnuCash)

---

### Post by james_king2 on 2014-12-31
I installed it from the Unbuntu software center in the OS.  I didn't download it from GnuCash directly. In other words the software center which came with the Unbuntu OS 14.04.1 LTS ISO. I haven't figured out how to install software any other way as I know nothing about typing in commands to run things as yet or understand the commands or where to type them in as yet.  I've only been fooling around for less than a week and a half with Ubumtu. The whole thing is confusing to me as yet.
Thanks for your note, Jim

---

### Post by yancek on 2014-12-31
You can go to the page below and click on the link "Start Tour" which will give you an overview of how to use Ubuntu.

[http://www.ubuntu.com/desktop/take-the-tour](http://www.ubuntu.com/desktop/take-the-tour)

Or download the Ubuntu Manual.

[https://ubuntu-manual.org/](https://ubuntu-manual.org/)

---

### Post by bapoumba on 2015-01-01
> **james_king2 said:**
> I installed it from the Unbuntu software center in the OS.  I didn't download it from GnuCash directly. In other words the software center which came with the Unbuntu OS 14.04.1 LTS ISO. I haven't figured out how to install software any other way as I know nothing about typing in commands to run things as yet or understand the commands or where to type them in as yet.  I've only been fooling around for less than a week and a half with Ubumtu. The whole thing is confusing to me as yet.
Thanks for your note, Jim
OK thanks. We'd need to know which files are on your Desktop then. Either take a screenshot or better, open a Terminal (search for "Terminal" in the search box as shown in the first screenshot from yancek's link) and run :
```
cd Desktop/
ls -a
```
Then highlight what comes out, and middle click to paste the output here.

---

### Post by schragge on 2015-01-01
If the OP already found his way to the terminal, I'd also like to suggest him running these commands:
```

echo $HOME
getent passwd $USER | cut -d: -f6
xdg-user-dir
xdg-user-dir DOCUMENTS
xdg-user-dir DESKTOP

```
and post back their output to let us see what directories the system thinks are his home directory, his Desktop, and his Documents folder

---

### Post by james_king2 on 2015-01-01
First, Thank all you folks and Happy New Year!  I have basically stumbled into a couple of things but haven't gone totally forward and only have been printing the Ubuntu Help Files as well as many threads simply because I have a memory about a split second long. I deleted all the stuff that was planted on my desktop a bit ago. I fired up GNUCash and started a new file from scratch without going into all the details as I wanted to try the "save as" and try to point it to a new folder. Now I may be wrong here and there as I do not understand the way or the places folders actually end up. I know how to do it in a Windows invironment but not in Ubuntu.  Any way, when I tried to do the "save as" thing, GNUCash said that I didn't have permission to save the file where I had tried to send it.  When I installed the OS, I simply named James as Administrator, (My real name) and it also seems that possibly the "Home Folder" and the "James" are inter conneced somehow. Also, it seems as though the "Home Folder" ends up tied to the "desktop" and places the files there. Now when I check the "permissions" the first and uppermost is called "Me" and the next listing is "James" and both have administrator settings. I can't find away to change it around or rename the "ME" as it doesn't do anything. 
Right now I can't say exactly how I stumbled into or onto this but it says this. Terminal - Gnome terminal 3.62 and says Terminal enulator for Gome desktop. I didn't play with that as I know nothing about it. I would have to go back to some of the thread print outs to be able to tell you how I got there actually but I think it was by using Ctrl, Alt, T,.  Hopefully this might help in some way? I would have to find out how to do a screen shot and paste it into the thread. 
I will download the manual as suggested but I have to wait until after 12:01 due to my service which charges for over running their limits as I have been pushing it a lot with Ubuntu. 
Thank you, Jim

---

### Post by schragge on 2015-01-01
> **james_king2 said:**
> Terminal - Gnome terminal 3.62 and says Terminal enulator for Gome desktop.
Yep. That's the thing.
> I would have to find out how to do a screen shot and paste it into the thread.
No need to do a screen shot. Just select text with the mouse, then press **Ctrl+Insert** to copy and **Shift+Insert** to paste.

---

### Post by james_king2 on 2015-01-01
bapoumba, this is what came up with the commands you asked me to try. 

james@james-System-Product-Name:~$ cd desktop/
bash: cd: desktop/: No such file or directory
james@james-System-Product-Name:~$ ls -a
.              .cache    .ICEauthority           .thunderbird


..             .compiz   Jim's Finances.gnucash  .wicd
.adobe         .config   .kde                    .wine
.aqbanking     .cups     .local                  .Xauthority
.bash_history  .dbus     .macromedia             .xsession-errors
.bash_logout   .gconf    .mozilla                .xsession-errors.old
.bashrc        .gnucash  .profile
.bibletime     .hplip    .sword
james@james-System-Product-Name:~$

---

### Post by james_king2 on 2015-01-01
schragge, I probably didn't get you command sintax right as I do not know the proper way to inter it. Anyway I will give what I got if any of it means anything at all?
james@james-System-Product-Name:~$ echo $home

```
james@james-System-Product-Name:~$ getent passwd $user | cut -d: -f6
/root
/usr/sbin
/bin
/dev
/bin
/usr/games
/var/cache/man
/var/spool/lpd
/var/mail
/var/spool/news
/var/spool/uucp
/bin
/var/www
/var/backups
/var/list
/var/run/ircd
/var/lib/gnats
/nonexistent
/var/lib/libuuid
/home/syslog
/var/run/dbus
/home/usbmux
/var/lib/misc
/var/lib/avahi-autoipd
/
/proc
/home/saned
/nonexistent
/var/run/speech-dispatcher
/var/run/avahi-daemon
/var/lib/lightdm
/var/lib/colord
/var/run/hplip
/var/run/pulse
/home/james
james@james-System-Product-Name:~$ xdg-user-dir DOCUMENTS
/home/james/
james@james-System-Product-Name:~$ xdg-user-dir documents
/home/james
james@james-System-Product-Name:~$ xdg-user-dir desktop
/home/james
james@james-System-Product-Name:~$ 
```

I tried  several ways of intering the commands but I doubt any of it is on target, Jim

---

### Post by schragge on 2015-01-01
Jim, the commands are case-sensitive, words in CAPS must be typed so. But I already see this:
```

[COLOR=green]james@james-System-Product-Name:~$[/COLOR] xdg-user-dir DOCUMENTS
[COLOR=red]/home/james/[/COLOR]

```
and this is not good.

---

### Post by schragge on 2015-01-01
@**james_king2**
Please try this commands:
```

xdg-user-dirs-update --force
xdg-user-dir DOCUMENTS

```

---

### Post by james_king2 on 2015-01-02
Schragge, I saw the caps but going back to my days in MS DOS and fooling around in that OS caps were not allowed. I will try your previous as well as your present commands and get back to you. Right now I am printing out the Ubuntu 14.04 manual on my Window 7 lap top. When I first tried the (xdg) command it came back twice as saying no such command then I tried a few more times and got as far as I had. 
I was almost tempted to reformat the drive and reload the Ubuntu OS. I originally tried it with dual boot with windows XP Pro already installed but I also new there was a problem with XP and then just trashed it all. 
Thanks for you input.  I am slow at getting things down but will manage as I get more accustomed to the system.

---

### Post by james_king2 on 2015-01-02
schragge, This is the results of the last two commands you asked me to try.
james@james-System-Product-Name:~$ xdg-user-dirs-update --force
Moving DESKTOP directory from  to Desktop
Moving DOWNLOAD directory from  to Downloads
Moving TEMPLATES directory from  to Templates
Moving PUBLICSHARE directory from  to Public
Moving DOCUMENTS directory from  to Documents
Moving MUSIC directory from  to Music
Moving PICTURES directory from  to Pictures
Moving VIDEOS directory from  to Videos
james@james-System-Product-Name:~$ xdg-user-dir DOCUMENTS
/home/james/Documents
james@james-System-Product-Name:~$ 

It looks like most everything has now moved onto the desktop? Jim

---

### Post by james_king2 on 2015-01-02
schragge, these are the folders on the desktp now after using your last commands. The gnucash says spread sheet on it rather than being a folder, Jim
Desktop after using the commands.
/home/james/Videos
/home/james/Templates
/home/james/Public
/home/james/Pictures
/home/james/Music
/home/james/Downloads
/home/james/Documents
/home/james/Desktop
/home/james/Jim's Finances.gnucash

---

### Post by james_king2 on 2015-01-03
schragge, I tried you last code as you had mentioned previously. As my last note with the items that were on the desktop I want to tell you this. Today after starting the machine all the items that had been on the desktop are nolonger present. If that is do to the code you had me inter, it worked up to this point I haven't tried anything else as yet other than fire up GNUcash. I wanted to see if it could find its files and it did find them. I am happy about that to say the least. 
The other thing I tried just to try it was go through each folder in DASH (I Think) and right clicked on each folder to get their properties. I changed the permissions to include myself as read and write on them. The permissions still list {Me} at the top of the drop box. I don't know if that is something native to Ubuntu or not? I guess as long as I can get to my files etc., it probably is nothing to worry about but, I can't help but wonder where the (Me) came from in the first place? 
I haven't tried anything else other than start reading the Ubuntu Manuel 14.04 I printed out early this morning. 
I want to thank you as well as the other folks for steering me on in all of this.  Brieng I don't really know my way around ths forum other than asking questions and using the "quick reply," I will have to dig or find out how to add in the (Solved) should that be the way this machine is going to continue to work with a nice clean desktop! 
My next challange is to try to figure out how to get my Epson LQ 570+ ESC/P2 dot printer to work under this system. I have searched the Hardware areas and it seems that Epson Dot printers that are 24pin do not work properly and there are not any work arounds that actually work for it either. I have downloaded several ppds or whatever they are called but I don't know how to really try them either. I also downloaded Ghostscript-8.14-2-i386 deb,. Anyway all the forums related to the Epson dot printers are closed. The ppd that is in my system for 24 pin only prints out garbage and spits out sheet after shhet of paper non-stop. 
The Epson site quit drivers for these printers around Windows 98  and never went further. I may never get it going under this system but I like using the printer for printing out things to see if I need to make corrections as it is less expensive to use than Inkjet or laser printers.
Thank you again, Jim

---

### Post by schragge on 2015-01-03
Yep. The second-to-last command (*xdg-user-dirs-update --force*) did the trick. Please mark this thread SOLVED (see [uwiki]UnansweredPostsTeam/SolvedThreads[/uwiki]), and open another topic about your printer if needed.

BTW, [openprinting.org]("https://www.openprinting.org/printer/Generic/Generic-ESC_P_Dot_Matrix_Printer") shows only built-in ghostscript printer drivers for epson dot matrix printers, but says they should work perfectly. Are you sure you really need that old ghostscript 8.14? Just install the version from Ubuntu repository:
```
sudo apt-get install ghostscript
```
The PPD for Epson LQ 570+ is provided by package *foomatic-db-compressed-ppds*, it should automatically get picked up by CUPS on install. Just to be sure, reconfigure CUPS manually afterwards:
```

sudo apt-get install foomatic-db-compressed-ppds
sudo dpkg-reconfigure -phigh cups

```
But please, don't continue discussing printing issues here, start another thread in **Hardware** subforum as I said.

---

### Post by james_king2 on 2015-01-04
schragge,
I did do the solved as you said. I will also go to hardware as you suggested as well should I need to. I certainly don't desire to mess things up. Again, thank you and the other folks for the help! Jim

---

