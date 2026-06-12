---
title: "Help with conky NOOB"
date: 2011-10-09
forum: Desktop Environments
---

### Post by 450rOOST on 2011-10-09
when I type conky in a terminal, this is what I get.  
I've tried removing the program and re-installing it.

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/linux/conky1.png[/IMG]

---

### Post by stinkeye on 2011-10-09
When running conky it will load the config @ **~/.conkyrc** which is a hidden file in home directory.
Conky does not place a config at ~/.conkyrc you have to make it yourself or download
somene elses and configure for your needs and computer specs.

If there is no **~/.conkyrc** config it will load the default config at **/etc/conky/conky.conf**
ctrl+h will show hidden files in your file browser.

The error is telling you your config isn't configured properly.
ie you have nothing below "TEXT" or you may have to use the **conky-all** package instead of **conky**.
The conky-all package has more compile options enabled which may be needed by your config.
In wich case uninstall **conky** and install **conky-all** 
 


Do you have a file in your home folder called **.conkyrc** (hidden)?

---

### Post by 450rOOST on 2011-10-09
> **stinkeye said:**
> When running conky it will load the config @ **~/.conkyrc** which is a hidden file in home directory.
Conky does not place a config at ~/.conkyrc you have to make it yourself or download
somene elses and configure for your needs and computer specs.

If there is no **~/.conkyrc** config it will load the default config at **/etc/conky/conky.conf**
ctrl+h will show hidden files in your file browser.

The error is telling you your config isn't configured properly.
ie you have nothing below "TEXT".


Do you have a file in your home folder called **.conkyrc** (hidden)?

I'll be honest, I don't understand a lot of what you said, I apologize.

Yes I have have a .conkyrc in the home folder.  When I open it, it is blank.  Is there where I need to put a conky file?

---

### Post by 450rOOST on 2011-10-09
[IMG]http://i678.photobucket.com/albums/vv143/RideRed/linux/HomeFolder.png[/IMG]

---

### Post by stinkeye on 2011-10-09
Yes.
You can delete that file if it is empty and then 
when you run **conky** it will load the default config @ /etc/conky/conky.conf
or just copy the default config to your home folder where you can easily edit.
In the terminal
```
cp /etc/conky/conky.conf ~/.conkyrc
```
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

### Post by 450rOOST on 2011-10-09
thank you so much, you&#472;e taught me more about conky in the last 10 minutes than what I've learned in reading the last 2 days, thanks.  I lready edited the conky to be on the right side of the screen, yay!

OK, so after I type 'conky' into the command line, and it comes up, how do I get it stay up and what do I press to get back to being able to type in a command?  Also, it seem kinda flickery, doesn't really stay on, turn on or off if I hover over with the mouse sometimes.

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/linux/conky2.png[/IMG]

---

### Post by 450rOOST on 2011-10-09
so in this thread [Post your conkrc. files](http://ubuntuforums.org/showthread.php?t=281865), the second post have a conky file, can I copy that and paste it into mine and then tweak for location, or are there too many variables?

---

### Post by stinkeye on 2011-10-09
The best way to test configs is to create a folder in your home directory
named **conky**
save the downloaded configs as anything you want
eg conky1 conky2 etc
in this folder.
Then to run conky using a specific config use ```
conky -c /path/to/config
```

eg ```
conky -c ~/conky/conky1
```

the **-c** tells conky to use a specific config.
the tilde "~" is a shortcut for **/home/your_username**
so is the same as writing **/home/450rOOST**

To run in terminal use "**&**" after the command (with a space) to allow conky to continue to run once the terminal is closed. 
eg```
conky -c ~/conky/conky1 &
```

or
press alt+F2 and run without the "&"

When testing configs its best to run in the terminal as you will see errors.

Once your happy with a config you can save it to ~/.conkyrc so as when you run **conky** it will use this config
or 
just continue using 
```
conky -c */path/to/config* 
```

---

### Post by 450rOOST on 2011-10-09
so I used the conky from the second post in that thread.  I definitely need to tweak some things.   But this one seems more stable.  I'm going to restart and see if it stays up.  How do I exit the terminal and keep conky going?

I want to add weather to this, but I think I can search around for that.  Thanks a ton stinkeye.

I don't want to mark this thread solved yet because I have some mroe q's that I hope people will help me with.

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/linux/conky3.png[/IMG]

---

### Post by stinkeye on 2011-10-09
No worries.
I'm subscribed to this thread so any problems just post.
Have a look at the conky howto link I posted earlier.
Also if your going to try more advanced configs 
you will need to uninstall conky and install the conky-all package.
Both are the same, conky-all just allows you to do more stuff with conky.

A lot of configs use scripts you will also have to download and 
check your conky config for correct paths to these scripts.
The scripts are usually posted at the same time as the conkyconfig if it uses any.

...and in the terminal
```
man conky
```
will explain all the variables.

---

### Post by 450rOOST on 2011-10-09
thanks, I will go through the guide.

this conky I have up displays network speeds, up and down.

the script reads 
```
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph _eth0_ 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph _eth0_ 20,130 000000 ffffff}
```

is what I have underlined what I need to change to get the graphs to work on mine?

So right not I should just go and get the conky-all package right now.

---

### Post by stinkeye on 2011-10-09
Yep, look in network connections to see what your using.

In the terminal
wired
```
ifconfig
```

wireless
```
iwconfig
```

---

### Post by 450rOOST on 2011-10-09
```
smoker@smoker-Dell-System-XPS-L502X:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Suckamea"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:F2:6C:DA:B6   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:101   Missed beacon:0


```

my wireless is called 'Suckamea', I tried replaing 'eth0' with 'Suckamea' to no avail, should that have worked?

---

### Post by 450rOOST on 2011-10-09
nevermind, I see.

---

### Post by stinkeye on 2011-10-09
Stick with it.
It's not that hard.
At the moment I'm running 4 conkys
# gmail
# surf report
# a forecast image from a local surf site
# and a hardware monitor under a transparent unity panel.

---

### Post by 450rOOST on 2011-10-09
thanks man, I've got a lot accomplished tonight.  I've been using linux for about 4 days.  2 days were install.

I'll come back to this thread later and I'll go through the guide.  I want to add email and weather, that would be sweet.  Thanks again for your help.

---

