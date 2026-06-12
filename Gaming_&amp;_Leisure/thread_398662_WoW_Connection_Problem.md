---
title: "WoW Connection Problem"
date: 2007-04-01
forum: Gaming &amp; Leisure
---

### Post by Thinkaboutit on 2007-04-01
So i installed wow(and Burning Crusade) on windows just today played it all but 30 minutes ago and decided to see if i could just copy it(the folder) across to Ubuntu and run it under wine. It all seems to be running well except that when i try to login to wow it doesn't get passed the Connecting stage... It has once gotten onto Authenticating but no further. Oh and i can play Counter Strike over the Internet no problems...
This is what i get when i run it under terminal:

me@ubuntu:~$ sudo wine "c:\\WoW\\WoW.exe"
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub

Im running Wine 0.9.34 on Ubuntu 6.10 Edgy x86
I only just recently converted to linux so my skills are very limited, anyone had this problem or know how to fix it?

---

### Post by justin whitaker on 2007-04-01
Do you have a firewall running? 

There is an old error, #134, that might be causing you an issue:

> Problem #3 - Error #134, "Unable to associate local address with socket:...
The socket is already bound to an address, or the parameter is a listening socket".

You need to make sure your loopback interface is up, by running "ifconfig lo up" or "sudo ifconfig lo up".

I found that here:

[http://wow4wine.wetpaint.com/page/Known+Issues](http://wow4wine.wetpaint.com/page/Known+Issues)

Good luck.

BTW: you may want to consider installing WoW on your Ubuntu partition via Wine or Crossover Office. It runs well on Feisty and Edgy.

---

### Post by Thinkaboutit on 2007-04-01
> **justin whitaker said:**
> Do you have a firewall running? 

I did just recently install Gaurddog but found it a pain having to add all the programs that i wanted to access the Internet into its tables. So i uninstalled it.

> Problem #3 - Error #134, "Unable to associate local address with socket:...
You need to make sure your loopback interface is up, by running "ifconfig lo up" or "sudo ifconfig lo up".
This didn't seem to work wow still cant get past the Connecting stage.

I might just try installing wow on my Linux partition and see how it goes. I though i could just save time by dragging it across from windows, but maybe not.

Thanks anyway, ill probably be back if that doesn't work either. :P

---

### Post by Thinkaboutit on 2007-04-02
OK so i fully reinstalled World of Warcraft AND Burning Crusade and i still have the same problem, when ever i try to log in it never gets past Connecting.....
And if i leave it for a couple of minutes it ends up saying Disconnected from Server. 
I have search through tones of posts on other forums, i even tryed all the troubleshooting on wowwiki and nothing seems to work. Am i doing something wrong???
Please help!

---

### Post by MakLeod on 2007-04-13
/bump I have the same exact problem

---

### Post by vem0m on 2007-04-13
just to note with a basic wine install with minor help from [This guide]("https://help.ubuntu.com/community/WorldofWarcraft") also of note there is no need to run it as a root user so stop the Sudo stuff tho i will tell u u will need to copy wow to ur linux partition so that u will be able to write to ur wow folder which u cannot do if it is on an ntfs drive/partition....

---

