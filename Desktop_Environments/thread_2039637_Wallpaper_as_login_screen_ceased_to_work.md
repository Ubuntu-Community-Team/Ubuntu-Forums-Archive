---
title: "Wallpaper as login screen ceased to work"
date: 2012-08-09
forum: Desktop Environments
---

### Post by loopinaloop on 2012-08-09
The first thing I've noticed after installing Ubuntu 12.04 is that when you set an image as a desktop wallpaper, it's automatically used as your login screen that appears right after reboot. It was great but after downloading last system update (or maybe I've done something else?) it ceased to work.

I really loved that feature. Can someone point me out where I've gone wrong or how to fix it? I honestly dislike the default purple screen.

---

### Post by ranger1021994 on 2012-08-09
You might have installed a script that enables user to change wallpaper like you did.
All you need to do is reinstall the script that enables 'Set as desktop wallpaper' option ON.

Go to this ppa :
[https://launchpad.net/~nae-team/+archive/ppa](https://launchpad.net/~nae-team/+archive/ppa)

---

### Post by loopinaloop on 2012-08-09
I'm afraid that I don't understand... Can I somehow refresh my system? I've noticed that generally sometime after installation system's performance drops significantly with various anomalies appearing now and then.

---

### Post by Frogs Hair on 2012-08-09
A script or application to change wallpaper would not have come through the update manager unless one was installed . Try logging out and back in or restarting again. Do you have My Unity or Ubuntu Tweak installed ? I ask because Ubuntu Tweak has an option to change the login background .

---

### Post by loopinaloop on 2012-08-09
Well... I had some other minor issues so I've decided to re-install whole system entirely. Guess what, right after fresh install I've updated my system and I still have default background.

On the other hand I'm not sure if I was properly understood. Previously after fresh install my login background wasn't any default, pre-installed wallpaper. Instead, whatever I've set as my desktop wallpaper was also, automatically, set as login background. Just after turning my computer on I saw my profile's wallpaper and login window waiting for choosing profile and entering password.

If that doesn't help, then maybe someone can point me out to where I can manipulate or change login background image.

Sorry for so many words, I'm just getting sure that I'm understood properly.
Thank you for your time && best wishes!

---

### Post by Frogs Hair on 2012-08-09
> Previously after fresh install my login background wasn't any default, pre-installed wallpaper. Instead, whatever I've set as my desktop wallpaper was also, automatically, set as login background.

This is normal behavior in 12.04, but on the first boot the login screen will be Ubuntu purple until the wallpaper is changed by the user. I don't know why that feature would not be working if you have reinstalled since your first post. You can set the login background with Ubuntu Tweak but you shouldn't have to . [http://www.webupd8.org/2012/04/ubuntu-tweak-07-gets-app-and-source.html](http://www.webupd8.org/2012/04/ubuntu-tweak-07-gets-app-and-source.html)

---

### Post by aff92 on 2012-08-09
You can install Ubuntu Tweak, which is a software designed to configure certain features in the Ubuntu system. Ubuntu Tweak does not automatically set the login background image same as the desktop background image, but it allows you to set the same image for both(desktop and login screen) easily.

First you have to download and install ubuntu tweak

Open a terminal (ctrl + alt + T)
Type the following: 
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

Now that you have installed Ubuntu Tweak on your system, you have to run it and apply the modifications you want to do.

Click on the Dash Home and type, in the search bar, Ubuntu Tweak.
You will directly see it in the search results (a green icon)

After the app launches, click on the Tweaks button.
Now choose Login Settings.
At the upper right part of the window (next to the search bar), you will find a small button labelled Unlock (with a Lock icon).
Press Unlock and provide the password if prompted.
Now you simply have to scroll downwards, you will see a thumbnail for your current login screen wallpaper and under it a wide button labelled: Set the same background as the current background. Click on this button! When you click, you will notice that the above thumbnail has changed to your current Desktop background image and this means that you successfully set your login background image the same as that of your desktop.
You can now simply close Ubuntu Tweaks.
To test the new configurations. simply Log out of your current session or wait until you reboot :)

I know it sounds like a very long process, but once you get to do it you will find it simple and easy!

Hope this helps!

---

### Post by loopinaloop on 2012-08-10
> **aff92 said:**
> sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

THANK YOU!

But it appears that Ubuntu Tweaks is already installed! :) The bad news is that I've already changed wallpaper it doesn't appear on the login screen. What has happened is that default purple wallpaper has disappeared and now all there is is a plain purple nothingness. HELP! :(

---

### Post by Frogs Hair on 2012-08-10
Disable any Ubuntu Tweak settings and restart light gdm. When you run the command you will be taken back to the login screen so close all applications.```
sudo restart lightdm 
```

---

### Post by stinkeye on 2012-08-10
After I used a wallpaper changer app the login screen was just a black background.

I fixed by putting some settings back to default and using the right click
desktop menu to change desktop background.

Terminal commands...
```
gsettings reset com.canonical.unity-greeter background
```
```
gsettings reset com.canonical.unity-greeter draw-user-backgrounds
```

Then choose Change Desktop Background in the right click desktop menu
and use the dropdown or add button to set a custom wallpaper.

---

### Post by kostkon on 2012-08-11
Normally, for this to work you generally need:

Firstly, your wallpaper must reside inside the Pictures folder.

Secondly, you must right click on that folder, select the Permissions tab and then select Access Files for the Folder Access in the Others group, and finally hit the Apply Permissions to Enclosed Files button.

It should then work without the need to do tweaks or install extra software.

---

### Post by orange2k on 2012-08-11
If you try to set a picture from your pictures folder as a background image and your home directory is encrypted, Ubuntu will not be able to read that image prior to logging in...

If thats the case then on the login screen you will still have the default wallpaper...

Correct me if I'm wrong...

---

### Post by loopinaloop on 2012-08-11
x

---

### Post by loopinaloop on 2012-08-11
> **kostkon said:**
> Secondly, you must right click on that folder, select the Permissions tab and then select Access Files for the Folder Access in the Others group, and finally hit the Apply Permissions to Enclosed Files button.

I did that but it still doesn't work. Maybe it's because I used Ubuntu Tweaks? How to reset changes made by this program?

I've moved desired image to the /usr/share/backgrounds and even renamed the file to pretend it to be as the default image. I'd did this because changing login screen background works only with default images that are shipped with pure installation.

That's why I think it can be linked to the access privileges. It still doesn't explain why I had no issues before and I experience them now. Even  that I've reinstalled the system entirely. Maybe it's because of the recent updates? No one else experiences this problem?

---

### Post by loopinaloop on 2012-08-11
Thank you so much, **kostkon, **your advices were most helpful! It appears that giving privileges to subfolders was not enough, I needed to give them to whole "Pictures" folder. I wonder if it's because I've copied all folders from my pre-format home directory, merging them with the post-installation ones?

Is there anything else that I could have broken by this action? Should I edit all my home subfolders and give them read-only privileges for the Others?

---

### Post by ron_digital on 2012-08-17
Hi,
There's a workaround that I used that might work for you, its pretty simple, just open a Firefox window and type in /home on the address bar.

You will open your home folder on firefox, navigate to the pictures folder where I assume will have all your backgrounds, click on the desired file and it will be opened on the browser window, right click on the middle of the image and select the context menu **Set as desktop Background**, it will open a preview window asking to confirm the **Set as desktop Background**, confim it and you're done.

Just log out and check it, the wallpaper will be back to the login screen. :D

---

### Post by ron_digital on 2012-08-17
> **ron_digital said:**
> Hi,
There's a workaround that I used that might work for you, its pretty simple, just open a Firefox window and type in /home on the address bar.

You will open your home folder on firefox, navigate to the pictures folder where I assume will have all your backgrounds, click on the desired file and it will be opened on the browser window, right click on the middle of the image and select the context menu **Set as desktop Background**, it will open a preview window asking to confirm the **Set as desktop Background**, confim it and you're done.

Just log out and check it, the wallpaper will be back to the login screen. :D

I have tested this same solution from other applications that also have this option and none of them work 100%, most of them only change the desktop background, somehow the only one that does the job correctly for the login screen is the Firefox.

---

### Post by loopinaloop on 2012-08-20
> **ron_digital said:**
> ...somehow the only one that does the job correctly for the login screen is the Firefox.
What worked for me was right-clicking the Picture folder directly under the /home/user directory and then selecting Properties &#8594; Permissions Tab &#8594; Access Files for the Folder  Access in the Others group (read-only) &#8594; hit the Apply Permissions to  Enclosed Files button. It should work if home directory isn't 

Just like user kostkon said. Thank you again, **kostkon**!

I've noticed that moving my home directory to a remote driver, formatting computer and then merging my old folder with the fresh one somehow changed privileges. I think that moving the Picture directory alone is enough for further problems.

---

### Post by gdesilva on 2012-08-24
@ron_digital, I am running Ubuntu Studio 12.04 xfce4 session and tried to change the login screen background using Ubuntu Tweak without success.

Tried your method of using Firefox to open up the image but when I right click on the image I do not have the option of setting it as  the desktop background - I can only copy, save image etc no option for setting it as the desktop background.

Any ideas?

Thanks


[B][COLOR=Red]EDIT: Just found out the solution thanks to Archwiki 

 [https://wiki.archlinux.org/index.php/LightDM](https://wiki.archlinux.org/index.php/LightDM) - 

Simply edit the relevant greeter.conf file and Bob's your uncle!
[/COLOR][/B]

---

### Post by krige on 2013-04-25
> **loopinaloop said:**
> The first thing I've noticed after installing Ubuntu 12.04 is that when you set an image as a desktop wallpaper, it's automatically used as your login screen that appears right after reboot. It was great but after downloading last system update (or maybe I've done something else?) it ceased to work.

I really loved that feature. Can someone point me out where I've gone wrong or how to fix it? I honestly dislike the default purple screen.

I also noticed the same thing with both my desktop and my laptop computers and liked it very much. At some point the feature disappeared by itself, the same way it appeared.

I don't remember having installed any tweaker program or having set any configuration file. One day I turned on my computers and I found the login screen wallpaper matched the desktop wallpaper. Some time later I turned them on and found the dull purple background.

I have read the posts in this thread but haven't found a real solution or explanation to that. Questions remain how that feature appeared and disappeared by itself and how can we set it up again?  


> **gdesilva said:**
>  [https://wiki.archlinux.org/index.php/LightDM](https://wiki.archlinux.org/index.php/LightDM) - 
Simply edit the relevant greeter.conf file and Bob's your uncle!
[/COLOR][/B]

How should we edit the greeter.conf so that the login wallpaper always matches the current desktop wallpaper?

---

### Post by krige on 2013-04-25
Well, it looks like Ubuntu 12.04 Unity greeter had introduced **selected user dynamic background** which allowed, when selecting a user from the available users list in the login screen, the background to change to reflect the selected user's desktop background.

My guess is that this feature has been switched on first in 12.04 and then off in 12.10.

More info at [http://askubuntu.com/questions/285583/how-do-i-enable-the-user-dynamic-wallpaper-in-the-login-screen-of-ubuntu-13-04](http://askubuntu.com/questions/285583/how-do-i-enable-the-user-dynamic-wallpaper-in-the-login-screen-of-ubuntu-13-04)

---

### Post by mwillams73 on 2013-05-18
I'd like to know why, as others have said. When I put my background in the background folder, using gksudo nautilus, and then marking the file as not only access but full permissions under root. Why is it that when i select this file under ubuntu tweak to be used as the log in background as well as my normal desktop background, it, well, doesnt work? Anything in that folder should also show up in the appearance subsection of the settings menu , but, well, doesnt? What sense does it make to even have that folder let alone any other that you can't access without root access, then say not only do you have to be root, but you also are'nt allowed to use this background that you have explicitly said is accessable by root and user but your OS says it can't be?

No offense, but ubuntu and linux in general keep regressing as far as I'm concerned when it comes to stupidly simple things like this................

---

### Post by mwillams73 on 2013-05-18
> **loopinaloop said:**
> I did that but it still doesn't work. Maybe it's because I used Ubuntu Tweaks? How to reset changes made by this program?

I've moved desired image to the /usr/share/backgrounds and even renamed the file to pretend it to be as the default image. I'd did this because changing login screen background works only with default images that are shipped with pure installation.

That's why I think it can be linked to the access privileges. It still doesn't explain why I had no issues before and I experience them now. Even  that I've reinstalled the system entirely. Maybe it's because of the recent updates? No one else experiences this problem?

This should work as inteneded, as i said before, but..... It doesnt. Call it a flaw in the linux system or whatever. If you have to enter a password to even change the log in background ( As you do in ubuntu tweak) then it should already have all the appropriate permissions inherently........... Honestly I had it working a couple of months ago but its failed , yet again on me, kinda like how everytime i fix something thats broken, it breaks all over again........

---

### Post by mwillams73 on 2013-05-18
Just friggin remembered, you have to set the permissions to read and write for everything and it works. Oddly enough though, They revert back to the "-" after you apply them. Ubuntu you rascal you!!!!!! lol

---

