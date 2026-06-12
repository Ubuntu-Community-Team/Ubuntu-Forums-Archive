---
title: "gnome-shell-extensions-alternate-tab: Alt-Tab window disappearing immediately"
date: 2011-10-17
forum: Desktop Environments
---

### Post by synd7 on 2011-10-17
I've been using gnome3 for a while on oneiric for a while and alternate-tab has never been working right for me. I figured it was just a product of using a development release but apparently not :/

I'm using the Webupd8 ppa to get the extensions if that makes a difference: ```
ppa:webupd8team/gnome3
```

I can alt-tab to the next window but it seems like its not registering that i'm holding the tab button, the window switcher disappears immediately.
If alt + tab are held the window stays up but the windows cycle way to quickly to be of any use in changing windows.

I've tried various gnome-shell themes and that hasnt changed anything
Stock alt-tab behaves fine in this respect.

Anyone else had this problem/have a solution?

---

### Post by CurlySurmudgeon on 2011-10-17
[http://www.only10types.com/2011/06/ubuntu-1104-natty-slow-alttab-window.html](http://www.only10types.com/2011/06/ubuntu-1104-natty-slow-alttab-window.html)

That fixed the alt-tab problem when I was running 11.04 but now that I've 'upgraded' (argh!) to 11.10 compiz has been deleted.  Along with many other things I had installed.  Some, like Album Shaper not only disappeared but the albums & photos too.  Worse, 11.10 won't even let me install the .deb that worked flawlessly in 8.x, 9.x, 10.x & 11.04.

I'm really bummed out with 11.10, it screwed my workstation so badly that it was unusable for 2 days and finally had to revert out of Unity...

WTF?

---

### Post by synd7 on 2011-10-18
Compiz isnt running, i'm using gnome-shell, not unity

---

### Post by Fran! on 2011-10-18
synd7, I'm having the same problem here. I'm not able to go through more than just one window when using "Alt-Tab". Switching off AlternateTab extension will let me use Alt-Tab normally, but of course I would love to be able to switch between all my Windows, not just my programs!

I'm using the same PPA. Detailed info:

ii  gnome-shell-extensions-alternate-tab                        3.2.0-0~webupd8~oneiric4                          Alternate Tab extension to GNOME Shell
ii  gnome-shell                                                 3.2.0-0ubuntu1                                    graphical shell for the GNOME desktop

Enabled extensions: 

System monitor
Native Window 
Pidgin IM
Dock
Applications Menu
Places Status


Been on Gnome3 just for today and I don't want to start hating it ! I feel lost without a complete Alt-Tab and without my "Open Windows" panel.

---

### Post by Fran! on 2011-10-18
Been looking at the xsession-error logs on my home folder. Each time I activate AlternateTab and do "Alt-Tab" combination I get the following error logged:

Window manager warning: Log level 8: g_source_remove: assertion `tag > 0' failed
Window manager warning: Log level 8: g_source_remove: assertion `tag > 0' failed

Tryed to google it without any luck. Any clues ?

---

### Post by snoxu on 2011-10-20
I'm also having trouble with this extension on Archlinux. 

When enabled and I alt-tab, it renders windows unusable and eventually the shell crashes.

I also experience the same thing as the OP in the previous version of extension.

A bit buggy if you ask me.

---

### Post by juniper1982 on 2011-10-21
same here.  windows switch too quickly.  however, the shell is stable - it never crashes.

---

### Post by Schr on 2011-10-28
I'm having the same problem. And i'm using the ppa:ferramroberto/gnome3

---

### Post by f_padia on 2011-11-02
I see this too. the windows disappear sooo fast its literally useless. Idea is great though. Hope this can be fixed easily

---

### Post by synd7 on 2011-11-14
Still going here and now its crashing gnome-shell.

grrr, i think it might be time to learn javascript and write my own window switcher

---

### Post by Copper Bezel on 2011-11-14
I'm honestly surprised there aren't any fixes out, if the problem is this widespread (even on Arch.) I have the same issue - Workspace / Icons switches immediately between the top two windows with no popup, and All / Previews crashes the shell. Either one is still better than the application-centric, workspace-agnostic default Alt+Tab, of course. = P I'm not considering it a major problem for my workflow - I just use the Super key and click - but it's comforting to know I'm not the only one for whom this extension simply does not work.

---

