---
title: "Desktop won't start (Tried KDE and gnome)"
date: 2007-05-31
forum: Desktop Environments
---

### Post by mrfredman on 2007-05-31
So ubuntu has been working just fine for months now. But all of a sudden I restarted it and it stopped working. When I try to login at the first screen it takes my name and password, then the screen goes black for a few seconds, and the mouse shows that its thinking, then it goes back to the login screen. Nothing works, it just always comes back to the login screen. Any ideas?

---

### Post by chacotaco on 2007-06-01
i know its simple, but have you tried a ctrl+alt+F7? I am having an issue where when I boot it all loads fine, you hear the first set of drum beats then it dumps me to a command line. I hit those keys and then I see the graphical login. I login and all is well...:confused: hope it helps

---

### Post by mrfredman on 2007-06-01
Nope that doesn't work. I think its deeper than that, but thanks for the suggestion.

---

### Post by phidia on 2007-06-01
Can you start a CLI (Alt+Ctrl+F1) and try to login from there? If you can login from _C_ommand _L_ine _I_nterface try the "startx" command and search or post the errors you get.

---

### Post by mrfredman on 2007-06-01
> **phidia said:**
> Can you start a CLI (Alt+Ctrl+F1) and try to login from there? If you can login from _C_ommand _L_ine _I_nterface try the "startx" command and search or post the errors you get.

awesome, thanks. I diagnosed my problem, and it was one I was having earlier. My hard drive is totally full and it doen't have room to make tmp files. I know I have 7gb of junk in my trash but I don't know how to delete it which leaves me with two questions, mthe answers of which should get me on my feet.

1) how do i find my trash can through the command line
and 
2) how do i empty it.

---

### Post by ThomasNL on 2007-06-01
the trash bin is in ~/.Trash

---

### Post by kushin77 on 2007-06-04
I had the same problem. this means that you dont have any space on your home directory. run the df command. confirm where your home directory is. look and you will see 100% of your drive is full. either delete or move your data somewhere else and run the startx 0 command. your /tmp/.X0-lock file needs to be removed then startx 0.

---

### Post by loathsome on 2007-06-04
> **mrfredman said:**
> awesome, thanks. I diagnosed my problem, and it was one I was having earlier. My hard drive is totally full and it doen't have room to make tmp files. I know I have 7gb of junk in my trash but I don't know how to delete it which leaves me with two questions, mthe answers of which should get me on my feet.

1) how do i find my trash can through the command line
and 
2) how do i empty it.

Clean your trash by running **[COLOR="DarkSlateGray"]$ sudo rm -R ~/.Trash[/COLOR]**

---

