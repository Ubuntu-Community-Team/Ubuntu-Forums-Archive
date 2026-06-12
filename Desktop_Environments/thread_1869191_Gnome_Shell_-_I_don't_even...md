---
title: "Gnome Shell - I don't even.."
date: 2011-10-25
forum: Desktop Environments
---

### Post by BazookaAce on 2011-10-25
Hey folks, 

So, like many people out there i've been trying to find a fix for when we enable "show desktop icons" while using Gnome Shell, since when we enable the desktop icons, the retarded GlobalMenu pops up *under* GS' statusbar. 

So i installed a new extension a couple of days ago that allows you to quickly open folders in nautilus and grant root access to the file system. 

The weird thing happened a couple of minutes ago. I thought it might be a bug, but i can reproduce it over and over again. 

**How it originally looks with the desktop icons enabled:**

[IMG]http://img822.imageshack.us/img822/525/desktop87.png[/IMG]

**Here's how it happened:**


[IMG]http://img233.imageshack.us/img233/6393/extensionpresscropped.png[/IMG]

**After i press it i need to access root:**

[IMG]http://img820.imageshack.us/img820/2329/autinputcropped.png[/IMG]

**And then the background disappears, (i added a new one) and voila! Desktop icons *without* global menu. **

[IMG]http://img402.imageshack.us/img402/987/desktopcropped.png[/IMG]

**But it will revert back when i log out, so how do i make it permanent? I know that if i do it permanent i'll have root access all the time, but you know.. i would like to have it**

---

### Post by crdlb on 2011-10-25
Just about everyone else had been able to remove that bar by removing appmenu-gtk3. From an earlier thread, I see that was suggested. Did you try it?

---

### Post by BazookaAce on 2011-10-25
I've tried and failed. It just won't work :(

---

### Post by BazookaAce on 2011-10-25
I've uninstalled the appmenu. What else do i have to uninstall? 

[IMG]http://img38.imageshack.us/img38/1795/rsz1screenshotat2011102.png[/IMG]

---

### Post by BazookaAce on 2011-10-25
Sorry for the bump, but i really want to figure this out.

---

### Post by crdlb on 2011-10-25
A fixed nautilus package has been released to oneiric-proposed. It will show up in oneiric-updates eventually, but you can install it from -proposed now: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

---

### Post by BazookaAce on 2011-10-25
Holy! 101 MB of updates on the proposed repo :p

---

### Post by merlinus on 2011-10-25
If I read the messages correctly, the Nautilus update was in today's update packages.

---

### Post by BazookaAce on 2011-10-25
> **crdlb said:**
> A fixed nautilus package has been released to oneiric-proposed. It will show up in oneiric-updates eventually, but you can install it from -proposed now: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

I want to make sweet sweet love to you. It works!

[IMG]http://www.funny-games.biz/images/pictures/661-give-me-a-kiss.jpg[/IMG]

**@Merlinus:** Yup, but it didn't fix my problem, but the one from the proposed repo did the job :)

---

### Post by merlinus on 2011-10-25
Glad the problem is fixed.  It is a non-issue for me, since I use a top panel and have compiz handle the desktop.  It is irrelevant whether or not mounted drives are displayed as icons.

But what dark theme are you using?  My old ones were not gtx3+, and so the only one I could find that works reasonably well with gnome-fallback is Marples-black.

---

### Post by BazookaAce on 2011-10-25
Shell theme is Elegance: [http://browse.deviantart.com/?qh=&section=&q=gnome+shell+elegance#/d4cyfw3](http://browse.deviantart.com/?qh=&section=&q=gnome+shell+elegance#/d4cyfw3)

GTK3 is Zukitwo: [http://gnome-look.org/content/show.php/Zukitwo?content=140562](http://gnome-look.org/content/show.php/Zukitwo?content=140562)

---

### Post by merlinus on 2011-10-25
Thanks for the links.  In my gnome tool, though, under Theme, the Shell Theme listings cannot be accessed.  The setting is preceded by a red exclamation point.

I have installed the shell extensions, however, but nothing shows up there either.

Any ideas???

---

### Post by crdlb on 2011-10-25
> **merlinus said:**
> Thanks for the links.  In my gnome tool, though, under Theme, the Shell Theme listings cannot be accessed.  The setting is preceded by a red exclamation point.

I have installed the shell extensions, however, but nothing shows up there either.

Any ideas???

The user theme extesion is probably failing to load. Press alt+f2 and type lg. Check the Errors tab.

---

### Post by merlinus on 2011-10-25
lg: command not found

---

### Post by BazookaAce on 2011-10-25
ALT + F2 and type R (Gnome Shell will reload). Close Gnome Tweak Tool and open it again. If it still doesn't work, check your updates. An update was released today (from the webupd8 repo).

---

### Post by crdlb on 2011-10-25
> **merlinus said:**
> lg: command not found

It said that in gnome-shell's alt-f2 dialog? 'lg' is a special command like 'r' or 'rt'. It's not a regular command.

---

### Post by merlinus on 2011-10-25
error msg: The program 'R' is currently not installed.

---

### Post by merlinus on 2011-10-25
> **crdlb said:**
> It said that in gnome-shell's alt-f2 dialog? 'lg' is a special command like 'r' or 'rt'. It's not a regular command.

Could not open location 'file:///home/merlin/lg'

When I ran the R command in a terminal, this was added info in addition to command not found:

You can install it by typing:
sudo apt-get install r-base-core

---

### Post by BazookaAce on 2011-10-25
What the.. :p You do have Gnome Shell installed?

---

### Post by crdlb on 2011-10-25
> **merlinus said:**
> Could not open location 'file:///home/merlin/lg'

I assumed you were using GNOME Shell. Apparently, that is not the case. Shell themes are for GNOME Shell. They won't work with the fallback panel or anything else.

---

### Post by merlinus on 2011-10-25
Please forgive my ignorance, but I thought gnome shell and fallback were the same.  IIRC I installed both, but which option do I select at login for shell?

Also, is there a shortlist of differences between the two?

---

### Post by crdlb on 2011-10-25
'GNOME' is GNOME Shell
'GNOME Classic' is the fallback session with gnome-panel and metacity.

If GNOME Shell fails to start, the fallback session will be run instead.

---

### Post by BazookaAce on 2011-10-25
If you want to use Gnome Shell you must install it

```
sudo apt-get install gnome-shell
```

After installation log out and choose "GNOME" as your session. If you want to go back to Fallback, then log out and choose "Ubuntu Classic".

---

### Post by merlinus on 2011-10-25
I have a GNOME option at login, so shell must be installed.  However.....  &*^%$%^&&*

Clicking on Activities makes my desktop look like an iPhone!

No thanks...

---

### Post by BazookaAce on 2011-10-25
Yo, it's linux you're using. You can customize it :p

---

### Post by merlinus on 2011-10-25
I have already spent hours customizing gnome-fallback, and it is pretty close to what I had in 10.10.

But given that cold weather is on the way, I will probably futz around with gnome-shell as well.

My preference is for a clean desktop, with a few icons for most-used apps and dropdown menus at the top left, and date/time, sound, logout and network connections at the top right, of a transparent-background toolbar.

I also use a dark theme for everything.

Thanks...

---

