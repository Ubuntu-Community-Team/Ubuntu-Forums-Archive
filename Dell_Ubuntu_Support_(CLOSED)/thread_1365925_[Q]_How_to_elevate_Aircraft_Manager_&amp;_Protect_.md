---
title: "[Q] How to elevate Aircraft Manager &amp; Protect GDM/xSplash?"
date: 2009-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by monxster on 2009-12-27
Hey guys,
 
I am a complete linux newbie only just having installed v9.10 (Karmic) on my Dell Mini 9 earlier today and I have to say, I am loving it!
 
I have done lots of reading on these forums and as a result have managed to install and tweak the system extensively with great success. However, I have two questions I was hoping I could get some help on as I cannot find an answer even though I have searched lots:
 
1. **Aircraft Manager:** When I originally installed v9.10 earlier today I foolishly used a simple user password and keyring (I used same key combo for both). After doing this I installed "Aircraft Manager" from the repositories and proceeded to map it to the keyboard shortcut Alt+Fn2 (Wifi Toggle). After I did this I could access the "Aircraft Manager" via the menu or the shortcut directly. When I did this I was NOT prompted for any password of any kind. 
 
After reading up on suggested password to avoid I decided to change my original user password and keyring. I changed my user password from the root terminal "sudo passwd" and I changed my keyring via Applications -> Accessories -> Passwords and Encryption Keys. I made sure that my new user password and keyring were the same so as to avoid getting a password prompt from "Network Manager" when I initially login and the PC acquires a wifi signal which I can confirm works just fine. 
 
However, ever since I changed my credentials, the "Aircraft Manager" now asks me for the system password upon launch via menu or keyboard shortcut!? Can someone please tell me how to bypass this password request and revert the launch sequence to the original status? Given that "Aircraft Manager" in v9.10 does not feature persistence, "Aircraft Manager" will be one of my most commonly used apps as I will be switching bluetooth off everytime upon initial boot so being able to restore the scenario where I can launch it with Alt+Fn2 and have it not ask for a password would be amazing. Is there some way of elevating the app to sudo status? 
 
I am aware I can just click "turn off bluetooth" on the panel icon or launch "Aircraft Manager" from terminal as sudo but I would like to get the shortcut sequence to work as it was doing just fine before my credential change and I do not understand why the behaviour has now changed. Call me a perfectionist I guess.... Any ideas?
 
2. **Protect GDM and xSplash Mods:** Since installing v9.10 today I have read up on GDM and xSplash and have been able to modify both quite well. I have changed the theme, icons, and background of GDM by launching "gnome-appearance-properties" at the login in prompt and making the desired changes. I have also changed my xSplash background and loading animation by adding custom images to usr/shared/images/xsplash. However, I would like to make sure that my mods are not overwritten in the case of a GDM and xSplash update being released by Canonical. My guess is that if an update is released all my images will be overwritten and my GDM changes will be erased. If this is so, is there a way of making sure my mods are not deleted and I have to reinstall them?
 
Please go easy on me if these are obvious questions, I am still learning. :)
This seems to be an awesome community so I am looking forward to your feedback.
 
Thanks!

---

### Post by monxster on 2009-12-28
BUMP!  Anyone???

---

### Post by Brandon Williams on 2009-12-29
> **monxster said:**
> After I did this I could access the "Aircraft Manager" via the menu or the shortcut directly. When I did this I was NOT prompted for any password of any kind.

I'm surprised by this. I have always been prompted for a password when starting aircraft-manager for the first time in a login session, unless I've recently run something else with sudo. Unless you reconfigure sudo to allow you passwordless access to aircraft-manager-util, you _should_ be prompted for a password.
 
> **monxster said:**
> I changed my user password from the root terminal "sudo passwd"

I'm not certain exactly what you did here. The standard way to change your user password is simply to run 'passwd' from a standard terminal ... no root terminal or sudo is required. Are you certain that you changed your user password? What you describe sounds like the method for adding a root password. 
 
