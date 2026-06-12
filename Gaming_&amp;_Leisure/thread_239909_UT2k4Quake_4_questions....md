---
title: "UT2k4/Quake 4 questions..."
date: 2006-08-20
forum: Gaming &amp; Leisure
---

### Post by darundal on 2006-08-20
Hi, couple of questions...
UT2k4:
-How do I enable anisotropic filtering and antialiasing (please, oh god of clear textures respond)
-Everytime I try to play online, it keeps trying to query the master server. No problem, except it just keeps on doing this. It never even gets to letting me go to online play, It isn't frozen, I can go back in the menu and play single player, but still. Running version 3369.

Quake 4:
-No matter what I set the quality to, the textures look really lo-res. Everything else works perfectly. Any ideas? (forgot which version)

---

### Post by User_Program on 2006-08-20
Give alittle more info on your hardware video card and if you installed the drivers for it yet.   

As for constant connection of the master server, do you have a firewall software or router?  Ports may need to be opened 

List of UT2k4 ports
Unreal   Tournament server
IN    UDP 7777 (default gameplay port)
IN    UDP 7778 (server query port
IN    UDP 7779+ (UDP 7779+ are allocated dynamically for each
                        helper UdpLink objects, including UdpServerUplin
                        objects. Try starting with 7779-7781 and add
                        ports if needed.))
IN    UDP 27900 (server query, if master server uplink is enabled.
                         Some master servers use other ports, like 27500)
IN    TCP 8080  
(Port 8080 is for UT Server Admin. In the [UWeb.WebServer] section of the server.ini file, set the ListenPort to 8080 (to match the mapped port above) and ServerName to the IP assigned to the router from your ISP.) 

You will not need all of these just the first 4 to play the 4 being to view the the server list.

Other suggestions for AA and textures.  On Nvidia cards there are setting you can change by using nvidia-settings  just type that in the terminal.

---

### Post by darundal on 2006-08-20
x850pro (FGLRX driver installed)
Have a firewall, but never had to open ports in windows, but will give it a try...

---

### Post by User_Program on 2006-08-20
I can't help you out in the ATI area. But I would think that ati has somthing similar to nvidia.  I also would think that graphic and performance would be compairable, hopfully someone will chime in that knows more.

I'm still not sure if your running a software firewall or hardware one.  If your running firestarter (software) I have had beter luck runnning that then any other software firewall.  Also just as a test to eliminate that it's the firewall try turning it off and connecting to ut2k4 then you will know if it's that for sure. (should have said that in my first post sorry)

---

### Post by darundal on 2006-08-20
Never actually opened the ports, just tried to play online one last time and it seemed to magically worked...any idea about the quake4 texture thing though?

---

### Post by User_Program on 2006-08-21
The only thing that comes to mind is a permission issue.  
There is a dir  /home/YOURUSER/.quake4  (it is hidden so in a file browser View>Show Hidden.  It may have only root permissions preventing you from chainging your config file to the settings you want. To change it  

It the Terminal
> sudo chmod 755 /home/YOURUSER/.quake4

Changing YOURUSER to the user you want to run q4.

That is the only thing I can think of ATM.  I'll post again if I think of anything else.

---

