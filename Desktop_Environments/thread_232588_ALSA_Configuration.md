---
title: "ALSA Configuration"
date: 2006-08-08
forum: Desktop Environments
---

### Post by PCalitrack on 2006-08-08
I am trying to configure my SB Live External 24 Bit sound card. It is currently giving me sound when I play Rythmbox and is the default when I boot up my computer. However, since I am on a laptop, there is another onboard sound card. Anyways, by the default setup Ubuntu gave me on install, my external sound card only has volume options when I click on the sound icon. So I go to the ALSA webpage...

I am referring from [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106")

On there it lists the driver for this sound card as snd-ca0106

However, when I search for that specific file... I get:
snd-ca0106.ko

What is the difference between snd-ca0106 and snd-ca0106.ko?

I just want more options from my soundcard other than the volume... and I figure following that website would help, but why is my driver named a little different?

---

### Post by 5-HT on 2006-08-09
Don't worry about the extension in the filename, that is the module. Modules for 2.6 tend to go as *foo.*ko
You can load it using *modprobe *or, to have it loaded on boot, add it to /etc/modules.

Once the module is loaded, running *alsamixer* should hopefully provide you with more options.

---

### Post by PCalitrack on 2006-08-09
Hmm... thanks for the info. I tried what you said, but it didn't seem to give me any more options in alsamixer. Guess there might be some more to it.

Just for reference though, modprobe only initials the module for the current session? If I rebooted, I would have to do it over again?

Also, what is the equivalent of the modules.conf file for Ubuntu?

---

### Post by 5-HT on 2006-08-10
[quote=PCalitrack]Hmm... thanks for the info. I tried what you said, but it didn't seem to give me any more options in alsamixer. Guess there might be some more to it. [/quote]

If you're running GNOME, do you see more options for sound control after loading the module and switching the device in Applications -> Sound & Video -> Volume Control (under File)?
[quote=PCalitrack]
Just for reference though, modprobe only initials the module for the current session? If I rebooted, I would have to do it over again? [/quote] Yup. To have the module loaded on boot, you can add it to /etc/modules.

In Ubuntu, modules.conf has been split up a bit into /etc/modules, files in /etc/modprobe.d, and /etc/modutils.

---

### Post by PCalitrack on 2006-08-10
> 
If you're running GNOME, do you see more options for sound control after loading the module and switching the device in Applications -> Sound & Video -> Volume Control (under File)?

I don't seem to have that Volume Control in my Gnome. Under my Sound & Video I just have music and movie players. alsamixer definately doesn't give me and more options after I run:
modprob snd-ca0106

---

### Post by 5-HT on 2006-08-10
Ah, sorry. The volume control isn't available from the menu by default.
You can add it via Alacarte Menu Editor (Applications -> Accessories) or run it by entering the following in a terminal:
```
 gnome-volume-control 
``` 
I don't have that card myself...is anyone else using that card and managed to get it working?

---

### Post by PCalitrack on 2006-08-10
It gave me the same options as alsamixer, which was just the volume out. Anyways, I guess I should just take it as it is since I am getting sound out of my speakers. Thanks.

---

