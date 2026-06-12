---
title: "Ubuntu hostname is not changing."
date: 2009-04-15
forum: General Help
---

### Post by Roasted on 2009-04-15
I set up a FOG imaging server with a basic desktop here at work. I named it UbuntuFOGDesktop. I also have a "mobile" server running on my laptop, so if I need to capture an image in another building I just use the laptop. Later, I just planned on using Samba to push the image over since I'm familiar with Samba.

I noticed this and I can't seem to figure it out. I'm using an XP desktop here and my Ubuntu FOG server.

The IP address is 10.1.1.111 to my Ubuntu desktop. When I try to ping the hostname, UbuntuFOGDesktop from the XP desktop, it says cannot be found. Yet it can ping the IP.

So I edited /etc/hostname to change the hostname. Then I rebooted. I named it FOG-Desktop. Then the XP desktop could see it fine.

Then I changed it back to UbuntuFOGDesktop. Same problem. I can't find it. But I tried to ping FOG-Desktop again and sure enough, it pinged it, showing me the IP of 10.1.1.111... which is my Ubuntu machine.

I checked /etc/hostname again and UbuntuFOGDesktop is indeed the hostname, however, somehow it's being read as FOG-Desktop which is what I previously had the hostname as.

Why is this not taking the hostname of UbuntuFOGDesktop?

---

### Post by Narvinye on 2009-04-16
To have the changes to the hostname take effect run 
```

sudo /etc/init.d/hostname.sh start
```

Then reboot.  

I'd recommend removing your pubilc IP from your post... usually not a good idea to post this information. :KS

---

### Post by Roasted on 2009-04-16
It doesn't matter, because it's a private IP address - no different than 192.168 IP addresses. I'll do it for the sake of doing it, though. :)

---

### Post by Narvinye on 2009-04-16
Ahhh ok.  Did running the shell script help to resolve the problem you were running into?

---

### Post by Roasted on 2009-04-16
I tried that command. Didn't work.

I've tried all of the following host names. Each process was me running sudo gedit /etc/hostname, changing the hostname accordingly, and rebooting. Then on my XP laptop I would try to ping that hostname. The results I got are below.

FOGDesktopUbuntu - Didn't work.
UbuntuFOGDesktopX - Didn't work.
UbuntuFOGDesktop - Didn't work.
FOG-Desktop - Worked.
FOGDesktop - Worked.
Taco-Bell - Worked.
Ubuntu-Intrepid - Worked.
FOG-Intrepid - Worked.
Ubuntu-FOG - Worked.
Ubuntu-FOG-Desktop - Didn't work.
Ubuntu-FOGdesktop - Didn't work.

What kind of restrictions are there on Ubuntu hostnames? Obviously there's something that dictates whether or not the hostname is pingable on a network. Something here is causing this inconsistency, yet I can't seem to figure it out. Does anybody know?

EDIT - Okay, figure this one out. I have my work laptop as dual boot so I can have certain images with me when I go to different buildings. I decided to go through this process with my laptop, but instead I would just name it once to what I wanted to name it and that'd be it. I named it FOG-Laptop, whereas the desktop I tested above is FOG-Desktop.

FOG-Desktop can be pinged.
FOG-Laptop cannot be pinged.

However, FOG-Desktop is also running Samba. Could that be it?

Lastly, I tried running the above init.d command on my laptop. I got the following.

administrator@FOG-Laptop:~$ sudo /etc/init.d/hostname.sh start
sudo: unable to resolve host FOG-Laptop

EDIT AGAIN - I googled that error above with sudo: unable to resolve host and I found a solved thread on the forums. Turns out my /etc/hosts file got matched up. Somebody posted in that thread saying what to do and all I had to do was change it accordingly, except use my hostname instead of the hostname in the example. Then I rebooted. I still couldn't ping FOG-Laptop, but I didn't have that error anymore. So I ran sudo apt-get install samba. BAM, now I can ping FOG-Laptop from my XP computer. Why is this? What is it in Samba that triggers it to work like this?

---

