---
title: "Installing Fluxbox?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by firecrotch on 2006-06-01
Hi,

I am running the Dapper RC of Kubuntu and I want to install Fluxbox.  I read in other threads that sudo apt-get install fluxbox would install it, but apparently, it's not in the repositories.  Do I have to install Fluxbox manually from source or what?

Thanks in advance.

---

### Post by bluevoodoo1 on 2006-06-01
Should be in the "universe" repository...
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Neobuntu on 2006-06-01
Quite fankly I would advise you try Xfce via "sudo apt-get install xubuntu-desktop" if your machine can handle it; because it's basically done and with menus and all.

If you want faster then you can try the (work in progress)  Ubuntu Lite (google it's wiki) as it uses Icewm and should be better on the slowest systems (way worst than people are giving away today; depending on where you are.) You might add a source list and install ubuntu-lite-desktop OR you may prefer to apt-get install a whole string of packs to make "Ubuntu Lite" on top of Ubuntu server install (see it's Wiki site.) Remember though, you'll be on your own form menu setup and stuff here. It's part done.

Fluxbox can be done but it's a lot more work and you'll miss what Ubuntu does for you (like your time back.) You might like DSL Linux better on REALLY old machines (That are hard to give away). Sorry if that's no help to you but I've tried them all at one time or another.

While Linux is great for new software on old hardware there's still no substitute for smokin' new(er) hardware.

---

### Post by Neobuntu on 2006-06-01
Yep, I just installed fluxbox and fluxconf and it was pretty and fast but NOTHING was configured. No menu, no terminal, no EXIT! 

When I crashed X "<Ctrl><Alt><Backsapce>" the kdm looped back to un-setup Fluxbox. Ack!

I was in the process of reinstalling GDM anyway so I did that via console (and now I'm stuck in xfce only) due to permissions on my .dmrc file the damnable thing keeps telling me (even though I set it to chmod 644 like it said.)

So you REALLY have a lot of work to do unless someone has a repo for Ubuntu-fluxbox somewhere.

Let's see, Fubuntu? :)

---

### Post by firecrotch on 2006-06-01
> **Neobuntu]Quite fankly I would advise you try Xfce via "sudo apt-get install xubuntu-desktop" if your machine can handle it said:**
> 

My hardware isn't THAT old... I just like Fluxbox.  I don't know why, but sometimes I just prefer it over KDE.  Thanks for the advice though.

[QUOTE=bluevoodoo1]Should be in the "universe" repository...
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Thanks a lot, that did it.  Working from Fluxbox now. :)

---

### Post by bluevoodoo1 on 2006-06-01
[QUOTE=firecrotch]Thanks a lot, that did it.  Working from Fluxbox now. :)[/QUOTE]

Alright! :)

---

### Post by Personatech on 2006-06-01
Hmmmm...  Good point re: XFCE and IceWM, I've used XFCE extensively and really liked it, IceWM less so.  That being said, I'm really digging Fluxbox right now.  I'll admit it does require a lot of work up front (you MUST read the Wiki and follow its instructions carefully - on my Dell notebook simply doing an apt-get was NOT all that was required).  However, the work you put into Fluxbox will be repaid handsomely when you settle down to use the WM.  Right click anywhere on the desktop and you have your menu - no moving the mouse to a taskbar to launch a program.  It's extremely responsive, supports KDE and Gnome programs, and has a nice clean interface that can be tricked out as much (or as little) as you like.

---

### Post by Neobuntu on 2006-06-01
Fubuntu rules!

---

