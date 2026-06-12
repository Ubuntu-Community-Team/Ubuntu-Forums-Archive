---
title: "Cant connect to internet on dial up"
date: 2005-07-11
forum: Desktop Environments
---

### Post by -murdoc- on 2005-07-11
My friend Richard just switched form Redhat to Ubuntu and cannot connect to the internet via dial up.

Internet worked fine on Redhat so any help is gratefully accepted.

---

### Post by jasmuz on 2005-07-11
[QUOTE=-murdoc-]My friend Richard just switched form Redhat to Ubuntu and cannot connect to the internet via dial up.

Internet worked fine on Redhat so any help is gratefully accepted.[/QUOTE]
 First off we need to know what modem is he using, on what port and using wich method of dialing.

---

### Post by -murdoc- on 2005-07-11
i know its 56k but thats all.
just txted him asking

---

### Post by -murdoc- on 2005-07-11
is there some application he can use to configure his connection?

---

### Post by varunus on 2005-07-11
Ubuntu uses the wvdial program to configure and dial dial-up connections.  If it isn't working, then it may be a driver issue.  Ask him how he dialed on redhat (what program he used) and what modem he has.

---

### Post by mikill on 2005-07-11
I got mine to work by going to System > Administration > Networking
Click on Modem ppp0
Click on Properties
Click on the Modem tab and Auto detect

Once you do that go back to the general tab and fill out that info and OK
Then click on DNS and fill in the IP's of your ISP's DNS servers - if you don't know them then either call or see if they have that info online.

---

### Post by jasmuz on 2005-07-11
[QUOTE=-murdoc-]i know its 56k but thats all.
just txted him asking[/QUOTE]
 If he dosent figure it out, tell him to run a terminal, and do a sudo pppconfig to configure a dialing script wich he will be able to bring on with pon/poff to disconnect.

---

### Post by RJARRRPCGP on 2005-07-11
Try:

**sudo pppconfig**  

Then when finished with the configuration, to connect:

**pon (name of ISP that you decided to give in pppconfig)**

---

