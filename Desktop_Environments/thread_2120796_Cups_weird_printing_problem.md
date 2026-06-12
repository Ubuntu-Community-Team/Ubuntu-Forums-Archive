---
title: "Cups weird printing problem"
date: 2013-02-27
forum: Desktop Environments
---

### Post by dustinr on 2013-02-27
Ubuntu 12.04 64bit
Cups 1.5.3
Printer: Zebra 2030

I know that cups in ubuntu 12.04 has a-lot of problems for many people. I have tried running updates for this release, but my problem still happens.

I can get this printer working and printing, but every so often it will cut the paper early. Sometimes when this happens it causes the printer to require a power cycle in order to print again. This is not consistent and I can not find a pattern of this behavior. It will happen anywhere from 20 prints to 300 prints.

Even the problem it self is not consistent. Some times it will cut the paper early and still be able to print ( the next page has text from the previous page ). Sometimes it will even not cut the paper and print two jobs on the same sheet. And sometimes the page will stop ejecting and stay in the printer, requiring a power cycle.

The best luck I have had to prolong this issue from occurring is doing these commands: 
```
sudo lpadmin -p Swecoin_AB_TTP_2030 -R usb-unidir-default
sudo lpadmin -p Swecoin_AB_TTP_2030 -o usb-no-reattach-default=true
    cycle power on printer
```

But the problem will eventually happen again. 

Does anyone have some advice or suggestions for me? 

I would like to downgrade cups to 1.4.4 ( ubuntu 10.10 ) because I dont seem to have problems with that one, but the downgrade process is being difficult with me. If anyone has some hints and suggestions to downgrade cups please let me know.

I have checked syslog and cups error logs with no real indication of what is causing this. I did notice the printer usb would dissconnect and then reconnect after every print. I resolved this by performing the commands I listed above. But still, The problem still occurs.
Thanks!

---

### Post by dustinr on 2013-03-01
*bump*

---

