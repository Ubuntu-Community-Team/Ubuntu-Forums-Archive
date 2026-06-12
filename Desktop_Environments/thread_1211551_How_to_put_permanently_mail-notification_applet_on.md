---
title: "How to put permanently mail-notification applet on gnome panel?"
date: 2009-07-12
forum: Desktop Environments
---

### Post by vickoxy on 2009-07-12
So, i was sarching for some simple gmail notifier and found mail-notification in synaptic. 

1) But i want to have its applet always in panel, not only when new messages are coming. Is that possible?

2) how can i set up time betwen message updates?

Thanks

---

### Post by vickoxy on 2009-07-13
No one uses mail-notification? Or is there some better alternative for multiple gmail - and maybe hotmail - accounts?

---

### Post by raronson on 2009-07-16
Unfortunately, there's no simple way to make this work like you've described, although there are a few options:

1) Keep evolution open but minimized.  This will place a notification next to your name in the upper right panel, and will inform you when you have new mail.  The limitation with this is that it doesn't mention for which account--only that you have unread messages.  Also, if you're not using a dock (awn, docky, for example) then seeing evolution persistently in the bottom panel may bug you.  But this depends on whether or not you have the panel set up to show applications from all workspaces.

1a) Keep evolution open, but on a separate workspace/desktop.  Set the bottom panel to only show applications for the current workspace.

2) Install Gmail Notify.  This is a sys tray application that periodically checks your Gmail account.  I have no idea if Hotmail has something similar...

3) Install Alltray, a utility that puts any specified application into the sys tray--but then again, you're limited by Evolution's handling of multiple accounts (see item 1).

Good luck.

---

### Post by vickoxy on 2009-07-17
Thanks for answers-well i tried evolution-wonderful e-mail programm, but i will not use it because i just love browser gmail layout (and haven´t got so many mails coming).

Unfortunately, mail-notification caused me some problems (sometimes it freezes, won´t reactivate...), although is very, very good when working. I tried others, but no one was good enough for multiple accounts. OK, i installed almost every mail-notifier that was to found in Synaptic, and maybe that caused a mess (reinstalled the system then). So, for now i should stay avay from mail notifiers. 

Except if someone who uses mail-notifier with  two or more accounts can give me some advice...

---

### Post by VCoolio on 2009-07-17
Have a look at [cgmail]("http://cgmail.tuxfamily.org/index.html"); multiple accounts possible; runs without mail client open; notification interval configurable; actions on incoming mail possible; always in tray if you want. I use the new version (check the link); the one in the repos is old.

---

### Post by vickoxy on 2009-07-17
> **VCoolio said:**
> Have a look at [cgmail]("http://cgmail.tuxfamily.org/index.html"); multiple accounts possible; runs without mail client open; notification interval configurable; actions on incoming mail possible; always in tray if you want. I use the new version (check the link); the one in the repos is old.

I had some issue with this notifier. Do you use Jaunty? I found it on ppa-the developer has there 0.6 version, but only for Hardy. But one has it for jaunty. Does it make any difference which one i install?

[https://launchpad.net/~ferama/+archive/ppa](https://launchpad.net/~ferama/+archive/ppa)
[https://launchpad.net/ubuntu/+ppas?name_filter=cgmail](https://launchpad.net/ubuntu/+ppas?name_filter=cgmail)

---

### Post by vickoxy on 2009-07-17
Yes, the issue with cgmail was-it won´t start. :-) So, i do not know why is that, but...

---

### Post by vickoxy on 2009-07-17
I installed cgmail 0.6 from ppa jaunty package, but after restart it looses all my accounts, and-of course- it won´t start at gnome startup (although i checked that option) :(

---

### Post by tjeremiah on 2009-07-17
For Mail Notification. Go to System > Preferences > Startup Application > click Add > Name the field > In command type ```
mail-notification --sm-disable
```

---

### Post by vickoxy on 2009-07-17
> **tjeremiah said:**
> For Mail Notification. Go to System > Preferences > Startup Application > click Add > Name the field > In command type ```
mail-notification --sm-disable
```

thanks-i will give a try to this programm. 

1) Does anyone knows how can i change those mail-notification applet icon (that one when there is no messages)

2) How to set up mail-notification to check more offten the messages?

3) Is it possible to make opacity for those pop-ups that are showing new messages-more jaunty alike?

Thanks

---

### Post by VCoolio on 2009-07-17
Well, sorry, you're right. I remembered wrong. I didn't install a new version but cgmail 0.4 on Jaunty. Works fine.

---

### Post by vickoxy on 2009-07-17
Hi,
thanks for answer, i added that line in cGmail 0.6 Version that was sugested in launchpad bug reports.. But after restart, there is applet, cGmail is active, but no new messages are detected. Why? I do not know, but when i open settings there is no account visable. When i add new account, then i have suddenly two or more same accounts.
Thanks

---

### Post by vickoxy on 2009-07-17
Well, for now, only gmail notifier that really works out of the box for me is **checkgmai**l (installed it from synaptic). It runs even multiple accounts from startup (see: [http://ubuntuforums.org/showthread.php?t=634205](http://ubuntuforums.org/showthread.php?t=634205)). Not as nice as cGmail, but at least it is working perfect (so far)

---

### Post by celem on 2009-11-08
You may have moved on by now but, if not, try gnubiff. It is in the repositories. I prefer it over cgmail because I use two webmail services, Yahoo and gmail and cgmail only supports gmail well. For Yahoo it links back to, in my case, thunderbird. Gnubiff treats Yahoo and gmail the same, providing me with notification and preview.

---

### Post by scribb on 2011-04-04
I'm using Joli OS (Ubuntu Lucid LTS + a bit of Maverick)
-----------------------------------------------------------------
To permanently display mail-notification icon on gnome panel, this is what I did:

1. Press ALT + F1 to open terminal
2. Type in this code:  gconf-editor   
PRESS ENTER
3. Navigate in gconf-editor folder tree to:  apps > mail-notification
4. Click on mail-notification
5. Tick the 'always-display-icon' option


[IMG]http://1.bp.blogspot.com/-QfDGuBQC4CU/TZljpUBoU-I/AAAAAAAAA50/D4hKmKwSU44/s1600/Screenshot.png[/IMG]



-----------------------------------------------------------------

To change/customise the mail-notification icon on the gnome panel, this is what I did:

(Note that the original location of my mail-notification icon is located at this directory:
/usr/share/icons/gnome/24x24/stock/net/stock_inbox.png)

1. Prepare a new icon and put it anywhere you want at the moment, whether it's in Desktop or home or document folder. We'll move this later on. Note the location. Make sure the size is 24 x 24 pixel. Make sure you rename it to  stock_inbox.png  . I stored my prepared new icon here:
/home/myname/Pictures/icons/stock_inbox.png

2. Move that file to the original location of mail-notification icon. Do it as root, like this:

PRESS ALT + F1   to open terminal
TYPE IN THIS CODE below:
sudo mv /home/myname/Pictures/icons/stock_inbox.png /usr/share/icons/gnome/24x24/stock/net
PRESS ENTER

That's it. 

PLEASE NOTE about that command code, you should type in your own directory after the 'sudo mv' (/home/myname/Pictures/icons/stock_inbox.png-----replace it with your own appropriate location of your newly created icon)

the /usr/share/icons/gnome/24x24/stock/net should stay the same (unless it's stored somewhere else in your system)

---

