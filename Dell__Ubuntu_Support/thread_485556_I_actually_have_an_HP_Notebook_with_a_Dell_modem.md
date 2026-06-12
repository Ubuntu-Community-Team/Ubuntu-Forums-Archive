---
title: "I actually have an HP Notebook with a Dell modem"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by krizzlekong on 2007-06-27
Hey, I don't know too much about computers, so try to keep your response in Lamen's terms. I don't have a Dell PC, but I have an HP Notebook with a Dell Modem built inside. Normally, on my Windows Vista OS, I can connect to other peoples networks wirelessly, but I can't when I run Ubuntu OS. My friend told me it's because my computer has a Dell modem. Is this true? If not, how can I get it to work?:(

---

### Post by mike999999 on 2007-07-01
Modems are usually not OEM specific. 

You probably have a WinModem which uses the cpu to do the work.  Linux and Winmodems don't get along all the time.

---

### Post by khedron on 2007-07-01
I don't think it is a WinModem, although the root cause of the problem is similar. Wireless under Linux is currently quite tricky. There should be a lot of howtos for this, though - just search the forums for "wireless" or even Google for "wireless linux".

I haven't done it personally, so I can't recommend one, I'm afraid.

The reason that wireless is tricky is that basically every vendor of wireless cards doesn't make Linux drivers, so until an Open Source developer writes one for your specific model (or chipset) you will have to "hack" the system, so to speak. This usually involves using the Windows driver provided with the card, with a wrapper to make it work on Linux. (The technical name for the wrapper is NDIS or something, I am a bit hazy on the details.)

I just found a link that might help you:
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by mike999999 on 2007-07-02
Oops. 

Missed the whole wireless thing. 

Let's clarify: 

Modem is your dial-up modem.(?)
Network Card (wlan) is for your wireless connection. 

Finally, do you mean that your router has a Dell logo on it?

It may also help if you post the output of iwconfig.

---

