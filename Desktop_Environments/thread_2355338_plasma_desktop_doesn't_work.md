---
title: "plasma desktop doesn't work"
date: 2017-03-11
forum: Desktop Environments
---

### Post by pagno2 on 2017-03-11
[COLOR=#111111][FONT=Ubuntu]I installed Plasma desktop following instructions in this site
[/FONT][/COLOR][http://www.tecmint.com/install-kde-plasma-5-in-linux/]("http://www.tecmint.com/install-kde-plasma-5-in-linux/")
[COLOR=#111111][FONT=Ubuntu]however it is not running.
Ubuntu keeps running Gnome at start.
 I also tried the console ctrl alt f1 but I can't login. I don't know what to write to login. Can't I do it through terminal?
GA[/FONT][/COLOR]

---

### Post by Frogs Hair on 2017-03-11
Hello and Welcome

Did you select the KDE session during login per the instructions.

---

### Post by pagno2 on 2017-03-12
Thanks [COLOR=#000000]Frogs Hair
not really
I am new to ubuntu (just a couple of months in Mint then I switched to Ubuntu as it seems more stable on the machines I have).
I never fully understood this login issue. When I press ctrl alt f1 the screen turns black. Something like the terminal but not the terminal. Then I am supposed to digit a login and a password. I do know the password but I do not know the login. I guessed it was the account name, however it doesn't work and I'm stuck there with a login request and I have to switch off the pc and restart.
GA[/COLOR]

---

### Post by Frogs Hair on 2017-03-12
I'm referring  to the instruction on the page you linked and selecting plasma from the greeter box icon. 
[http://www.tecmint.com/install-kde-plasma-5-in-linux/](http://www.tecmint.com/install-kde-plasma-5-in-linux/)

---

### Post by pagno2 on 2017-03-13
Hi Frogs Hair
if you refer to "it will ask you to configure sddm login manager, click OK and select the &#8216;lightdm&#8217; login manager as default" that window never popped up. At least I never saw it so I couldn't tik the choice.
GA

---

### Post by Frogs Hair on 2017-03-13
The instruction is for 16.10 only so be sure that's what you're using.   I would then enter all the instruction's commands one by one to make sure you didn't miss anything. It shouldn't  cause any problems and it will ensure you followed all the steps.

---

### Post by pagno2 on 2017-03-13
I have Ubuntu 16.10 installed
I followed your suggestion and evidently I did something wrong in earlier installation of plasma. In fact at the command instruction "$ sudo add-apt-repository ppa:kubuntu-ppa/backports" I get stuck with a "$: command not found".
Has kubuntu something to do with this?
GA

---

### Post by Frogs Hair on 2017-03-13
The command works here though it is not a trusted key. Open software & updates and enable all Ubuntu sources excluding sources code, then in other  software tab enable the Canonical Partners repository. Try the command again.  


```
sudo add-apt-repository ppa:kubuntu-ppa/backports
[sudo] password for d-book: 
 Backports of new versions of KDE Platform, Plasma and Applications as well as major KDE apps for Kubuntu.
 More info: https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/backports
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keybox '/tmp/tmpgj0krsgd/pubring.gpg' created
gpg: /tmp/tmpgj0krsgd/trustdb.gpg: trustdb created
gpg: key 2836CB0A8AC93F7A: public key "Launchpad Kubuntu Updates" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
OK

```

---

### Post by pagno2 on 2017-03-13
I tried again and this time it worked for the first part. I had made a mistake in the command.
Nevertheless an error came out 

Errors were encountered while processing: /tmp/apt-dpkg-install-EgZ4BE/501-kaccounts-providers_4%3a16.04.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

and I couldn't "configure sddm login manager", nor "select the &#8216;lightdm&#8217; login manager as default" as requested.
GA

---

### Post by Frogs Hair on 2017-03-13
I don't see a reason to use a PPA when installing kubuntu-full includes the plasma widgets. :confused: Try the following commands.  

```
sudo apt-get update
``` ```
sudo dpkg --configure -a 
```

---

### Post by pagno2 on 2017-03-14
The process went well.
"Done" at the end.
However I do not see any "plasma" installed. Perhaps it is possible only through kubuntu.
GA

---

### Post by pagno2 on 2017-03-15
Now after boot the sign "kubuntu" pops up in the middle of the black screen, but at the end I found my self in the ubuntu 16.10 desktop and nothing seems to have changed.

---

### Post by Frogs Hair on 2017-03-15
After a lengthy installation the instructions provided worked, the first login was very slow though . Try the following  command.

```
sudo apt-get -f install 
```

---

### Post by pagno2 on 2017-03-15
Same situation. Kubuntu word blinking at boot then it ends up to Ubuntu 16.10.
Perhaps there is something missing in the process. I thought I could install plasma from ubuntu, I am afraid I might mess up something keeping on with this mixed ubuntu/kubuntu installation.
I am trying to switch to a better interface, isn't there an easy interface? I liked cinnamon but I think it is meant for Mint as plasma for kubuntu.
GA

---

### Post by Frogs Hair on 2017-03-15
Well, it took an hour to remove the ppa and the KDE / Kubuntu desktop components  which are installed when using the instruction.  Have you considered trying an Xubuntu live session to see if you like it. It is a more traditional DE. Having more than one desktop is less than ideal due to bloat caused application duplication.

[https://www.youtube.com/watch?v=wLNqn2wjGms](https://www.youtube.com/watch?v=wLNqn2wjGms)

---

### Post by Perfect Storm on 2017-03-15
elementary OS is pretty simple interface Pantheon, check my signature.

---

### Post by Frogs Hair on 2017-03-15
> Same situation. Kubuntu word blinking at boot then it ends up to Ubuntu 16.10. Remember when you get to the login screen to select the plasma session as in post # 4 . Select the icon on the top right of the greeter/login box.

---

### Post by pagno2 on 2017-03-17
> **Frogs Hair said:**
> Remember when you get to the login screen to select the plasma session as in post # 4 . Select the icon on the top right of the greeter/login box.
That is the problem. I don't see any login screen. I just see the blue word kubuntu after boot, but then it ends up into the ubuntu 16.10 desktop. When I shut down I once again see the blue word kubuntu.
But a part from this word I never see anything different from classical Ubuntu 16.10 installation, not at any moment.
GA

---

### Post by Frogs Hair on 2017-03-17
The sequence I saw was the flashing Kubuntu followed by login screen where I selected plasma and after a long pause the desktop loaded. This might have something to do with your graphics card also. When I followed the tutorial everything happened as stated including selection of lightdm in the terminal.

---

### Post by deadflowr on 2017-03-17
> **pagno2 said:**
> That is the problem. I don't see any login screen. I just see the blue word kubuntu after boot, but then it ends up into the ubuntu 16.10 desktop. When I shut down I once again see the blue word kubuntu.
But a part from this word I never see anything different from classical Ubuntu 16.10 installation, not at any moment.
GA

Do you have autologin set?

---

### Post by pagno2 on 2017-03-17
Is it a sw? If so no, I don't have it.
GA

---

### Post by deadflowr on 2017-03-17
> **pagno2 said:**
> Is it a sw? If so no, I don't have it.
GA

What's sw?

---

### Post by pagno2 on 2017-03-21
> **Frogs Hair said:**
> The sequence I saw was the flashing Kubuntu followed by login screen where I selected plasma and after a long pause the desktop loaded. This might have something to do with your graphics card also. When I followed the tutorial everything happened as stated including selection of lightdm in the terminal.
Graphic card is a very new AMD Radeon. It might be the issue.

deadflowr I don't know what the autologin set is.
GA

---

### Post by deadflowr on 2017-03-22
> deadflowr I don't know what the autologin set is.
In the regular Ubuntu desktop,  go to System Settings >> User Accounts.
There is an option to set the user to autologin here 
It's marked as Automatic Login and has a toggle button to turn it on or off.
The autiologin option can also be set during installation.
It does what it's name implies, automatically logs you in, without user intervention.

---

### Post by pagno2 on 2017-03-26
OK thanks.
I did set (unlock) the autologin but nothing happened.
Should I uninstall kubuntu and restart? KDE plasma basic installation?
GA

---

### Post by Frogs Hair on 2017-03-26
> **pagno2 said:**
> OK thanks.
I did set (unlock) the autologin but nothing happened.
Should I uninstall kubuntu and restart? KDE plasma basic installation?
GA
  

Plasma is feature of the Kubuntu desktop and the PPA you used provides the newest version . Removing Kubuntu would not allow you to login, you can remove the PPA and Kubuntu , but it is lengthy process to remove all of it . Have you considered a clean installation of Kubuntu or another Ubuntu flavor ? In the time you have into this you could have tried and installed a different flavor.

---

### Post by pagno2 on 2017-03-26
I reinstalled following again this tutorial [http://www.tecmint.com/install-kde-plasma-5-in-linux/](http://www.tecmint.com/install-kde-plasma-5-in-linux/)
Nothing changed.
According to the tutorial during installation, it asks to configure sddm login manager, but that doesn't happen. There is no OK to click nor &#8216;lightdm&#8217; to select in order to set login manager as default.
GA

---

### Post by pagno2 on 2017-03-27
I realized that in the settings there was a KDE settings and plasma wasn't enabled. I did it and restarted.
Now I see the plasma desktop with the plasma icons at the bottom end of the screen and the classical gnome/ubuntu icons at the top.
Still no choice appears at start.
I probably have to work it out in the settings.
GA

---

### Post by Frogs Hair on 2017-03-27
Glad to here you were able to access Plasma , but there's something wrong if you see no option at login and you didn't see the light dm setup screen.

You might try the following.

```
sudo dpkg-reconfigure lightdm
```

---

### Post by pagno2 on 2017-03-27
Thanks Frogs Hair
Everything is good to me for practicing.
I decided to uninstall plasma and tried to uninstall kubuntu.
I successfully did the first, not yet the second. Kubuntu icon still flashing at boot.
However the system works properly.
I set Ubuntu desktop in a way fine to me. When I have a couple of hours I'll install ubuntu 16.4 into a third partition and when it is ok I'll format the 16.10 partition and use it for future tries.

---

### Post by deadflowr on 2017-03-27
> Kubuntu icon still flashing at boot.
feels like that's the [plymouth]("https://wiki.ubuntu.com/Plymouth") theme.
try removing with
```
sudo apt-get remove plymouth-theme-kubuntu-logo plymouth-theme-kubuntu-text
```

---

### Post by pagno2 on 2017-04-19
Thank you deadflowr
that did work
I don't see any kubuntu sign anymore
however I think the several processes I did might have messed up something as I have some issues, for example I can't install Overgrive and I don't see zipped files on the desktop though I see them from the file manager.
I'll open a specific thread.
Thanks
GA

---

