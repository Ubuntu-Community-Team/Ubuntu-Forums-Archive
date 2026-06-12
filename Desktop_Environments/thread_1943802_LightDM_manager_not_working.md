---
title: "LightDM manager not working?"
date: 2012-03-20
forum: Desktop Environments
---

### Post by Tornikee on 2012-03-20
I have this little issue with LightDM manager - I can't run the app from the dash (it doesn't appear while typing 'lightdm', despite the app being installed and visible both in Synaptic and in Software Manager), and also the Ubuntu user login screen doesn't show the current desktop wallpaper (though I did choose that option in Ubuntu Tweak), it's just plain black.

---

### Post by grahammechanical on 2012-03-20
LightDM is a display manager. It provides the login screen on Ubuntu 11.10. Once we log in LightDM hands over control to the desktop environment and its windowing manager. In 11.10 that is Gnome 3 and Compiz and Unity. LightDM is not something that you can run from the Dash.

On the other hand, I am aware of something called Simple LightDM Manager that is a little utility that lets you select your own background image for the LightDM background screen.

Is this what you are referring to? That you can run from the Dash by typing Simple or Simple LightDm Manager. 

I use to use it myself.

---

### Post by Tornikee on 2012-03-20
Thank you for clarifying. Yes it should've been Simple LightDM Manager that I used to use. But then its absence wouldn't lead to the issue with login screen I described, so it's probably caused by some other reason?

---

### Post by grahammechanical on 2012-03-20
Hi. again.

I have used Simple LightDM Manager and I have just tested what I am about to say on an 11.10 install and a 12.04 install.

In 11.10 there are two ways to change the background image for the LightDM/login screen.

1) Used Simple LightDM Manager.

2) Manually edit a configuration file.

In 12.04 it is much simpler. All we do is select a static background image as a wallpaper and it becomes the background image for the LightDM/login screen. If you have more than one user, then each user can select their own wallpaper and when they click on their username at the login screen the background image will change to that of their selected wallpaper.

This does not work if we use the wallpaper slideshow. Then the lgoin background image will be the default image which is called warty-final-ubuntu.png

You will find all the wallpapers in file system /usr/share/backgrounds.

If you go to file system /etc/lightdm you will find a file called unity-greeter.conf if you open that file in text editor (Gedit) you will see this line:

> background=/usr/share/backgrounds/warty-final-ubuntu.png

That is the line that decides what image will be the default image when we use the wallpaper slideshow.

In 12.04 if I go to file system /var/lib/AccountsService/users I see a file called by my user name. When I open that file with the text editor I see this line:

> Background=/usr/share/backgrounds/Small_flowers_by_Dariusz_Duma.jpg

That is the static background image that I am using and which is now the login background image. This setting overrides the setting in /etc/lightdm/unity-greeter.conf.

This is what I have in my 12.04 /var/lib/AccountsService/users/myusername file:

> [User]
XSession=ubuntu
XKeyboardLayouts=gb	extd;gr	extended;
Background=/usr/share/backgrounds/Small_flowers_by_Dariusz_Duma.jpg

This is what I have in my 11.10 /var/lib/AccountsService/users/myusername file:

> [User]
Language=en_GB
XSession=ubuntu

Do you see how it is possible to edit this file in 11.10 and set the background image that you want for the LightDM/login background?

If you decided to edit these files you need to run the Gedit with the command

> gksudo gedit

That will let you edit those files with administrator privileges, which you will need. When you save the file you may find that Gedit has saved a copy of the file as backup by putting the tilde character ( ~ ) at the end of the file name. This will make the file a hidden file that cannot be seen by File Manager unless you have selected Show Hidden Files. This backup file will need to be deleted as it may cause conflicts.

Regards.

---

### Post by Tornikee on 2012-03-21
Thanks for the replies. I just installed Simple LightDM Manager and used it to set login screen again.

---

