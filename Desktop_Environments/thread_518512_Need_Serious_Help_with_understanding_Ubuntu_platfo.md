---
title: "Need Serious Help with understanding Ubuntu platform heirarchy"
date: 2007-08-06
forum: Desktop Environments
---

### Post by chriv on 2007-08-06
OK.  I'm trying.  REALLY, really, trying.

I have been using Windows less and less and less, because I have found with the abundance of open source software available for BOTH windows and linux (like Firefox, Thunderbird, and OpenOffice), that I need windows less and less.

I have been trying to move exclusively to linux desktops like Ubuntu, but cannot yet.

Why?  I am still not able to tweak it to the amount I need, simply because I do not know how it works.  Terms like GDM, Gnome, Gnome2, X11, xorg, Nautilus, etc., are still new to me, and I don't know how to customize them the way that I really need.

I'll post a specific problem first, and then I'll post a more general problem second.

Problem # 1:

Back in the days of Windows 3.1, you could choose to replace your Windows "shell" with another program.  For instance, if you changed the Windows "shell" from "Program Manager" to "Notepad", than starting Windows would open up only notepad instead of Program Manager, and closing Notepad would end Windows.

Here is what I want:  **When one of my users (just one of them only) logs into Ubuntu, I do not want them to see their desktop.  Instead, I want "/usr/bin/vmplayer /vmware/VM1.vmx" to run (launching a VMware Virtual Machine in the free VMWare player INSTEAD of their normal desktop).  When the user closes the VMware Player, Ubuntu should return to the main login screen**.  I'm pretty sure this can be done, but I don't know how (and not for lack of research).

Problem # 2:

I don't understand enough about the way Ubuntu really works to figure this out on my own.  I don't know many of the terms that are used by Ubuntu, Gnome, Xorg, X11, Nautilus, etc. (yet), and it makes it darn near impossible for me to find solutions in google or on ubuntu forums (or any other linux forums for that matter).  Also, it seems that Ubuntu is so far customized away from the norm sometimes that I cannot find the answers I need when going to sites for Nautilus or Gnome, etc.

Can somebody give me a REALLY THOROUGH primer of Ubuntu, X Server, Nautilus, and Gnome terms.  I'll never really be able to take advantage of the power of this system until I understand it better.

Here are some specific questions:

1) Can someone diagram the layers of Ubuntu?  What runs on top of what (and where do bash, Xserver, GDM, Gnome, and Nautilus fit into this picture)

2) As thorough a list of startup scripts, customization scripts, rc files, configuration files, their locations, and startup order as you are willing to provide.  For instance, what are the first scripts executed?  What follows?  When does the Xserver start?  Where are the customizations set for the Xserver?  What starts next?  Where can that be customized?  And all the way down to where to set customizations for logons for individual users!

Please, if someone is willing to provide a thorough and accurate answer for this on the forums, I think it would not only help myself understand the bigger picture, but can also help many other power users as well.

Eventually, A FAQ and/or OS map for Ubuntu power users would be great!

Thanks!

---

### Post by koshari on 2007-08-06
possable solution 1-

i think you may be looking at running vmserver in something like kiosk mode? this may give you the efect your seeking, 

another option would be to have the program run in any xserver without a panel and running at boot time, however the tools to get the panel back wouldnt neccesary have to be disabled. 

possable soltion 2

bash is basicly cmd in windows
Xserver is a window manager/gui, losesly speaking gnome, KDE, XFCE fluxbox and enlightenment are all window managers, 

nautilas is gnomes implementation of windows explorer, 
as is konkerer KDEs version of windows explorer. and thunar is xfces version of a windows explorer.

look at the boot profile without the quiet splash screen and you will get a pretty good idea of the order linux boots in, 

basicly its the bootloader, then kernel run, load services , load window manager, then load user services.

---

### Post by az on 2007-08-06
> **chriv said:**
> 
1) Can someone diagram the layers of Ubuntu?  What runs on top of what (and where do bash, Xserver, GDM, Gnome, and Nautilus fit into this picture)

-A graphical program is a client of the X server (it has something for the x server to display)  Nautilus is such an example.  Nautilus belongs to a suite of programs that all work together - gnome.  Gnome is a desktop environment.
-A desktop envirnoment runs in an X session
-A session in X is managed by a desktop manager (KDM, GDM, WDM...)  An X Session is pretty much about permissions.  Just like you log into a bash shell, you log into an X session.
-X (the x server) is a program that displays stuff on your screen
-The kernel abstracts your hardware and manages memory and other ressources.

> **chriv said:**
> 
2) As thorough a list of startup scripts, customization scripts, rc files, configuration files, their locations, and startup order as you are willing to provide.  For instance, what are the first scripts executed?  What follows?  When does the Xserver start?  Where are the customizations set for the Xserver?  What starts next?  Where can that be customized?  And all the way down to where to set customizations for logons for individual users!


