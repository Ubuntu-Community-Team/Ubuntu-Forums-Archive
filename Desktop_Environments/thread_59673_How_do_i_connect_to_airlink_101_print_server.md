---
title: "How do i connect to airlink 101 print server?"
date: 2005-08-24
forum: Desktop Environments
---

### Post by arunsub on 2005-08-24
I have installed Airlink101 print server. It's connected to my wireless router. How do I install it in Ubuntu? If I select the network printer option, then should i select CUPS? If i select CUPS, then i have to enter the URL. I entered the print server's IP address in the URL, but when i print a test page it doesn't print. Can someone tell me how to configure the network printer?

Thanks.

---

### Post by planetmn on 2006-06-03
I was reading your other thread on this, since I have the same print server, and I was able to get it working.  Here's what I did:
Install a network printer using HP JetDirect and use the print servers IP address as the host.  Select the proper printer from the list and you should be good.

-dave

---

### Post by arunsub on 2006-06-04
I just came back from vacation. Give me few days. I'll give it a try and get back to you.

---

### Post by arunsub on 2006-06-07
[QUOTE=planetmn]I was reading your other thread on this, since I have the same print server, and I was able to get it working.  Here's what I did:
Install a network printer using HP JetDirect and use the print servers IP address as the host.  Select the proper printer from the list and you should be good.

-dave[/QUOTE]
I sent a private message with my print server configuration. Did you get that?

---

### Post by planetmn on 2006-06-07
from your PM:
[I]Hi,

I tried as you said. I got the following status when I entered the IP of my print server:
USB
Printer Name : PS-576903-U3
Printer Status : On line

I then went to the new printer setup. I selected network printer, selected HP JetDirect. I gave the printer IP 192.168.x.xxx as the host name (without [http://)](http://)). I left the port as 9100 (default). I then went to the next step and selected my printer name (Epson Stylus C80). I then gave Stylus-C80-network as the printer name and gave the ip in the location and clicked apply. I then gave a test page to print and nothing happened. Any idea?[/I]

Well, if you can see your printer status via your web browser, we know your network connection to it is good.  Have you tried printing a test page from the print servers web site?  I don't remember off the top of my head, but I assume that you've printed to this printer via the USB port in Ubuntu, correct?  Have you printed, via the print server, from any other computer?  Do you have the one or the three port version of the print server?  If the three port, make sure your printer is connected to port one and try again.  If the three port, you may need to (I don't know this because I have a one-port version) have an address something like 192.168.x.xxx/PS-576903-U3.  I'm not sure if each port gets it's own IP address, but probably not, in which case the IP address would only identify the server, and there would need to be a way to identify the printer itself.

-dave

---

### Post by arunsub on 2006-06-07
It's a 3 port print server. 2 LPT and 1 USB. My printer is connected to USB. I could print if I connect the printer directly. I could print a test page from the web browser through airlink configuration page, but I can't make it to work using the new printer connection. I tried all options and nothing worked.

---

### Post by planetmn on 2006-06-07
Ok, so I think the only thing that needs to be done now is somehow tell the print server which port/printer to use.

If you have access to a windows machine, can you do the following:
1) Under printers and faxes, right click on the printer and select properties
2) Go to the Ports tab and select configure port
3) What is listed for the Printer Name or IP address?

Unfortunately since i have the single port version it's hard for me to figure out what the next step would be, or what piece of information is missing.  You may want to look into zeroconfig networking (bonjour on windows, rendezvous on mac, with a quick search I couldn't find an easy way to do it in linux) since the server (at least mine) supports the protocol.

-dave

---

### Post by arunsub on 2006-06-08
I'll check that get back to you.

---

### Post by arunsub on 2006-06-09
printer name or ip address has ip address of the printer. 192.168.x.xxx. Port name is PS-576903-U3. I tried all options and nothing worked. I think I'll connect the printer directly for time being.

---

### Post by hedden on 2006-06-17
[QUOTE=arunsub]I have installed Airlink101 print server. It's connected to my wireless router. How do I install it in Ubuntu? If I select the network printer option, then should i select CUPS? If i select CUPS, then i have to enter the URL. I entered the print server's IP address in the URL, but when i print a test page it doesn't print. Can someone tell me how to configure the network printer?

Thanks.[/QUOTE]
Please read my artide:
[http://www.hedden.org/airlink.html](http://www.hedden.org/airlink.html)
Best regards,
Thomas Hedden

---

### Post by arunsub on 2006-06-18
After playing with the print server, it's not working even from Windows. I'll fix the windows problem and then work on your guide. Due to lack of time I'm not able to do that. It's a wonderful guide. Thank you.

---

### Post by dwybert on 2006-07-22
just managed to get ubuntu6 working with a Brother HL2040 Laser via an airlink APSUSB2 print server.

1) needed to install the HL-2040 driver from Brother
brhl2040lpr_1.1.2-3_i386.deb
also installed the CUPS driver (probably not needed)
cupswrapperhl2040_1.0.0-1_i386.deb

2) then logged into the APSUSB2 print server and gathered the server's IP address and from the printer status, got the printer name, in my case it was PS-576FB8-P1

3) under ubuntu admin, printing, I created a network printer, select Unix LPD
set hostname= <ip addr>, queue= PS-576FB8-P1
then set the manufacturer, and then the model driver HL2040

works fine

---

### Post by arunsub on 2006-07-24
I think I tried that and it didn't work. I'll give it a try once again.

---

