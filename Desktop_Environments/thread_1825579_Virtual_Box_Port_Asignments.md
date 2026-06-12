---
title: "Virtual Box Port Asignments"
date: 2011-08-15
forum: Desktop Environments
---

### Post by Babyd3k on 2011-08-15
I need to assign 19 usb ports to 9 different virtual copies of Win XP so I can slim down a data collection set up from 10 computers to 1. The reason I have to assign all these ports is because the usb devices I am using are literal clones of each other and there is no way to pick one device from the pile and it is very important that every device gets routed to the correct Win install or all the data will be ruined. 

Now here is what I have, I have a default install of 10.04 it has the default install of the newest virtual box from sun downloaded last week. There are 9 cloned VM's of Win XP Pro all set and ready. I have figured out how to assign the 4 usb ports on the motherboard. What I had to do to make those 4 work is as follows

 I issued the: 

VBoxManage list usbhost

command the output looks like this:
Address:            sysfs:/sys/devices/pci0000:00/0000:00:04.1/usb1/1-4//device:/dev/vboxusb/001/009


In a vbox forum post I was told that I find:
Address:            sysfs:/sys/devices/pci0000:00/0000:00:04.1/usb1/1-4

Then subtract 1 from the end and that would make this port 3 so I go into the vbox control panel for usb make a filter and tell it to send port 0003 to whatever v machine I'm in and it works slick. 

FYI: you can just put 3 but vbox will add the leading zeros

Now the problem starts here. I need 19 usb ports, I only have 4 on the motherboard so I need to know the syntax for other controllers or usb hubs. When I plug into a 5 port controller card I get this output 

Address:            sysfs:/sys/devices/pci0000:00/0000:00:04.0/usb5/5-5//device:/dev/vboxusb/005/002

Anyone have any ideas at all on how I turn this into a port number?

---

