---
title: "how do i connect to my isp?"
date: 2009-06-24
forum: Desktop Environments
---

### Post by rsj-1 on 2009-06-24
good day all
i installed ubuntu 9 desktop. for the next door nabor.
 
how do i connect to his isp?
 
his isp is [www.dialup4less.com]("http://www.dialup4less.com")
it is dialup thru a modem.
i have the phone # the modem calls
and i have the address (125.126.38.45) example
it was working on ubuntu 6.
please keep in mind that this is new to me so 
please explain step by step.
my email is [EMAIL="rsj-1@juno.com"]rsj-1@juno.com[/EMAIL]
 
i thank you in advance.

---

### Post by Alex8080 on 2009-06-24
try some stepbystep-guides online like:

[https://help.ubuntu.com/community/DialupModemHowto#Configure%20Connection%20to%20Internet%20Service%20Provider](https://help.ubuntu.com/community/DialupModemHowto#Configure%20Connection%20to%20Internet%20Service%20Provider)

---

### Post by rushikesh988 on 2009-06-24
Making a dial up connection in ubuntu using mobile
1.At First go to terminal from Applications --> Accessories- --> Terminal
2.Terminal will open on your screen
3.Now type the following command into the terminal
"sudo wvdialconf/etc/wvdial.conf"

It will ask for a password type the password of your profile there

4.It will show some messages in the terminal(see image)

Plz note the type of modem connected for example here in 3rd line from bottom and note the max speed too (in 5th line from bottom)

5.Now type the command "su" into the terminal .
It will ask for a root password enter there root password (or your if there is only one user on the system)
And enter the command:

" sudo gedit /etc/wvdial.conf " into the terminal
It will open the new window called 'gedit'

6.Edit it as follows bt remember to change Modem type as like your modem and modem address ,your service providers dialling number(you can ask this no to the service provider) ,speed too then save it .(make a backup of original file)

copy paste this and edit as I told you

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3= AT+CGDCONT=3,"IP","airtelgprs.com",,0,0
Init4 = AT+CPIN?
Init5 = AT E0
Init6 = AT+CGQREQ=3,0,0,0,0,0
Init7 = AT
Init8 = AT+CGQMIN=3,0,0,0,0,0
Phone = *99***3#
Password = b
Modem Type = USB Modem
Stupid Mode = 1
Baud = 460800
Modem = /dev/ttyACM0
ISDN = 0
Username = a

7.Now go to the terminal and type ' wvdial ' there. Wait for some time...........

8.Now wait for some time let it get some other IP addresses like this
->local IP address 117.98.32.192
--> pppd: &#65533;?&#65533;&#65533;X&#65533;[06][08]H&#65533;[06][08]
--> remote IP address 192.168.100.101
--> pppd: &#65533;?&#65533;&#65533;X&#65533;[06][08]H&#65533;[06][08]
--> primary DNS address 202.56.230.5
--> pppd: &#65533;?&#65533;&#65533;X&#65533;[06][08]H&#65533;[06][08]
--> secondary DNS address 202.56.240.5-
--> pppd: &#65533;?&#65533;&#65533;X&#65533;[06][08]H&#65533;[06][08]

9. If you get this type of messages then chill and use firefox  ENJOY

---

