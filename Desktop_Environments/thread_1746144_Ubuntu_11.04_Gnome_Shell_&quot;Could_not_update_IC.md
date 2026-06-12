---
title: "Ubuntu 11.04 Gnome Shell &quot;Could not update ICEauthority file /home/user/.ICEauthority"
date: 2011-05-01
forum: Desktop Environments
---

### Post by Grozzy on 2011-05-01
Hello forum!
I recently installed Ubuntu 11.04 with Unity as the default desktop environment, but I wanted Gnome 3 instead. So the installation of Gnome 3 and Gnome Shell went through, and I'm presented with a nice "gnomeish" gdm, but when I type my user password and try to log in all I get is this:

```
Could not update ICEauthority file /home/pontus/.ICEauthority
```
And all I can click is a button that logs me out.

I've tried from the terminal to change owner and rights and I've even tried to delete the file, but I still get this dialog every time I log in.

Is there something else I can do and what may cause this strange problem?

Thank you!

---

### Post by ipx on 2011-05-01
I just got the same thing when installing it 15 minutes ago. Ubuntu 11.04 with Gnome 3 installed from the ppa-repository. I removed .ICEauthority but it didnt help.

I've tried the following so far:
- chmod -R 1777 /tmp
- chmod -R 777 ~/.local
- Create an empty .ICEauthority-file and chmod 777 it