> **monxster said:**
> However, ever since I changed my credentials, the "Aircraft Manager" now asks me for the system password upon launch via menu or keyboard shortcut!? Can someone please tell me how to bypass this password request and revert the launch sequence to the original status?

As I said above, that's the way I expect aircraft-manager to work. You can bypass the password by adding a line like this to the end of your /etc/sudoers file (use 'sudo visudo' to edit /etc/sudoers):

```
%admin ALL=NOPASSWD: /usr/bin/aircraft-manager-util
```

> **monxster said:**
> Given that "Aircraft Manager" in v9.10 does not feature persistence, "Aircraft Manager" will be one of my most commonly used apps as I will be switching bluetooth off everytime upon initial boot

If what you want is for the bluetooth radio to be disabled by default when you first log in, I suggest that you create a startup application that runs the following command line: 'gksu /usr/bin/aircraft-manager-util BT off' That way, you won't have to do anything actively when you first log in (assuming that you make the above change to /etc/sudoers).

> **monxster said:**
> Since installing v9.10 today I have read up on GDM and xSplash and have been able to modify both quite well. I have changed the theme, icons, and background of GDM by launching "gnome-appearance-properties" at the login in prompt and making the desired changes. I have also changed my xSplash background and loading animation by adding custom images to usr/shared/images/xsplash. However, I would like to make sure that my mods are not overwritten in the case of a GDM and xSplash update being released by Canonical. My guess is that if an update is released all my images will be overwritten and my GDM changes will be erased. If this is so, is there a way of making sure my mods are not deleted and I have to reinstall them?

How exactly did you make the changes you describe? Was it all done by using the config utilities and/or changing config files? Or did you replace any installed image and/or theme files with your desired alternatives? If you only modified existing config files and did not replace any image or theme files, you should be fine. If you did replace some image or theme files, tell us how you did it so that we know how safe your method was.

---

### Post by keelyizzy on 2009-12-29
im avin the same problem i have jus bought the dell mini inspiron and ive pressed f2 t turn the wi fi on ad its asking for an authorisation code can any1 help plz

---

### Post by monxster on 2009-12-29
[FONT=Consolas][SIZE=3]@Brandon Williams: [/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]> **Brandon Williams said:**
> The standard way to change your user password is simply to run 'passwd' from a standard terminal ... no root terminal or sudo is required. Are you certain that you changed your user password? What you describe sounds like the method for adding a root password. [/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]I am certain I successfully changed my username password. I say this because after my change the old password no longer works whereas the new one does. I was not aware that you could change a password without being root user or using sudo so the method I used for doing this was:[/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]```
gksu /usr/bin/x-terminal-emulator
```[/SIZE][/FONT]```

[FONT=Consolas][SIZE=3]passwd <myusername>[/SIZE][/FONT]
```
 
