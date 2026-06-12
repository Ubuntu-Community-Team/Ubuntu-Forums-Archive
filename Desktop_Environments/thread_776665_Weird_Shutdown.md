---
title: "Weird Shutdown"
date: 2008-04-30
forum: Desktop Environments
---

### Post by Live2Hunt on 2008-04-30
Whenever I shutdown or restart, a black screen appears with some text that I assume, is what it's doing in the background when it shuts down. The usual Ubuntu screen does not appear when you shutdown. Can someone help me fix this? I'm still pretty new to Ubuntu, been using it for 5 days now.

---

### Post by i2k on 2008-05-01
Does the Ubuntu screen show when booting up?

---

### Post by Live2Hunt on 2008-05-01
Bootup works fine as it should. It's just the shutdown that has a problem. It doesn't effect the shutdown in anyway, but I just find it rather annoying.

---

### Post by rossmoore on 2008-05-01
I've been getting the same thing - shutdown has been taking longer than usual. I've had a black screen with some text, and then some error/warning messages pop up for about a second before it finally shuts down.

I have resolved to investigate this tonight and tomorrow. I'll try and write down what I can of the messages, and see if I can find where (if?) the shutdown log is written to so I can hopefully peruse the messages at my leisure.

I presume the problem is a malfunctioning driver, or perhaps some disc mounting/unmounting issue, but I don't know for sure yet. Have you got an ATI graphics card? Others have noticed something might be incompatible between the fglrx ATI graphics card driver and the kernel - I have an ATI card and have been having problems and I'm told this could be the cause.

See if you can remember / photograph what it says during shutdown.

I warn you now, I'm a relative noob myself so if anyone else cares to pitch in they're more than welcome...

---

### Post by Live2Hunt on 2008-05-01
I have an Nvidia graphics card with the restricted drivers.
This started happening only 2 days ago and I had the drivers before then. I'm pretty sure this isn't the cause of it.

---

### Post by yssida on 2008-05-01
Mine does too and it's taking longer than usual to shutdown.

---

### Post by jbpostal on 2008-05-01
wht is registry entry problem ?? and does it comes from an improper shutdown ?

---

### Post by jeremy12 on 2008-05-01
I to am getting this issue but it also happens when i restart

Screen shot of the Shutdown screen:
[IMG]http://i31.tinypic.com/rsvqwy.jpg[/IMG]

What is some general hardware is everyone using that is getting this error?

I am using a Dell Oxtiplex 745

-SATA Hard Drive (i think this or dual core is the issue)
-ATA CD/DVD Drive
-Intel Dual core
-and just the base on board video and LAN

---

### Post by rossmoore on 2008-05-01
Mine's not really like that - definitely no "sigkill" messages, and booting up is fine and error-free.

(Well, I haven't fully checked dmsg, but it looks fine).

I'll tell you more tonight when I'm in front of the machine.

Hardware - Pentium 3.0Ghz (it shows 2 processors in XP and Ubuntu, but I think they're hyperthreaded or something, I'm pretty sure it's not dual core), Dell machine, ATI X300 card, 1Gb RAM.

---

### Post by rossmoore on 2008-05-02
Sorry, I'm going to have to bow out for a little while. My ubuntu computer has just gone to heaven.

Before it died, I had a look in etc/rc.local which is the script that's run on shutdown. There was some stuff in there relating to removing modules and even installing modules (a modprobe line with no -r option) which seemed a bit odd, so I commented that out (the default is an empty script). It didn't seem to make a difference, but I wonder if you have to rebuild the boot image for changes to this script to be picked up?

---

### Post by Roger Kauffman on 2008-05-02
I have recently upgraded my gutsy to hardy.  Overall the system is working extremely well but like a few others I also am having Weird Shutdown problems.  My system will not shut down it merely hangs and the system freezes with the following messages:

NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed

NetworkManager: <WARN> nm_dbus_init(): Could not get the system bus.  Make sure the message bus daemon is running!

The only way to recover to to crash the system through a forced power down.

The system will subsequently start in what seems to be a normal way.

I would be grateful for any help.

---

### Post by rossmoore on 2008-05-02
My PC is now dead - in a pre-Bios running kind of way, so I'm guessing power supply, see my earlier posts.

But that's exactly the messages I was getting, only with mine the messages were only displayed for about 2s, after a long pause during shutdown (1 minute?), and before it did finally and correctly shutdown.

---

### Post by luisjorge on 2008-05-27
Hi! I'm having the same problem (the black screen with white text at shutdown instead of the "splash" screen). This began about three weeks ago after an update of several things, and I don't know what caused it. I haven't found a solution yet, but I'm investigating. Shutdown doesn't take longer than usual, only looks really ugly, lol.

---

### Post by geoffree on 2008-05-31
Since upgrading to Hardy I get an error message when shutting down. It sounds similar to what you are describing.  The text is as follows:

NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [1211975349.806238] nm_print_open_socks(): Open Sockets List

NetworkManager: <debug> [1211975349.806238] nm_print_open_socks(): Open Sockets List Done.

NetworkManager: <WARN> nm_hal_deinit(): libha1 shutdown failed - Connection is closed

NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running!

The shutdown works without problems except for this message.  How do I get the message bus daemon to run?  Or otherwise, how to respond to this error message?

Geoffrey

---

