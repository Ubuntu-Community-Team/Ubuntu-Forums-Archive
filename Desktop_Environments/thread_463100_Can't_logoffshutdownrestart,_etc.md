---
title: "Can't logoff/shutdown/restart, etc"
date: 2007-06-03
forum: Desktop Environments
---

### Post by xwisdom on 2007-06-03
Hello,

I'm having a problem in feisty. All was working fine until one day I tried logging off and the computer freezes just when I click the logoff/shutdown or restart button. I can still move the mouse but the logoff panel remains on screen with the button that I have clicked. I can do ctrl-alt-f1 etc but I can't get the system to logout and go back to the login prompt. I'm using an integrated video card and all was working before. The last thing I remember installing was acl but I don't think that should have any effect on the gui. The strange thing is that I'm able logoff when using an LTSP client but I can't logoff when I'm on the local PC

Any ideas? Could this be a gnome/gdm issue?

Many thanks

---

### Post by aliyanage on 2007-06-03
did you already try shutting down from the terminal?

```
sudo shutdown -r now
```


regards
aliyanage

---

### Post by xwisdom on 2007-06-04
> **aliyanage said:**
> did you already try shutting down from the terminal?

```
sudo shutdown -r now
```


regards
aliyanage


Yeah that works but I have to press ctrl-alt-f1 and login to shut down the system. It's the GUI screens that are not working. It just freezes after I click on any of the logout buttons. It even freezes when I click on the cancel button. If I press ctrl-alt-backspace then it logs me out.

Do you know what I can reinstall to fix the session that deals with the logout screens?

---

### Post by floke on 2007-06-04
Are you using restricted drivers?
I had this problem with the ATI driver until I disabled it.

---

### Post by xwisdom on 2007-06-04
> **Steve.K said:**
> Are you using restricted drivers?
I had this problem with the ATI driver until I disabled it.

not as far as I know. My video card is built into the motherboard so it's not one of those 3d cards. Te strange thing is that it was working before.

---

### Post by floke on 2007-06-05
It could be a gdm issue - I've had this problem with gdm borks before too.
You could try - I think it';s this - sudo dpkg-reconfigure gdm
Or, failing that install and use KDM instead and see if that works - if it does at least you'll know its a gdm issue.

---

### Post by xwisdom on 2007-06-05
> **Steve.K said:**
> It could be a gdm issue - I've had this problem with gdm borks before too.
You could try - I think it';s this - sudo dpkg-reconfigure gdm
Or, failing that install and use KDM instead and see if that works - if it does at least you'll know its a gdm issue.

Thanks will give it a try

---

### Post by vanadium on 2007-06-05
I also have this issue from time to time, especially after using XMMS. However, at the point where the system "freezes", I can kill the X server using Ctrl+Alt+Backspace and from then on, the system continues to shut down as if nothing happened. It is one of those issues with Feisty that I can live with, although I wished they weren't there.

---

### Post by vanadium on 2007-06-05
I also have this issue from time to time, especially after using XMMS. However, at the point where the system "freezes", I can kill the X server using Ctrl+Alt+Backspace and from then on, the system continues to shut down as if nothing happened. It is one of those issues with Feisty that I can live with, although I wished they weren't there.

---

### Post by floke on 2007-06-05
I have a recurring issues now and again with the r.init local scripts freezing on shutdown. 
I ctrl-alt-F1 to tty and run: sudo /etc/init.d/gdm restart
This takes me back to the login screen from where I can then shut down normally.

---

### Post by xwisdom on 2007-06-06
I've tried the sudo dpkg-reconfigure gdm but I'm still experiencing the same problem. 

So from what we know it's

1) Is it GDM that's causing this?
2) Is it GNOME?
3) Does this problem only exists in Feisty?

---

### Post by FuturePilot on 2007-06-06
Are you by chance running xcompmgr? If I run that and try to shutdown it appears that everything has frozen. But it's just that the shutdown menu has popped up but is not visible. If I click on the right spot, where the shutdown button would be it shuts down.

---

### Post by obiyoda on 2007-06-08
I have the same issue. I am running Edubuntu and am wondering if you are also running edubuntu since you mentioned LTSP. If you are it may be an issue with LTSP/edubuntu. The computer I am running on is an e-machine with an onboard NVIDIA GEFORCE 6100. I wonder if you have any of the same components.

---

### Post by obiyoda on 2007-06-08
I found a solution. It seems it is a problem with LTSP.  If you follow theses instructions it should help. Worked on my setup here.
[http://ubuntuforums.org/showpost.php?p=2433293&postcount=15](http://ubuntuforums.org/showpost.php?p=2433293&postcount=15)

---

### Post by Rui Pais on 2007-06-13
> **FuturePilot said:**
> Are you by chance running xcompmgr? If I run that and try to shutdown it appears that everything has frozen. But it's just that the shutdown menu has popped up but is not visible. If I click on the right spot, where the shutdown button would be it shuts down.

Hi,

Any solution/workaround on this? 
(besides set session to close without ask for confirmation... or hit ghosts buttons ;))

---

