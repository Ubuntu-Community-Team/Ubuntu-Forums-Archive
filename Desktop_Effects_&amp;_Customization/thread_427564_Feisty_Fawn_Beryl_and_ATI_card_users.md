---
title: "Feisty Fawn: Beryl and ATI card users"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by Neuralgia on 2007-04-29
The idea of this thread is to see if someone that has managed to get Beryl working in their ATI card model, and post out the solution. 

I've read people getting it to work on x1400, and lot's of x800 problems.

You may want to post your xconf.org along with your problem.

=-=-=-=-=-=-

In my case, I'm just tired of having problems with Beryl.

I've seen like 25 threads, and 25 more guides to install Beryl on Feisty, and none seem to work.

I own a Dell Dimension 8400 (desktop) w/ ATI x300 card, and an Inspiron 6400 w/ ATI x1300 (laptop)

In my case, what really bothers me, is the fact that:

     1. Beryl world without problems in Edgy, in both computers. Never seem to have any problems. In both cases I used the wiki guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

What went wrong? why did in my last version I had it working and now it's gone? I can't even use the regular "Desktop Effects", since I get "The Composite extension is not available".

     2. ATI gives no support. Please sign the petition here 
[http://www.petitiononline.com/x200MLin/petition-sign.html?](http://www.petitiononline.com/x200MLin/petition-sign.html?)

On both computers, when I log to the "Gnome with XGL" session, I get the "white screen of death".
I can see the mouse cursor, and can turn around the cube, but my whole desktop is white.

=-=-=-=-=

Hope this can help you

---

### Post by Rinzwind on 2007-04-29
Dell 9300 with an X300.
No problems at all.
Installed Feisty from scratch (I have a seperate /home so I just did a complete install; in 2 scripts I have all the software I remove and install to get me up and running with the apps I like). 
Installed the restricted driver in 'admin'.
Installed Beryl with the instructions in the unofficial guide to Feisty. 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29) Only thing I did extra was to install beryl-manager aswell.

And I was good to go. Beryl works without a hitch and it's fast and responsive.
Emerald wortks too except for some themes in SVN that are corrupt.

This:
> 
On both computers, when I log to the "Gnome with XGL" session, I get the "white screen of death".
I can see the mouse cursor, and can turn around the cube, but my whole desktop is white.

is because of this:
> 
What went wrong? why did in my last version I had it working and now it's gone? I can't even use the regular "Desktop Effects", since I get "The Composite extension is not available".


Your display driver is to blame. Get the composite working and Beryl works too.
Does rendering work when you check glxinfo?

ALSO: The Ubuntu version of beryl-core is incompatible with Xgl according  to this page:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

If you update Beryl after installation from Universe you screw things up. After initial install of Beryl you need to do this:
> 
# [http://ubuntuforums.org/showthread.php?t=418550](http://ubuntuforums.org/showthread.php?t=418550)
sudo -v
echo beryl hold | sudo dpkg --set-selections
echo beryl-core hold | sudo dpkg --set-selections
echo beryl-plugins hold | sudo dpkg --set-selections
echo beryl-plugins-data hold | sudo dpkg --set-selections
echo beryl-plugins-unsupported hold | sudo dpkg --set-selections
echo beryl-plugins-unsupported-data hold | sudo dpkg --set-selections
echo beryl-settings hold | sudo dpkg --set-selections
echo beryl-settings-bindings hold | sudo dpkg --set-selections
echo emerald hold | sudo dpkg --set-selections
echo libberyldecoration0 hold | sudo dpkg --set-selections
echo libberylsettings0 hold | sudo dpkg --set-selections
echo libemeraldengine0 hold  | sudo dpkg --set-selections
echo emerald-themes hold  | sudo dpkg --set-selections
echo beryl-manager hold | sudo dpkg --set-selections


---

### Post by randomstuff on 2007-04-29
Laptop with an X700.

Installed the fglrx driver with the restricted driver manager. Worked like a charm, except I manually had to set my monitor specs in the xorg conf (resolution and horizontal frequency).

Then I used the [beryl wiki guide]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL") without a problem. Only thing bad about the guide is it is a bit confusing about how to set up the XGL session and startup scripts etc. for GNOME, but I managed.

