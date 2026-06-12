---
title: "ping not working?"
date: 2012-04-27
forum: Desktop Environments
---

### Post by MG2R on 2012-04-27
I'm using Ubuntu 10.04 LTS as a home storage server. I have a script that pings to my main pc (running Windows 7 64 bit, unfortunately) and if the pc is available, it  powers up my raid array. Otherwise, the raid array is put in standby mode.

Yesterday, I reinstalled my Windows OS. Since then, the script does not work anymore. I did some debugging and apparantly, I cannot ping to the pc anymore. I checked the IP-adres to make sure I was pinging to the right adres, but when i run 'ping 192.168.1.151', none of my packets are received by the pc.

Does anyone know how to solve this?

---

### Post by papibe on 2012-04-27
Hi MG2R.

By any chance the Windows's LAN IP changed?
Why are you using the IP instead of the name?
Have you check your Windows configuration so the ping functionality is [enable]("http://answers.microsoft.com/en-us/windows/forum/windows_7-networking/how-to-enable-ping-response-in-windows-7/5aff5f8d-f138-4c9a-8646-5b3a99f1cae6"), and open in the [firewall]("http://www.sysprobs.com/enable-ping-reply-windows-7")?

Just a few thoughts.
Regards.

---

### Post by MG2R on 2012-04-29
> **papibe said:**
> Hi MG2R.

By any chance the Windows's LAN IP changed?
Why are you using the IP instead of the name?
Have you check your Windows configuration so the ping functionality is [enable]("http://answers.microsoft.com/en-us/windows/forum/windows_7-networking/how-to-enable-ping-response-in-windows-7/5aff5f8d-f138-4c9a-8646-5b3a99f1cae6"), and open in the [firewall]("http://www.sysprobs.com/enable-ping-reply-windows-7")?

Just a few thoughts.
Regards.

The IP of my laptop is a static one, given by my router (my router is set up to reserve an IP-address for my laptop). I always use IP's :p.
Apparantly, my firewall was blocking the pings :s Thanks!

---

