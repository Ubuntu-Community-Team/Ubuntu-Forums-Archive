---
title: "gnome-ppp not working"
date: 2005-12-14
forum: General Help
---

### Post by SpartanZac on 2005-12-14
Hello
I just recently installed ubuntu 5.10 on my mom's system.  I was able to get dial -up networking to work via the Network Settings tool under the Administation Menu.  I thought this was a clumsy way of dialing out so in installed wvdial off the 5.10 cd and downloaded gnome-ppp (latest version) from debian's site.  When I run gnome-ppp under sudo everything seems to work fine, the log indicates no write errors and it says pppd started successfully.  However firefox is not able to load a web page.  When i try to ping a distant server via either ip address or dns address, I get an error saying "no network connection" or something along similar lines.  If i connect via Network Settings, everything works fine.  I just have a problem with gnome-ppp.  I do have to tell it to ignore terminal settings since it is trying to use the isp number string as a user name.  I am at a total lose.  I have a feeling it is a pppd config problem.  But I am willing to use another dialer.  
Any Ideas?

---

### Post by mikeymouse on 2005-12-14
Hi:
 Before you can get gnomeppp working you should thru a terminal do a 
 sudo pppconfig.  Fill the information out as required. Then setup your gnomeppp.
  Hope this helps.. 
  mikeymouse

---

### Post by SpartanZac on 2005-12-14
Didn't do a lick of good.

---

### Post by linuxguiri on 2005-12-29
I'm having the exact same problem. Have you found any solutions since this last post?

---

