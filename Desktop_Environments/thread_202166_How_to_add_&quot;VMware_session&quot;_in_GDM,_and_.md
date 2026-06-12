---
title: "How to add &quot;VMware session&quot; in GDM, and run it in fullscreen ?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by patrick295767 on 2006-06-22
How to add "VMware session" in GDM, and run it in fullscreen ?
  
The idea is that the user can choose kde, gnome or vmware.;) 
  
Thank you.

---

### Post by scxtt on 2006-06-22
where is the VM running?  i don't see why you couldn't XDMCP into a VM that's running on a server (and that's properly configured for XDMCP) ...

---

### Post by bluevoodoo1 on 2006-06-22
I did a quick little thing and it seems to work. 

```
sudo gedit /usr/share/xsessions/vm.desktop
```

paste this in
```

[Desktop Entry]
Encoding=UTF-8
Name=VMware
Comment=vmware
Exec=vmware
Terminal=False
TryExec=vmware
Type=Application

```

Load up your OS, then hit ctrl+alt+enter to go fullscreen, ctrl+alt to leave full screen. Exit vmware to leave the session.

---

### Post by mhancoc7 on 2006-06-23
Works perfect!!!
```
[Desktop Entry]
Encoding=UTF-8
Name=Windows XP
Comment=vmware
Exec=vmware
Type=Application
```
Is there are way to automatically start a guest os. I have a panel button set up with the following code. It work great, but does not work with the gdm login.
```
vmware "/home/mhancoc7/vmware/Windows XP Professional/Windows XP Professional.vmx"
```
Does anyone have any ideas?

Jereme

---

### Post by bluevoodoo1 on 2006-06-23
[QUOTE=mhancoc7]Does anyone have any ideas?[/QUOTE]

I tried something out for you. I did it with Fedora Core 5 on vmware as an example, should be the same steps for XP, just change the paths and such.

```
gedit .vmfc5
```
paste this in:
```

#!/bin/sh

exec vmware /home/bluevoodoo1/vmware/fc5/fc5
```

```
chmod +x .vmfc5
```

then the xsession:
```
sudo gedit /usr/share/xsessions/vmfc5.desktop
```

```
[Desktop Entry]
Encoding=UTF-8
Name=VMwarefc5
Comment=vmware
Exec=/home/bluevoodoo1/.vmfc5
Terminal=False
TryExec=/home/bluevoodoo1/.vmfc5
Type=Application
```

I tested it and it seems fine. You still have to "connect," but it will be the only OS available.

EDIT: you can write 
```
vmware /home/mhancoc7/vmware/Windows\ XP\ Professional/Windows\ XP\ Professional.vmx
```
instead of 
```
vmware "/home/mhancoc7/vmware/Windows XP Professional/Windows XP Professional.vmx"
```  (I don't know how the quotes will be in the script)

---

### Post by mhancoc7 on 2006-06-23
You are awesome!!!

I set up vmware to automatically Power on XP when it is launched. Now I can select Windows XP from the GDM session list and Windows XP starts in fullscreen. To exit I simply shut down Windows and then click File>Exit from the Vmware menu. I am then returned to GDM. AWESOME!!!!

Thanks, Jereme

---

### Post by patrick295767 on 2006-06-23
[QUOTE=mhancoc7]You are awesome!!!

I set up vmware to automatically Power on XP when it is launched. Now I can select Windows XP from the GDM session list and Windows XP starts in fullscreen. To exit I simply shut down Windows and then click File>Exit from the Vmware menu. I am then returned to GDM. AWESOME!!!!

Thanks, Jereme[/QUOTE]
  
I confirm !!
  
This is AWESOME !!!
VMware is sooo fast under this GDM. 
 
I installed a windows, vmware tools. That's really great thing.
the script is also working. The users have **directly** the vmware and windows in fullscreen when vmware session selected. :KS
 
This is better than wine since wine is taking looooot of CPU for simple tasks. 
  
Thank you again for your great reply & help !

---

### Post by patrick295767 on 2006-06-23
Additional thing:
 
In order to give users the recommandation of using linux desktop instead of windobe, I made small changes in the :
/etc/gdm/gdm.conf:
```

DefaultSession=fvwm
```

and

```
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode where
# the session saving stuff is disabled in GDM
ShowLastSession=false
```
  

That is it !! Everthg working great !
 Thank you !
:KS Ubuntu Linux is Fast & Great !! :KS

---

### Post by txmail on 2006-06-23
If there was a way to just start XP and once finished have VMWare close out automatically; that would be truly awesome. Think of the possiblilites; and not just for running Windows; a bare install of X with options for other OS's. My NX! clients just got more powerful anyway...

---

### Post by bluevoodoo1 on 2006-06-23
I'm glad it's working out for you all. It was a good idea [patrick295767] to begin with. 

Many, if not most, programs can be run like this. I've done it before with epsxe emulator and a few other games. And if there is another feature you'd like to start along with vmware simply add it to the script:

```

#!/bin/sh

gnome-settings-daemon &
exec vmware /home/bluevoodoo1/vmware/fc5/fc5

```

---

### Post by temcat on 2006-06-23
Isn't it roughly equivalent to dual booting? I just wonder what's the point of it...

---

### Post by patrick295767 on 2006-06-23
[QUOTE=temcat]Isn't it roughly equivalent to dual booting? I just wonder what's the point of it...[/QUOTE]
  
Schools are using this sometimes :)

