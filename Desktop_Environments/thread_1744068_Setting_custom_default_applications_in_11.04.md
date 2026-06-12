---
title: "Setting custom default applications in 11.04"
date: 2011-04-30
forum: Desktop Environments
---

### Post by jethro1138 on 2011-04-30
Hi there!

OK, I'm trying to set the default apps using gnome-default-applications-properties. In previous versions I was able to set custom apps for everything. Looks like Gnome3/Ubuntu 11.04 doesn't let me do that for, say, the mail reader. I'm one of those people who still use Alpine, and in previous versions I was able to set the default to run an xterm (well, aterm) which auto-ran alpine. 

This version, looks like that's not there. I'm wondering if there's a way to set that anyway... like registering a script I write as a "mail client" so it's available in the chooser. 

Second... and almost MORE annoying... the "Terminal Emulator" default app DOES have a custom option. But it also recognises that I have aterm installed, which I want to use as the default app... however, since it has an aterm option, it won't let me enter aterm as a default command. Which I want to do because I want to modify the commandline options. But if you choose "Custom" and type "aterm" into the Command field... it ERASES your commandline options and puts it's default sterm options in! 

Now I'm not sure if these are normal issues or bugs or what exactly is going on, but any input would be very much appreciated (:

---

### Post by PsyWolf on 2011-04-30
I just ran into the same problem.  I wanted to set up gmail as my default mail client.

Edit:
After some more research, I found
[Desktop Webmail]("http://www.webupd8.org/2010/04/desktop-webmail-sets-gmail-hotmail-and.html")
and
[Gnome Gmail]("http://www.webupd8.org/2010/01/gnome-gmail-v14-adds-file-attachment.html")


p.s. if you use gmail, these go really well with [Gmail Watcher]("http://www.webupd8.org/2010/09/gmailwatcher-gmail-notifier-especially.html")

but I'd still like to know how to get a script I wrote to show up in that list.

---

### Post by jethro1138 on 2011-05-01
> **PsyWolf said:**
> 
After some more research, I found
[Desktop Webmail]("http://www.webupd8.org/2010/04/desktop-webmail-sets-gmail-hotmail-and.html")
and

I installed that thinking it'd give me a clue as to where/what I could edit myself. Sadly it totally doesn't show up in the default apps for me. I'll keep digging.

---

### Post by 8-bit on 2011-05-03
I have the same problem. After installation Google Chromium is there as an alternative for Firefox and the icon changed to Chromium. But after installing Gnome Gmail there is no alternative in Preferred Applications.
 
I'm using Unity. Haven't tested it with the classic desktop.

---

### Post by abi278 on 2011-05-11
This is really annoying me as well, because I can't set a -newwindow switch for my preferred browser.  When I click on a link in say Pidgin or Tomboy, I don't want a new tab in an existing window that's usually on a different workspace!

Tried gconf-editor - setting my preference for a new window under desktop/gnome/url-handlers/http has done nothing.

---

### Post by BFG on 2011-05-30
I have this problem too. I need the custom option to set up gmail to accept mailto: actions.

Another 11.04 papercut?

---

### Post by glowplug19 on 2011-06-20
I am having the same problem. Any news?

I've even tried using```
sudo update-alternatives --config x-www-browser
```, which only lists the available executable paths and allows me to choose a selection, but I can't add flags/options.

---

### Post by ga2re2t on 2011-12-01
bump!

would also like to know how to set a custom default application. need to manually set acroread as the default PDF reader because for some strange reason it's not showing up in the list of alternative apps (even after remove/install).

Cheers!

---

### Post by perpetuus.flamma on 2011-12-11
> **ga2re2t said:**
> bump!

would also like to know how to set a custom default application. need to manually set acroread as the default PDF reader because for some strange reason it's not showing up in the list of alternative apps (even after remove/install).

Cheers!

hmm..try Moving the ~/.local/share/applications file to some other location.
that did the trick for me..if your problem was changing the default application for a file.

---

