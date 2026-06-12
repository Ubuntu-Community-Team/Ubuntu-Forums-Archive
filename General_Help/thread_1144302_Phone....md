---
title: "Phone..."
date: 2009-04-30
forum: General Help
---

### Post by A-bot on 2009-04-30
[SIZE=3]I am trying to connect my cell phone to my computer to transfer files. How can I access it?

Thanks,
Adam
[/SIZE]

---

### Post by calvinps on 2009-04-30
> **A-bot said:**
> [SIZE=3]I am trying to connect my cell phone to my computer to transfer files. How can I access it?

Thanks,
Adam
[/SIZE]

What are you using to connect your phone? It is a lot easier just to use its USB cable.

;)

---

### Post by A-bot on 2009-04-30
That's what I am using :P.

---

### Post by calvinps on 2009-04-30
> **A-bot said:**
> That's what I am using :P.

Ok. When you connect your phone, the memory card (if any) and flash memory shortcuts should just appear on the desktop, and when you click on them, you now have access to your phone's files!

Eazy peazy lemon squeezy :lol: :P :D

---

### Post by A-bot on 2009-04-30
They don't appear on the desktop. When I put in an SD card or attach an external hard drive, the icons appear on my desktop. When I plug in my phone, nothing comes up, not even in computer.

---

### Post by Hobgoblin on 2009-04-30
What phone?

---

### Post by calvinps on 2009-05-01
> **Hobgoblin said:**
> What phone?

His cell phone.

**[deleted]**

---

### Post by jigglywiggly on 2009-05-01
What cell phone is this? Do you just browse it like a memory stick? Or is it an iPhone where you have to SSH the phone to access the files?

---

### Post by elasto1mania on 2009-05-01
run this in terminal
```
tail -s 3 -f /var/log/messages
```
What do you get?

---

### Post by A-bot on 2009-05-03
> **jigglywiggly said:**
> What cell phone is this? Do you just browse it like a memory stick? Or is it an iPhone where you have to SSH the phone to access the files?

I'm using an HTC Touch Diamond Pro.

---

### Post by Annoying Moose on 2009-05-17
We have another victim!

I recently obtained a Samsung Slyde SPH-M540 cell phone, and currently have it connected to my computer via USB.  The cell phone appears to recognize my computer - it says it's connected, and has even taken the opportunity to charge its battery - but Ubuntu seems oblivious.  No appropriate options seem to be available; no icons have appeared in the desktop, computer, /mnt, or /media folders.

When I run [FONT="Monospace"]tail -s 3 -f /var/log/messages[/FONT] in a terminal window, I get this:

```

May 17 15:47:50 eman-laptop kernel: [11345.205735] usb 7-1: USB disconnect, address 2
May 17 15:47:54 eman-laptop kernel: [11349.278447] usb 7-1: new full speed USB device using uhci_hcd and address 3
May 17 15:47:54 eman-laptop kernel: [11349.435414] usb 7-1: configuration #1 chosen from 1 choice
May 17 15:47:54 eman-laptop kernel: [11349.438778] cdc_acm 7-1:1.0: ttyACM0: USB ACM device
May 17 15:50:28 eman-laptop kernel: [11503.148828] usb 7-1: USB disconnect, address 3
May 17 16:18:57 eman-laptop -- MARK --
May 17 16:38:23 eman-laptop kernel: [14372.861847] usb 7-1: new full speed USB device using uhci_hcd and address 4
May 17 16:38:23 eman-laptop kernel: [14373.021791] usb 7-1: configuration #1 chosen from 1 choice
May 17 16:38:23 eman-laptop kernel: [14373.025254] cdc_acm 7-1:1.0: ttyACM0: USB ACM device
May 17 16:58:57 eman-laptop -- MARK --

```

---

### Post by A-bot on 2009-05-18
My phone will recognise it, and it will charge, Ubuntu just won't recognise it, and that's where the problem is.

---

### Post by merlin_ie on 2009-05-18
not sure if this will help you, but as you're using a data cable, maybe you should check the phone settings and in the section " PC connection ", you can choose " Mass Storage "..It's what I do with my Samsung Tocco. Hope this helps

---

### Post by Annoying Moose on 2009-05-23
"Helps" is too mild a word.  From the main menu, I selected Tools, then Mass Storage, then Connect to PC, and voila: 8.0 GB Media icon on the desktop.  It seems odd that it won't do that by itself automatically when it finds a connection, but at least it works.  Thank you!

---

### Post by merlin_ie on 2009-05-23
glad to have helped :D:D

---

