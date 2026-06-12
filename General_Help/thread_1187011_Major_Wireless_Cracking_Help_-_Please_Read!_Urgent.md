---
title: "Major Wireless Cracking Help - Please Read! Urgent!"
date: 2009-06-14
forum: General Help
---

### Post by Vision1337 on 2009-06-14
Hey all, i just want to point out, this is for educational purposes, for testing my networks vulnerabilities and so on, so no one can crack my network.

Info:

Model: Toshiba
Comp: Satellite Pro L300
Model Number: PSLB1A-02D008

Problem:

So im following a tutorial on cracking wireless...
(Note: Everyone i've looked at is the exact same)

Link To Tutorial: [http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/](http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/)


I decided not to patch, it had something to do with updating the driver, mines up to date.
Im currently at:

editing the sources

"sudo gedit /etc/kismet/kismet.conf Change the line that begins with ’source=’ to ’source=madwifi_ag,ath0,madwifi’. Now reboot the computer. After it boots back up you should be able to access the internet again via your wireless card."


since im not using madwifi, and when i type iwconfig, i get wlan0 in use, so i put:


source=rt8180,wlan0,rtl8187b


im not sure if that is right the original writing i was told is:


source=rt8180,interfacename,name

so i've just edited it myself....

when i type "lspci" in terminal i get a whole lot of stuff but the only thing that sticks out to me is:

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

moving on.. i ran:

sudo airmon start wlan0

sudo kismet

no errors there, in kismet i found the channel id and essid

but i get stuck at this part:

"sudo airodump wlan0 filename channel# 1[B]"

i get:

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel <#>'

when i [/B][B]run 'ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel <#>'

i get:

bash: syntax error near unexpected token `newline'

if i change the <#> to <1> i get:

bash: syntax error near unexpected token `1'

atm im stuck :)
[/B]

---

### Post by Vision1337 on 2009-06-14
Need help urgently pls :)

---

### Post by gradinaruvasile on 2009-06-14
I am no exper on this, but

did u run

when i run 'ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel <#>'
with <1> or just 1?

---

### Post by night_fox on 2009-06-14
> Hey all, i just want to point out, this is for educational purposes, for testing my networks vulnerabilities and so on, so no one can crack my network.

lol

:popcorn:

---

### Post by Vision1337 on 2009-06-14
> **gradinaruvasile said:**
> I am no exper on this, but

did u run

when i run 'ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel <#>'
with <1> or just 1?

<1> let me try with 1

Edit: i get:

vision@vision-laptop:~$ ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel 1SIOCSIFFLAGS: Permission denied
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.

---

### Post by gradinaruvasile on 2009-06-14
Insert sudo before the command if u are not root.

---

### Post by Vision1337 on 2009-06-14
same thing:

vision@vision-laptop:~$ sudo ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel 1
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.

---

### Post by Vision1337 on 2009-06-14
anyone here to help? im soooo close..

---

### Post by AndyCee on 2009-06-14
The ';' seperates two statements. Try putting a sudo before the second statement as well.

ie:
```
vision@vision-laptop:~$ sudo ifconfig wlan0 up; sudo iwconfig wlan0 mode Monitor channel 1
```

---

### Post by gradinaruvasile on 2009-06-14
Maybe a conflict with your network-manager?

---

### Post by Vision1337 on 2009-06-14
i now get:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

when i place the 2nd sudo in, i am connected to the net via wireless, might that be it? im only going to disconnect the net if i need to?

---

### Post by gradinaruvasile on 2009-06-14
Probably yes...

---

### Post by Vision1337 on 2009-06-14
Let me try it, brb

---

### Post by Vision1337 on 2009-06-14
nope i get the same thing

---

### Post by Vision1337 on 2009-06-15
bump still need help

---

### Post by AndyCee on 2009-06-15
Try swapping the command order. The point of having the interface down is so you can change settings, so it seems odd to bring it back up *before* altering it.

```
vision@vision-laptop:~$sudo iwconfig wlan0 mode Monitor channel 1; sudo ifconfig wlan0 up
```

---

### Post by Vision1337 on 2009-06-17
worked ty! will post back soon

---

### Post by Vision1337 on 2009-06-17
exact same error:

vision@vision-laptop:~$ sudo airodump wlan0 filename channel# 1

Unsupported hardware link type  803 - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel <#>'

i might have to patch... the link to the thread is: [http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/](http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/)

if anyone can tell me how to patch my chipset/drivers, i will check later, please leave what i need to type in terminal / give you, so you can help me tysm!

---

### Post by cariboo on 2009-06-17
If you want to check the security of your own network, why do you need the info so uregently?

---

### Post by Vision1337 on 2009-06-17
what do you mean? im wanting to crack my network to see 1. how easy it is 2. what i can do to improve it, all im asking for is some help.

---

