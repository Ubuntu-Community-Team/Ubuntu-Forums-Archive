---
title: "Missing Top Menu Bar"
date: 2009-08-03
forum: Desktop Environments
---

### Post by dm_fw on 2009-08-03
Under XUBUNTU 9.04 (Desktop/i386) the top menu bar has disappeared for my main user.  I tried to click around the screen, right mouse click, etc. but I can not make the bar reappear.  Can I recover the bar or is this a bug requiring a re-install? 


I am not sure if this is my mistake or an issue with updates.

---

### Post by gettinoriginal on 2009-08-03
Two things to try: First, push your mouse curser against the top of the screen for 1 second to see if you panel pops down, it may be set to autohide.  If it does come down, right click on it and choose properties and uncheck autohide.  If that does not work, look to see if there is a small grey box in the upper right or left corner, if so, click on it, and the panel should reappear, these are your hide buttons, the panel may be hidden to the left or right.
[ATTACH]123512[/ATTACH]

---

### Post by lvleph on 2009-08-03
You can also create a new panel. Right click on an existing panel and then click new panel. From there you can right click the new panel and click add to panel.

---

### Post by rr1024 on 2010-01-05
This has now happened to me, there is now drop down for the menu bar and there is no 
"small grey box in the upper right or left corner"

I can't launch anything, lucky I had firefox on the desktop or I wouldn't even be able to launch the internet....

does anyone know how or why this can occur it seems like this should be impossible to do....This is something that I have come to expect from windows not linux...lol

---

### Post by Timbot2000 on 2010-01-05
Ist bad, Have the same thing. No top or bottom panel, and I have networking issues too and cannot access the Network Manager (Why is this not accessible anywhere except the panel????!!!). Tried upgrading to 9.10, but the bizarre behavior of XFCE just migrated along with it. 
rm -rf is unavailing.

---

### Post by bobcollard on 2010-01-06
> **Timbot2000 said:**
> Ist bad, Have the same thing. No top or bottom panel, and I have networking issues too and cannot access the Network Manager (Why is this not accessible anywhere except the panel????!!!). Tried upgrading to 9.10, but the bizarre behavior of XFCE just migrated along with it. 
rm -rf is unavailing.
Right click your desktop.  In the menu go to Applications/Settings/Panel  Add whatever panels that are missing and then add whatever icons you need to make it work for you.

---

### Post by sebistilp on 2010-01-11
i have the same problem in Xubuntu 9.10, i can not ad a menu bar on my desktop, if i want to open panel it wont open, i don't know how to ad the menu bar on my desktop

---

### Post by bobcollard on 2010-01-11
> **sebistilp said:**
> i have the same problem in Xubuntu 9.10, i can not ad a menu bar on my desktop, if i want to open panel it wont open, i don't know how to ad the menu bar on my desktop

When you "right click" on the desktop do you get a menu?  This menu should have: "Applications> that leads to: Settings> which leads to:  Panel"   I've been using Xubuntu for awhile and it works for me.  I'm not sure why you are losing your panels?  I know you can make it invisible by changing the settings for Transparency, or have it auto hide, but, to remove it completely you would have to be aware you were doing that.  I am completely up to date with 2.6.31-17 kernel.  It can't be from any update I'm aware of.

---

### Post by fontman on 2010-02-15
[SIZE=2][COLOR=Navy]A temporary solution is to create an additional session 

Right click, *Applications, Settings, Session and Startup*, check *Display chooser on Logon*, and also *Automatically Save Session on Logout*.

I have not found a way to allow the additional session to load automatically, but this should suffice until the problem is fixed.[/COLOR][/SIZE]

---

### Post by redcrystalmoon on 2010-02-21
...

---

### Post by bobcollard on 2010-02-21
> **redcrystalmoon said:**
> I'm also missing my top ( and only) menu bar. .
I don't have an answer to your problem.  The one time I removed too many panels I got mine back using the desktop, see screenshot.  Since then I have used Cairo Dock for most of my applications and leave the panel hidden.
Edit: the picture is blurry because it was taken with my cell phone, desktop menu bottom left with Appllcations at the bottom highlighted.

---

### Post by denham2010 on 2010-02-22
Xfce, unlike Gnome, allows you to run your desktop without any panels at all (very handy if using a dock replacement such as AWN, Cairo Dock, Gnome Do etc).

If all your panels are gone, the panel settings from the menu will not work as xfce4-panel is not running.

Here is your fix:

1. Either press ALT + F2 or in a terminal, enter the following:
```
xfce4-panel &
```

This will re-start your panels and now the panel settings option will work to allow you to configure them.

2. To ensure the panels start on start-up:
 - Close ALL running applications you do not wish to auto-start.
 - Open Settings manager and go to Session & Start-up
 - In the General Tab, under Logout Settings, tick Automatically Save Session On Logout
 - Re-start your computer.
 - Open Settings Manager and un-tick the Auto Save option.
 - Re-start your computer again.
(You need to do the 2nd re-start otherwise, anything you open while in this session will still be remembered for auto start.)

Your panels should now start on log-in.

Cheers.

---

### Post by pndragon on 2010-03-09
Thanks, man! Just what I needed.

---

### Post by edanto on 2010-06-29
I have the same problem - I rather stupidly right clicked on the top bar and clicked remove panel (thinking it would just remove part of the whole bar), and now the top of my screen is completely empty, just all desktop.

No hidden bar, nothing in the corners.

I'm using Ubuntu 10.04, and the command xfce4-panel & doesn't work for me (I didn't think it would since I'm using Gnome)

