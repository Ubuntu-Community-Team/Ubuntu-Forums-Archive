---
title: "how to make a link on the desktop"
date: 2012-09-20
forum: Desktop Environments
---

### Post by ddavidd on 2012-09-20
Ubuntu 12.04 LTS
Gnome Classic desktop

I simply want to make a link to a folder on the desktop.

I found these instructions:

sudo apt-get install --no-install-recommends gnome-panel

(which is not necessary since the Software centere shows gnome-panel as already installed)

Create new launcher

Open the terminal and run the following command

Code
gnome-desktop-item-edit ~/Desktop/ --create-new

This brings the following error:

gnome-desktop-item-edit: file:///home/david/Desktop does not have a .desktop or .directory suffix

Can anyone suggest how to fix this?
Is there not an easy way to create a link to a folder on the desktop?

---

### Post by coffeecat on 2012-09-20
A desktop launcher is not the same as a link to a folder. If it's a link to a folder that you are wanting to create, try this:

Open a nautilus file browser and navigate to the parent of the folder you want a link for. Right click on the folder you want to link to and then click on "Make Link". A new folder with a link arrow appears named "Link to whatever". Simply drag and drop the link folder to your desktop. You can then delete the original link.

This works just fine with the Unity desktop but I see no reason why it should not work with the classic desktop.

---

### Post by sharathkumar on 2012-09-20
Hi, try changing the word "Desktop" to your system language's "desktop", translate it and try.

---

### Post by ddavidd on 2012-09-20
Two good suggestions, thanks

Right clicking on a folder and selecting "make link" produces an error (attempting to translate into English) "This target supports no symbolic links" and when I click "skip", nothing happens. 

The second suggestion got further, although I thought the terminal doesn't accept German letters.
I change desktop to Arbeitsfläche in the command and it worked, thanks!
But clicking the starter also brings an error "an error occurredin teh execution of the application" although I entered location not application.
I will play with it further!

---

