---
title: "Network printers in Gnome printing dialog do not work"
date: 2007-10-23
forum: Desktop Environments
---

### Post by eugenwinter on 2007-10-23
Hi there 
  I have posted this problem already once but got no reply. However, I thought that the problem 
may be solved in Gutsy - this was not the case. 
After upgrading my machine to Gutsy I found all our network printers exported by our CUPS server 
in the GNOME printing dialog. Unlike in Edgy now the "Print" button seems to work. Unfortunately no printing job is sent to the server after pressing "Print". I use Ubuntu 7.10 AMD64. 
I can print from the command line using "lp". Has anyone an idea what is going on here?

thanks
  Eugen

---

### Post by fdimmling on 2007-10-23
> **eugenwinter said:**
>  [...] I found all our network printers exported by our CUPS server in the GNOME printing dialog. Unlike in Edgy now the "Print" button seems to work. Unfortunately no printing job is sent to the server after pressing "Print". I use Ubuntu 7.10 AMD64. 
[...]

I had this problem when I had forgotten to enter the hostname of the server in the /etc/hosts file of the clients. The network printer appeared as ipp://fd-deskop:631/printers/Business-Inkjet-1200 but the name fd-desktop could not be resolved and printing was impossible. 

Friedrich

---

### Post by Macchi on 2007-10-23
I am experiencing similar problems with printing on Gutsy. Shared printers cannot be detected by other computers the network. Everything worked in Feisty. This occurs on a fresh instal .

The previous comment on the URL and hostnames may point at the root cause for this problem. We are thankful for hints on how to solve this situation.

(Such serious problems with printing are very disappointing because they limit seriously the ability to use Ubuntu for small and medium business enterprises. Network printing is very important. In this area I hope that stability is going to be prioritized before the addition of new functionality or sugar for the graphical interface.)

---

### Post by fdimmling on 2007-10-24
> **Macchi said:**
> I am experiencing similar problems with printing on Gutsy. Shared printers cannot be detected by other computers the network. Everything worked in Feisty. This occurs on a fresh instal .

The previous comment on the URL and hostnames may point at the root cause for this problem. We are thankful for hints on how to solve this situation.[...]

I am not shure if my posting is pointing to the root of your problem because it refers to basic network configuration which did not change from Feisty to Gutsy. But I sometimes forget this step when I install a new system on a computer. 
CUPS is broadcasting the printer with the name of the computer in the address. Every client has to know how to resolve this name by information from /etc/hosts, in my example a line

192.168.0.2 fd-desktop

In my case the printer server is also a scanner server and fax server. It is the only computer in the network which is assigned a fixed address by the router. Every client has a line in /etc/hosts to tell it how to reach the server.

Maybe it would be possible to automatically enter the name of the server into /etc/hosts if it is not yet there on configuring the printer.

Friedrich

---

### Post by froy02 on 2007-10-24
Configure your printers using firefox by using:
"http://localhost:631/".  When the printers window open click on printers and check if your printers are there. You can modify them by selecting modify printer and it would guide thru the setup.

Hope that helps.

---

### Post by eugenwinter on 2007-10-24
Thanks for all that responses. Unfortunately, non of the suggested solutions worked. I was maybe not precise enough in the description of my problem. 
I have a Debian Etch server with CUPS running on it. The server exports the printers on the web to the servers running on the Ubuntu clients. The network printers exported by the server are also 
visible on the Ubuntu clients. Have a look on the two screenshots attached to this post. The printers appear in the Printing setup dialog aswell as in the printing dialog itself. Printing works also from Firefox and from OpenOffice but not from Evolution or Evince or any other application that use the 
Gnome/Gtk printing dialog as show in file gnome_printing_dialog.jpg.
Unlike Feiste where the Print button was disabled for network printers you can press the button now but no job is sent to the server.
So I slowly do not think that this is a problem of a wrong setup but rather a problem in one of the Gnome or GTK libraries.

regards 
   Eugen

---

### Post by keenboy on 2008-03-31
Fresh install of ubuntu 7.10 and I have the same problem.

I can print from Openoffice, firefox, thunderbird etc etc But not evince!!

---