Does anyone know, please, the correct command for Ubuntu?

thanks

---

### Post by Aisteru on 2010-07-17
First @edanto, you typed that the top of your screen was all desktop. If you have any other gnome panels (at the bottom of your desktop maybe), right-click on one, in a bare spot, and you should see an "new panel option. That should be what you want. After that, right-click on the new panel & add the applets you want.
   I do not think gnome will let you delete all your panels.

As to the main question, you could also right-click the desktop, go to Applications>Settings>Xfce settings, click on Session and Startup, and add Xfce panel.

I hope this helps someone. 

A candle looses nothing by lighting another candle.

---

### Post by edanto on 2010-07-17
Thanks very much.

I actually solved the problem of the missing top menu bar using exactly what you are suggesting.  But I had started another thread about it and didn't update this one with the good news.

The main problem now is that I can't get the network manager icon to re-appear.  Someone in the other thread suggested something but it didn't work.  

If you have any ideas, I'd be grateful if you could have a look at [http://ubuntuforums.org/showthread.php?t=1526816](http://ubuntuforums.org/showthread.php?t=1526816)  

cheers

---

### Post by hdoan48 on 2010-10-16
> **bobcollard said:**
> When you "right click" on the desktop do you get a menu?  This menu should have: "Applications> that leads to: Settings> which leads to:  Panel"   I've been using Xubuntu for awhile and it works for me.  I'm not sure why you are losing your panels?  I know you can make it invisible by changing the settings for Transparency, or have it auto hide, but, to remove it completely you would have to be aware you were doing that.  I am completely up to date with 2.6.31-17 kernel.  It can't be from any update I'm aware of.

I also have a similar problem. I'm a long time Windows user and have some knowledge with HP and Solaris Unix. Recently I have decided to try Ubuntu. As I wanted a stable version, I installed Ubuntu 10.04 on a Compaq Deskpro EN, Pentium 3, 900Mhz and 512 MB memory. My monitor is a Samung Syncmaster 216BW with native resolution of 1680x1050. 
The installation completed successfully but after the first reboot I started to get the 2 errors:

error: no suitable mode found
error: unknown command 'terminal'.

and the system would continued to boot up to the logon screen. After I logon, the Desktop is empty with no Top Menu or Bottom Menu.  The background is OK and if I right click on the desktop, I got a menu with 7 options: Create Folder, Create Launcher, Create Document, Cleanup By Name, Keep Aligned (selected), Paste (inactive) and Change Desktop Background.
I can also press alt-F2 to enter a command, or press ctrl-alt-F1 to get to terminal mode. So everything seems to be functional but there is no Menus or Icons on the Desktop.
However, I have discovered the following situation: at the login screen, after I click on my user-id to , the password field is displayed and a menu bar is now displayed at the bottom of the screen with 3 options: Language, Keyboard and Sessions. The default value for Sessions is GNOME. The 2 other values for Sessions are Failsafe Gnome and Xterm. If I change the Sessions value to Failsafe Gnome then logon, then after I logon I will have a normal desktop with Top Menu bar and Bottom Menu Bar. But if I logon with the default GNOME value for Sessions then I will get no menu bars or icons on the desktop.
I have tried several suggestions in this forum to modify file /etc/default/grub to change the resolution from 640x480 to  1680x1050 and execute sudo update-grub but this doesn't solve the problem.
Can anyone help please ?

---

### Post by bobcollard on 2010-10-17
hdoan48,  Sorry, but, your problem is with Ubuntu (Gnome) not Xubuntu  (XFCE) and yes there is a difference.  You should start a new thread.

---

### Post by hdoan48 on 2010-10-17
> **bobcollard said:**
> hdoan48, Sorry, but, your problem is with Ubuntu (Gnome) not Xubuntu (XFCE) and yes there is a difference. You should start a new thread.
 
Thank you very much Robert. With the information found on this forum, I have managed to make the top and bottom menu bars re-appear, the screen resolution is 1680x1050. Everything seems to be working fine. However the following error messages
 
error: no suitable mode found
error: unknown command 'terminal'.

still appear at boot time. I can live with this for now and will find ways to get rid of them.

---

### Post by bobcollard on 2010-10-17
No suitable mode found is due to the fact that your screen resolution is not set until you login.  It is probably 1024x768.  I have that, but, I have an external screen running on a laptop and I just think it is normal.  Supposedly you can change the resolution of your boot screen, I don't bother.  As for Terminal?  I don't know unless you have something calling for terminal at startup.  Hope this helps.

---

### Post by hdoan48 on 2010-10-18
> **bobcollard said:**
> No suitable mode found is due to the fact that your screen resolution is not set until you login. It is probably 1024x768. I have that, but, I have an external screen running on a laptop and I just think it is normal. Supposedly you can change the resolution of your boot screen, I don't bother. As for Terminal? I don't know unless you have something calling for terminal at startup. Hope this helps.
 
As I'm experimenting Linux on my old Compaq Deskpro EN, I have removed Ubuntu 10.04 from the machine and tried to install Linux Mint 9. On Mint, I got an additional message "error: no video mode activated", even if I have modified /etc/default/grub to add option i915.modeset=1. I know that Linux Mint 9 is based on Ubuntu 10.04, therefore I think that's normal. Well, I think that I should live with these annoyed messages if I want to continue to play with Linux to get some more experience. I'm just wandering why Linux cannot set something by default like Windows that will make the installation complete normally even with a lower resolution or less optimal video support, then allows the user to install a more appropriate driver after the system is installed.
Thank you for your help.

---