---

### Post by patrick295767 on 2006-06-23
[QUOTE=txmail]If there was a way to just start XP and once finished have VMWare close out automatically; that would be truly awesome. Think of the possiblilites; and not just for running Windows; a bare install of X with options for other OS's. My NX! clients just got more powerful anyway...[/QUOTE]
  
This is indeed nice idea. 
You can make use of your samba server to mount the user folders.
  
Concerning  the windows95, Windwos98, WindowsMe, and FreeBSD, you cannot make use of the functionallity of the SHARED FOLDER option of VMware unfortunately. 
I would recommand to use the SAMBA if you make use of these OS's. 
  
Concerning quitting automatically the VMware & returning to GDM, this is very possible. This was working for me before with vmware 4. I am trying to figure out how ... 
    
  
(Wine is not ""emulating"" everthg and can sometimes be too slow, so VMware can then be useful to be still under our great Ubuntu Linux.)

Greetigns to bluevoodoo1 & mhancoc7 ! :KS

---

### Post by mhancoc7 on 2006-06-23
This is very awesome. It is much better than dual booting. This way if I decide to trash windoze I simply delete the windoze folder and voila it is gone. No resizing the partition. I have also added all my emulators (znes, gfceu, stella, mupen, supertux) to the GDM list.

Thanks to all, Jereme

---

### Post by patrick295767 on 2006-06-23
[QUOTE=mhancoc7]This is very awesome. It is much better than dual booting. This way if I decide to trash windoze I simply delete the windoze folder and voila it is gone. No resizing the partition. I have also added all my emulators (znes, gfceu, stella, mupen, supertux) to the GDM list.

Thanks to all, Jereme[/QUOTE]
  
That's a good idea too !! Thank you !
 
I added samba to let users have their personal data.
  
Let's trash windozze partition's forever  !! :-)

---

### Post by AndyCooll on 2006-06-28
Just want to ask what is the difference between this and the "Full Screen" button in VMware Server?

---

### Post by Dubbayoo on 2006-06-28
[QUOTE=AndyCooll]Just want to ask what is the difference between this and the "Full Screen" button in VMware Server?[/QUOTE]

I believe they want to login directly to the vmware guest from gdm instead of logging into gdm then opening vmware.

---

### Post by mhancoc7 on 2006-06-28
Yes this lets you select "Windoze XP" from your GDM Sessions list. It will then load Vmware and automatically launch "Windoze XP" in fullscreen. It runs really fast.
Jereme

---

### Post by patrickfromspain on 2006-07-03
just wanted to say: that's nice!

Thanx for the tips!

---

### Post by patrick295767 on 2006-07-04
[QUOTE=patrickfromspain]just wanted to say: that's nice!

Thanx for the tips![/QUOTE]
  
Some schools in US and Europe use this functionality to give possibility to students to use either linux or windoze.
Then, You get a much faster Windoze OS (in fullscreen), and have the "windoze /home" (e.g. net use) via using the Samba of the Main Server of the School. 
 
Then, you can totally change the gdm, and put two icons box only : LINUX or Windows ... That's another story...

Greetings

---

### Post by Crashmaxx on 2006-07-05
Wow, this is a really cool idea. Now I don't know much about sessions in ubuntu, mainly because I usually just run ubuntu and nothing else. So can you leave a session running and switch to another? Cause it would be really nice to be able to run XP in one session and switch to ubuntu without shutting it down. You know, leave something running in XP, like TiVo desktop, and pop back to ubuntu and do other stuff.

Now I know I can just run vmware in ubuntu like I do now and do this, and this will run slower. But it all would look a lot slicker to just switch back and forth then run it in a window. And when I just run one or the other it will be faster.

Anyway, sorry to go off topic, but I bring all this up because I have a dual boot with XP right now and XP doesn't really work. Something loading on start-up freezes it up. So I would like to remove it and everything on my hard drive and do a fresh install of ubuntu. Then maybe run the saved files from the XP partition in vmware like this. I think I might have to save it to a separate partition though. Maybe I will keep the grub too and make another partition with a backup of ubuntu for when I mess it up. I don't know yet, but I want something different.

