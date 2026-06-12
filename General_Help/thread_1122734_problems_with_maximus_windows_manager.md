---
title: "problems with maximus windows manager"
date: 2009-04-11
forum: General Help
---

### Post by an93l on 2009-04-11
I have looked up and down this and the ubuntu forums for a fix for this problem and have found nothing so I am starting a new topic.

I am running ubuntu 9.04 netbook remix, and the issue is that every time I switch on my AAO maximus opens a new process so there is a maximus process for every reboot. before I did a system re-install I had like 20 maximus processes running and most of my 512MB of memory was taken up. now I have about 8 maximus processes and I know that next time I start the system up this will increase to 9 or 10. Is anyone else having this issue, I would check If I were you.

Another thing, I have been trying to report this issue to the devs but the problem reporting tool does not work.

---

### Post by pedrobl on 2009-06-12
Same thing here!
I get something around 70 "maximus" processes when I boot now... and I do not have 70 windows opened. I tried to kill them all (killall), but they got restarted... :(
I think the problem comes from the fact that in every reboot, I get about 2 "maximus" processes more.

Any ideas?

---

### Post by Legace on 2009-06-12
> **pedrobl said:**
> Same thing here!
I get something around 70 "maximus" processes when I boot now... and I do not have 70 windows opened. I tried to kill them all (killall), but they got restarted... :(
I think the problem comes from the fact that in every reboot, I get about 2 "maximus" processes more.

Any ideas?
You could disable maximus from System > Preferences > Startup Applications.

---

### Post by pedrobl on 2009-06-26
> **Legace said:**
> You could disable maximus from System > Preferences > Startup Applications.

Thanks, but I have two problems with your suggestion:
1. I could also stop using the mini, but that wouldn't REALLY solve the problem.
2. It doesn't work: I tried it, rebooted, and I now have 74 maximus processes.

The question is: is there a way of removing those useless processes?

I found out that in the directory ~/.config/gnome-session/saved-session I have 83 .desktop files, some of them (73) refer to maximus processes... lets delete those... yes!! that did it! :)

OK this is what I did:
[LIST=1]
[*]Open a terminal.
[*]Type:
[FONT="Courier New"]cd ~/.config/gnome-session/saved-session[/FONT]
[*]To delete every file in that directory that contains the word "maximus", type:
[FONT="Courier New"]grep -l maximus * | xargs rm[/FONT]
[*]Restart the session
[/LIST]

Let me know if it works for you...

Pedro.

---

### Post by earthpigg on 2009-06-26
in sessions (8.04) or startup applications (9.04), has anyone tried **_*UN*_**checking 'automatically remember running applications when logging out' ??

---

### Post by pedrobl on 2009-06-29
> **earthpigg said:**
> in sessions (8.04) or startup applications (9.04), has anyone tried **_*UN*_**checking 'automatically remember running applications when logging out' ??

Yeap, I disabled it a few weeks ago, but the 70+ processes still came up every time I started. I had it enabled before, and it's probably the reason why it reached so many processes... I should probably file a bug, as maximus should not be considered a running "application" when you log out.

I forgot to mention this in my previous post, thanks!

---

### Post by netbook-dude on 2009-09-24
> **pedrobl said:**
> Thanks, but I have two problems with your suggestion:
1. I could also stop using the mini, but that wouldn't REALLY solve the problem.
2. It doesn't work: I tried it, rebooted, and I now have 74 maximus processes.

The question is: is there a way of removing those useless processes?

I found out that in the directory ~/.config/gnome-session/saved-session I have 83 .desktop files, some of them (73) refer to maximus processes... lets delete those... yes!! that did it! :)

OK this is what I did:
[LIST=1]
[*]Open a terminal.
[*]Type:
[FONT=Courier New]cd ~/.config/gnome-session/saved-session[/FONT]
[*]To delete every file in that directory that contains the word "maximus", type:
[FONT=Courier New]grep -l maximus * | xargs rm[/FONT]
[*]Restart the session
[/LIST]

Let me know if it works for you...

Pedro.

:KS AMAZING - THANK YOU!!!! My system had over 95 Maximus Processes running and I my system was becoming unbearable to use.

Great thinking and thank you once again!

netbook-dude

---

### Post by an93l on 2009-09-25
I found that when I upgraded my system to the release version it solved the problem. I think it was just as I was using an alpha.

---

### Post by ttl886201 on 2009-10-25
Go to System -> Preferences -> Startup Applications -> Options and uncheck automatically remember running applications on logout. Then remove all saved sessions in .config/gnome-sessions/saved-sessions. Reboot. You can then recheck the remember applications box. 

From my limited understanding, Ubuntu opens a failsafe session if one of the previous sessions was improperly shutdown or has some sort of bug. Since your previous session was saved, you end up reloading the buggy session (i.e. Starting Maximus on log in) each time and Ubuntu opens a failsafe session each time. Unchecking the box, deleting the saved-sessions, and rebooting clears any buggy sessions and stops Ubuntu from opening a failsafe session. You must uncheck the remember applications option box in order to properly delete the saved-sessions. If you try to delete the saved-sessions without unchecking the box, they will simply reappear during your next login.

---

