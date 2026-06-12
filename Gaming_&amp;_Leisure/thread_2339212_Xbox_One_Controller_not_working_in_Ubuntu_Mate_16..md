---
title: "Xbox One Controller not working in Ubuntu Mate 16.04"
date: 2016-10-06
forum: Gaming &amp; Leisure
---

### Post by Blix775 on 2016-10-06
I have been trying to use my Xbox One controller on Ubuntu Mate 16.04 but it is not working. I have read it should work out of the box. I have a Blutooth 4.0 usb dongle and I can see the controller and pair it but it does not work after being paired. It says successfully connected and paired but it does nothing. Steam does not respond to it and neither do gog.com games. Can anyone tell me if there is any known problems or if I am missing some steps to configure it. Thanks in advanced.

---

### Post by oldrocker99 on 2016-10-07
Here's the skinny on using a wireless XBox controller:[http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working](http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working)

Note that I don't have that controller and don't know if this'll work.

---

### Post by luckyknight on 2016-12-04
That link is about the Xbox 360 controller which uses it's own wireless adapter. The Xbox One S controller has bluetooth and the user above is trying to use that.

I also have the same issue - the controller will pair but it will do nothing.

However after googling around I found the solution.

```
sudo echo 1 > /sys/module/bluetooth/parameters/disable_ertm
bluetoothctl
scan on
pair xxx (the Mac of the controller)
connect xxx (the mac of the controller)
```

I also tried pressing the connect button on the controller as well.

It's now connected.

I am using kernel 4.8.12 on Ubuntu 16.04

---

### Post by oldrocker99 on 2016-12-05
My mistake, and thanks for coming up with a solution. Please mark this thread as [SOLVED] to help others with the same problem.

Also, please surround terminal commands or output with {code} and {/code} using [], square brackets. Your post has been edited.

---

### Post by luckyknight on 2016-12-05
I've added:


```

[I]echo 1 > /sys/module/bluetooth/parameters/disable_ertm
echo -e "connect xx:xx etc \nquit" | bluetoothctl
to /etc/rc.local
[/I]
```

But, it didn't work on boot. The first part did, the bluetoothctl didn't.


So I am not quite there with an automated solution

---

### Post by elmas2 on 2017-03-08
This will solve xbox s controler bluetoorh connect and disconnect problem.


1. install ---->  sudo apt install sysfsutils
2. open as administrator with gedit  --->  /etc/sysfs.conf after this
3. Add this line in sysfs.conf -->   module/bluetooth/parameters/disable_ertm = 1
4. Save and restart.

---

