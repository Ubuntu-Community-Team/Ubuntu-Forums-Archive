---
title: "1505N return from sleep? Bluetooth?"
date: 2007-07-15
forum: Dell  Ubuntu Support
---

### Post by LinuxBob on 2007-07-15
Just got my new 1505 N it rocks.  Couple of things i need help with:

1)  Power management, would like the laptop and display to sleep and it goes to sleep Ok.  How do I wake it up? I move the mouse hit keys nothing.   I have had to resort to hard reboot.

How do I wake up the sleeping laptop and/or display?

2) Bluetooth.  I see "bluetooth platform listed as installed hardware under "Hardware Information", I see Bluetooth Device Manager listed as enabled service.   How do I access Bluetooth to use keyboard & mouse, how do I verify I have bluetooth as no icon is provided nor is there andthing under applications or system preferences/administration (other than services listed}.

---

### Post by neptho on 2007-07-16
1: Have you tried pressing the 'power' button?  If the lid switch doesn't 'kick it off', that usually will.

2. sudo apt-get install bluez-utils

---

### Post by ndinadis on 2007-07-16
i am also having problems with the laptop waking up, its a pain!
I am trying some stuff and will see if I can get it fixed and will make sure to send you the info 
I had a question actually regarding the changes dell made to ubuntu 
Do you have the actual 1505N model or did you put ubuntu on yourself as I did?

---

### Post by LinuxBob on 2007-07-16
I purchased the actual 1505N model.  It is working great except for the sleep function wake up.

Yes I did hit the power button briefly and the laptop remained asleep.  

apt-get blueutilz does what exactly?

I called Dell's ubuntu support and while the first time I received good assistance in enabling the restricted nVidia driver, last night I simply asked how to wake up the notebook and got referred to Canonical!  According to this tech rep Dell onyl supports hardware and cannot address a situation when your keyboard and mouse do not wake up a sleeping PC as it does on eveyr other PC i have ever worked with.

I can work around, albeit grudgingly, the sleep/wake issue.  What about the Bluetooth?

---

### Post by AJL on 2007-07-16
I'd like to get in line on the Bluetooth question.  I see it in BIOS (I think?) but how can I start using it?

---

### Post by DonA on 2007-07-16
Regarding Bluetooth...  you'll probably need to buy the interface card.  I did.  If the blue LED isn't lit, chances are your unit doesn't have it.  Next time your 1505N is powered down, remove the battery.  You should see on the side a small "trap door".  Remove it.  If there is a connector dangling free, then you don't have the Bluetooth interface card.  Fortunately it's only about $20 from Dell, and is a snap to install.  It's about the size of a postage stamp.  It's called the "Dell Wireless 355 Bluetooth Module, for Inspiron".  As soon as you install it, you should notice the Bluetooth LED lit on subsequent power-ups.

Regards:   ..DonA

---

### Post by jairp on 2007-07-16
Well, seems like all e1505 users have similar problem. I have the same situation when it comes to waking up the laptop once the screens shuts off.

and, let me tell you smt. this is not only the problem of ubuntu, but, even in windows xp, it did the same thing. And, even my frnds seemed to have this problem. 

And, especially if u r woking unplugged, then the monitor(LCD screen) shuts itself a lot faster. and u cannt help but cold boot the PC. one way around is to. Plug the cable back. and shut the lid. then, wait until the power led flashes(as it does when it is sleeping) this could take a min or two depending on ur setting in power settings.. then open the lid and press some keys. violal.. this works. but ,  ur setting in power settings should not be when i close the lid do nthin. put a option like, when i close the lid, put it in standby.

---

### Post by ndinadis on 2007-07-16
I have the bluetooth for sure (I installed it myself and the blue led is on) 
I assume he does as well as he ordered the laptop and it is shown in the hardware monitor 
I have done the script listed above it states it is already installed
What I would like to know is how to install the bluetooth icon in the system tray? I have seen someone with it and I assume it is an interface similar to what I had in the windows world.
This sucks with the suspend wakeup problem 
I am actively working with several people to try and solve it by using pieces of other versions etc to get it working. I have done some stuff and had it sort of work once! lol

---

### Post by NickWV on 2007-07-17
Here is a good Bluetooth device documentation provided by the community : [http://help.ubuntu.com/community/BluetoothMouse](http://help.ubuntu.com/community/BluetoothMouse)

I just followed the instructions there and was able to make use of the logitech bluetooth mouse I bought, works great!

---

### Post by strabes on 2007-07-17
1) If you have a bluetooth module, run this: ```
sudo aptitude install bluez-gnome
```

2) It looks like you have an nvidia card. I guess you could still see the suspend/hibernate link in my signature even though it's for ATI cards (I think.)

---

### Post by ndinadis on 2007-07-17
I actually figured out what I was hoping to accomplish with bluetooth last night minutes after I wrote my post 
sorry I did not post it was getting late.
I went to sypnaptic and searched "blue" and found 2 files that included an interface and system tray icon, I installed them opened the program and a couple preferences later and I think its how I want it.
I think the command listed is the same thing unless it is the command just to enable bluetooth which I had already done earlier and was installed on the system from the start (smart ubuntu :) )

---

### Post by LinuxBob on 2007-07-18
> **DonA said:**
> Regarding Bluetooth...  you'll probably need to buy the interface card.  I did.  If the blue LED isn't lit, chances are your unit doesn't have it.  Next time your 1505N is powered down, remove the battery.  You should see on the side a small "trap door".  Remove it.  If there is a connector dangling free, then you don't have the Bluetooth interface card.  Fortunately it's only about $20 from Dell, and is a snap to install.  It's about the size of a postage stamp.  It's called the "Dell Wireless 355 Bluetooth Module, for Inspiron".  As soon as you install it, you should notice the Bluetooth LED lit on subsequent power-ups.

Regards:   ..DonA

DonA, perfect repsonse!  Will check as soon as I get home tonight.  While I recall Dell advertising the e1505n as having Bluetooth, I do not recall being presented an option for it when I configured my laptop.  Thus I assumed it came standard.  Again, I do see a "bluetooth platform" in the hardware manager and see a bleutooth service chacke din services, but no Bluetooth icon anywhere.

$20 isn't bad and sounds like an easy install if need be.  I want to use a Bluetooth keyboard & mouse and run this laptop from my rec room couch using my Hitachi 57" HDTV as monitor (S video out on the nvidia 7300 card) and pipe surround sound into my 7.1 Onkyo receiver.

---

