---
title: "problem with netwok card"
date: 2005-11-01
forum: Desktop Environments
---

### Post by wammy on 2005-11-01
ok... really wierd problem here...

just installed a dual boot machine (win2000 + ubuntu5.10) 
but in ubuntu the network card fails where with win2000 everything works fine.

at first i installed ubuntu 5.10 64bit but the installer already complained about being unable to obtain dhcp info...
i figured it was a glitch so i assigned the network info manually.

after install it seems that i cant ping any pc's in the network but i can ping its own ip number (192.168.0.128)...
also i cant get into gnome so i figured it has to do with 64bit stuff so i quickly install the 32 bit version
alas, exactly the same problem.

although ifconfig shows its alive and kicking and i can ping myself i presumed the nic just kinda half died or its to exotic for ubuntu so i put in a super standard realtek nic that has never let me down, no matter what kind of distro.

same problem.
so i fiddle around with mii-tool.
auto negotiation fails so i force the different modes manually
doesnt help either.

so i figure it might be the hub since i have had certain nic's before that didn't like cetain hubs so i plug it into another working hub across the room...
doesnt help...

so i figure maybe its an ipv6 problem so i disable ipv6 and reboot but it still doesnt work.

so just to make sure its a problem with ubuntu i boot back into windows only to find out that the nic seems to work fine in win2000...

so im out of options here...

what the heck is going on?

any ideas?

---

### Post by wammy on 2005-11-02
n...no...n.. . nobody? :'(

---

### Post by mips on 2005-11-02
Stupid question, did you 'activate' the card under System->Administration->Networking   ?

---

### Post by jvictor on 2005-11-03
Please check if u have your network interface up and running, also can u tell what is ur network card modem i mean the chipset u r using ?

Post the o/p of typing the command **ifconfig** in your terminal / shell

mips, please dont b so aggresive. He must be new to Linux, lets help him out :)

---

### Post by mips on 2005-11-03
[QUOTE=jvictor]
mips, please dont b so aggresive. He must be new to Linux, lets help him out :)[/QUOTE]

Sorry if it sounds aggresive, there was no intent. Reason why I said 'stupid question' is that I battled my ass off on monday trying to get internet connection sharing going on a second LAN card. I tried everything, then I saw the 'activate' button and hey presto everything worked after i dunno how many hours. I did feel very stupid though ;)

---

### Post by wammy on 2005-11-03
hmm... i pulled the disk from this pc and put it into another pc and booted into ubuntu. it all seems to work fine in the other pc.
i guess ubuntu doesnt like my motherboards chipset which is a via vt8237.

---

### Post by mips on 2005-11-03
Deleted. Think I'm loosing my mind.

---

### Post by jvictor on 2005-11-03
well  well to the best of what i know via 8237 is a sata controller ..what has it to do with Networking ?

---

### Post by mips on 2005-11-03
Lets see your **/etc/network/interfaces** file
Lets see output of **ipconfig -a** command
Lets see output of **mii-diag** command
Lets see output of **mii-tool** command
Lets see output of **sudo dmesg** command

What does the PC connect to, router, switch, hub, provide **make & model** ?

---

### Post by wammy on 2005-11-07
[QUOTE=jvictor]well  well to the best of what i know via 8237 is a sata controller ..what has it to do with Networking ?[/QUOTE]

actually, it's the southbridge and it has among other things intergrated support for sata, lan etc...
so it has a lot to do with networking...

anyway,
i will try and post some more info when i get the chance.

---

### Post by wammy on 2005-11-07
i couldnt dig through dmesg since it was flooded with a 'setkeycodes' message.
i fixed that and finally could see the dmesg output.
all i noticed was an error about acpi.
since booting took about 6 or 7 minutes i figured it had to do with this acpi error so i disabled powermanagement in the bios.

it boots faster and strangely enough, the nic also seems to work now all of the sudden...
don't ask why.... 

i've had a ton of problems with this mobo (pcchips M861G) and still have.
only thing i can say is just dont buy cheap stuff like i did...

---

### Post by mips on 2005-11-07
Hmm, strange, a few people seem to have luck by disabling acpi.


Good to know you are working.

---

