---
title: "Unable to figure out how to connect to a router using Ubuntu"
date: 2009-02-25
forum: General Help
---

### Post by bllybb758 on 2009-02-25
Hello, im new to Ubuntu and i need to know why i cant connect to my router using the provided program. I have tried to fill out what i can but the things that throw me off are

BSSID
MAC
what type of WEP key

i tried to manually configure it but i got lost 

I am the Router admin so what ever you need me to set up for that. 

im using the following
Nublet guide (which doesnt help me)
D-Link DWL-120+
Ubuntu 8.10
WRT54G

---

### Post by Father Marc on 2009-02-25
> **bllybb758 said:**
> Hello, im new to Ubuntu and i need to know why i cant connect to my router using the provided program. 

What type of *ubuntu are you using? In Ubuntu (Gnome) the "provided program" is nm-applet and interfaces differently than Kubuntu (KDE 3.5/4) which uses a different applet/"provided program."

A little more info will help others help you.

+ Pax Christi +

---

### Post by bllybb758 on 2009-02-25
> **Father Marc said:**
> What type of *ubuntu are you using? In Ubuntu (Gnome) the "provided program" is nm-applet and interfaces differently than Kubuntu (KDE 3.5/4) which uses a different applet/"provided program."

A little more info will help others help you.

+ Pax Christi +

i dont know, how do i check?

Ubuntu because i got it off of ubuntu.com

---

### Post by Father Marc on 2009-02-25
Um, which desktop or Ubuntu did you install?

Ubuntu - Command Line
Ubuntu
Kubuntu
Xubuntu
Fluxbuntu

??

---

### Post by Father Marc on 2009-02-25
Okay... you are using GNOME as your desktop. That's important to remember for future posts on the forum.

Does your desktop have a little network icon in your task tray? Is that what you are using to connect to your wireless?

Does that program show your wireless network (through your router) as an option?

Pax

---

### Post by bllybb758 on 2009-02-25
> **Father Marc said:**
> Um, which desktop or Ubuntu did you install?

Ubuntu - Command Line
Ubuntu
Kubuntu
Xubuntu
Fluxbuntu

??

Ubuntu 8.04 32bit version Desktop edition


if that helps any

---

### Post by Father Marc on 2009-02-25
> **Father Marc said:**
> Okay... you are using GNOME as your desktop. That's important to remember for future posts on the forum.

Does your desktop have a little network icon in your task tray? Is that what you are using to connect to your wireless?

Does that program show your wireless network (through your router) as an option?

Pax

What type of security do you have enabled on your router? WEP (and what kind?), WPA?

The first thing I would do is disable your security on your router and see if you can connect then.

If so, then that is your speed bump. Then, reenable the security and use the program you've been using to "Edit Connections" and delete the connection that matches your network. Then, try to connect to that connection fresh and it will ask you for your security info.

I've found with WEP that sometimes the *kinds* of WEP are mixed up, (64 really provides 128, etc.) and so you might have to do a little trial and error.

Anyway, next step is get it connected WITHOUT security. THEN reenable it and work through that.

Pax

---

### Post by bllybb758 on 2009-02-25
> **Father Marc said:**
> What type of security do you have enabled on your router? WEP (and what kind?), WPA?

The first thing I would do is disable your security on your router and see if you can connect then.

If so, then that is your speed bump. Then, reenable the security and use the program you've been using to "Edit Connections" and delete the connection that matches your network. Then, try to connect to that connection fresh and it will ask you for your security info.

I've found with WEP that sometimes the *kinds* of WEP are mixed up, (64 really provides 128, etc.) and so you might have to do a little trial and error.

Anyway, next step is get it connected WITHOUT security. THEN reenable it and work through that.

Pax

WEP with 10 char's

ok the hex key didnt do the trick

---

### Post by bllybb758 on 2009-02-25
> **bllybb758 said:**
> ok the hex key didnt do the trick

a thought--> can it be because it isnt showing any connections it doesnt know where to go?

---

### Post by bllybb758 on 2009-02-25
is there a option on my router that connects it? because it doesnt show up on my pc

---

### Post by bllybb758 on 2009-02-26
Can someone reply please?

---

### Post by issih on 2009-02-26
First a qick glossary:

essid: this is simply the name of your network
mac address: a unique hardware code that identifies your networking hardware, this is NOT the same as an IP address.

So you get no list of detected wireless networks in the network manager applet?

If that is the case, then the chances are your wireless card is not loading its drivers correctly.

Can you please open a terminal and post the output from the following commands:

```
sudo lshw -C network
```
enter your login password when prompted

```
ifconfig -a
```

---

### Post by Father Marc on 2009-02-26
If the drop down list of "Wireless Networks" that appears when you click on the NetworkManager applet in your task tray doesn't include your network, then you have a problem.

Open a terminal prompt under Applications --> Accessories --> Terminal.

You should get a prompt that looks ends with a $. (That means you are acting as the regular user.)

If you are a newbie, then you should know that people will often give terminal commands for you to type by starting the line with ~$ to represent a user prompt and ~# to represent the "super-user" prompt. So...

~$ iwconfig

Type that... "iwconfig"... as a command, and then cut and paste the results for me to see in a post.

HINT: Use your cursor to highlight the text you want to cut and then right-click on it and select "Copy." Then just paste it like any other text.

Mine looks like this:

marc@ubuntu-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"Belkin_N_Wireless_AC5DE3"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1C:DF:AC:5D:E3   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-62 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Keep with it. We'll figure it out. And if you're new to Linux, you should know that it will be worth the trouble. You'll learn tons about computers, a little bit at a time... wireless troubles are probably THE most frustrating thing you'll come across, so don't give up.

+ Pax Christi

---

