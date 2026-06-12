---
title: "Couple of problems"
date: 2009-05-14
forum: General Help
---

### Post by Souljah on 2009-05-14
Hi,

I have a couple of problems since upgrading to v9.04 Jaunty.

1. I have some sound issues. Specifically speaking, on skype. When launching Skype, I'm unable to hear anything. If I go into the Skype options menu and choose Sound Devices, I see that my sound card is listed on all 3 sub categories, which is SOUND IN, SOUND OUT, and RINGING. The sound card name is **HDA NVidia (plughw:Nvidia:,0)**. There's 3 other options on there too. I have tried all 3. When I click on Make a Test Call, Skype tells me "There's a problem with audio playback". However, if I choose, "Make a test sound" and then quickly choose "Make a Test Call" it works, except for the Mic portion which the echo test service doesn't record. I'm baffled as to what the problem might be. I tried the default sound recording option in Ubuntu and that works fine, records my voice and plays it back fine. 

2. I have enabled automatic login for my session. There is only 1 user, me. The other 2 users in the household are my parents and I'm cool with them accessing Ubuntu. Thing is, with automatic login enabled, the wireless prompt comes on to ask me for the password, which is the keyring, before it connects to the wireless router. How can I have that password saved and do that also automatically?

I also had a bluetooth problem but I think I solved that by the dongle I'm using. The dongle might be faulty. Peace and God bless.

Ryan

---

### Post by mb_webguy on 2009-05-14
Can't help you on the first problem, but as for the second...

[LIST=1]
[*]Open up your Home Folder by clicking Places>Home Folder
[*]Press CTRL-H (or click View > Show Hidden Files)
[*]Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it
[*]In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.
[*]Delete any files you find within the keyrings folder
[*]Logout or restart the computer
[/LIST]

When you log back in, you'll be asked for your network password.  Once you enter it, the keyring manager will open asking you to enter a new keyring password. Leave both boxes blank, and click OK (or Create, or whatever the positive answer is).  After that, you won't be prompted for you password.

---

### Post by Souljah on 2009-05-17
> **mb_webguy said:**
> Can't help you on the first problem, but as for the second...

[LIST=1]
[*]Open up your Home Folder by clicking Places>Home Folder
[*]Press CTRL-H (or click View > Show Hidden Files)
[*]Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it
[*]In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.
[*]Delete any files you find within the keyrings folder
[*]Logout or restart the computer
[/LIST]

When you log back in, you'll be asked for your network password.  Once you enter it, the keyring manager will open asking you to enter a new keyring password. Leave both boxes blank, and click OK (or Create, or whatever the positive answer is).  After that, you won't be prompted for you password.

The solution you gave didn't quite resolve it, however, I had to go into the wireless connection options and make it available to all users, after that it seems to doesn't want to ask for a keyring anymore which is a good thing. As for the first problem with Skype, I resolved it by selecting Pulse audio. The topic can now be closed.

---

