---
title: "Chromium-browser fullscreen problem"
date: 2011-02-14
forum: Desktop Environments
---

### Post by paha77 on 2011-02-14
I'm running 5 outdoor touchscreen machines (aka kiosks) with Ubuntu. 

There's a special user on the machines with a special xsession, which only runs Chromium browser without any window manager:

```
rendszer@rendszer-desktop:~$ cat /usr/share/xsessions/kiosk.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Kiosk Mode
Comment=Chromium Kiosk Mode
Exec=/usr/share/xsessions/chromeKiosk.sh
Type=Application

```

```
rendszer@rendszer-desktop:~$ cat /usr/share/xsessions/chromeKiosk.sh
#!/bin/bash

while true; do chromium-browser %u --kiosk --start-maximized --disable-restore-background-contents --login-screen-size="800,600" --disable-translate --disable-new-tab-first-run --enable-vertical-tabs; sleep 5s; done

```

Until 8th Feburary, 2011 everything went well but on that thay I've upgraded all packages and since then the Chromium browser beaves strange:

Even it's started in maximized, there's a little stripe on the bottom of the screen. (As seen on the screenshots).

Today I've set up a virtual machine to test it and the result is the same (see the other screenshot).  

Do you have any ideas?

Thanks.

---

### Post by burnin240sx on 2011-07-11
Did you ever find a solution to your issue? I'm having the same issue with RHEL6 and I don't think it's the browser but more a setting that i'm missing. I've tested it with firefox and got the same result. the weird thing is that the output resolution is correct. I can also move the window around. I just can't get it to maximize or do full screen.

---

### Post by paha77 on 2011-07-12
> **burnin240sx said:**
> Did you ever find a solution to your issue? I'm having the same issue with RHEL6 and I don't think it's the browser but more a setting that i'm missing. I've tested it with firefox and got the same result. the weird thing is that the output resolution is correct. I can also move the window around. I just can't get it to maximize or do full screen.

Unfortunately I haven't found any solution. :-(  So if you'll find anything please share.

Thx.

---

### Post by burnin240sx on 2011-07-15
So after going a little crazy I found that the issue was with chrome not detecting the correct window size. In the past the window size was saved in the "Local State" file. but google has since moved the location of the setting to ~/.config/google-chrome/Default/Preferences.

Now the best was for me to have chrome run in kiosk mode with the correct window size was with this script. that checks your display resolution and replaced the correct setting in the Preferences file.
```

#!/bin/bash

#get mac address and set as a viarble to be used in url.
MAC=$(ifconfig eth0 | grep -o -E '([[:xdigit:]]{1,2}:){5}[[:xdigit:]]{1,2}')

#get current resolution from xrandr and save the screen size into the chrome Preferences. If not done chome starts in fullscreen with the size of the last window.
cat ~/.config/google-chrome/Default/Preferences | perl -pe "s/\"bottom.*/\"bottom\": $(xrandr | grep \* | cut -d' ' -f4 | cut -d'x' -f2),/" > ~/.config/google-chrome/Default/Preferences
cat ~/.config/google-chrome/Default/Preferences | perl -pe "s/\"right.*/\"right\": $(xrandr | grep \* | cut -d' ' -f4 | cut -d'x' -f1),/" > ~/.config/google-chrome/Default/Preferences

#Turn off screensaver
xset s off

#turn off power management
xset -dpms

#check if chrome is running and if not start it. This is to prevent loops.
if !(ps -A | grep -w chrome > /dev/null)
then

#sleep for 10 seconds because the web page will not load due to network not fully started at first boot.
sleep 10s
google-chrome --kiosk http://phys31223.physics.gatech.edu?mac=$MAC&

#hide the cursor
unclutter -grab
fi

```

I hope that this will help out any frustrated chrome kiosk users out there.

Stephen Lester
RHCSA

---

### Post by paha77 on 2011-07-18
> **burnin240sx said:**
> 
I hope that this will help out any frustrated chrome kiosk users out there.


Unfortunately it doesn't help.  I use chromium so the preferences file is: ~/.config/chromium/Default/Preferences.  I've chmoded it to 0400 so chromium is only able to read it and saved the "window placement" section as:

```
      
         "window_placement": {
         "bottom": 1024,
         "left": 0,
         "maximized": false,
         "right": 1280,
         "top": 0,
         "work_area_bottom": 1024,
         "work_area_left": 0,
         "work_area_right": 1280,
         "work_area_top": 0
      }

```

But nothing happens. :(

---

### Post by harryharryharry on 2011-12-25
I am not running chromium in kiosk mode. My problem: When I was running chromium maximized - the minimize, maximize and close buttons were not visible (basically the same problem I saw in the attachments). minimizing the instance of chromium-browser temporarily fixed this problem, which was pretty annoying though...

same as paha77 chmod 0400 after modifying the Preferences file didn't work for me either. This was my solution (beware, all chromium-settings such as bookmarks are lost):

```
sudo apt-get purge chromium-browser
```
```
sudo apt-get autoremove
```
```
sudo aptitude purge ~c
```
```
sudo rm -rf ~/.config/chromium/
```
```
sudo apt-get install chromium-browser
```
```
sudo nano ~/.config/chromium/Default/Preferences
```

type in your correct resolution as mentioned in other posts, save, exit and start chromium-browser. I guess by this time you could optionally use chmod 0400 to prevent the Preferences file from being changed, but I don't see the added value since it didn't work to begin with :(...

I find it rather strange that I had to completely remove the config files, modifying them didn't result in success...

---

### Post by paha77 on 2011-12-26
> **harryharryharry said:**
> 

same as paha77 chmod 0400 after modifying the Preferences file didn't work for me either. This was my solution (beware, all chromium-settings such as bookmarks are lost):


Thx harry, I'll give it a try.

---

### Post by sweetdanger on 2012-01-14
> **harryharryharry said:**
> I am not running chromium in kiosk mode. My problem: When I was running chromium maximized - the minimize, maximize and close buttons were not visible (basically the same problem I saw in the attachments). minimizing the instance of chromium-browser temporarily fixed this problem, which was pretty annoying though...

same as paha77 chmod 0400 after modifying the Preferences file didn't work for me either. This was my solution (beware, all chromium-settings such as bookmarks are lost):

```
sudo apt-get purge chromium-browser
``````
sudo apt-get autoremove
``````
sudo aptitude purge ~c
``````
sudo rm -rf ~/.config/chromium/
``````
sudo apt-get install chromium-browser
``````
sudo nano ~/.config/chromium/Default/Preferences
```type in your correct resolution as mentioned in other posts, save, exit and start chromium-browser. I guess by this time you could optionally use chmod 0400 to prevent the Preferences file from being changed, but I don't see the added value since it didn't work to begin with :(...

I find it rather strange that I had to completely remove the config files, modifying them didn't result in success...


Thanks!! This Work for ME!! On Ubuntu 11.04

---

### Post by c2h2 on 2012-06-11
is it fixed?

afaik, without a window manager, full screen can be an issue,

I have built my own embedded chromium with CEF [http://code.google.com/p/chromiumembedded/](http://code.google.com/p/chromiumembedded/) but can do fullscreen properly, looking for answer as well.

---

### Post by botov13 on 2013-04-23
This may help
[http://nexxylove.tumblr.com/post/22690398464/ubuntu-web-kiosk-in-10-easy-steps](http://nexxylove.tumblr.com/post/22690398464/ubuntu-web-kiosk-in-10-easy-steps)

---

