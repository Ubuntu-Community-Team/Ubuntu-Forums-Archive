---
title: "can connect with wvdial but cannot with gnome-ppp"
date: 2005-12-07
forum: General Help
---

### Post by howlerbr on 2005-12-07
ok, here is my problem: I can connect to the internet with wvdial. I' ve ran wvdialconf /etc/wvdial.conf changed to my ISP number, user and password and everything goes fine. Also, I had to put Stupid Mode = 1 in that file.

but I really need to connect with gnome-ppp (since is my mother that is the primary user of the computer) and it is more user-friendly. But I can connect with it. It gives me an error and abort. I thought that this app uses wvdial behind the scenes, is that correct? Probably I'm missing some configuration. Do you have any tip?

---

### Post by Bachstelze on 2005-12-07
is it THAT difficult for your mom to open a terminal and type "wvdial" ?

---

### Post by howlerbr on 2005-12-07
yes it is! actually I could configure gnome-ppp I just need to uncheck a checkbox in the options tab... (about carrier detect)

but I'm facing a new problem now! In the first time I can connect but when I disconnect and try to connect later (without reseting the computer) the I got a message saying that I have no permission on /dev/ttySL0.

Why in the first time I can connect and in others not? If I wanna connect again I need to reboot the computer.

I think the solution is simple but I could not figure it out yet. The user is alredy in dip group.

What should I do? I think that gnome-ppp changes the permission of that device.

---

### Post by digitalkarabao on 2005-12-07
try altering the launcher command of gnome-ppp to 'sudo gnome-ppp'.

---

### Post by mikeymouse on 2005-12-07
Hi: yep sure is confusing.
  do a sudo pppconfig  enter all your data and then you will be able to setup gnomeppp in the regular manner.. Hope this helps 
 Goodluck.. mikeymouse

---

### Post by howlerbr on 2005-12-07
didn't work... I put "sudo gnome-ppp" in the shortcut and now gnome-ppp does not launch...

I'm still with the problem. When my connection is dropped and I try to connect again I got a message: "Could not open modem". When I click in details it says that I have no permission on /dev/ttySL0. So I have to reboot in order to connect to the internet again.

Could someone help?

---

