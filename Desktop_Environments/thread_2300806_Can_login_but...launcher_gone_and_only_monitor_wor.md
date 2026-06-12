---
title: "Can login but...launcher gone and only monitor works. How to fix?"
date: 2015-10-28
forum: Desktop Environments
---

### Post by Effi_Sland on 2015-10-28
[TABLE]
[TR]
[TD="class: votecell"] 

              [/TD]
              [TD="class: postcell"]        I've been a Ubuntu user about 2 years. I am using the same user  account and have most defaults for upgrading etc and have the current  version and updates.


  I can login to my account but can't get anything to work really as  the Launcher does not appear. My shortcut to system monitor works and I  can access the System settings however once I open that window I can't  close it. The icons like time, sound, in the upper right corner are not  there anymore.

  
The only thing I did today was I changed my background to use my  pictures folder and turned off the launcher 'hide'. The background  picture didn't change so I went back in and did it again. I couldn't  close out of that window and I couldn't open anything else. I opened a  guest account and shut down from there. I could re-login as my main user  but the launcher didn't appear and I couldn't do anything else...but I  could create another admin account.

  
So, I have admin status but everything on the computer belongs to my  main user account, so I can't delete anything. I'd rather not start over  with a new account, but when I login as my main user I can't do  anything!! Help...

     

[/TD]
[/TR]
[/TABLE]

---

### Post by dino99 on 2015-10-28
you did not said which flavor/DE its about, so ... only can propose to watch the logs to find something usefull; and resetting/reconfiguring/cleaning the system

---

### Post by Effi_Sland on 2015-10-28
I'm logged in as a new user and it's 64 bit Ubuntu Version 15.04 - thought I had been keeping up with upgrades so should be 15.1, not sure why it's not.

Do how do I reset/reconfigure/clean the system if I can't really do anything? Maybe command line instructions would help.

---

### Post by grahammechanical on 2015-10-28
Here is something that you can try.

At the Grub boot menu select Advance Options for Ubuntu and the select recovery mode. At the recovery menu select Resume. Does that get you to a working desktop? If it does go to System Settings>Software & Updates>Additional Drivers tab and experiment with a different video driver.

Resume.

---

### Post by Effi_Sland on 2015-10-30
Thanks for that. I have an inkling of what you are talking about however since after booting it just goes directly to login and doesn't stop at grub I'm not sure how to get it to start doing that. Special keystroke? Sorry for this lameness, I will also see if I can find a thread on that. In the meantime I am installing 15.1, maybe it's just a coincidence but I was never offered the opportunity and it was only after I created a new user account that it asked me to upgrade. Am hoping it will fix the video driver if thats what it is. I have a feeling it is because it's been freezing up quite regularly these days...and if its not the video driver doing that I was thinking about exiting this Ubuntu experiment...so I'm hoping it is .... if not maybe it's just my box.

---

### Post by zeke2135 on 2015-10-30
This sounds very similar to what I am experiencing. I see the following things:

- There is no launcher, no menus or top bar, shortcuts like the super key don't work.
- I can also bring up the system monitor app with ctl-alt-delete as said above.
- Only one user, my admin user, can log in from the GUI. Other users get a notification that the password is incorrect. However, another user can log in through ssh.

- This is interesting, I can see compiz running, but it is only using about 2MB, whereas it usually uses ~30MB and up

So it seems that somehow compiz is not running normally. I've tried using sudo apt-get install --reinstall to reinstall compiz, unity, ubuntu-session, the xserver and lightdm.

I'm running ubuntu 14.04.3. I tried the idea to select advanced options and recovery mode. It did not work. The desktop looks the same, but low res.

---

### Post by deadflowr on 2015-10-30
Have either of you tried the reset commands?
```
dconf reset -f /org/compiz/
setsid unity
```

