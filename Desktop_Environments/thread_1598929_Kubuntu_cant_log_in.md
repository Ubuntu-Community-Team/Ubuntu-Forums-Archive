---
title: "Kubuntu cant log in"
date: 2010-10-17
forum: Desktop Environments
---

### Post by maz32 on 2010-10-17
hello all
I have put on kubuntu over my Ubuntu installation and from what i had read it just changes the look but now all my users are gone and i cant make a new one and if i put the correct information in the user and password filed it says im wrong 

when i changed over i couldn't see an options at Ubuntu log in screen so i changed to kubuntu with the terminal 

is there any way to make a new user , retrieve the old user or change back to Gnome (vanilla Ubuntu) 

thanks matt

---

### Post by ankspo71 on 2010-10-17
Hi,
Are you able to use the computer at all because of this?

You won't see any options in the login screen until after you click on the username you want to log in with. I think this applies to both Kubuntu and Ubuntu, but I definitely know that it applies to Ubuntu. Or did that fail to work? You should have been able to at least log in though.

If you can still use one of the desktops, then this link shows how you can remove the Kubuntu and return to a pure Ubuntu. The process involves removing all of the packages that came with Kubuntu, then reinstalls Ubuntu to make sure there are no Ubuntu packages missing.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Before you remove Kubuntu though... you might still be able to use it (if you still want to use it, I mean). The part where you say your users are missing and all passwords are wrong leaves me wondering what is going on though. It could be only that the Kubuntu's display manager "KDM" (login window) is not working. Hopefully isn't more than that. Can you press **Ctrl+**Alt+F2 at this point, and log into the terminal sucessfully? If you can then type this command: (Edited:Sorry that was supposed to be Ctrl+Alt+F2)
```
sudo /usr/sbin/update-alternatives --config x-session-manager
```
With that command you will be able to choose between KDM and GDM.
Choose GDM if KDM is not working. (KDM is the blue login window for Kubuntu, and GDM is the Ubuntu default purple and brown login window).

Now you can reboot with the command:
```
sudo reboot
```
Now hopefully you will be able to log in when the computer restarts.

Hope this helps.

---

### Post by maz32 on 2010-10-18
i wasn't able to use the computer but after a while i tried again pressing ctrl alt f1-12 tried everything and one of them just did nothing for a while just blinked in the top left corner put in the same information as i did before in the log in screen  and it just worked 
 
thanks anyway ankspo im sure this would have helped if nothing else worked,  it was the sort of answer i was looking for. im sorry for causing too much hassle

---

