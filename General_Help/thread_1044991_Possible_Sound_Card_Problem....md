---
title: "Possible Sound Card Problem..."
date: 2009-01-20
forum: General Help
---

### Post by RoB RuLeZ on 2009-01-20
I recently installed Ubuntu to my machine and I believe I may have a problem with my soundcard. When my machine tries to play a sound, like recieving a new email message for example, I hear a very annoying, low beep sound and it comes from the speaker even if I have headphones plugged in. Correct me if I'm wrong but I don't believe that is normal. Please keep in mind I am absolutely new to Ubuntu so keep your responses as basic as possible. Thanks in advance to any helpful responses.

---

### Post by Yashiro on 2009-01-20
[http://www.foogazi.com/2008/05/01/how-to-disable-the-system-beep-in-ubuntu/](http://www.foogazi.com/2008/05/01/how-to-disable-the-system-beep-in-ubuntu/)

---

### Post by RoB RuLeZ on 2009-01-20
> **Yashiro said:**
> [http://www.foogazi.com/2008/05/01/how-to-disable-the-system-beep-in-ubuntu/](http://www.foogazi.com/2008/05/01/how-to-disable-the-system-beep-in-ubuntu/)

Thank you my friend, however the 'system beep' tab they speak of is not there.

---

### Post by Yashiro on 2009-01-20
So use the other method?

Open Applications Menu, Accessories, Terminal

Type:

> sudo gedit /etc/modprobe.d/blacklist

And then add these three lines to the bottom of the file:

> #pc speaker beep
blacklist pcspkr
blacklist snd_pcsp

Save the file and quit gedit.
Reboot.

---

### Post by RoB RuLeZ on 2009-01-20
> **Yashiro said:**
> So use the other method?

Open Applications Menu, Accessories, Terminal

Type:



And then add these three lines to the bottom of the file:



Save the file and quit gedit.
Reboot.
Excellent, thank you.

---

