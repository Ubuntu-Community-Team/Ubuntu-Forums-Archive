---
title: "GDM install problem..."
date: 2009-12-12
forum: Desktop Environments
---

### Post by ShawnB391 on 2009-12-12
This is the GDM that I'm trying to install
[http://gnome-look.org/content/show.php/Wooden?content=90685](http://gnome-look.org/content/show.php/Wooden?content=90685)

These are the steps I've been following
[http://ubuntuforums.org/showpost.php?p=7576112&postcount=365](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365)
and
[http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)

I've been able to change the background image, but I would like my login to look like the one in the picture from gnome-look.org....

What are the steps I should take to install this GDM in Karmic Koala?

---

### Post by spiderbatdad on 2009-12-12
```
sudo apt-get install gdm-2.20
```
Then choose gdm-2.20 when offered selection during the installation process. Next:
```
sudo -i
cd /etc/gdm
sed &#8217;s|X11R6/||&#8217; gdm.conf > /tmp/gdm.conf
mv /tmp/gdm.conf .
exit
```
Next reboot. Login using username then password from the default gdm, assuming you are not using auto-login. Now you should find System>>Administration>>Login Window...go to the "Local" tab. There should be gdm themes to choose from. To add additional themes, simply drag the GDM.tarred package from your desktop or download directory, and drop the package into the "Local" tab window of theme options.

---

### Post by ShawnB391 on 2009-12-12
> sudo -i
cd /etc/gdm
sed &#8217;s|X11R6/||&#8217; gdm.conf > /tmp/gdm.conf
mv /tmp/gdm.conf .
exit


Returned this error.

> 
shawn@shawn-laptop:~$ sudo -i
[sudo] password for shawn: 
root@shawn-laptop:~# cd /etc/gdm
root@shawn-laptop:/etc/gdm# sed &#8217;s|X11R6/||&#8217; gdm.conf > /tmp/gdm.conf
-bash: X11R6/: No such file or directory
sed: -e expression #1, char 1: unknown command: `&#65533;'
&#8217;: command not found
root@shawn-laptop:/etc/gdm# mv /tmp/gdm.conf .
root@shawn-laptop:/etc/gdm# exit


I rebooted and received this message.

> 
No servers were defined in the configuration file and XDMP was disabled. This can only be a configuration error. GDM has started a single server for you. You should log in and fix the configuration. Note that automatic and timed logins are disabled now.


Eventually I was able to log in. My log in screen now has a little yellow flower and a blue background.

---

### Post by spiderbatdad on 2009-12-13
The error looks like it is in your command. Sometimes it is easier to copy paste from instructions. After the substitution is the file gdm.conf...you need a space in front of the file name.
```
sed &#8217;s|X11R6/||&#8217; gdm.conf > /tmp/gdm.conf

```
The idea of this command is to search the file /etc/gdm/gdm.conf and replace every instance of /usr/X11R6/bin/ with /usr/bin/. Hence the cd into /etc/gdm first.
This is a posted bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/gdm-2.20/+bug/445256](https://bugs.launchpad.net/ubuntu/+source/gdm-2.20/+bug/445256)
So however the file gets edited, by hand or through sed expression, thats the idea.

On launchpad the command is issued like this: ```
 sed -i 's/X11R6\///' /etc/gdm/gdm.conf 
```In this case you would not cd /etc/gdm first.

---

### Post by ShawnB391 on 2009-12-13
I uninstalled GDM 2.20, reinstalled GDM, then I retried reinstalling GDM 2.0 useing sed -i 's/X11R6\///' /etc/gdm/gdm.conf.  I was able to open System > Administration > Login Window and add my GDM Theme, however, when I reboot I am still reciveing the "No servers were defined in the configuration file and XDMP was disabled. This can only be a configuration error. GDM has started a single server for you. You should log in and fix the configuration. Note that automatic and timed logins are disabled now." error. Also, when I am able to get past this error, my GDM still isn't working. How can i configure my system to display this GDM properly?

---

### Post by spiderbatdad on 2009-12-13
I have not encountered this error, but have run the above procedure on several machines running Karmic. It looks like a sessions error. That is, from the options at the login screen, I think you need to select a session like Gnome.
I'm assuming when you install gdm-2.20 you get a dialog asking you to choose between gdm and gdm-2.20, and you select gdm-2.20.

Also, you might have a look through the file /etc/gdm/gdm.conf to see that is edited properly. I'll add an archive of mine here for comparison.

You can extract it on your desktop by right click and choose extract here. Then in your terminal run
```
diff ~/Desktop/gdm.conf /etc/gdm/gdm.conf
``` If the command just returns a prompt, the files are identical.
There is also a /etc/gdm/gdm.conf-custom that gdmsetup writes. Youmight browse it and see if anything is configured there.

---

### Post by Big_tone on 2009-12-20
For those people just looking to replace the ugly brown background gdm screen: this is the most simple workaround.
first - open up a terminal and type: sudo nautalis then type your password when prompted and minimize terminal (you are now root in nautilis) and navigate to /usr/share/images/xsplash via the window that opened (this will allow you to rename and edit your xsplash background)

second - download or create a bg of your choice and save to the desktop.

third - make the name of this file the same as the one in usr/share/images/xsplash (in my case it was bg_2560x1600.jpg)

fourth - drag your new image into the xsplash folder (usr/share/images/xsplash), replace when it asks you too (good practice to backup originals) and WALLAH!  No more ugly brown screen.  Since the same image is used for splash screen and login screen, there will be no more brown.

You can also edit the white loading bar (with gimp or whatever) but, I like it as is.

---

### Post by abilashgt on 2010-01-01
when i used this:
sudo sed &#8217;s|X11R6/||&#8217; gdm.conf >/tmp/gdm.conf

i am getting a message: 
sed: -e expression #1, char 11:unterminated 's' command


pls help me..i am stuck

---

### Post by spiderbatdad on 2010-01-01
try again. try pasting commands from second post. I suspect you did not observe spaces.

---

