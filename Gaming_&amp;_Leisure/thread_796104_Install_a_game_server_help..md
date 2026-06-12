---
title: "Install a game server help."
date: 2008-05-16
forum: Gaming &amp; Leisure
---

### Post by Fulgore on 2008-05-16
I would like some help with installing the game Kingpin.

I used to have it installed in to 
/usr/local/games/kingpin

I notice that Ubuntu uses /usr/games/
Do I use this directory?

I have noticed everything is locked, like the filesystem, tring to mount other drivers.
Or I get you need root to do this...blah blah 
How do i get rid of all this?
Anything else I extract i get error
tar: readme: cannot open: permission denied
.....
..
.

Why is everything locked how do I disable all the locking so when I logon I have all the right permissions?

I am sort of new to this. Well I have used a remote telnet terminal to run my old kingpin server. So I know a few commands.
Now I have the server at home on my cable connection.
Just want to get this installed.
I have installed wine, not sure why as I dont want to play it, I just want to run the server in a terminal window.
Help me please.

---

### Post by h4mx0r on 2008-05-17
I have no clue what this game is about. But if its a windows executable you have to run it with wine and check winehq application database to see how well it runs and what you might have to do to get it working. playonlinux also has tips for getting some things to go but don't think I saw one for kingpin. You will probably want to use cron to start the game server with wine at boot and execute short commands to the server every so often for maintenace (like to make sure its running or restart it if you gave it new files to work with). ssh is also good for uploading/downloading things to your server and adjusting settings remotely. ufw will help too for setting up a firewall so that it only acts as a game server and doesn't make needless traffic. If you want to ban access to certain users try /etc/hosts.deny I hope I was of some help more info would be great :)

---

### Post by h4mx0r on 2008-05-17
Alright I didn't quite read what you said. Don't run wine with root its not a good thing. Also your game might require certain fonts or .net maybe a native dll something like that if it already isn't running.

use "sudo su" to become root and if something requires root it usually will say "sudo" meaning do with root.

why are you trying to extract a readme file!? use "nano" to view text files.

"chown" and "chmod" control permissions and "ls -an" shows permissions.

"man tar" to read the info on how to extract, also tar only extracts .tar files or .tar.gz you should try using some commandline extraction program that deals with all that crap for you, however I don't know of any I just read the manpages. Also if the extension has changed or isn't true like it says ".zip" but is really a ".rar" do stat on the file to see the true one.

If you login remotely and tell the server to run do it with & at the end to tell it to make a subprocess so it doesn't turn off when you close the terminal hopefully if it still goes off maybe try &&.

Please don't ever say telnet it sucks, if your on a windows machine use putty to access ssh on your server its more effective.

---

### Post by Fulgore on 2008-05-19
Ok I will start again. Thanks for your replys h4mx0r.

I have a pc at my house that runs game servers in windows.
Kingpin and Enemy Territory. Both have linux patches etc. So there is no need to run wine as I dont want to play them games on that pc, just serve in a terminal window.
I formated this pc because I was sick of it being hacked, if it wasnt so random hack I found that you could download game server files from the games being servered. It's a windows thing. So I installed ubuntu.
I have found everything seems to be locked. How do I unlock the system? (file system, mnt drives, ..etc)

I need a guide to install games into linux and then get them working.

cannot open: permission denied that is the error I get when I try to open any tar files that I have downloaded. (kingpin linux server patch)

This is getting frustrating. I see why so many people dont use it.

---

