---
title: "Microsoft Bluetooth Mobile Keyboard 6000"
date: 2011-04-30
forum: Desktop Environments
---

### Post by COMTIBoy on 2011-04-30
I'm currently running Ubuntu 11.04 and having trouble getting my Microsoft Bluetooth Mobile Keyboard 6000 sync'd up.

Under Bluetooth setup, I select Setup New Device.  My keyboard shows up in the list. I highlight it, it then prompts me to enter in the PIN number that is shown. I type in the pin number and press <enter> and nothing happens after that.  Its like the system is not receiving the input.

If I install Kubuntu 11.04 on the same system...the Bluetooth utilities work fine and I'm able to get the keyboard working, so it appears this doesn't seem to work when running the gnome interface.

Any tips on how I can get this working ?  I know the keyboard works fine.

I think if I can get this solved, I'll truly be a happy camper.

Thanks in advance

---

### Post by COMTIBoy on 2011-04-30
Humm....I think I just got it working.

1.Opened a terminal shell.
2.Typed:  

gksudo /etc/init.d/bluetooth stop
gksudo /etc/init.d/bluetooth start

3. Then it started working...(no pin entered....) right from within the terminal. 

I'd still be curious to know if others are using this keyboard with 11.04 and your experiences.

Thanks

---

