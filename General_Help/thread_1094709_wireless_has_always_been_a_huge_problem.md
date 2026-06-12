---
title: "wireless has always been a huge problem"
date: 2009-03-12
forum: General Help
---

### Post by rmausser on 2009-03-12
Hi there. 

I love Ubuntu. It's great, been using it for 4 years now. The wifi on my previous Compaq laptop worked flawlessly. 

I thought I should say one good thing before one bad thing. Actually I said two.

Ubuntu on my new HP Pavilion dv2000 on the other hand, the wifi makes me want to throw this computer against a brick wall really hard. 

As reference, it works awesome in Vista (and by awesome I mean awesome for Vista)


This is Ubuntu Intrepid 64-bit and I am running the Broadcom STA wireless driver, as it wont work without it, on the .13 kernel (but this problem has been around since I installed Intrepid)

Basically I have two issues.

First issue: Every (approx 5 minutes) I will completely lose all packet transfer over any wifi network (not just one specific network) The wirless modem will keep a solid connection the entire time (full bars) BUT packets will cease to be transfered both ways. 

This will last as long as 7 minutes. This brings me to issue number 2.

Second Issue: If I disconnect from any network, and try to reconnect within the same computer session, I cannot. No matter how many times I try after disconnecting, the wireless WILL NOT reconnect unless I restart my computer. Sometimes, I will restart my computer, and it will still not reconnect so I have to restart it several times. 

In Wicd it Authenticates the network, and then gets stuck on "Obtaining IP address." On my own router I could flush the IP table for DHCP, but with wirless cafe's, my University's wirless internet, airport wifi etc I cannot. So this is not a good answer to the problem. 

Third Issue: my wireless will not go over 300 KB/s transfer rate. I have a wireless N router and wireless N card in my computer... my router recognizes it as being N. 

I can seem to slightly fix the lag/speed problem if I run 

sudo iwconfig eth1 rate 54M
sudo ifconfig eth1 mtu 1492

in the terminal. Doing this every time is annoying so I tried the tutorial where you add this data to

/etc/network/interfaces

but it doesnt work for me. 

Plus, this doesnt solve issue two. 

Please, please help. This is not a threat but I am getting very busy in school and cannot deal with this 4 minute lag while doing my essay in Google Docs and researching online articles. 


Help me please. Fix my Internet and I will give you $10 in music credits at an online store or something. (almost said itunes..ooops)

Thanks 

Rob.

---

