---
title: "Cannot View Server Outside Network"
date: 2008-04-02
forum: Desktop Environments
---

### Post by cantdrive55 on 2008-04-02
I just setup a Linux box running Ubuntu-7.10 to serve as my home's file server as well as being a Torrent box. I followed several different How-To's and got it all up and running. However I've run into a bump with the Apache server. I have it setup so that I can add/remove/seed torrents remotely when I'm not on my network at home. When I point my browser to [http://localhost](http://localhost) it works fine, also when I use my IP. But as soon as I leave my home network and try to use it say at school, nothing comes up. I type in my dedicated IP but nothing happens. I tried pinging it but it comes back as "Destination Net Unreachable" I asked a friend to try pinging it from his house and it seemed to work for him but he couldn't view the page. 

Any ideas as to what might have gone wrong? 

Thanks,
Jeff

---

### Post by mister_p_1998 on 2008-04-03
Is your Firewall blocking it?
Maybe your school is blocking that port, a lot of Schools/Colleges block Torrent ports, they do at my work.

---

### Post by cantdrive55 on 2008-04-03
I've made sure that my router has port 80 forwarded to the static ip set on the Linux box. For the school blocking I know its a possibility but they won't tell me definitively as I have asked before.

I have no-ip setup so when I point to that site it should just transfer me to the ip directly right? It doesn't and I can't ping that address either.

---

### Post by mister_p_1998 on 2008-04-05
If your router is your real-world IP, I dont see how you can connect to an address on your network,as it will be an internal IP - eg 192.168.1.2. You cant connect to an internal IP from the outside world. They can go out, but not vice-versa.

---

### Post by lavinog on 2008-04-05
> **cantdrive55 said:**
> I just setup a Linux box running Ubuntu-7.10 to serve as my home's file server as well as being a Torrent box. I followed several different How-To's and got it all up and running. However I've run into a bump with the Apache server. I have it setup so that I can add/remove/seed torrents remotely when I'm not on my network at home. When I point my browser to [http://localhost](http://localhost) it works fine, also when I use my IP. But as soon as I leave my home network and try to use it say at school, nothing comes up. I type in my dedicated IP but nothing happens. I tried pinging it but it comes back as "Destination Net Unreachable" I asked a friend to try pinging it from his house and it seemed to work for him but he couldn't view the page. 

Any ideas as to what might have gone wrong? 

Thanks,
Jeff

My school blocks all pings...can you ping google.com from school?

What kind of internet connection do you have at home?
Do you have a router..if so did you foward your ports?
Where did you get your dedicated ip address?
have you tried [www.whatismyip.com](www.whatismyip.com) from home?
it wouldn't make sense for your school to block port 80 since they would block all websites.
I think the problem is that your ISP is using NAT or you are using the wrong ip address.
I have heard of ISPs using NAT before which means that unless you can convince your isp to setup port fowarding on their system you won't be able to connect.

---

