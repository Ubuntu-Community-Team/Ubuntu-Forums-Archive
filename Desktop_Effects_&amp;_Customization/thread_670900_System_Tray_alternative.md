---
title: "System Tray alternative?"
date: 2008-01-17
forum: Desktop Effects &amp; Customization
---

### Post by bakaeigo on 2008-01-17
Is there a standalone application that can act as a replacement for the default GNOME system tray? I've rid myself of the gnome panels, and the system tray app for AWN is very ugly, as well as completely uncustomizable.

---

### Post by glycerine102 on 2008-01-18
I like [Stalonetray]("http://stalonetray.sourceforge.net/").  I have set mine completely transparent and it looks aesthetically pleasing next to AWN.   Really the only problem I have now is getting rid of the last gnome-panel.

---

### Post by phyrewall on 2008-01-18
<strike>If this is for KDE, does it require KDE libs? I hope not. </strike>  Nevermind, I checked the deps. Duhr.

<strike>Also, is it possible to get rid of ALL gnome panels? If so, how? </strike> Nevermind also. Google is your friend.

Thnx

---

### Post by bakaeigo on 2008-01-18
> **glycerine102 said:**
> I like [Stalonetray]("http://stalonetray.sourceforge.net/").  I have set mine completely transparent and it looks aesthetically pleasing next to AWN.   Really the only problem I have now is getting rid of the last gnome-panel.

Thanks, I'll try that. Oh, and what I did to get rid of the last gnome panel:
type into the terminal "sudo nautilus", then navigate to usr/bin
move "gnome-panel" to the root folder. Then end gnome-panel from system monitor. It won't come back unless you put gnome-panel back into usr/bin.

---

### Post by zeusalmighty on 2008-01-20
Hi, I've actually removed all gnome panels with a less destructive way, 
[COLOR="Blue"]
**[LINK]("http://ubuntuforums.org/showthread.php?t=652367&highlight=awn+applets")**[/COLOR]

---

### Post by jeffus_il on 2008-01-20
The best thing is to use another window manager, You can use openbox, fluxbox, icewm, simply install via synaptic, they automatically appear on your login screen, and then add more minimalist desktop utilities, rox is one of them GKRellm is another, there are many alternatives, and that way you can always go back to your original gnome ...

---

### Post by zeusalmighty on 2008-01-20
There's something I need to ask, because there's some things I don't understand, excuse my stupidity.

So, Gnome is a **W**indow **M**anager, like KDE? Compiz is the desktop effects, but does it only work with Gnome, or can it work with any WM you install? And what are theme engines? I'm really confused with all these, sorry to barge in on the thread.

---

### Post by jeffus_il on 2008-01-20
> **zeusalmighty said:**
> There's something I need to ask, because there's some things I don't understand, excuse my stupidity.

So, Gnome is a **W**indow **M**anager, like KDE? Compiz is the desktop effects, but does it only work with Gnome, or can it work with any WM you install? And what are theme engines? I'm really confused with all these, sorry to barge in on the thread.

Gnome is not a window manager, it is a desktop environment running on Linux systems, It uses a window manager, the default one has been Metacity, it runs well on Openbox, It prefers managers supporting a certain standard, I forget now what it is, read below, and now seems to be going the compiz way to support fancy desktop effects.

[Read about Gnome]("http://en.wikipedia.org/wiki/GNOME")

[Read about Window Managers]("http://en.wikipedia.org/wiki/Window_manager")

---

### Post by mcduck on 2008-01-20
> **zeusalmighty said:**
> There's something I need to ask, because there's some things I don't understand, excuse my stupidity.

So, Gnome is a **W**indow **M**anager, like KDE? Compiz is the desktop effects, but does it only work with Gnome, or can it work with any WM you install? And what are theme engines? I'm really confused with all these, sorry to barge in on the thread.

No, Gnome, KDE and XFCE are Desktop Environments. They include a lot more than just window manager, they have their own sets of applications, widget toolkits, development tools and loads of other stuff working on background and making things like drag&drop possible.

Gnome's default window manager is Metacity, KDE has Kwin and Xfce uses Xfwm. Compiz is a window manager as well, so you can use it to replace the default window manager in desktop environments.

You can't run Compiz in Fluxbox, because they both are just window managers, if you remove Fluxbox from Fluxbox you have nothing left ;) But you can use Fluxbox or Kwin or any other as Gnome's window manager.

---

### Post by zeusalmighty on 2008-01-20
Thanks to both, that was pretty enlighting (Enlightment is another WM, right? ;) )

Back to the point. I also want to use a tray with my Kiba-Dock, but it's built-in looks awful. Any other apps like **stalonetray**? Anyone can tell me how to setup stalonetray to be completely transparent and Bottom Center? Thaaaanks!

---

### Post by urukrama on 2008-01-20
You can also try [trayer]("http://www.kfsoft.com/trayer/intro.htm").

---

### Post by zeusalmighty on 2008-01-20
Well, I'm either confused, or you're sarcastic and I don't get it, or you made a small mistake...

[Trayer]("http://www.kfsoft.com/trayer/intro.htm") seems like an application for Windows, and does something completely irrelevant to what I'm looking, it transfers applications from the task bar to the tray...

---

### Post by kaboodle_fish on 2008-01-20
> **bakaeigo said:**
> Is there a standalone application that can act as a replacement for the default GNOME system tray? I've rid myself of the gnome panels, and the system tray app for AWN is very ugly, as well as completely uncustomizable.

Do you mean something like Gimmie? 

[http://beatniksoftware.com/gimmie/Main_Page](http://beatniksoftware.com/gimmie/Main_Page)

---

### Post by zeusalmighty on 2008-01-20
That looks really interesting, but it's not what I was looking for, maybe the poster. Any other more lightweight suggestions?

---

### Post by urukrama on 2008-01-20
> **zeusalmighty said:**
> 
[Trayer]("http://www.kfsoft.com/trayer/intro.htm") seems like an application for Windows, and does something completely irrelevant to what I'm looking, it transfers applications from the task bar to the tray...

Sorry, I meant this [trayer]("http://packages.ubuntu.com/gutsy/x11/trayer"). Sorry for the confusion.

---

### Post by zeusalmighty on 2008-01-20
It's interesting, but I can't get it to function as I want it to. I want it's background to be completely transparent, so only the icons are showing, and to be on top all the time. Also, centered, but I already got that pinned down...thanks either way.

Anyone else?

---

