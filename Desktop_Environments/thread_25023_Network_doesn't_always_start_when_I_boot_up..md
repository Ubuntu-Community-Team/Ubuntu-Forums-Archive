---
title: "Network doesn't always start when I boot up."
date: 2005-04-09
forum: Desktop Environments
---

### Post by Jerrac on 2005-04-09
I just updated Kubuntu today, hoping that this problem would go away. It hasn't. When I boot into Kubuntu, my network doesn't always start. I have to go into the Control Center and restart the network. Any ideas? 

Oh, and sometimes when I try to into Administrator Mode in the Network Settings, it just sends me back to the start page of the Control Center after I enther my password. Why would it do that?

Thanks for all your help!

---

### Post by Jerrac on 2005-04-11
[QUOTE=Jerrac]I just updated Kubuntu today, hoping that this problem would go away. It hasn't. When I boot into Kubuntu, my network doesn't always start. I have to go into the Control Center and restart the network. Any ideas? 

Oh, and sometimes when I try to into Administrator Mode in the Network Settings, it just sends me back to the start page of the Control Center after I enther my password. Why would it do that?

Thanks for all your help![/QUOTE]
Well, I got the admin mode working fine. But it still doesn't do the network all the time. Anyone?

---

### Post by russnh on 2005-04-12
I'm having similar problems on my Dell Inspiron 8000 laptop. The network connects, but takes about five minutes to display a web page. I'm obviously not looking in the right place to solve this problem.

>Oh, and sometimes when I try to into Administrator Mode in the Network >Settings, it just sends me back to the start page of the Control Center after I >enther my password. Why would it do that?

Same here. How did you solve that?

---

### Post by Jerrac on 2005-04-12
[QUOTE=russnh]I'm having similar problems on my Dell Inspiron 8000 laptop. The network connects, but takes about five minutes to display a web page. I'm obviously not looking in the right place to solve this problem.

>Oh, and sometimes when I try to into Administrator Mode in the Network >Settings, it just sends me back to the start page of the Control Center after I >enther my password. Why would it do that?

Same here. How did you solve that?[/QUOTE]

Well, once I get it to connect to the net, it works fine. But it just took me 10 minutes to get it to connect... grr...

As for the admin mode, just go into the menu editor and click the Control Center icon, then tell it to run as different user, and put root into the box. That way it asks for your password everytime you start it up.

---

### Post by Jonathan2007 on 2005-04-12
Check my response in [this](http://ubuntuforums.org/showthread.php?t=25249)  thread. It talks about my problems with the control panel too. The admin mode seemed to work for a while and then it just sent me back to another page. Now I can get it to work again. I don't know. It is crazy. The devs have got some work cut out for them.

P.S. I believe somewhere I saw a setting to start the network on bootup. You might try that and see if it helps.

---

### Post by russnh on 2005-04-13
[QUOTE=Jerrac]Well, once I get it to connect to the net, it works fine. But it just took me 10 minutes to get it to connect... grr...

As for the admin mode, just go into the menu editor and click the Control Center icon, then tell it to run as different user, and put root into the box. That way it asks for your password everytime you start it up.[/QUOTE]
 Thanks for the thread pointer, but it doesn't seem to work for me. (I'm still learning lots about Linux so I may have missed something...)

---

### Post by sonny on 2005-04-13
> I just updated Kubuntu today, hoping that this problem would go away. It hasn't. When I boot into Kubuntu, my network doesn't always start. I have to go into the Control Center and restart the network.

I'm a not so newbe in Linux, and I had the same problem with my network, it took me about 15-20 min to get it running, and I realized it was my on-board network card, I had a MSI VIA series mobo, and the VIA network included in my mobo is not supported in Linux (as for my knowloedge); MSI drivers required me to create a new module and recompile my kernel  ;-) , the way I solved it was buying an old network card with a realtek chipset (it seems that realtek is well supported in linux). Have you tried using an other distro?

If you can't get it to run rightly in an other distro then you'd better do some google for your network chipset and then see if it's supported in Linux, if it doesn't then your'e about to spent $5 in an old-second-hand network card.

---

