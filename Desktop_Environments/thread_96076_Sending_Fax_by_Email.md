---
title: "Sending Fax by Email"
date: 2005-11-28
forum: Desktop Environments
---

### Post by larry on 2005-11-28
Dear All,
I heard it is possible to send fax by the internet (you write an email and you have it faxed), but I have never done before nor know which packages I should install.
Furthermore: is sending a fax this way as free as sending an email?
Regards

Larry

---

### Post by sophtpaw on 2005-11-28
[QUOTE=larry]Dear All,
I heard it is possible to send fax by the internet (you write an email and you have it faxed), but I have never done before nor know which packages I should install.
Furthermore: is sending a fax this way as free as sending an email?
Regards

Larry[/QUOTE]

I have the same question Larry. Could one of you pros out there please enlighten us?

thank you 

--
sophtpaw

---

### Post by anil_robo on 2005-11-29
I'm not a pro, just a noob like many of linux users. I had once subscribed to a paid service called e-fax where it was possible to send them an email and they shall have it faxed.

If you want to send fax for free, you shall have to use dial-up internet. I tried the same from windows XP on dialup line in an emergency, and sent around 30 pages of fax with cover page flawlessly. With Linux, I think there are two programs you may try out. One is hylafax and the other is efax. The first program (hylafax) doesn't exist when I try to install it from the official repositories. efax installs however. But I can't try it out right now because I'm shifting house and dont have access to phone line. Maybe you can install efax. The steps:
1. Applications--> Accessories--> Terminal
2. In terminal, type this:
    sudo apt-get install efax
3. If it asks you whether to install or not, type y and press enter

I just did that and I see that efax is not listed in the applications menu (even after refreshing the panel) , however you can try running it from a terminal command. To do that, open a terminal window and type efax and press enter. Remember to have your modem set up before that.

If you're successful, please post your response so that others can benefit. If you fail, still post so that someone can reply to you. :)

---

### Post by sophtpaw on 2005-11-29
[QUOTE=anil_robo]I'm not a pro, just a noob like many of linux users. I had once subscribed to a paid service called e-fax where it was possible to send them an email and they shall have it faxed.

If you want to send fax for free, you shall have to use dial-up internet. I tried the same from windows XP on dialup line in an emergency, and sent around 30 pages of fax with cover page flawlessly. With Linux, I think there are two programs you may try out. One is hylafax and the other is efax. The first program (hylafax) doesn't exist when I try to install it from the official repositories. efax installs however. But I can't try it out right now because I'm shifting house and dont have access to phone line. Maybe you can install efax. The steps:
1. Applications--> Accessories--> Terminal
2. In terminal, type this:
    sudo apt-get install efax
3. If it asks you whether to install or not, type y and press enter

I just did that and I see that efax is not listed in the applications menu (even after refreshing the panel) , however you can try running it from a terminal command. To do that, open a terminal window and type efax and press enter. Remember to have your modem set up before that.

If you're successful, please post your response so that others can benefit. If you fail, still post so that someone can reply to you. :)[/QUOTE]
O.k - i did that. Installed efax with Synaptic. Does not run simply putting 'efax' in the terminal. 
I then also installed 'efax gtk' which is a front end for efax. That is there in  Applications/Office/Efax-gtk. 
Now, i just need to learn how to use it. It doesn't appear intuitive to my intuition. In fact it is all goobledeegook right now.

--
sophtpaw

---

### Post by ngms27 on 2005-11-29
Most Email servers i.e. MS Exchange provide this facility providing a modem is directly connected to the server running the service.

To do this via the internet I reckon you will have to pay someone as there will be a cost involved for the telephone call.

The other alternative is to hook up a modem to your box, connect to the telephone line and run a Fax Server locally. This may provide the facility to send via email/drag and drop etc.

HTH

JonnyT

---

### Post by larry on 2005-12-01
Thanks Everybody.
I am on the move and I won't be able to try my hands at efax for some time.
Has anyone already tested if it works with a non-dial up connection (like the DHCP you may have at work)?
Cheers

Larry

---

