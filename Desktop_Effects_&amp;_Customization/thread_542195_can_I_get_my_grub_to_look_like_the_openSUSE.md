---
title: "can I get my grub to look like the openSUSE?"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by lunamystry on 2007-09-03
I recently had a rather unpleasant experience trying to install openSUSE. I am planning on trying again but the more i read the less i want to. 

I was wondering though, with openSUSE when I choose which operating system to boot into there is colour there. CAN I get that for my KUBUNTU? sort of like the opensuse type menu that i have. If i can get it how do i get it?

---

### Post by lsmobrian on 2007-09-03
[http://tldp.org/LDP/LG/current/jayanth.html](http://tldp.org/LDP/LG/current/jayanth.html)


think this is what youre wanting

---

### Post by lunamystry on 2007-09-04
ITS EXACTLY what I was looking for. I need a little help though. How do I copy the gzip file that I created to the grub folder?
with my incompetence someting will probably go wrong so also how do I back up the file thats already in the /boot/grub and if something does go wrong how do i recover it?

---

### Post by banewman on 2007-09-04
It is not that difficult if you have the admin password.
At the terminal type - sudo cp -v /path/to gzip.file /boot/grub/.
e.g.   sudo  cp  -v  /home/you/ splash.xpm.gz  /boot/grub/
Check your spelling and spacing and the whole thing should be fine. :)

---

### Post by lunamystry on 2007-09-04
```
lunamystry@alexis:~$ sudo cp -v/home/lunamystry/images/wallpapers/grub images/splash.xpm.gz /boot/grub
cp: invalid option -- /
Try `cp --help' for more information.
lunamystry@alexis:~$ sudo cp -v/home/lunamystry/images/wallpapers/grub images/splash.xpm.gz/boot/grub
cp: invalid option -- /
Try `cp --help' for more information.
lunamystry@alexis:~$ sudo cp -v'/home/lunamystry/images/wallpapers/grub images/splash.xpm.gz/boot/grub/'
cp: invalid option -- /
Try `cp --help' for more information.
lunamystry@alexis:~$

```

Did not work.

I got it right. I played around with the spacing in the code i am not sure which one I changed but i think it worked. 

THANK YOU

---

### Post by lunamystry on 2007-09-04
I messed up! i can't boot into Feisty now. I don't know what went wrong. When I try to boot feisty my  PC turns off. What could that mean?

---

### Post by jhernandez1270 on 2007-09-04
Because you have a space in one of your folder names (grub images) you need to surround it with quotes.  Try it like this:

sudo cp -v "/home/lunamystry/images/wallpapers/grub images/splash.xpm.gz" /boot/grub

---

### Post by lunamystry on 2007-09-04
I did that and I thought it worked but i guess it did not. because now i can login to my feisty without the PC just switcing off, but I there is no picture there. Its still black and white.

---

### Post by lunamystry on 2007-09-04
I found the problem. It is the picture that i am trying to use for my boot picture. When i log into my Gutsy hard drive and the cut and paste the picture on the desktop then reboot into my feisty hard drive it works. I don't know why but there is something wrong with the picture i made. Maybe the pixels or something. I am going to try a new picture and see if it works.

---

### Post by ayoli on 2007-09-04
what about giving a try to this:
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)
this how to makes my grub really sexier :)

---

### Post by lunamystry on 2007-09-04
I am growing to hate the terminal now. I tried the guide and i think its what I want but I think I am missing a few things needed to finish it. 

> Then edit your menu.lst

Code:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
and make it use gfxboot
Code:
gfxmenu /boot/grub/message.suse # the suse can be replaced

That part of the guide does not work on my PC. :(

---

### Post by ayoli on 2007-09-04
be more precise, please.
Did you install the package provided in the thread and fellow the steps to hav your new grub with gfx enabled (i mean part with grub commands) ?
Then did you copy a graphical message file provided in the thread in your /boot/grub dir ?
then what the prob with editing your /boot/grub/menu.lst file ?
You also may post your prob in the thread where I point you.

---

### Post by lunamystry on 2007-09-04
> **ayoli said:**
> be more precise, please.
Did you install the package provided in the thread and fellow the steps to hav your new grub with gfx enabled (i mean part with grub commands) ?
Then did you copy a graphical message file provided in the thread in your /boot/grub dir ?
then what the prob with editing your /boot/grub/menu.lst file ?
You also may post your prob in the thread where I point you.

I installed the package fine, and copied the message.suse to grub fine. 
I did all that was in the thread up to the above commands. I don't know what to edit in the menu.lst if I edit something and ithink i should use kate rather than gedit but I am not sure if it will work and I can't make it use gfxboot

---

### Post by ayoli on 2007-09-04
> **lunamystry said:**
> I installed the package fine, and copied the message.suse to grub fine. 
I did all that was in the thread up to the above commands. I don't know what to edit in the menu.lst if I edit something and ithink i should use kate rather than gedit but I am not sure if it will work and I can't make it use gfxboot

you can use kate to edit this file, hit ALT+F2 then type :
```
kdesu kate /boot/grub/menu.lst
```
then add this line at the almost top of the file:
```
gfxmenu /boot/grub/message.suse
```
replace "message.suse" with your graphical mmessage file name.
then save, that should be ok if you have fellow the previous steps.

---

### Post by lunamystry on 2007-09-04
I am going to reboot now, If anything goes wrong i am going to sleep and fix it tomorrow probably. 

I did what you said and added the line the first line of the file then left a line. 
Thank you for your time.

---

### Post by banewman on 2007-09-08
And how is grub looking? I have been following from a distance and am curious. 8)

---

### Post by lunamystry on 2007-09-08
grub still looks the same. I think that it is because I was trying to cahnge the wrong Grub. I have two ubuntu unstallaltion (gutsy and feisty). The last time i ended up with my PC not booting and i couldn't even run a live disc. That was because of my stupidity though not the instructions here. After the instructions here did not wotk I tried to some other things not undoing whatever I had done before. I changed my boot manager to LILO and then It just would not boot anymore. I am kinda afraid to try now because I have someting downloading and it may take two more days so I will probabaly try again in two to three days.

---

