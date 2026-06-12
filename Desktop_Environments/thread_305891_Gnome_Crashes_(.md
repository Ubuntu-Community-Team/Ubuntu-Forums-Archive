---
title: "Gnome Crashes :("
date: 2006-11-24
forum: Desktop Environments
---

### Post by dutch_boi1 on 2006-11-24
hey i read the sticky about how to install beryl with the latest nvidia drivers etc. i Dont need to install the latest nvidia drivers so i skipped that bit.. i installed Beryl fine.. then tried launching beryl-manager in the terminal.. and X crashed, so i ctrl+alt+backspace'd my way out to login and tried loging in. i could login and i further read i had to add beryl-manager to my startup programs in the sessions menu thing.

Now that was a bad idea because whenever i try logging in my normal user it starts loading Gnome (panels etc), and then the panels just dissapear and im left with nothing.

How do i fix this? i can login root etc so i hopefully can fix it. and also doing a failsafe login doesnt do anything.

Please help

(ps. is beryl just compiz with another name and extension? if so cant i just use compiz? also do i need to have XGL installed cause i dont want my screen as a cube i just want the pretty effects :)

---

### Post by Bruegger on 2006-11-24
Not sure what guide you have referred to install beryl.
It is always a good practice to install the latest graphic drivers before you proceed with installing beryl.
Have you amended your xorg.conf and your gdm-custom files???
Use any editor to view those files and compare with the ones provided in the installation guide you followed.

Simply put,Beryl is a fork of compiz with more effects than compiz and needs XGL for rendering the effects.
There are numerous guides in the forum and wiki on this.

---

### Post by dutch_boi1 on 2006-11-24
welll.... the guide i followed was a sticky and posted by an admin i think. alot of people got it working, this is the url:
[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl)

basicly what i need to do is remove the startup of the beryl-manager from my sessions window in my usual user account.

Is there a file i can edit from my root directory which can fix this?

err also i didnt need to ammend any files as they were the same as from the guide.

---

### Post by Bruegger on 2006-11-24
The xorg.conf needs to be amended to enable the effects.
I am not sure how to remove the beryl-manager from sessions start-up in root...looking for it.

In the meantime...in ur root login..do
sudo nano /etc/X11/xorg.conf

and see if your device and screen sections are amended and reflect the commands mentioned in the guide u followed.
If not..input them..save the file and reboot.

---

### Post by tomcheng76 on 2006-11-24
press ctrl + alt +f1 to enter console
cd ~/.config/autostart
rm beryl-manager.desktop

---

### Post by frodon on 2006-11-24
Only the latest nvidia drivers (9629 or higher) allow to run beryl except if you ant to install Xgl or Aiglx.

As for beryl it is the community version of compiz.

If you don't install them beryl won't work.

---

### Post by dutch_boi1 on 2006-11-24
omg thank you so much tomcheng76, it boots now :D. hmm how would i go about installing the latest drivers? ive tried before but i didnt know what i was doing :(.

Thanks again tomcheng76

---

### Post by frodon on 2006-11-24
Don't worry it's quite easy because some users made a repository, all is explained in the guide :
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

---

### Post by dutch_boi1 on 2006-11-24
i really love the ubuntu community :) im installing the drivers for my nvidia 7950GT from the repo's in the url u gave me :).

Thanks for the help ill get back to you tommorrow as to how this went ;) :).

---

