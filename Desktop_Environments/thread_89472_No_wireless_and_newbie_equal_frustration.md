---
title: "No wireless and newbie equal frustration"
date: 2005-11-12
forum: Desktop Environments
---

### Post by just1m on 2005-11-12
I have a netgear wg311t card and just loaded breezy this morning. I am new to linux in general and most of the posts relating to this aren't to clear to me. Any thoughts?

---

### Post by Zotova on 2005-11-12
Have you tried ndiswrapper? It is available via synaptics - it allows you to use your windows drivers (the ones which came with the card on the disc) on Linux.

---

### Post by just1m on 2005-11-12
no, not to sure how to do it. Can you run me through it?

---

### Post by Zotova on 2005-11-12
If you go into synaptics.

System menu - Administration - Add applications

then search for ndiswrapper and tick the install box and then apply. That will download ndiswrapper and install it for you. 

Once installed there should be a new entry under administration which will allow you to install your windows drivers.

---

### Post by just1m on 2005-11-12
not seeing it. what heading would it be under?

---

### Post by Zotova on 2005-11-12
Sorry, just to clarify, when you search for ndiswrapper.

Tick the ndiswrapper-utils for install and ndisgtk - when you install ndisgtk the new menu item will appear.

---

### Post by just1m on 2005-11-12
files are downloading

---

### Post by just1m on 2005-11-12
Ok files are here. I have it open and it shows a win2k driver, a win9x driver and a winxp driver. which should i use?

---

### Post by Zotova on 2005-11-12
I'd go for the xp driver personally. If that doesn't work the 2k one and then the 9x one.

I'd presume the ndiswrapper team would focus on xp drivers however.

---

### Post by just1m on 2005-11-12
there are three files in the xp folder. I think the .inf or the .sys file is the one to use. Thoughts?

---

### Post by Zotova on 2005-11-12
Ndiswrapper should ask for the .inf file but you are supposed to have the sys files as well.

I have never used the gui version of ndiswrapper I always configured it via the terminal. I'm presuming you'd select the inf file with the gui and it would then setup your card. 

If you are however confrotable using the terminal I can talk you through how to do that a lot better.

---

### Post by just1m on 2005-11-12
I'd be fine giving it a try.

---

### Post by Zotova on 2005-11-12
Ok then.

Firstly for ease, move the inf files and sys files into their own directory. Lets say /home/username/ndis
(replacing username with whatever you username is)

Open the terminal and type: cd /home/username/ndis

To check ndiswrapper is actually installed type:

ndiswrapper

You should then get some information about the options ndiswrapper has.

To install your driver type:

ndiswrapper -i driver.inf

Replace driver with the name of your inf file.

Then type:

ndiswrapper -l

If everything is ok it should say driver present hardware present. If everything is ok type:

modprobe ndiswrapper

(your cards light should now light up)

Finally type ndiswrapper -m

You should now be able to configure your card via system - administration - networking.

Hope that helps.

---

### Post by Cuppa-Chino on 2005-11-12
Just1n in case you still have difficulties I recommend you check out:

[Nice example is on the Ndiswrapper project wiki page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Complete_Example_1_-_Netgear_WG311v2_.2B_Ndiswrapper_.2B_Ubuntu.2FDebian_.28Post_by_Yueh_-_stevenyu24_AT_gmail.com.29")

it could be that Ubuntu installed a driver for your card already (ACX driver), if that is the case the above walkthrough should help.

Also what encryption are you planning on using? 

If WEP then NDISWRAPPER UTILS should work fine, if you are planning to use WPA then I can throuroughly recommend the following: 
[ndiswrapper with WPA]("https://wiki.ubuntu.com/forum/hardware/ndiswrapperWithWPA")

---

### Post by just1m on 2005-11-12
Did it just as written but it saus name [www.ubuntu.com](www.ubuntu.com) could not be found please check name and try again. I also tried with yahoo as well so no dice

---

### Post by emperor on 2005-11-12
The Netgear wg311t should work with the default atheros driver in breezy, no need  to use windows drivers under ndiswrapper. 

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wg311t%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wg311t%29)

I would advice that you verify the chipset in the card using:

sudo lspci -v

and using 

dmesg |less

Also do not use the "restricted" security mode, use "open". It is possible to get "restricted" to work, but you have to change the mode of the radio to do so.

There is another thread today on this same subject with more details and a successful outcome.

---

### Post by Zotova on 2005-11-13
If I remember correctly though don't the new netgear cards use a different version and this is no longer works with the Linux native drivers? Or am I thinking of a different card.

---

### Post by quietglow on 2005-11-13
When you did "ndiswrapper -l yourdriver.ini" what was the response? This is critical cause if it gave a bunch of "forcing driver" errors its not going to work.

---

### Post by emperor on 2005-11-13
[quote=Zotova]If I remember correctly though don't the new netgear cards use a different version and this is no longer works with the Linux native drivers? Or am I thinking of a different card.[/quote]

"lspci -v" should reveal the chipset. The hardware vendors change chipset constantly, so it is possible that there has been a change.

---

