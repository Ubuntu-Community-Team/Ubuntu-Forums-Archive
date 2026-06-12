---
title: "X Server Problem after installing Beryl."
date: 2007-01-31
forum: Desktop Environments
---

### Post by jcroot on 2007-01-31
Hey Guys!

I was trying to install Beryl in my Ubuntu Edgy System just to see &#8220;If I will be able to give it a try&#8221; but it didn&#8217;t work&#8230; I followed this guide: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL) 
So this is basically what I did:

Note: I will give details so any body here can easily help me.

1:  I open the terminal and run this command:  fglrxinfo

After I entered the command the output was something like this:

direct rendering: Yes

2:  Then I add deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main to the ubuntu system repository.

3: I open the terminal again and update the repository: sudo apt-get update

4: After all this I installed the X Server (O try to install it) using this command:
sudo apt-get install xserver-xgl

5: Then I installed the beryl and emerald-themes packages:

install sudo apt-get install beryl emerald-themes

5: Good, then I followed the instrucction to add an Xgl login session

So I did this:

&#8220;The startup script: Use your favorite text editor to create a script startxgl.sh in your path, like so:&#8221;
sudo gedit /usr/local/bin/startxgl.sh
it open a text file and I entered this code:
#!/bin/sh
/usr/bin/Xgl :1 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer &
sleep 4  
export DISPLAY=:1 
exec gnome-session

6: Then I followed this:

&#8220;For GNOME: Instead of adding a separate desktop session, you could alter your standard X session. This is not recommended for most users (see above). It might be useful however if you do not want to set up a separate X session for Beryl for some reason.&#8221;
First change gdm.conf-custom:
sudo nano /etc/gdm/gdm.conf-custom
Here I changed the code to: sudo gedit  /etc/gdm/gdm.conf-custom
And I added this code to the botton of the file:
0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

Now I restart my Ubuntu linux system and it says:

Fail to start the X Server, (your original interface) It is like that is not setup correctly. Would you like to view the X Server to dianose the Problem?
So I choosed &#8220;Yes&#8221;
And It says:
GDM: X Server not dfound: /usr/bin/xgl :0 :0 &#8211;Ful screen &#8211;ac &#8211;accel
GLX: pbuffer  - accel xu: gbo 
-aut /var/lib/gdm/ :0 X Auth &#8211;nolisten tcp ut7

Error: Command coud not be executed!

Please install the X Server to correct GDM configuration and restart GDM

This is all guys, can somebody please tell me what to do? I just got a black windows to type some code (I guess this black windows is the shell so I can fix my pc) but I don&#8217;t know what to do. Will I be able to install beryl one day without going trough all this?

---

### Post by jcroot on 2007-02-01
Anybody please?

---

### Post by jcroot on 2007-02-01
Please, I need help... :(

---

### Post by spacegypsy on 2007-02-01
Seems that I have the same problem!

See [this thread.]("http://ubuntuforums.org/showthread.php?t=351207")

If you got any solution, please let me know.

Did you save your xorg.conf before changing it?

thanx

---

### Post by Roma_emu on 2007-02-01
"GDM: X Server not dfound: /usr/bin/xgl :0 :0 –Ful screen –ac –accel"

I assume that the "xgl" in there is a typo that happened when you wrote the contents of the X server log. Because in your file it should say Xgl, not xgl.

I had a lot of problems to install Beryl (got it working after some 6 hours), but my problem was related to the Nvidia drivers (I have an older graphic card and the regular driver wouldn't work for me). Your problem seems to be that Xgl isn't installed...

What is the output of this?
 ls /usr/bin/*gl

---

### Post by glabouni on 2007-02-01
[http://ubuntuforums.org/showthread.php?t=351319](http://ubuntuforums.org/showthread.php?t=351319)

---

