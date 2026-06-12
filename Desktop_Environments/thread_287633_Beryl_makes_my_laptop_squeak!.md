---
title: "Beryl makes my laptop squeak!"
date: 2006-10-29
forum: Desktop Environments
---

### Post by noxxle on 2006-10-29
I followed the intructions to get beryl running on edgy and i noticed that grub shows two kernel options now. I have the General kernel which edgy originally installed, and after beryl a 386 kernel. Why did beryl install a 386 kernel? I have a pentium M dual core, i was assuming the general/common kernel utilized the 686 smp? Anyway, when i boot with the general kernel and i activate beryl my computer makes high pitched squeak sounds when i do things such as pull down menus. Its not coming from the harddrive, sounds like its from the processor..... any ideas?

---

### Post by phersotty on 2006-10-29
I think its your graphics processor.  I noticed the fan on my graphics card in my tower revved up when I started playing with Beryl.  It would probably be more noticable in a laptop since everything is crammed is such a small space.

---

### Post by noxxle on 2006-10-29
its a squeak though.. And its predictable. If i rapidly click on a window in the taskbar to minimize and maximize i can make the sound and it correlates with the window shrinking and enlarging.

---

### Post by thepizzaking on 2006-10-29
Did you install the nVidia beta drivers from the 3rd party repository?  When I did that it decided it wanted to install the 386 kernel and the 386 restricted modules instead of upgrading the generic restricted modules which was also available.
So I manually told my generic restricted modules to update, then I could remove the 386 kernel safely.

If you didn't follow that:
You should be able to (provided you still have the repository for the nVidia drvers activated) tell the system to upgrade the restricted modules for generic, then remove the 386 kernel without any problems.

Then again, if you didn't install the nVidia drivers from the repository I have no idea what's wrong.

P.S. I get that sound too on my laptop but only sometimes.

Hope this post was helpful.

---

### Post by noxxle on 2006-10-29
i did install the drivers from the 3rd party repo. However, i checked and my generic restricted drivers are already up to date. There is also an x86_64 generic restricted which has been installed. Thats odd because i am not on a 64 bit system...

---

### Post by phersotty on 2006-10-29
Squeaks ??  Are you sure its not coming from your speakers?  Could it be a sound effect?  I still think its your graphics card, but I'm not absolutely sure.

---

### Post by Paulus on 2006-10-29
Yeah, that your graphics card... I bet it does the same under glxgears.

Mine does the same and apparently theres nothing to stop it?!

---

### Post by noxxle on 2006-10-29
how are the nvidia drivers from the 3rd party repo different from the ones that were already in ubuntu's repos?

---

### Post by noxxle on 2006-10-29
I get the same squeak by changing the Font Rendering in Preferences>fonts. Its just a single squeak each time i change the settings, but its very annoying when using beryl because it occurs all the time.

---

