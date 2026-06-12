---
title: "Kppp tool in Kubuntu"
date: 2005-09-06
forum: Desktop Environments
---

### Post by OBnascar on 2005-09-06
I have Kubuntu right now set up on a dual boot with Linspire five-0. I set up the Kppp tool in Kubuntu with the same info as I did in Linspire . 

But, my problem in Kubuntu is, it dials up fine but then freezes at the: [COLOR=Blue]logging on to network.[/COLOR]When I lift up a telephone on the line it has a dial tone. To me that would indicate that it has hung up for some reason. 

Has anyone ever had this happen and knows what the solution is, or would anyone else know what the fix would be ? Maybe it is just a simply thing as re-adjusting some setting in configuring. 

My modem is a [COLOR=Red]"Actiontec", 56k, v.90 external serial port.[/COLOR]

Any suggestions or comments are welcome.

---

### Post by djib on 2005-09-07
Hello,
I don't know if this can help you but I know that kppp has some problems with devices such as /dev/modem.
If it is what you have selected, you should select the 'real' device, not a link. What you can do is launch linspire, open a terminal and type in :

```
ls -la /dev | grep modem
```

Now you should get a line showing what device /dev/modem is pointing to.
You can then boot under kubuntu and input that device in kppp instead of /dev/modem

I hope this will help.

---

### Post by OBnascar on 2005-09-07
[QUOTE=djib]Hello,
open a terminal and type in :

```
ls -la /dev | grep modem
```

Now you should get a line showing what device /dev/modem is pointing to.
You can then boot under kubuntu and input that device in kppp instead of /dev/modem

I hope this will help.[/QUOTE]

Thanks "djib", I'll give it a try and post back.

---

### Post by OBnascar on 2005-09-07
Yes djib, that did not work for me, still will not connect to the network.

I did try though to use the documentation that I had for setting up ppp in a terminal.

After I set ppp up in the command line, when I run "pon", I get this:[COLOR=Red]**/user/sbin/pppd: in file /ect/ppp/peers/provider:  unreconized option '/dev/modem'**[/COLOR]

Can someone please tell me what unreconized option '/dev/modem' means ?

When I did use the Kppp tool I always got this error: [COLOR=Red]**/etc/resolv.conf is missing or can not be read**[/COLOR]. That file does exist and has read & write permission but does not have exec. Does it need exec ? If so I am not able to figure out how to change it because the options are grayed out.  Does the ppp I set up in the terminal also use this file ?

Need more help !

---

