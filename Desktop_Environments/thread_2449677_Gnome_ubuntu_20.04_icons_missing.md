---
title: "Gnome ubuntu 20.04 icons missing"
date: 2020-08-31
forum: Desktop Environments
---

### Post by kingpenguin on 2020-08-31
I want to start off by saying that if I click on the deal on the bottom of the icon bar to show all of your  applications I have an icon for my application f5vpn. When I look at the top right of my task bar next to my wifi icon, sound and the power button I see the icon as well. When I go into by browser and go to the web portal to connect to my vpn I get a spot on the application bar but it does not have an icon at all. This is telling me that the icon's are there but for some reason when executing it from the web site (There is no way to just launch the application as it just closes if not opened by the web browser) it does not have an icon. This is an .deb installer for this application and also states ubuntu support for the f5vpn. Can someone help me what I can try to get this fixed?

---

### Post by kingpenguin on 2020-08-31
I wanted to add a picture for some context. 
[IMG]https://i.imgur.com/nM44I39.png[/IMG][IMG]https://i.imgur.com/727wCvI.jpg[/IMG]

---

### Post by monkeybrain20122 on 2020-08-31
You need to make a .desktop file for it. You can look at any .desktop file in /usr/share/applications to get the template. You used to be able to just put the .desktop file in ~/.local/share/applications and make it executable then the "icon" will show, but since gnome seems to have done some weird things to nautilus I don't know if that still works(I did some tests after installing 20.04 and apparently I couldn't launch .desktop files from ~/.local/share/applications so I just replaced nautilus with nemo and used unity, then got rid of gnome shell) If not then you would have to put the file in /usr/share/applications (needs sudo)

---

### Post by kingpenguin on 2020-09-01
I already do have a .desktop file. it is in /opt/f5/vpn/com.f5.f5vpn.desktop . I am not 100% sure how to tell if the icon is in the location because I am not 100% sure where the icons it is looking for are.
[IMG]https://i.imgur.com/lO1jxvS.png[/IMG]

---

### Post by monkeybrain20122 on 2020-09-01
No, /opt won't work. You have to either copy it or symlink it to /usr/share/applications or /usr/local/share/applications like 

```
sudo ln -s /opt/f5/vpn/com.f5.f5vpn.desktop /usr/local/share/applications/com.f5.f5vpn.desktop
```

If you get a blank box after this then you would have to edit the desktop file ( /opt/f5/vpn/com.f5.f5vpn.desktop) and give the path to the icon in the line 

```
Icon=f5vpn
``` 
change it to
```
Icon=/path/to/icon
```

There should be an icon somewhere in your /opt/f5 folder or one of the subfolders. If not you can just download a picture as the icon, place it somewhere (maybe create a folder called /home/your_username/share/icons) and use that in the Icon= line above.

---

### Post by kingpenguin on 2020-09-01
Sorry, I do not mean to be picky but I just want to make 100% I do this right. I do seem to have a /usr/share/applications/ with *.desktop files in there but I do not have a folder called /usr/local/share/applications . Will the /usr/share/applications folder work or do I need to create one in the location that you stated?

---

### Post by kingpenguin on 2020-09-01
Well I tried to do the /usr/share/applications/com.f5.f5vpn.desktop and changed the image file but I am still having issues. I disconnected the vpn and tried to reconnect but the icon is still black. I am wondering if it has something to with it being opened from a web browser using xdg-open.
[IMG]https://i.imgur.com/2mAJh9s.png[/IMG]
[IMG]https://i.imgur.com/zByBIZW.png[/IMG]
[IMG]https://i.imgur.com/DV2u2EU.png[/IMG]

---

### Post by monkeybrain20122 on 2020-09-01
/usr/share/applications works too. Make sure the .desktop file is executable



You may have to logout and log back in.

---

### Post by kingpenguin on 2020-09-01
I have logged off and rebooted the computer. I am still getting the same issue. I have done a "sudo chmod 755 /usr/share/applications/com.f5.f5vpn.desktop" to make sure it is executable. I will say though that almost none of the other files in this location have executable permission's and they do seem to work as expected? Every other .desktop has the equivalent to chmod 644. Also the part that I am confused with isn't the gnome's application menu populated by the .desktop file? If it was an issue with the .desktop would that icon not show up as well?
[IMG]https://i.imgur.com/QTVeqsa.png[/IMG]
[IMG]https://i.imgur.com/z2d8LGp.png[/IMG]

---

### Post by monkeybrain20122 on 2020-09-01
So if you open the file manager and go to /usr/share/applicatons or  /opt/f5/vpn/ to actually look at the desktop file or its link, do you see the icon?

About the executable bit, maybe you don't need it. Usually I put custom launcher files (.desktop files) in ~/.local/share/applications where it seems that I do need to make them executable, but as said it seems that that location no longer works for gnome shell in Ubuntu 20.04 (but you can try, I no longer have gnome shell or nautilus on this machine)

---

### Post by kingpenguin on 2020-09-01
If you look at my pictures I posted above I took a picture of the file and what I put in the .desktop file in gnome.

---

### Post by kingpenguin on 2020-09-01
Sorry duplicate post because the first time I entered it, I did not see it post correctly

---

### Post by monkeybrain20122 on 2020-09-01
well that seems to be a gnome issue then if the icon shows in the dash but not the dock. Can you pin the launcher to the dock by creating a favourite? (I don't really know, not using gnome shell)

---

### Post by kingpenguin on 2020-09-01
I can but the application is not launched from clicking the program. I have to go to a website and then the website opens the application though xdg-open. If I just click on the icon favorite from the launcher it does nothing because it is not supposed to be opened that way. So now I have one that is not opened but does show the correct icon and still the same black box from when xdg-open opened the application
[IMG]https://i.imgur.com/VUB2s1m.png[/IMG]

---

### Post by monkeybrain20122 on 2020-09-01
You can add a StartupWMClass= to your .desktop file, see if it helps.
[https://askubuntu.com/questions/367396/what-does-the-startupwmclass-field-of-a-desktop-file-represent](https://askubuntu.com/questions/367396/what-does-the-startupwmclass-field-of-a-desktop-file-represent)

---

### Post by kingpenguin on 2020-09-01
Sorry for taking so long to respond but I wanted to try and figure out what you were talking about. I was able to find out the wm_class is 'WM_CLASS(STRING) = "f5vpn", "F5 VPN"". I am not exactly sure how to change this to to do what you are talking about.

---

### Post by monkeybrain20122 on 2020-09-01
Add this line to your .desktop file, see if it works. 
```
StartupWMClass=f5vpn
```

If it still doesn't work I am out of idea.Hopefully someone more knowledgeable will help you to solve your problem.

---

### Post by kingpenguin on 2020-09-01
Ha! you are amazing. This got it working!
[IMG]https://i.imgur.com/icLXWd1.png[/IMG]

---

### Post by monkeybrain20122 on 2020-09-01
wow, glad that it finally works. Now you can go to thread tools and mark the thread as solved.

---

