---
title: "Conky/Cairo wifi"
date: 2010-05-29
forum: Desktop Environments
---

### Post by Scooter_X on 2010-05-29
Hello all, I've been digging for the past few days, and haven't found a solution to an issue I'm having with Cairo.

I'm trying to use the 'rings.lua' script found [here]("http://conky.linux-hardcore.com/?page_id=2800") and for the life of me I cannot figure out the name or argument I should be using to display my wifi signal strength. I noticed one line that said: 
```
[COLOR=Black][I]-- "name" is the type of stat to display; you can choose from 'cpu', 'memperc', 
'fs_used_perc', 'battery_used_perc'.[/I][/COLOR]

```And doesn't seem to allow for wifi signal strength, but I don't know. Also if it does, I don't know what argument to use. The script that was relevant to wifi that I use in conky normally is:
```
${if_up wlan0}WiFi: ${hr}
Strength: ${wireless_link_qual_perc wlan0}% $alignr Essid: $alignr${wireless_essid wlan0}
DLS: ${downspeed wlan0} $alignr Total: ${totaldown wlan0}
ULS: ${upspeed wlan0} $alignr Total: ${totalup wlan0}
Public IP: $alignr ${execi 3600 wget -O - http://whatismyip.org/ | tail}
Local  IP: $alignr${addr wlan0}${endif}
${if_up eth0}Wired: ${hr}
```So I made my own element in the settings table and tried using my own name ('wifi') and using the argument 'wlan0' as well as 'hr' (I don't know what 'hr' means, it just was the bit that was actually outputting the value)

So, yea. I'm a little stuck and haven't been able to find anything to help me figure it out. I'd appreciate some help. Thanks.

PS- What exactly does fs_used_perc refer to? I assume that the element refers to the hard drive and how much space is left, but I don't know. I also tried figuring that one out and couldn't.

---

### Post by Jeroensum on 2010-05-30
Now, I don't know why the default variable in Conky doesn't work, but here's a fix.

To calculate the signal strength there is a little floating point math involved which is only achievable by tools like awk. Bash itself can only do integer math which will allways result in 0 when trying to solve these kinds of (math)problems.

The simplest way to get the value is to write a small script which does the math for you and to call that script from Conky. I'm by no means a Bash guru but this thing does what you want from it, output the percentage:

```

#!/bin/bash
arg1=`iwconfig wlan0 | grep Link | cut -d "=" -f2 | cut -d "/" -f1 | sed 's/ //g'`
arg2=`iwconfig wlan0 | grep Link | cut -d "/" -f2 | cut -d " " -f1 | sed 's/ //g'`

echo $arg1 $arg2|awk '{print $1/$2*100}' | cut -d "." -f1

```

You may need to substitute wlan0 with your own adapter ;)
Save the script as wifi_perc.sh and give it execute permissions: 
chmod 700 wifi_perc.sh

To call the script from Conky replace:

  ```
${wireless_link_qual_perc wlan0}%
```

With:

  ```
${execi 120 path_to_script/wifi_perc.sh}%
```

execi is Conky's way of calling an external script and 120 is the amount of seconds Conky will wait until it calls the script again.

You might see some difference between the percentage in Conky and the percentage in your applet, this is because Conky checks the signal strength every 2 minuten (120 seconds) and the applet will have some other interval. If you want you can call the script every second but I wouldn't recommend it because of sysloads. In my opinion 2 minutes is fine but you could tweak it to 10-20 seconds, just keep an eye on your sysload for awhile to make sure it doesn't strain the system.

To answer your last question:
fs_used_perc is the percentage of (disk)space used by the filesystem, in otherwords they probably run  *df -h*  and fetch the *Use%* column from the specified mount point ;)

Have fun!

---

### Post by Scooter_X on 2010-05-30
Thank you, Jeroensum for your help. Actually, I just hopped on right now to post what I found out about the wifi thing. And it wasn't conky itself that was having problems, it was the rings script. What I found out at the end was that my argument was correct, and I needed to use "wireless_link_qual_perc" as my 'name' in the element of the rings script. Here's what I have down:

        name='wireless_link_qual_perc',
        arg='wlan0',
        max=100,
        bg_colour=0xFF9E00,
        bg_alpha=0.3,
        fg_colour=0xFF9E00,
        fg_alpha=0.7,
        x=165, y=170,
        radius=30.0,
        thickness=20,
        start_angle=0,
        end_angle=360

So if anyone else doesn't know how to do this, hopefully they'll find this thread. I wish that I could find some sort of document that lays out all of the variables and such that I can use, sortof like [this ]("http://conky.sourceforge.net/variables.html")one here, but for cairo/lua stuff... I had to dig deep and read tons of forum posts for this. And it should've been simple in my opinion.

Anyway, thanks again. Also for filling me in on the filesystem thing. I appreciate that.

---

