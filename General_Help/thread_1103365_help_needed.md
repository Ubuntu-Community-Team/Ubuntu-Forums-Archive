---
title: "help needed"
date: 2009-03-22
forum: General Help
---

### Post by urd on 2009-03-22
hi, today i have been figthing against ubuntu, 'cause for some reason i can't log in :S

the log image disappeared, an my computer sesion starts these way

[[IMG]http://img12.imageshack.us/img12/4024/ubuntu007.th.jpg[/IMG]](http://img12.imageshack.us/my.php?image=ubuntu007.jpg) 

so i try a lot such as

```
dpkg-reconfigure xserver-xorg

start x

sudo /etc/init.d/ gdm start 
```

some of the answers was

[[IMG]http://img12.imageshack.us/img12/7307/ubuntu001.th.jpg[/IMG]](http://img12.imageshack.us/my.php?image=ubuntu001.jpg)

[[IMG]http://img12.imageshack.us/img12/7761/ubuntu008.th.jpg[/IMG]](http://img12.imageshack.us/my.php?image=ubuntu008.jpg)

i really don't now what to do next :S ... i'm to new with ubuntu, and google won't help  me :S

thanks

---

### Post by lisati on 2009-03-22
Unless I am mistaken, "start x" should be one word (no space):
```
startx
```
Hope this helps.

---

### Post by urd on 2009-03-22
> **lisati said:**
> Unless I am mistaken, "start x" should be one word (no space):
```
startx
```
Hope this helps.

alredy try it, but does´t work :S

---

### Post by demlasjr on 2009-03-22
you also can try to reinstall the x-server

> sudo apt-get remove ubuntu-desktop

and then 
> sudo apt-get install ubuntu-desktop

2 weeks ago I got the same problem and I resolved with this

---

### Post by urd on 2009-03-22
> **demlasjr said:**
> you also can try to reinstall the x-server



and then 


2 weeks ago I got the same problem and I resolved with this

:(:(:( ... still whitout working :S:S:S

---

### Post by demlasjr on 2009-03-22
any message when running "startx" ?

---

### Post by urd on 2009-03-22
> **demlasjr said:**
> any message when running "startx" ?

[[IMG]http://img11.imageshack.us/img11/9967/ubuntu009.th.jpg[/IMG]](http://img11.imageshack.us/my.php?image=ubuntu009.jpg)

this is the message

---

### Post by 3Miro on 2009-03-22
Problem is with the ATI Driver. Something is most likely not set up correctly in the xorg.conf file. I have never used ATI so I don't know what he xorg.conf should look like. Have you tried installing/reinstalling the ATI driver?

---

### Post by demlasjr on 2009-03-22
try with 
> sudo dpkg-reconfigure -phigh xserver-xorg

if not working I think you need to reinstall the radeon drivers. But can wait for other ideas...Anyway, try to rebuild x with the
> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by urd on 2009-03-22
> **3Miro said:**
> Problem is with the ATI Driver. Something is most likely not set up correctly in the xorg.conf file. I have never used ATI so I don't know what he xorg.conf should look like. Have you tried installing/reinstalling the ATI driver?

i don't know how to do that :oops:

---

### Post by cybergalvez on 2009-03-22
> **urd said:**
> hi, today i have been figthing against ubuntu, 'cause for some reason i can't log in :S

the log image disappeared, an my computer sesion starts these way

[[IMG]http://img12.imageshack.us/img12/4024/ubuntu007.th.jpg[/IMG]](http://img12.imageshack.us/my.php?image=ubuntu007.jpg) 

so i try a lot such as

```
dpkg-reconfigure xserver-xorg

start x

sudo /etc/init.d/ gdm start 
```

some of the answers was

[[IMG]http://img12.imageshack.us/img12/7307/ubuntu001.th.jpg[/IMG]](http://img12.imageshack.us/my.php?image=ubuntu001.jpg)

[[IMG]http://img12.imageshack.us/img12/7761/ubuntu008.th.jpg[/IMG]](http://img12.imageshack.us/my.php?image=ubuntu008.jpg)

i really don't now what to do next :S ... i'm to new with ubuntu, and google won't help  me :S

thanks

its gdm not Gdm from your image

---

### Post by demlasjr on 2009-03-22
> **urd said:**
> i don't know how to do that :oops:

can you try this:

[http://ubuntuforums.org/showthread.php?t=1097993](http://ubuntuforums.org/showthread.php?t=1097993)

:)

---

### Post by 3Miro on 2009-03-22
> **urd said:**
> i don't know how to do that :oops:

I don't know the package for the ATI driver, can anyone point his guy to the right package/s. The problem seems to be with the driver.

---

### Post by demlasjr on 2009-03-22
> **3Miro said:**
> I don't know the package for the ATI driver, can anyone point his guy to the right package/s. The problem seems to be with the driver.

like I said one message before you:

[http://ubuntuforums.org/showthread.php?t=1097993](http://ubuntuforums.org/showthread.php?t=1097993)

maybe will help

---

### Post by urd on 2009-03-22
> **demlasjr said:**
> like I said one message before you:

[http://ubuntuforums.org/showthread.php?t=1097993](http://ubuntuforums.org/showthread.php?t=1097993)

maybe will help

mmm if i can´t log how i can download the file for installing the driver?? :(:( ... i have the terminal, but i don´t have internet whit the terminal :(

---

### Post by demlasjr on 2009-03-22
> **urd said:**
> mmm if i can´t log how i can download the file for installing the driver?? :(:( ... i have the terminal, but i don´t have internet whit the terminal :(

this command
> wget [https://www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run](https://www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run)


will download automatic the driver from console. If you have the cable in your network card and the internet working in desktop mode I think will work too in terminal. Just try what say there. If you don't have internet on ubuntu pc, put your cable from your modem in your network card and I think will work. check with a ping or ifconfig.

---

### Post by urd on 2009-03-23
woot ...  thanks, finally i can fix that :)

---

### Post by demlasjr on 2009-03-24
welcome dude ;)

---

### Post by urd on 2009-03-31
hi again!! this happened again, but this time i don't have inet :S... how i do it, runing the file from  usb ??? :)

thanks

---