When you boot, your bios will transfer control to the boot manager.  The boot manager will load a kernel into ram and use it to run the system.  It will then load an init ram disk (initrd) which will do autodetection and configuration of your computer.  It will then hand off control to init on the OS on the hard drive.  The start init scripts will be run from /etc/init.d/*  One of these scripts will start X and your X session will start.  When X starts, Gnome can be configured to run scripts at startup.  That's what I think you are looking for.

---

### Post by chriv on 2007-08-06
> **koshari said:**
> possible solution 1-

i think you may be looking at running vmserver in something like kiosk mode? this may give you the efect your seeking, 

another option would be to have the program run in any xserver without a panel and running at boot time, however the tools to get the panel back wouldnt neccesary have to be disabled. 

Before I go crazy looking how to do these, are these global solutions (that affect everyone who uses the PC), or can I implement them for a single user.  The key is that I need to do this for a single user. :)

I did some more research on this last night, and I found [_[COLOR="Blue"]an interesting article on replacing Nautilus in GNOME]("http://www.psychocats.net/ubuntu/nonautilusplease")[/COLOR]_, but it makes the changes globally (for all users), which is not what I need.

However, it got me thinking:
[LIST]
[*]Step 1) **What if I mess around with GNOME so that none of the Nautilus components load for any user**?
[*]Step 2) **What if I then manually load all the Nautilus components** for every other user (except the one I want to limit access) **using** their $HOME/**.gnomerc files**?
[*]Step 3) And **what if I then edit that one user's $HOME/.gnomerc file to load the VMware player INSTEAD of Nautilus**?
[/LIST]

[LIST]
[*]Is this feasible?
[*]How would I implement step 1?  Maybe by deleting or renaming some of the following files from /usr/share/applications so that they do not load by default:
[LIST=1]
[*]nautilus.desktop
[*]nautilus-computer.desktop
[*]nautilus-folder-handler.desktop
[*]nautilus-home.desktop
[/LIST]
[*]How would I then implement step 2? What would I have to put in $HOME/.gnomerc for most users to make Nautilus load somewhat normally?
[*]I think I can handle step 3.  I would just make an executable shell script as $HOME/.gnomerc for the user with the limited access, place a line in it to load VMware Player with the correct VM, and NOT load any Nautilus components, right (or would I need some of them)?
[/LIST]

If I am on track, can someone help me implement this?

If I am way off-base, can someone set me straight?

Thanks again!

---

### Post by chriv on 2007-08-06
**[COLOR="Red"][SIZE="4"]OK.  I created a solution that is VERY CLOSE to what I need.[/SIZE][/COLOR]**

**I can put a [COLOR="Blue"].gnome2/session[/COLOR] file in the user's $HOME directory with the following contents:**
```
[Default]
0,id=117f000101000118644313100000015680000
0,RestartStyleHint=2
0,Priority=60
0,Program=VMware Player
0,CurrentDirectory=/home/jessica
0,CloneCommand=vmplayer
0,RestartCommand=vmplayer -X /home/user/vmware/UserVM.vmx
num_clients=1
```
**[COLOR="Red"][SIZE="4"]This makes the user start with ONLY VMware Player running (in full screen mode), with no nautilus, no gnome desktop, no panels, no menus, no volume control, etc.[/SIZE][/COLOR]**

Please note that I did this COMPLETELY without documentation on the .gnome2/session file, and only by experimenting with it. :)  There is probably a better config than this.  Anybody that is more familiar with Gnome sessions, please feel free to contribute.  Remember that the end goal is to give the user a login that ONLY provides them with access to the VM in vmplayer (and nothing else), but will return to the login screen if vmplayer ends.

[B][SIZE="4"][COLOR="Red"]The only problems:
1) There is no way for the user to log out of their X session (but at least they cannot use it either).
2) Ideally, closing VMware Player would end the user's X session and return them to the login screen (but this doesn't happen either).  Instead closing VMware Player gives the user a completely unusable desktop (AFAIK)![/COLOR][/SIZE][/B]

**This is SO CLOSE to what I need**.  I guess I'm going to have to write a bash script to check to see if an x-session is currently running for the user without vmplayer running.  If so, it should kill the xsession.  Then I guess I should make it a cron job, so that it will run periodically (I'm too lazy and don't have the linux skills yet to make the script a daemon).

**[SIZE="5"][COLOR="Red"]Anybody have any suggestions for an easy will to tell the x-session to end for the user if vmplayer exits?[/COLOR][/SIZE]**

---

### Post by MMoudry on 2007-08-07
well my suggestion would be running a shell script in background every 3 seconds that checks the output of 'ps -A' and terminates the session if no VMWare is found.

 However I am sure there is more proper way to do this with some sort of process hooks. 

I am almost sure that the process manager can execute actions when an event happends (ie a flagged process exits). This way it would just terminate the session when vmware exits. hmmm need to do more research on this.... 

Another way would be to use a wrapper. Spawn a parent process that spwans vmware as a child process once the user logs in. Once VmWare exits the parent process kills the session, hmmm another research subject....

MM

---

### Post by weblordpepe on 2007-08-07
Yesss I'm the first one to say it!

Control + Alt + Backspace

That will restart X, and put you back to the login screen.

---

