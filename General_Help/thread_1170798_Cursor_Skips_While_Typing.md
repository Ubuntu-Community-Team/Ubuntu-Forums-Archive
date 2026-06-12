---
title: "Cursor Skips While Typing"
date: 2009-05-26
forum: General Help
---

### Post by Jimbo8927 on 2009-05-26
Hi,

I'm recently new to Ubuntu and have been having a problem--when I am typing (in firefox or MS Word (the latter through Crossover), the cursor has a tendency to skip--sometimes to previous text written (above) and sometimes to text written below (in the case of e-mails with the text chain below). Sometimes it also "clicks out," similar to when if click on a window outside of whatever program you are using (ex. word) then using the keyboard no longer sends a signal to that program (though it doesn't seem to send any signals/commands to any other programs...)

This problem is getting pretty annoying, and it doesn't seem to be related to my hardware--when I dual-boot in Windows I don't have this problem--it's only with Ubuntu.

Can anyone help me??

---

### Post by michy99 on 2009-05-26
Are you using a laptop with a touchpad? Often the touchpad will be too sensitive in Ubuntu, and you will bump it while typing without even realizing it. There is a program which lets you configure the touchpad called gsynaptics. You can install it thorough the Synaptic Package Manager or open a terminal and enter```
sudo apt-get install gsynaptic
```

---

### Post by Jimbo8927 on 2009-05-26
Yes, I am using a laptop with a touchpad, and it definitely is very sensitive in Ubuntu, so I think perhaps you're right, and I must be bumping it while typing.

I installed gsynaptics, but when I try to run "touchpad" (I assume that's the program I should run since I believe it wasn't present in the preferences menu before I installed gysnaptics, but please let me know if I'm mistaken) I get an error message:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I'm guessing this is an easy thing to do, but I have no idea to how to do it. Can you please help?

Thanks so much!

---

