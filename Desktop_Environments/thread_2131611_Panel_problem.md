---
title: "Panel problem"
date: 2013-04-02
forum: Desktop Environments
---

### Post by BulmaSMG on 2013-04-02
Hey. Yesterday I was trying to do something panel related and it had me use terminal. I don't remember the exact command but it resulted in my panel disappearing. After rebooting I got it back. But now after every time I log in it has a messege that tells me that the XFCE panel isn't loaded and it has to be exucuted. So I hit execute and there it is. How do I make it so I don't get that messege and so the panel comes up on it's own?

---

### Post by neruson on 2013-04-02
You need to tell us what you were doing. Type "history" into your terminal and post the output here. If I remember correctly typing "history > output" will save it to a file. The xfce4-panel was probably removed from the startup applications/processes but to be sure we need to know what you were doing.

---

### Post by BulmaSMG on 2013-04-02
> **neruson said:**
> You need to tell us what you were doing. Type "history" into your terminal and post the output here. If I remember correctly typing "history > output" will save it to a file. The xfce4-panel was probably removed from the startup applications/processes but to be sure we need to know what you were doing.

Here:

[http://lkubuntu.wordpress.com/2011/09/04/make-xfce4-bottom-dock-act-like-docky-awn/](http://lkubuntu.wordpress.com/2011/09/04/make-xfce4-bottom-dock-act-like-docky-awn/)

I only did the first command and once I saw my panels go away I flipped and didn't go any further with it.

I would of put it in the OP but I wasn't able to find it at the time.

---

### Post by neruson on 2013-04-02
I ran the first command "xfce4-panel -q" and my panels disappeared too. I then ran "killall xfce4-panel" just to make sure it wasn't running in the background for whatever reason and then I hit "alt+f2" and typed "xfce4-panel." I logged out and logged back in without a problem. Click on your menu and navigate to Settings>Settings Manager and click on Session & Startup. Click on the "Session" tab and make sure the xfce4-panel listing says "immediately" under Restart Style. Under that setting this worked for me.

I'm using xubuntu 12.04.

---

### Post by BulmaSMG on 2013-04-03
> **neruson said:**
> I ran the first command "xfce4-panel -q" and my panels disappeared too. I then ran "killall xfce4-panel" just to make sure it wasn't running in the background for whatever reason and then I hit "alt+f2" and typed "xfce4-panel." I logged out and logged back in without a problem. Click on your menu and navigate to Settings>Settings Manager and click on Session & Startup. Click on the "Session" tab and make sure the xfce4-panel listing says "immediately" under Restart Style. Under that setting this worked for me.

I'm using xubuntu 12.04.

Thanks, dude. I'll try it out next time I boot into Linux.

---

### Post by BulmaSMG on 2013-04-03
No luck. Logging in I still get this error:

[IMG]http://i.imgur.com/F3eyQsQ.png[/IMG]

Followed by one about it being in kiosk mode and me not being able to acess/change it's settings. Even though I CAN acess/change settings. Weird....

---

### Post by neruson on 2013-04-03
I'm unable to recreate the errors you're getting with the information you provided me. The only thing I can think of is making sure the "save session for future logins" box is checked when you logout (after you start your panel again of course.). If that doesn't work can you post a picture of the second error message you are receiving?

---

### Post by BulmaSMG on 2013-04-03
> **neruson said:**
> I'm unable to recreate the errors you're getting with the information you provided me. The only thing I can think of is making sure the "save session for future logins" box is checked when you logout (after you start your panel again of course.). If that doesn't work can you post a picture of the second error message you are receiving?

Did it and still get the same errors.

[IMG]http://i.imgur.com/qwAiVeP.png[/IMG]

This isn't worth a whole reinstall considering I still get my panels back and am able to use them just fine but if I can't figure it out I probably just will. I've only had the OS alongside my Windows 7 install for about 4 days and haven't done enough to it to be upset over another install.

---

### Post by Frogs Hair on 2013-04-04
Are you running XFCE 4.8 as in the instruction or 4,10 ?  I am in the 4.10 session and the panel preferences are in the settings menu and you can add a panel if the app opens. I don't if the panel has to be running to open the settings.

---

### Post by BulmaSMG on 2013-04-05
> **Frogs Hair said:**
> Are you running XFCE 4.8 as in the instruction or 4,10 ?  I am in the 4.10 session and the panel preferences are in the settings menu and you can add a panel if the app opens. I don't if the panel has to be running to open the settings.

4.10.

I can open panel settings and change them just fine.

---

### Post by Frogs Hair on 2013-04-06
double

---

### Post by Frogs Hair on 2013-04-06
It possible the commands which were for 4.8 broke something.  Does the add panel selection work in panel settings ?

---

### Post by BulmaSMG on 2013-04-06
> **Frogs Hair said:**
> It possible the commands which were for 4.8 broke something.  Does the add panel selection work in panel settings ?

Yes. Everything panel related works fine. The issue is just the annoyance of the message every time I boot.

---

