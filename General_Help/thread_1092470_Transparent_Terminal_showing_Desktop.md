---
title: "Transparent Terminal showing Desktop"
date: 2009-03-10
forum: General Help
---

### Post by nehagarg on 2009-03-10
Hiya,

I deleted my xorg.conf files (including failsafe and backup) by mistake yesterday. (Yes, i know .. veryyy stupid :) ) .. However, I have my computer running again as I want it, including a dual monitor set up.

I use Ubuntu 8.10. I have my terminal set to a transparent background. It used to work ok but now the transparent background shows my desktop instead of the browser window running behind it. I hope I am making sense. I have attached a screen shot too.

Why is this happening and how can I fix it please ?? Any help would be mucho appreciated.

Thanks :)
NG

---

### Post by klemes on 2009-03-10
This is probably due the the fact you are not running compiz with your new setup and thus you are defaulting to GNOME terminal's default behaviour of showing your desktop's background in transparent mode.
If you activate compiz you should see as background the background of whatever window there is behind the console.

---

### Post by nehagarg on 2009-03-10
Thanks :)

I am new to ubuntu .. Could you also tell me how to activate compiz ?? I havent been able to find a way to do it .. 

Thanks
NG

---

### Post by klemes on 2009-03-10
Simply right-click at your desktop and choose 'change Desktop background' from the drop down menu.Then select Visual effect and then click on Extra or Custom and compiz will start if everything is alright.

---

### Post by Nano_ext3 on 2009-03-10
Compiz can be installed by going to Add/Remove programs and searching for "compiz"  Make sure that at the top "All available Packages" is selected and under Softwae Sources under Systen Tab > Administration > Software sources, that you have the third party repositories enabled.  Compiz can also be installed via the terminal:

sudo apt-get install compiz

To properly have this running your computer must support compiz with the appropriate video card driver.  Make sure that under System > Preferences > Appearance , that at the very least, normal effects is enabled under the tab "Visual Effects" tab.  If you cannot enable this try installing EnvyNG , which is a fantastic program to install your ATI / or Nvidia driver automatically.   This will also, in addition to the graphics driver, a repository addition , so your normal system updates will include the latest driver , when the EnvyNG developer decides to code the latest stable driver.  The developed tends not to code , or push the Beta drivers, which are the latest on nvidia's webside (do not know about ATI)

Install EnvyNG by doing:

Gnome :  sudo apt-get install envyng-gtk
KDE   :  sudo apt-get install envyng-qt

This can be also done via Synaptics Package manager under,System > Administration > Synaptics

Once installed, go to your System > Prefrences > Advanced Desktop Settings or type "copmiz" into the terminal.


Hope this helps, 

Let me know if you need anything else.


Cheers!

-Nano

---

### Post by nehagarg on 2009-03-10
I tried that before . It tries to find drivers and then says can't find Desktop settings. So the visual effects are only set to the most basic :(

lspci tells me I am using Intel Corporation Mobile 945GM/PM/GMS

Thanks
NG

---

### Post by nehagarg on 2009-03-10
Thanks Nano

Trying to Install compiz and envyng-gtk both give me this error

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I have not been able to set my visual effects setting to Normal. It says Dekstop settings not available. I am guessing this has to do with my graphics card driver or the xorg.conf file. I am using intel 945GM. And the xorg.conf file got deleted and seems like i only have the most basic functionality here. :(

Thanks
NG

---

### Post by klemes on 2009-03-10
I have been running the same card and it is very capable of running compiz.
Try the steps that are described in the previous post.

---

### Post by klemes on 2009-03-10
Try to only have one instance of the package manager running.
ie if you use apt-get on the console close Synaptic and vice versa.

---

### Post by nehagarg on 2009-03-10
Done.


I have compiz now and still dont seem to be able to set the visual effects to anything more than the None option .. When I try to set it to Normal, it searches for drivers and the tells me that Desktop settings could not be enabled.

Thanks for all the help guys. I really appreciate it .. This is really wierd .. :S

NG

---

### Post by nehagarg on 2009-03-10
Could it be a setting in my xorg.conf file ?? Because that file did get deleted. I dont want to completely replace it because it might mess up my dual monitors.

---

### Post by klemes on 2009-03-10
Make sure that you have in your xorg.conf (/etc/X11/xorg.conf)in the Device section a line that says "Driver" "intel" or "Driver "i810" .If not edit that line appropriately with sudo gedit /etc/X11/xorg.conf  .

---

### Post by Nano_ext3 on 2009-03-10
Did you install Envy-NG via my directions above? You must have the proper driver installed first.  

Could you also run this command in terminal for us?

sudo lspci -v | grep VGA

or.

sudo lspci -v (and find where it notes "ATI" or "NVIDIA")


That could help us out a great deal.  Like my laptop, if you have a legacy ATI graphics adapter, EnvyNG will not be able to install it and give you a warning.  Could you paste in your post if you do* receive a warning or error when trying to auto install the "ATI" driver with EnvyNG? 

Also with my laptop, I have to tell compiz (after changing to the ati driver) to SKIP CHECKS, to get it to run on a legacy card.

The script that launches compiz checks your graphics card against a blacklist of cards which are "known" to behave badly with compiz. But you can overrule these checks: create file under your home directory with the path

 ~/.config/compiz/compiz-manager and put in it the line:
SKIP_CHECKS=yes


Then compiz will be launched regardless. I guess you should also look through the bug reports and see if you can find what the issue is supposed to be (if any) with this card.  My best suggestion is to NOT enable the advanced settings, as they were blacklisted for a reason.  I often had poor CPU performance and choppy video sometimes.  Use CAUTION when doing any of this.

If your XORG.CONF is broken, go to Terminal and type "sudo -dpkg-reconfigure xserver-xorg" to reconfigure x server.  If you want to start out with the EXACT original you once had, you could boot the liveCD and then copy the file /etc/X11/xorg.conf and then email it to yourself or something then copy it into your new installation, but FIRST backup the orig. but doing "cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup"  Now paste the contents of that text file from your email into the "real" xorg.conf, getting rid of anything in there first.

Hope this helps!

Cheers!

-Nano

---

### Post by nehagarg on 2009-03-10
Cheers Guys :)

