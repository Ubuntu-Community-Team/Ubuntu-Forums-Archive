---
title: "1505n wireless nightmare"
date: 2007-08-14
forum: Dell  Ubuntu Support
---

### Post by El Lance-O on 2007-08-14
Everything has worked (with some tweaking) no problem on my new 1505, and I love it completely.

BUT.

The wireless is really, really, annoying.

It's just to damn touchy! It won't connect unless the signal is above 50%, and sometimes when I connect to one, it either disconnects out of nowhere, or all of the other SSID's disappear in the Network Manager.

Is this because of the buggy pile of crap (at least in my opinion) that Network Manager is? Or is this because I am constantly going around town and connecting to different wireless connections, which bring several factors into consideration?

I mean, a laptop is meant to be taken around. And I'm pretty sure that the wireless card I have is n series, which is the best of the crop right now....right?

It sure doesn't perform like it.

So what should I do? Is there a fix that I didn't know about for the 1505n's?

Please help, this is pretty much my sanity at this point.

---

### Post by El Lance-O on 2007-08-15
Alright, here is an update to my problem so maybe I will get a response.

I never really paid attention to my wifi light, but I noticed that when in my Network Admin manager, and it says that it is connected, it just blinks rapidly, with breaks here and there.

If it really IS connected, it's bold with no blinking.

I also noticed that when I look at ifconfig when it isn't wanting to work, I get this:

```
ellanceo@TheThinGreyBox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:7C:2E:2A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:45:5A:3F  
          inet6 addr: fe80::21b:77ff:fe45:5a3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:320 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:116 (116.0 b)  TX bytes:10160 (9.9 KiB)
          Interrupt:16 Base address:0x2000 Memory:ecfff000-ecffffff 

eth1:avah Link encap:Ethernet  HWaddr 00:1B:77:45:5A:3F  
          inet addr:169.254.4.124  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x2000 Memory:ecfff000-ecffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14419 (14.0 KiB)  TX bytes:14419 (14.0 KiB)

```

What is 'UP BROADCAST MULTICAST?" And where the hell did Eth1:avah come from?

Please help me with this people, it took me about 2 and a half hours of trying to connect over and over again just to make this post. And my signal strength is close to 70%. This cannot be right.

---

### Post by El Lance-O on 2007-08-15
Oh, and I forgot to mention, but if the fact that I am using other people's wifi to go on the internet discourages you from wanting to help, please understand that I live in quite the dysfunctional home, and I do not have the money needed for the INSANELY expensive internet here in Alaska. And I really need this as it is vital for me to get my schoolwork done, as I am enrolled in an online school.

I only mention this because when I have had wifi problems in the past, people have refused to help me simply because it wasn't my router I was connecting to, and they don't support "wifi pirating"

Just someone please respond soon, I have an assignment due tomorrow and I really do not want to sit on the side of the road somewhere to get internet, like I am doing now.

---

### Post by Matthew Wiebelhaus on 2007-08-15
I dont know the problem but i wouldn't buy anything n right now because its unstable and one companies N frequency Could Be Different than another ones.

---

### Post by El Lance-O on 2007-08-16
Well it's a tad late for that.

And it worked just fine before, it has just been the last week or so that it has been dropping out. And I've noticed that it is pretty much ALWAYS with linksys routers.

I am just hoping it will resolve itself.

---

