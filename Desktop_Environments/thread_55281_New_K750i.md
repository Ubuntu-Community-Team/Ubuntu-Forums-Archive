---
title: "New K750i"
date: 2005-08-08
forum: Desktop Environments
---

### Post by saadat on 2005-08-08
I have a new Sony Ericsson K750i what is the recommended software in Linux to handle synchronisation and image transfers....

---

### Post by Kjell on 2005-09-03
I'm trying to get my K750i to sync with Evolution using MultiSync.
Its OK to access the files on the phone as Ubuntu mounts the phone as Removable media. 

USB cable
First I tried using the USB cable, I was not able to get multisync / k750i to sync.
I tried following: 
For MultiSync set-up, I first had to find out how the phone was reconized by Ubuntu
by using the "root" comand:  tail -f/var/log/messages
among all the results from this I could see that the phone was connected to 
/dev/ttyACM0 and /dev/ttyACM1
So I used this in Multisync configuration and started the sync function, the phone 
reconized that something wants to sync - but the phones just tries / nothing happens. It's like,  the light is ON - but nobody is home.

BLUETOOTH
As I could not get it to work with the USB cable,  I got a bluetooth dong, trying to use it with MultiSync.
For multisync bluetooth setup I need the adress of the K750i, I did get this using the comand: hcitool scan ,which gave me the adress and the phone name.
I used the adress for multisync - then seached for devices - it found my K750i 
My phone responed with a new bluetooth device - and the name of my Ubuntu system.  Then K750i asks for a password - (ubuntu system password) 
What password ?   I just cant figure out what password it needs

I cant enter my Ubuntu-system password as this password is alfa 
it not possible to enter alfa passwords on the phone, only nummeric.

Stuck again !  and seaching for solutions

---

### Post by dilerra on 2005-09-14
Hi there,

The password being asked for is probably the one you (or someone else) has entered in the following file:

/etc/bluetooth/pin

Open that file as root and change the password if you like... I have a W800i myself and it works nice syncing with Ubuntu Breezy (Development Release). The only problem is that no contacts are synced (only addressbook and todo-list). That's a shame...

---

### Post by sinaen on 2006-01-06
Can you transfer files via bluetooth?
or is it just adress lists and such

in what format should these adress/phone books be?

---

### Post by gippie on 2006-12-14
Sync success on Ubuntu with Sony Ericsson's k750i/w800i

I just did a sync on my converted k750i to w800i and evolution using multisync with the plugins libmultisync-plugin-evolution, libmultisync-plugin-irmc and libmultisync-plugin-syncml  obtained via de synaptic package manager in ubuntu 6.10 edgy.

Managed to sync contacts, calender and tasks by using the cable that came with the phone. Might try to use the bluetooth as well in case i forget my cable.

Initially the sync did not got anywhere as multisync did not get any of the plugins displayed. Also the libmultisync-plugin-all would not be installed because of some dependency problem so i removed my previous installed multisync and installed it fresh with these plugins. irmc needs to see the phone connected on /dev/ttyACM0. IRMC is the first plugin and Ximan evolution is the second plugin.

Good luck

Gippie

---

### Post by rydow on 2006-12-22
I had a K750i and I found this page [http://stefans.datenbruch.de/k750i/](http://stefans.datenbruch.de/k750i/) and the thing I had most fun with was using the phone as remote control over bluetooth for xine.

I don't remeber all the details of setting things up since the phone broke, while washing the car the phone slipped into to a bucket of water and never worked properly afterwards.

It is a good phone but not fool or water proof...

Hope you find the link interesting
Jonas

---

