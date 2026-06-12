---
title: "problems"
date: 2006-06-11
forum: Desktop Environments
---

### Post by 2pacalypse on 2006-06-11
A couple of days ago I've finally installed Ubuntu Dapper Drake after I've been having problems installing it, and now i got it installed+fully updated and i must admit its a very very good OS, but i do have a little issues here and there, little annoying problems that on their own arnt really bad, but since theres a bunch of em its kinda annoying

1-OpenGL, everytime i run a game that run on OpenGL he doesnt work properly and say that my OpenGL is misconfigured, broken or not installed, but i already installed the graphical drivers (nvidia-glx) so what does he want from me?

2-All the 3D games i run (currently i only have Wine games) are running extremely slow but my computer is 2 times stronger then the recommended recuirments

3-My Azureus is kinda buggy for startes when ever i run it, it seems that all the GUI gets stuck, i can open new tabs and stuff like that but it wont close afterwards, same thing happends with the notifications. and even after I close the program, they still appear.the 2nd prob with it is that sometimes, the program disappears, no crash message no nothing just vanishe's and the 3rd prob is that no matter what the program does not appear in the toolbar so i must always keep it on my taskbar(which is kinda uncomfortable)

4-Whenever i restart or shutdown. the computer wont do it he simply kicks me into a dos like screen and asking for username, but i cant type it since the keyboard is disabled

5-whenever my screensavers kicks me, i cant get out of it. if i move the mouse he either freezes and forces me to push the restart button or he goes back to the greeter and says that the greeter program crashed, trying a new greeter

6-I cant compile programs, he says something about a problem of no c compiler was found (although i did installed the gcc program from synaptic)

7-I cant play movie's although i got all the codecs needed already installed, when ever i run a movie on a program (i've tried on Kaffeine,Xine player, Mplayer,Movie Player and KMPlayer) and its always either crashs, feezes or showing a black screen witho the movie's audio, but no video (kinda takes out the fun from watching movies on the computer)
p.s.
i also got 2 question

1-how do i log in as root?

2-how do i install RPM files? i got Kpackage already but it seems to be faulty (does accept the root's password although its the realy password)

Thanks in advance

---

### Post by elbryan on 2006-06-11
try to do:
- sudo passwd
and specify your root password. (sudo means: SuperUser Do).

To install rpm file simply do rpm -iv package_name.rpm.

Obviously you will have to have installed rpm package. (sudo apt-get install rpm).

^^

---

### Post by 2pacalypse on 2006-06-11
10x ;)
but do you have any suggestions about my primary problems?

---

### Post by mumushi on 2006-06-11
[QUOTE=2pacalypse]10x ;)
but do you have any suggestions about my primary problems?[/QUOTE]

what is the brand of your video card? let's start from there.

---

### Post by mumushi on 2006-06-11
Im sorry. Your graphics gard is nvidia. try doing this: 

```
sudo apt-get install nvidia-kernel-common nvidia-glx
```

i hope it helps.

---

### Post by 2pacalypse on 2006-06-12
nope, didnt worked. still get the OpenGL probs

---

### Post by mumushi on 2006-06-12
[QUOTE=2pacalypse]nope, didnt worked. still get the OpenGL probs[/QUOTE]

ok go to [http://www.nvidia.com/content/drivers/drivers.asp]("http://www.nvidia.com/content/drivers/drivers.asp") 

i hope that link would help you. basically your problem is with your graphics card driver.

---

### Post by 2pacalypse on 2006-06-12
ok, but it cant be that all the problems are from the video driver, any suggestions about the 3-7 probs? and also, i dont know how to install the drivers all that well, i understand that i need to boot with run level 3(b4 X server starts) but i dont know how, when i run it with alt+ctrl+F1 he still claims in inside X Server

---

### Post by 2pacalypse on 2006-06-13
a friend came over and helped me out with the graphics prob ;), and it also magicly fixed the video problem. but still 10x for the help mumushi ^^ now i only need solution to probs 3-6

---

### Post by 2pacalypse on 2006-06-14
can any1 please help me with these probs? the 3-6 probs in the first post & also these two

1- My firefox keeps crashing back to the desktop from reasons unknown, he just crashs without any message

2-Whenever im running a themed login, at the login screen he claims that the greeter is crashing, trying another one and then he goes to the plain greeter, but when i configured it as the plain he gives me the same message again and he uses the themed greeter. this happends all the time when i use the greeter, i cant login without getting this message

---

### Post by 2pacalypse on 2006-06-19
can any1 please help me with these problems?

p.s.
the video prob is back from some strange reason and my friends method isnt working anymore

---

### Post by Haegin on 2006-06-21
For the problems compiling try installing build-essential

Good luck with the other problems. It seems lots of people are battling with dapper. (and I thought it was an enterprise release that was supported for three years)

---

