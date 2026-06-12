---
title: "sudo sudo  no take password"
date: 2006-01-10
forum: Forum Feedback &amp; Help
---

### Post by bullfrog on 2006-01-10
what do you do when sudo apt-get[anything] wont take password? have reloaded with ubuntu disk same thing. have used gksudo nautilus it take password but then sudo apt-get cant find command. what am i doing wrong? i mean like[sudo apt-get update. i have been all over the forums havent seen a problem like this.  sudo worked fine fora preet good while.loaded 5 different hard drives then it just quit. have used 2 different disk.     anyone know?     thanks for your time     bullfrog:confused: :confused: :confused:

---

### Post by gruepig on 2006-01-11
What do you mean it won't take your password?  Does 'sudo apt-get update' prompt you for a password and then give an error message?  If so, what?  Or does it not prompt?  What do you get if you run 'which sudo'?

---

### Post by Thirsteh on 2006-01-11
Boy that was a good read :)

It seems like you're having some problems with the latest version of sudo as well. Are you sure you're not adding an ampersand at the end of the command? If you did that, you would not be able to enter your password as you sent the process to the background (ampersand=&).

---

