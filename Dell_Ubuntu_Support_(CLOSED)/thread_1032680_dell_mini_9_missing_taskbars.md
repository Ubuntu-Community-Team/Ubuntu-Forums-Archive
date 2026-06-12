---
title: "dell mini 9 missing taskbars"
date: 2009-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by frani23 on 2009-01-06
I was trying to get rid of the office program that includes email, calander and contacts.  I turned off the computer then when I turned it back on, the task bars were gone.  Only the desktop picture shows.  I have tried rebooting and pressing alt-f2(which is hard on mini 9) and nothing helps.  I am still new to ubuntu, so simple esplinations would be good.  Also, I would be willing to restart or reload the system...but I don't know how to do that.  Thanks in advanced.

---

### Post by ugm6hr on 2009-01-06
Unfortunately, that program (Evolution) is pretty tightly integrated into the desktop (Gnome).

If you do Alt+F2 again, type the following in the box:
```
gksudo synaptic
```

This loads the package manager.  Search for evolution, and select it for installation.

Of course, if you did something other than removing Evolution, that won't help.

EDIT: If you don't know what you are doing, I would suggest refraining from trying to "customise" your Ubuntu installation for now.

---

### Post by frani23 on 2009-01-06
Thanks but I can't press alt f2!  That is, I press it but it doesn't do anything.  Can't I just reboot the whole system?  (Like windows) That would make it easier then trying to figure out what is wrong.  I don't have anything important on the computer since it only has a 16gb drive...

---

### Post by vipok1980315 on 2009-01-06
We are a professional engaged in Beijing invoice consultation services companies, professional and real and effective invoice, providing strict secrecy mechanism, if you are interested in learn more about Beijing invoice-related information, please visit our company website! Thanks!Acupuncture [[size=1][color=silver]Acupuncture[/color][/size]](http://www.tcmyi.cn/)[size=2] [size=1]&#21271;&#20140;&#21457;&#31080;[/size] [/size][[size=1][color=silver]&#21271;&#20140;&#21457;&#31080;[/color][/size]](http://www.bjzhilv.com/)[size=2] [size=1]&#21271;&#20140;&#21457;&#31080;&#21672;&#35810;[/size] [/size][[size=1][color=silver]&#21271;&#20140;&#21457;&#31080;&#21672;&#35810;[/color][/size]](http://www.bjzhilv.com/) &#27668;&#27169; [[size=1][color=silver]&#27668;&#27169;[/color][/size]](http://www.cnqimowang.com/) Traditional Chinese Medicine [[size=1][color=silver]Traditional Chinese Medicine[/color][/size]](http://www.tcmyi.cn/)

---

### Post by ugm6hr on 2009-01-06
> **frani23 said:**
> That is, I press it but it doesn't do anything.  Can't I just reboot the whole system?  (Like windows)

Presumably you mean re-install rather than reboot (a reboot achieves nothing).

And yes - you can.  But you need an external USB DVD drive (see the instructions / DVD which you should have gotten with the Mini9), or you need a (perhaps 2GB size) USB [flash drive]("https://help.ubuntu.com/community/Installation/FromUSBStick") to install with (since there is no internal DVD drive).

Perhaps try explaining what you did to cause the problem, and we could try and fix it?

---

### Post by frani23 on 2009-01-28
Hello, I hadn't realized that you had replied, sorry for the delay.  I am starting to get really desperate, and I am thinking about sending it back to dell so they can fix it...but usually they make the problem worse.  Okay, so what I remember doing was trying to remove evolution in the add/remove menu.  It told me that I had to go to another program in the administration menu(I don't remember the name)because Evolution was a bundle then I went to that program and clicked on the first thing that said Evolution and removed it and all of its components.  Then I closed the program and checked to see if it had been removed. (What I wanted to do was use another program that was only a calander and contacts because I do not need another email thing and Evolution forces the user to use the email)  Evolution had not been removed and the other program had not been installed even though on the add/remove menu it was...So I went back to the administration add/remove program and proceeded to remove all of the things that said evolution (there were like 5) and all of their components. Then I closed that program and checked if evolution had been removed and the other program installed but it still hadn't so I gave up and turned off the computer (I think...I might have reinstalled evolution, maybe and then turned off the computer).  Then when I turned the computer on again, only the desktop background showed and not the toolbars.  I can get to the start up screen and enter my password and my desktop background comes up.  I can only right click and a meager menu comes up, nothing that allows me to bring up a program or toolbar.  I also cannot press alt f2 because it is diffrent on the dell mini.  So as you can see, it seems pretty difficult to fix so I would prefer to restart the computer.  I actually have a 250gb external drive that I can use, I just need to know how to use it to reinstall Ubuntu.  Sorry for the long thing but I hope it helps to explain how I got to the point where I am.

