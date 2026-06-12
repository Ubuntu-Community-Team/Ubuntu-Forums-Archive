---
title: "use cron to maintain wireless internet connection"
date: 2009-05-19
forum: General Help
---

### Post by jakupl on 2009-05-19
My computer often jumps out of the connection during the night.
would it be possible to create a script to check if the internet connection is okay, if not then make it connect to my wireless and put in the password.
Then have cron run it every hour or so.

---

### Post by jakupl on 2009-05-20
bump

---

### Post by KhurramM on 2009-05-20
If u can perform two tasks on cli:

1> Check whether connected

2> Connect to internet

Then u can use cron. Better find the cli commands, I dont wireless, then I can help u on with cron, Insha-Allah.

---

### Post by kerry_s on 2009-05-21
sure just create a bash script with the commands then have cron run it say like hourly.
example>
in terminal:
sudo crontab -e

```
* /1 * * * /home/you/.wireless
```

 replace "you" with your name. save and close(ctrl+x & y & enter)

press alt+f2, type> gedit ~/.wireless

```
#!/bin/sh
iwconfig wlan0 essid "any" key xxxxxxxxxxxxxx
dhclient wlan0

```

replace "wlan0" with your connection
replace "any" with your wireless name
replace "xxxx" with your key

don't forget to make it executable, you can right click> properties> permissions
or in terminal
chmod +x ~/.wireless

something like that.

when you say loses it's connection what does that mean? is it like totally dropped no name nothing?

the reason i ask, is it could be as simple as putting "dhclient wlan0" in crontab.

---

### Post by jakupl on 2009-05-21
> **kerry_s said:**
> 
```
#!/bin/sh
iwconfig wlan0 essid "any" key xxxxxxxxxxxxxx
dhclient wlan0

```

replace "wlan0" with your connection
replace "any" with your wireless name
replace "xxxx" with your key

don't forget to make it executable, you can right click> properties> permissions
or in terminal
chmod +x ~/.wireless

That script does not work completely. My computer starts talking to the router, but not the internet. (and I had to run it as root to make it do anything)
> **kerry_s said:**
> 
when you say loses it's connection what does that mean? is it like totally dropped no name nothing?

the reason i ask, is it could be as simple as putting "dhclient wlan0" in crontab.
It completely dies. When I come to the computer in the morning, nm-applet usually shows the wired icon in stead of the wireless icon. As if it thinks it should be wired.
It completely forgets the essid and everything.

---

### Post by jakupl on 2009-05-21
uh by the way, it is encrypted with wpa2 encryption.

---

### Post by kerry_s on 2009-05-21
> That script does not work completely. My computer starts talking to the router, but not the internet. (and I had to run it as root to make it do anything)


thats why the "sudo crontab -e" for root to run it.
do you know how to manually connect it from command line?
use those same commands in your script.

i'll show you mine, hold on got to jump on a different computer, be back.

---

### Post by jakupl on 2009-05-21
> **kerry_s said:**
> thats why the "sudo crontab -e" for root to run it.
do you know how to manually connect it from command line?
use those same commands in your script.

i'll show you mine, hold on got to jump on a different computer, be back.

thanks. I'm not using crontab yet, I want the script to work first.

---

### Post by kerry_s on 2009-05-21
> It completely dies. When I come to the computer in the morning, nm-applet usually shows the wired icon in stead of the wireless icon. As if it thinks it should be wired.
It completely forgets the essid and everything. 

routers are setup to keep a dhcp lease for a period of time, this is so they can reuse the address if there has been no activity on a given lease.
anyways, you might try just renewing the dhcp lease to keep the connection alive. so try this:

```
**sudo crontab -e**
*** /1 * * * dhclient wlan0**

```

i don't use encryption on mine, just hidden essid & mac filtering.
i'm also not using cron for mine i have it set to a launcher, so i can connect when i resume from suspend. since i'm running it from a launcher i have the "sudo command" set up in visudo(example: %users ALL=(ALL) NOPASSWD: /sbin/ifconfig, /usr/sbin/iwconfig, /sbin/dhcpcd ) so i don't have to use a password. i'm running arch so my dhcp client is different.

the idea is the same your just running it from cron.
anyways mine looks like this. see pic

---

### Post by jakupl on 2009-05-21
woops, Sorry, I lost this post, because i am an idiot.

---

### Post by kerry_s on 2009-05-21
> What does this mean * /1 * * * I never really figured out how to use slashes in crontab.

```
 <minute> <hour> <day> <month> <day-of-week> <command>
```

"/1" tells cron every hour. "*" this is neutral or like yes to all of it, not sure how explain, like "*" has the same meaning as 0-6, "0" being sunday, for the day of the week.

example: say i want to wakeup mon->fri at 9am, it would be:
```
00 09 * * 1-5 $HOME/Scripts/alarmclock
```


> altso, I altso use mac filtering, but if you don't use encryption, isn't it then possible for people nearby to sniff everything that you do online?

yes and no, it's still encrypted/scrammbled a jumbled mess with in all the other stuff in the air on a 2.4ghz frequency. to capture and decode such things takes a lot of time and effort, most just want the victory of the crack, my router does not broadcast the name so it's hidden but not locked, no fun in cracking something thats not locked, but if they were to guess the name and try and connect, they would just get dropped quietly cause there not on the mac filter list, unless they spook/clone it, otherwise they'll just wait and wait and wait, but never get connected.
anyways, i'm not that paranoid. ohh, and my router has a very long password, non-dictionary, takes awhile to type in. lol

---

### Post by jakupl on 2009-05-21
Well I have now done
crontab kept saying that I had a bad hour "/1" so I just did this:
```
**sudo crontab -e**
**20 * * * * dhclient wlan0**

```


and I got rid of the encryption, because it was annoying me. So I will get back to you if it works.
The problem is, that it is pretty hard to check if it is working, as I don't know if it is random or not. I have lost the connection the last 3 nights, so if it stays up tonight, then I will call it a success. But it will take some days to be sure. Thanks a lot.

---

### Post by kerry_s on 2009-05-21
> **jakupl said:**
> Well I have now done
crontab kept saying that I had a bad hour "/1" so I just did this:
```
**sudo crontab -e**
**20 * * * * dhclient wlan0**

```


and I got rid of the encryption, because it was annoying me. So I will get back to you if it works.
The problem is, that it is pretty hard to check if it is working, as I don't know if it is random or not. I have lost the connection the last 3 nights, so if it stays up tonight, then I will call it a success. But it will take some days to be sure. Thanks a lot.

sorry, looking at the man page it should be "*/1" so it would look like:
```
* */1 * * * dhclient wlan0
```

20 minutes is a little to often don't you think, you could do 55min, less than an hour which is what most routers are set to for lease, i know i changed mine to 1 day when i setup my router dhcp lease:
```
55 * * * * dhclient wlan0
```

---

