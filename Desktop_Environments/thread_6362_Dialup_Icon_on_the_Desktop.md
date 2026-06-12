---
title: "Dialup Icon on the Desktop"
date: 2004-11-27
forum: Desktop Environments
---

### Post by elder68 on 2004-11-27
Being new to Ubuntu I am connecting to the internet via Computer - systemconfiguration- networking. Which seems a bit awkward to me and I have to supply a password along the way. Is there a way of putting a dialup icon on the desktop which you just click on and it begins dialing. 

Fortunately I am using an external modem and I can see by the lights when it is connected and I suppose this is a bit redundant in a way, but all other linux systems that I have used show the activity of the connection on the toolbar somewhere. 

Any help would be appreciated,

Bill.

---

### Post by calvinpriest on 2004-11-28
If you right-click on an empty space on top panel, you can select "Add to Panel" and then choose "Modem Lights".  This will give you an icon (a rather bulky, awkward one, actually) that will show status and you can click on to make a connection.

As for an icon on the desktop, you could drag and drop the Networking icon there, but you'll still have to click on the modem, etc., before it begins dialing.

---

### Post by Nikola on 2004-11-28
[QUOTE=calvinpriest]If you right-click on an empty space on top panel, you can select "Add to Panel" and then choose "Modem Lights".  This will give you an icon (a rather bulky, awkward one, actually) that will show status and you can click on to make a connection.

As for an icon on the desktop, you could drag and drop the Networking icon there, but you'll still have to click on the modem, etc., before it begins dialing.[/QUOTE]
 I recomend Gnome-ppp, very nice dial-up app.

---

### Post by elder68 on 2004-11-29
Thank you Nikola and CalvinPriest, I will try the Gnome-PPP.
Got the Medem Ligts on the task bar OK but it would not connect or disconnect. Likely the PON and POFF commands that Modem Ligts has as a default are not the ones the modem is looking for. 

Bill.

---

### Post by zenwhen on 2004-11-29
Edit the file /etc/group and put your username directly after:

```
dip:x:30:
```

Your user will then be able to make connections with your modem.

---

### Post by elder68 on 2004-11-30
[QUOTE=zenwhen]Edit the file /etc/group and put your username directly after:

```
dip:x:30:
```

Your user will then be able to make connections with your modem.[/QUOTE]

I did the above and still could not connect from the Modem Lights applet. Tried "wvdial" it tells me that it cannot open /dev/modem "no such file or directory. However, if I "sudo wvdial" it will dial out OK.

If I enter "pon" as the command line either as a simple user of "sudo pon" i get:
"/usr/sbin/ppd: in file /etc/ppp/peers/provider: unrecognized option '/dev/modem'

If I set the modem up under "System Configuration" "Networking" the modem works OK and will connect to the internet. I find this latter method of connecting to the internet a bit on the "klunky" side, if I may say so. Most other distros I've used, connecting to the internet has been a simple click on the desktop.

Any help would be appreciated,

Bill.

---

### Post by zenwhen on 2004-12-01
Did you have gnome-ppp search for your modem?

---

### Post by zenwhen on 2004-12-01
See the image below:

1) I click this to connect to the the internet. It's a launcher I made with an icon that coems with Ubuntu to launch gnome-ppp.
2) This comes up when I click that. The setup button there brings up...
3) ... and this is where you will find the....
4) ...detect button that will configure your modem for you. Then you just need to provide your ISP information in (2) and hit connect. If you have added your user to the dip group you will be able to just hit the button I showed in (1).

I hope this works for you.

---

### Post by elder68 on 2004-12-01
[QUOTE=zenwhen]Did you have gnome-ppp search for your modem?[/QUOTE]

I don't seem to have gnome-ppp, or at least I can't find it.

Bill.

---

### Post by zenwhen on 2004-12-01
[QUOTE=elder68]I don't seem to have gnome-ppp, or at least I can't find it.

Bill.[/QUOTE]

sudo apt-get install gnome-ppp

---

### Post by krietor on 2004-12-05
Couldn't find package gnome-ppp - where is it? 
Not in warty anywhere.

---

### Post by zenwhen on 2004-12-07
[QUOTE=krietor]Couldn't find package gnome-ppp - where is it? 
Not in warty anywhere.[/QUOTE]

```
wget http://zenhardwhere.com/files/gnome-ppp_0.3.17-2_i386.deb

sudo dpkg -i gnome-ppp_0.3.17-2_i386.deb
```

Enjoy. :)

---

