---
title: "Cairo Dock annoyance"
date: 2009-08-01
forum: Desktop Environments
---

### Post by vainhero on 2009-08-01
Hello everyone. This is my first post so bear with me 
 I have a peculiar problem with cairo-dock in xubuntu. . . Whenever I click on a launcher for Matlab, Mathematica, Firestarter, Terminal Services, Spark or a cxoffice program, the program's window does not dock on the designated launcher on the dock. 

 With firefox, when I open a window, it minimizes to my firefox launcher on the dock. I now click on firefox in the dock, and it does not open a new instance, it opens the currently running session. This is what is supposed to happen.  

However, with all these programs above, they minimize to a new section of the dock as if they did not have a launcher and they take on a new icon. Clicking on the launcher opens a new instance! NO!!

  Somebody told me to try -nosplash on these programs, but alas, no luck. These programs simply bypass the splash screen but then create a new space on the dock, instead of docking at their launcher!!! 

 i just want these programs to minimize to their launchers  

 Anybody here know a thing about cairo-dock? I don't know french and couldnt navigate the cairodock homepage :(  thanks ubuntu community!

---

### Post by vitz3 on 2009-08-01
What you need to do is specify the window class in the launcher. So for example, if you want terminal windows to minimize to your terminal launcher, enter the window class in the class field under (advanced?) options of the launcher which would be gnome-terminal. After that the windows should minimize to the launcher and not dock on the right side of the dock.

Combined with compiz and the genie effect mod your should be rockin'

edit**
Oops, I didn't notice that you're using xubuntu. In that case it's outta my field. Might be similar tho. Good luck. =)

---

### Post by vainhero on 2009-08-01
ok... 
i your advice worked really well! most of my programs now minimize correctly. Also, if you check 'prevent from stealing appli' on the launcher, it negates the minimizing
Your class suggestion led me to this post :: [http://ubuntuforums.org/showthread.php?p=6330590](http://ubuntuforums.org/showthread.php?p=6330590) 
Here i found the command ...
```
xprop|grep WM_CLASS|cut -d\" -f4
```... which finds the class of the selected window.


however, not all my problems were solved quite so easily. It turns out that Mathematica 7 does not have a class!! It is merely an empty string! How can I group by class if it doesnt have a class?


Secondly, I have launchers for crossover office to launch Microsoft Word and Microsoft Excel. Both these have the same class: "Wine". As you might guess, this causes tons of problems. When I launch Word, Excel goes and thinks that I just opened it!


problems problems problems... thanks for the advice so far, has anyone else encountered a similar situation?

---

### Post by fabounet on 2009-08-03
one solution : tell the devs that they should respect the X standards (seriously)

---

### Post by vainhero on 2009-08-06
</sarcasm>

Im not asking for them to change or conform. i just want to know how to link the two programs. And it must be possible

sigh...

---

