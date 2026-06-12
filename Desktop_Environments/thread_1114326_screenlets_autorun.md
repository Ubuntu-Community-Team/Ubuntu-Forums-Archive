---
title: "screenlets autorun?"
date: 2009-04-02
forum: Desktop Environments
---

### Post by B4RR13N705 on 2009-04-02
Hi, i just installed scrennlets and i put some of them in my desktop, then i restart my pc. The screenlets daemon was running, but my screenlets wasnt there, ive waited for some minutes and nothing, so i have to start them manually. Is this normal? or am i doing something wrong?

---

### Post by andrea000 on 2009-04-02
Did you check the screen lets daemon in your start up?
apps.menu session start up and see if it's checked if not
check it then it should start the next time you reboot.

---

### Post by mtbsoft on 2009-04-02
If the daemon (Screenlets Manager icon?) is running but the screenlets aren't, check in the Screenlets Manager that you have ticked the *Auto start on login* option for *each* of the screenlets you selected - it is an individual, not global, setting.

Could be you set it for one which you subsequently removed but forgot to do it for the rest.

---

### Post by andrea000 on 2009-04-03
Oh check to see if when you put your screenlets on the desktop
your check run at start up of go to start up and put a check by it there

---

### Post by B4RR13N705 on 2009-04-03
I can see the daemon running but the desklets arent there! I looked for that option of autostart but i couldnt find it! In the properties of each one i can see an option called

"Trated like a widget"

Maybe is that?

---

### Post by B4RR13N705 on 2009-04-03
okay, i found that option, now they autostart! thanx 4 the help!

---

### Post by Marlonsm on 2009-04-03
Go to Applications>Accessories>Screenlets, you'll see this window, just select the screenlet(s) you want and check "Auto Start on Login"

[IMG]http://img205.imageshack.us/img205/4689/screenshot1jxr.png[/IMG]

EDIT: sorry, I was a little bit late...

---

### Post by Jugney on 2010-02-15
Oddly enough, I have the Screenlets daemon set to start in Preferences -> Startup Applications, and each of my desired screenlets have "Autostart on Login" ticked, but none of them load on startup.

If I open the Screenlets Manager, I see none of them have "Start/Stop" ticked. If I manually start them, then I see multiple instances. As though an instance was already running, but they didn't show up until then.

I have them running in a widgets layer, and that is always running, they're just not there.

Any ideas?

---

### Post by mtbsoft on 2010-02-15
> **Jugney said:**
> I have them running in a widgets layer, and that is always running, they're just not there.
I know this might sound like an obvious question so please excuse me but are you actually showing the widget layer?  I have some of my screenlets on the widget layer which means they are hidden until I show the layer with F9.

Have you also tried setting them as non-widget and seeing if they show at login?

---

### Post by Jugney on 2010-02-16
I kept searching around in other threads and there were two things that fixed my problem.

**To fix the issue of multiple screenlets being opened at a time**

I navigated to home/[username]/.config/Screenlets and went into the individual folders for all of my desired Screenlets. What I found is that those running more than one instance had more than one .ini file. So I just deleted all of those files so I could start over.

[B]To fix not starting at login
[/B]
I navigated over to usr/share/Screenlets and opened up permissions on that folder. Once that was done, I went to the Screenlets Manager and stopped and started again all my desired screenlets.

I'm not sure why this would be an issue in the first place. It would be great if these things didn't trip up such a great program.

Regardless, I'm very happy now with my Screenlets and Widget layer! I've also set up my Desktop corners so I can quickly access them with a mouse swipe. Ahhhhhhhhhhh..........

---

