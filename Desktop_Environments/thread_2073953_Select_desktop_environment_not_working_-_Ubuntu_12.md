---
title: "Select desktop environment not working - Ubuntu 12.10"
date: 2012-10-20
forum: Desktop Environments
---

### Post by Canaryguy on 2012-10-20
Hello,

I installed Ubuntu 12.10 x32 and after that I installed the Gnome Shell Desktop Environment but when I log out and try to change to Gnome I see the option but I cannot select it, it doesn't work.

Anybody having the same problem?

---

### Post by SMOKE14 on 2012-10-20
I just installed Gnome, and what you have to do is select the desktop environment, then click OK. Log in, and you should have it.

---

### Post by Canaryguy on 2012-10-20
I installed Gnome successfully through the Software Center. Short after the instalacion it asked me what gdm I wanted and I left the default option "lightgdm" Then I logged out and in the logging screen, before writing my password I try to change to Gnome but I cannot select it, the list of the other desktops environments that I have installed appear but I cannot select any of them.

---

### Post by SMOKE14 on 2012-10-20
Did you just log out, or did you restart? If you just logged out, try completely restarting, then try to select it, then OK, then your password.

---

### Post by Canaryguy on 2012-10-20
I tried logging out, restarting the computer and even turning it off. The only thing I haven't tried is to uninstall and reinstall it again.

---

### Post by SMOKE14 on 2012-10-20
Then I am at a complete loss. You might try uninstalling then reinstalling the environment.

---

### Post by Canaryguy on 2012-10-20
Well, thanks anyway. The solution will turn out sooner or later :-)

---

### Post by Nick Payne on 2012-10-20
After selecting Gnome, did you click on OK? It's now a two step rather than a one step process...

---

### Post by Frogs Hair on 2012-10-20
Try the tab and enter key . This was happening in beta 2  but was resolved  with an update two weeks ago.  Make sure you are up to date.

---

### Post by Canaryguy on 2012-10-20
Well, I found out what the problem was. It sounds really stupid hahaha.

Well, I had installed different desktop environments so when I logged out to use one of them I saw the list but I couldn't see the OK button because my screen is not big enough (I'm using a netbook). I thought I had just to click on the desired desktop enviroment but, as Nick Payne said, you also have to click on the OK button (which it was not displayed).

Well mystery solved.

Thank you guys for your help.

---

### Post by SMOKE14 on 2012-10-20
> **Canaryguy said:**
> Well, I found out what the problem was. It sounds really stupid hahaha.

Well, I had installed different desktop environments so when I logged out to use one of them I saw the list but I couldn't see the OK button because my screen is not big enough (I'm using a netbook). I thought I had just to click on the desired desktop enviroment but, as Nick Payne said, you also have to click on the OK button (which it was not displayed).

Well mystery solved.

Thank you guys for your help.
Thought I had said that :confused:
But glad you got it working! :D

---

### Post by Miles_T on 2012-10-23
Hi
Where is that ok button supposed to be?
I can not see it

---

### Post by Canaryguy on 2012-10-23
> **Miles_T said:**
> Hi
Where is that ok button supposed to be?
I can not see it

When you install another desktop environment like Gnome Shell once you log out you click on the Ubuntu logo and then you see the list of options to change to Gnome Shell. The last option from the list is the OK button to confirm your option. This is happening in Ubuntu 12.10. In previous versions of Ubuntu you just needed to click on the the desired Desktop environment without confirming it with the OK button.

---

### Post by masuch on 2012-10-23
how can I get on ok button if it is not visible on display ?

---

### Post by Canaryguy on 2012-10-23
> **masuch said:**
> how can I get on ok button if it is not visible on display ?

Did you installed different desktops? I did and when I was going to choose one of them I couldn't see the OK button because there were too many options. 

You can use the tab key to move through the options and Enter to select it.

---

### Post by masuch on 2012-10-24
> **Canaryguy said:**
> Did you installed different desktops? I did and when I was going to choose one of them I couldn't see the OK button because there were too many options. 

You can use the tab key to move through the options and Enter to select it.

Yes, I have read that I have to click on OK button otherwise it is not going to switch to that desktop - some new stuff in 12.10 against 12.04 . did not try ? Why ?
Because the bigger problem for me is if I do it how can I switch back to xfce desktop if it is not visible on display !?
if it is possible to switching between default environment from terminal before to get on login screen I would much appreciate if you can share those information :-) - in such case I would be afraid of not to get back to my xfce desktop which is only desktop mainly used by me.

---

### Post by Canaryguy on 2012-10-24
> **masuch said:**
> Yes, I have read that I have to click on OK button otherwise it is not going to switch to that desktop - some new stuff in 12.10 against 12.04 . did not try ? Why ?
Because the bigger problem for me is if I do it how can I switch back to xfce desktop if it is not visible on display !?
if it is possible to switching between default environment from terminal before to get on login screen I would much appreciate if you can share those information :-) - in such case I would be afraid of not to get back to my xfce desktop which is only desktop mainly used by me.