Note that some users experience a logout (which shouldn't happen normally)
when performing these commands.
But it should reset to unity's default settings.

---

### Post by zeke2135 on 2015-10-30
I tried the reset commands. The first time, it didn't work. After I read the suggestion, I tried again to see if I could look for some output, and voila, it worked, sort of. 

The system settings dialog doesn't work: intermittently, the individual settings panels pop up briefly, and close immediately. 

After reinstalling unity-control-center, the settings panel works somewhat better I think, but consitently won't pop up the user accounts panel. I get the following if I start it from command line:

```

libwayland-egl.so.1: cannot open shared object file: No such file or directory
Failed to load module: /usr/lib/x86_64-linux-gnu/unity-control-center-1/panels/libuser-accounts.so

```

I tried reinstalling the vivid enablement stack after reading
[http://askubuntu.com/questions/672620/how-to-fix-missing-libwayland-egl-so-1-and-libuser-accounts-so-in-ubuntu-14-04-3](http://askubuntu.com/questions/672620/how-to-fix-missing-libwayland-egl-so-1-and-libuser-accounts-so-in-ubuntu-14-04-3)
and I get:

```
The following packages have unmet dependencies:
 libwayland-egl1-mesa-lts-vivid : Depends: libegl1-mesa-lts-vivid (= 10.5.9-2ubuntu1~trusty2) but 10.5.9-2ubuntu1~trusty3 is to be installed
```


BTW I am running the vivid kernel and vivid x server, which would no doubt be the same as [[COLOR=#000000]Effi_Sland running 15.04.[/COLOR]]("http://ubuntuforums.org/member.php?u=2007140")

---

### Post by Effi_Sland on 2015-10-30
...still waiting for 15.10 install to complete...

Other weird symptoms:
- noticed things slowing down, checked system monitor, there was a huge flow of outgoing network traffic, closed firefox and no bittorrent running (never upload anyway) - so something was uploading to somewhere. Turning off my connection fixed that but no idea what it was doing.

- when browser got stuck I noticed in system monitor some plugin running that was stalled so I killed it and it fixed the problem (everything else was frozen). That got me into the bad practice of checking system monitor and killing processes that seemed suspicious when there were problems. I recall now that I was doing this prior to my other issues. However if I killed vital system processes shouldn't they start up again when I rebooted?

---

### Post by Effi_Sland on 2015-10-30
Installed 15.10. No difference. Can't get Terminal to start.

---

### Post by zeke2135 on 2015-10-30
Effi_Sland, How are you trying to start the terminal? Ctl-alt-F1 should give you a terminal, and Ctl-alt-F7 should get you back to the desktop.

---

### Post by deadflowr on 2015-10-30
```
ctrl +alt + T
```
should open a terminal in a desktop.

Also, Ubuntu has the file manager handle the desktop, so you might be able to try right clicking.
If the right click opens a menu with new document new folder, open a new folder.
Then open that folder which will open the file mansager.
Then go to the left side pane and go to Computer.
Then go to **usr**, then to **share**, then to **applications**.
Scroll down the applications folder and find the Terminal app.
click on it to open.


It's unclear if you ever tried this, so...

---

### Post by Effi_Sland on 2015-10-30
> **zeke2135 said:**
> Effi_Sland, How are you trying to start the terminal? Ctl-alt-F1 should give you a terminal, and Ctl-alt-F7 should get you back to the desktop.

Yes it did, fullscreen. asking me my login. What is it again? Finally had to restart. Logged back in (I had the password correct) but my name (which I assumed is my 'login') has a space in it.

I can get a terminal by right clicking on the desktop and selecting it. Miraculously I can start firefox from the terminal!

I can quit boxes with Control Q, there is no other way (no X in the corner, or resizing). I must have killed all these processes. Rebooting does not reset them. Possible to restart it with default?

---

### Post by Effi_Sland on 2015-10-30
> **deadflowr said:**
> Have either of you tried the reset commands?
```
dconf reset -f /org/compiz/
setsid unity
```

Note that some users experience a logout (which shouldn't happen normally)
when performing these commands.
But it should reset to unity's default settings.

That definitely starting doing something, however I got this error showing up twice:

```
Error: Plugin 'opengl' not loaded
```

We're getting somewhere!

This all started when I was trying to track down whatever was taking up so much uploading space - was probably firefox...

I see running as "Whoopsie" and taking up 437.1 MiB of virtual memory...kill it and it pops back up again. But I could only kill it after login/pswd

---

### Post by deadflowr on 2015-10-31
An opengl plugin error usually means a graphics driver problem
Do you know what graphics card you have?

Sidenote #1: Whoopsie is part of the Ubuntu crash reporting system. Comically part of whoopsie >> daisy.

Sidenote #2: Sometimes doing things like fixing breakage can be eased by installing a secondary desktop.
I think the gnome flashback session is the best in relation to Ubuntu as it has a no effects option.
And it is very compatible with Ubuntu as a whole. (Meaning it doesn't install extra stuff like terminals and file managers)
You can simply run:
```
sudo apt-get install gnome-session-flashback
```
then logout and in the login page click on the icon in the username/password window>>top right corner of that little window.
You then choose gnome flashback no effects.

It'll give you an old style session, but more importantly, it'll give you the ability to navigate more easily to figure out how to fix things.
imo.
Just a suggestion ,though.

---

### Post by Effi_Sland on 2015-10-31
Yes! Thank you! I am in, and actually I like the old style. More importantly all the functionality is there.

Assume I need to correct my display drivers - started 'System Testing' and no issues there.

Will prioritize some learning on these so I'm not so feeble when something goes wrong...thanks again!

---

