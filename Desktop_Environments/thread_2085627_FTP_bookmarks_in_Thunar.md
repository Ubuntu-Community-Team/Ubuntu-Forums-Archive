---
title: "FTP bookmarks in Thunar"
date: 2012-11-18
forum: Desktop Environments
---

### Post by 3Nex on 2012-11-18
In Nautilus, i used to have all my FTP accounts as bookmarks (in the side pane) which is incredibly convenient... Now i switched from Gnome to XFCE desktop and Thunar doesn't want to remember any "remote" (i'm guessing) bookmarks. He only remembers local bookmarks. 

So if i bookmark [ftp://example.com](ftp://example.com) in Thunar, it works, but after next booting up this bookmark will no longer exist. 

Can i explain to Thunar that i want this bookmark to remain there?

---

### Post by LewisTM on 2012-11-18
The next version of Thunar (1.5.x) supports network bookmarks. You can install it by following the instructions [here]("http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html").

If you don't want to install a development version, you can do what Xfce users have been doing for the past few years and use **gigolo** to bookmark your network connections. Since I have many such and I don't want to crowd my bookmarks menu, I still prefer that simple and elegant program, even though I have Thunar 1.5.2 installed.

Cheers!

---

### Post by 3Nex on 2012-11-19
I actually will be satisfied with a development version of Thunar, but i have a question regarding a part of your post 
> **LewisTM said:**
> do what Xfce users have been doing for the past few years and use **gigolo** to bookmark your network connections
because for first use, Gigolo was pretty confusing for me. It just wouldn't ask me or let me enter my credentials for the FTP account i wanted to test. The Edit option simply didn't offer that field. And if i'd double click the FTP account i've entered, it would just say that it can't connect to it (no **** sherlock). 

So I guess my question here is: Why are all those Xfce users not using Nautilus instead?

---

### Post by LewisTM on 2012-11-20
Gigolo makes a great dashboard for FTP connections, especially in list mode with the side panel visible. You get one-click control over your connections. I'm surprised it hasn't worked for you. Gigolo uses the same susbsystem as Nautilus's 'Connect to server' function and stores the passwords in the same keyring.

You can use Nautilus as your preferred file manager in Xfce, many users opt for that, although with the new Thunar I expect fewer will, it's that awesome.

Thunar has some undeniable advantages
1) It uses the same libraries and toolkit as Xfce so it loads faster and uses less RAM
2) It displays file lists faster.
3) It's [User Custom Actions]("https://help.ubuntu.com/community/ThunarCustomActions") are very powerful.
4) It has a "Open Parent folder" button
5) It supports Emblems
6) It supports associating filetypes with new custom commands.
7) It has a built-in bulk file renamer.

---

### Post by rai4shu2 on 2012-11-20
> **3Nex said:**
> So I guess my question here is: Why are all those Xfce users not using Nautilus instead?

Nautilus is a part of Gnome, and I don't want to run Gnome. I just want Xfce. Or rather I want Xfce and [Worker]("http://www.boomerangsworld.de/worker/"). It takes a bit of getting used to, but it is vastly superior to every other file manager.

---

### Post by Frogs Hair on 2012-11-20
So I guess my question here is: Why are all those Xfce users not using Nautilus instead?

I used Nautilus at first because Unity and the Gmome Shell use it and I am running the XFCE session and not Xubuntu. I have switched back to Thunar in the XFCE session because it is much faster that shell.

---

