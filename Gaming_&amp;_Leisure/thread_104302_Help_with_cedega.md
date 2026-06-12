---
title: "Help with cedega"
date: 2005-12-15
forum: Gaming &amp; Leisure
---

### Post by tanis143 on 2005-12-15
Ok, I just re-installed cedega after having to make a bunch of hardware changes, and now it wont go through the config. Right after the registration it just goes away. Same thing when I try to run it, it comes up with the screen to play or register, I hit play, and it goes away. Today is my first day to run Ubuntu and Cedega, so I'm very newbish.

---

### Post by joshuapurcell on 2005-12-15
When you say that Cedega 'goes away', do you mean that the window closes completely? If that's what is happening, then open a terminal and see if anything from the program is still left:> ps-ef | grep cedegaIf something shows up then remove it by typing the command **kill *#ofProcess***, and then try to run Cedega again. Replace #ofProcess with the process number you found with the ps command.

If opening the program continues to do the same thing as before once you are sure that is shutting down completely after every problem, then use the terminal window again and issue the command to start Cedega (which is **cedega**). Now you will be able to view some log information in the terminal while the program runs and maybe it will tell a little more about the problem you are having.

---

