---
title: "[SOLVED] Compiz Fusion - Some borders never go away - screenshot"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by scb0825 on 2007-08-23
Hey I posted a few days ago but I didn't get any helpful answers. I figured that I would wait for Trevino to update his repos and see if it fixes it, but it didn't (I just installed the newest repos). This problem did not surface until the 8/17 update to Trevino's repos. Here is the issue...

When some menu's and the authentication window  (like for Synaptic) are closed, they leave a semi-transparent border on the screen. This border is on top of all other windows, and visible on all desktops. 

What is interesting is that the borders that the menus leave will go away if I open that same menu again wait a second or two and then close the menu. Sometimes this also happens when I mouse over something and a text box appears (like for a webpage, or icon, whatever). Those will go away too if I go back to that thing and mouse over it again; although they have to be in the exact same place or it will not work. 

The authentication window is different; no matter how many times I open the window the border never goes away. To make it go away, I have to reload CF by using the following command
compiz --replace -c emerald &

Anyway, I understand that CF is still beta and there will be issues with it... although this is pretty annoying! :)

If anyone has ANY ideas... please let me know. Thanks in advance for any help...

EDIT:
I believe I solved this issue. I reviewed several threads, and one external link. I combined the stuff to solve my issue. I'm not sure if I needed to combine these things, as some may have been redundant.. but I'm still noobish ;)

First I removed ALL Compiz stuff. I did this by following only the cleanup commands found [here]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/")
The commands are...
> sudo apt-get remove compiz-core desktop-effects 
sudo apt-get remove compiz compiz-gnome 
sudo apt-get remove compizconfig-settings-manager 
sudo apt-get remove compiz-fusion-plugins-extra
sudo apt-get remove compiz-fusion-plugins-unofficial 
sudo apt-get remove libcompizconfig-backend-gconf

Then as good measure I did another remove command found at this [thread]("http://ubuntuforums.org/showthread.php?t=533201")
The command is...
>  sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev

Since I had Emerald installed, I went a head and removed it as well. I got the command from this [thread]("http://ubuntuforums.org/showthread.php?t=533501"). 
The command is...
> sudo apt-get --purge remove emerald*


After that I removed the Compiz folders discussed in the [thread]("http://ubuntuforums.org/showthread.php?t=533201") mentioned above. When I first tried fixing this I did not delete these folders and it did not fix the problem. After some trial an error, I eventually just moved the folders to the trash instead of moving them to my desktop everytime. :)
Since I removed Emerald, I also trashed it's folder from the home directory while I was in there.

Once everything was gone, I reinstalled using Trevino's repos. I used the commands found [here]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/").
The commands are...
> sudo aptitude -y update
sudo aptitude install compiz compiz-gnome \ compizconfig-settings-manager compiz-fusion-plugins-extra \ compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf

Then I reloaded Compiz and changed the settings back to what I like... and everything seems to be in working order. The only thing that isn't 100% yet is the desktop viewer in the lower right corner. I can use the cube/expo to change desktops and move windows around but it never reflects the changes down there. This could be a different issue though...

---

