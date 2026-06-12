---
title: "Newbee needs help!!!"
date: 2011-03-29
forum: Desktop Environments
---

### Post by insane_subro on 2011-03-29
Hi Guys..... I have been using windows for centuries now..... or it feels like. Now I feel like going for something new, better. Downloaded Ubuntu 10.10... Installed (15 GB to / "root" 5 GB to swap) . every thing went well. It said restart.. Did that... now I only have a black screen that looks like CMD or the Terminal. It says Ubuntu tty1 on top. subro@ubuntu Login... keyd my login then password.. done.. then it says welcome bla bla bla and type the command .... No UI No desktop.... What went wrong. Even when I try Ubuntu without installing its the same. HELP!!!!:confused:

---

### Post by Krytarik on 2011-03-29
Did you see any error messages?

May it be that you burned the "Alternate CD"?

Login at the console with your chosen username and password, and check if "ubuntu-desktop" is installed:
```
dpkg -l |grep ubuntu-desktop
```

---

### Post by insane_subro on 2011-03-29
No error message.... I downloaded from Ubuntu website...

---

### Post by tiendh on 2011-03-29
Just re-install it. I guess that you made mistake when installing Ubuntu

---

### Post by insane_subro on 2011-03-29
4 times i re-installed... nothing happens.. black screen with white text no GUI...

---

### Post by safarin on 2011-03-29
You install Ubuntu desktop or Ubuntu server??

---

### Post by ndefontenay on 2011-03-29
If you ended up installing something with no GUI,

you still can install it now. It will download a bunch of packages and next thing you know you'll get a GUI.

We will also know if there's any mistake. Type following and press enter:

sudo apt-get install gdm

This will prompt you for a password. It's the one you've picked during the installation.

Sorry you're having a hard time trying something new (It will end up really cool once you get the GUI up!)

---

### Post by insane_subro on 2011-03-29
Thanks [ndefontenay]("http://ubuntuforums.org/member.php?u=234062")... I really appriciate it... Vl try today.. and let you know.. So it seems internet is required.. I use my phone as modem but here I cant can I?

---

### Post by Krytarik on 2011-03-29
How about finally checking this!?:
> **Krytarik said:**
> 
Login at the console with your chosen username and password, and check if "ubuntu-desktop" is installed:
```
dpkg -l |grep ubuntu-desktop
```
Also, please post the outputs of those commands:
```
lsb_release -a
uname -a
```

---

### Post by alazou on 2011-03-29
It would also be interesting to know the name of your graphics do :
> lspci |grep VGA

---

### Post by insane_subro on 2011-03-30
I hardly understood most of the things you asked me. But I tried my level best. attaching the pictures of the result that I got.
Thanks for your help....

---

### Post by matt_symes on 2011-03-30
Hi

> attaching the pictures of the result that I got.
Thanks for your help....

You have gdm installed and you have the whole desktop installed.

gdm is your log in manager where you log in and that starts your X windows session.

What happens if you type

```
sudo service gdm start
```

when you are at the last screen shot you posted above. Enter you password. It will not be echoed to the screen. That is normal. Post a screen photo of what happens and any text displayed.

Also, can you boot into the LiveCD ?

Kind regards

---

### Post by insane_subro on 2011-03-30
> **matt_symes said:**
> Post a screen photo of what happens and any text displayed.

Didnt understand I am sorry to sound like an Idiot.. but u can treat me like one!!

> **matt_symes said:**
>  Also, can you boot into the LiveCD ?

When I go into recovery mode and low graphics mode I get into the desktop.... Normal boot I cant. If i am not wrong Live CD=Ubunto iso CD. This is from where I installed.:(

---

### Post by matt_symes on 2011-03-30
Hi

> **insane_subro said:**
> Didnt understand I am sorry to sound like an Idiot.. but u can treat me like one!!

I would never do that and you don't sound like an idiot so don't worry. :)

What i want you to do is...

Boot into normal mode, login to the console and type

```
sudo service gdm start
```

When you have typed that i want you to take a photo of the screen so i can have a look at it.

> 
When I go into recovery mode and low graphics mode I get into the desktop.... Normal boot I cant. If i am not wrong Live CD=Ubunto iso CD. This is from where I installed.:(

That is a good sign that you can get into low graphics recovery mode. I think either gdm is not starting or is crashing. I think it's more lightly it's crashing.

I just want a screen shot after you type the above command so i can have a look.

Kind regards

---

### Post by alazou on 2011-03-30
> **insane_subro said:**
> Didnt understand I am sorry to sound like an Idiot.. but u can treat me like one!!



When I go into recovery mode and low graphics mode I get into the desktop.... Normal boot I cant. If i am not wrong Live CD=Ubunto iso CD. This is from where I installed.:(

It would really help to know what's your graphic card, my guess is that there is an error whit the graphical interface and so it can't start. 
If it's a non supported card it'll be tricky.

so first when you are logged in the CMD interface do :
```
lspci | grep VGA
```

you can also please include the output of
```
cat /var/log/boot.log
```

and also please
```
grep "EE" /var/log/Xorg.0.log
```

Those will tell us what is going wrong with your setup.

you can also in the meantime try to bypass GDM with
```
startx
```
it should normaly start the graphical interface if the problem is GDM related

---

