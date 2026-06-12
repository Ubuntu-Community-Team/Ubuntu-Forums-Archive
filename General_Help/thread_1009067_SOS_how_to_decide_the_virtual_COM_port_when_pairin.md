---
title: "SOS: how to decide the virtual COM port when pairing pc and device"
date: 2008-12-12
forum: General Help
---

### Post by fablepan on 2008-12-12
Hi there, 

I am new to ubuntu. Now, I am trying to send and receive data between my laptop (IBM R60) with a device. I use a bluetooth adapter for my PC as it does not come with bluetooth. I have several questions when trying to construct the communication between them. Please note that I am using Ubuntu 8.10, which was updated from 8.04.

1) I am not sure whether I have succeeded in paring them. By using:
 
hcitool scan

I can find the address and name of the device. After that, I use:
sdptool browse 11:11:11:11:11:11 (11:11:11:11:11:11 is the address of device)

Then, PC tells me to input the passkey of the device, which is 1234 by default. 

After that, I right click bluetooth logo, and choose "browse files on device...", But I get an error:

Could not display "obex://[11:11:11:11:11:11]/".
Error: Service search failed
Please select another viewer and try again.

Also, I can not send files to device. when I did that, I met the following error: 
Error Occured
org.openobex.Error.ConnectionAttemptedFailed

So, I am not sure whether the pairing is successful. 

In addition, when I use: 

hcitool cc 11:11:11:11:11:11
Can't create connection: Operation not permitted

Then, I use:

sudo hcitool cc 00:80:98:E6:8C:93. Then, nothing happens. I then check the active connection by using: hcitool con. I get: 
connections:

It seems that there is no connections. Could anyone help me out of this. I have been tied here for long time. 

2). If I could finish the above step, Could anyone help to decide which COM port is used? The name of the Virtual COM port is very important for me to send command to device. 

Thanks for your time and help!!! 

:)

---

