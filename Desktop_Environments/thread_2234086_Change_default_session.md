---
title: "Change default session"
date: 2014-07-12
forum: Desktop Environments
---

### Post by kari0ca on 2014-07-12
Hi there,
I have kubuntu 13.04 and recently i've made the update of some aplications and after that i only can login at the XBMC session, before this problem, i didn't even realized that i had a session for the XBMC.

So at the desktop environment i only can log in on this session, and i can't use the operating system, only the XMBC application

After that problem happened, i can change to the terminal mode (Ctrl+Alt+F1) at login and see if i could change the session or fix this problem, the thing is i can see the files that have the configuraton of the session, but i can't change them effectively.
for instance: i can see the session files on ~/.kde/share/config/sessions/      kmix and kwin and both seems to be ok.
at /var/lib/AccountsServices/users/  i can see my user file, and there, on the XSession parameter, there is XBMC. If i change this value and reboot my machine, nothing happens
at /usr/share/xsessions  i can see both files: kde-plasma.desktop and XBMC.desktop, so i think that the solution would be to change the session on my user file, but even doing that, after a reboot, the file is changed to have the session XBMC.

How can i change the session effectively?

---

### Post by Bucky Ball on 2014-07-12
Reboot the machine. When you get to the login screen you will find a drop-down menu 'Sessions'. You should be able to choose the correct desktop environment session from that.

---

### Post by kari0ca on 2014-07-14
> **Bucky Ball said:**
> Reboot the machine. When you get to the login screen you will find a drop-down menu 'Sessions'. You should be able to choose the correct desktop environment session from that.That's the problem. I used to have only one session: KDE, but after the update of XBMC, on my login screen i can only see/choose the XBMC session as shown on the image attached.

---

### Post by Bucky Ball on 2014-07-14
Please attach large images by using 'Go Advanced' or 'Adv Reply' and clicking the paperclip icon. Thanks. 

Now that is odd. Where you have your cursor in the screenshot, directly over the 'xbmc' button. What happens when you click it? Do you get a selection of sessions?

---

### Post by kari0ca on 2014-07-14
That's the only session that is displayed to me to select.As i said on the first post, i have 2 sessions on at /usr/share/xsessions, but i can only select XBMC

---

### Post by xc3RnbFO8P on 2014-07-14
Try
> sudo apt-get install --reinstall linux-image-$(uname -r)
and restart

---

### Post by Bucky Ball on 2014-07-15
> **Ringi said:**
> Try

and restart

? Doubt the image has gone anywhere. If going this way, better, and less drastic, would be:

```
sudo apt-get install unity
```

Install the desktop environment again and see if that brings things into shape. Although I doubt Unity has gone anywhere, either. Are you getting a list of kernel options at boot? If not, try hitting shift directly after the BIOS screen at boot and that should bring up the list. You possibly just need to choose the correct kernel.

---

### Post by steeldriver on 2014-07-15
first thing I would check is what desktop sessions are available according to 

```

ls /usr/share/xsessions/

```

---

### Post by xc3RnbFO8P on 2014-07-15
> **Bucky Ball said:**
> ? Doubt the image has gone anywhere.

It just **reinstall** the image, this works for me, I have 9 sessions.

ringi@ringi-Lenovo-Ideapad-Flex-15:~$ ls /usr/share/xsessions/
cairo-dock.desktop    
gnome.desktop                  
gnome-fallback.desktop  
ubuntu.desktop  
xubuntu.desktop
gnome-classic.desktop  
gnome-fallback-compiz.desktop  
kde-plasma.desktop      
xfce.desktop
ringi@ringi-Lenovo-Ideapad-Flex-15:~$

---

### Post by kari0ca on 2014-07-17
> **steeldriver said:**
> first thing I would check is what desktop sessions are available according to ```
ls /usr/share/xsessions/
```As i said on first post, i have 2 files (sessions): XBMC.desktop and kde-plasma.desktop> **Ringi said:**
> It just **reinstall** the image, this works for me, I have 9 sessions.ringi@ringi-Lenovo-Ideapad-Flex-15:~$ ls /usr/share/xsessions/cairo-dock.desktop    gnome.desktop                  gnome-fallback.desktop  ubuntu.desktop  xubuntu.desktopgnome-classic.desktop  gnome-fallback-compiz.desktop  kde-plasma.desktop      xfce.desktopringi@ringi-Lenovo-Ideapad-Flex-15:~$I think that the image that i have is ok, and i dont want to install another desktop environment, i just want to configure KDE to show and use the kde session.but i will try at the weekend the image reinstall.

---

### Post by steeldriver on 2014-07-17
What does 

```

cat /etc/X11/default-display-manager

```

say? it's possible that xbmc has just replaced your display manager with one that only recognizes xbmc sessions - you may need to run

```

sudo dpkg-reconfigure kdm

```

---

### Post by kari0ca on 2014-07-17
> **steeldriver said:**
> What does 

```

cat /etc/X11/default-display-manager

```

say? it's possible that xbmc has just replaced your display manager with one that only recognizes xbmc sessions - you may need to run

```

sudo dpkg-reconfigure kdm

```

```

cat /etc/X11/default-display-manager
 
```/usr/sbin/lightdm

```

sudo dpkg-reconfigure kdm
 
```Package 'kdm' is not installed and no information is available...

---

### Post by kari0ca on 2014-07-17
> **Ringi said:**
> Try
```
sudo apt-get install --reinstall linux-image-$(uname -r)
```
and restart
I've tryed that ad got no result on my problem.

---

### Post by kari0ca on 2014-07-18
```
sudo apt-get install --reinstall kubuntu-desktop
```
That solved my problem.
Now i can choose the session that i want!

---

### Post by Bucky Ball on 2014-07-18
Excellent. Please mark the thread as solved to help others. Good luck. ;)

---

