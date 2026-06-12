---
title: "Intrepid is good... but..."
date: 2008-12-05
forum: General Help
---

### Post by jobsonandrew on 2008-12-05
So I just installed Intrepid Ibex yesterday.. There are a few things I'd like to clear up:

1) Why cant I/How do I set a screensaver for the login screen? I tend to just switch my Laptop on and go out.. the login screen is eventually hidden, but the backlight stays on..? it seems strange that a modern operating system doesn't protect the screen at the login prompt

2) Is there a way to log in remotely via VNC, and get to YOUR desktop, i.e. not a separate session... Imagine I turn my computer on, and go out.. then log in via VNC from somewhere else.. how can I get the desktop that I usually see when I log in (in the same way that logging on with windows terminal services would)

3) My Fn+F8 key wont switch between the laptop panel and an external monitor correctly, I have to go into the Nvidia X Server configuration every time to click some buttons, I know this could probably be automated via script, but Windows just seemed to remember the settings it used last time whenever i turned it on, and could be quickly switched to the other screen, and it would be at native res..? I have yet to find a good guide on configuring X

4) for some reason the only way i can get to my Freecom NAS drive is to mount it at the terminal (as type 'cifs') I cannot refer to it as "smb://<host>/<share>" anymore.. but I can browse shares on my vista machine that way... smbclient will connect at the terminal, I can cd into folders and 'get' or 'put' files, but as soon as I 'ls' to view the content of a folder, smbclient crashes.. could this be a problem with gvfs, samba, nautilus, or other?

Any thoughts/ideas would be great

Thanks

---

### Post by cariboo on 2008-12-05
> 2) Is there a way to log in remotely via VNC, and get to YOUR desktop, i.e. not a separate session... Imagine I turn my computer on, and go out.. then log in via VNC from somewhere else.. how can I get the desktop that I usually see when I log in (in the same way that logging on with windows terminal services would)

You can connect to your laptop using vnc, I would suggest installing tightvncserver, it is in the repositories. To be able to see the desktop remotely you will have to be logged in on the laptop. You also have to setup port forwarding on your router if you are using one. 

Jim

---

### Post by jobsonandrew on 2008-12-05
hey thanks! yeah im using a router and most of the time i would be tunneling the connection over SSH.. and i have no problems with port forwarding. However, my point was that if the machine was NOT logged in yet, (i.e. I had just turned it on, and thats all) how could I log into my desktop as if i had logged on locally?

It's quite sensible that the machine is very protected because nobody has logged on yet... but not everyone is bothered about such security before login (especially home users)...

Thanks again

---

### Post by Zorael on 2008-12-05
Regarding (4);
> **Zorael said:**
> Per default Ubuntu doesn't heed requests towards "computer names" like Windows does (\\COMPUTER and smb://COMPUTER). So you'll want to enable WINS (Windows Internet Name Service) host resolution. You need to install **winbind** with your package manager of choice, and modify **/etc/nsswitch.conf** slightly.
```
$ sudo aptitude install winbind
```
Pop up that nsswitch.conf in a text editor with superuser permissions and find the 'hosts:' line. Mine looked like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
Now just add **wins** after files (order matters) and save the file.
```
hosts:          files **[COLOR="DeepSkyBlue"]wins[/COLOR]** mdns4_minimal [NOTFOUND=return] dns mdns4
```
Then restart samba for good measure. I think that ought to do it.
```
$ sudo service samba restart
```

On a sidenote, use **smbtree** to discover other computers in your network. Just hit enter when it asks for a password unless you need to authenticate towards the other computers to access their shares.
```
$ smbtree
Password: 
LAPPNET
	\\TLEILAX        		Linux Mint
		\\TLEILAX\Print_to_PDF   	Print to a PDF File
		\\TLEILAX\IPC$           	IPC Service (Linux Mint)
		\\TLEILAX\video          	
		\\TLEILAX\audio          	
		\\TLEILAX\downloads      	
		\\TLEILAX\print$         	Printer Drivers
	\\SUNSPIRE       		
		\\SUNSPIRE\video
		\\SUNSPIRE\downloads
		\\SUNSPIRE\pleiades
...
```
As for crashes? Pass!

---

### Post by jmszr on 2008-12-05
jobsonandrew,
          
            For what help it is, to avoid the Login process go to System > Administration > Login Window > Security > and then actuate Enable Automatic Login,

---

### Post by jobsonandrew on 2008-12-06
Thanks for the suggestions.

I dont think it is having problems with computer names, because if i use
```

smb://FND/PUBLIC

```
It will fire up the disk in the NAS (you can hear it), its after that point that problem occur.

Automatic login is not something that i want to enable, its certainly not something that you should *need* to do

---

