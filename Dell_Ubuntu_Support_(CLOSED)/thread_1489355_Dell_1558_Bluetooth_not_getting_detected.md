---
title: "Dell 1558 Bluetooth not getting detected"
date: 2010-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by venkidwaraka on 2010-05-21
Anybody has any problem with the bluetooth driver in Dell 1558?
Initially I had problem with the wireless driver but when I searched for some Hardware drivers, that fixed that issue. Now I face the problem with my bluetooth device. The device is not even getting recognized. I have checked by listing the devices, but it says "No device".
Please help with the appropriate driver or a way to solve this.

Thanks in advance:)

---

### Post by Rackstar on 2010-05-21
I'm having the same issue. Did you file a bugreport?

Thanks!

---

### Post by venkidwaraka on 2010-06-03
Not yet!! I haven't filed an official bug report yet. In some of the threads, they point out that it is caused due to the wireless driver malfunctioning. But I don't find a reason for that to affect the Bluetooth. Do you think so??:confused:

---

### Post by Rackstar on 2010-06-03
I don't have a clue actually...

Where did you find that?

---

### Post by venkidwaraka on 2010-06-08
I have got my bluetooth working all of a sudden. But we have to keep it on from windows. It can't be switched off from inside Ubuntu I suppose.
Try that one.

Please try this way
1) Get into windows
2) Switch on the bluetooth
3) Restart and get into ubuntu

See if this works.

Thanks:guitar:

---

### Post by kokonobs on 2010-06-08
This is a common problem. Apparently if you switch of the bluetooth in windows, ubuntu is unable to detect it. This means you'll have to go into windows to enable it and then back into ubuntu for it to bee seen. 

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by Rackstar on 2010-06-09
Good to hear that! Although I don't have Windows installed... I won't do a dualboot for only getting my bluetooth to work :p

Windows doesn't have the equivalent of a live cd, do they? Any other suggestions?

---

### Post by venkidwaraka on 2010-06-09
> **kokonobs said:**
> This is a common problem. Apparently if you switch of the bluetooth in windows, ubuntu is unable to detect it. This means you'll have to go into windows to enable it and then back into ubuntu for it to bee seen. 

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Thank you very much for this, Dude!!
I tried installing bluez when I had the problem but that dint fix the issue. Maybe that time bluetooth was not getting detected and hence the trouble. So do you think that keeping it turned on and reinstalling the bluez driver will fix the problem?

Thanks

---

### Post by venkidwaraka on 2010-06-09
> **Rackstar said:**
> Good to hear that! Although I don't have Windows installed... I won't do a dualboot for only getting my bluetooth to work :p

Windows doesn't have the equivalent of a live cd, do they? Any other suggestions?

I guess you had a windows pre-installed with the Studio..right??
Or did you make an order without OS?:p

---

### Post by kokonobs on 2010-06-09
> **Rackstar said:**
> Good to hear that! Although I don't have Windows installed... I won't do a dualboot for only getting my bluetooth to work :p

Windows doesn't have the equivalent of a live cd, do they? Any other suggestions?

Not sure what else you could do. There were some suggestions on a page i saw but i cant remember what page it was sorry. (try googling it) The only thing i can think of is to go into BIOS and make sure the bluetooth device in turned on.


> I tried installing bluez when I had the problem but that dint fix the issue. Maybe that time bluetooth was not getting detected and hence the trouble. So do you think that keeping it turned on and reinstalling the bluez driver will fix the problem?

Possibly. Try that and see.. Also make sure you are certain that you have a bluetooth device installed. because the bluetooth manager is started by default on 10.04 whether or not a bluetooth device exists.

Thanks

---

### Post by venkidwaraka on 2010-06-11
> **kokonobs said:**
> 
Possibly. Try that and see.. Also make sure you are certain that you have a bluetooth device installed. because the bluetooth manager is started by default on 10.04 whether or not a bluetooth device exists.

Thanks

