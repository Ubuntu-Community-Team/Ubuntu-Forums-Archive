---
title: "How can I use screen edges in Unity?"
date: 2011-05-03
forum: Desktop Environments
---

### Post by udippel on 2011-05-03
I for one find Unity not as bad as others. What I despise is that screen edges don't work any longer for me. Respectively corners ... .
In the 'old' Gnome, I used to have full screen applications on the desktop; for example Virtualbox running something in full screen. Then I would have compiz set to expose all desktops by an upper left corner mouse event. Then I could easily click on another application to switch to it.
With the event of Unity, this doesn't work any longer. Worse, the launcher doesn't pop up when I create a mouse event on the left edge in Virtualbox. So I cannot switch between Virtualbox and other applications any longer, except by un-full-screen Virtualbox in order to navigate.
Very ugly.
Is there any possible way, for example by setting, that the unity launcher overrides the present screen (Virtualbox) like it did before for edge events?

---

### Post by bloodorange on 2011-05-03
You can still do this in Unity.  Have you installed CompizConfig Settings Manager?  With that installed, go to the Scale plugin.  Then click on the Bindings tab.  The setting you need is probably the top one that says Initiate Window Picker.  It can be set to any corner or edge, although you wouldn't want to use the top-left corner in Unity as that's already in use to activate the Panel.

It still works when you have full screen virtual machines running in VirtualBox, but you just have to hit and release the right Ctrl key before moving your mouse to your chosen corner.

---

### Post by udippel on 2011-05-03
> **bloodorange said:**
> 
It still works when you have full screen virtual machines running in VirtualBox, but you just have to hit and release the right Ctrl key before moving your mouse to your chosen corner.

That's what I call a downgrade or regression, actually. because I don't like my fingers on the keyboard when what I want to achieve can be done with a mouse. Could be done before Unity came along, that is.

Thanks for the reply anyway!

---

### Post by bloodorange on 2011-05-04
This works the same for me in Natty as it did in Maverick and others before.  I've always had to press Ctrl to release the full-screen virtual machine so that I can return to the host.

---

### Post by udippel on 2011-05-04
> **bloodorange said:**
> This works the same for me in Natty as it did in Maverick and others before.  I've always had to press Ctrl to release the full-screen virtual machine so that I can return to the host.

You can argue until the cows come home, I didn't have to, by setting the top upper left corner as edge event, and now it is gone. Over. I do appreciate any hint to eventually get it back, though my interest is low in how others configured their compiz in a manner that required a combined keyboard- and mouse-event. While I could in a handy (and impressive) manner use a single mouse event to switch between Gnome and XP.

---

### Post by bloodorange on 2011-05-04
I wasn't arguing with you.  I was just expressing my surprise, explaining how it has always worked on my systems, and, furthermore, just trying to help you.

---

### Post by Copper Bezel on 2011-05-04
> I do appreciate any hint to eventually get it back, though my interest is low in how others configured their compiz in a manner that required a combined keyboard- and mouse-event.
It's not a Compiz thing (or a Natty-Maverick thing.) It has to do with the way that VirtualBox handles host-guest mouse interaction, and it does seem to have changed, as the behavior I get is the one you describe (and my Virtualbox install is outdated, as VB's closed-source version has to be updated manually.)

Right Control is the Host Key, which reverts to the Host mouse cursor. Within VB, the cursor you're moving isn't your xcursor.

(This is actually rather a good thing in a *sense*, because it means that Compiz screen edges *within* virtual machines can be used now. = )

---

### Post by udippel on 2011-05-05
Yes, I get a better picture now. By the way, the 'Ctrl'-trick didn't work either here. 
So I need to go off full-screen and go back to full-screen if I want to be there later.
And when I do so, the launcher shows the two windows at its left, but I always end up at the VirtualBox-window that need to be minimized before I can access the guest. That's a very bad regression; and that's the nicest term I can find for this nonsense.  :(

Go away, unity!

---

### Post by udippel on 2011-05-06
> **Copper Bezel said:**
> It's not a Compiz thing (or a Natty-Maverick thing.) It has to do with the way that VirtualBox handles host-guest mouse interaction, and it does seem to have changed, as the behavior I get is the one you describe (and my Virtualbox install is outdated, as VB's closed-source version has to be updated manually.)

Right Control is the Host Key, which reverts to the Host mouse cursor. Within VB, the cursor you're moving isn't your xcursor.

(This is actually rather a good thing in a *sense*, because it means that Compiz screen edges *within* virtual machines can be used now. = )

I have no clue from where you get all of this.
Nothing is true. I just logged off - logged on to Ubuntu Classic (with effects), and get exactly what I got earlier. I can set the edge event to whichever edge I like, and then full-screen (!!) VirtualBox allows me to 'expo' with a single mouse event without any key. In 11.04, and the latest VirtualBox (4.0.6), to be repeated. And this is how I have been working for the last years, and I am not going to kiss anyone for deciding that this is a method 'not supposed to be used'. It is extremely handy, that is what it is, to switch between full-screen XP and Linux.

---

### Post by kokoshmusun on 2011-09-14
I used to be able to set edge-binding for showing the desktop.  Now there is no such option.  Where can I do that?  i.e., I hover to a corner and all windows are hidden, desktop shows.

---

### Post by Copper Bezel on 2011-09-15
Go into CompizConfig Settings Manager and select General Options, then the Keybindings tab. Scroll down, and you'll see "Show Desktop" has a line for setting it to a screen edge. Click the little "None" across from the monitor icon, then the corner you want to set it to. Done. = )

---

### Post by kokoshmusun on 2011-09-16
> **Copper Bezel said:**
> Go into CompizConfig Settings Manager and select General Options, then the Keybindings tab. Scroll down, and you'll see "Show Desktop" has a line for setting it to a screen edge. Click the little "None" across from the monitor icon, then the corner you want to set it to. Done. = )

Thanks a lot! ):P

---