[FONT=Consolas][SIZE=3]I will bear in mind that this command can be executed directly next time which saves some time so thanks! As to whether or not this changed the 'root' password, I am not sure but I guess the insertion of <myusername> in the command means that did not happen. Is there a way to check the 'root' password is still the default to verify?[/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]> **Brandon Williams said:**
> Unless you reconfigure sudo to allow you passwordless access to aircraft-manager-util, you _should_ be prompted for a password.......You can bypass the password by adding a line like this to the end of your /etc/sudoers file (use 'sudo visudo' to edit /etc/sudoers): [/SIZE][/FONT]> **Brandon Williams said:**
> [FONT=Consolas][SIZE=3]```
%admin ALL=NOPASSWD: /usr/bin/aircraft-manager-util
``` [/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]Thanks for this. I modified /etc/sudoers as per your instructions and am now able to launch &#8220;Aircraft Manager&#8221; without a password being required. Also since you pointed it out, I do remember using terminal to install apps with &#8216;sudo apt-get install&#8217; before using the &#8220;Aircraft Manager&#8221; originally and that is why I guess originally it did not prompt me for a password. As for the bypass command, am I correct in assuming this password bypass will only apply to &#8220;Aircraft Manager&#8221;? Are there any security implications that I am missing with such a bypass? [/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]> **Brandon Williams said:**
> If what you want is for the bluetooth radio to be disabled by default when you first log in, I suggest that you create a startup application that runs the following command line: 'gksu /usr/bin/aircraft-manager-util BT off' That way, you won't have to do anything actively when you first log in (assuming that you make the above change to /etc/sudoers). [/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]This solution would be even better. How do I go about setting up a start-up application? Any good tutorials out there? Ideal solution would be to setup a startup script that turns off Bluetooth for my user account and a startup script that turns off WIFI and Bluetooth AND requires a password to activate either for a guest user account. [/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]Am I to assume that if I mod the line in /etc/sudoers to:[/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]```
%Admin <myusername>=NOPASSWD: /usr/bin/aircraft-manager-util
```[/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]Then the bypass will only apply to the &#8220;Aircraft Manager&#8221; running in my session and not the guests? If so then do you know how I could go about then making WIFI and Bluetooth be disabled on start-up and preserve the password requirement for activation on the guest session? [/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]> **Brandon Williams said:**
> How exactly did you make the changes you describe [to the GDM and Xsplash]?......tell us how you did it so that we know how safe your method was. [/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3]I modified the GDM by executing the following command from the terminal:[/SIZE][/FONT]
 
[FONT=Consolas][SIZE=3][COLOR=black]```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```[/COLOR][/SIZE][/FONT]
 
[COLOR=black][FONT=Consolas][SIZE=3]Then I logged out of my session and using the Appearance GUI box changed the Theme to &#8216;Clearlooks&#8217; the Icons to &#8216;Gnome&#8217; and the Wallpaper to my custom image. Once done I logged back in and removed the appearance GUI box from login screen with: [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Consolas][SIZE=3]```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Consolas][SIZE=3]I also added a custom login logo by running:[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Consolas][SIZE=3]```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/logo_icon_name --type string "<mylogo>"
```[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Consolas][SIZE=3]As for xSplash, I modified the background and startup animations by overwriting the files in:[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Consolas][SIZE=3]/usr/share/images/xsplash [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Consolas][SIZE=3]with custom images from my portfolio. The files I overwrote where bg_xxxxx, logo_xxxxx, and throbber_xxx[/SIZE][/FONT][/COLOR]
[FONT=Consolas][SIZE=3][/SIZE][/FONT] 
[FONT=Consolas][SIZE=3]I got these instructions from this great post: [http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683)[/SIZE][/FONT]
 
[COLOR=black][FONT=Consolas][SIZE=3]Will those MODs survive an update push? I read in the post the possibility of diverting the updates to dummy files but to be honest did not really get how that would work? [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Consolas][SIZE=3]Anyway thanks for the help and sorry for the long post and questions but I am still very green![/SIZE][/FONT][/COLOR]

---

### Post by Brandon Williams on 2009-12-29
Your original post didn't mention that you specified your user name when you ran passwd. Now it's clear to me that you changed the password you intended to change. Sorry about the confusion.

The change I suggested for /etc/sudoers allows any user who is part of the admin group to run aircraft-manager-util without entering a password. It won't allow a non-admin user (like the guest account) to run the command without a passwd, and it won't allow any other command to be run without a password. If you want just one user to be able to run aircraft-manager-util password-less, change '%admin' to whatever your username is.

I use XFCE, but IIRC, adding a startup app for Gnome works like this: System -> Preferences -> Sessions. On the 'Startup Programs' tab, click Add and fill in the fields in the dialog. The Name and Comment fields can be whatever you want. The Command field should be: gksu /usr/bin/aircraft-manager-util BT off

