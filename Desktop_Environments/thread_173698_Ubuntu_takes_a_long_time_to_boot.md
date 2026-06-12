---
title: "Ubuntu takes a long time to boot"
date: 2006-05-10
forum: Desktop Environments
---

### Post by DarkManX4lf on 2006-05-10
for a couple of days now ubuntu has taken a long time to boot up...it stalls at "loading network interface"....is there a way to fix this?

---

### Post by gerbman on 2006-05-10
What's "booting"...j/k, I'm a little spoiled by linux and the lack of reboots :-)

Your machine can't get an IP address, so it's just hanging. Do you have a working internet connection when the machine finally boots, or do you have to set up the connection manually? One option is to hit CTRL+C when the "loading network interface" comes up, but you'll probably have to set the connection up manually later on with something like```
sudo dhclient
```Help any?

---

### Post by DarkManX4lf on 2006-05-10
well im using a laptop and its wifi card to access my network...

heres exactly what it stalls on
"configuring network interfaces..."

but once im in gnome i have no network problems....

---

### Post by gerbman on 2006-05-10
[QUOTE=DarkManX4lf]well im using a laptop and its wifi card to access my network...

heres exactly what it stalls on
"configuring network interfaces..."

but once im in gnome i have no network problems....[/QUOTE]I have the same problem with my laptop and wireless. I usually just hit CTRL+C when that part comes up, and then set up the connection myself using dhclient.

---

### Post by DarkManX4lf on 2006-05-10
aight i'll try that and see how it goes

thanks

also i want to add, i have some problem reading cd's on ubuntu, sometimes i would put in a cd and it wont read the files, or it shows a file liek this "????????????????????????????????????????????"...just like that...the only way i can get it to read a cd after it shows that is by rebooting....is this common ?

---

### Post by Sef on 2006-05-10
> is this common ?

No it is not, but there was another thread with the same problem.  If I can find it, I will post it here.

---

### Post by OneSeventeen on 2006-05-10
I have the same problem, and when I go into gnome I have to change the network settings to whatever my current network is.. each time... even if I'm on the same network as last time.

It remembers, and shows the name selected, but I have to re-select the same wireless network and submit it.

If I hit control+c, then I have to set it, reboot, and set it again.  will dhclient restart my wireless networking without rebooting?  (I"ll try tomorrow at work)

---

### Post by gerbman on 2006-05-10
[QUOTE=OneSeventeen]I have the same problem, and when I go into gnome I have to change the network settings to whatever my current network is.. each time... even if I'm on the same network as last time.

It remembers, and shows the name selected, but I have to re-select the same wireless network and submit it.

If I hit control+c, then I have to set it, reboot, and set it again.  will dhclient restart my wireless networking without rebooting?  (I"ll try tomorrow at work)[/QUOTE]dhclient should automatically renew your IP address. What's your /etc/networking/interfaces file look like?

---