Anyway the bluetooth works fine when we get into ubuntu after switching the bluetooth on from windows. As you said, the bluetooth service gets started as soon as ubuntu starts up and thats true. If the device is not turned on in BIOS, we won't be getting it in windows as well. Right?
This is the reason why I am not exactly able to spot the problem.

Thanks,
Venk!

---

### Post by kokonobs on 2010-06-11
> If the device is not turned on in BIOS, we won't be getting it in windows as well. Right?

Thats Right.. I said that because there was a long thread with some other guy and it turned out that he did not even have bluetooth. he only assumed he did cos the bluetooth manager was turned on automatically.

The link i posted did not really say why it is.

---

### Post by ingeva on 2010-06-13
I don't believe that the bluetooth problem has anything to do with Windows.
I have a Vostro 400, and I've been running all previous versions of Ubuntu with little trouble (the only thing I had to do was disable/uninstall the bluetooth managers/drivers).

With Lucid the bluetooth won't initialize. That is, it works perfectly until the GRUB has started loading the OS. After that it's dead as a stone. If I connect a cabled keyboard or mouse they both work perfectly, but I want to use the wireless keyboard coming with the computer. The only case it doesn't work is with Lucid Lynx. My next step is to try Mint 9, which is based on it. I haven't come that far yet, and maybe it's unpopular even to mention ... :)

---

### Post by gabo.cr on 2010-06-13
I wonder if Win* is the only option for us... will it work if I do it from VirtualBox?
(I really don't want to dual boot at this point)
[-(

---

### Post by venkidwaraka on 2010-06-16
> **ingeva said:**
> I don't believe that the bluetooth problem has anything to do with Windows.
I have a Vostro 400, and I've been running all previous versions of Ubuntu with little trouble (the only thing I had to do was disable/uninstall the bluetooth managers/drivers).

With Lucid the bluetooth won't initialize. That is, it works perfectly until the GRUB has started loading the OS. After that it's dead as a stone. If I connect a cabled keyboard or mouse they both work perfectly, but I want to use the wireless keyboard coming with the computer. The only case it doesn't work is with Lucid Lynx. My next step is to try Mint 9, which is based on it. I haven't come that far yet, and maybe it's unpopular even to mention ... :)

I don't think Mint is so much unpopular. But as far as I know, it is definitely not a good competitor for Ubuntu. All softwares will have some issues on its way, then only it will evolve.Right?
There is no option for me to move to Mint at this point. 
The case is we are not able to switch on the bluetooth hardware after getting into ubuntu. If its already switched on from windows, it works very fine and the software is much better than any others. Anyway I am trying to reinstall bluez after switching on the bluetooth from windows.
I will let you know the effects.

Thanks:guitar:

---

### Post by kamaaina on 2010-06-16
Ack! So by wiping out the windows partition I now have a bluetooth chip that will never turn on again?

---

### Post by venkidwaraka on 2010-06-18
> **kamaaina said:**
> Ack! So by wiping out the windows partition I now have a bluetooth chip that will never turn on again?

Let's hope that they will fix this issue with the next update if issue is reported. I tried to report the same, but unfortunately it failed. Those who plan to wipe out windows completely, please leave the bluetooth on before doing that.

Otherwise you won't be able to do that unless a new release comes up fixing it.

I tried each and every possible way to make this alright. I reinstalled Bluez after keeping the bluetooth on, that also didn't make it. :confused:

---

### Post by venkidwaraka on 2010-06-18
> **gabo.cr said:**
> I wonder if Win* is the only option for us... will it work if I do it from VirtualBox?
(I really don't want to dual boot at this point)
[-(

There is a chance that it might work if windows is installed in virtual box. But not tested. It would be appreciated if you are bold enough to try that out and let us know the results.

Thanks,
Venk!

---

### Post by kamaaina on 2010-06-18
A vm on virtual box cannot use any devices that are not available to the host.

---

### Post by venkidwaraka on 2010-07-02
Then that will create a problem. We have to find some other way.
Either we can report a bug to ubuntu or any other choice??

Thanks,
Venk!

---

