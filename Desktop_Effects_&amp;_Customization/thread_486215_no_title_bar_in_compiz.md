---
title: "no title bar in compiz"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by mohtasham1983 on 2007-06-27
Hi guys,
After upgrading compiz I couldn't run it anymore, therefore I uninstalled it and reinstalled it with beryl. 

I followed the installation instruction for beryl, in its website and installed beryl successfully, but I did like beryl as much as I did compiz. Beryl has much more feature but not as stable and fast as compiz. 

When I choose compiz as the windows manager from beryl-manager menu, compiz run and works fine, but there is no title bar and desktop cube. 

By the way, I have an intel graphic card.

Any idea how to bring back the title bar in compiz?

---

### Post by ronocdh on 2007-06-29
First, do you have 915resolution installed? I think it's necessary for most Intel graphics chipsets. Beyond that, I know that with Beryl the user can declare separate windowing managers and decorators. A common problem with Beryl is a disappearance of the title bar, and I know this can easily be circumvented if the user just declares good ol' MetaCity as the manager/decorator (I forget which, sorry). This means that Emerald themes cannot be used, but at least the user can see the title bar!

---

### Post by mohtasham1983 on 2007-07-02
I dont know if 915 resolution is installed. How can I check it? I have tried to switch decorator and windows manager in different combinations, but no title bar in compiz. I have title bar in beryl though

---

### Post by izizzle on 2007-07-02
You can install 915resolution through synaptic. Just search for it in synaptic.

Now, for the title bar problem. Open up the xorg conf file by typing > gksudo gedit /etc/X11/xorg.conf. Now find the section that says SCREEN. Add a line right before the EndSection line that reads like this: > Option "AddARGBGLXVisuals" "true". Now save the file and restart X by pressing cntrl-alt-backspace.

tell me if this works //izizzle

---

### Post by mohtasham1983 on 2007-07-02
Thanks for reply. But I don't have title bar yet :(

---

### Post by izizzle on 2007-07-02
Did you add any other lines besides the one I told you you to add? 

BTW: I live in Oakland(close to u ;D)

---

### Post by mohtasham1983 on 2007-07-03
No, I didn't make any other changes.

---

### Post by izizzle on 2007-07-03
Thats weird....it worked for me.....Did you restart X?
Try uninstalling beryl....

---

### Post by mohtasham1983 on 2007-07-03
Actually I have uninstalled beryl and compiz several times without withouth any sucess. My problem is probably with xorg.cong content, but I don't know what each option means.

I have changed the original file without making a backup at first.

---

### Post by izizzle on 2007-07-03
remember to **ALWAYS** make a backup before messing with the xorg.conf file. Anyways, what graphic card do you have? Did you install the drivers for it?

---

### Post by mohtasham1983 on 2007-07-08
I have intel graphic card which doesn't require manual driver installation.

---

### Post by izizzle on 2007-07-08
Which card is it? Check the restricted drivers section to find out if the card's drivers are enabled or disabled.

---

### Post by mohtasham1983 on 2007-07-11
It doesn't require any restricted driver indeed.

---

### Post by mohtasham1983 on 2007-07-11
I uninstalled and installed it more than 10 times with different repositories. Finally I got it working using eye candy repository, but cube is gone. Currently working on it to have it back. I really miss it :)

---

### Post by izizzle on 2007-07-15
Happy to hear that you finally got it working............ Sorry, but I can't help you with the cube problem.....
good luck though!

---

### Post by namdung on 2008-05-22
After installing ccms, my title bar disappeared when fiddling with the settings. After much trying out I got it back again. In the CompizConfig Seetings, select Effects -> Window Decoration.

---

