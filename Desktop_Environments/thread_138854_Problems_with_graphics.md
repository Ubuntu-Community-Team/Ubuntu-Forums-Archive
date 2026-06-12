---
title: "Problems with graphics"
date: 2006-03-02
forum: Desktop Environments
---

### Post by josh34 on 2006-03-02
I used this [guide]("http://ubuntuforums.org/showthread.php?t=120091") to fully encrypt a server installation and then I installed the ubuntu desktop by using "apt-get install ubuntu-desktop." My problem is that when I boot normally, the computer asks for my encryption password, then I see all the items loading, then I hear the sound that usually tells you that the computer is ready for you to log in, but instead of seeing the log in screen, I see a black screen with a bar about 1 inch high going across the top of the screen. This bar is make of pink, green, and white vertical lines. If I move my mouse I can ocassionaly see a horizontal black stripe going through the bar. I can't do anything so I press the power button and when I do I get a text login, as if you were logging into a server install, then the computer turns off. How can I fix this? Is it a driver problem?

Thanks,
Josh

P.S. I have had plain desktop installs of Ubuntu on this computer before, and I have never had any problems. Also I can run the live cd just fine.

---

### Post by andrewsawyer on 2006-03-02
Have you tried to reconfigure your xorg.conf file?

If you type nano /etc/X11/xorg.conf then at the top there is a command shown that you can type to reconfigure the graphics.  I can't remember what it is off the top of my head I'm afraid, but I'd suggest tha tyou give that a try.

---

