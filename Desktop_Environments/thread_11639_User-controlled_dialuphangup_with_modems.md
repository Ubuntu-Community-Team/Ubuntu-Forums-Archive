---
title: "User-controlled dialup/hangup with modems"
date: 2005-01-18
forum: Desktop Environments
---

### Post by haakon on 2005-01-18
Greetings,

I am setting up my computer-illiterate father with an Ubuntu system. I have set up a serial modem in the setup dialog found under Preferences, and from that dialog, I can have it dial up and connect. However, that dialog requires sudo access to run, and seems to assume that people want to dial up during boot and disconnect on shutdown of the system.

What I want is for my father to be able to press a button to dial up (with no entry of passwords), and press a button to disconnect. Is there any way to do this?

I'm thinking of setting up gnome-ppp, but I have never used this program before? Does it come with Ubuntu? Will it work well? Any caveats?

Haakon.

Edit: Just to clarify, yes, I am talking about the good old-fashioned RS-232 serial 56.6kb modems. My father has no need for DSL :)

---

### Post by ilari on 2005-01-18
Hi,

You can use the "gnome modem lights" applet, which you can add to your father's gnome-panel. In the applet's settings you can define the commands that start and end the connection. I recommend using the pon and poff-scripts, but they require some additional configuration to be done.

First of all, your father has to be in the "dip" group. Secondly, you have to define the correct connection settings in /etc/ppp/peers/provider and /etc/chatscripts/provider. I use only LAN/WLAN so I am not sure, if the network-admin tool configures those files automatically. Another way is to name the peer's settings file explicitly after pon-command ('pon settings-file'). After the correct settings are configured, he can start/end the connection just by pressing the button in the applet. He also sees the connection status and time in the applet.

-- 
  Ilari

---

### Post by haakon on 2005-01-18
Thanks, Ilari, I will definitely try this. I didn't know about Modem Lights, it looks very relevant. Hopefully, the network-config tools in which I have set the modem up has configured those scare ppp files :)

I would also like to hear from Ubuntu users who have actually done what I am trying to do.

---

### Post by m4ng0 on 2005-01-19
As ilari said, "Modem Lights" works just fine. I use it without problems. First of all create a connection with
*sudo pppconfig*
and give a name to it. Then add users to dip group, and finally configure Modem Lights (by clicking with right mouse button) so that calls
*pon TheNameYouChoseForConnection*
to connect and
*poff*
to disconnect

---

### Post by haakon on 2005-01-19
Great, thanks. I will try that later today. (I hate this combination of not having touched a modem for ~5 years and being unable to try stuff until I get out to my fathers') :)

---

### Post by haakon on 2005-05-01
Ok, my father has been happily using Ubuntu since I started this thread. The modem lights applet has been perfect. Great stuff!

Now I've upgraded him to 5.04. In the new GNOME, the Modem Lights applet seems to be gone -- I cannot find it in the dialog to add stuff to the panel from. There's a different applet called Modem something, but that's really awkward to use, requires root access to dial up, and forgets options you enter into it so it doesn't actually work at all.

So my question: is Modem Lights gone from GNOME 2.10/Ubuntu 5.04? Or could there be a package I'm missing? (I installed ubuntu-desktop with all deps) Does anyone else have Modem Lights in the list of applets they can add?

Thanks for any help,
Haakon.

EDIT: Didn't realize this forum only applies to Ubuntu 4.10, sorry. Please direct any replies to the thread at [http://www.ubuntuforums.org/showthread.php?p=154700](http://www.ubuntuforums.org/showthread.php?p=154700) .

---

### Post by chettyk on 2005-05-02
Thanks everybody. This is information I too needed. I'd like to set up Ubuntu for my in-laws who have a dial-up connection. I think this ought to be made available as a HOWTO.

---