No success. :(

---

### Post by shox15 on 2011-05-01
exactly the same problem happen to me when i update from unity to gnome ,also try different permission ,please help

---

### Post by Xaqq on 2011-05-01
Hi,
Same problem here :(

---

### Post by oldfred on 2011-05-01
This sometimes occurs with moving /home and these were the fixes suggested then.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER or $HOME
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chown $USER:$USER /home/$USER/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
or depending on permissions desired:
sudo chmod 600 $HOME/.ICEauthority

fred@fred-MavericDT:~$ echo $HOME
/home/fred
fred@fred-MavericDT:~$ echo $USER
fred
fred@fred-MavericDT:~$

---

### Post by ipx on 2011-05-01
> **oldfred said:**
> This sometimes occurs with moving /home and these were the fixes suggested then.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER or $HOME
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chown $USER:$USER /home/$USER/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
or depending on permissions desired:
sudo chmod 600 $HOME/.ICEauthority

fred@fred-MavericDT:~$ echo $HOME
/home/fred
fred@fred-MavericDT:~$ echo $USER
fred
fred@fred-MavericDT:~$

Thank you for that, however it did not work for me. I tried all of the above and I still get this error.

---

### Post by Grozzy on 2011-05-01
> **ipx said:**
> Thank you for that, however it did not work for me. I tried all of the above and I still get this error.

Didn't work for me either. This is what makes it so strange.

---

### Post by techgs on 2011-05-01
I have faced similar problem and finally found the work around.

I have taken following steps (  I am sure that some one will find more easy way to do that.)

1.  By pressing CTRL+ALT F1 I could go command line mode.

2.  I have installed lxde as alternative desktop manager just to keep my work.

3.  From the Others menu I could figure out gnome3 manager.

4.  Made the changes to stop autologin.

Voilla...

rebooted and selected gnome3 session...

Everything worked as expected and .ICEauthority error disappered and now I am using Gnome 3 on Natty.

:guitar:

---

### Post by ipx on 2011-05-01
> **techgs said:**
> I have faced similar problem and finally found the work around.

I have taken following steps (  I am sure that some one will find more easy way to do that.)

1.  By pressing CTRL+ALT F1 I could go command line mode.

2.  I have installed lxde as alternative desktop manager just to keep my work.

3.  From the Others menu I could figure out gnome3 manager.

4.  Made the changes to stop autologin.

Voilla...

rebooted and selected gnome3 session...

Everything worked as expected and .ICEauthority error disappered and now I am using Gnome 3 on Natty.

:guitar:

Hm.. I tried doing that, and when I logged into the lxde-session and looked inside "Login Screen" settings there was no autologin. However, now when I logout and login as "Gnome/Openbox" it will now show a black screen for a second and then right back at login screen.

All I get in the syslog is two Gtk-WARNING's with some gtkwidget

Edit:
I also tried removing all gnome-related configuration folders (.gnome, .gnome2, .gconf, .gconfd, .metacity), still the same problem.

These are the two error messages I got: 
gdm-simple-greeter[3075]: Gtk-WARNING: /build/buildd/gtk+3.0-3.0.8/./gtk/gtkwidget.c:6786: widget not within a GtkWindow
gdm-simple-greeter[3075]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47

This guy seems to have the same problem: [http://ubuntuforums.org/showthread.php?t=1738674](http://ubuntuforums.org/showthread.php?t=1738674)

---

### Post by Grozzy on 2011-05-01
I installed LXDE and it was all I needed, because I need to end my day here in Finland :D
I think this error is supposed to occur when you have autologin enabled, so I will try enable autologin and then disable it. Maybe you can try that and let me know if it works.

Good night and see you tomorrow!

---

### Post by ipx on 2011-05-01
I got it to work now by reinstalling gnome through apt-get. The general solution however seems to be to install another desktop manager like lxde and run it once, after that gnome3 should work.

---

### Post by Grozzy on 2011-05-01
Yes! It worked for me too. Thank you **techgs** for the tip.

**Here's the solution:**

1. Install another desktop manager, e.g. LXDE.
2. Log in using it.
3. Reboot and log in using Gnome Shell.

At first gnome-shell did not autostart, but that could easily be solved by adding a startup command.

Thank you all!

**EDIT:** This did not work when I removed LXDE.

---

### Post by Serry911 on 2011-05-01
> **Grozzy said:**
> Yes! It worked for me too. Thank you **techgs** for the tip.
 
**Here's the solution:**
 
1. Install another desktop manager, e.g. LXDE.
2. Log in using it.
3. Reboot and log in using Gnome Shell.
 
At first gnome-shell did not autostart, but that could easily be solved by adding a startup command.
 
Thank you all!
hello, guyz iam really a very newbie and i loved ubuntu 10.10 and then i upgraded to 11.04 then installed gnome3 and now i have the same error like yours, i have no internet connection now as the laptop cannot login so i cant install lxde i will appreciate if u helped me how to solve this issue briefly pleaseeeeeee
Thank you

---

### Post by VampiricPadraig on 2011-05-01
> **Serry911 said:**
> hello, guyz iam really a very newbie and i loved ubuntu 10.10 and then i upgraded to 11.04 then installed gnome3 and now i have the same error like yours, i have no internet connection now as the laptop cannot login so i cant install lxde i will appreciate if u helped me how to solve this issue briefly pleaseeeeeee
Thank you

Same here. :)

---

### Post by Serry911 on 2011-05-02
> **VampiricPadraig said:**
> Same here. :)
So what will we do dood? I don't know what to do am using the other laptop with windows 7 and it really sucks

---

### Post by davoudi on 2011-05-02
Select recovery mode in the boot time, then sudo apt-get install lxde to get ride of switching back and forth to windows 7. Now you have a simple nice linux environment to do your things. You need to install gnome-shell as well. Now can change startup option using command gconf-editor. Select "desktop", "gnome", "required_components", remove compiz and add "gnome-shell. This however didn't work for me, so I don't know what I am missing.

---

### Post by Serry911 on 2011-05-02
> **davoudi said:**
> Select recovery mode in the boot time, then sudo apt-get install lxde to get ride of switching back and forth to windows 7. Now you have a simple nice linux environment to do your things. You need to install gnome-shell as well. Now can change startup option using command gconf-editor. Select "desktop", "gnome", "required_components", remove compiz and add "gnome-shell. This however didn't work for me, so I don't know what I am missing.
 well i only have ubuntu on my laptop and iam not that expert and i tried yestreday to install lxde but it didnt install because of no internet connection i think, iam downloading 11.04 livecd now and all my data (100GB) are in the home folder as i dont have other partitions can u tell me how to remove gnome3 and get back to unity or actually re-installing 11.04 without loosing data?
Thank you very much

---

### Post by Grozzy on 2011-05-02
Okay, I admit, the solution did not work. When I removed LXDE, the ".ICEauthority" error just keeps coming back.
](*,)

