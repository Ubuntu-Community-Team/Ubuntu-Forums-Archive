---
title: "Strange problem with file transfering phone-pc"
date: 2009-04-27
forum: General Help
---

### Post by elasto1mania on 2009-04-27
Hello,
I have a really strange problem, my phone SE W595 was able to communicate with ubuntu 8.10 and even 8.04. When I installed 9.04 it suddenly stop working.
I installed again 8.10 and it doesn't work on 8.10 either.

Any ideas

---

### Post by dLeon on 2009-04-27
Soft:
- Maybe your usb cable is damage.
- Maybe your usb plug is damage.
- Maybe your bluetooth (if you use it) signal damage.

Hard:
- Maybe your phone is damage.

What were you (actually) do before this happen?

---

### Post by elasto1mania on 2009-04-27
I use wire fro transfering.
I tried it on windows and everything works ok.
If set the phone to usb mode i get nothing. Transfering mode shows only files on phone cannot be accesed and shows only the free space of the phone.

---

### Post by dLeon on 2009-04-27
Is Ubuntu (Desktop/Nautilus/your file manager) show your mounted phone?
Mount your phone with sudo. Try to 'sudo ls' your phone.

---

### Post by elasto1mania on 2009-04-27
Thanks for your answers. :)
They didn't work. :(
Well I found Wammu it transfers files not really fast but it do it job. :)
Thx again

---

### Post by elasto1mania on 2009-04-28
I realized I can't transfer files from phone to pc .
BUT i found the real solution.

I executed this command

tail -s 3 -f /var/log/messages

and got Current: sense key: No Sense
Additional sense: No additional sense

I googled a bit and found the solution

edit: /etc/udev/rules.d/60-persistent-storage.rules

change: IMPORT{program}="vol_id --export $tempnode"
to: ENV{DEVTYPE}=="partition", IMPORT{program}="vol_id --export $tempnode"  

[https://bugzilla.redhat.com/show_bug.cgi?id=473035]("https://bugzilla.redhat.com/show_bug.cgi?id=473035")

---

### Post by kingofbadluck on 2009-08-20
Any way you can explain this solution in a simpler way? Im new to Ubuntu and wanting to use my ubuntu with w595 aswell, but that code thing is like chinese for me :)
Any help is appreciated.

---

### Post by Jerubaal on 2009-09-10
So is your phone now transferring files to & from Ubuntu easily now?
I'm considering getting the W595 imminently and would like to know whether I shouldn't!

---

### Post by elasto1mania on 2009-10-07
It do work.
You will be able to aces phone memory and card memory. You will se them like usb.

This is the procedure for ubuntu 8.10 on ubuntu 9.04 is the same just the file is placed somewhere else and is called 70-persistent-storage.rules or something like that.
I am still trying to figure out hoe to get it work on 9.10.
Sorry for this big delay.

---

### Post by Jerubaal on 2009-10-08
Thanks for reply. I bought the W595 and got usb access to it by changing those persist.storage.rules type files.
Have just upgraded to 9.04, but yet to try it on there. Probably won't bother and just go straight to 9.10...

---

### Post by karpatt on 2009-10-30
For 9.04 the file is not in /etc but in /lib

/lib/udev/rules.d/60-persistent-storage.rules

---

### Post by johann_p on 2010-03-25
Same here, the W595 cannot be mounted as a mass storage.
I am using Ubuntu 9.10 and the line that I am supposed to change for the workaround does not exist in /lib/udev/rules.d/60-persistent-storage.rules

---

