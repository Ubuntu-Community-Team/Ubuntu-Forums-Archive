---
title: "network ip address"
date: 2009-04-26
forum: General Help
---

### Post by krishna1650 on 2009-04-26
hello friends,
i want to IP address of my network. i have used "ifconfig -a" command. it shows inet addr:192.168.1.2. but i want to know actual IP address provided by the ISP( internet service provider) by command. is there any such command?

thanks for help.

---

### Post by marcw on 2009-04-26
> **krishna1650 said:**
> hello friends,
i want to IP address of my network. i have used "ifconfig -a" command. it shows inet addr:192.168.1.2. but i want to know actual IP address provided by the ISP( internet service provider) by command. is there any such command?

thanks for help.

Try this in a browser:
[http://whatismyip.com/](http://whatismyip.com/)

---

### Post by lovinglinux on 2009-04-27
```
wget www.whatismyip.com/automation/n09230945.asp -O - -q
```

---

### Post by krishna1650 on 2009-04-27
> **lovinglinux said:**
> ```
wget www.whatismyip.com/automation/n09230945.asp -O - -q
```

thanks for reply. though it returns IP address, but it is using  [www.whatismyip.com](www.whatismyip.com). is there any command or way to get IP address without taking help from [www.whatismyip.com](www.whatismyip.com).

once again, thanks for the information.

---

### Post by lovinglinux on 2009-04-27
> **krishna1650 said:**
> is there any command or way to get IP address without taking help from [www.whatismyip.com](www.whatismyip.com).

I also would like to know  8)

---

### Post by Halito77 on 2009-04-27
> **krishna1650 said:**
> hello friends,
i want to IP address of my network. i have used &quot;ifconfig -a&quot; command. it shows inet addr:192.168.1.2. but i want to know actual IP address provided by the ISP( internet service provider) by command. is there any such command?

thanks for help.


 Your IP comes up as 192.168.xxx.xxx because you are located behind a router.  The only way to obtain the real IP address that I know of is to enter the router(other than obtaining it from the net). This is because its the router that is the hardware that actually establishes the connection with your ISP and hence has the IP you are looking for.    

You should be able to gain access to your router using firefox etc.  The access/gateway address can be found in your network settings (or using the route command where it comes up under gateway and default), but it is typically 192.168.0.1, 192.168.1.1 etc...  and often requires a username and PW.  If you havent set one up it is likely to be the defaults values that you should be able to find on the net.      

The easiest way is still to obtain the IP through the net as mentioned above.     

If you on the other hand want your computer to have the real IP address you would have to set your router into bridge mode (but it then looses its router functions - hence only 1 computer can be on the net at a time) and set up a connection.     

Hope this clarifies the issue

---

### Post by krishna1650 on 2009-05-02
> **Halito77 said:**
> Your IP comes up as 192.168.xxx.xxx because you are located behind a router.  The only way to obtain the real IP address that I know of is to enter the router(other than obtaining it from the net). This is because its the router that is the hardware that actually establishes the connection with your ISP and hence has the IP you are looking for.    

You should be able to gain access to your router using firefox etc.  The access/gateway address can be found in your network settings (or using the route command where it comes up under gateway and default), but it is typically 192.168.0.1, 192.168.1.1 etc...  and often requires a username and PW.  If you havent set one up it is likely to be the defaults values that you should be able to find on the net.      

The easiest way is still to obtain the IP through the net as mentioned above.     

If you on the other hand want your computer to have the real IP address you would have to set your router into bridge mode (but it then looses its router functions - hence only 1 computer can be on the net at a time) and set up a connection.     

Hope this clarifies the issue

thanks for the information, it clarifies the issue.

---

