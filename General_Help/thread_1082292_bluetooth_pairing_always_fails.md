---
title: "bluetooth pairing always fails"
date: 2009-02-27
forum: General Help
---

### Post by sdowney717 on 2009-02-27
It actually worked one time, got the authorization code and it paired up to the vx 8300. But I deleted the pair cause I lost the code and now it wont work anymore.
It will find the phone, but cant pair up at all on either phone.
The phones can find each other.

The adapter is bluetooth 2.0 capable.
The phones are vx8300 and vx5300

any ideas?

---

### Post by fragos on 2009-02-27
I've a VX8300 and had to enable discovery on the phone to be able to pair. VX8300 discovery time out in a very short period of time unlike the Ubuntu desktop which can be left discoverable all the time.

---

### Post by sdowney717 on 2009-02-27
yes in a minute it will time out.
It will discover the phone but I cannot pair up.

Once the phone is discovered, the timeout should not matter.?
Seems the timeout is just hiding the phone from being discovered.

Is there another program i can use instead of the bluetooth applet.
Is something not installed that needs to be installed?

I dual boot, so I can succesfully pair with XP blue soleil driver.
However, I think most useful services are disabled on this phone

---

### Post by sdowney717 on 2009-02-27
[http://www.pcauthority.com.au/Tutorial/106497,syncing-a-bluetooth-phone-with-a-linux-box.aspx](http://www.pcauthority.com.au/Tutorial/106497,syncing-a-bluetooth-phone-with-a-linux-box.aspx)

wish it was so easy

[http://ubuntuforums.org/showthread.php?t=964139&page=11](http://ubuntuforums.org/showthread.php?t=964139&page=11)

apparently lots of others having trouble

---

### Post by sdowney717 on 2009-02-28
well I deleted everything with bluetooth out of synaptic including configurations.
Reinstalled these items.

Now it can pair with the phone.

well it only paired with a vx5300.
The vx8300 still wont pair.

---

### Post by sdowney717 on 2009-03-01
well I installed blueman and can now connect to both phones.
[https://launchpad.net/~blueman/+archive/ppa](https://launchpad.net/~blueman/+archive/ppa)

However, verizon disables all file services to these phones so 
what a waste of my time.
I tried connecting to the phones using bitpim, but bitpim cant connect. 

Apparently you cant do anything using bluetooth to these phones?

---

### Post by fragos on 2009-03-02
> **sdowney717 said:**
> well I installed blueman and can now connect to both phones.
[https://launchpad.net/~blueman/+archive/ppa](https://launchpad.net/~blueman/+archive/ppa)

However, verizon disables all file services to these phones so 
what a waste of my time.
I tried connecting to the phones using bitpim, but bitpim cant connect. 

Apparently you cant do anything using bluetooth to these phones?

Many carriers including Verizon disable phone features to force you into buying mobile media from them.

---

### Post by sdowney717 on 2009-03-04
I did discover I can email pictures to myself.
I did not have to edit anyfiles to get blueman to work.
What I did was remove completely with configurations all bluetooth files.
then reinstalled everything.
Then added blueman repo
installed blueman.

---