I'm not sure but maybe this thread can be of help.

[http://ubuntuforums.org/showthread.php?t=940287](http://ubuntuforums.org/showthread.php?t=940287)

---

### Post by masuch on 2012-10-24
> **Canaryguy said:**
> I'm not sure but maybe this thread can be of help.

[http://ubuntuforums.org/showthread.php?t=940287](http://ubuntuforums.org/showthread.php?t=940287)

Hi,

Thanks , it solved problem how to setup default display manager from command line "/etc/X11/default-display-manager". That is good to know as well, thanks for tip.
What I am looking for is how to setup default desktop environment. I have a list of desktop environments - I believe it has to be stored somewhere. And somewhere has to setup default desktop environment.

---

### Post by grahammechanical on 2012-10-24
The last used desktop environment becomes the default environment automatically.

Go to file system /etc/lightdm/lightdm.conf and you will see what the user-session and what the greeter-session are listed as.

This is what controls the default session (I think) but it is re-written when we select a different user session at login.

Regards.

---

### Post by masuch on 2012-10-24
> **grahammechanical said:**
> The last used desktop environment becomes the default environment automatically.

Go to file system /etc/lightdm/lightdm.conf and you will see what the user-session and what the greeter-session are listed as.

This is what controls the default session (I think) but it is re-written when we select a different user session at login.

Regards.

There is:
[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu

how can I setup default xfce dektop environment within login screen ? It is not there even if I am using it. it has to be somewhere else.

---

### Post by masuch on 2012-10-25
Please anybody knows where is stored default desktop environment used within login screen to click on "select desktop environment"

---

### Post by Canaryguy on 2012-10-26
> **masuch said:**
> Please anybody knows where is stored default desktop environment used within login screen to click on "select desktop environment"

I havent' tried it but maybe you can change the options here to start your preferred desktop:

/usr/share/xsessions

---

### Post by masuch on 2012-10-28
> **Canaryguy said:**
> I havent' tried it but maybe you can change the options here to start your preferred desktop:

/usr/share/xsessions

thanks , fine to know.

---

### Post by yogeshthegenius on 2012-11-13
> **Canaryguy said:**
> Well, I found out what the problem was. It sounds really stupid hahaha.

Well, I had installed different desktop environments so when I logged out to use one of them I saw the list but I couldn't see the OK button because my screen is not big enough (I'm using a netbook). I thought I had just to click on the desired desktop enviroment but, as Nick Payne said, you also have to click on the OK button (which it was not displayed).

Well mystery solved.

Thank you guys for your help.

I m having the same problem (have a small screen because of which can't see the OK button) can u please tell me how did u get to the ok button??? how were u able to see all the desktop environments on that small screen???

---

### Post by Canaryguy on 2012-11-13
> **yogeshthegenius said:**
> I m having the same problem (have a small screen because of which can't see the OK button) can u please tell me how did u get to the ok button??? how were u able to see all the desktop environments on that small screen???

I couldn't see all of them. I uninstalled Lubuntu Desktop and KDE Desktop and kept only Ubuntu and Gnome Shell. But I think you can move amongst the options using the Tab key until you think you have reached the correct one and then Enter and then continue pressing the Tab key until you reach the OK button which is the last option and Enter. Well, I hope they fix this error for small screens. For now that's the only solution I can give you now.

---

### Post by yogeshthegenius on 2012-11-13
> **Canaryguy said:**
> Did you installed different desktops? I did and when I was going to choose one of them I couldn't see the OK button because there were too many options. 

You can use the tab key to move through the options and Enter to select it.
Thanks I could figure it out.... I blindly got to OK and pressed enter which worked :D

---

### Post by zlot on 2012-11-17
> **yogeshthegenius said:**
> Thanks I could figure it out.... I blindly got to OK and pressed enter which worked :D

I'm not getting an OK no matter what. I'll keep trying, but I probably need to uninstall soomething.

---

### Post by zlot on 2012-11-17
> **yogeshthegenius said:**
> Thanks I could figure it out.... I blindly got to OK and pressed enter which worked :D

I'm not getting an OK no matter what. I'll keep trying, but I probably need to uninstall something.

---

### Post by zlot on 2012-11-17
OK I got it now. I had to tab TWICE to get to the invisible OK. There was yet another desktop environment I wasn't seeing even before the OK. Sure wish there was a better fix for this, although I am grateful for having gotten this far.

Edit #1
OK So I'm trying different desktops now, but it seems that after using XFCE I now have a permanent nice login screen that has a dropdown for all the different desktop environments...and they all FIT and there's an nice, easily visible "SUBMIT" button to press after you put your password in. I seem to have lost the guest account, but who cares at this point?

---

