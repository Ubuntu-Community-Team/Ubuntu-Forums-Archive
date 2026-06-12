---
title: "Sidebar and Theme Installation Help in Gnome"
date: 2007-09-20
forum: Desktop Environments
---

### Post by tropcky on 2007-09-20
hi i really wanna know how u guys make thes side bar with all cpu and memory hard desk network all system information 
plez tell me how 
 and by the way i trayed to instal the theme i dont know way i instaled so meny tar.gaz themes i dont know y that one dont wanna instal  thank u

---

### Post by aysiu on 2007-09-20
Let's say the *Thinblack.tar.gz * file is on your desktop.

Paste these commands in the terminal: ```
cd ~/Desktop
tar -xvzf Thinblack.tar.gz
mkdir ~/.icewm
mkdir ~/.icewm/themes
mv ThinBlack4 ~/.icewm/themes/
``` The first command changes directories to your desktop directory. The *D* must be capitalized. In any case, don't retype the commands--just copy and paste them in.

The second command unzips the zipped archive.

The third and fourth commands make sure you have the proper directory structure in place for themes. If you get an error message saying the directory already exists, just keep going with the next command.

The fifth command moves the unzipped folder into your themes folder.

ThinBlack should now be available for use under **Settings** then **Themes**.

---

### Post by tropcky on 2007-09-20
ferst thank u fro helping me 
2th it didnt work i did what u told me but i still cant faind it 
help plez thanks 
( and dont forget the info side dock thing i just told u about ) 
thank u

---

### Post by tropcky on 2007-09-20
hellooooooooooooooooooo

---

### Post by aysiu on 2007-09-20
If you want help, you have to put in at *least* as much effort as I put in helping you.

"But I still can't find it" doesn't help me help you. What error messages did you get, if any? Did it extract the zip files? Did it move to the folder? What happened? I'm not a mind reader, and I can't see your computer screen.

Also, "hellooooooooooooooooooo" after one hour of waiting on an online forum isn't polite. You should wait at least twenty-four hours before bumping a thread.

---

### Post by tropcky on 2007-09-20
oky i got thes msg 

tropcky@tropcky-linux:~/Desktop$ mkdir ~/.icewm
mkdir: cannot create directory `/home/tropcky/.icewm': File exists
tropcky@tropcky-linux:~/Desktop$ mkdir ~/.icewm/themes
mkdir: cannot create directory `/home/tropcky/.icewm/themes': File exists
tropcky@tropcky-linux:~/Desktop$ mv ThinBlack4 ~/.icewm/themes/

---

### Post by aysiu on 2007-09-20
> **tropcky said:**
> oky i got thes msg 

tropcky@tropcky-linux:~/Desktop$ mkdir ~/.icewm
mkdir: cannot create directory `/home/tropcky/.icewm': File exists
tropcky@tropcky-linux:~/Desktop$ mkdir ~/.icewm/themes
mkdir: cannot create directory `/home/tropcky/.icewm/themes': File exists
tropcky@tropcky-linux:~/Desktop$ mv ThinBlack4 ~/.icewm/themes/
So what happened after that last command? No error messages?

And can you post the output of these commands as well? ```
cd ~/.icewm/themes
ls
```

---

### Post by tropcky on 2007-09-20
no i dont see ant err msg   
and the post is 
ThinBlack4

---

### Post by aysiu on 2007-09-20
Well, it's installed. So when you go to the IceWM menu and click on Settings and Themes, it doesn't appear in that menu?

---

### Post by tropcky on 2007-09-20
IceWM ??????????
 i dont have menus like u  i open themes from system-prefrences-theme   
 and i cant faind it ther

---

### Post by aysiu on 2007-09-20
> **tropcky said:**
> IceWM ??????????
 i dont have menus like u  i open themes from system-prefrences-theme   
 and i cant faind it ther
Ah, that's the problem!

You're not using IceWM. You're using Gnome.

The themes for Gnome you get off [http://www.gnome-look.org](http://www.gnome-look.org)

They're either GTK themes or Metacity themes. Download them. Drag and drop the .tar.gz file to the theme manager window and that's it.

---

### Post by tropcky on 2007-09-20
will now i need help for sue i installed the lcewm and it make my desktop kde and i really cant use so what ?

---

### Post by tropcky on 2007-09-20
oky thank u so much for helping me all that time 

but i need anther thing  its the side dock that its all information about system like the one in the theme photo

---

### Post by aysiu on 2007-09-20
Since this isn't really about installing the ThinBlack theme in IceWM, I've moved your posts to their own thread with a new title and in the proper subforum.

I don't know what you mean about installing IceWM and getting KDE. The two are completely separate from one another. Can you show an example of what the side dock is?

---

### Post by tropcky on 2007-09-20
oky ferst of  cuz i am soooo new to linux  
when i installed the icewm  and loged into its seson  i faound my self into some thing like kde  all my shurtcuts is gone the top panal is gone  so i hade to change the seson to gnome onc agen      plez try to under stant  i know my english is so much even more the word ( sucks ) and i am really sorry about it 




 
the said bar i asked u about u gonna faind in here its in the right side of the pic

---

### Post by aysiu on 2007-09-20
That's not KDE. That's definitely IceWM, and it looks as if you're using ThinBlack. Congratulations! So what's the issue?

---

### Post by tropcky on 2007-09-20
maaaaaaaaaaan u got me all rong thes pic its not for my desk top its from the web 
and i really cant even make a print screen from my icewm desk top its really a poooooor kde 

i cant make it gnome  
so thats way i still using the real gnome antel now 

so if i gonna install icewm tell what 2 do from all over the beging antel it becoms just like thes pic 
thank u for helping

---

### Post by tropcky on 2007-09-20
oky i am in icewm right now if u can tell me how how to print screen u know take a screen shot so i will be able 2 show u the the problem i am in   tell hoe to make in trimenal

---

### Post by aysiu on 2007-09-20
> **tropcky said:**
> oky i am in icewm right now if u can tell me how how to print screen u know take a screen shot so i will be able 2 show u the the problem i am in   tell hoe to make in trimenal
Well, since you also have Gnome installed, this should work:

To take a screenshot, press the Windows key and the Space Bar together. Your cursor should appear in the taskbar. Type ```
gnome-screenshot
```

---

### Post by tropcky on 2007-09-20
will it works and i save in the desktop   but ther is no desk top so i cant see it

---

### Post by aysiu on 2007-09-20
> **tropcky said:**
> will it works and i save in the desktop   but ther is no desk top so i cant see it
You don't need to see it right now.

Whatever browser you're using will see it in the image upload dialogue.

---

### Post by tropcky on 2007-09-20
okyu here its is and as u see ther is  no shortcuts ther is nothin

---

### Post by aysiu on 2007-09-20
That looks about right. You're using ThinBlack. The thing is--window managers (IceWM, Fluxbox, WindowMaker, SawFish, Enlightenment) tend to come pretty barebones, and you have to figure out wallpaper, icons, etc. step by step, unlike desktop environments (KDE, Gnome, Xfce) that come with all the bells and whistles working "out of the box."

If you want to customize IceWM, check out the first four of five pages of [this thread](http://ubuntuforums.org/showthread.php?t=263710).

---

### Post by tropcky on 2007-09-20
oky man thank u so mucj for helping and i hop if u can help with that side bar if i gonna not use the icewm 
i will use gnome normal gnome so how can i have thes side bar 

thank u so  much for helping

---

### Post by tropcky on 2007-09-20
man i am sorry  that i am asking 2 much

---

