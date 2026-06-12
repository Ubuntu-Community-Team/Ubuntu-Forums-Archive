---
title: "Not able to change desktop wallpaper 14.04"
date: 2014-12-02
forum: Desktop Environments
---

### Post by Evan I S on 2014-12-02
[COLOR=#000000][FONT=Arial]Greeting!

As titled I have an issue in changing desktop wallpaper.  Followings are I have tried but no success.
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
#Try with [/FONT][/COLOR][COLOR=#000000][FONT=Arial]command line [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]gsettings set org.gnome.desktop.background picture-uri file:///home/serrano/Pictures/y.jpg[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]h[/FONT][/COLOR][COLOR=#000000][FONT=Arial]ttp://askubuntu.com/questions/66914/how-to-change-desktop-background-from-command-line-in-unity[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]#Try with app called  "Wallch" [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]http://melloristudio.com/wallch/

#Try reinstall ubuntu desktop
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get install --reinstall ubuntu-desktop[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get update

What else I should try to get it done?  I look forward to hearing from you![/FONT][/COLOR]

---

### Post by Hansiman on 2014-12-02
Are you certain that your file-path is correct? Could you copy in the exact phrase you use?

---

### Post by Evan I S on 2014-12-02
@Hansiman Yes the path is alright!  Matter is making no effect when applying to change the wallpaper.  Simply right click on a png file from the pop up menu I chose " set as desktop background ".  Does not work.  I believe something to do with system setting.  May something have been corrupted.

---

### Post by grahammechanical on 2014-12-02
> [COLOR=#000000][FONT=Arial]gsettings set org.gnome.desktop.background picture-uri file:///home/serrano/Pictures/y.jpg[/FONT][/COLOR]

That is not the correct command for you. That was the correct command for the person that gave the answer on AskUbuntu. HIs/her user name is "serrano."

You need to have an image in the Pictures folder. Which is in your /home/username folder. 

> [COLOR=#000000][FONT=Arial]gsettings set org.gnome.desktop.background picture-uri file:///home/UserName/Pictures/ChoosenImage.jpg[/FONT][/COLOR]

You must substitute UserName for your user name and substitute ChoosenImage for the name of the image that you want to make the desktop background.

But I am sure that if we put an Image in the Pictures folder and then use System Settings>Appearance and click on the panel that says Wallpapers and change it to Pictures Folder, then any images in the Pictures Folder will be available to select as a desktop background.

If we want to create a background slide show of our own images then we use something like Wallch.

Ubuntu Desktop Guide (Help) under the heading Change the Desktop Background

> [FONT=Arial][COLOR=#000000]Select the Pictures folder to use one of your own photos from your Pictures folder. Most photo management  applications store photos there.[/COLOR][/FONT]

Regards.

---

### Post by Evan I S on 2014-12-02
@grahammechanical  Thank you for your reply.
1. Yes I did according to path my picture stored folder.  I am using Firefox as file explorer so I am familiar with the command file://.
2. System Settings>Appearance and click on a picture I want to set as desktop wallpaper does not make effect.  I remember by click on the photos immediately background changes. But now doesn't 
3. Wallch I tried in a hope of switch on the function I lost.  But doesn't help.
I suspect that accidentally the function disabled I try to find with dconf editor under gnome such menu but I could not find any related.

---

### Post by Hansiman on 2014-12-02
Do you currently have a wallpaper now, or is your background just black or white?

---

### Post by Evan I S on 2014-12-02
@Hansiman I have it the one originally equipped.

---

### Post by buzzingrobot on 2014-12-02
Have you log out and in?  I've noticed that new wallpaper is sometimes not applied unless I do that.

---

### Post by Evan I S on 2014-12-02
@buzzingrobot I have been had this issue for few weeks.  During that time I did multiple times of rebooting and log out and in :-)

---

### Post by buzzingrobot on 2014-12-02
Hmmm.  What are the permissions on the files?  I just checked here.  If I remove Read permissions on a file, it won't be set as the background. Permissions on image files here look like this:>  -rw-r--r--

---

