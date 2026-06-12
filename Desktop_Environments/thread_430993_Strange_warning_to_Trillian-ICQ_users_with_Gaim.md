---
title: "Strange warning to Trillian-ICQ users with Gaim"
date: 2007-05-02
forum: Desktop Environments
---

### Post by mattG on 2007-05-02
Hello,

I am using Gaim in Ubuntu 7.04 for ICQ communication. People using Trillian in Windows get a strange warning when they start to communicate with me:

> This user appears to be using an older Mirabilis ICQ client, which depends on an outdated version of the ICQ protocol.  As such, you *may* experience intermittent message loss.  Encourage them to upgrade to Trillian or a newer build of ICQ! (You can e-mail them, or call them... :))  You may turn off this warning in ICQ Account Preferences -> Misc.

This gets kind of annoying because everyone asks me what is wrong with my ICQ client. Is there any workaround on my side to prevent this message from popping up in Trillian?

Thanks!


Matt

---

### Post by notwen on 2007-05-02
You may want to try the newer version of Gaim -[Pidgin]("http://www.pidgin.im")-  You can try the .deb files located on this [thread]("http://ubuntuforums.org/showthread.php?t=429255").  I'd recommend backing up your .gaim folder in your home folder.  Pidgin will take on all your settings/info from gaim, you will only need to add it to your Menu, this can also be found in the thread w/ the .deb files.  Hope this helps your warning issue, but if not atleast you're using the new Gaim. =]

---

### Post by mattG on 2007-05-03
Good idea. I tried it but unfortunately the message still appears with Pidgin... :( 

Thanks anyway!

---

### Post by bobpaul on 2007-05-04
Wow. I haven't seen that warning since ICQ transitioned from their own protocol to the AIM's extensionable OSCAR protocol after the AOL buyout.

Generally my experience is that trillian will forward any warning the server provides to the user, whereas the official ICQ client doesn't. My guess is the version number for the protocol GAIM sends is a little older and the server is providing a warning.

You should post this on over at the GAIM website to ensure they are aware.

---

### Post by mattG on 2007-05-04
> **bobpaul said:**
> 
You should post this on over at the GAIM website to ensure they are aware.

I will - as soon as their website is reachable again... (Down due to the Pidgin release)

By the way: What are good alternatives to GAIM? I know too many Trillian users...

---

### Post by bobpaul on 2007-05-06
> **mattG said:**
> I will - as soon as their website is reachable again... (Down due to the Pidgin release)

By the way: What are good alternatives to GAIM? I know too many Trillian users...

Well, there's multiclient webmessengers like meebo. Or there's the KDE oriented Kopete which actually looks pretty nice. My understanding is that developement on Kopete has been much quicker than GAIM over the past couple of years. They had voice/video for a long time, thought I think the file transfer support might be lacking?? Those are the ones I know of.

Or you can use any Jabber client (Gaim, Kopete, etc) and connect to a Jabber server with AIM, ICQ, MSN, and Yahoo support. That will not support file, voice, etc with those clients, but will work.

Trillian 0.74 works on WINE I hear, if you can find an old version.

---

