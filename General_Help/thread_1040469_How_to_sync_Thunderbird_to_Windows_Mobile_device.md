---
title: "How to sync Thunderbird to Windows Mobile device"
date: 2009-01-15
forum: General Help
---

### Post by jackmetal on 2009-01-15
Wow, I feel like a newbie again.  I've been using Linux for a long time, but just decided to set up a sync relationship between my ubuntu 8.10 system and my Windows Mobile device.  I've read through "numerous" tutorials, url's and forum threads, but so far nothing I've done is working.  

I can see my device attach and get an IP address (of course the 169.xx.xx.xx address).  I've added a rule to allow it through ufw and I've installed every multi-sync, open-sync and synce app, tool and library, but I really am lost.  :-)

Here's my setup:
Ubuntu 8.10
Thunderbird 2.0.0.19 w/Lightening 0.9
Windows Mobile 6.1 - HTC Touch Pro

This is the very last thing that I use windows for at all, I hope to get this setup and remove my Windows partition once and for all...!

Thank-You VERY much in advance for any help you can give.  It is definitely appreciated!!

---

### Post by jackmetal on 2009-01-15
After a LOT more review, I've stumbled upon FinchSync.

Has anyone used that successfully, or is there a better option I should look into?

---

### Post by BlakeM on 2009-01-17
In much the same situation you are. I have an i-mate JasJar I'd like to sync with Thunderbird.

Any help would greatly be appreciated.

---

### Post by BlakeM on 2009-01-17
Yeah, I've looked into it as well. I'm amazed that there aren't more people trying to sync Thunderbird and a Windows Mobile device. There seems to be a stable way of syncing Evolution and Windows Mobile devices. As much as I like the idea of using Thunderbird, it looks like Evolution is the only way to go.

Has anyone had any luck in Intrepid?

It seems that FinchSync is the only way to sync with Thunderbird at this time. Haven't personally tried implementing this, though.

---

### Post by jackmetal on 2009-01-17
Yeah, I'm in the middle of gettng FinchSync working.  Looks like it's going to be the way to go (at least for now).   Mandriva has it setup out of the box, I'm really surprised the Ubuntu hasn't gotten there yet.  But....That's the good thing about Linux.. If it works in any platform, you can get it to work in any other.  :-)

I'll let you know how it goes with my config.  So far everything is looking very good!!!  I'll post a good step-by-step tutorial on it when I'm finished.

I have nothing against Evolution, but I really have NO Intention of leaving Thunderbird and moving back to Evolution.  I'll get this working if it kills me.  ;-)

---

### Post by BlakeM on 2009-01-25
Yeah, I know what you mean. Recently adopted Linux after using Windows for several years. If I can get a few things working, I'm never going back. Unfortunately, I'm having a lot of trouble...

How's your experience with FinchSync been? You got around to posting that tutorial?

---

### Post by jackmetal on 2009-01-26
No, unfortunately I got sidetracked on another issue (getting my Broadband Wireless working in a WinXP Guest OS on my Ubuntu Host.  I need that for my work, so I've been focused on that instead.  Hopefully, I can get that working and get back to testing my FinchSync setup.  From everything I've read on it, it looks like it's a pretty straightforward setup. 


> **BlakeM said:**
> Yeah, I know what you mean. Recently adopted Linux after using Windows for several years. If I can get a few things working, I'm never going back. Unfortunately, I'm having a lot of trouble...

How's your experience with FinchSync been? You got around to posting that tutorial?

---

### Post by BlakeM on 2009-01-27
Yeah, finally had time to look at FinchSync. Like you I'm trying to fix several problems at once with Ubuntu. I have to keep reminding myself that once it's all setup Ubuntu will be totally worth it (fingers crossed).

You're right about FinchSync. It seems to be a very easy setup. I'll put it in practice tonight though.

Good luck with your other issue. Hopefully by the end of the month we'll both be Ubuntu savvy and loving it.

---

### Post by jackmetal on 2009-01-30
You would think that since it is seamless in Mandriva, it shouldn't be soooooo hard to have it working in Ubuntu.  :-)

It's tempting to move to Mandriva (I've used it in the past and liked it a lot), but I'm trying to stick it out with Ubuntu.  Hopefully they will get it worked out soon.  Until then, hopefully we can find workarounds for our bugs that will keep us on Ubuntu.  We can hope!  LOL

---

### Post by jackmetal on 2009-02-05
Well, I finally had time to get to the FinchSync setup.  It works Perfectly!

Server Setup: Just run 'java -jar finchsync.jar' ; change the port (if needed - default 8080), setup the sync sources (contacts, calendars/todo's) ; create a client name/password and add the sync sources to it.

Client Setup: install finchsync on your client ; setup the server (name, IP, port, login/passwd); setup the category mapping ; then sync.

That was it.  Worked great.

PS: I also managed to get OpenSync syncing my phone with Evolution. (But, I'm sticking with FinchSync until they add a plugin for Thunderbird to OpenSync; and even then - I may stick with FinchSync)

---