---

### Post by iPirates on 2007-04-29
Got it working on mine too.  
Followed the instructions here: [http://ubuntuguide.org/wiki/Ubuntu_Feisty](http://ubuntuguide.org/wiki/Ubuntu_Feisty)
Also installed 'beryl-manager' and i did:

sudo apt-get install build-dep beryl

which installed a bunch of stuff....
it worked perfect off of aiglx.
I havent even installed any drivers for my card, they're just running off of whatever was installed along with feisty.

---

### Post by Neuralgia on 2007-04-29
> **Rinzwind said:**
> Your display driver is to blame. Get the composite working and Beryl works too.
Does rendering work when you check glxinfo?

How do I get the composite working?

> ~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6334 (8.34.8)


I already knew about what you mention about Universe repo srewing thing up. I followed the instructions from the ubuntuguide (link infirst post).

=-=-=-=-=

I'm "this close" to reinstalling from scratch Feisty (rememeber, that I upgraded), but I'm sure this is not the solution, since I'll lose like a whole week of tweaking my Ubuntu, to get everything working (scanner, 5.1, webcam, email, etc.)

---

### Post by Rinzwind on 2007-04-30
Composite: it should be something in your /etc/X11/xorg.conf file but I'm just a newbie as you ;)

Thing is: installing from scratch is probably the easiest way for you to get it going. 

Oh and to help you out:
Before I reinstalled I made 3 scripts:
remove
install
berylblockupdates

1 removes anything I want to get rid of from the original install (evolution, ekiga, gaim etc).
The install does all I do want to have (live VLC, my own wallpaper changer, beryl etc).
The berylblockupdates does what I posted in my 1st reply.

It takes me 49 minutes to have my machine back up and running with what I have installed now. Try to find what you installed and write it down into apt-get install instructions and save the file in a fdd or send it to a gmail account or something like that (I store them on my laptop).

Updating is mostlikely 99% of the time the problem: someone missed to update 1 lib and all of us keep looking to fix your problem ;)

---

### Post by CRIKEY on 2007-04-30
x600

beryl works without a hitch using aiglx all i did is follow the instructions for ubuntu 7.04 on the beryl website

---

### Post by wave00 on 2007-05-02
Sorry @ randomstuff 
i'have X700 on Asus A6V but i'm not able to set up the Xorg and X700 don't work with restricted driver manager, i have a black screen.
Sorry but i don't speak  english very well!!!:)

---

### Post by blitzer on 2007-05-02
I used the default Open Source Driver (had to fglrx is not supported for my video card :( ) after doing this ```
sudo dpkg-reconfigure xserver-xorg
``` and choosing ati and the rest left to default.

Enabled Desktop Effects with compiz built in to Ubuntu and it worked beautifully.   Went to Add/Remove or (Synaptic Package Manager) and installed Beryl + Emerald worked beautifully  :popcorn:

---

### Post by dogmir on 2007-05-02
what i did to get it workin on my aspire 5100 which has the x1100...is basicly go through the same thing as in most of the guides out there....fglrx driver and xgl etc....compiz would kind of work but beryl would always fail...then i came across an article here [http://ubuntuforums.org/showthread.php?t=428442]("http://ubuntuforums.org/showthread.php?t=428442")
and it works perfectly....

---

### Post by usielt05 on 2007-05-10
im new to ubuntu so i dont exactly know what i specifically installed. But Beryl is working without any problems that i can tell.
All ive done is installed Beryl from the Synaptic, i believe it was Synaptic IDK didnt really pay much attention was too excited messing with everything :), 

Im running an X800 on an Abit Fatal1ty motherboard. I haven't installed any drivers for it i just did a regular install my Feisty is a Fresh 4 hour ago install

---

### Post by misfitpierce on 2007-05-10
Beryl and compiz run smooth on my ATI Xpress 200M in my laptop.... Task was tricky and dont remember my steps but I love it :)

---

