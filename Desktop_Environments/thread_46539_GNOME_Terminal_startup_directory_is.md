---
title: "GNOME Terminal startup directory is /  ?"
date: 2005-07-05
forum: Desktop Environments
---

### Post by papabean on 2005-07-05
I searched the forums and maybe I didn't use the proper terms, but Gnome Terminal starts in the / directory.  I've checked the configuration editor and checked through the profile, but I can't find where to change that.  How do I get the Gnome Terminal to start in my home directory?

---

### Post by frodon on 2005-07-05
If your terminal don't start in home directory by default, it's possible to specify a command to be executed on terminal startup (have a look in terminal options), specify "cd /home/your_user_name" to be executed on startup.
I'm not in front of my computer but i think it should work, if not i will test that at home.

---

### Post by papabean on 2005-07-06
Thanks for the advice, but that didn't do it.  The only option that was similar was "Use a custom command."  Using that to CD just caused the terminal to launch, cd to my home directory and immediately close.  I fixed that in the configuration editor and gnome-terminal is working again, but it still starts in / but there has to be a way to change it.

---

### Post by frodon on 2005-07-06
ok ... very strange
Have a look in the user window in System>Administration if you specify the good home directory, there is also here some options which could help you to start in home directory.
I supose you use bash terminal (default, in my case I use tcsh but it's globally the same thing), so in your home directory you have a .bashrc file which specify aliases and other things, you can add here some shell commands and after add in the terminal options the startup command "source .bashrc".
Don't worry your not alone  :wink:  I will search what i do to start in home directory this evening because I'm not at home.

---

### Post by papabean on 2005-07-06
I'm familiar with the .bashrc file, but aliasing probably won't work in this case.  And the gnome-terminal doesn't offer a preference for startup command (or I just can't find it).  I think what I may do is simply change the default terminal to something I'm more familiar with like Eterm or rxvt.

---

### Post by frodon on 2005-07-06
ok I've tested it. Just add "cd /home/your_user_name" at the end of your .bashrc file and it will work perfectly.
It's all you have to do.

---

### Post by papabean on 2005-07-06
Ok.  That's a bit of a hack, but it will definitely work.  Thanks for the tip.

I did change the default terminal to Eterm and got the same thing.  This is the first distro I've used where the default folder to start a terminal in is /.  However, I don't care if it's done in my .bashrc or elsewhere.  :grin:

---

