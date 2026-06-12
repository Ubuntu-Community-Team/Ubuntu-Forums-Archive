---
title: "Screen Resolution problems....."
date: 2005-06-16
forum: Desktop Environments
---

### Post by astronerd on 2005-06-16
Hi all, I installed the binary drivers for the ATI Raedon X300 video card last night and when I rebooted today it changed the screen resolution to really big.  Well I read on how to fix that, you have to edit the /etc/X11/xorg.conf file and change the display settings.  Well I did that and it went to a resolution that I couldnt even read things.  So being the idiot that I am, I tried to edit the file back to a more useable resolution, but messed something up.  So now I cant even boot into X, it just gives me the command line.  I dont know much about linux or commands so I dont know how I can change/edit the file from there so that I can get a resolution to work and let me back in with X working.  (Does this make sense?)  Basically I need to figure out how to edit a file without using gedit or something like that.  And I need to be able to save etc so that X will run again.  Please remember that I am a fool, so make the directions as easy as possible.....  Thanks in advance! 
Charles

---

### Post by astronerd on 2005-06-16
[QUOTE=astronerd]Hi all, I installed the binary drivers for the ATI Raedon X300 video card last night and when I rebooted today it changed the screen resolution to really big.  Well I read on how to fix that, you have to edit the /etc/X11/xorg.conf file and change the display settings.  Well I did that and it went to a resolution that I couldnt even read things.  So being the idiot that I am, I tried to edit the file back to a more useable resolution, but messed something up.  So now I cant even boot into X, it just gives me the command line.  I dont know much about linux or commands so I dont know how I can change/edit the file from there so that I can get a resolution to work and let me back in with X working.  (Does this make sense?)  Basically I need to figure out how to edit a file without using gedit or something like that.  And I need to be able to save etc so that X will run again.  Please remember that I am a fool, so make the directions as easy as possible.....  Thanks in advance! 
Charles[/QUOTE]


Got it working, just used
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure xserver-xorg 
   hope this helps someon else........

---

### Post by netrattler on 2005-06-17
You can use vi to edit your file it might be a little more complicated to use then gedit but here are some basic instructions on how to edit with it.

1. sudo vi /etc/X11/xorg.conf
2. by pressing the i key on your keyboard this will put you into insert mode so your able to type.
3. When your done editing your file hit the Esc key to exit out of insert mode
4. To save the changes hold down the "shift key and press the : key" then type wq and press the enter key and it will write the changes to the file and exit.

If you need to exit the file without saving because you messed something up by accident just hit the "Esc key" then hold down the "shift key and press : key" and type q! and it will exit without saving the changes.

To learn vi you can always run the tutorial for it by running vimtutor and it runs you through a active tutorial allowing you to use the program as you learn it.

Hope this helps,
Joe

---

### Post by LongTooth on 2005-06-17
Can I assume this is the same with vim?

---

### Post by netrattler on 2005-06-17
Yes

Joe

---