### Post by HaoTian on 2007-05-10
Got Beryl working in an XGL session easily (using the guides posted earlier) on my Acer 5110 laptop w/ Radeon X1600 Mobility.  My only problem was that in the XGL session I couldn't get my dual display to work properly (It thought that both were 1280x1024, but my laptop is only 1280x800), so I'm unable to use it :(

Shame... it worked beautifully otherwise!

---

### Post by Goombie on 2007-05-10
I have a Dell Inspiron 9100 laptop with an ATI Mobility Radeon 9100 128MB video card. Installed Beryl alright using the AIGLX drivers, it runs ok. Only problem I have is a black window in my video player, so I can't watch videos that well. :(
Does anyone know the difference between the AIGLX and whether I should use one or the other? I'm confused as to what the difference is.

---

### Post by strumluff on 2007-05-10
For the topic I use an ATI Xpress 1100 (200M) on my laptop. I have it set up using XGL runs fine mostly with a couple of bugs, can't wait for improved proprietary drivers so we can use AIGLX.

> **Goombie said:**
> I have a Dell Inspiron 9100 laptop with an ATI Mobility Radeon 9100 128MB video card. Installed Beryl alright using the AIGLX drivers, it runs ok. Only problem I have is a black window in my video player, so I can't watch videos that well. :(
Does anyone know the difference between the AIGLX and whether I should use one or the other? I'm confused as to what the difference is.

Yeah basically AIGLX is part of a normal session you use so it is preferred to run Beryl with AIGLX and the ATI open-source drivers however not all cards support this which is why some of use have to use the closed source drivers with an XGL session which works okay but with improved resource usage, CPU usage imparticular.

As for your video problem, have you tried troubleshooting this? Choose the possible solution depending on the video player you use.

"This is an Issue with the Xv video driver with video players such as mplayer and xine (As well as players that use those backends, such as Totem and Kaffiene), because of the way it works, it bypasses composite and AIGLX, creating the "Video surrounded by blue border" effect. To disable it in mplayer, launch mplayer, go to prefrences and go to the "Video" tab. Then under "Video drivers" make sure that "x11 (XShm)" is highlighted. In Xine, open the setup window and click the Video tab. Change the video driver to "xshm", click Apply, and restart Xine.

Totem, among other video players, can also use a GStreamer backend. To fix this in GStreamer, open a terminal and type in:

gstreamer-properties

and press enter. Click the Video tab, then choose "X Window System (No Xv)". Click close and restart Totem if open. "

---

### Post by Goombie on 2007-05-10
Strumluff, that worked like a charm! I can actually see my videos now. :D

Thanks very much for your explanation about AIGLX and XGL, and for helping an Ubuntu newbie. :)
Now I can use Beryl all the time, since that was the only problem left.

---

### Post by ba5e on 2007-05-17
Hi I have a X1950 Pro linked by DVI to a 1680x1050@75 monitor with no screensaver and the fglrx drivers installed from this howto:

[http://wiki.cchtml.com/index.php/Ubu...lation_Guide#C](http://wiki.cchtml.com/index.php/Ubu...lation_Guide#C)

and Beryl installed by this howto:

[http://wiki.beryl-project.org/wiki/I...eisty_with_XGL](http://wiki.beryl-project.org/wiki/I...eisty_with_XGL)

Yes, all standard fare and it works like a dream however if I leave the pc alone and the monitor goes to standby, then I wake it with a key press or mouse shake - I see the green light come on, then the monitor just goes straight back to standby again.

The only way to bring the pc back (CTRL ALT F1 etc does not work) is to do a CTRL ALT BACKSPACE. This reloads X and the screen reinitialises.

I found the error

Code:

[fglrx:firegl_lock] *ERROR* Process 5774 is using illegal context 0x00000005

in
Code:

dmesg | grep fglrx

Full results as follows:

Code:

[   31.142958] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   31.145906] [fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[   31.145999] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   32.108832] [fglrx] total      GART = 130023424
[   32.108839] [fglrx] free       GART = 114032640
[   32.108841] [fglrx] max single GART = 114032640
[   32.108844] [fglrx] total      LFB  = 268304384
[   32.108846] [fglrx] free       LFB  = 244305920
[   32.108848] [fglrx] max single LFB  = 244305920
[   32.108849] [fglrx] total      Inv  = 0
[   32.108851] [fglrx] free       Inv  = 0
[   32.108852] [fglrx] max single Inv  = 0
[   32.108854] [fglrx] total      TIM  = 0
[ 1913.175059] [fglrx:firegl_lock] *ERROR* Process 5774 is using illegal context 0x00000005
[ 1916.229280] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 1916.241378] [fglrx] total      GART = 130023424
[ 1916.241385] [fglrx] free       GART = 114032640
[ 1916.241387] [fglrx] max single GART = 114032640
[ 1916.241389] [fglrx] total      LFB  = 268304384
[ 1916.241390] [fglrx] free       LFB  = 244305920
[ 1916.241392] [fglrx] max single LFB  = 244305920
[ 1916.241394] [fglrx] total      Inv  = 0
[ 1916.241395] [fglrx] free       Inv  = 0
[ 1916.241397] [fglrx] max single Inv  = 0
[ 1916.241398] [fglrx] total      TIM  = 0
[ 3349.643261] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 3349.655618] [fglrx] total      GART = 130023424
[ 3349.655626] [fglrx] free       GART = 114032640
[ 3349.655628] [fglrx] max single GART = 114032640
[ 3349.655630] [fglrx] total      LFB  = 268304384
[ 3349.655632] [fglrx] free       LFB  = 244305920
[ 3349.655634] [fglrx] max single LFB  = 244305920
[ 3349.655636] [fglrx] total      Inv  = 0
[ 3349.655637] [fglrx] free       Inv  = 0
[ 3349.655639] [fglrx] max single Inv  = 0
[ 3349.655641] [fglrx] total      TIM  = 0