---

### Post by anjilslaire on 2009-01-28
you can press alt+f2 by the following:

hold alt+Fn+s.

Fn is the blue button between Ctrl & Win

---

### Post by ugm6hr on 2009-01-29
You can do as above, or try this:

Ctrl+Fn+Alt+A (aka Ctrl+Alt+F1 on Dell Mini 9)

You will get to a black screen.  At the prompt, type (enter your password and "Enter" when prompted):

```
sudo apt-get update
sudo apt-get install gnome-panel evolution-data-server
sudo poweroff
```

This will turn eveything off.  When you reboot, hopefully things will be working.  If not, we will reinstall Evolution completely.

PS: You can leave Evolution and use another mail app if you want - I do on my main laptop (Thunderbird).

PPS: You could send it back to Dell - but they will just reinstall Ubuntu for you.  Unless you have a next-day warranty, it would be quicker to follow advice here.  But try and check back at least daily for responses!

---

### Post by frani23 on 2009-01-29
Okay, I actually got a response from the ctrl-fn-alt-a thing but it doesn't let me enter my password.  I will keep trying and let you know...at least now there is hope!

---

### Post by frani23 on 2009-01-29
> **frani23 said:**
> Okay, I actually got a response from the ctrl-fn-alt-a thing but it doesn't let me enter my password.  I will keep trying and let you know...at least now there is hope!

I think I am actually doing more harm then good...I can type my login but when I hit enter to try to put in my password, it doesn't let me type anything and after a couple of seconds it tells me incorrect login and prompts for the login again...maybe I am doing it wrong.  Am I supposed to do the ctrl-fn-alt-a comand before the login screen loads or after I login?

---

### Post by ugm6hr on 2009-01-30
> **frani23 said:**
> I can type my login but when I hit enter to try to put in my password, it doesn't let me type anything 

It does let you type your password.  You just won't see anything on screen

Type it in when asked, and press Enter again.

---

### Post by frani23 on 2009-01-30
When I press alt-fn-ctrl-a and don't touch anything else, it says:

[COLOR="Red"]Starting up...
Loading, please wait...
usplash: Setting mode 1023 x 768 failed
usplash:  Using mode 800 x 600

Ubuntu 8.04.1 frances tty1

frances login: *Stopping NTP server ntpd[/COLOR]

Then I type my login, hit enter, [COLOR="red"]Password:[/COLOR] comes up and I can't type anything.

---

### Post by ugm6hr on 2009-01-30
> **frani23 said:**
> Then I type my login, hit enter, [COLOR="red"]Password:[/COLOR] comes up and I can't type anything.

Have you tried just typing your password at the "Password" prompt and pressing Enter?

You will not see a cursor move, or get any feedback as you do this, but it should work.

If that doesn't work, what happens if you just press Enter?  Or press it a few times?

---

### Post by frani23 on 2009-02-02
help help help, I did everything, the taskbars are back but now it is asking me if I want to delete [COLOR="Red"]oafi id: gnome_FastUserSwitchApplet [/COLOR]I don't think anyone will respond in the next few minutes so I will not delete it if I am not answered in half an hour.  Thanks if anyone helps!

---

### Post by frani23 on 2009-02-02
Also the [COLOR="Red"]OAFIID: Gnome_MixerApplet[/COLOR], [COLOR="red"]OAFIID: Gnome_Panel_TrashApplet [/COLOR]and [COLOR="red"]OAFIID: Gnome_FastUserSwitchApplet[/COLOR], I shouldn't delete right?

---

### Post by ugm6hr on 2009-02-03
You do not want to delete anything.

Did it boot back into the Desktop OK?

---

### Post by frani23 on 2009-02-03
Yup every thing reloaded good and those messages came up again (I didn't press anything yesterday), and pressed the don't delete button as per your instructions.

It actually installed some updates and restarted just fine so i turned it off and turned it back on this morning and I am actually typing on it right now.  yay!  Thanks so much for your time and patience!!!

---

### Post by frani23 on 2009-02-04
I didnt delete them but the windows continue to come up when I turn on the computer and I just figured out that the volume and trash doesn't work on the task bars.  I was wondering if we could fix that, if we can't its okay, but it would be nice to have those working...

---

### Post by ugm6hr on 2009-02-04
Maybe try just reinstalling everything (inc Evolution):
```
sudo apt-get install ubuntu-desktop
```

---

