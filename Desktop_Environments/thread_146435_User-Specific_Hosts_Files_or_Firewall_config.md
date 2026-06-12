---
title: "User-Specific Hosts Files or Firewall config?"
date: 2006-03-18
forum: Desktop Environments
---

### Post by Tim Dub on 2006-03-18
Hi, I'm Tim Dub, and I'm a relative newbie to both Ubuntu and Linux in general. I've tinkered around with various live distros and finally decided to dive in and dual-boot Ubuntu Breezy with WinXP. My family and I have been mostly-pleased thus far with the results. I know my way around XP and thus I've caught on fairly quickly on how to customize Breezy, even though it's a whole different Badger.

:-k But I've run into a problem. "Get on with it!" I'm sure you say:

My fiancee has a ten-year-old son who will likely soon begin hitting the IM and chatroom networks. We're concerned about the usual things parents *should be* concerned about when it comes to this matter. A simple solution would be to do the "localhost hack" on the Hosts file or configure the firewall (through Firestarter; I like mine GUI) to block off, for example, oscar.aol.com, chat.yahoo.com, etc. I'm a regular AIM user and it would be a pain to have to go back and un-block the servers and then re-block them, so I'm wondering if there's a way to blacklist and/or whitelist certain domains at strictly the user-level.

I did Search for such a topic but couldn't find one. If there's already a How-To on this, please feel free to point me that way and then tell me to STFU and RTFT. Thanks :)

---

### Post by Zelut on 2006-03-18
Well you could use firestarter as you mentioned and block the domains & ports that you want.  I setup something similar for my younger brother & we used a whitelist which, of couse, only let him hit his school sites, wiki, etc.

Firestarter should prompt for a password to edit anything, so the ten-year-old's user wouldn't have access to anything you didn't specify.  Then, when you login to your user you could simply click 'stop firewall' and you're back to normal.  When you logout & he logs in I believe it should restart the firewall as needed.

I can't think of any user-level filters (off the top of my head) but the firestarter method seems fairly quick & easy, for me anyway.

---

### Post by Tim Dub on 2006-03-20
Sounds like a good idea, except I'd rather Firestarter be running for all users. Now, from what I understand, Firestarter's just a front-end for IPtables, right? So, even without the Firestarter process itself running, would our connection still be protected? Sorry, I'm still used to the Windows world where "firewall off" means "wide-open."

---

### Post by Zelut on 2006-03-20
I understand you're used to the idea of "firewall off" meaning "ooh crap we're all gonna die" ;) , but it can be quite different in Linux.

Are you using a router or are you directly connected to a modem?  If you are behind a router then it also should act as a firewall so you'd basically be using firestarter as the whitelist/blacklist for your son.

A good way you can check (with or without firestarter) is to go to this website & do the "[Shields Up]("http://grc.com")" check.  It'll give us a good idea of what we need to work with.

Linux is inherentely more secure than windows.  you dont NEED a firewall to safely browse the internet.  I haven't used a firewall on any of my machines & I've stayed safe for nearly a year.

---

### Post by Tim Dub on 2006-03-21
Funny you should mention ShieldsUp; I happened to have tried it this morning, both with and without Firestarter running, and while all my ports were "Stealth," Breezy failed the Ping test both times. Wierd.

I'm connected to DSL by an adapter which I suppose could be considered a router (it's that little white box that BellSouth sent me). I think I get it now; Firestarter could be better-used for blacklisting but having it off won't leave us wide-open for attack because Ubuntu has all these ports/services/etc off by default...unlike ol' XP. If Firestarter were necessary, it would have been installed and enabled by default in Ubuntu; they're just cool that way.

Thanks for your help; I'm sure I'll have more questions for everybody :)

---