It sounds like your gdm config changes should survive gdm updates. Also, as long as you diverted the existing xsplash files before replacing them, as the instructions you used indicate, you should be fine with xsplash updates, too. Diverting the files tell dpkg that you moved them so that removing or upgrading the package will operate on the renamed files, not replacement files.

---

### Post by Brandon Williams on 2009-12-29
> **keelyizzy said:**
> im avin the same problem i have jus bought the dell mini inspiron and ive pressed f2 t turn the wi fi on ad its asking for an authorisation code can any1 help plz

Enter your password when it asks for authorization; whatever password you use to log in.

---

### Post by monxster on 2009-12-29
@Brandon Williams:
 
Thanks for the help and advice.  Have created the start-up app as advised and all is working well with bluetooth being switched off immediately on startup.
 
Understood about re the password bypass only applying to admin group users.  
 
Now that is sorted do you know how I could set the netbook to startup the guest sessions with WIFI and Bluetooth OFF by default as opposed to active?  I have small kids and they use the netbook but I do not like them to access the net unless supervised so it would be great if their account could initiate with both radio settings as off and then only activate once I enter the password.
 
As for the GDM and Xsplash changes, understood and thanks for the confirmation. 
 
I must say I am really enjoying using Karmic and I think if all goes well I will take the leap and also put it on my D630, SC440, and Samsung N140 (though I hear this model is not yet fully supported).  :)
 
The other thing is I run an Exchange Server 2003 box from my home for my email and was wondering if there are any mail clients that can sync using RPC over HTTPS?

---

### Post by Brandon Williams on 2009-12-29
> **monxster said:**
> Now that is sorted do you know how I could set the netbook to startup the guest sessions with WIFI and Bluetooth OFF by default as opposed to active?  I have small kids and they use the netbook but I do not like them to access the net unless supervised so it would be great if their account could initiate with both radio settings as off and then only activate once I enter the password.

You could add this entry to sudoers:
```
All ALL=NOPASSWD: aircraft-manager-util BT off,aircraft-manager-util WIFI off
```

It will allow all users to turn off WIFI and BT without a password. Then, you can add startup apps for the guest user that will turn off bluetooth and wifi. The wifi command looks the same as the BT command that you've already used ... just substitute WIFI for BT in the command line.


As for your question re: RPC and HTTPS, it's probably best to start a new thread in the networking issues form.

---

### Post by monxster on 2009-12-29
You are right. I will do some research re RPC of HTTPs and if required will start a new thread. 
 
As for your suggestion to use:
 
```
All ALL=NOPASSWD: aircraft-manager-util BT off,aircraft-manager-util WIFI off
```
 
I can see how that would work but ideally once the wifi and bt is off, I would like for my kids not to be able to simply open the aircraft manager up or click on the wireless icon and activate the wifi or bt without having to input an admin password from myself or thier mum so is their a way to get the "aircraft-manager-util" to request a password if activated from the guest session once the radios have been turned off?  I know it sounds a bit harsh but they once managed to activate the internet when my phone was tethered to it and not knowing the charges watched tons of online cartoons and cost me an arm and a leg!  So preferably would want to avoid a relapse...  
 
Thanks again buddy.

---

### Post by Brandon Williams on 2009-12-29
The command lines that my suggested sudo config allow are only those that turn the wifi and bluetooth off. All other command lines, including the ones to turn the wifi and bluetooth back on, would still require a password.

Take a look at the man page for sudoers to get a better idea of how the suggested config works.

---

### Post by monxster on 2009-12-30
@Brandon Williams:  

Re read your post and immediately saw what you meant re the password bypass only applying to turning off the radio.  I have modified sudoers accordingly and then also added a line bypassing password to turn it on for my user only and added the appropriate startup apps and all is working like a charm!

Thank you for your help and advice.

---

### Post by monxster on 2009-12-30
-deleted double post-

---

