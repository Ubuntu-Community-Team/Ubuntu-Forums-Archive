---
title: "Network Internet Connection?"
date: 2009-03-31
forum: General Help
---

### Post by Naz_Farooq on 2009-03-31
Hi All,
I have been facing a serious problem for last few days.
My laptop is connected to a network in the office. When I boot from WindowsXP, internet is working very well and I can easily access to the server because I need to get files from the server.
But if I boot from ubuntu 8.10, automatic connection is established with "eth0" and the network light is also blinking but when I start firefox or any other browser, it does not browse as no connection is established. I cannot access to the server even as it shows "unable to mount the location"
I am much worried about it because few days ago it was working very well. I completed my updates 3 days ago after 17 days. I need to upgrade my software and ubuntu 8.10 to jaunty 9.04 but it seems impossible without internet connection.
Can any one help me please.
Thanks in advance.

---

### Post by iaculallad on 2009-03-31
Can you ping your router/server from your 8.10 laptop?

---

### Post by Naz_Farooq on 2009-03-31
Yes, I can ping the server only. The automatic settings are the same as it was earlier when there was no problem at all.

---

### Post by iaculallad on 2009-03-31
If its a kernel update which you had previously mentioned, try rolling it back to the previously installed working kernel. You can use the Synaptics Package Manager to do that task for you.

---

### Post by pgmer6809 on 2009-03-31
> **Naz_Farooq said:**
> Hi All,
I have been facing a serious problem for last few days.
My laptop is connected to a network in the office. When I boot from WindowsXP, internet is working very well and I can easily access to the server because I need to get files from the server.
But if I boot from ubuntu 8.10, automatic connection is established with "eth0" and the network light is also blinking but when I start firefox or any other browser, it does not browse as no connection is established. I cannot access to the server even as it shows "unable to mount the location"
I am much worried about it because few days ago it was working very well. I completed my updates 3 days ago after 17 days. I need to upgrade my software and ubuntu 8.10 to jaunty 9.04 but it seems impossible without internet connection.
Can any one help me please.
Thanks in advance.

Are you accessing the network via a wired or wireless connection?
If wired then ::
You seem to be experiencing the completely unsolved problem with Hardy and later distros where the wired network does not work. The link comes up fine, but when you try to assign an IP address (manually or via DHCP) it fails. Hence Network Manager thinks the link is up, but it is unusable.
(check this by running ```
ifconfig eth0
``` from the cmd line. You should see that the link is up, but if you look carefully you will see that there is no IP address assigned.

Many people might give you 'workarounds' that involve Network Manager, but Network Manager is not the problem. The problem is at a much more basic level -- I think at the driver layer, but maybe the layer above that.

The only solution I have found after a YEAR of complaining about this is to use the wireless on the laptop, if that is an option for you.
Also I would not count on it being fixed in Jaunty Jackalope either since there has been absolutely NO acknowledgment of the problem from the Ubuntu team.
:(
I have this problem with 3 different brands of ethernet chip on two desktops and one laptop. I have sent the error messages to Ubuntu but NOTHING has come back.
And they have the NERVE to put Gutsy at end of life when it is the last version of Ubuntu that I know of that works.

Good luck you will need it.

pgmer6809

---

### Post by Naz_Farooq on 2009-03-31
Thank You Very Much. So you also have been facing the same problem for a long time. But the problem is that I dont have wireless connection in the office. I do have wireless in my laptop, but no wireless connection in the office. Its strange that I faced the same problem 20 days ago that internet was not working but 2 days ago it suddenly started working and everything was fine and I thought that the problem is solved but could not understand how. But I was satisfied. Yesterday, I tried to connect my laptop with a wired network to access server and internet but I was shocked after having the same bloody problem. It was agonizing when I needed and it was not accessing. Anyways, if you find any solution, please let me know again.
Thanks

---

