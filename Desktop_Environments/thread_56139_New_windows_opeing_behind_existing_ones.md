---
title: "New windows opeing behind existing ones"
date: 2005-08-11
forum: Desktop Environments
---

### Post by Watter on 2005-08-11
I had this problem in Fedora Core 4 (but not FC3) and it was one of the main reasons I decided to give Ubuntu a try. Well, as it turns out I really like Ubuntu, however this particular problem remains. 

About 30% of the time when I click an icon to open a new application, the new application will open its window behind the existing windows ont he destop instead of in front of them. It's quite maddening. It seems to happen most often with Firefox (although that may just be because that's the app I open the most) but it has happened at least a few times with most of the application that I frequently open new instances of, including Terminal and Nautilus.

Since this was happening to me on FC4 as wellas Ubunto (both completely fresh installs) I have to believe that others have experienced this as well. Any advice?

---

### Post by Stormy Eyes on 2005-08-11
It's not a bug, but a feature of most window managers. Under X Window, there are two popular "focus policies": "click to focus", and "focus follows mouse pointer". Under "click to focus", a window will remain unfocused until the user clicks on it. Under "focus follows mouse", the focus will follow the mouse pointer, but the window manager will not raise the window to the top unless either the user clicks on it or the user has set a "raise window on focus" option.

Some window mangers allow you to set an option to allow newly opened windows to grab the focus if you want it to, but I think that as of GNOME 2.10, the default policy is to avoid letting one window "steal" the focus from another.

You might find the [Understanding X Window](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-understanding.html) section of the FreeBSD Handbook useful.

---

### Post by Watter on 2005-08-11
If it were a consistent behavior or one I had experienced in the past three years of using Linux/Gnome as my primary workstation, I'd be more inclined to think that it's a misunderstanding of the expected behavior on my part. However, 1) it isn't consistent. I can click the same icon to start an application 10 times in a row and sometimes it will behave one way and the rest of the time another, and 2) I'm not new to Linux or Gnome and I have never experienced this behavior before. I've used Redhat 9, FC1, FC2, and then FC3 as my primary desktops for 9 hours a day for the last three years and never had this problem. 

Regardless of whether it's a bug or a "feature", it's killing my productivity and I'd love to find a workaround that allowed for the more typical behavior I've come to expect. 

When I open an new application, I'd like for the new application window to be on top. This seems fairly intuitive. Why would I have opened that app if I didn't intend to begin working with it. Most of the time, this is what happens, however, as I originally stated, about 30% of time it doesn't.

---

### Post by Watter on 2005-08-11
I don't know if this is helpful, but I can recreate this "feature" with some reliability by opening a new Firefox window (by clicking on the Firefox icon in my top panel), Alt-tabbing back to the window I was using before I opened the new Firefox window, and then clicking the Firefox launcher int he panel again. Most of the time (but not always), this will cause the second Firefox window to open behind the others. 

For what it's worth "Select windows when the mouse moves over them" is not checked in the "Windows Preferences".

---

### Post by Stormy Eyes on 2005-08-11
[QUOTE=Watter]Regardless of whether it's a bug or a "feature", it's killing my productivity and I'd love to find a workaround that allowed for the more typical behavior I've come to expect. [/quote]

It's not consistent? All right. I thought that it was consistent under Ubuntu and FC4, but you wanted to know why GNOME in Ubuntu and FC4 wasn't behaving the same way as under FC3. Sorry about that.

[QUOTE=Watter]When I open an new application, I'd like for the new application window to be on top. This seems fairly intuitive. Why would I have opened that app if I didn't intend to begin working with it. Most of the time, this is what happens, however, as I originally stated, about 30% of time it doesn't.[/QUOTE]

OK. It may be a bug in GNOME's standard window mangler, Metacity. I can't help you with Metacity, as I myself refuse to use it, but you can run GNOME with a different window manager if you want. I have a [HOWTO for using Openbox with GNOME](http://ubuntuforums.org/showthread.php?t=34239&highlight=openbox+gnome); if you want to, maybe you should try using Openbox instead of Metacity and seeing if it behaves more like what you're used to.

---

### Post by Watter on 2005-08-11
[QUOTE=Stormy Eyes]OK. It may be a bug in GNOME's standard window mangler, Metacity. I can't help you with Metacity, as I myself refuse to use it, but you can run GNOME with a different window manager if you want. I have a [HOWTO for using Openbox with GNOME](http://ubuntuforums.org/showthread.php?t=34239&highlight=openbox+gnome); if you want to, maybe you should try using Openbox instead of Metacity and seeing if it behaves more like what you're used to.[/QUOTE]
Hey, thanks! I'll look into that.

---

### Post by Stormy Eyes on 2005-08-11
[QUOTE=Watter]Hey, thanks! I'll look into that.[/QUOTE]

No problem. I wrote that HOWTO, so if you have any questions about Openbox, just post 'em there.

---

### Post by Watter on 2005-08-11
Well, good new and bad news (for me anyway). The good news is that this problem does not occur in Openbox. The bad news is that I've been using metacity for so long, that I'm not sure I can get used to Openbox very easily. I try to keep my hands off the rodent as much as possible and my fingers are so set in their metacity ways (switching between desktops, moving between windows, etc.) that I think it may take quite a bit of customization to get Openbox to where I could use it in a way I'd like. It certainly was nice and efficient, though. Fast too. 

I think I'll continue to look for a solution using Metacity. Nuts! They just fixed one of my mosted hated and longstanding problems with Metacity in this version and I thought I was free and clear.  ](*,)

---

### Post by Watter on 2005-08-11
Well I'll be a butternut's uncle...

According to [this](https://www.redhat.com/archives/fedora-desktop-list/2005-April/msg00022.html), it looks like Stormy was correct in his initial assumption of "feature" not "bug". A very poorly implemented feature because it's inconsistent (i.e. some times new windows grab focus and sometimes they don't), but a "feature" nonetheless.

This "feature" was intended to prevent new windows from "stealing" focus, and that's fine, if those new windows were generated by system or application without my explicit action (i.e. a GAIM New Message window). However, this isn't fine when we're talking about new windows explicitly created by the user such as by clicking an icon to start a new instance of an application. 

The way this panned out is a bit of a mess though, and I think I know why. As far as I can tell, almost all new application windows DO come up and grab focus. The reason my Firefox windows have been inconsistent in doing so is that when I click on the Firefox icon when an existing Firefox window alredy exists, a new application  instance isn't actually started. A command is actually sent to firefox for it to open a new window or tab (depending on how you have it configured). That is why the new windows are sometimes coming up behind currently focused window. 

I realize I'm basically talking to myself inthis thread, but hey, maybe someone else will have the same problem some time and this will give them a head start on it.

---

### Post by burlap on 2005-08-13
New apps are not focused when you hold ctrl after launching them. I encounter this problem quite often: I clik to open an app and in the meantime I use ctrl+something in another app and as I expect the new app to launch focused, it does not happen. 

Another case is best (beagle tool): it tends to open in the background without any reason (maybe it is the case of the feature described by Watter), but best is under development and I forgive it a lot... However, this time I might file it as a bug... 

And one more thing: I'd say that better behavior when you find a bug is to file it instead of trashing an app and using another one. Otherwise no apps will ever improve.

---

