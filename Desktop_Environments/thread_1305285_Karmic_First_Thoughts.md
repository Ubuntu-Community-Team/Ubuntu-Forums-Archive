---
title: "Karmic First Thoughts"
date: 2009-10-29
forum: Desktop Environments
---

### Post by NoSheds on 2009-10-29
First post.  I hope this is the right place - sorry if it isn't.
Splash screen, preferred last 2 incarnations.

Login Screen.  Why can't I customise it?  I want to type in user name and have no list of users.  Don't like the new version.  Apart from anything else, listing valid users is a small security risk.


New icons on menu bar for battery, wireless strength, volume control etc are grey and boring.  I want the ones from the last version back, but I've yet to find them,  

Icon for folders, guess what, preferred the last version.  Haven't found a nice replacement yet.

No big problems, just don't like the new appearance.  Previously I've been able to find a nice alternative quickly, not managed that with this version.

Oh, Epiphany and Evolution appeared by default in Message Notification window, yet Epiphany crashed every time I clicked on it.  I don't use either - I use Mozilla and Pidgin - they were installed and the defaults, why didn't they appear in the Message Notification window?

---

### Post by joewski on 2009-10-29
> **NoSheds said:**
> 
Splash screen, preferred last 2 incarnations.

Login Screen.  Why can't I customise it?  I want to type in user name and have no list of users.  Don't like the new version.  Apart from anything else, listing valid users is a small security risk.


Well for you it isn't a great problem but for me its turned into a small disaster. When I upgraded from 9.04 to 9.10 I ended up with the xubuntu login screen. I now trying to figure out how to customise to how Ubuntu should look. You see I run multiple desktops so the upgrade didn't go as it was supposted to.

I also think the add/remove application too is a backward step. In 9.04 you could pick several programs to install at once. Now you need to click and select, then install. It is more highly time consuming and requires more clicks per application.

Also Ubuntu one has stopped working across the board on all my machines that I have installed.

Also another weak aspect of the upgrade process, is the management of repositories. I have a local repository that I prefer to use because it doesn't cost me any download fee. (bigpond) So what I needed to do was turn off all the repositories not related to Bigpond, then switch the Bigpond repositories from Jaunty to Karmic. Set the update the download process. It then bombs out. Then I have to switch repositories back to main and switch off the Bigpond repositories and then perform the upgrade using update-manager -d command.

---

### Post by NoSheds on 2009-10-30
> **joewski said:**
> 
I also think the add/remove application too is a backward step. In 9.04 you could pick several programs to install at once. Now you need to click and select, then install. It is more highly time consuming and requires more clicks per application.

Sorry install didn't go so well for you.
You can get Add/Remove Programs back using sudo apt-get install gnome-app-install. You then have to add it to a menu somewhere.
I hadn't spotted the Software Centre when I posted.  I hate it too!

In previous versions of Ubuntu, I've managed to get the "correct" splash screen by uninstalling packages like xubuntu then re-installing them with the "correct" one last.  There have also been websites listing how to directly download/install/configure the relevant files to revert to the correct splash screen system.  However, I don't know if this info will be available for such a new version.

HTH

---

### Post by Malcy on 2009-10-30
My first thought is....

If I can't replace the appalling brown pixellated mess that appears at start up with something a bit more appealing (even moving text would be better) then I'm either going back to 9.04 or looking elsewhere. :frown:

---

### Post by folke on 2009-11-01
> **joewski said:**
> Well for you it isn't a great problem but for me its turned into a small disaster. When I upgraded from 9.04 to 9.10 I ended up with the xubuntu login screen. I now trying to figure out how to customise to how Ubuntu should look. You see I run multiple desktops so the upgrade didn't go as it was supposted to.

+1.

Mine also got Xubuntu as default?

I am now trying to get the right one with the help from this post.
[http://swiss.ubuntuforums.org/showpost.php?p=8203532&postcount=3](http://swiss.ubuntuforums.org/showpost.php?p=8203532&postcount=3)

Lets se how it goes :)

--
Regards Folke

---

### Post by Malcy on 2009-11-01
There's a bit more to changing the start up appearance than that. Startup consists of four stages.

1. Grub/boot manager
2. Usplash
3. Xsplash
4. GDM

So here is how I worked out how to change things.

1. Install Startup manager, you can do this in synaptic.

2. If you want to set a boot screen graphic open startup manager and go to the appearance tab. You will need a bootloader/grub theme. One source is to go to Gnome-Look.org and select splash screens from the menu. Download your choice and use Manage Bootloader themes to add it. Check the Use background image box.

3. If you want to change the Usplash stage (this is the B/W Ubuntu symbol screen) you can get ready made themes from the same location in Gnome-look. Files must end in .so. Use the manage usplash themes to add and select your theme. 

If you want to make your own theme, it is possible but requires a bit of work. Instructions here:

[http://ubuntuforums.org/showthread.php?t=771410](http://ubuntuforums.org/showthread.php?t=771410)

4. The Xsplash image is much easier. It is stored at a series of images of different resolutions at /usr/share/images/xsplash. Simply choose the image that you want and replicate it in the required resolutions. 

You will want it to match the GDM background so either choose an image from /usr/share/backgrounds or put a copy of your chosen image in this folder at the appropriate resolution (1280x1024 and 1280x800 seem to be common).

n.b if you want to make a usplash theme that matches xsplash and GDM, then choose something with few colours as usplash images are limited to 256 colours.

5. To set the GDM background and theme, fonts etc follow the instructions on this link:

[http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)

I hope that this helps. I'm sorry it isn't simpler but my start up is now a lot easier on the eye. :D

---

### Post by Melcar on 2009-11-01
I like the new boot splash screen.  I also like the default login screen, but it would have been a world's difference if we are able to change it; why can't we change it now?  The new icons are alright, except for the network and volume ones; since I like using dark colours for my panels they end up almost invisible.  No big deal since I can always change them.  The only real problem I'm having in the visual department is fonts being to blurry in Firefox and some other applications; fonts in GNOME itself are fine (sharp and easy to read) but they look messed up in Firefox for some reason.  
Overall I like Karmic.  To bad the KDE side didn't get as much love :(.

---

### Post by DAFFEY on 2009-11-01
Tried to 'update' my desktop from 9.04 to 9.10. (dual boot with XP).  Now  Ubuntu sys is trashed. (still boots XP)

Tried to update my laptop from 9.04 to 9.10 (dual boot vista/Ubuntu/Mint) now that Ubuntu is trash. then tried installing from a CD to the laptop.  After a whole new series of unfamiliar screens/questions I could only guess at, I'm back at day zero (new, non-configured) with all my configuration and files gone.  Also, the wireless isn't working (did in 9.04)

I don't know enough about Linux Lingo to bail myself out of this one, There are so many "help" screens/threads that I can't remember where I am after 5 minutes.

Bottom line folks, Linux will never go mainstream if non-geek people cannot find their way thru it.  

For the record, flickering screen with file check in progress keeps scrolling on the desk top until complete then goes to a non responsive dead screen.  Manual power off is the only recourse.

This may not be the right forum for this commentary, but I don't know where feed back is??  Daffey

---

### Post by petri on 2009-11-02
Switch user is not possible, there it is on the menu uppright but it doesn't switch the user. 

Just when I got it work in Jaunty on my poor AMD drivers #-o

---

