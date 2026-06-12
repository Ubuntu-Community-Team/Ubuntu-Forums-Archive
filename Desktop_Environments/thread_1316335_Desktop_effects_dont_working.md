---
title: "Desktop effects dont working"
date: 2009-11-05
forum: Desktop Environments
---

### Post by javorulz on 2009-11-05
Hi, as title says my desktop effects are not working, I have a lenovo y530 with NVIDA GeForce 9000M with 256MB but... trying to use desktop effects i just get a message saying "Searching for drivers" and then just says "cannot activate desktop effects" i also tryed with compiz but it just doesnt seem to work

I've tryed everything... i modified xorg.conf, installed some stuff found in web, modify blacklist but nothing seems to work and its so strange cuz my laptop crashed last week when i upgraded to Karmic (new kernel doesnt work on my laptop and had some issues with previous) so i reinstalled everything, but before upgrading i had Compiz working very well without doing anything strange but now it does not work

any ideas?? wanna to me post something else??

---

### Post by Castor68 on 2009-11-05
I have the same problem with my desktop. With 8.04 LTS everything was perfect. I upgraded to 9.10 Beta and my nightmare started. Even with a clean installation of Karmic Koala, nothing works.

It seems there is not answer for us. I posted it weeks ago. Nothing yet.

---

### Post by rBoLt on 2009-11-06
its the correct device detected?
go to hardware drivers. do an auto detect. else run update manager. i saw there is a package update for nvidia drivers.

---

### Post by javorulz on 2009-11-06
if i go to hardware drivers i just get a message saying that my PC is using privative software for modem by software... just that... i dont see any other driver just the one for the modem :S

---

### Post by jayanramesh on 2009-11-07
Dear javorulz,
It may be due to previous driver you are using it.Download the  latest driver 190.42 from the below link and install. It may solve your problem.

> [http://www.nvidia.com/object/linux_display_amd64_190.42.html]("http://www.nvidia.com/object/linux_display_amd64_190.42.html")


---

### Post by randytan on 2009-11-07
I had the same problem when my office unit was "upgraded" so I had to install stuff from scratch and upgrade via the net.

At first the Koala was fast but it was lacking the effects and what not. Tried installing all the drivers from other sources and synaptic with little to no success.

Then when fiddling with the controls some more, I wound up in the Appearance Preferences window. When I clicked in visual effects, it was set to none. I clicked in extra and was told that I didn't have drivers and what not but it offered to look for me. After the app finished installation of the drivers, all was right with the world and things worked again!

Give it a try. Hope the solution for you is as simple as it was for me.

Good luck!

---

### Post by jayanramesh on 2009-11-07
Dear randytan,
> Re: Desktop effects dont working
I had the same problem when my office unit was "upgraded" so I had to install stuff from scratch and upgrade via the net.

At first the Koala was fast but it was lacking the effects and what not. Tried installing all the drivers from other sources and synaptic with little to no success.

Then when fiddling with the controls some more, I wound up in the Appearance Preferences window. When I clicked in visual effects, it was set to none. I clicked in extra and was told that I didn't have drivers and what not but it offered to look for me. After the app finished installation of the drivers, all was right with the world and things worked again!

Give it a try. Hope the solution for you is as simple as it was for me.

Please download the latest driver from the link below
[http://www.nvidia.com/object/linux_display_amd64_190.42.html]("http://www.nvidia.com/object/linux_display_amd64_190.42.html")

---

### Post by javorulz on 2009-11-07
it seems that the info of my laptop lied to me or something, it seems i dont have an Nvidia card
output of lspci
> 
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)


So i guees i have an intel card... also 256 MB i followed this guide but it didnt work
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

