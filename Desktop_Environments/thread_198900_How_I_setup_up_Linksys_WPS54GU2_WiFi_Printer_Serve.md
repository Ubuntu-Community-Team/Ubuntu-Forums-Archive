---
title: "How I setup up Linksys WPS54GU2 WiFi Printer Server"
date: 2006-06-17
forum: Desktop Environments
---

### Post by JackD on 2006-06-17
I have a Linksys WPS54GU2--which is a great wi-fi print server. It's not as well documented for Linux as it is for Windows, but it works fine with CUPS.

[LIST]
[*]To begin working with the WPS54GU2, you have use a **wired** cable connection.

[*]After it's been wired into a local hub/switch then you can run the easy configuration program on a networked client--which only runs on Windows


[*]Do all the configurations listed in the guidelines and give it a fixed IP address

[*]Now, use a browser (you can put away the Windows system, you don't need it any longer) and go to the IP address that you set in the previous step

[*]Log in and go to the PRINTER section where you'll see an input for "Printer Model"--give it a name to use in the URI (so, don't put in spaces). Save.

[*]Ok, you're ready to set up CUPS and create an IPP URI that will be something like ipp://192.168.1.4/LASERJET1200. Obviously, you use your own IP number and the name of the printer that you entered with the browser configuration.
[/LIST]

That's it.

---

### Post by Ed Armstrong on 2006-07-24
Please can anyone help me set up my Linksys Wps54GU2 with my Lexmark P4350 all in one printer - Linksys say that they have problems getting it to work with all in ones. They suggest that I obtain a generic Lexmark printer driver - help please?

Ed:-D ](*,)

---

