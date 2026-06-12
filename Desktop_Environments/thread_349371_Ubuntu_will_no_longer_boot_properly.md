---
title: "Ubuntu will no longer boot properly"
date: 2007-01-30
forum: Desktop Environments
---

### Post by m_memmory on 2007-01-30
Last night I was attempting to install some fancy looking graphical wonders on Ubuntu (Edgy) and tried XGL with Compiz but got no where.  Then I read that AIGLX with Beryl might work better so installed that and it worked without a problem and looked great.

However I noticed that under the Beryl Window Manager I was able to select between the Gnome default window manager (whose name escapes me at the moment), Beryl window manager and also Compiz and for a test I selected Compiz which then froze the system up - the windows all lost their borders/title bars and nothing responded.

I ended up doing a restart of the computer and now, whenever I restart, I get nothing.  Ubuntu automatically boots into my user account on start-up and gets to the point of showing a orangey coloured background and then stops.  This is normally when my background would show and the taskbars would show up but nothing happens at all.  If I then do 'Ctrl', 'Alt' and 'Backspace' then the login window shows but after attempting to login I get a window saying "I notice that there is already a pane running and I will quit" (or words to that effect) and it freezes up again.

I've tried doing different login sessions from when I get the login window up but everyone of them says the same error message and crashes (even the default Gnome login and the one that runs no scripts on login) - the only one that does work is the one for the Terminal but from there I don't know what to do.  I've had a look at some of Beryl's user files in my Home directory but I can't see anything in there that'll sort it out.

Could someone please give me some advice as to what I can do that'll get Ubuntu up and running again please?  At the moment I'm stuck with my alternate boot-up of Windows and it's annoying me already ... I want Linux back!!

Thanks for any advice/suggestions that you can think of.

---

### Post by nkkromhof on 2007-01-30
One suggestion would be to hit CTRL-ALT-F2, this will give you the opportunity to log in in text mode.

Log in with your username and password, this should give you a command line.

At the command line type 

```
killall gnome-panel
```

This will kill the running Gnome panel and makes it restart automatically.

Use CTRL-ALT-F7 to go back to your graphical desktop


Hope this help, just post here if you run into any other problems!

---

### Post by m_memmory on 2007-01-30
Thanks for the advice but it doesn't seem to have helped.  It boots up, stops, and then I tried killing the gnome-panel and doing CTRL-ALT-F7 but I just got a black screen with the mouse cursor displayed over the top.

I tried doing a few more logins under different sessions and I'm still thinking that it's some setting that I've done under Beryl.  Is there a file somewhere that I can move or delete that will reset Beryl back to default or something?  As I think that might help ... or at least prove that I'm wrong with my thinking.

---

### Post by nkkromhof on 2007-01-30
While you're at the text terminal with CTRL-ALT-F2, type "ps -e", this will list all running processes. Look through the list and use killall to kill anything beryl, compiz related.

Also, when you've got the mouse cursor on the black screen try hitting CTRL-ALT-Backspace (this would be my first recommendation)

As a last ditch effort you could use ALT + SysRQ (Printscreen key)+ k to kill all processes this should return you to the GDM login screen, you might have to use the right ALT key. I have heard reports that this can potentially mess things up, but I've had to use it several times myself without serious problems, just a fair warning though.

---

### Post by m_memmory on 2007-01-30
Thanks for the tip.

I've actually been able to boot myself back into Ubuntu again now.  I don't know what made me think of trying it but I tried 'apt-get remove' beryl and was then able to login without any trouble back to my default desktop.  However if I then install beryl and run the beryl-manager the screen seizes up as it's attempting to install.

So I guess I was able to prove to myself that there's something wrong with the settings for beryl.  Now it's just a case of finding them and resetting them back to normal again I guess.

Thanks for the assistance.

---

### Post by nkkromhof on 2007-01-30
If you're running an nVidia card then you don't need AIGLX and you're better off using the nvidia-glx drivers.

I highly recommend using this how-to: [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

---

### Post by m_memmory on 2007-01-30
Thanks once more :)

As it happens it seems that I am using the nvidia-glx drivers for my nvidia card.  I did a search in Synaptic Package Manager for whatever AIGLX I might have installed and it seems to suggest I don't have any ... so maybe I uninstalled them when I was messing about yesterday or something.

Anyway I've got Beryl up and running again now.  I deleted the .beryl files/folder from my home directory and ran the beryl-manager again and it all seems to be back to normal again.

Thank you for your help - it's really annoying when something stops working and your unable to gain access to your desktop.

---

### Post by nkkromhof on 2007-01-30
> **m_memmory said:**
> it's really annoying when something stops working and your unable to gain access to your desktop.

I know that feeling!

Glad you got it figured out!

---

### Post by hal10000 on 2007-01-30
> ....it's really annoying when something stops working and your unable to gain access to your desktop

Just a hint

If your xserver refuses to start, there is the log file /var/log/Xorg.0.log which in many cases can give you hints on what happened, also your /home/yourname/.xsession-errors file can help if  you get weird behaviour when running graphical programs

---

