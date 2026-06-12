---
title: "How to create a desktop shortcut launcher?"
date: 2022-06-02
forum: Desktop Environments
---

### Post by veedub67 on 2022-06-02
Hello,

I'm using 20.04.4 LTS

I'm trying to follow this tutorial to create a shortcut [https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)

When I get to step 3, I don't have the option to 'Paste'

I'm logged in as a user other than root.

Would appreciate advice on what I'm doing wrong, or suggestions on how to troubleshoot.

Thanks
VW

---

### Post by mIk3_08 on 2022-06-03
> **veedub67 said:**
> Hello,

I'm using 20.04.4 LTS
I'm trying to follow this tutorial to create a shortcut [https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)
When I get to step 3, I don't have the option to 'Paste'
I'm logged in as a user other than root.
Would appreciate advice on what I'm doing wrong, or suggestions on how to troubleshoot.

Thanks
VW

You can just create a Ubuntu.desktop file with the command below inside your .desktop file

```
Name=
Comment=
GenericName=
Exec=
Icon=
Type=
Categories=
MimeType=
Actions=
Keywords=
```

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290560&stc=1[/IMG]
Once done save it and put in your desktop. Once successfully created you can launch it then from your desktop to automatically change the desired icon you want to your Ubuntu.desktop file. Regards and Cheers.

---

### Post by vanadium on 2022-06-03
Just paste the .desktop into your "Desktop" folder in your file manager. You get improvements in the handling of desktop icons in 20.04 by disabling the default Desktop Icons extension, and installing Desktop Icons NG, the fork that is used in newer Ubuntu versions (at this time 21.01 and 22.04). In july, when 22.04.01 is released, strongly consider upgrading to 22.04. Gnome Shell has improved very much, also performance wise, and Desktop Icons NG provides a better experience of desktop icons.

---

### Post by mIk3_08 on 2022-06-03
> **vanadium said:**
> strongly consider upgrading to 22.04. Gnome Shell has improved very much, also performance wise, and Desktop Icons NG provides a better experience of desktop icons.
Thanks for the advised vanadium. Yes. I agree. using the latest and new Linux Ubuntu Operating System has a big advantage to it. Good Luck! Regards and Cheers.

---

### Post by veedub67 on 2022-06-03
Hello,

I've upgraded to 22.04

I've also noticed that in /home/user/Desktop 
there is already a desktop file: AIProtector.desktop

for the shortcut that I would like.

Given that the desktop file is already present, any thoughts as to why there is no icon appearing on the desktop?

---

### Post by yancek on 2022-06-03
I used the link you posted to create a Desktop shortcut without problems.  I think you need to go into Nautilus (Files) and open the Desktop directory and paste there.  There should be no reason this would not work, it did for me 

> Given that the desktop file is already present, any thoughts as to why there is no icon appearing on the desktop? 		 .  

So does that mean you have resolved the problem of the link on the Desktop and only need the icon?  Have you tried the standard method, right click the Desktop link, click properties and left click on the generic icon image in the window?  From there you should be able to navigate your system to find an appropriate icon.  If the software you have the link on the Desktop for does not come with a standard Ubuntu install you may have to search for the icon as it may not be in the standard location.

---

### Post by veedub67 on 2022-06-03
> **yancek said:**
> So does that mean you have resolved the problem of the link on the Desktop and only need the icon?

Unfortunately no.

The desktop is blank, apart from the wallpaper.

If I right-click on the desktop I have three options

- Change Background
- Display Settings
- Settings

---

### Post by veedub67 on 2022-06-03
Something else that I have noticed, is that since the upgrade there appears to be a problem with opening Settings.

When I click on Settings an icon appears on the taskbar (for about 1 second) and then it closes. The Settings are not displayed, this was working prior to upgrading to 22.04

---

### Post by veedub67 on 2022-06-03
Well I'm able to open settings via Terminal

Just not via the menu option accessible via the right-hand top corner of the desktop.

This is not ideal, but appears to be a cosmetic issue only.

---

### Post by veedub67 on 2022-06-03
If I right-click on the file: home/user/Desktop/AIProtector.desktop

and select: 
Open with Create Launcher on the panel

I get:
Failed to add a plugin to the panel
GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.xfce.Panel was not provided by any .service files

---

### Post by veedub67 on 2022-06-03
Hello,

So I have followed the steps: 
Create a desktop application shortcut launcher manually

From here
[https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)

And there is still no icon on the desktop

And I've checked that the file that I have created is in the Desktop directory

---

### Post by mIk3_08 on 2022-06-04
> **veedub67 said:**
> Hello,
So I have followed the steps: 
Create a desktop application shortcut launcher manually

From here
[https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)

And there is still no icon on the desktop
And I've checked that the file that I have created is in the Desktop directory
Have you tried to launch the icon via desktop clicking only, the icon that you copy from the application folder and placed it on the desktop?

---

### Post by veedub67 on 2022-06-04
> **mIk3_08 said:**
> Have you tryied to launch the icon via desktop clicking only, the icon that you copy from the application folder and placed it on the desktop?

I have completed Steps 1 & 2

But when I get to Step 3, there is no icon appearing on the desktop. So I am stuck at Step 3.

---

### Post by veedub67 on 2022-06-04
I have finally fixed this after trying probably half a dozen different suggestions based on other people's experiences.

I needed to install: Ding
and restart

Then the desktop icons appeared

---