@Nano

Here is the result of the command you asked me to run

stargazerr@stargazerr-laptop:~$ sudo lspci -v | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


I dont really use a Nvidia graphics card.

Also, I am not trying to set myself up with the advanced settings. Just the Normal settings. Right now it is set to None. I edited my xorg.conf file to include Driver "i810" .. But now when I try to go to Visual Effects and set it to Normal, it just keeps searching for available drivers.

I do not really want to restore my original xorg file as it will mess up the dual monitors I have set up. All I need is for my terminal to start showing the window behind it when set to transparent and not the desktop.

Thanks
NG

---

### Post by Nano_ext3 on 2009-03-10
Try taking a look at this : thread [http://ubuntuforums.org/showthread.php?t=966733](http://ubuntuforums.org/showthread.php?t=966733)

------------------------------------------------------------------
FIXED! What did it for me was to install libgl1-mesa-dri.
The clue was in the output from:

grep EE /var/log/Xorg.0.log

which said:

dlopen of /usr/lib/dri/i915_dri.so failed

Apparently the file was missing.
------------------------------------------------------------------

Then it suggests the following for installing the driver:

1.  sudo apt-get install xserver-xorg-video-intel
2.  Then press Alt+F2, to reload x server
3.  gksudo displayconfig-gtk
4.  Type "sudo lspci | grep VGA" again into Terminal
5.  Should now show the right driver.
6.  Regardless run "compiz-check" in Terminal.  Systems should be a go :)

Another user suggested:  

"2)However looking around I found a post (Sorry, I can't find it again) suggesting to uninstall using Synaptyc Package Manager all the packages containing "fglrx"."

Removing the fglrx driver may help.

------------------------------------------------------------------


Let me know if any of that helps ,

Ill get you up an running, I love the challenge :)


Cheers!

-Nano

---

### Post by nehagarg on 2009-03-10
Thanks Nano, :)

Your suggestion worked .. I was actually looking at this same thread, you suggested :) ..

BUT BUT BUT .. Here is what I did

1. reconfigured the xorg.conf file and installed the intel driver. Everything checked out on compiz check.
2. restarted computer
3. Went into visual effects and was now able to select the Normal option. The terminal started working the way I wanted it to. Me VERY happy :D
4. Now, I wanted to set up my dual monitor again. So, Went into screen resolution. Unchecked Mirror Screens and set the resolution for the external monitor to 1440x900 and for the laptop screen to 1048x768.

And here .. we were back to square 1 .. :( .. I now have a dual monitor but again I cant have anything but the None setting selected on visual effects. What the Hell ??? :(

NG

---

### Post by Nano_ext3 on 2009-03-10
Im sorry to say, Im not sure how xorg and this "backwards" way of installing the driver, reacts when asked to do a dual monitor setup.  Ill keep looking, Ill most likely reply tommorow, I will be busy for the rest of the day.

Cheers!


-Nano

---

### Post by nehagarg on 2009-03-10
Will Do .. Thanks for all the help so far Nano :)

NG

---

### Post by nehagarg on 2009-03-12
Bumping this one up .. Any help anyone please ?

Thanks
NG

---

### Post by Nano_ext3 on 2009-03-12
Ive only been using linux for a few years, heavily in the last year.  That is all I can think of for now , Im sorry.  

Moderators?  Any input?

---

