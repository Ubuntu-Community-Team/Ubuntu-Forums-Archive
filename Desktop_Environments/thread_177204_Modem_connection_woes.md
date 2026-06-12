---
title: "Modem connection woes"
date: 2006-05-15
forum: Desktop Environments
---

### Post by electroconvulsive on 2006-05-15
](*,)                                            ](*,)                                      ](*,)  
I have an ongoing problem with using an external modem to connect to the internet. The problem is that if I use the direct modem connection. The modem will connect to the internet but there I am totally unable to ping my ISP or use my browser. I am using an older US Robotics 56k Ext Fax Modem and it is connected at /dev/ttyS0 by serial connection.  

I have already disabled the IPV6 for my connection by adding /etc/modprobe.d/bad_list and adding the line "alias net-pf-10 off" to the document. I have used "ip a | grep inet6" to check that the IPV6 was turned off then I went into the about:config in firefox and disabled the IPV6 feature there. But still no joy.To add to all of this when I go into the network monitor properties for ppp0, which is the modem it returns a subnet mask of 255.255.255.255 which is not right under IPV4.

 Is there something else that I have missed here? I am starting to wonder if this is actually a winomdem (manufactured 1998 ) but considering the fact that it is actually dialling out I am wondering about that. I have been able to connect to the internet via a winxp machine that it is networked to but am pretty unhappy to have to let the firewall down on the windows machine in order for this machine to access the internet (I am using Sygate personal firewall pro and sygate home network to allow internet connection sharing but sygate home network does not generate a linux client floppy).

If anyone can help on this one I will really appreciate it.

---

### Post by corstar on 2006-05-16
I recenty had some joy getting my winmodem in a Toshiba A60 laptop working.:) 

I discovered that I could not connect to the net using Kppp or Gppp for whatever reason, but if I activated the /dev/modem by right clicking on the modem applet (in the gnome-panel), it worked perfectly.

Maybe you could give it a try..I hope it works for you.

---

### Post by electroconvulsive on 2006-05-16
Soory but that doesnt help. You see the modem is dialling out and according to the applet is connected. There is somenthing else internally which is making this happen. The properties for the modem say it is on a subnet of 255.255.255.255 which is not normal under IPV4. Thanks for the tip though.

---

### Post by electroconvulsive on 2006-05-17
Just to add to my own thread again agter doing a little more investigation on my system a few important facts have come up that may help this along.

1. The subnet mask I complained about is the same on my Win machine
2. I can ping and surf the net through this modem connection from the ubuntu live cd (hows that).
3. I can ping the IP address of my ISP's server but not the name of that server.
4. After running a port scan on the IP address awarded by ISP to my modem on connect it said that only a few ports were open. at the time of doing this scan Firestarter was disabled and unfortunately I know nothing about running iptables yet.  

Open Ports on my modem's IP address according to network tools port scan are:

111 - sunrpc
139 - netbios -ssn
445 - microsoft ds
538 - gdomap
899 - unknown
1174 - unknown
4801 - unknown

Well if iptables is supposed to be set up to have all ports open by default there must be something wrong with my iptables configuration. Hopefully someone can tell me where the config file is stored and how to write it. Obviously the loopback address (Io) is open because my OS is running properly and so is the local network (eht0) because im having no trouble with shared foders on the machine next to it.

---

