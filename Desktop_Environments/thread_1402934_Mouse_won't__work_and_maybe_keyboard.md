---
title: "Mouse won't  work and maybe keyboard"
date: 2010-02-09
forum: Desktop Environments
---

### Post by IWC316 on 2010-02-09
I just installed Ubuntu for the first time and the mouse would not work.  I restarted the computer and it did for only maybe 10 sec.  I have never used Linux so i am not sure if the keyboard works. I tried to hi alt to get to a menu bu I got nothing.  It is a wireless keyboard "Logitech" and a wired Gateway mouse. 
 
So what is the deal?

---

### Post by IWC316 on 2010-02-09
The keyboard works to login  with the password and alt does nothing when I rebooted it.  When I boot vista they both work.

---

### Post by IWC316 on 2010-02-09
Ok I have rebooted and gave it another shot.  I tried to clicked firefox quick and the little circle popped up to show it was working and it froze.  So it seem to be the whole deal.
 
Anyone?   Anyone?

---

### Post by warp99 on 2010-02-09
You seem to have a conflict with other USB devices if the keyboard or mouse is also USB. Remove any other devices and try again. If the problem persists try a different USB slot for the keyboard and/or mouse.

---

### Post by jenaniston on 2010-02-09
A full install ? . . . 
try the second choice for the Ubuntu recovery mode kernel - at least to get to a text command line
 and start troubleshooting -
 and at exit from *that *you can still be put in a user text mode but at a *full* runlevel " N 2", btw -
 but without GUI.

But if booting a live version that the screen won't come up (*not* your case here I think) -
but for the record for other readers . . . use the Esc key twice to get to a text mode choice.

What version / distribution by the way . . . and what is the cpu ? 64-bit . . . ?

Some config and/or drivers for your model keyboard/mouse/display prolly . . .

---

### Post by IWC316 on 2010-02-09
I get to the desktop and it appears to freeze up.  I have an Intel 1.6 GHz dual core processor and partitioned off 60g on the HDD.  I have tried unplugging each of the usb devices and no luck.  They are the key board, mouse, and wireless adapter.  I may be able to dig up an old style keyboard, ps2 if i remember right but that would defeat the purpose.  I am looking to get this puppy going as fast as possible to hook up to the HDTV.
 
I may try to reinstall Ubuntu and see if that takes care of it.:popcorn:

---

### Post by warp99 on 2010-02-10
You don't need to reinstall since that's not the issue. With Linux you never need to reinstall except for a catastrophic failure. Constant reinstalling is a Windows mentality. This is only a conflict and you just need to resolve it. 

I suggest you go into your BIOS settings and make sure that your USB legacy devices settings for the keyboard/mouse are turned on. If they are then try the opposite and turn them off.

---

### Post by jenaniston on 2010-02-10
> **warp99 said:**
> You don't need to reinstall since that's not the issue. . . . This is only a conflict and you just need to resolve it. 

Yes, I agree . . . and it is very good to be reminded of this as I too have
 also found myself* falling *into that re-install mentality on occasion.
 > **warp99 said:**
>  . . .
I suggest you go into your BIOS settings and make sure that your USB legacy devices settings for the keyboard/mouse are turned on. If they are then try the opposite and turn them off.

Good suggestion . . .

 USB input devices, such as a keyboard or mouse, can require USB legacy emulation to work correctly.

As an alternative,
 you can configure the USB host controller's resource settings to **match those that are assigned by the BIOS** . . .
so to resolve the conflict you can try setting the USB Host Controller to use the BIOS settings.

---

### Post by warp99 on 2010-02-10
I just remembered, I had a similar problem with a Logictech keyboard and mouse combination not working correctly on an EVGA motherboard. The solution for me was to plug the mouse into the P/S 2 (purple) keyboard connector and the keyboard into a USB slot sans the adapter. 

BTW I did this by accident and was surprised that it worked!!!

---

### Post by uilenspiegel on 2010-02-15
What you're describing sounds similar to the issue described, and solved, in this post on the Mint forums: [http://forums.linuxmint.com/viewtopic.php?f=49&t=38423&start=0](http://forums.linuxmint.com/viewtopic.php?f=49&t=38423&start=0)

Does this seem to be the problem?

---