---

### Post by johnnyslogan on 2011-05-02
Hi - I had the same problem, and it turned out, I didn't do the 

```
sudo apt-get install gnome-shell
```

during installation of gnome 3. It might be worth a try.

---

### Post by thomasmilo on 2011-05-02
> **techgs said:**
> I have faced similar problem and finally found the work around.

I have taken following steps (  I am sure that some one will find more easy way to do that.)

1.  By pressing CTRL+ALT F1 I could go command line mode.

2.  I have installed lxde as alternative desktop manager just to keep my work.

3.  From the Others menu I could figure out gnome3 manager.

4.  Made the changes to stop autologin.

Voilla...

rebooted and selected gnome3 session...

Everything worked as expected and .ICEauthority error disappered and now I am using Gnome 3 on Natty.

:guitar:
Techgs,
Thank you for this solution.  I like the lighter desktop better anyway and now I don't have to rush to solve the continuing gdm issue.

---

### Post by WG- on 2011-05-02
And same problem here :D

Hopefully it is fixed very very soon.

---

### Post by Bodman on 2011-05-02
Same here. :confused:

---

### Post by davoudi on 2011-05-02
> **Serry911 said:**
> well i only have ubuntu on my laptop and iam not that expert and i tried yestreday to install lxde but it didnt install because of no internet connection i think, iam downloading 11.04 livecd now and all my data (100GB) are in the home folder as i dont have other partitions can u tell me how to remove gnome3 and get back to unity or actually re-installing 11.04 without loosing data?
Thank you very much
You are given the opportunity to use safe mode with internet access. If you are experiencing problem with the wireless, then the most easy solution is to use wire to install lxde. You can do the rest of the things wirelessly.

---

### Post by Tropcon on 2011-05-02
> **Serry911 said:**
> can u tell me how to remove gnome3 and get back to unity or actually re-installing 11.04 without loosing data?
Thank you very much

I reinstall my OS quite often. The trick is, don't let the installer format the partition.

NOTE: This is assuming that you used the default, guided partitioning method.

Boot up the live CD and enter the installer.
When you get to the "Allocate Drive Space" Section of the installer, chose "Something Else" (what a descriptive name.) This will take you into the manual partition editor.
Find your Ubuntu partition on the list, right-click on it and say "Change."
In the resulting window, change the "Use as:" section to "Ext4 jouraling file system"
Then set the "Mount point" to "/"
Click OK, and AFTER you get back to the main partitioning window make sure that the "Format?" section is UNchecked. If you used a file system other than Ext4 in the original installation, it will force a format because it has to change the file system.
If the partition is not marked for formating, go ahead and finish the installation making sure to use the exact same name, user-name and password as you did in the original installation. If you don't, it can mess things up.
That's all! You will have to reinstall any programs you had before, but all your files and program settings will still be there.

ANOTHER NOTE: If you are using this method to install a DIFFERENT version of Ubuntu than the one you're starting with, it may be a good idea to delete the hidden files containing program settings in your home folder to prevent problems with different program versions.

By the way, I'm having the same problem with the /ICEauthority file. I haven't tried all the posted fixes yet, but I'll write back if something works.

---

### Post by buster2209 on 2011-05-02
Follow the upgrade instructions from here;