Please let me know if you have any ideas what is causing this, or if I can supply some more information, thanks in advance

---

### Post by skug on 2007-05-25
Hi...

I believe I have the same problem as wave00.

 After installing the fglrx driver ( tried every way/howto/wiki I could find ) I end up with a blank screen when X starts and the entire laptop freezes to a halt, theonly way to restart is by harbooting (holding down the powerbutton until it shuts down the power).  

I am using an Asus A6Va laptop with an Mobility Radeon X700 gpu.
I actually had fglrx, aiglx and beryl running fine with edgy and early builds of feisty but when feisty whent to kernel 2.6.20+ it stopped working, not even the newest ATI drivers (8.36.5 when writing this) work. 

eI would relly appreciate any hints/suggestions on what the problem might be or how I could get it working. 

Thanks in advance :P

---

### Post by lsutiger on 2007-06-13
I didn't do any type of sudo command in Feisty. I just checked off the checkmark in the  "restricted drivers" section (Main menu-->System-->Administration-->Restricted Driver Manager). I tried all types of apt-get's and jacked up my system...I then did a fresh install and did what I said before. Installed Beryl by [ this tutorial]("http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html"). Has a few bugs, but it is beryl! Nothing that messes with the computer's performance.
Wish you luck! Ubuntu is not only fun, it is free :)

...Freedom is our common call

---

### Post by serlex on 2007-06-13
I got a X200 on board, installed restricted drivers then installed beryl, all went fine. When i run beryl-manager, red diamond comes up on task bar but no effects. any ideas?

---

### Post by KitChy on 2007-06-13
Got my ATI Radeon x1800 working within 5mins of following these instructions:

[CLICK MEH!]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---

### Post by serlex on 2007-06-13
what does this mean

> Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by lsutiger on 2007-06-13
You need to right click on the beryl icon and configure it, in adition to installing Emerald Theme manager. You also need to select your window manager ( It's all in the dropdown menu from Beryl)
[Follow the instructions from this link]("http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html") to setupo xgl also

---

### Post by bharat_kk_2000 on 2007-07-06
I have a DELL Inspiron 9300 laptop with ATI Mobility Radeon 300 as my graphics card. I have Beryl-svn working on Ubuntu Fiesty on a resolution of 1280x800. Resolution of 1440x900 works for 2 minutes and results in freezing of system. Beryl doesn't startup at any higher resolution than this and the X server crashes. Refer the link below for instructions that I have followed for my installation - 

[http://bharatparik.blogspot.com/2007/07/installing-beryl-svn-on-ubuntu-feisty.html](http://bharatparik.blogspot.com/2007/07/installing-beryl-svn-on-ubuntu-feisty.html)

Hope this helps.

---

