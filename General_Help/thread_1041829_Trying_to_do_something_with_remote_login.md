---
title: "Trying to do something with remote login"
date: 2009-01-17
forum: General Help
---

### Post by Arukas on 2009-01-17
I am working on a small home project.  I am trying to get network two of my machines.  They are both using Ubuntu. 

I would like to set my second computer up where I can just do a remote log-in and operate the computer that way.

I read some posts, but I am just more confused.

---

### Post by RealPSL on 2009-01-17
The first thing you have to do is enable remove login with System > Administration > Login Window. Select the Remote tab and from the Style drop down choose "Same as Local" and click close.

From the remote Ubuntu PC you are connecting from you should have Options in the lower left hand corner. Choose "Remote Login via XDMCP" Enter the IP address of the target computer and you should be all set.

---

### Post by nothingspecial on 2009-01-17
```
sudo apt-get install ssh
``` on both machines

To log in and run graphical apps
```

ssh -X -C -c blowfish username@ipaddress
```

Now that`s too much typing for me so I create an alias. Aliases are great for long commands.

To log in to my server I use ```
server
```

To log into my wifes laptop I use ```
suzie
```

To make an alias ```
nano ~/.bashrc
```

To give you an example here is the alias I put in my .bashrc to log in to my server

```
alias server='ssh -X -C -c blowfish user@192.168.2.4'
```

Do you get the idea. Now in a terminal I just type ```
server
``` to login. From that terminal you can now launch apps on the other computer.

Another useful thing to use is screen.

```
sudo apt-get install screen
```

To launch it just type screen. What this doe is allow you to run things in a terminal and then detach the process so that closing the terminal doesn`t close the process.

An example would be if I wanted to start a torrent on my server. From my laptop.
```
screen
```
```
server
``````

screen
```
```
deluge
```
do my stuff
Ctrl + A 
Ctrl + D to detach deluge from the terminal but keep it running. I can then do other stuff on the server without stopping my torrent.
Ctrl + A
Ctrl + D to detach my session on the server but leave deluge running still.

---

### Post by Arukas on 2009-01-24
I finally got my computers talking alright.  My network is connected to the internet.  How can I keep the internet from trying to log on ussing ssh?  I just want my computer on my intranet to remote log on.

---

### Post by mb_webguy on 2009-01-24
You can use Vinagre (Remote Desktop Viewer under Applications->Internet) to login to the other computer.  It's easy to set up (by simply clicking a couple of checkboxes in the Remote Desktop settings under System->Preferences), and you can set a password.  If you're concerned about security beyond simply setting a password, you can change the port used and enable encryption under the Advanced tab.

---

### Post by cariboo on 2009-01-24
If you are connected to the internet through a router, you shouldn't have to worry about anyone trying  to crack your remote computer if you don't have any ports forwarded.

If you do have port forwarding enabled, I would suggest installing denyhosts on your remote computer, this won't stop people from trying to break into your computer, but it will deny access to anyone who tries to log in more than 5 times unsuccessfully. Denyhosts in in the repositories and you can install it on your remote computer using Synaptic Package Manager and of course the command line.


Jim

---

