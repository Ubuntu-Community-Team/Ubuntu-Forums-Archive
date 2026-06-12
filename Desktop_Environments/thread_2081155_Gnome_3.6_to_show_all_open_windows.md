---
title: "Gnome 3.6 to show all open windows"
date: 2012-11-06
forum: Desktop Environments
---

### Post by Sparrow40k on 2012-11-06
Hey, I'm Blake

To start I feel I should point out that I am pretty new to Ubuntu and Linux in general, so common slang, acronyms and general information I wont know.
I have recently install Gnome on Ubuntu 12.10 (64bit) on my computer using:
> sudo apt-get install gnomeand it works fine.

So my problem..
With Gnome 3.6 I have noticed that in the toolbar on the top, it only shows the one active window that is in use.
How can I make it show all the windows that are currently open and then maybe put the clock more to the right (or just remove it because I am thinking about getting something cool with Conky). Something like Windows.

Example pictures below...

Thanks for reading and your help in advanced.

---

### Post by jbicha on 2012-11-06
Try [http://extensions.gnome.org/](http://extensions.gnome.org/) There is an extension to move the clock and others to show a dock.

Without extensions, you can see all the open windows by opening the Activities Overview; you can press the Super (Windows) key as a shortcut to pull it up. Or Alt+Tab.

---

### Post by 28c64 on 2012-11-06
Frippery bottom panel is good for this. I used it when I was using gnome-shell.

[https://extensions.gnome.org/extension/3/bottom-panel/](https://extensions.gnome.org/extension/3/bottom-panel/)

---

### Post by Sparrow40k on 2012-11-08
> **28c64 said:**
> Frippery bottom panel is good for this. I used it when I was using gnome-shell.

[https://extensions.gnome.org/extension/3/bottom-panel/](https://extensions.gnome.org/extension/3/bottom-panel/)

I'm using Gnome 3.6 and this doesn't work..

---

### Post by grege on 2012-11-12
> **Sparrow40k said:**
> I'm using Gnome 3.6 and this doesn't work..

What you are after is called "Window List" and there are several of them.

This one works for me

[https://extensions.gnome.org/extension/25/window-list/](https://extensions.gnome.org/extension/25/window-list/)

:)

ps

If it is greyed out go here and manually install a version fixed for 3.6

[http://shs-schubert.de/gnome-shell/](http://shs-schubert.de/gnome-shell/)

Download the zip file and unzip, and put the folder [email]windowlist@o2net.cl[/email]

into ~/.local/share/gnome-shell/extensions/ which is a hidden folder in your home folder. Open the file manager and press ctrl + h to show hidden folders

Original extension is here [https://github.com/siefkenj/gnome-shell-windowlist](https://github.com/siefkenj/gnome-shell-windowlist)

Then log out and in again and use Tweak Tool to turn the extension on.

---

### Post by Sparrow40k on 2012-11-12
So to give an idea, this is a quick mock-up of what I want. How can I make this or where can I get it?

---

### Post by Sparrow40k on 2012-11-12
> **grege said:**
> What you are after is called "Window List" and there are several of them.

This one works for me

[https://extensions.gnome.org/extension/25/window-list/](https://extensions.gnome.org/extension/25/window-list/)



YES!! This is exactly what I want!!

But when I like "ON" and it installs, nothing at all happens... ?

---

### Post by grege on 2012-11-12
> **Sparrow40k said:**
> YES!! This is exactly what I want!!

But when I like "ON" and it installs, nothing at all happens... ?

Run Tweak Tool from the menu. If Tweak Tool is not there then install it. Inside Tweak Tool is a menu to turn extensions on and off. You also use Tweak Tool to control themes and many other config items.

If the extension still does not work grab the manually install one from the link above. I am using the manually installed one and it works.

I also have the Gnome PPA installed to provide all the Gnome bits that normal Ubuntu leaves out.

---

### Post by grege on 2012-11-12
Open this page and search. Only extensions that will work will show in the list.

[https://extensions.gnome.org](https://extensions.gnome.org)

Window List does not show yet, therefore you will need to download the fixed version and replace the one you tried to install.

So go here [http://shs-schubert.de/gnome-shell/](http://shs-schubert.de/gnome-shell/)

And in the middle of the page find this -

..:: Upgrades and Updates ::..

"gnome-shell-windowlist" posted by: Schubi on 2012-10-30
gnome-shell-windowlist adds a window switcher to the top bar of gnome-shell.

original extension: gnome-shell-windowlist by bysiefkenj

Changes by Schubi:
- Gnome Shell 3.6 support,
- added "extend-left-box",
- added option for show title and app name together,
- other minor changes

..:: Download ::..

Select the link "Download" which will give you the file

[email]windowlist@o2net.cl.zip[/email]

From the file manager (Nautilus) click on the zip file and open and extract the contents and copy them into the hidden folder that will be in your home folder under .local. All hidden folders start with a dot/period/fullstop

then in .local go to share, then gnome-shell, then extensions.
 Then replace the folder [email]windowlist@o2net.cl[/email] if it exists or if it does not just copy in the contents of the zip

In the end you should have a folder .local/share/gnome-shell/extensions/windowlist@o2net.cl

Then restart Gnome and use Tweak Tool to turn it on.

ps

While you are at it add the theme extension and create a folder called .themes in your home folder.

From here you can download the themes, just unzip them into .themes

[http://browse.deviantart.com/?q=gnome+3.6](http://browse.deviantart.com/?q=gnome+3.6)

enjoy

---

### Post by Sparrow40k on 2012-11-14
> **grege said:**
> Open this page and search. Only extensions that will work will show in the list.

[https://extensions.gnome.org](https://extensions.gnome.org)

Window List does not show yet, therefore you will need to download the fixed version and replace the one you tried to install.

So go here [http://shs-schubert.de/gnome-shell/](http://shs-schubert.de/gnome-shell/)

And in the middle of the page find this -

..:: Upgrades and Updates ::..

"gnome-shell-windowlist" posted by: Schubi on 2012-10-30
gnome-shell-windowlist adds a window switcher to the top bar of gnome-shell.

original extension: gnome-shell-windowlist by bysiefkenj

Changes by Schubi:
- Gnome Shell 3.6 support,
- added "extend-left-box",
- added option for show title and app name together,
- other minor changes

..:: Download ::..

Select the link "Download" which will give you the file

[EMAIL="windowlist@o2net.cl.zip"]windowlist@o2net.cl.zip[/EMAIL]

From the file manager (Nautilus) click on the zip file and open and extract the contents and copy them into the hidden folder that will be in your home folder under .local. All hidden folders start with a dot/period/fullstop

then in .local go to share, then gnome-shell, then extensions.
 Then replace the folder [EMAIL="windowlist@o2net.cl"]windowlist@o2net.cl[/EMAIL] if it exists or if it does not just copy in the contents of the zip

In the end you should have a folder .local/share/gnome-shell/extensions/windowlist@o2net.cl

Then restart Gnome and use Tweak Tool to turn it on.

ps

While you are at it add the theme extension and create a folder called .themes in your home folder.

From here you can download the themes, just unzip them into .themes

[http://browse.deviantart.com/?q=gnome+3.6](http://browse.deviantart.com/?q=gnome+3.6)

enjoy

Thank you! worked perfectly!

---

### Post by Sparrow40k on 2012-11-14
*FACEPALM!!!*

I have no idea what has happened but all I did was log out while I was getting something to eat. I come back to log in and I notice that it is only showing the 1 active window again. I went into the Tweak Tool to see what up and it doesn't let me click 'ON' or 'OFF', it is blocked and there is a yellow exclamation mark next to it. And [Here]("https://extensions.gnome.org/extension/25/window-list/") where there would normally be the option for 'ON' or 'OFF', there is just a red square saying "ERROR"
I have other extensions also with Gnome and they have always been running fine, and they still are so I tried deleting the folder and starting again. But I still have the same result... 

PLEASE HELP!.. :(

---

### Post by grege on 2012-11-14
I do not know why yours worked then did not. Mine continues to work as it should.

But, extensions can interfere with each other. As each extension is written by an individual and not part of Gnome proper you can get the situation where two extensions fight each other.

My suggestion is to use Tweak Tool to turn off all of your extensions, then restart the shell and just turn on Window List. If it works then you can turn on the others one by one until you find the culprit. I tend to move the clock right to keep it out of the way. The top bar is divided into three regions - left, center and right.

You can restart the shell at any time without logging out, just press Alt-F2 then type in r and press enter.

---

### Post by Sparrow40k on 2012-11-23
I have the same setup on my laptop and I get the same result. I've tried using google for help but get nothing...

---

