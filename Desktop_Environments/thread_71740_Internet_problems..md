---
title: "Internet problems."
date: 2005-10-04
forum: Desktop Environments
---

### Post by abdulisse on 2005-10-04
Hi,
    I just installed Hoary on my laptop which i will provide the specs for below and the installation went good. I noticed during the install though that at one point when it was "confiquring connection" or something, i did not get a good look went too fast, the end result was a "Fail", and it gave me options. I click on "setup connection later".

So the rest of the installation went good and everything was installed and confiqured. It booted and i logged in. Everything seemed perfect and okay. Then i pluged in my network wire which is connected to a cable internet modem. 
[img]http://www.jplistings.ca/include/gdthumb.php?pass=../photos/forsale/individual/104188_19827078.jpg&mw=120[/img]

The little computer screens at the top were blinking and i thought it was all good. So i launched Firefox and typed in 'google.ca' which didn't do anything.
I got the usual message of 'cannot find, check name and try again'.

Can anyone help me on setting up my connection? Please and thank you in advanced.

Computer specs : [http://www.epinions.com/pr-Laptops_Hewlett_Packard_Compaq_Presario_2100US_Laptop_DB954A_ABA/display_~full_specs](http://www.epinions.com/pr-Laptops_Hewlett_Packard_Compaq_Presario_2100US_Laptop_DB954A_ABA/display_~full_specs)

---

### Post by cwaldbieser on 2005-10-04
[QUOTE=abdulisse]Hi,
I just installed Hoary on my laptop which i will provide the specs for below and the installation went good. I noticed during the install though that at one point when it was "confiquring connection" or something, i did not get a good look went too fast, the end result was a "Fail", and it gave me options. I click on "setup connection later".
So the rest of the installation went good and everything was installed and confiqured. It booted and i logged in. Everything seemed perfect and okay. Then i pluged in my network wire which is connected to a cable internet modem. 
[img]http://www.jplistings.ca/include/gdthumb.php?pass=../photos/forsale/individual/104188_19827078.jpg&mw=120[/img]
The little computer screens at the top were blinking and i thought it was all good. So i launched Firefox and typed in 'google.ca' which didn't do anything.
I got the usual message of 'cannot find, check name and try again'.
Can anyone help me on setting up my connection? Please and thank you in advanced.
Computer specs : [http://www.epinions.com/pr-Laptops_Hewlett_Packard_Compaq_Presario_2100US_Laptop_DB954A_ABA/display_~full_specs](http://www.epinions.com/pr-Laptops_Hewlett_Packard_Compaq_Presario_2100US_Laptop_DB954A_ABA/display_~full_specs)[/QUOTE]
A couple things to try:
1) System -> Administration -> Networking -> Network Settings Dialog -> select eth0 connection.  Disable then re-enable.  Are you connected?

2) In the terminal, try running this command:
```

$ sudo dhclient

```
It will try to automatically connect to the Internet for you.

3) See if you can ping an IP address like
```

$ ping 68.142.226.38

```
If you can ping the IP address, but not the name ([www.yahoo.com)](www.yahoo.com)), then you might just have to set your DNS server(s).

---

