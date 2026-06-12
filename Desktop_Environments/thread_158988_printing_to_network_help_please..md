---
title: "printing to network help please."
date: 2006-04-12
forum: Desktop Environments
---

### Post by dmizer on 2006-04-12
first of all, i have spent days poking around at [http://www.linuxprinting.org/](http://www.linuxprinting.org/) and miles of endless ubuntu forum posts on the subject and i just can't seem to crack this nut.

i need to be able to print to my office networked printer.  it is a canon iRC3100F. as near as i can tell, there is no linux driver.  is there a way to get this printer working through an emulator or through wine or a similar rig?

---

### Post by dmizer on 2006-04-19
can cups use windows drivers for printing if the windows drivers are installed in a windows emulator or in a wine environment?

i need to be able to print.  that's my only problem at this point.  and printing is a make or break option for ubuntu in my office.  as a result of this, i am even willing to pay for an option that would solve this problem.

the canon iRC3100F has unix printing ability, but i can't seem to figure out how to make that work to my advantage.

are there any printing options for linux other than cups?

---

### Post by bbarrons on 2006-04-19
How is the office printer on the network? Is it connected direct to a hub or switch or is it connected to another computer and shared from there? I had a problem with a hp printer coneected to an XP machine. The only way it would work was to turn off bidirectional on the xp side? If it is connected to a hub or switch can you ping the printer?
I dont know the answer but it helps to think out loud......
Bill

---

### Post by dmizer on 2006-04-19
better than nothing.

it is connected directly to a router.  i am able to ping the printer as well as view the printers configuration manager via the browser.  it's there, i just can't print to it because there are no cups drivers for it that i have been able to find.

printer's configuration manager indicates that ipp as well as http are turned on.

here's the configuration page.  it's in japanese, but i will try to provide something of a bad translation:

```
DHCP : OFF
RARP : OFF
BOOTP : OFF
IP&#12450;&#12489;&#12524;&#12473; (ip address) : 192.168.1.50
&#12469;&#12502;&#12493;&#12483;&#12488;&#12510;&#12473;&#12463; (netmask) : 255.255.255.0
&#12466;&#12540;&#12488;&#12454;&#12455;&#12452;&#12450;&#12489;&#12524;&#12473; (gateway) : 0.0.0.0
&#12503;&#12521;&#12452;&#12510;&#12522;&#12469;&#12540;&#12496; (dns1) : 0.0.0.0
&#12475;&#12459;&#12531;&#12480;&#12522;&#12469;&#12540;&#12496; (dns2) : 0.0.0.0
&#12507;&#12473;&#12488;&#21517; (host name): Canon366656
&#12489;&#12513;&#12452;&#12531;&#21517; (domain name) : 	
DNS&#12398;&#21205;&#30340;&#26356;&#26032; (dns server): OFF
WINS&#12395;&#12424;&#12427;&#21517;&#21069;&#35299;&#27770; (wins name display): OFF
WINS&#12469;&#12540;&#12496;&#12398;IP&#12450;&#12489;&#12524;&#12473; (wins server ip): 0.0.0.0
&#12494;&#12540;&#12489;&#12479;&#12452;&#12503; (node type) : b&#12494;&#12540;&#12489; (b node)
&#12473;&#12467;&#12540;&#12503;ID (scope id) : 	
LPD&#21360;&#21047;&#12434;&#20351;&#29992; : ON
LPD&#12496;&#12490;&#12540;&#12506;&#12540;&#12472;&#12398;&#20986;&#21147; (banner page display) : OFF
RAW: ON
&#21452;&#26041;&#21521;&#12434;&#20351; (bi directional?): OFF
IPP : ON
HTTP : ON 
```

---

### Post by brentoboy on 2006-04-19
When I test drove windowsxp64. I had similar issues with unsupported printers.  The M$ answer to the issue--which worked for me--is to find another driver by the same company from a similar timeframe, and try using it instead.

This "works" because the PostScript language for most printers from the same company have simlar inner workings.

In Ubuntu, my IBM Infoprint 1116 uses the Infoprint 12 driver (perfectly)

Play around with all the drivers from your printer's manufacturer.

---

### Post by dmizer on 2006-04-19
okay ... just to be sure, i tried every single driver in the canon printer list.  none of the drivers will allow me to print.

cups does not have a driver for my printer.  i need another option ... is there anything at all i can do?

---

### Post by bbarrons on 2006-04-20
What is the model number of the printer. I tried to do a search for a 366656 and found nothing. I have someone I can talk to that might be able to help. I take it you have no problems with other computers on the ntwork talking to the printer?

---

### Post by bbarrons on 2006-04-20
another thought..... does canon provide device management software??? sometimes this will installed on a pc and then it can share from there. cups might not be the answer...

---

### Post by dmizer on 2006-04-20
it's a canon iRC3100F. (i've only been able to find japanese information on this model ... and my japanese is not that good).

don't know about device management software, but even if it did exist i would have no way of enabling it on the network as i do not have access to the office network admin.

---

### Post by bbarrons on 2006-04-20
I had an hp plotter in a network setting hooked up as your canon is.  The easiest way to get it to work was to use device manegement software on one pc that was able to see the printer. I then shared the printer from there. The rest of the network various windows platforms  would look at the pc rather then the ip address of the plotter.  I know you are trying to get a linux box to see the printer, I am sure there is a driver out there for cups that would work......it might not be a canon driver. someone elses might do the trick. no help from canon support??

---

### Post by dmizer on 2006-04-20
> no help from canon support??
same kind of support i get from anyone else.

"what version of windows do you have?"
"i don't have windows.  i run linux."
"linux? what's that?"
"it's a free operating system"
*long pause* "sorry, we can't help you."

and so, i post in forums ... lol.

anyway, i'm told that the printer has the ability to listen to both unix and mac os for printing.  and i even found a linux folder on the drivers cd, but i haven't found anything in the folder that can help me figure out how to get it to work.

there may well be a cups driver for it, but i have no way of knowing where to look or how to find it, and i've been at it a while (i use to work internet tech support, so i'm no slouch with google).

---

