---
title: "Remote viewing of a console X app or desktop?"
date: 2015-09-25
forum: Desktop Environments
---

### Post by 1clue on 2015-09-25
Hi.

This is somewhat urgent, needed for my job.


[LIST=1]
[*]I have an Ubuntu box which I use for development as a workstation.
[*]I have a Mac which has an X server on it, as well as Skype and Webex.
[*]These boxes are side-by-side on my desk.
[*]I want to:
[LIST=1]
[*]Open an X app on my Ubuntu box as usual for local use.  For example, Sublime Text 2.
[*]Later, open the remote viewing app on my Mac, which watches either one application or the whole desktop, as I choose.
[/LIST]

[*]I want to type on my Linux box, and have Webex and Skype share what I'm doing with my team-mates.
[/LIST]

I intend for this to use ssh,  but frankly anything I have to do is fine, this is a controlled network without wifi.

I know how to get an app or remote X session already, you don't have to explain that part.  The problems with just running a remote X session and controlling it from my mac are:
[LIST=1]
[*]Keyboard shortcuts are not handled well.
[*]I already have an app or apps going, and I want to share with somebody.
[*]Skype desktop share doesn't work on Ubuntu
[*]Webex does'nt work on Ubuntu
[*]When you get either of them to work, they're flaky.
[/LIST]

Does anyone have a recommendation for something that can hook into the console X session without interfering with its operation?

Thanks.

---

### Post by TheFu on 2015-09-25
screen?

---

### Post by 1clue on 2015-09-25
Sorry for the confusion.  I need to share X gui apps like Sublime Text, Firefox, etc from my Linux box console session (keyboard and monitors actually hooked to the Linux box) to the Mac, which will then share via Skype or Webex.

Thanks.

---

### Post by TheFu on 2015-09-25
Ah - sorry.

[https://unix.stackexchange.com/questions/2554/sharing-an-x-server-session-across-computers](https://unix.stackexchange.com/questions/2554/sharing-an-x-server-session-across-computers) might be something there. Never tried any of them.

---

### Post by uninvolved on 2015-09-27
How about VNC? TigerVNC is pretty good. I am using it right this moment. (I don't trust hotel wifi and, other than that, it's too long a story to share here.)

---

### Post by TheFu on 2015-09-27
> **uninvolved said:**
> How about VNC? TigerVNC is pretty good. I am using it right this moment. (I don't trust hotel wifi and, other than that, it's too long a story to share here.)

VNC is non-secure method. x2go using the NX protocol is more secure, faster, more efficient, and has sharing. NX uses ssh tunnels. With VNC, we must use the --localhost option to force people to "do the right thing." Most people do not.

> $ vncserver -localhost

Do not omit the -localhost argument, this stops VNC from listening on the external interface. IMPORTANT Note the server number returned by vncserver after you launch it. You will need this number to kill the server and to configure the SSH client. 

---

### Post by uninvolved on 2015-09-27
Crap... I had a nice long post written out and hit the "cancel" because I'm not that bright, it seems. *sighs*

Anyhow, to try to type out the important bits again. I'd assumed they'd be running it with the localhost switch but, frankly, you're very right and I should not assume such things. Additionally, I've just taken a new client for a spin because I was kind of worried about the security. I used the TurboVNC viewer which has encryption enabled and selected right out of the box. My situation is a bit different so I don't use the switch but, instead, use a very long password and encryption. The server's at home and isolated from the home network just to keep it safe(ish). My major reasoning is simply to avoid using the various hotel's wireless connections without encryption that I can reasonably trust. I simply connect and do my browsing through that - I've bandwidth aplenty and have been pretty content with it while I'm out engaging in my wanderlust.

However, you're very much correct and I should not assume they'd be loading the server with the localhost switch enabled. I certainly should have mentioned that as it's rather important.

As an aside, do you know if x2go can be run pre-login? Having a nice GUI to be able to use to login with via remote would be handy.

---

### Post by TheFu on 2015-09-27
I've lost posts here too. Generally just walk away for a few hours after. ;) More often, the browser posts the same stuff twice for some unknown reason.

Almost everyone who left VNC for x2go was happy they made the switch. "night and day" is frequently said after they switched.
x2go doesn't need an active login session (neither does vnc). It uses ssh, which starts a session. If you have key-based ssh already setup, installing x2go is 3 minutes of effort when you know it.  15 minutes if you need to follow instructions. You'll never look back (well, until they screw it up).  My main desktop is actually running in a private cloud on a headless server. Been doing this for about 4 yrs now.

With all this said - I don't know/think that x2go will do what the 1clue wants. I have used x2go to run rdesktop to another machine on the LAN and that works BETTER, faster, than rdesktop.  I know that skype screen sharing works from Win7 (skype and x2go client running) with other skype users. Don't know if OSX will do it correctly or not.  Never know until you try.  There isn't any way to hand over control to someone else that way either, which I thought was key for 1clue.

I've used x2go from 5 different continents. It works nicely.

---

### Post by 1clue on 2015-10-28
Sorry for not getting back for awhile.  x2go is a bit flaky but the best option at the moment.  I think the flaky part is the mac.

Thanks.

---

### Post by TheFu on 2015-10-28
> **1clue said:**
> Sorry for not getting back for awhile.  x2go is a bit flaky but the best option at the moment.  I think the flaky part is the mac.

Thanks.

I use x2go from win7 and minimal ubuntu server running openbox WM clients constantly.  About once a month the Windows client will either lose the correct resolution or disappear because the remote x2go server is extremely busy and can't be contacted. A restart of the x2go client fixes it.

The only tricks I recall were installing the font packages from the x2go site.

I don't use OSX - can't say anything about that. Tried it a few years ago, not for me, to put it nicely.

---

### Post by 1clue on 2015-10-28
I think my biggest issue is that the linux box has the monitors side-by-side and the mac has them one on top of the other, so there's insane stretching unless I reorganize things.  I like the vertical orientation better, so I might have to weld up a monitor stand for dual 24" monitors.  Not sure how that's gonna work.

The mac side of it was definitely the hardest thing to do, but they actually have a pretty good X server.  I found x2goclient on homebrew, which is a package manager for open source on mac.  Still no more than 15 minutes or so of work, but now I have it.

Frankly I'll take Mac over any Windows.  At least Mac is UNIX under there, which makes it somewhat consistent with Linux.  I admit to using the terminal more than any other mac user I know.  :)

I'd like to figure out how to make the delay be less.  My original intent was to share my screen with my mac, and then hook up skype screen sharing with others.  Right now there are several seconds lag when I'm doing that, so maybe I need to tweak for a lower bandwidth connection?

---