[http://ugr.teampr0xy.net/install](http://ugr.teampr0xy.net/install)

There's no need for lxde or gnome-session as /.ICEauthority wont be broken.

---

### Post by Tropcon on 2011-05-02
A strange thing just happned. I installed LXDE, logged into Gnome 3 (and it worked) then uninstalled LXDE using:

```
sudo apt-get autoremove lxde
```

After rebooting, Gnome 3 still works.
The only other thing I did was make a backup copy of the ICEauthority file.
Is it still working because I used autoremove instead of plain remove?

---

### Post by davoudi on 2011-05-02
> **buster2209 said:**
> Follow the upgrade instructions from here;

[http://ugr.teampr0xy.net/install](http://ugr.teampr0xy.net/install)

There's no need for lxde or gnome-session as /.ICEauthority wont be broken.
Thanks. All I need was a fresh ubuntu installation. Now I got Gnome3 up and running. Have fun folk.

---

### Post by Grozzy on 2011-05-03
*Press CTRL + Alt + F1 to switch to the first console and type the commands there.*

According to this thread [http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343) you should try this command to get rid of .ICEauthority error:

```
sudo apt-get install gnome-session
```But if that doesn't work try to, as said, install LXDE and then boot into it. After that you should be able to boot Gnome Shell. I had to add the command "gnome-shell --replace" to autostart because it didn't start at login (I did it through LXDE because I couldn't do much in Gnome at that point). If everything works then, you can uninstall lxde with the command:

```
sudo apt-get autoremove lxde
```Hope this helps!

---

### Post by hilldog on 2011-05-03
> **thomasmilo said:**
> Techgs,
Thank you for this solution.  I like the lighter desktop better anyway and now I don't have to rush to solve the continuing gdm issue.

I have no idea why this works but it did! Now I have Gnome 3 on Natty and a fall back desk mgr just in case. Pretty sweet!

---

### Post by huangweiqiu on 2011-05-04
Hi folks

this tips may help you to fix the ICEauthority problem

[http://linuxfloat.org/gnome3-could-not-update-iceauthority-file-homeusericeauthority](http://linuxfloat.org/gnome3-could-not-update-iceauthority-file-homeusericeauthority)

---

### Post by Jagoly on 2011-05-04
hello. I'm currently trying out a few new DE's (yes, because I hate unity). At the moment I'm trying gnome 3 on a seperate 11.04 test partition. I installed gnome 3, and am having this problem. I've got a laptop, and at the moment wired access = not gonna happen.

On my currently in use 10.10 install, I got the debs for openbox (and it's dependencies) because it had only 2 dependencies. back on natty, I used dpkg from the ctrl-alt-f2 terminal to install it.

reboot, natty's gnome 3 gdm now shows openbox, but logging into it gives exactly the same error message. Do I have to get lxde?

---

### Post by LEOThanhTiep on 2011-05-04
hi! I've s problem. after setup window to win7. I can't select boot in ubuntu. Any solution! Thanks!!!...

---

### Post by maverick280857 on 2011-05-05
I did a clean install of Ubuntu 11.04 64-bit a few hours ago, and installed Gnome3. I get the .ICEauthority error on trying to log-in, but none of the above remedies worked.

Most importantly though, I don't know how to install "lxde" or "gnome-session" because apparently my wireless network does not work on the text mode console. Any ideas for this?

---

### Post by maverick280857 on 2011-05-05
Okay, here is what I did:

1. Boot from Ubuntu 11.04 Live CD and use the "Try Ubuntu" feature.
2. Connect to the wireless.
3. Use [http://leastaction.wordpress.com/2011/02/05/use-the-ubuntu-live-cd-to-mount-your-local-installation/](http://leastaction.wordpress.com/2011/02/05/use-the-ubuntu-live-cd-to-mount-your-local-installation/) to mount my Ubuntu installation.
4. Do
```

sudo apt-get update 
sudo apt-get upgrade
sudo apt-get remove network-manager
sudo apt-get install lxde wicd

```
5. Reboot into LXDE.
6. Log out of LXDE.

**Note**: I had to install wicd to get the wireless to work in LXDE. And wicd conflicts with network-manager, which has to be removed.

Now at the login-screen, I see the following options:

**GNOME/Openbox**: does not work (login screen reappears after apparent automatic logoff)
**LXDE**: Works with limited functionality (no network :-()
**Openbox**: Works with limited functionality (no network :-()
**Ubuntu**: Returns the error message "Failed to load session "ubuntu"" and returns me to login screen.
**Ubuntu Gnome Shell Desktop**:  Returns the error message "Failed to load session "gnome"" and returns me to login screen.
**User Defined Session**:  Returns the error message "Failed to load session "gnome"" and returns me to login screen.

(I also tried to rename ~/.ICEauthority to ~/.ICEauthority-old, but this does not improve matters.)

I would appreciate any suggestions or ideas.

**Conclusion**: I am only able to run LXDE.

I guess I will do a clean install now...

---

### Post by mercurycc on 2011-05-05
Today I upgraded gnome-session-bin, and then I got the same error, reporting Failed to load session "gnome".

---

### Post by maverick280857 on 2011-05-05
A clean install and following the instructions mentioned on [http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343) helped. Now I have Gnome 3 running, although after all the effort put in, I don't think its really worth it :-P

---

### Post by 23dornot23d on 2011-05-05
Only if you are thinking of doing a clean install , 

Try the instructions on my link for Gnome-Shell below ..... purge and then re-install it as I have done this before when UNITY would not work as GNOME-SHELL seemed to stop it ( but now everything runs fine ).

It takes a bit of time ..... but I now have 

GNOME-SHELL / UNITY / LXDE / ENLIGHTENMENT /KDE ...... 
( all with CONKY and CAIRO-DOCK too )

All running happily together.

I can switch from desktop to desktop ...... as the same user ...... but would advise people if
they want to run 3 or more separate desktops ..... use a USER for each as the desktop settings then remain with each users setup.

**[COLOR=Red]Might be worth trying before doing a complete fresh install .......[/COLOR]**

---

### Post by jrussell88 on 2011-05-09
If you're sharing /home you may run into problems with this. 

Different User IDs for different installations can overwrite one another, causing the .ICEauthority problems. 

See my notes here today: [http://linuxfloat.org/gnome3-could-not-update-iceauthority-file-homeusericeauthority#comment-346](http://linuxfloat.org/gnome3-could-not-update-iceauthority-file-homeusericeauthority#comment-346)

Having been through it on several machines with a range of problems from warnings on login to a failure to run the graphical desktop, I think ICEauthority shouldn't be hard to fix, as long as you know what the source of the conflict is. 

John

---

### Post by gccradioscience on 2011-05-30
I am having the same problem too on my SR2010NX today,  this happenned when I tried to create a new account, cause there was a problem with the window that could not tell me the connected hard drives.  So I created a new account, then deleted the old account, and when I rebooted this error came up.  Right now I am using the back up "live" CD until I can get my main installation back, and that means I have to leave the computer on and I have to purchase a external hard drive, do a back up, then put the CD back in and reinstall the OS again and the hard drive will be all linux ubuntu partition just like my netbook.   Yes, the partition of 11.04 upgrade has failed today after deleting a old account.  

Adam E. 

  




> **Grozzy said:**
> Hello forum!
I recently installed Ubuntu 11.04 with Unity as the default desktop environment, but I wanted Gnome 3 instead. So the installation of Gnome 3 and Gnome Shell went through, and I'm presented with a nice "gnomeish" gdm, but when I type my user password and try to log in all I get is this:

```
Could not update ICEauthority file /home/pontus/.ICEauthority
```
And all I can click is a button that logs me out.

I've tried from the terminal to change owner and rights and I've even tried to delete the file, but I still get this dialog every time I log in.

Is there something else I can do and what may cause this strange problem?

Thank you!

---

### Post by GutsyVirgin on 2011-05-31
Interesting... my error occurs when I logoff, not reboot. Except the directory given on mine is /var/lib/gdm/.ICEauthority, but I suspect it boils down to the same issue.

I also get an accompanying error directly after than one which says:
"There is a problem with the configuration server (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with the status 256)"

I'm guessing these errors may have been brought on by my many failed attempts to get the Nvidia drivers configured for my machine which apparently is impossible :(

---

### Post by dennon57 on 2011-06-04
i have the same problem, all start when change mi password user  and resolved login in shell at root an change back the same password if some one know how i change mi pass and dont have this problem i appreciate they tell me ubuntu 11.4 natty  and my folder home is encrypted 

sorry by the grammatical but the english is not my language

---

### Post by Tropcon on 2011-06-05
To change a password using the command line:

```
sudo passwd *username*
```

---

### Post by tadao on 2011-06-14
The only thing that resolved this issue in my Ubuntu 11.04 login was to go to console (typing Ctrl-Alt-F2 for example), logging in as root or your own user, and installing:

sudo apt-get install gnome-session
or as root:
apt-get install gnome-session

This installed gnome-session and gnome-session-common and resolved this issue completely.

---

### Post by hoangdang on 2011-08-02
Here is the fix people (at least for me in Ubuntu 11.04)

1) Go to Ubuntu Software Center
2) Search for 'Gnome-session manager' 
3) Remove the package
4) Re-install the package
5) Reboot
6) :KS

---

### Post by scottstensland on 2011-08-06
There is no need to install and cut over to a different window manager ...

SOLUTION - Use a different userid which has admin power (sudo).
First logout of your account which has the ICEauthority file error,
then login using that different loginid which has sudo power and issue:

sudo chown XXXX:XXXX /home/XXXX/.ICEauthority
sudo chmod 644 /home/XXXX/.ICEauthority

where XXXX is your loginid which has the ICEauthority file error message.
This works fine for me when I had that error.

enjoy - Scott Stensland

---

### Post by sumantsingh on 2011-08-06
Tell u what, don't install gnome 3 on ubuntu 11.04, it doesn't support it, i have installed gnome 3 on 11.04, it sowing problem like failed to load session "gnome-fallback" with logout option, you cannot even login with gnome, you'll have to work with unity interface that sucks. use gnome classic view..:)

---

### Post by tonynardi on 2011-09-07
First I will describe the circumstances which led me to this error and then provide the solution.

I am using Ubuntu 11.04 Classic theme, went into System -> Administration -> Users and Groups.

Within Users and Groups I checked a box that allowed me to login without providing a password.  This turns out to be a problem if your file system is encrypted, as your password is used to authenticate a session and decrypt the file system.

And here is the solution I came across, after many unsuccessful attempts using the other solutions found on this forum:

--Before you log in, hit ctrl+alt+f1
--enter your username
--enter your password
--hit ctrl+alt+f7
--it should now say that you are already logged in, marked by a green checkmark where your username is displayed in the login box
--login and hopefully you will be able to use the graphical interface to make the necessary changes.

--GOOD LUCK--

---

### Post by OPunWide on 2012-01-11
My system crashed during an upgrade to Natty Narwhal. It refused to try to fix that, but instead wanted to go straight to Oneiric Ocelot. I crossed my fingers, having little other choice. Amazingly, it seemed to do the full upgrade. But then I found that I had this thread's issue.

I tried many of the suggested owner:group and permission fixes, but none had any effect. I couldn't get into Gnome, but I had SSH access, so I could make changes from there. The final fix for me was: 

```
sudo apt-get install lxde
```

Then reboot (it went to lxde), and log in to Gnome to verify that it was working. Then because I didn't need it:

```
sudo apt-get autoremove lxde
```

That's all, and everything is fine now.

---

### Post by neversaydie on 2012-06-06
First of all I am using Ubuntu 11.10 and I found the same error when I tried to login into my machine today.  I have found a workaround for that. Here how it works:

Pressed CTRL+ALT+F1 to logging into another terminal. Then checked who is the owner of my logged in user.

# ls -l /home

I've found my user is owned by 'root'. Just execute the following command to change the owner and group to the desired user:

# sudo chown user:user /home/user

Then pressed CTRL+ALT+F7 to go back to the Graphical User Mode and provided the password for the user. And this time I was able to logging into the machine.

Hope this may help someone for the same problem. Thanks.

---

### Post by ggallozz on 2012-10-10
**SOLVED** this way:

1. move the file '.ICEAuthority' somewhere in my own folders and applied property for my own owner +Read,Write,eXecute

2. with  Nautilus set "Properties" of my /home/username directory to read-write-eXecute

3. copied back '.ICEAuthity' to my home dir

4. logged out and in


I GUESS that problem went out from my new fresh installation of Natty on my second disk partition (were was Oneiric), knowing that my /HOME has always  been on the 4th, eXtended, disk partition, thus independent of OS installations.

---