---

### Post by patrick295767 on 2006-07-06
[QUOTE=Crashmaxx]Wow, this is a really cool idea. Now I don't know much about sessions in ubuntu, mainly because I usually just run ubuntu and nothing else. So can you leave a session running and switch to another? Cause it would be really nice to be able to run XP in one session and switch to ubuntu without shutting it down. You know, leave something running in XP, like TiVo desktop, and pop back to ubuntu and do other stuff.

Now I know I can just run vmware in ubuntu like I do now and do this, and this will run slower. But it all would look a lot slicker to just switch back and forth then run it in a window. And when I just run one or the other it will be faster.

Anyway, sorry to go off topic, but I bring all this up because I have a dual boot with XP right now and XP doesn't really work. Something loading on start-up freezes it up. So I would like to remove it and everything on my hard drive and do a fresh install of ubuntu. Then maybe run the saved files from the XP partition in vmware like this. I think I might have to save it to a separate partition though. Maybe I will keep the grub too and make another partition with a backup of ubuntu for when I mess it up. I don't know yet, but I want something different.[/QUOTE]
  
You have to get into your /etc/gdm/gdm.conf:

```
[servers]
# These are the standard servers.  You can add as many you want here
# and they will always be started.  Each line must start with a unique
# number and that will be the display number of that server.  Usually just
# the 0 server is used.
0=Standard
1=Standard
```
 to get your two sessions.

Greetings !!
  
==
btw, vmare run faster if you select the whole disk (genuine partitiions) than virtual one (file).

---

### Post by Dubbayoo on 2006-07-09
> **bluevoodoo1 said:**
> I tried something out for you. I did it with Fedora Core 5 on vmware as an example, should be the same steps for XP, just change the paths and such.

```
gedit .vmfc5
```
paste this in:
```

#!/bin/sh

exec vmware /home/bluevoodoo1/vmware/fc5/fc5
```

```
chmod +x .vmfc5
```

then the xsession:
```
sudo gedit /usr/share/xsessions/vmfc5.desktop
```

```
[Desktop Entry]
Encoding=UTF-8
Name=VMwarefc5
Comment=vmware
Exec=/home/bluevoodoo1/.vmfc5
Terminal=False
TryExec=/home/bluevoodoo1/.vmfc5
Type=Application
```

I tested it and it seems fine. You still have to "connect," but it will be the only OS available.

EDIT: you can write 
```
vmware /home/mhancoc7/vmware/Windows\ XP\ Professional/Windows\ XP\ Professional.vmx
```
instead of 
```
vmware "/home/mhancoc7/vmware/Windows XP Professional/Windows XP Professional.vmx"
```  (I don't know how the quotes will be in the script)



I can't get this part to work. Here is my setup:

**my desired VM**
/data/vmware/virtual_machines/Tiny XP Professional/Windows XP Professional.vmx


**My xsession**
steve@ubu:~$ more /usr/share/xsessions/vm.desktop
[Desktop Entry]
Encoding=UTF-8
Name=VMware
Comment=vmware
Exec=/home/steve/.vmxp
Terminal=False
TryExec=/home/steve/.vmxp
Type=Application


**My script**
steve@ubu:~$ more .vmxp
#!/bin/sh

exec vmplayer /data/vmware/virtual_machines/Tiny\ XP\ Professional/Windows XP Professional.vmx

---

### Post by bluevoodoo1 on 2006-07-09
> **Dubbayoo said:**
> I can't get this part to work. Here is my setup:

**my desired VM**
/data/vmware/virtual_machines/Tiny XP Professional/Windows XP Professional.vmx


**My xsession**
steve@ubu:~$ more /usr/share/xsessions/vm.desktop
[Desktop Entry]
Encoding=UTF-8
Name=VMware
Comment=vmware
Exec=/home/steve/.vmxp
Terminal=False
TryExec=/home/steve/.vmxp
Type=Application


**My script**
steve@ubu:~$ more .vmxp
#!/bin/sh

exec vmplayer /data/vmware/virtual_machines/Tiny\ XP\ Professional/Windows XP Professional.vmx

Did you make your .vmxp script executable?
```
chmod +x .vmxp
```

and also there are a few spaces that need \ after them. Like this...
```
exec vmplayer /data/vmware/virtual_machines/Tiny\ XP\ Professional/Windows\ XP\ Professional.vmx
```

---

### Post by Dubbayoo on 2006-07-09
It was the spaces that I missed. Thanks a lot.

---

